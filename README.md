# xcode_autobuild

* 因为公司最近人员变动，只有我一个人懂iOS开发，有时不在公司又遇到需要给测试装包比较烦，所以借助现有的一个[Python](https://github.com/carya/Util) 自动打包 + 上传到蒲公英应用分发平台 脚本，自己加了一层applscript小脚本，可以通过邮箱来控制mac调用appleScript来执行shell命令行，进而执行自动打包脚本。能够完成自动编译 + 打包 + 清除中间文件 + 上传到蒲公英应用分发平台。
 
### AppleScript 远程操控Mac
         AppleScript是macOS下的脚本语言，可以使用苹果自带的Applescript编辑器进行编辑，虽然停止更新了，但还是蛮简单易用的，而且和程序结合比较方便。关于AppleScript的基础知识这里有一篇[简单的介绍](http://blog.csdn.net/jymn_chen/article/details/19755895)。关于如何遥控Mac这位朋友的[文章](http://sspai.com/35799)说的也比较明白。
         
### XCode命令行打包
        xcode提供了xcodebuild命令给我们来通过命令行进行程序编译，也提供了xcrun命令进行打包，[这里](http://liumh.com/2015/11/25/ios-auto-archive-ipa/#script-build)详细介绍了这两种命令的参数及打包脚本的工作流程和方法。
### AppleScript执行打包脚本
我在脚本中只做了两件事情：
* cd到工程根目录。
* 执行自动打包脚本。
       Applescript是通过do shell script "$(shell string)"来执行shell命令行的。 每个do shell script 语句相当于开启一个新的终端线程。需要执行多条命令行时写在同一个do shell 语句中，中间用“;”进行间隔。

set HOME_PATH to "/Users/Projects/"
set PROJECT_PATH to HOME_PATH & "paipai360/app/ios_1211/paipai360_v2.0/paipai360-2"

set SHELL_LOCATION to "cd " & PROJECT_PATH
log SHELL_LOCATION


set SHELL_BUILD_WITH_PYTHON to "./autobuild.py -p paipai360-2.xcodeproj -t paipai360-2 -o /Users/rrty/Desktop/abcd.ipa"
log SHELL_BUILD_WITH_PYTHON

do shell script SHELL_LOCATION & "; " & SHELL_BUILD_WITH_PYTHON
        
### 使用方法			
        使用时将autobuild.py中的参数按照要求修改完后，									
