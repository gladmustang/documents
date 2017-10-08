<span style="color: rgb(0,0,0);background-color: rgb(255,255,255);font-size: 14px;font-family: tahoma, arial, 宋体;">本文介绍了解决React Native端口号修改的方法，分享给大家，具体如下：</span>

<span style="color: rgb(0,0,0);background-color: rgb(255,255,255);font-size: 14px;font-family: tahoma, arial, 宋体;">**看图说话**</span>

![这里写图片描述](http://files.jb51.net/file_images/article/201707/2017072810101514.png)

<span style="color: rgb(0,0,0);background-color: rgb(255,255,255);font-size: 14px;font-family: tahoma, arial, 宋体;">一般情况下,如果本地安装过一些服务的话，ReactNeact 就会毫不犹豫的给你报出错误信息，</span>

<span style="color: rgb(0,0,0);background-color: rgb(255,255,255);font-size: 14px;font-family: tahoma, arial, 宋体;">如果你是这个错误，那么你的端口号被占用了，ReactNative默认端口为8081</span>

![这里写图片描述](http://files.jb51.net/file_images/article/201707/2017072810101515.png)

<span style="color: rgb(0,0,0);background-color: rgb(255,255,255);font-size: 14px;font-family: tahoma, arial, 宋体;">**解决方案1：**</span>

<span style="color: rgb(0,0,0);background-color: rgb(255,255,255);font-size: 14px;font-family: tahoma, arial, 宋体;">很简单，找到使用node生成的ReactNative项目 使用node命令：</span>

<span style="color: rgb(0,0,0);background-color: rgb(255,255,255);font-size: 14px;font-family: tahoma, arial, 宋体;">在cmd命令中，切换到项目目录下，输入:</span>

<span style="color: rgb(0,0,0);background-color: rgb(255,255,255);font-size: 14px;font-family: tahoma, arial, 宋体;">`react-native start --port 9999`</span>

<span style="color: rgb(0,0,0);background-color: rgb(255,255,255);font-size: 14px;font-family: tahoma, arial, 宋体;">**接下来，继续走**</span>

![这里写图片描述](http://files.jb51.net/file_images/article/201707/2017072810101716.png)

<span style="color: rgb(0,0,0);background-color: rgb(255,255,255);font-size: 14px;font-family: tahoma, arial, 宋体;">**然后，**摇晃设备或者命令行输入adb shell input keyevent 82，打开开发者菜单</span>

<span style="color: rgb(0,0,0);background-color: rgb(255,255,255);font-size: 14px;font-family: tahoma, arial, 宋体;">点击Dev Settings（提示：最后一个tab）进入，然后选择Debug server host& port for device</span>

<span style="color: rgb(0,0,0);background-color: rgb(255,255,255);font-size: 14px;font-family: tahoma, arial, 宋体;">进行IP地址及其端口号配置，例如：</span>

<span style="color: rgb(0,0,0);background-color: rgb(255,255,255);font-size: 14px;font-family: Helvetica, Tahoma, Arial, sans-serif;">**注意： 模拟器提供了一个特殊的IP，这个IP地址为10.0.2.2，这个IP地址可以说等同于PC本机的IP地址127.0.0.1，所以，通过这个特殊的IP地址可以进行PC与模拟器之间的通信。**</span>

![这里写图片描述](http://files.jb51.net/file_images/article/201707/2017072810102017.png)

<span style="color: rgb(0,0,0);background-color: rgb(255,255,255);font-size: 14px;font-family: tahoma, arial, 宋体;">输入完成之后，点击确定，回到开发者菜单，然后选择点击Reload JS。重新加载即可。</span>

<span style="color: rgb(0,0,0);background-color: rgb(255,255,255);font-size: 14px;font-family: tahoma, arial, 宋体;">**解决方案2：**</span>

<span style="color: rgb(0,0,0);background-color: rgb(255,255,255);font-size: 14px;font-family: tahoma, arial, 宋体;">在Android中找到src/main/java/MainApplication（Android 主入口文件）类名，找到 onCreate方法,代码附上：</span>

<span style="color: rgb(0,0,0);background-color: white;font-size: 14px;">`@Override`</span>

<span style="color: rgb(0,0,0);background-color: white;font-size: 14px;">`public`</span> <span style="color: rgb(0,0,0);background-color: white;font-size: 14px;">`void`</span> <span style="color: rgb(0,0,0);background-color: white;font-size: 14px;">`onCreate() {`</span>

<span style="color: rgb(0,0,0);background-color: white;font-size: 14px;">`super.onCreate();`</span>

<span style="color: rgb(0,0,0);background-color: white;font-size: 14px;">`//SoLoader.init(this, /* native exopackage */ false);`</span>

<span style="color: rgb(0,0,0);background-color: white;font-size: 14px;">`SharedPreferences mPreferences =  PreferenceManager.getDefaultSharedPreferences(getApplicationContext());`</span>

<span style="color: rgb(0,0,0);background-color: white;font-size: 14px;">`mPreferences.edit().putString("debug_http_host","localhost:8099").commit();`</span>

<span style="color: rgb(0,0,0);background-color: white;font-size: 14px;">`}`</span>

<span style="color: rgb(0,0,0);background-color: rgb(255,255,255);font-size: 14px;font-family: tahoma, arial, 宋体;">PS：通过 linux 映射</span>

<span style="color: rgb(0,0,0);background-color: rgb(255,255,255);font-size: 14px;font-family: tahoma, arial, 宋体;">然后在控制台cmd中运行：</span>

<span style="color: rgb(0,0,0);background-color: rgb(255,255,255);font-size: 14px;font-family: tahoma, arial, 宋体;">`npm start react-native start –port 8099`</span>

<span style="color: rgb(0,0,0);background-color: rgb(255,255,255);font-size: 14px;font-family: tahoma, arial, 宋体;">修改即可，即可完成配置，摇晃手机，刷新页面即可！</span>

<span style="color: rgb(0,0,0);background-color: rgb(255,255,255);font-size: 14px;font-family: tahoma, arial, 宋体;">以上就是本文的全部内容，希望对大家的学习有所帮助，也希望大家多多支持脚本之家。</span>