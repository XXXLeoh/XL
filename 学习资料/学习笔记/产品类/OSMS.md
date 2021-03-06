## OSMS

堡垒机（SAS-H/OSMS）



堡垒机概述

产品定位

![image-20200722100734388](E:\Typora\Image\image-20200722100734388.png)

为客户的网络提供单点登陆方式，方便管理的同时也对网络有一定程度的保护

![image-20200722100913280](E:\Typora\Image\image-20200722100913280.png)

产品型号划分

![image-20200722100943776](E:\Typora\Image\image-20200722100943776.png)

堡垒机升级路线

![image-20200722102419314](E:\Typora\Image\image-20200722102419314.png)设备登陆

- 浏览器：https://设备的管理IP地址
- M口默认地址：192.168.1.1
- 根据整数的差异，页面将显示为OSMS或SAS[H]

串口登录

- 默认用户名/密码：conadmin/conadmin
- 波特率：115200
- 数据位：8

串口常见操作

- 查看接口IP地址
- 设置接口地址
- 查看硬件特征值
- 修改系统时间
- 重置堡垒机管理员、运维管理员、审计管理员用户名和密码
- 初始化配置——恢复为出厂配置，版本号不会变，会丢失证书
- 恢复系统——相当于重装系统，会将版本恢复到当前的固件版本，不丢证书
- 设备关机

后台登陆

- 登陆场景
    - 不将一次性密码发给客户
    - 登陆操作结束，及时退出SSH连接
- 登录方式
    - 设备页面或串口下开启远程协助
    - ssh端口22
    - 账号develop(串口也可登陆后台)
- 一次性密码申请方式
    - 收集HASH值和状态码
    - 400电话申请

堡垒机账户角色权限

- 系统管理
    - 堡垒机管理员
        - 系统缺省，主责堡垒机系统参数配置、诊断维护、备份升级等工作
        - 支持用户认证参数配置，第三方服务器联动配置等
        - 不能管理设备和运维权限
- 资产运维
    - 运维管理员
        - 系统缺省，主责资产管理，运维安全审计业务
        - 支持所有设备资产和用户人员录入，运维权限分配和审批，运维功能参数配置，所有运维审计日志分析和统计报表
    - 设备管理员
        - 分管的运维审计业务
        - 支持设备资产和普通用户录入，运维权限分配，运维审计日志分析和统计报表
    - 普通用户
        - 分管的运维任务
        - 支持对设备进行运维管理，工单申请管理权限
- 安全运维
    - 审计管理员
        - 主责安全审计和日志管理业务
        - 支持审计人员权限分配
        - 支持安全审计参数配置
        - 支持审计日志分析和统计报表
    - 审计员
        - 分管安全审计业务
        - 支持审计日志分析和统计报表

缺省系统账号开启

自5.6R10F00SP13开始，系统账号运维管理员和审计员管理员会在当密码为初始密码（新设备或者串口重置账号密码)时，将账号禁用。需要登陆堡垒机管理员账号将其启用。

角色分配

![image-20200722110053469](E:\Typora\Image\image-20200722110053469.png)

辅助插件--Java

![image-20200722110210949](E:\Typora\Image\image-20200722110210949.png)

必要的辅助工具-ActiveX控件

![image-20200722110326662](E:\Typora\Image\image-20200722110326662.png)

前置机/应用平台

- 所提供的功能
    - 详尽的录屏审计，补充例如URL审计匮乏的审计信息
    - 审计范围通过前置机的部署而扩大，支持了一些堡垒机无法代理的应用/协议或无法直达的网络
- 核心科技
    - 微软在Windows Server 2008开始推出RemoteApp功能模块。(server2003激活RD后可直接使用)
- 前置机系统支持情况:
    - server2003、server2008、server2012(5.6.10sp11之后)

应用平台

- 型号1000C、1100C、2000C支持安装应用平台;
- 目前应用平台的版本有5.6R10F00、F00SP03、F00SP06、F00SP11(还未对外发布)，升级需要使用2.0的NTFS格式U盘在串口下进行升级
- 镜像为Windows server 2008 SP2



应用的发布--前置机/应用平台

