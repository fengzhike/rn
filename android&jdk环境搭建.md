# 工具/原料
1. JDK(Java Development Kit)
2. Android SDK（Android Software Development Kit）
# Java 安装与环境变量
## 安装
1. 将下载的jdk-8u121-windows-x64.exe安装于制定路径
2. 安装jdk会自动安装jre
3. 安装完成之后，可以用下述方法检查JDK是否安装成功：打开cmd窗口，输入
```
    java -version
```
    出现java版本号，即安装成功
## 配置环境变量
1. 右击开始栏的计算机，属性->高级系统设置->环境变量->系统变量->新建。创建JAVA_HOME变量，变量值为JDK在电脑上的安装路径。
2. 创建JAVA_HOME环境变量。value为jdk安装路径
3. 然后在变量列表里查看Path变量，Path变量使得系统可以在任何路径下识别java命令，如果不存在，则新建变量 Path，否则选中该变量，单击“编辑”按钮，将光标移动到变量值的输入框中内容的最前面，在文本框的起始位置添加“%JAVA_HOME%\bin;%JAVA_HOME%\jre\bin;”或者是直接“%JAVA_HOME%\bin;”，单击确定按钮
4. 在变量列表里查看CLASSPATH 变量，如果不存在，则新建变量CLASSPATH，否则选中该变量，单击“编辑”按钮，在“变量值”文本框的起始位置添加“.;%JAVA_HOME%\lib\dt.jar;%JAVA_HOME%\lib\tools.jar;”
5. 配置完成这三项之后，需要测试下是否成功。打开cmd窗口，输入javac
```
  javac
```
  出现javac的选项即配置成功

# Android sdk安装与环境变量配置
## 安装
1. 通过android studio 安装Android sdk
2. 下载Android sdk并安装
## 环境变量配置
1. 创建ANDROID_HOME环境变量。value为Android sdk安装路径
2. 添加Android SDK中platform-tools和tools的目录路径到Path变量值中
    “%ANDROID_HOME%\platform-tools;%ANDROID_HOME%\tools”
3. 配置完Android SDK后，需要测试下配置是否正确。打开cmd窗口，输入android –h或者adb。按下回车键出现类似下面的画面表示配置成功
4. 此时连安卓手机或者打开虚拟机，运行 adb devices 显示设备列表

# 安装react-native 并创建工程
```
  npm install -g react-native-cli
  react-native init AwesomeProject
  cd AwesomeProject
  react-native run-android
```

# 可能遇到的坑
## 5037端口被占
出现这个问题：
adb server version (32) doesn't match this client (36); killing...
error: could not install *smartsocket* listener: cannot bind to 127.0.0.1:5037:
通常每个套接字地址(协议/网络地址/端口)只允许使用一次。 (10048)
could not read ok from ADB Server *failed to start daemon *
error: cannot connect to daemon
可能是有一个原因引起的，也有可能是别的原因！
这我里因为 Genymotion模拟器的adb和sdk里的adb冲突了！
解决方法：genymotion设置中的adb设置 改成你sdk的路径！

## 设备是离线状态
adb devices
设备offline 多个adb.exe造成的，关掉进程或者删除多余的adb
