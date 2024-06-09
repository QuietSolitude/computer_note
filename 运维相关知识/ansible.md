# ansible教程
  ansible是远程自动控制服务器。     

###### 安装ansible
  `which python3`有输出就是说明安装了。     
  `sudo apt install python3-pip` 安装pip     
  `pip install --user ansible` 安装ansible。     
###### docker架设一个服务器
  `docker pull ubuntu` 
  `docker inspect <container id> | grep "IPAddress"` 查看docker服务器的ip地址     
  `docker ps`查看container id    
  `docker run -p ip:端口 ubuntu tail -f` 用docker运行另外一个计算机，然服务器一直跑，tail -f就是让服务器一直跑。     
  服务器跑了之后，在打开另外一个终端，要设置好hosts文件和ansible.cfg文件，然后要登录docker容器。
  `docker exec -it <container-id> bash` 登录都容器。       
  `service ssh start` 开始ssh服务器   
  `apt update`更新软件 vu
  `apt install openssh-server` 安装ssh     
  `ssh docker@172.27.0.2 -p 32805` 链接容器    
```
  //在容器里面
  useradd -rm -d /home/ubuntu -s /bin/bash -g root -G sudo -u 1000 test
  echo 'test:test' | chpasswd    //创建账户test和密码是test
```
  ` ssh docker@ip -p prot`连接docker      
  `ssh 用户名@主机名 -p 端口` # eg ssh docker@localhost -p 32805
  # 用户名是指想用什么用户名称登录到远程服务器。
  # 主机名可以是本机主机的名称（localhost），或者其他名称比如www.google.comd的google的主机名，或者主机的ip地址， 具体看使用那中主机要去登录。
  # -p是指要登录到的远程主机的端口。
  # 这个命令是使用ssh登录远程服务器的。
  # 在使用ssh到时候，机器上会记录远程服务器的一个id，如果服务器地址没有变，但id变了，ssh就会报错。
  # 这是因为这样就很有可能有人在利用这个地址造假，然后窃取信息，但是每次启动一次doker容器，服务器的id就会变，但地址不变，这种情况
  # 只要删除保存在~/.ssh/knownhosts文件，然后在重新连接ssh就可以了。
```
server1 ansible_ssh_host=localhost ansible_ssh_port=32805 ansible_ssh_user=test ansible_ssh_pass=test

[local]
server1
//使用了useradd命令后，hosts文件修改内容。
```
ansible.fcg文件配置    
```
[defaults]

inventory = hosts
remote_user = docker
host_key_checking = False
```

playbook
---------------
```
---
- name: Play the template module
  hosts: all
  vars:
    dynamic_word: "World, Silence"


  tasks:
    - name: generation the hello_world.txt file
      ansible.builtin.template:
        src: /home/solitude/playbooks/hello_world.txt.j2
        dest: /home/ubuntu/hello_world.txt
        mode: 774
        owner: test
        group: root

```
- 什么是hosts（属于ansible的playbook的知识点，hosts是自己写的）
  ansible会给每个服务器起一个内部名字。比如起个server1名字。        
  hosts是指目标服务器。hosts: server1。     
  如果hosts的值是单一服务器的内部名称，那么就只对这一台服务器进行操作。   
  服务器组是指有多个服务器组成的。 比如 服务器组名local，local有server1 server2两个服务器。 
  如果hosts的值是服务器组的名称，那么就是对这个服务器组里面所有的服务器进行操作。      
  如果hosts的值是all的话，就是对所有服务器进行操作。      

- src和dest    
  src：是指要获取文件的路径，包含文件的名字和后缀。    
  dest: 要把文件放在远程计算机那个文件夹里的路径，但必须要包含文件的名字和后缀。    

- linux目录    
  每个用户都有一个家目录。每个用户的个人文件都存放家目录下面。    
  一般家目录的路径规则是:/home/<用户名>    
  root的家目录是/root。    

- Linux文件权限    
  - linux里面每个文件都有所属的用户；所属的用户组还有权限。    
  - 所属的用户表示这个文件属于那个用户。    
  - 所属的用户组表示这个文件属于哪个用户组。    
  - 权限是3个8进制数字。    
   - 分别表示：所属用户有什么权限，所属用户组有什么权限，其他人有什么权限。    
   - 4表示可读，2表示可写，1表示可执行。如果同时可读可写，那就是4 + 2 = 6，如果同时可读可写可执行，那就是4 + 2 + 1 = 7    
   - 640表示，所属的用户有6 = 4 + 2可读和可写的权限，所属的用户组有4可读权限，其他人什么权限都没有。    
   - 755表示，所属的用户有7 = 4 + 2 + 1可读可写可执行的权限，所属用户组有5 = 4 + 1可读和可执行的权限，其他人有5 = 4 + 1可读和可执行的权限。    
   - 0640的0是指文件，1是指文件夹。    
- owner, group和mode
  - owner = 远程的所属的用户；group = 远程所属的用户组；mode = 权限。    
  - 用groups可以查到当前用户的用户组。 eg. groups 所属的用户。    

登录队长给服务器的hosts设置    
---------------------------------
```
[servers]
servers1 ansible_host=159.69.247.69

[all:vars]
ansible_python_interpreter=/usr/bin/python3
```
