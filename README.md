# AiXcoder Local User Guide

(中文版)[https://github.com/aixcoder-plugin/localservice/blob/master/%E6%9C%AC%E5%9C%B0%E7%89%88aiXcoder%E4%BD%BF%E7%94%A8%E6%8C%87%E5%8D%97.md]

AiXcoder Local is an AI-driven code completion tool. The supported programming languages ​​are Java and Python. IntelliJ IDEA, Eclipse, PyCharm, Android Studio, and Visual Studio Code (VS Code for short) are supported.

## Install online

Search "aiXcoder" on the plugin marketplace and install.

After the plugin is installed, the local service will be downloaded automatically when the IDE is started for the first time or when the plugin is activated.

## Offline installation

AiXcoder Local is divided into two parts, one is a plug-in, and the other is a background service.

Step 1: Download the plugin

The plugins is installed to your IDE or editor. You can download the installation package of the plugin here according to the type of your IDE or editor:

Download [IntelliJ](https://aixcoder.com/#/local), [Eclipse](https://aixcoder.com/#/local), [VS Code](https://marketplace.visualstudio.com/items?itemName=aixcoder-plugin.aixcoder&ssr=false#overview) plug-in packages.

Step 2: Download the background service

https://github.com/aixcoder-plugin/localservice/releases

You can find our latest version here. Download the corresponding server-win.zip (x64 Windows 7 and above), server-osx.zip (Mac OS X) or server-linux.tar.gz (tested on Ubuntu 18.04LTS).

Step 3: Install the plugin

IDEA/PyCharm/Android Studio：

**Do not unzip the downloaded zip file!**

![File Settings Plugins Install plugin from disk](https://github.com/aixcoder-plugin/localservice/raw/master/idea-install-zip.png)

VS Code：

![Extensions tab Install from VSIX](https://github.com/aixcoder-plugin/localservice/raw/master/vscode-install-vsix.png)

Eclipse requires you to copy the downloaded jar to "dropins" folder under Eclipse's installation folder：

![Copy jar to dropins folder](https://github.com/aixcoder-plugin/localservice/raw/master/eclipse-installed.png)

Step 4: Install the service

Unzip the downloaded compressed archive and place the files inside the following directories. You need to manually create these directories.

***

Windows

`%UserProfile%\aiXcoder\installer\localserver\current\server`

Generally speaking, this directory is:

`C:\Users\<User Name>\aiXcoder\installer\localserver\current\server`

```powershell
# In PowerShell, you can use this command to decompress to the destination folder:
Expand-Archive "server-win.zip" -DestinationPath "%UserProfile%\aiXcoder\installer\localserver\current\server"
```

***

Mac OS X

`~/Library/Application Support/aiXcoder/installer/localserver/current/server`

The directory `~/Library` is usually hidden. You can access this directory by typing`~/Library/Application Support` in the "Go"->"Go to Folder" of the top menu bar of Finder.

```sh
# In Terminal, you can use this command to decompress to the destination folder:
unzip server-osx.zip -d "~/Library/Application Support/aiXcoder/installer/localserver/current/server"
```

Some browsers (such as Safari) will automatically decompress this zip file to the `server-osx` directory. Please note that **Hidden files exist under this directory**. To copy all files containing hidden files to the specified directory, you can run this command:

```sh
# In Terminal, you can use this command to copy all files to the destination folder:
mkdir -p "~/Library/Application Support/aiXcoder/installer/localserver/current/server"
cp -R . "~/Library/Application Support/aiXcoder/installer/localserver/current/server"
```

***

Linux

`~/aiXcoder/installer/localserver/current/server`

```sh
# In the shell terminal, you can use this command to decompress to the destination address:
tar xf server-linux.tar.gz -C "~/aiXcoder/installer/localserver/current/server"
```

If everything is smooth, you should be able to see the installed service：

![aixcoder.bat inside server folder](https://github.com/aixcoder-plugin/localservice/raw/master/local-installed.png)

## Troubleshooting

### It seems to have no effect after installation

There are many reasons for this phenomenon, we can check them one by one:

* Reason 0: **Your language, IDE, or operating system is not supported**
  The local version currently only supports the Java language, and the editor only supports IntelliJ IDEA, Eclipse, Android Studio, and Visual Studio Code. The operating system requirements are 64-bit Windows 7 or above, Mac OS X, or Linux with a GUI (such as Ubuntu). It is recommended to use Intel i5 or better CPU.
* Reason 1: **The plugin is not installed**
  If the plugin is successfully installed, open the settings page and search for aiXcoder to find the corresponding settings page. If you cannot find this page, it is that the plugin is not installed.
* Reason 2: **Local service did not download / unzip successfully**
  When you launch the IDE, the plugin will automatically check for updates and download the latest local version of the service. You can see a download progress bar in the IDE. The local service will not start until the download is complete.
  The local service will be extracted into this directory:
    * Windows: `C:\Users\<User Name>\aiXcoder\installer\localserver\current\server`
    * Mac OS X: `~/Library/Application Support/aiXcoder/installer/localserver/current/server`
    * Linux: `~/aiXcoder/installer/localserver/current/server`
  If there are few files in this directory (less than 23), it is that the extraction was unsuccessful. This may be caused by permissions or disk space. You can consider manually downloading and installing it.
* Reason 3: **Local service is not started**
  Generally, when you open the editor and write the code, the local service will start automatically when the prompt box pops up. If it is not started, find the aixcoder.bat or aixcoder.sh in the destination directory of "Cause Three" and execute it directly. You may be able to see where the problem is.
  If you still have questions, e-mail us at support@aixcoder.com.
