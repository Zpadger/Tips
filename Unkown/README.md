解决Github图片无法加载的问题  
问题描述  
打开Github查看别人项目的时候，图片无法加载，甚至包括自己的Github头像，十分头疼。  

解决思路  
使用本地hosts文件对网站进行域名解析，一般的DNS问题都可以通过修改hosts文件来解决，Github的CDN域名被污染的问题也不例外，同样可以通过修改hosts文件来解决，将域名解析直接指向IP地址来绕过DNS的解析，以此解决域名污染问题。  
所以主要的思路就是首先找到hosts文件，然后添加上Github的域名IP映射。  
Mac如何解决？  
1.查找并打开hosts文件  
Mac的hosts文件路径为/tec/hosts  
首先打开Mac的Finder，然后使用快捷键Shift+Command+G，调出搜索对话框，路径填写/tec/hosts  
即可找到hosts文件，为了防止修改错误，记得首先备份一个hosts副本(这是一个好习惯，以后修改文件都要记住备份副本)  
但是在该路径下打开hosts文件可以看到文件已锁定，没有权限无法修改；所有可以将hosts文件复制到桌面进行编辑保存后，再替换原hosts文件，替换过程中需要输入一次管理员密码。  
2.在hosts文件中添加Github地址  
未修改前的hosts文件原内容应该是  
```
##
# Host Database
#
# localhost is used to configure the loopback interface
# when the system is booting.  Do not change this entry.
##
127.0.0.1	localhost
255.255.255.255	broadcasthost
::1             localhost
```
将以下内容复制粘贴到hosts文件中  
```
# GitHub Start
140.82.113.3      github.com
140.82.114.20     gist.github.com

151.101.184.133    assets-cdn.github.com
151.101.184.133    raw.githubusercontent.com
151.101.184.133    gist.githubusercontent.com
151.101.184.133    cloud.githubusercontent.com
151.101.184.133    camo.githubusercontent.com
151.101.184.133    avatars0.githubusercontent.com
199.232.68.133     avatars0.githubusercontent.com
199.232.28.133     avatars1.githubusercontent.com
151.101.184.133    avatars1.githubusercontent.com
151.101.184.133    avatars2.githubusercontent.com
199.232.28.133     avatars2.githubusercontent.com
151.101.184.133    avatars3.githubusercontent.com
199.232.68.133     avatars3.githubusercontent.com
151.101.184.133    avatars4.githubusercontent.com
199.232.68.133     avatars4.githubusercontent.com
151.101.184.133    avatars5.githubusercontent.com
199.232.68.133     avatars5.githubusercontent.com
151.101.184.133    avatars6.githubusercontent.com
199.232.68.133     avatars6.githubusercontent.com
151.101.184.133    avatars7.githubusercontent.com
199.232.68.133     avatars7.githubusercontent.com
151.101.184.133    avatars8.githubusercontent.com
199.232.68.133     avatars8.githubusercontent.com

# GitHub End
```   
如图所示  
![](.../Unkown/xiugai.png)
修改完成之后保存，然后将原hosts文件替换，重新打开Github，即可发现网页中的图片都可以正常加载了。
