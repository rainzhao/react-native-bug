## 开发React-native中遇到的bug

### 1. adb devices 无设备
* 首先检查platform-tools是否加入了环境变量。
* 先运行`adb kill-server`，然后运行`adb start-server`

### 2. 红屏问题"Could not get BatchedBridge, make sure your bundle is packaged correctly"

### 3. adb reverse tcp:8081 tcp:8081 and it says error: closed
*	第一种情况你的platform-tools版本过低，这个命令只支持android 5.0以上
	*	解决办法：
		*	Android SDK Tool (update it to latest version)
		*	Android SDK Platform-tools (update it to latest version)
		*	Android SDK Build-tools (update it to latest version)
		*	Android Support Repository under Extra folder (update it to latest version)
* 第二种情况你的8081端口被占用了
	* 解决方案一：在运行react-native start时添加参数--port 8800
	* 