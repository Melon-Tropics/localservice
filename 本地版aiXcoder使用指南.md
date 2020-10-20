# 本地版aiXcoder使用指南

本地版aiXcoder是一个AI驱动的代码提示工具。支持的编程语言有Java和Python。支持的编辑器有IntelliJ IDEA，Eclipse，PyCharm，Android Studio和Visual Studio Code（简称VS Code）。
aiXcoder提供代码提示和代码搜索两个主要功能。

各种功能的详细介绍请参考： https://aixcoder.com/#/Product?tab=1

## 在线安装

请参考我们的本地版下载页面： https://aixcoder.com/#/local

或者从插件市场下载 [IntelliJ](https://plugins.jetbrains.com/plugin/13574-aixcoder-ai-completion/), [Eclipse](https://marketplace.eclipse.org/content/aixcoder-ai-code-completer), [VS Code](https://marketplace.visualstudio.com/items?itemName=aixcoder-plugin.aixcoder&ssr=false#overview).

插件在安装之后，第一次启动IDE或激活插件的时候会自动下载本地服务。

## 离线安装

aiXcoder本地版分为两个部分，一个是插件，一个是服务程序。

### 第一步：下载插件

插件是安装到您的IDE或编辑器，您可以根据您的IDE或编辑器的种类，在这里下载插件的安装包：

[IntelliJ](https://plugins.jetbrains.com/plugin/13574-aixcoder-ai-completion/)、[Eclipse](https://marketplace.eclipse.org/content/aixcoder-ai-code-completer)、[VS Code](https://marketplace.visualstudio.com/items?itemName=aixcoder-plugin.aixcoder&ssr=false#overview)


### 第二步：下载服务

https://github.com/aixcoder-plugin/localservice/releases

在这里可以找到我们最新的版本。下载对应的server-win.zip（x64 Windows 7及以上），server-osx.zip（Mac OS X）或server-linux.tar.gz（在Ubuntu 18.04LTS上测试过）。

### 第三步：安装插件

IDEA/PyCharm/Android Studio：

**不要解压下载下来的zip文件！**

![File Settings Plugins Install plugin from disk](https://github.com/aixcoder-plugin/localservice/raw/master/idea-install-zip.png)

VS Code：

![Extensions tab Install from VSIX](https://github.com/aixcoder-plugin/localservice/raw/master/vscode-install-vsix.png)

Eclipse 安装需要将jar拷贝到Eclipse安装目录的dropins文件夹下：

![复制 jar 到 dropins 文件夹](https://github.com/aixcoder-plugin/localservice/raw/master/eclipse-installed.png)

### 第四步：安装服务

将下载下来的压缩包解压，把里面的文件放到以下目录，您需要手动创建这些中间目录。


Windows

`%UserProfile%\aiXcoder\installer\localserver\current\server`

通常来说，这个目录是：

`C:\Users\<用户名>\aiXcoder\installer\localserver\current\server`

```powershell
# 在PowerShell里可以用这个命令解压到目的地址：
Expand-Archive "server-win.zip" -DestinationPath "%UserProfile%\aiXcoder\installer\localserver\current\server"
```

***

Mac OS X

`~/Library/Application Support/aiXcoder/installer/localserver/current/server`

`~/Library`这个目录通常是隐藏的，您可以在访达（Finder）的顶端菜单栏的“前往”->"前往文件夹"中输入`~/Library/Application Support`以访问这个目录。

```sh
# 在终端(Terminal)中可以用这个命令解压到目的地址：
unzip server-osx.zip -d "~/Library/Application Support/aiXcoder/installer/localserver/current/server"
```

有的浏览器（比如Safari）会自动解压缩这个zip文件到`server-osx`目录。请注意，**该目录底下存在隐藏文件**。想要拷贝包含隐藏文件的所有文件到指定目录，可以运行这个命令：

```sh
# 在终端(Terminal)中可以用这个命令复制当前文件夹下的所有文件到目的地址：
mkdir -p "~/Library/Application Support/aiXcoder/installer/localserver/current/server"
cp -R . "~/Library/Application Support/aiXcoder/installer/localserver/current/server"
```

***

Linux

`~/aiXcoder/installer/localserver/current/server`

```sh
# 在Shell终端中可以用这个命令解压到目的地址：
tar xf server-linux.tar.gz -C "~/aiXcoder/installer/localserver/current/server"
```

如果一切顺利，服务安装后应该是这样的：

![aixcoder.bat 在 server 目录里](https://github.com/aixcoder-plugin/localservice/raw/master/local-installed.png)

## 疑难解答

### 装上之后似乎没有效果

导致这个现象的原因有很多，我们可以一一排查：

* 原因零：**你用的语言、IDE或操作系统不受支持**
  本地版目前仅支持Java语言，编辑器只支持IntelliJ IDEA，Eclipse，Android Studio，Visual Studio Code。操作系统要求是64位的Windows 7或以上、Mac OS X或有GUI的Linux（比如Ubuntu）。推荐使用Intel的i5或更好的CPU。
* 原因一：**插件没安装上**
  如果插件安装成功，打开设置页面搜索aiXcoder可以找到相应的设置页面。如果找不到这个页面，那就是插件没有安装上。
* 原因二：**本地服务没有下载/解压成功**
  启动IDE的时候插件会自动检查更新并下载最新的本地版服务。你可以在IDE看到一个下载的进度条。下载完成之后本地服务才会启动。
  本地服务会解压到这个目录里：
    * Windows: `C:\Users\<用户名>\aiXcoder\installer\localserver\current\server`
    * Mac OS X: `~/Library/Application Support/aiXcoder/installer/localserver/current/server`
    * Linux: `~/aiXcoder/installer/localserver/current/server`
  如果这个目录里文件很少的话（少于23个），那就是解压没有成功。这可能是权限或磁盘空间导致的，可以考虑手动下载安装一下试试。
* 原因三：**本地服务没有启动**
  一般来说打开编辑器，一写代码，提示框弹出的时候本地服务就会自动启动了。如果没有启动的话，到“原因三”的目的目录中找到aixcoder.bat或aixcoder.sh，直接执行，也许能看出问题在哪。

如果还有问题的话，加入我们的qq群（892015062），或者直接在 [aiXcoder Issue Tracker](https://github.com/aixcoder-plugin/issue-tracker) 中提交问题，我们将尽快处理与解决这些 Issues。
