# Git & Github Essential Turorial
Git Basic Concept
---
![image](https://hackmd.io/_uploads/BydWlTu56.png)
![image](https://hackmd.io/_uploads/BJG4TVsqa.png)

1.Download Git & Register Github
---
website: https://git-scm.com/downloads
website: https://github.com/

2.Build Github Repositories
---
.gitignore和license選自己喜歡的就好
![image](https://hackmd.io/_uploads/B1HCFauq6.png)

3.Build Git control
---
(1)cd到該資料夾位置，建立版本控制:`$ git init`，同時產生隱藏檔.git。
(2)停止版本控制:`$ rm -r .git`
(3)保持好習慣，常檢查資料庫: `$ git status`
![image](https://hackmd.io/_uploads/Skf6IHj9p.png)

4.Set Git Configuration
---
$ git config
(1)列出目前組態設定：`$ git config --list`
(2)設定使用者名稱:`$ git config --global user.name
<user_name>`
(3)設定使用者信箱:`$ git config --global user.mail <user_mail>`
(4)連接至github Repositories:`$ git remote add origin <git_reepository_url>`
(5)檢查與github連接情況:$`git remote -v`
![image](https://hackmd.io/_uploads/HkCCiro9a.png)

![image](https://hackmd.io/_uploads/rk9xhBi56.png)


5.Track Files
---
將檔案交給git追蹤:`$ git add <file_name>`
追蹤所有檔案:`$ git add .`
add前
![image](https://hackmd.io/_uploads/HJJ8hro5a.png)
add後
![image](https://hackmd.io/_uploads/SJ2QhSj96.png)

6.Submit Files & Upload to Github
---
(1)提交檔案版本:`$ git commit -m "<version_name>"`
![image](https://hackmd.io/_uploads/Bkp53Hsq6.png)
提交後，檢查status，空的表示提交成功
![image](https://hackmd.io/_uploads/ryS33Bi9a.png)
(2)push至github:`$ git push`
`$ git push -u <node_name> <branch_name>`，ex: `$ git push -u origin master`
![image](https://hackmd.io/_uploads/BJhrTHicp.png)

![image](https://hackmd.io/_uploads/Syvuaro56.png)

(3)查看版本紀錄:`$ git log`，更簡潔:`$ git log --oneline`
![image](https://hackmd.io/_uploads/S179aHjqp.png)
若有退回版本，需要使用`$ git reflog`查看
(4)從github下載檔案:`$ git clone <git_repository_url>`
(5)若github上的版本，有人commit後，要更新本地檔案:`$ git pull`
$ git pull = $ git fetch + $ git merge
可以看到test1.txt本地為123，變更為github上的1234
![image](https://hackmd.io/_uploads/BJGSRBj96.png)

![image](https://hackmd.io/_uploads/H1BwRSi9a.png)
(6)刪除remote數據庫資料，不刪除local端資料: `$ git rm <file_name>`
`$ git commit -m 'rm <file_name>'`
`$ git push`

7.Branch
---
分支可視為整個檔案的不同版本
(1)檢查分支:`$ git branch`
(2)建立分支:`$ git branch <branch_name>`
(3)刪除分支:`$ git branch -d <branch_name>`
(4)切換分支:`$ git checkout <branch_name>`
(5)建立並切換目錄至新分支:`$ git checkout -b <branch_name>`
(6)切換到最新版本:`$ git checkout master`

8.Reset File Content
---
(1)還原至指定commit:`$ git reset <commit>`
![image](https://hackmd.io/_uploads/rJQ-btoca.png)
(2)還原檔案內容:`$ git checkout -- <file_name>`
(3)檢視檔案改變內容:`$ git diff <commitA> <commitB>`
![image](https://hackmd.io/_uploads/H1fqCOo5p.png)
並且reset又可分為以下三種模式
![image](https://hackmd.io/_uploads/B1rqbKs96.png)
(4)只還原指定版本指定檔案:`$ git checkout <commit> <file_name>`
(5)還原所有檔案:`$ git reset --hard <commit>`

9.Reset File state
---
git的檔案可以同時處在兩種狀態，先將檔案改成12345後`$ git add`，在修改檔案為123456，並用檢查
![image](https://hackmd.io/_uploads/SJIu3djcp.png)

(1)還原指定檔案狀態:`$ git reset HEAD <file_name>`
(2)清空Changes not staged for commit和Changes to be committed區塊: `$ git reset --hard HEAD`

10.Rebase、Merge
---
HEAD指向目前所在分支，前面的checkout <commit>和check <branch>，其實都是在移動HEAD。
開發時，會以主要分支為主，所以在確認測試檔功能正常後，要將測試分支加回master。
branchA和branchB都是master衍生，現在將branchB合併至branchA上，移至branchB輸入以下指令
Rebase可以理解成將當前branch重新定義基準:`$ git rebase  <branchA>`
Merge雖然功能類似，但是會增加一個額外的commit:`$ git merge <branchA>`

11.Set untracked files
---
(1)將不想追蹤檔案名稱加入.gitignore中

Summary
---
(1)檢查git:`$ git status`、`$ git log`、`$ git remote`、`$ git branch`
(2)設定branch和commit並上傳github:
設定branch:`$ git checkout <branch_name>`
加入追蹤:`$ git add .`
設定版本:`$ git commit -m '<version_name>'`
上傳github:`$ git push`
(3)回復指定版本和更新為github上版本
移至指定branch:`$ git checkout <branch_name>`
跳至指定commit:`$ git reset <commit>`
還原檔案:`$ git checkout <file_name>`
更新為github上版本:`$ git pull`

Reference
---
[曼曼來比較快_Git 版本控制](https://https://ithelp.ithome.com.tw/users/20139195/ironman/4770)
[Git教學：如何 Push 上傳到 GitHub](https://gitbook.tw/chapters/github/push-to-github)
[【Git】從零開始學習 Git - 30 天的學習筆記](https://ithelp.ithome.com.tw/articles/10280729)
[30天精通Git版本控管](https://ithelp.ithome.com.tw/users/20004901/ironman/525)
[[Git][教學]](https://progressbar.tw/posts/3)
[Day13- git/github操作](https://medium.com/tsungs-blog/day13-git-github%E6%93%8D%E4%BD%9C-304ad94a1c6a)
[git上传linux文件到GitHub上](https://www.cnblogs.com/chen8023miss/p/12082093.html)
[[第一週]版本控制與 Git 基本指令](https://miahsuwork.medium.com/%E7%AC%AC%E4%B8%80%E9%80%B1-%E7%89%88%E6%9C%AC%E6%8E%A7%E5%88%B6%E8%88%87-git-%E5%9F%BA%E6%9C%AC%E6%8C%87%E4%BB%A4-fa3c4ba286a2)
[Git 與 Github 版本控制基本指令與操作入門教學](https://blog.techbridge.cc/2018/01/17/learning-programming-and-coding-with-python-git-and-github-tutorial/)