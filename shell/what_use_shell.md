# Shell

### 爲什麽要使用shell脚本？
 由於一直要手動輸入命令，但是命令多了容易亂，輸入錯誤或者命令過於長容易忘記， 所以使用shell脚本來解決問題。    

### 什麽是shell脚本？
 shell脚本是為shell編寫的脚本程序，一般後綴名是.sh，運行這個shell脚本，那麽系統會使用shell解釋器來運行脚本裏面的内容。        
 shell是一個程序，而bash是這個shell的解釋器（Linux默認的shell解釋器）。    

### 要怎麽使用shell脚本？
 先創建一個名爲start.sh文件。然後在裏面添加下面的内容。    
```
#!/usr/bin/env bash  

docker compose up -d
```
這裏是#!是告訴系統在後面的路徑裏指定的shell解釋器來運行下面的`docker compose up -d`命令。    
上面的例子是告訴系統去usr/bin/env裏找一個名字叫bash的解釋器來運行命令。
