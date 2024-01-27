# 重签名添加权限实现可调试

* 重签名添加权限实现可调试
  * 概述
    * 方式1：用codesign重新签名，加上可调试的entitlement权限
    * 方式2：用`jailbreakd_client`加可调试的权限

详解：

## 用codesign重签名加可调试权限

* 用codesign重新签名，加上可调试的entitlement权限
  * 优点
    * 此方式相对比较通用，适用于各种机型和系统
  * 缺点
    * 需要熟悉codesign签名和entitlement权限等细节
  * 举例
    * 给akd重签名，使其可调试
      * 从iPhone中导出akd
        ```bash
        scp root@192.168.1.22:/System/Library/PrivateFrameworks/AuthKit.framework/akd akd_origin
        ```
      * 导出adk的entitlement权限
        ```bash
        ldid -e akd_origin > akd_entitlements.xml
        ```
      * 修改entitlement，增加可调式相关权限
        * 修改`akd_entitlements.xml`
          * 加上权限
            * `get-task-allow`=true
            * `task_for_pid-allow`=true
            * `run-unsigned-code`=true
            * ->
              ```xml
                  <key>get-task-allow</key>
                  <true/>
                  <key>task_for_pid-allow</key>
                  <true/>
                  <key>run-unsigned-code</key>
                  <true/>
              ```
          * 去掉权限
            * seatbelt-profiles
              ```xml
                  <key>seatbelt-profiles</key>
                  <array>
                      <string>akd</string>
                  </array>
              ```
            * com.apple.security.network.client
              ```xml
                  <key>com.apple.security.network.client</key>
                  <true/>
              ```
        * 保存为`akd_entitlements_debuggable.xml`
      * 用新的entitlement去重新签名
        ```bash
        cp akd_origin akd_debuggable
        codesign -f -s - --entitlements akd_entitlements_debuggable.xml akd_debuggable
        ```
      * 再把重签名后的akd放回越狱iPhone中
        ```bash
        scp akd_debuggable root@192.168.1.22:/System/Library/PrivateFrameworks/AuthKit.framework/akd
        ```
  * 详见
    * [手动重签名 · iOS逆向开发：签名和权限 (crifan.org)](https://book.crifan.org/books/ios_re_codesign_ent/website/common_issue/process_debuggable/self_do_resign.html)

## 用`jailbreakd_client`加可调试的权限

* 用`jailbreakd_client`加可调试的权限
  * 说明
    * `jailbreakd_client`是部分越狱系统才有的工具，好像是
      * 用的coolstar系越狱（Electra或者Chimera）后，有对应文件
        ```bash
        xia0:/chimera root# ls -la
        total 1100
        drwxr-xr-x  8 root wheel    256 Feb 26 13:19 ./
        drwxr-xr-x 28 root wheel    896 Sep 16 17:44 ../
        -rwxr-xr-x  1 root wheel 168736 Sep 17 10:21 inject_criticald*
        -rwxr-xr-x  1 root wheel 207920 Sep 17 10:21 jailbreakd*
        -rwxr-xr-x  1 root wheel 133840 Sep 17 10:21 jailbreakd_client*
        -rwxr-xr-x  1 root wheel 167296 Sep 17 10:21 libjailbreak.dylib*
        ...
        ```
    * 基本用法
      ```bash
      /electra/jailbreakd_client <PID> 1
      ```
  * 暂未成功使用，之前的折腾详见
    * 【未解决】iOS逆向：寻找可用的jailbreakd_client用于给进程加可调试权限
    * 【未解决】iOS逆向：用jailbreakd_client给debugserver去加上entitle和platformize
