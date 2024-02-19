# SSH Workstation on Visual Studio Code
1.Download Visual Studio Code
---
website:https://code.visualstudio.com/

2.Download Remote-SSH
---
下載擴充功能Remote-SSH
![image](https://hackmd.io/_uploads/HyRWTcs9p.png)

3.Log in
---
設定SSH設定檔，Host自訂，Hostname為IP，User為帳號名稱
![image](https://hackmd.io/_uploads/rycowDxha.png)


![image](https://hackmd.io/_uploads/Sy-6Dvl2a.png)

![image](https://hackmd.io/_uploads/Skappqs96.png)

4.Generate Keys
---
(1)Press <win+R>
(2)Open cmd
![image](https://hackmd.io/_uploads/Sk8N95icT.png)
(3)Generate keys:`ssh-keygen -t rsa`，輸入後一直Enter
![image](https://hackmd.io/_uploads/HyZBs5j5T.png)
(4)產生檔案如下
![image](https://hackmd.io/_uploads/By8qs5iq6.png)

5.Log in without password
---
(1)在工作站建立authorized_keys檔案
Build directory .ssh: `mkdir .ssh`
cd至.ssh: `cd .ssh`
Build file authorized_keys: `touch authorized_keys`
![image](https://hackmd.io/_uploads/r1qFsDg3p.png)

![image](https://hackmd.io/_uploads/ry2-Xug2T.png)
(2)Copy public key to file authorized_keys
![image](https://hackmd.io/_uploads/HyyKcvx2a.png)
(3)Revise config
![image](https://hackmd.io/_uploads/BJw2UOgnT.png) 
<font color="#f00">特別注意:</font>若其他使用者或資料夾的權限過大，系統可能因此判斷對應金鑰不安全，無法免密碼登入。
解決方法: 修改.ssh和authorized_keys的權限
Revise permission: `chmod <user><group><other> <file or dicrectory>`
Check permission: `ll -d <file or directory>`
![image](https://hackmd.io/_uploads/r11IUulnT.png)
| Dec | Read | Write | Execute | Binary |
| --- | ---- | ----- | ------- | ------ |
| 7 | v | v | v | 111 |
| 6 | v | v | x | 110 |
| 5 | v | x | v | 101 |
| 4 | v | x | x | 100 |
| 3 | x | v | v | 011 |
| 2 | x | v | x | 010 |
| 1 | x | x | v | 001 |
| 0 | x | x | x | 000 |

6.X server setting
---
(1)Download Remote X11
![image](https://hackmd.io/_uploads/Skiilug2p.png)
(2)Revise config
![image](https://hackmd.io/_uploads/BkWt-_lh6.png)

7.MobaXterm
---
題外話,如果習慣使用MobaXterm的話，只需要以下設定，即可免密登入
包括: Remote host, Specify username, Use private key
![image](https://hackmd.io/_uploads/B1LIMCgna.png)
修改Settings預設編輯軟體，即可透過vscode進行編輯。
![image](https://hackmd.io/_uploads/ryolmAx26.png)
