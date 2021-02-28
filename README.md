# XCloud

XCloud : 适合初学者，喜欢的小伙伴可以点上边的Star支持一下哦
***
[XCloud体验点这里](https://www.xcloud.show/)

#### 体验注意(二选一即可)：

* 直接使用QQ登陆，新用户自动注册
* 注册，进入注册页面注册，需正确填写邮箱，以便接收验证链接进行注册信息验证。

#### 作者不太会前端，前台界面已经尽力了。

#### 有特殊需求的小伙伴可以自己动手改造前端，爱莫能助。

### 更新与开发进度

* 2021.2.28
    * 文件相关
        * 文件上传升级为生产者消费者模式
    * 用户相关
        * 优化用户锁机制（字段不同锁不同），提高并发访问速度
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
        * 日志集成Log4j2（未启用，启用只需取消掉yml、pom等文件中相关log4j2注释即可）
        * 请求次数统计（累计、成功、失败）
        * 日志文件生成
        * 响应时间统计
    * 优化邮件发送
    * 前端注册等界面增加账号与邮箱填写时的AJAX唯一性校验

###

* 待开发
    * 文件相关
        * 文件以及文件名的重命名（考虑中……）
        * 文件列表分页展示（考虑中……）
    * 用户相关
        * 支付宝引入

### 项目主要功能

* 文件的批量上传、下载、删除
* 文件夹的新建、删除
* 文件二维码、链接分享

### 项目亮点

* 提供了安卓App访问接口，并且已经写出一版***安卓App***，可在本人另一个仓库获取
* 上传文件异步持久
* 服务器只负责文件、文件夹和用户的统一管理
* 复杂邮件发送（HTML）模板
* 速度测试（300兆宽带）
    * 上传：104MB压缩包，用时***1分35秒***
    * 下载：104MB压缩包，用时***5秒***
    * 仅限测试，带宽的不同使得上传、下载速度的不同。
* Nginx部署SSL证书
* 动静分离

### 所用技术

#### 前端

* HTML、CSS、JavaScript、JQuery、Bootstrap、fileInput插件、腾讯防水墙、Toastr插件

#### 后台

* SpringBoot
* MyBatis
* MySQL
* Druid:阿里高性能数据库链接池
* Redis:缓存
* OSS:文件服务器
* ThymeLeaf:模板引擎
* Nginx:反向代理
* Tomcat
* Maven
* jackson
* 二维码工具:google.zxing

### 页面展示

#### 主要界面

* <img src="https://www.xcloud.show/static/img/git/xcloud/browse/front_login_03.png" alt="登陆" width="600px"/>
* <img src="https://www.xcloud.show/static/img/git/xcloud/browse/front_home.png" alt="主页" width="600px"/>
* <img src="https://www.xcloud.show/static/img/git/xcloud/browse/front_share.png" alt="分享" width="600px"/>
* <img src="https://www.xcloud.show/static/img/git/xcloud/browse/front_upload.png" alt="上传" width="600px"/>

#### 邮箱界面

* <img src="https://www.xcloud.show/static/img/git/xcloud/browse/email02.png" alt="邮箱" width="600px"/>

### 本地开发运行部署

#### Xcloud 项目

* JDK版本: 1.8
* 下载zip直接解压或安装git后执行克隆命令 https://github.com/zhang-sexy/XCloud-Server.git
* 配置 MySQL、Redis、OSS、邮箱、QQ互联、腾讯防水墙等信息
* 运行MySql脚本文件 xcloud.sql
* 修改各配置文件相应依赖IP配置（默认本地127.0.0.1）
* jar包后台运行:nohup java -jar xcloud.jar &
* 注意: Log4j2 已配置但未启用，启用需手动修改: yml、pom、mybatis.xml、log4j2.xml

#### Xcloud Android App 项目

* Xcloud Android App项目请移步到本人XCloud仓库 </br>https://github.com/zhang-sexy/XCloud.git

### 写在最后

由于技术有限，难免会有一些设计不合理之处，有好的想法，私聊我(206547334)即可。

* 目前版本前后端耦合度较高，但在设计初便定义了服务器统一返回格式，见<br>
  cn.zf233.xcloud.common.ServerResponse<br>
  所以前后端分离的实现只会修改少部分代码
* Logo已申请版权，请勿商用
