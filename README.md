# Android-SerialPort-API
[Fork](https://code.google.com/archive/p/android-serialport-api/)自Google开源的Android串口通信Demo，修改成Android Studio项目 

This lib is a [fork](https://code.google.com/archive/p/android-serialport-api/) of the Android serial port communication Demo open sourced by Google.

## Installation & Usage
**Gradle**

添加依赖:

Add the dependency:

```
allprojects {
    repositories {
        ...
        jcenter()
        mavenCentral() // since 2.1.3
    }
}

dependencies {
        implementation 'com.licheedev:android-serialport:2.1.3'
}
```

**Import**

```java
import android.serialport.SerialPort;
```

**`su` path**

In order to read/write to a serial port in Android you'll need `su` binary installed on device (this can be done by rooting the device). Usually Android devices that has the ability to communicate with serial ports have `su` installed on the default path `"/system/bin/su"`. To change this use:

```java
// su默认路径为 "/system/bin/su"
// The default path of su is "/system/bin/su"
// 可通过此方法修改
// If the path is different then change it using this
SerialPort.setSuPath("/system/xbin/su");
```

**Usage**

```java
// 默认8N1(8数据位、无校验位、1停止位)
// Default 8N1 (8 data bits, no parity bit, 1 stop bit)
SerialPort serialPort = new SerialPort(path, baudrate);

// 可选配置数据位、校验位、停止位 - 7E2(7数据位、偶校验、2停止位)
// or with builder (with optional configurations) - 7E2 (7 data bits, even parity, 2 stop bits)
SerialPort serialPort = SerialPort 
    .newBuilder(path, baudrate)
// 校验位；0:无校验位(NONE，默认)；1:奇校验位(ODD);2:偶校验位(EVEN)
// Check bit; 0: no check bit (NONE, default); 1: odd check bit (ODD); 2: even check bit (EVEN)
//    .parity(2) 
// 数据位,默认8；可选值为5~8
// Data bit, default 8; optional value is 5~8
//    .dataBits(7) 
// 停止位，默认1；1:1位停止位；2:2位停止位
// Stop bit, default 1; 1:1 stop bit; 2: 2 stop bit
//    .stopBits(2) 
    .build();
    
// read/write to serial port - needs to be in different thread!
InputStream in = serialPort.getInputStream();
OutputStream out = serialPort.getOutputStream();

// close
serialPort.tryClose();
```

实现方式参考

Implementation reference
1. Check [sample project](https://github.com/licheedev/Android-SerialPort-API/tree/master/sample)
2. https://juejin.im/post/5c010a19e51d456ac27b40fc
