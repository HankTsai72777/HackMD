# SSH Workstation on Visual Studio Code
1.Download Visual Studio Code
---
website:https://code.visualstudio.com/<br/>

2.Download Remote-SSH<br/>
---
下載擴充功能Remote-SSH<br/>
![image](https://hackmd.io/_uploads/HyRWTcs9p.png)<br/>

3.Log in
---
設定SSH設定檔，Host自訂，Hostname為IP，User為帳號名稱<br/>
![image](https://hackmd.io/_uploads/rycowDxha.png)<br/>

![image](https://hackmd.io/_uploads/Sy-6Dvl2a.png)<br/>

![image](https://hackmd.io/_uploads/Skappqs96.png)<br/>

4.Generate Keys
---
(1)Press <win+R><br/>
(2)Open cmd<br/>
![image](https://hackmd.io/_uploads/Sk8N95icT.png)<br/>
(3)Generate keys:`ssh-keygen -t rsa`，輸入後一直Enter<br/>
![image](https://hackmd.io/_uploads/HyZBs5j5T.png)<br/>
(4)產生檔案如下<br/>
![image](https://hackmd.io/_uploads/By8qs5iq6.png)<br/>

5.Log in without password
---
(1)在工作站建立authorized_keys檔案<br/>
Build directory .ssh: `mkdir .ssh`<br/>
cd至.ssh: `cd .ssh`<br/>
Build file authorized_keys: `touch authorized_keys`<br/>
![image](https://hackmd.io/_uploads/SyTnnFZhp.png)<br/>


![image](https://hackmd.io/_uploads/ry2-Xug2T.png)<br/>
(2)Copy public key to file authorized_keys<br/>
![image](https://hackmd.io/_uploads/HyyKcvx2a.png)<br/>
(3)Revise config<br/>
![image](https://hackmd.io/_uploads/BJw2UOgnT.png)<br/>
<font color="#f00">特別注意:</font>若其他使用者或資料夾的權限過大，系統可能因此判斷對應金鑰不安全，無法免密碼登入。<br/>
解決方法: 修改.ssh和authorized_keys的權限<br/>
Revise permission: `chmod <user><group><other> <file or dicrectory>`<br/>
Check permission: `ll -d <file or directory>`<br/>
![image](https://hackmd.io/_uploads/r11IUulnT.png)<br/>
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
(1)Download Remote X11 & Xming<br/>
載點: https://sourceforge.net/projects/xming/<br/>
![image](https://hackmd.io/_uploads/Bk2Z00-h6.png)

![image](https://hackmd.io/_uploads/Skiilug2p.png)<br/>
(2)Revise config<br/>
![image](https://hackmd.io/_uploads/BkWt-_lh6.png)<br/>
(3)開啟Xming<br/>
![image](https://hackmd.io/_uploads/r1n2aRZ2T.png)<br/>

![image](https://hackmd.io/_uploads/SyXFCCb3a.png)<br/>

![image](https://hackmd.io/_uploads/r1X5A0bna.png)<br/>

![image](https://hackmd.io/_uploads/ByziAAZnT.png)<br/>
(4)即可在vscode直接開啟nWave等tools<br/>
![image](https://hackmd.io/_uploads/rJ8G6R-np.png)

7.MobaXterm
---
題外話,如果習慣使用MobaXterm的話，只需要以下設定，即可免密登入<br/>
包括: Remote host, Specify username, Use private key<br/>
![image](https://hackmd.io/_uploads/B1LIMCgna.png)<br/>
修改Settings預設編輯軟體，即可透過vscode進行編輯。<br/>
![image](https://hackmd.io/_uploads/ryolmAx26.png)<br/>
