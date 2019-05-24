# 缘起

我们在项目中有时需要使用一些第三方的sdk，比如支付宝支付SDK，虽然官方提供的aar下载，但是却不能在gradle中直接引用，尤其是一些二开的sdk，比如我的另一项目af-pay，其中就需要依赖原生的支付宝sdk，支付宝sdk升级后，原来的jar换成了aar，由于Android module不能直接使用aar，导致我的af-pay library没法升级。为此，为了大家能够简单使用这类sdk，专门建立了一个aar-ref的项目，为简化使用这些aar。

以下是一个示例，以支付宝支付sdk作为示例

## 官方使用方式

1. 去支付宝开放平台下载最新的支付宝aar sdk，比如`alipaySdk-15.5.9-20181123210601.aar`，放到app的libs目录下
2. app/build.gradle中添加本地aar所在的目录及依赖
```gradle
repositories {
    jcenter()
    flatDir { dirs 'libs' }
}
dependencies {
    compile fileTree(include: ['*.jar'], dir: 'libs')
    compile (name: 'alipaySdk-15.5.9-20181123210601', ext: 'aar')
```

## 使用aar-ref

app/build.gradle中添加依赖

```gradle
dependencies {
    compile fileTree(include: ['*.jar'], dir: 'libs')
    compile 'cn.ieclipse.aar-ref:alipaySdk:15.6.2'
}
```

是不是简单的许多，而且，更重要的一点是，它还可以在library module中使用

# SDK 列表

|名称            |SDK                | 最新版本    | 项目链接     |  说明 |
| -------------- |:----------------:|:----------:|:-----------:|:--------:|
| 支付宝          |[alipaySdk](http://jcenter.bintray.com/cn/ieclipse/aar-ref/alipaySdk)         |15.6.2      |Jamling 上传           | 已是最新
| 百度自动升级     |[bd_autoupdate_sdk](http://jcenter.bintray.com/cn/ieclipse/aar-ref/bd_autoupdate_sdk) |1.3.1       |Jamling 上传             | 上百度市场必须集成
| 360自动升级     |[360update](http://jcenter.bintray.com/cn/ieclipse/aar-ref/360update) |7.0.3       |[Jamling/MarketUpdateSDK](https://github.com/Jamling/MarketUpdateSDK)             |  上360市场必须集成
| 银联支付     |[unionpay](http://jcenter.bintray.com/cn/ieclipse/aar-ref/unionpay) |3.5.4       |[Jamling/af-pay](https://github.com/Jamling/af-pay)             |  

# 贡献

欢迎大家踊跃参加，不断发展壮大aar-ref项目。如需贡献，请提交包含.aar文件的PR，并在PR中说明aar的用途，版本号及来源信息。


