#### 2022.10.23：

安卓可以用vmos pro（提供root环境）+小黄鸟，ios可以用圈x（见另一个仓库），服务器版本暂时没什么用了。

#### 创作原因：

群里朋友说有人拿这个请假赚钱，那我只好写一个开源的了。。。 

#### 配置要求：

有公网IP服务器一台

ios设备：有小火箭

安卓（root）：小火箭

安卓（非root）：vmos一类的虚拟机上

**仅供学习参考，不要用于非法用途**

#### 文件说明：

`wzxyQianDuan.zip`: 个人信息提交页面代码

`wzxy.jar`: 后端代码打包的jar，用来保存和获取前端提交的信息

`rule.js`:anyproxy的规则

#### 部署流程：

服务器放开端口：8001 8002  8181 8182 

服务器安装nodejs java(jdk1.8) docker环境

**1、**`wzxy.jar`包上传到服务器 启动

`nohup java -jar wzxy.jar --server.port=8181 >outlog.log 2>&1 &`

浏览器访问 ip:8181 返回信息即正常

**2、** wzxyQianDuan.zip 在本地（windows，要有node环境）解压

修改src/App.vue 70行 127.0.0.1改为服务器的公网ip 保存

在主目录，

```
# 安装依赖
npm install 

# 打包
npm run build
```

会生成dist文件夹，上传到服务器

具体启动教程建议参考这个[(5条消息) Docker部署vue项目并运行_小小小果子的博客-CSDN博客_docker运行vue](https://blog.csdn.net/weixin_46244732/article/details/118699753?spm=1001.2101.3001.6650.16&utm_medium=distribute.pc_relevant.none-task-blog-2~default~OPENSEARCH~Rate-16-118699753-blog-120887454.topnsimilarv1&depth_1-utm_source=distribute.pc_relevant.none-task-blog-2~default~OPENSEARCH~Rate-16-118699753-blog-120887454.topnsimilarv1&utm_relevant_index=19)

**3、** 下载rule.js

修改192行 logo的值，小程序首页可以抓到你的学校的logo url ，保存 上传到服务器

服务器安装anyproxy，fs

#安装anyproxy  官网 http://anyproxy.io/cn/#%E5%BF%AB%E9%80%9F%E5%BC%80%E5%A7%8B

`npm install -g anyproxy`

#安装fs

`npm install fs`

#启动anyproxy

`anyproxy`

#访问http://ip:8002 ，web界面上能看到所有的请求信息  左侧，安装证书到手机

键盘ctrl+c #退出anyproxy

手机小火箭添加 http ip 端口即可

#安装pm2进程守护

`npm install -g pm2`

#在rule.js的同一目录下启动

 `pm2 start "anyproxy -i --rule rule.js"`

#### 测试：

先在前端页面提交信息，小火箭连接服务器（代理），返回小程序查看

#### 致谢：

[niusme/buzaixiaoyuan: 我在校园，假条模拟。基于安卓+root+xposed或者vmos虚拟机，不适用与ios (github.com)](https://github.com/niusme/buzaixiaoyuan)

[Milky01/wozaixiaoyuan: 圈X我在校园自动打卡，伪装假条 (github.com)](https://github.com/Milky01/wozaixiaoyuan)

**QQ群808655664，仅供交流学习，请在下载后24小时内删除。一切责任由使用者自负，与作者无关。**

**QQ群808655664，仅供交流学习，请在下载后24小时内删除。一切责任由使用者自负，与作者无关。**

**QQ群808655664，仅供交流学习，请在下载后24小时内删除。一切责任由使用者自负，与作者无关。**











