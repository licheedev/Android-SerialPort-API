# Android-SerialPort-API

**Gradle 引用**

添加依赖

```
dependencies {
        implementation 'com.licheedev:android-serialport:2.1.2'
}
```

**修改`su`路径**

```java
// su默认路径为 "/system/bin/su"
// 可通过此方法修改
SerialPort.setSuPath("/system/xbin/su");
```

**可选配置数据位、校验位、停止位**

实现方式参考
> https://juejin.im/post/5c010a19e51d456ac27b40fc

```java

// 默认8N1(8数据位、无校验位、1停止位)
SerialPort serialPort = new SerialPort(path, baudrate);

// 7E2(7数据位、偶校验、2停止位)
SerialPort serialPort = SerialPort //
    .newBuilder(path, baudrate) // 串口地址地址，波特率
    .parity(2) // 校验位；0:无校验位(NONE，默认)；1:奇校验位(ODD);2:偶校验位(EVEN)
    .dataBits(7) // 数据位,默认8；可选值为5~8
    .stopBits(2) // 停止位，默认1；1:1位停止位；2:2位停止位
    .build();
```
