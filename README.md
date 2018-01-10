# Android-SerialPort-API
Google官方的Android串口通信Demo，修改成Android Studio项目

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
        compile 'com.github.licheedev.Android-SerialPort-API:serialport:1.0.1'
}
```

**修改`su`路径**

```java
// su默认路径为 "/system/bin/su"
// 可通过此方法修改
SerialPort.setSuPath("/system/xbin/su");
```
