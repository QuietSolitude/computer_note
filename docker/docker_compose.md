# Docker Compose

### 爲什麽要使用docker compose？
 由於docker只能運行一個容器，想要運行多個容器的時候，docker滿足不了要求，所以使用docker compose。    

### 什麽是docker compose？
 Docker Compose是一個用於定義和運行多個容器的工具。    

### 如何使用docker compose工具？
 要使用docker compose這個工具，需要創建一個名為docker-compose.yml文件。    
 假設要運行數據庫MogoDB和對象存儲系統Minio， 可以在docker-compose.yml文件裏添加以下内容。    

```
services:              # 定義了docker需要運行的服務。

  

 database:  

  image: mongo:latest  # 是指要拉取的鏡像，這裏是mogo: latest鏡像和minio: latest鏡像。

  ports:               # 是指定義運行該容器的自定義端口。

   - 27017:27017

  environment:         # 是指定義環境變量。

   - MONGO_INITDB_ROOT_USERNAME=root

   - MONGO_INITDB_ROOT_PASSWORD=no-password

  

 objstorage:

  image: quay.io/minio/minio:latest

  ports:

    - 9000:9000

    - 9001:9001

  command: server /data --console-address ":9001"  # command是指運行該服務的命令。

  environment:

    - MINIO_ROOT_USER=root

    - MINIO_ROOT_PASSWORD=no-password

    - MINIO_DEFAULT_BUCKETS=devenv_test
```
保存好后，在當前文件裏使用`docker build`命令來構建這多個容器，    
儅構建完成后在使用`docker compose up`來運行所有的容器，若是在這個命令後面加上`-d`則容器會在後臺運行。    
使用`docker compose down`來停止運行所有容器。 
檢查容器那些運行可以是使用`docker compose ps`命令或者去docker app哪裏看。    
