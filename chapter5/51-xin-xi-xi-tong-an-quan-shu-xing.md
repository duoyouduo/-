# 5.1 信息系统安全属性

## 1.保密性

* **最小授权原则** 给某个人授权时，给其职能所需要的最小的权限；
* **防暴露** 隐藏以提高安全性，比如为防止有人破解数据库，数据库名可以采用非标准的方式来命名数据库；
* **信息加密** 加密后传输，即使被截获，截获者也无法了解信息原始内容，除非破解；
* **物理保密** 采用相应物理设备，发送时加密，接收时解密；

## 2.完整性

信息从一个节点发送到另一个节点时，信息是不能有变化的，否则会有安全隐患（信息篡改，造成损失）

* **安全协议** 
* **校验码** 接收后校验，就知道和原始信息是否相同，比如下载的md5码验证（下载到的资料是否被篡改、是否出错）等。。。 
* **密码校验、数字签名、公证**。。。

## 3.可用性

合法用户可以以合法的方式使用相应的资源，如果一台服务器不能给合法用户提供相应功能，那么可用性就遭到了破坏，比如DDoS攻击破坏的就是网络的可用性；

* **综合保障（IP过滤、业务流控制、路由选择控制、审计跟踪）**

## 4.不可抵赖性

* 主要手段：**数字签名**，签名可以识别发送者的身份，发送者就无法抵赖其发送过的信息。









