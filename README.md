# xcode_autobuild

* 因为公司最近只有我人懂iOS开发，有时不在公司又遇到需要给测试装包比较烦，所以借助现有的一个[Python](https://github.com/carya/Util) 自动打包 + 上传到蒲公英应用分发平台 脚本，我自己加了一层applscript小脚本，可以通过邮箱来调用appleScript来执行shell命令行，进而执行自动打包脚本。能够完成自动编译 + 打包 + 清除中间文件 + 上传到蒲公英应用分发平台。