![image-20200722111001299](E:\Typora\Image\image-20200722111001299.png)

应用的发布--堡垒机

1.Supervisor登陆，在【设备管理】-【设备】-【前置机】中添加前置机。

2.添加应用:非remoteapp模式将前置机上的应用路径复制粘贴;remoteapp模式填写别名。应用平台的发布位置在【设备管理】-【设备】-【应用平台】下方的【应用配置】中。流程与前置机应用发布相同



堡垒机前置机/应用平台实际简易拓扑

![image-20200722111216061](E:\Typora\Image\image-20200722111216061.png)

协议&需求实现

![image-20200722111244275](E:\Typora\Image\image-20200722111244275.png)

字符协议

![image-20200722112218905](E:\Typora\Image\image-20200722112218905.png)

图形协议

![image-20200722112415965](E:\Typora\Image\image-20200722112415965.png)

图形协议RDP/VNC----通过图形化界面，可以结合鼠标和键盘

代理功能实现可通过：web浏览器/mstsc/vnc客户端

![image-20200722112539129](E:\Typora\Image\image-20200722112539129.png)

文件协议

![image-20200722112636532](E:\Typora\Image\image-20200722112636532.png)

文件代理

文件协议FTP/SFTP---上传下载文件

代理功能实现可通过：web浏览器/Winscp/XFTP

![image-20200722113025438](E:\Typora\Image\image-20200722113025438.png)

web 代理

![image-20200722113132229](E:\Typora\Image\image-20200722113132229.png)

WEB协议-URL审计

- 需要用到本地浏览器
- 推荐IE浏览器，基于ActiveX实现全程自动代理功能
- 也可使用火狐浏览器，需要手动设置代理

![image-20200722113333652](E:\Typora\Image\image-20200722113333652.png)

- 客户端需要设置代理才能进行正常通信，IE浏览器可自动检测和安装ActiveX进行自动代理设置
- 火狐等其他浏览器需要手动配置代理
    - http://ip:50010/user.pac
    - ip是堡垒机ip
    - user是当前登录的堡垒机账号

WEB协议-URL+录屏审计

浏览器登陆堡垒机后，使用web调用mstsc方式调用前置机IE再经过web代理访问目标设备(客户端浏览器基于Java或ActiveX，前置机IE基于ActiveX自动设置代理);由于客户端调用前置机使用RDP协议，故可实现录屏审计

![image-20200722113727320](E:\Typora\Image\image-20200722113727320.png)

设备访问

设备管理员/普通用户通过浏览器登陆堡垒机后进入设备访问页面，选择和确认目标设备、协议账号等信息后，进行登录

触发登录后，浏览器会给予ActiveX或Java调用mstsc使用前置机IE访问目标设备

调用出前置机IE后会提交https://ip/prev_web_proxy.php?verify_hash=**的URL进程认证请求

数据库审计

- 数据库审计是指通过前置机/应用平台打开数据库运维软件，对运维人员的操作进行录屏审计和命令审计
- 数据库命令审计支持的数据库应用

数据库审计-部署

环境部署:
0.如果是将应用平台作为数据库运维前置机，则不需要如下设置;
1.前置机一台，并安装堡垒机代理程序和数据库应用;
2.前置机上将前置机代理程序和数据库应用作为应用发布remoteapp
3.堡垒机配置监听口(monitor)，开启数据审计功能;
4.外置前置机访问DBserver的流量镜像到堡垒机的监听口;

![image-20200722140912670](E:\Typora\Image\image-20200722140912670.png)

数据库审计-前置机相关设置

正确填写前置机代理、前置机代理路径，两者要保持一致。并在前置机上进行了remoteapp发布。所要使用的数据库客户端也需要进行发布。安装堡垒机代理程序。

访问策略

运维管理员/设备管理员在【运维权限】-【访问策略】中建立访问策略，将自己建立的设备交由其他人员运维，其中可以对部分访问动作进行限制、管理。**匹配顺序由上向下，匹配即跳出。**



日志审计

**安全审计功能**

目前可以支持的协议审计:

