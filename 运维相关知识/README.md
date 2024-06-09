## 运维知识点

 1. `ssh-keygen -t ed25519 -C //使用ssh命令生成ed25519密匙,生产的密匙必须保留或者备份。`
 2. `cat`命令是打开文件
 3. `ssh 用户名@ip //ssh root@23.88.45.151 使用ssh登录服务器` 
 4. `docker compose down //是停掉一批container，该命令是在有docker-compose.yml文件中使用`
 5. `cat scripts/restart-webserver.sh //来查看文件内容`
 6. `docker compose up -d webserver //启动container`
 7. `scp[本地文件][用户名]@[ip地址][远程路径] // scp text.txt root@ip-address:/root/text.txt`