# Fiddler抓包教程

## **1. fiddle和F12抓包对比**

相同点：

- 都可以对http和https进行抓包分析

不同点

- F12无法抓取app端的请求
- F12无法修改请求数据，请求之前和请求之后数据无法修改
- F12可以在console控制台输入部分命令，方便查看前端数据信息

## **2. fiddler的核心功能**

- 接口测试
  - 发送自定义请求，模拟小型接口测试场景

- 定位前后端bug
  - 抓取协议包，进行前后端联调

- 构建模拟测试场景
  - 数据篡改，重定向

- 弱网测试
  - 模拟限速操作，进行弱网以及断网测试内容

- 前端性能分析及优化

## **3. fiddler的工作原理**

- 本地应用和服务器之间所有的请求和响应都会先经过fiddler

## **4. fiddler功能配置使用**

**规则设置：Rules**

-  隐藏不需要的数据包
  - 连接数据包
  - 304数据包
  - ...

- 断点调试
  - 可以配置fiddler断点调试功能
  - 开启调试功能之后，所有请求之前及响应之后的所有数据包都可以进行拦截

- 弱网测试配置
  - 设置网络的配置文件的对应相关参数，模拟网络情况
  - 通过打开配置文件，进行修改对应的网络延迟 

## **5. 配置证书抓取https包**

fiddler默认只能抓取http的数据包，如果要抓取https数据包则需配置相关证书

- 打开Tools工具栏下面的选项options界面，选择https选项，勾上前两个(捕获https连接和解密https通道)

- 在connections里配置

- 重置更新证书，actions选第一个不断下一步

## **6. 设置过滤器**

 过滤器的核心作用就是抓取需要的数据包内容

**过滤器的基本配置步骤**

- 勾上开启过滤状态usefilter
- 选择抓取指定服务器的数据包show only the following hosts，写上对应的服务器地址，多个地址间用分号隔开
- 勾上hide if url contains,

过滤无关紧要的数据包正则格式：

` REGEX:(?insx)/[^\?/]*\.(css|ico|jpg|gif|bmp|wav|js|jpeg)(\?.*)?$`

## **7. 模拟网络测试**

给fiddler代理设置不同的网络情况模拟网络测试场景

- 2G
  - 上传：500，下载：400

- 3G
  - 上传：100，下载：100

- 4G
  - 上传：15，下载：10

配置开启网络设置的具体步骤：

- 打开fiddler网络配置相关文件：ctrl+r
- 通过ctrl+f进行搜索关键字：300
- ctrl+s保存并开启弱网规则，performance勾上simulate modem speeds

## **8.线上调试**

线上调试核心功能就是在完成请求的时候，先抓取服务器返回的响应信息，然后进行修改，重新发送请求之后，返回客户端修改之后的响应相关内容

**具体操作流程及步骤：**

- 第一步： 发送请求并获取服务器的响应时间，复制服务器返回的代码并修改，然后保存为html
- 第二步：autoresponder,勾上enable rules，add rule，选择刚刚保存的html文件    
- 第三步：回到页面进行刷新，查看响应信息
  - 通过shift+F5清空页面缓存

## **9.断点调试**

在客户端发送请求时进行拦截，并且修改相应的数据参数，再放行请求到服务器

- 第一步：抓取数据包
- 第二步：拦截请求数据，勾选拦截之前的请求操作(automatic breakpoints ---> before requests)
- 第三步：重复操作进行调试replay

## **10.接口需求文档整理**

 没有接口需求文档的时候怎么进行接口测试？

- 使用fiddler抓取进行分析整理接口需求文档
- 使用jmeter进行脚本录制整理接口需求文档



# 网页视频下载

> 先通过插件/f12/fiddler获取m3u8链接

- f12：网络-->搜索m3u8，类型一般是xhr-->右击复制链接地址或双击下载m3u8文件

## 1.使用插件猫抓/idm进行资源嗅探

- 猫抓

嗅探到的资源可能有两个m4s文件(如b站，大的是视频文件，小的是音频文件，当然b站有专门的下载插件)

如果嗅探到的资源是分片的，用m3u8进行下载

[地址](https://github.com/xifangczy/cat-catch/releases)

## 2.m3u8下载器

https://github.com/nilaoda/N_m3u8DL-CLI/releases

## 3.m3u8下载网站

http://blog.luckly-mjw.cn/tool-show/m3u8-downloader/index.html

## 4. OBS录屏



# b站下载

## 客户端

DownKyi(B站专用）

唧唧Down(B站专用）

## 在线

[snapany](https://snapany.com/zh/bilibili)

[DataTool.vip](https://www.datatool.vip/)

[cobalt](https://cobalt.tools/)

# ffmpeg下载及配置

[下载地址](https://ffmpeg.org/)

配置：

1.点击download，找到微软图标，windows builds by BtbN,找到master-win64-shared.zip,点击下载

2.新建ffmpeg文件夹，将bin中的3个exe文件复制到ffmpeg文件夹

3.打开环境变量，新建用户变量，变量名ffmpeg，路径为新建ffmpeg文件夹路径

4.打开cmd，输入ffmpeg验证是否安装成功

5.为ffmpeg安装you-get插件，输入`pip3 install you-get`,输入you-get检查是否安装成功

6.you-get  -o  保存路径 视频链接

# 其他github地址

[GitHub - gityuanbao/share](https://github.com/gityuanbao/share?tab=readme-ov-file)
