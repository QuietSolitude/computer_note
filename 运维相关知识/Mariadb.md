# Mariadb
* 学习Mariadb笔记。

###### 安装与卸载
  使用dockers安装：`docker run --name some-mariadb --env MARIADB_ROOT_PASSWORD=my-secret-pw  mariadb:latest //密码是my-secret-pw` --env的功能是设置环境变量。  格式是--env 环境变量=值  环境变量名称叫做MARIADB_ROOT_PASSWORD，翻译过来就是mariadb root 密码。       
  这是mariadb的镜像规定的变量。  mariadb的镜像就靠读取这个环境变量来设置root密码。    
  `docker ps -a //查看内容`    
  `docker system prune -a -f //清理docker`    
  `docker pull mariadb:latest //下载但是不安装mariadb的镜像。`        
  `sudo apt-get purge mariadb-server //卸载mariadb`      

###### Mariadb命令
  `mysql -uroot -pmy-secret-pw --protocol tcp //连接Mariadb. --protocol tcp是改变网络协议，默认是socket改为TCP` 
  `mysqldump -uroot -pmy-secret-pw --protocol tcp 要备份的数据库 > 备份数据库.sql//备份`       
  `mysql -u用户名 -p密码 --protocol tcp 要恢复的数据库 < 备份数据库.sql`恢复数据库    
  `show databases; //显示所有数据库`     
  `use 数据库名/表名; //使用数据库/表`     
  `show tables; //显示所有的表`    
  `desc 表名; //显示表的基础字段属性和约束`          
  `create database 数据库名; //创建一个数据库`     
  
```
create tabale 表名(,, )engine=innodb charset=字符编码 comment '备注信息'

// create table test(id int primary key auto_increment, name varchar(50))engine=innodb charset=utf8 comment 'this is a test';
// id类型是int,是主键，自动递增
```
`show create table 表名 //查看表的建表信息`     
增加`insert  into 表名(字段) values(字段的  值); // insert into test(name) value('sss')`     
更改`update 表名 set 字段的属性='xxxx' where 对应的元素；//update test set name='silence' where id=1;`  
查找`select 要查的元素/* from 表名;(\G) //查询单个字段/或所有的字段 如果分号换成\G是将字段纵向显示`     
删除`delete from 表名 where 要删除额字段 //delete from test where id=1`       


`docker run  -p 3306:3306  --env MARIADB_ROOT_PASSWORD=密码 mariadb` //运行容器映射mariadb端口。     
`mysql -hlocalhost -P3306 -uroot -p密码 --protocol tcp` 连接数据库 


```
create table students(
	user_id INT NOT NULL AUTO_INCREMENT,
	PRIMARY KEY (user_id),
	username VARCHAR(100) NOT NULL,
	sex VARCHAR(40) NOT NULL,
	email VARCHAR(100) NOT NULL		
);     创建表时，主键primary key要放在要设定的主键下面。
```