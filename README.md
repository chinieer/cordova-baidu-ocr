# Cordova Plugin BaiduOcr
================================

百度云OCR的cordova插件，身份证识别功能已测试通过，取消原工程的hook部分，修改部分bug。

Forked from https://github.com/liugogal/cordova-plugin-baidu-ocr


## Installation


1、Run

    cordova plugin add cordova-baidu-ocr

Or

    cordova plugin add https://github.com/hankersyan/cordova-baidu-ocr.git

2、Baidu云申请并下载aip.license授权文件。注意：id应匹配。

3、在config.xml里添加license文件的resource-file，注意：修改PATH/TO/

    <platform name="android">
        <resource-file src="PATH/TO/aip-android.license" target="app/src/main/assets/aip.license" />
    </platform>
    <platform name="ios">
        <resource-file src="PATH/TO/aip-ios.license" target="aip.license" />
    </platform>

### Supported Platforms

- Android
- iOS


### Using the plugin ###

A full example could be:

初始化（init）：
```js
    BaiduOcr.init(
        ()=>{
            console.log('init ok');
        },
        (error)=>{
            console.log(error)
        })
```
扫描身份证（scan id card）:
```js
    //默认使用的是本地质量控制，如果想使用拍照的方式，可以修改参数为
    //nativeEnable:false,nativeEnableManual:false
    BaiduOcr.scanId(
        {
            contentType:"IDCardFront", // 背面传 IDCardBack
            nativeEnable:true,
            nativeEnableManual:true
        },
        (result)=>{
            console.log(JSON.stringify(result));
        },
        (error)=>{
            console.log(error)
        });
```
销毁本地控制模型（destroy）：
```js
    BaiduOcr.destroy(
        ()=>{
            console.log('destroy ok');
        },
        (error)=>{
            console.log(error)
        });
```
