# iOS逆向调试：Xcode+iOSOpenDev

* 最新版本：`v1.0.1`
* 更新时间：`20241126`

## 简介

介绍iOS逆向的动态调试期间的，常用的好用的调试方式：Xcode+iOSOpenDev。主要包括先是概览；再介绍为何要实现可调式debuggable；以及对应底层机制；以及如何实现可调试，包括用unc0ver、XinaA15等工具越狱后自带可调试、用codesign加上权限重签名、用jailbreakd_client加上权限等，以及用插件XcodeRootDebug等；然后介绍具体的调试方式，包括Attach挂载模式和Spawn孵化模式；然后给出具体的调试的例子，包括Xcode汇编代码、函数调用堆栈、hook代码加断点等等效果；最后加上附录、包括如何查看进程PID。

## 源码+浏览+下载

本书的各种源码、在线浏览地址、多种格式文件下载如下：

### HonKit源码

* [crifan/ios_re_debug_xcode_iosopendev: iOS逆向调试：Xcode+iOSOpenDev](https://github.com/crifan/ios_re_debug_xcode_iosopendev)

#### 如何使用此HonKit源码去生成发布为电子书

详见：[crifan/honkit_template: demo how to use crifan honkit template and demo](https://github.com/crifan/honkit_template)

### 在线浏览

* [iOS逆向调试：Xcode+iOSOpenDev book.crifan.org](https://book.crifan.org/books/ios_re_debug_xcode_iosopendev/website/)
* [iOS逆向调试：Xcode+iOSOpenDev crifan.github.io](https://crifan.github.io/ios_re_debug_xcode_iosopendev/website/)

### 离线下载阅读

* [iOS逆向调试：Xcode+iOSOpenDev PDF](https://book.crifan.org/books/ios_re_debug_xcode_iosopendev/pdf/ios_re_debug_xcode_iosopendev.pdf)
* [iOS逆向调试：Xcode+iOSOpenDev ePub](https://book.crifan.org/books/ios_re_debug_xcode_iosopendev/epub/ios_re_debug_xcode_iosopendev.epub)
* [iOS逆向调试：Xcode+iOSOpenDev Mobi](https://book.crifan.org/books/ios_re_debug_xcode_iosopendev/mobi/ios_re_debug_xcode_iosopendev.mobi)

## 版权和用途说明

此电子书教程的全部内容，如无特别说明，均为本人原创。其中部分内容参考自网络，均已备注了出处。如发现有侵权，请通过邮箱联系我 `admin 艾特 crifan.com`，我会尽快删除。谢谢合作。

各种技术类教程，仅作为学习和研究使用。请勿用于任何非法用途。如有非法用途，均与本人无关。

## 鸣谢

感谢我的老婆**陈雪**的包容理解和悉心照料，才使得我`crifan`有更多精力去专注技术专研和整理归纳出这些电子书和技术教程，特此鸣谢。

## 其他

### 作者的其他电子书

本人`crifan`还写了其他`150+`本电子书教程，感兴趣可移步至：

[crifan/crifan_ebook_readme: Crifan的电子书的使用说明](https://github.com/crifan/crifan_ebook_readme)

### 关于作者

关于作者更多介绍，详见：

[关于CrifanLi李茂 – 在路上](https://www.crifan.org/about/)