- 字符审计: SSH、Telnet
- 图形审计:RDP、VNC、X11
- 文件审计:FTP、SFTP
- Web审计：图形日志（需要前置机）、URL日志
- 数据库审计:数据库图形、数据库SQL(需要镜像流量)
- 堡垒机自身审计:各个账户的操作行为记录
- 会话在线状态:设备管理员、审计员

**字符审计**

审计结果

- 回放操作
- 实时查看
- 命令记录
- 结果记录
- 根据命令/结果查找日志

**图形审计**

协议类型：RDP、VNC

审计结果（用户操作完整记录）

- 回放操作
- 实时查看
- 键盘日志

**文件审计**

协议类型：FTP、SFTP

审计结果：实时查看、命令查看

**网页审计：**

协议类型：http、https

审计结果：URL审计、URL+录屏下的图形日志

**数据库审计：**

审计结果：定点回放、全程回放

**堡垒机系统日志**：

- 堡垒机账号分配
- 账号授权
- 登录堡垒机过程
- 认证管理
- 授权管理
- 自动改密

离线播放

所有日志都可以下载之后使用【堡垒机日志管理工具】在本地播放登陆有审计权限的设备账号，可以在【运维管理】-【工具下载】-【日志管理工具中】下载堡垒机日志管理工具。

由于该应用基于Java，所有使用之前需要先添加file:///作为Java的例外安全站点



#### 堡垒机的使用

运维流程

![image-20200722145239077](E:\Typora\Image\image-20200722145239077.png)

其他拓展功能

账号认证方式

![image-20200722145604959](E:\Typora\Image\image-20200722145604959.png)

特殊认证方式

ADlopenLADP/Radius需要堡垒机管理员登陆后，预先在【用户管理】-【用户认证】-【认证服务器】中添加相关信息

OTP令牌认证中堡垒机本身无需连接公网，在【用户管理】-【用户认证】-【认证配置】中开启OTP认证，用户手机上需要安装绿盟相关APP

UKEY认证则需要另外购买飞天令牌，此种认证方式的用户无法使用客户端登陆

短信认证需要向服务提供商购买相关服务，目前支持凌凯短信和咪咕数媒（已停止合作，之前购买的未到期服务仍可使用)，【用户管理】-【用户认证】-【短信网关】开启相关功能

通用功能-配置备份恢复

全部配置文件不包括接口路由HA配置，继续相同引擎版本导出跨平台配置文件内容:

- 用于将5.6.6版本的配置信息直接导入到5.6.8以上版本;
- 包括系统大部分配置信息;
- 其中，未备份的配置信息包括网络中的接口、DNS、路由和高可用性配置。

http://192.168.255.65/iaes/search/viewsolution/3449

DNAT环境

该功能在V5.6R10F00SP10上支持较好，如需使用该功能应先升级到SP10版本。启用DNAT功能后需要填写DNAT地址，并将上图红框中的运维端口与网闸DNAT配置保持一致。

例如将堡垒机的远程桌面运维端口3389DNAT为33389，则须将堡垒机上DNAT配置中的远程桌面运维端口修改为33389。



设备账号改密

登陆运维管理员supervisor，在【设备管理】-【密码】中可以通过一些设置使用堡垒机对所选的设备账号进行改密的手动/自动执行。

改密的顺利执行需要预先进行以下设置:

1.密码规则:指定新密码（随机/指定);
2.改密脚本:针对不同的设备有不同的改密脚本，可自行修改至匹配;
3.将密码规则和改密脚本与设备账号绑定。

![image-20200722150307090](E:\Typora\Image\image-20200722150307090.png)

审计日志的备份、恢复

审计管理员登陆堡垒机，可将审计日志通过FTP进行备份、恢复。

PS:目前恢复日志只可恢复字符协议日志以及键盘交互之类的信息，图形日志只能通过离线日志查看器播放

联动交互

![image-20200722150430184](E:\Typora\Image\image-20200722150430184.png)

堡垒机通信端口说明

![image-20200722150633062](E:\Typora\Image\image-20200722150633062.png)

常见功能使用

![image-20200722150748426](E:\Typora\Image\image-20200722150748426.png)