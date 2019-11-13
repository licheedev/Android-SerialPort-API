# Android-SerialPort-API

用这个API写的一个小工具 [Android-SerialPort-Tool](https://github.com/licheedev/Android-SerialPort-Tool)

基于这个API封装的库 [SerialWroker](https://github.com/licheedev/SerialWorker)，有分包、粘包疑惑的，可以参考一下里面的DEMO

[![](https://jitpack.io/v/licheedev/Android-SerialPort-API.svg)](https://jitpack.io/#licheedev/Android-SerialPort-API)

**Gradle 引用**

1. 在根build.gradle中添加

```
allprojects {
    repositories {
        ...
        maven { url 'https://jitpack.io' }
    }
}
```

2. 子module添加依赖

```
dependencies {
        implementation 'com.github.licheedev.Android-SerialPort-API:serialport:1.0.1'
}
```

**修改`su`路径**

```java
// su默认路径为 "/system/bin/su"
// 可通过此方法修改
SerialPort.setSuPath("/system/xbin/su");
```
