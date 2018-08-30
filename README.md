# Technology Stack
ID | Platform | Function |  Lnguage  | Build Status
 -------- | -------- | ------------ |  ------------ | ------------
 1  |   Android | [Framework](https://github.com/jiangshide/framework) | [Java](https://github.com/jiangshide/framework) [kotlin](https://github.com/jiangshide/kotlin_android) | [![Build Status](https://travis-ci.org/Bilibili/ci-ijk-ffmpeg-android.svg?branch=master)](https://github.com/jiangshide/framework)
 2  |   Ios | [Framework](https://github.com/jiangshide/ios) |	Swift	| [![Build Status](https://travis-ci.org/Bilibili/ci-ijk-ffmpeg-ios.svg?branch=master)](https://github.com/jiangshide/ios)
 3  |   Web | [Backstage](https://github.com/jiangshide/backstage) | 	[Golang](https://github.com/jiangshide/backstage) [JS](https://github.com/jiangshide/backstage_js)	|	[![Build Status](https://travis-ci.org/Bilibili/ci-ijk-ffmpeg-ios.svg?branch=master)](https://github.com/jiangshide/backstage)
 4  |   Api | [Interface](https://github.com/jiangshide/zd112_api) |	Golang	| [![Build Status](https://travis-ci.org/Bilibili/ci-ijk-ffmpeg-ios.svg?branch=master)](https://github.com/jiangshide/zd112_api)
 5  |   Spark | [Analysis](https://github.com/jiangshide/analysis) |	Scala	| [![Build Status](https://travis-ci.org/Bilibili/ci-ijk-ffmpeg-ios.svg?branch=master)](https://github.com/jiangshide/analysis)
 6  |   Block Chain | [Identification](https://github.com/jiangshide/idendification) |	Golang	| [![Build Status](https://travis-ci.org/Bilibili/ci-ijk-ffmpeg-ios.svg?branch=master)](https://github.com/jiangshide/idendification) 
 
# Base framework 
Platfor |	Module | Status	|	Open Level
 -------- | ------------ |  ------------ |  ------------ 
 Android | UI模块 | 基础完成	|	低(可定制)
 Android | 网络模块(http,socket) |	 基础完成		|	低(可定制)
 Android | 消息模块 | 	开发中	|	需定制
 Android | 事件分发模块 |	开发中	|	需定制
 Android | 安全控制与认证模块 |	开发中	|	需定制
 Android | 数据适配模块 |	基础完成	|	低(可定制)
 Android | 升级模块 |		基础完成	|	中(可定制)
 Android | 错误日志模块(java,native) | 	基础完成	|	低(可定制)
 Android | HTML5交互模块 |	基础完成	|	中(可定制)
 
## 项目目的
打造最简单与最全的客户端移动基础框架,兼容所有原生接口(本身是基于原生开发:同步原生接口兼容实现),让开发者使用最少的代码去最大化的实现项目需求,应变各种紧急项目快速输出
## 项目架构
   ![Image](https://github.com/jiangshide/framework/blob/master/img/android_frame.svg)
## 项目案例
### 1.UI模块(通用导航栏,通用加载刷新,通用对话实现,二维码相关,以及基础用到的view...)
#### 1.1 通用导航栏
#### 1.2 通用加载刷新控制
#### 1.3 通用对话框实现
#### 1.4 二维码实现
#### 1.5 通用手势密码实现
#### 1.6 通用滚轮实现
#### 1.7 高级按钮操作等
### 2.网络模块
### 3.消息模块
### 4.事件分发模块
### 5.安全控制与认证模块
### 6.数据适配模块
### 7.升级模块(普通更新,热更新)
#### 7.1 普通同更新~默认:只需要一段代码即可
    new UpdateView(this).init().setListener(this);
#### 7.2 普通更新～截取更新核查结果
    new UpdateView(this).init(new Callback() {
                @Override
                public void onSuccess(NetInfo info) throws IOException {
                    
                }
    
                @Override
                public void onFailure(NetInfo info) throws IOException {
    
                }
            });
#### 7.3 普通更新～截取更新文件下载请求过程
    new UpdateView(this).init().setProgressListener(new ProgressCallback(){
                @Override
                public void onProgressMain(int percent, long bytesWritten, long contentLength, boolean done) {
                    super.onProgressMain(percent, bytesWritten, contentLength, done);
                }
    
                @Override
                public void onResponseMain(String filePath, NetInfo info) {
                    super.onResponseMain(filePath, info);
                }
            });
#### 7.4 普通更新~同时截取更新核查与文件下载：自定义场景与界面展示
    new UpdateView(this).init(new Callback() {
                @Override
                public void onSuccess(NetInfo info) throws IOException {
    
                }
    
                @Override
                public void onFailure(NetInfo info) throws IOException {
    
                }
            }).setProgressListener(new ProgressCallback(){
                @Override
                public void onProgressMain(int percent, long bytesWritten, long contentLength, boolean done) {
                    super.onProgressMain(percent, bytesWritten, contentLength, done);
                }
    
                @Override
                public void onResponseMain(String filePath, NetInfo info) {
                    super.onResponseMain(filePath, info);
                }
            });            
### 8.错误日志模块(java,native)
### 9.HTML5交互模块
### 10.分享模块

## 项目集成(非常优雅的集成,最大化灵活控制,只需要几个步骤)

1.在你的项目工程根目录所在的build.gradle中添加:maven { url "https://jitpack.io" }

        allprojects {
            repositories {
                google()
                jcenter()
                maven { url "https://jitpack.io" }//当前需要添加的
            }
        }
        
2.在你项目工程app所在目录下build.gradle中添加:implementation 'com.github.jiangshide:framework:1.0.1'

        dependencies {
            implementation fileTree(dir: 'libs', include: ['*.jar'])
            implementation 'com.android.support:appcompat-v7:28.0.0-alpha3'
            implementation 'com.android.support.constraint:constraint-layout:1.1.2'
            testImplementation 'junit:junit:4.12'
            androidTestImplementation 'com.android.support.test:runner:1.0.2'
            androidTestImplementation 'com.android.support.test.espresso:espresso-core:3.0.2'
            implementation 'com.github.jiangshide:framework:1.0.1'//当前需要添加的
        }
        
### 3.拷贝demo中gradle.properties文件覆盖自己项目中的gradle.properties,需要注意:
#### 3.1 如果打release包的话需要替换成自己的密钥文件与相关信息：
        KEY_FILE=demo
        KEY_ALIAS=jsd
        KEY_PASSWORD=jsddemo
        STORE_PASSWORD=jsddemo
#### 3.2 网络主机替换：需要替换成自己的IP或域名
    #the net config
    PRODUCTION=http://10.20.6.50:8091
    PREPRODUCTION=http://10.20.6.50:8091
    TEST=http://10.20.6.50:8091
    API=/api/zdb/
    UPDATE=update
#### 3.3 api协议配置,可替换成自己实际协议的名称
    #BaseData protocol
    CODE=code
    SUCCESS=success
    TIME=date
    MSG=msg
#### 3.4 可修改网络默认配置
##### the http params
    HTTP_CONNECT_TIME=30
    HTTP_READ_TIME=30
    HTTP_WRITE_TIME=30
    HTTP_MAX_CACHE_SIZE=10 * 1024 * 1024
##### the four type:1~FORCE_NETWORK;2~FORCE_CACHE;3~NETWORK_THEN_CACHE;4~CACHE_THEN_NETWORK
    HTTP_CACHE_TYPE=4
    HTTP_IS_GZIP=true
    HTTP_SHOW_LIFECYCLE_LOG=true
    
# 服务宗旨:
### 一.面向企业：
#### 1.提供专业的技术支持
#### 2.一对一技术方案提供
#### 3.零容忍问题服务
### 二.面向个人：
#### 1.获得与企业同等的态度
#### 2.最优化项目技术支持
#### 3.最大化项目技术扩展

# 友情合作:
   ![Image](https://raw.githubusercontent.com/jiangshide/framework/master/img/weixin.jpeg)
# 鼓励与支持:   
   ![Image](https://raw.githubusercontent.com/jiangshide/framework/master/img/play.png)
   
   