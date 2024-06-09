# 学习Git遇到的错误记录和解决方法
## push常见的错误
* error: failed to push some refs to '
  1.解决方法是  
    1.1.想把本地完全强制推送过去就git push origin main -f  
    1.2.如果想与远程代码合并，那就git pull origin main合并代码，然后再推送。  

* 如果GitHub出现身份或者密码已经过期：
  1.解决方法是  
    先去GitHub账户中，选择设置->开发人员设置->个人访问令牌->生成新令牌->然后填写表单->单击生成令牌->复制生成的令牌。  
    然后根据不同的系统进行操作：  
      windows：  
      从控制面板转到凭据管理器->Windows Credentials ->查找->编辑->密码替换为GitHub 个人访问令牌->完成   git:https://github.com  
      如果您没有找到->单击"添加通用的Credentials->Internet 地址，您需要输入您的用户名和密码将是您的GitHub 个人访问令牌->单击"确"，  
      您就完成了git:https://github.comgit:https://github.com。  
      linux:  
      对于 Linux，您需要使用用户名和电子邮件地址配置本地Git：  
      ```
        $ git config --global user.name "your_github_username"
        $ git config --global user.email "your_github_email"
        $ git config -l
      ```
      配置 GIT 后，我们可以开始使用它来访问 GitHub.如果你在git命令没有弹出提示输入用户名和密码   
      那么就要使用：   
      ```
        $ git config --global --unset credential.helper
        $ git config --system --unset credential.helper
      ```
        来删除缓存记录。   
        可以使用 `$ git config --global credential.helper cache`让计算机记住令牌。  
  
* 出现fatal: ‘origin‘ does not appear to be a git repository fatal: Could not read from remote的错误  
  当add和commit都可以，唯独push不行，主要的原因是链接不上，本地链接和远程分支断开链接了，要重新链接就可以了。   
  1.查看情况  
    可以使用`git branch -v`这个命令查看分支的情况。   
    `git remote -v`查看是不是断开链接，如果没有断开就会显示，看是不是显示错误。如果断开的话就不会显示任何内容。   
  2.解决方法  
    2.1.如果是断开链接可以如下操作  
      在gitHub（或者其它）中链接仓库    
        使用`git remote add origin https（或者其它）：地址`。   
        使用`git remote -v`检查远程仓库是否是对应地址。  
        使用`git branch -v`检查分支是否正确，需要切分支就可以切到你要的分支。  
        都正确就可以push上去就好了。  
    2.2.如果是链接错误  
      使用`git remote -v`来查看仓库信息  
      然后使用`git remote remove origin`来删除远程仓库链接  
      `git remote add origin 仓库`来重新添加远程仓库。  
      然后push就可以了。  

* error: failed to push some refs to xxx   
  1.出现这种错误可以很大概率是手动修改了远程仓库中的文件，导致一些文件在本地仓库和远程仓库上不一致导致的错误  
  2.解决方法：  
    使用`git pull --rebase origin main`将远程仓库同步到本地，然后重新add, status, commit, push就可以了。  