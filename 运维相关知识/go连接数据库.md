# 使用go语言连接数据库

启动mariadb的镜像    
----------------------------
`docker run --name some-mariadb --env MARIADB_ROOT_PASSWORD=密码  mariadb:latest` 使用docker安装mariadb    
`docker run  -p 3306:3306  --env MARIADB_ROOT_PASSWORD=密码 mariadb` //运行容器映射mariadb端口。      
`--env`的功能是设置环境变量，格式是--env 环境变量=值，以上的荔枝环境变量叫 MARIADB_ROOT_PASSWORD 这是mariadb的镜像规定的变量，这样    
mariadb镜像就可以读取这个变量来设置root密码。    

连接数据库命令    
--------------------------
`mysql -hlocalhost -P3306 -uroot -p密码 --protocol tcp` 连接数据库 这里登录的密码是指mariadb容器的密码一样。    
登录成功后便可以创建数据库和表。
要注意的是，在创建表属性的时候，指定主键的语句要在被指定的属性后边。例如下面：   
```
create table students(
	user_id INT NOT NULL AUTO_INCREMENT,
	PRIMARY KEY (user_id),
	username VARCHAR(100) NOT NULL,
	sex VARCHAR(40) NOT NULL,
	email VARCHAR(100) NOT NULL		
);     创建表时，主键primary key要放在要设定的主键下面。
```

什么是sqlx库和driver库       
--------------------------
sqlx库是go语言内置的连接数据库的库。     
driver包定义了应被数据库驱动实现的接口，这些接口会被sqlx包使用。    

安装sqlx库：    
在go项目中使用`go get github.com/jmoiron/sqlx`来安装这个库。    
并在import里面引用这个`"github.com/jmoiron/sqlx"`包。    

安装driver库：    
在go项目中使用`go get -u github.com/go-sql-driver/mysql`来安装这个库。    
并在import里面引用`_ "github.com/go-sql-driver/mysql"`包。    
在包前的`_`是表示只调用包里面的 init 函数。无法调用包中别的函数。    

```go
package main

import (
	"fmt"

	_ "github.com/go-sql-driver/mysql"

	"github.com/jmoiron/sqlx"
)
//创建一个结构
type Persion struct {
	UserId   int    `db:"user_id"`
	Username string `db:"username"`
	Sex      string `db:"sex"`
	Email    string `db:"email"`
}

//创建一个全局变量的数据库对象
var Db *sqlx.DB

func init() {
	//Open函数返回值一个返回值是连接好的数据库对象，另一个返回值是连接时出现的错误。如果错误err不为空，否则为空。这是go语言的错误处理机制。
	//连接数据库
	database, err := sqlx.Open("mysql", "root:test@tcp(localhost:3306)/test")
	//nil是go语言里的零值
	if err != nil {
		fmt.Println("打开数据库失败， err: ", err)
		return
	}
  
	//初始化数据库
	Db = database

}

func main() {
	//Exec函数可以执行数据库的insert, update, delete命令。
	//返回的是修改好的集，和是否修改成功。
	r, err := Db.Exec("insert into students (username,sex,email) value(?,?,?)", "stu02", "girl", "stu01@qq2.com")

	if err != nil {
		fmt.Println("修改失败，err:", err)
		return
	}

  //获取插入数据的Id
	id, err := r.LastInsertId()

	if err != nil {
		fmt.Println("修改失败，err:", err)
		return
	}

	fmt.Printf("修改成功，修改了第%d个数据", id)

}

```


