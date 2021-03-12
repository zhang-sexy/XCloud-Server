# XCloud

基于OSS的在线存储应用。版本包含：🌍完全版本、📱阉割版本<br>

#### 适合初学者，喜欢的小伙伴可以点上边的Star支持一下哦

***
[XCloud体验点这里](https://www.xcloud.show/)

#### 体验注意(新用户二选一即可)：

* 选择QQ登陆，新用户自动注册
* 选择用户注册，需正确填写邮箱，以便接收验证链接进行注册信息验证。

#### 有特殊需求的小伙伴可以自己动手改造前端，爱莫能助。

### 更新与开发进度

* 2021.3.8
    * 文件相关
        * 增加文件、文件夹重命名
        * 增加文件、文件夹复制与移动

* 2021.3.2
    * 架构
        * 更改为分布式架构以提高多用户访问时的响应和处理速度
        * 各个服务器节点全部安装 Redis，做文件上传缓存
        * 单个上传文件按1MB进行切片并缓存至Redis，持久化消费者将文件在Redis中的缓存切片进行组装，而后进行持久化
        * 阿里云共享 Redis 做分布式锁、MyBatis二级缓存等
    * 前台
        * 美化用户信息展示页面
        * 增加用户分享链接、二维码管理

* 2021.2.28
    * 文件相关
        * 文件上传升级为生产者消费者模式
        * 优化锁机制（用户间锁不同且字段间锁不同），保证同用户多终端的并发操作不会出现MySQL数据不一致的情况。
    * 用户相关
        * 优化用户下载机制（文件下载量按字节统计）
        * 增加登陆注册时的图片验证码

* 2021.2.14
    * 文件相关
        * 文件分享优化
        * 支持链接和二维码分享
        * 可设置分享有效期
    * 用户相关
        * 邮箱用户QQ用户头像展示与修改
        * 用户账号合并
        * 账户信息统一展示与修改
        * 邮箱验证码登陆
        * 改进用户用量计算方式
        * 优化用户等级规则

* 2021.2.7

    * 舍弃饱受诟病的丑陋前端，引入Bootstrap，大改过后，更加美观
    * 增加后台文件分类
    * 增加用户头像展示与修改（1MB内头像）、暂不支持裁剪

* 2021.1.30

    * 增加Mybatis二级缓存，缓存至Redis
    * 前端上传文件临时缓存至Redis，异步持久化至OSS，提高了执行效率，加快了响应速度
    * 增加统一日志（切面）
        * 日志集成Log4j2
        * 请求次数统计（累计、成功、失败）
        * 日志文件生成
        * 响应时间统计
    * 优化邮件发送
    * 前端注册等界面增加账号与邮箱填写时的AJAX唯一性校验

####

* 待开发
    * 文件相关
        * 文件列表分页展示（舍弃）
    * 用户相关
        * 支付宝引入

### 项目主要功能

* 文件的上传、下载、删除，重命名
* 文件夹的新建、删除、重命名
* 文件、文件夹的复制与移动
* 文件二维码、链接分享

### 项目亮点

* 提供了安卓App访问接口，并且已经写出一版***安卓App***，可在本人另一个仓库获取
* 上传文件异步持久
* 服务器只负责文件、文件夹和用户的统一管理
* 复杂邮件发送（HTML）模板
* 速度测试（保定地区300兆宽带）
    * 上传：135MB压缩包，用时***45秒***
    * 下载：135MB压缩包，用时***5秒***
    * 仅限测试，带宽的不同使得上传、下载速度的不同。
* Nginx部署SSL证书
* 动静分离、反向代理、负载均衡

### 所用技术

#### 前端

* HTML、CSS、JavaScript，JQuery、Bootstrap、腾讯防水墙，Toastr、clipboard、fileInput插件

#### 后台

* SpringBoot
* MyBatis
* Redisson
* MySQL
* Druid:阿里高性能数据库链接池
* Redis:缓存
* OSS:文件服务器
* QQ互联
* ThymeLeaf:模板引擎
* Nginx
* Tomcat
* Maven
* jackson
* 二维码工具:google.zxing

### 页面展示

#### 主要界面

* <img src="https://www.xcloud.show/static/img/git/xcloud/browse/front_login.png" alt="登陆" width="600px"/>
* <img src="https://www.xcloud.show/static/img/git/xcloud/browse/front_home.png" alt="主页" width="600px"/>
* <img src="https://www.xcloud.show/static/img/git/xcloud/browse/front_upload.png" alt="上传" width="600px"/>
* <img src="https://www.xcloud.show/static/img/git/xcloud/browse/front_share.png" alt="分享" width="600px"/>
* <img src="https://www.xcloud.show/static/img/git/xcloud/browse/front_copy.png" alt="复制/移动" width="600px"/>
* <img src="https://www.xcloud.show/static/img/git/xcloud/browse/front_detail_file.png" alt="文件详情" width="600px"/>
* <img src="https://www.xcloud.show/static/img/git/xcloud/browse/front_detail.png" alt="个人信息" width="600px"/>

#### 邮箱界面

* <img src="https://www.xcloud.show/static/img/git/xcloud/browse/email02.png" alt="邮箱" width="600px"/>

### 本地开发运行部署

#### Xcloud 项目

* 部署
    * JDK版本: 1.8
    * 下载zip直接解压或安装git后执行克隆命令 https://github.com/zhang-sexy/XCloud-Server.git
    * 配置 MySQL、Redis、OSS、邮箱、QQ互联、腾讯防水墙等信息
    * 运行MySql脚本文件 xcloud.sql
    * 修改各配置文件相应依赖IP配置（默认本地127.0.0.1）
    * jar包后台运行:nohup java -jar xcloud.jar &
    * 注意: Log4j2 已配置但未启用，需启用只需去掉: yml、pom、mybatis.xml、log4j2.xml等文件中的相关注释即可
* 注意
    * 单体版本获取 [点这里](https://www.xcloud.show/) 账号：notes、密码：notes，登陆后在XCloud项目文件夹中获取
    * 定时任务包 cn.zf233.task
    * 定时任务有两个
        * 1.负责记录请求数量（0点）
        * 2.负责用户信息刷新（1点）
    * 上述第二个任务只需要有一个服务器节点运行即可，其他服务器打注释即可

#### Xcloud Android App 项目

* Xcloud Android App项目请移步到本人XCloud仓库 </br>https://github.com/zhang-sexy/XCloud.git

### 写在最后

由于技术有限，难免会有一些设计不合理之处，有好的想法，私聊我(206547334)即可。

* 目前版本前后端耦合度较高，但在设计初便定义了服务器统一返回格式，见<br>
  cn.zf233.xcloud.common.ServerResponse<br>
  所以前后端分离的实现只会修改少部分代码
* Logo已申请版权，请勿商用
