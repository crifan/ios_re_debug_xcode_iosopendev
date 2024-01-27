# 如何实现可调试debuggable

* 如何实现app可调试Debuggable
  * 概述
    * 全局的
      * 越狱工具越狱后，系统全局自动支持app可调式
        * 部分机型用unc0ver越狱后，自带：app可调式
        * A12+的机型，用XinaA15越狱后，自带：app可调式
      * 借助于插件XcodeRootDebug实现
    * 针对特定app的
      * （用codesign）给app二进制文件重新签名，加上可调试权限

下面详细解释：
