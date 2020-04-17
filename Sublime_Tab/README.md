安装完成Sublime之后，Tab快捷键失效的解决方法
<h3> Sublime Text提示'Unable to download XXX. Please view the console for more details.'安装插件失败解决 </h3>
<p>首先，在<a href="https://www.sublimetextcn.com/" target="_blank">Sublime Text官网</a>下载软件。</p>
<p>打开软件新建保存为html文件，按照网上教程，在文件内可以快速确定HTML骨架，只需要输入html:5或!然后按下Tab键即可自动生成，但是在实际操作的过程中，Tab键却没有作用，无法进行代码自动补全。</p>
<p>搜索后发现是Sublime Text需要安装Emmet插件，按下Command+Shift+P调出搜索框，安装install；</p>
<p>然后在搜索框输入Emmet准备安装插件，却出现了标题所述的报错，在搜集了目前网上给出的解决方案之后，选择了一个非常简单易行的办法。</p>
<p>1.打开Sublime Text，Preferences ->Package Settings->Package Control->Settings-User,在文件中添加以下几行代码：  
"downloader_precedence":<br />
{<br />
    	"linux": [ "curl", "urllib",    "wget" ],<br />
    	"osx": [ "curl", "urllib" ],<br />
    	"windows": [ "wininet" ]<br />
    },<br />
</p>
<p>2.重启Sublime Text，问题解决</p>
<p>3.打开搜索框，输入html，选择语法格式“Set Syntax:HTML”</p>
<p>原文可见：<a href="https://github.com/wbond/package_control/issues/1220" taget="_blank">Github Issue</a></p>
