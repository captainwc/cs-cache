# windows下vscode设置C++环境

> 教程来源于网络多方面搜集，经过本人执行总结出一条较为简单的路径

## 一、软件准备

vscode：

windows power shell：微软商店

mingw：[https://sourceforge.net/projects/mingw-w64/files/Toolchains%20targetting%20Win64/Personal%20Builds/mingw-builds/8.1.0/threads-posix/sjlj/x86_64-8.1.0-release-posix-sjlj-rt_v6-rev0.7z/download](https://sourceforge.net/projects/mingw-w64/files/Toolchains targetting Win64/Personal Builds/mingw-builds/8.1.0/threads-posix/sjlj/x86_64-8.1.0-release-posix-sjlj-rt_v6-rev0.7z/download)

因为vscode只是一个编辑器而不是ide，要想运行c++代码需要提供一个编译环境。这个的下载比较慢，后面我会传到百度网盘上。

## 二、软件配置

### mingw

选择一个文件夹解压，相当于安装位置，然后复制其中bin文件夹的路径。

从控制面板进入系统和安全->系统，选择高级系统设置，点击下面的“环境变量”，选择“系统变量”下面的“Path”，点击编辑->新建，然后将刚复制的bin文件夹位置粘贴上去，一路点击确定退出。

此后在win+r运行cmd或直接在power shell下面，运行`gcc -v`命令，如果能出现版本信息，表示安装成功。

### windows power shell

运行程序后点击设置，会出现他的json文件，通过这个我们可以自己设置其外观，比如字体、大小、背景等。*这一步不是必须的*

由于Powershell默认禁止运行脚本，需要先开启权限。

在管理员模式下运行powershell，然后输入命令`set-ExecutionPolicy RemoteSigned`

#### 常用命令

一、更改默认位置

`echo "Set-Location D:\" > $Profile`

### vscode

首先需要安装几个插件，直接搜索，C/C++，code runer，run in terminal等

然后设置里搜索"code runner"，将“code-runner：run in terminal”和“code-runner：save file before run”勾选上。勾选后者主要是改动代码后可以直接运行，而不用先保存。

此时运行时powershell会出现微软的广告，下面可以将其去掉

打开文件`C:\Users\%username%\AppData\Roaming\Code\User\settings.json`，在其中加入一行代码

`"terminal.integrated.shellArgs.windows": ["-NoLogo"]`

然后在powershell中输入

`code C:\Users\%username%\Documents\WindowsPowerShell\Microsoft.PowerShell_profile.ps1`

在其中输入`clear`，保存文件即可。











































