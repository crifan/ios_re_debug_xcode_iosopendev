# Xcode+iOSOpenDev概览

关于iOS逆向中的动态调试，之前已有完整的成套的教程：

[iOS逆向开发：动态调试](https://book.crifan.org/books/ios_re_dynamic_debug/website/)

而此处是单独介绍其中的，最常用的，最好用的部分：

用`Xcode+iOSOpenDev`实现GUI图形方式去调试

* 对比
  * 和**command line**=**命令行**方式的[debugserver+lldb](https://book.crifan.org/books/ios_re_debug_debugserver_lldb/website/)调试方式相比
    * **GUI**=**图形界面**方式的调试：`Xcode+iOSOpenDev`
      * 图形界面中，调试更加直观
        * Xcode中加函数断点
        * Xcode中给hook代码加断点
        * Xcode中查看和调试汇编代码
* 前提
  * （app/二进制文件等）调试目标必须是：**可调试**=**Debuggable**的
