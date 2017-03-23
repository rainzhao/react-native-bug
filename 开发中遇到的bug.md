## 开发React-native中遇到的bug

### 1. adb devices 无设备
* 首先检查platform-tools是否加入了环境变量。
* 先运行`adb kill-server`，然后运行`adb start-server`

### 2. 红屏问题"Could not get BatchedBridge, make sure your bundle is packaged correctly"
* 问题原因：无法拉取到bundle，可能是由于你的ip设置的不对。
	* 解决方法一：摇一摇手机，如果发现没有弹出选项，可能是手机禁止了弹框权限，开启一下权限，选择dev Settings 设置ip：端口号
	* 解决方法二：手动拉取bundle,首先在`android/app/src/main/`下新建`assets`目录然后在根目录下执行：`curl "http://localhost:8081/index.android.bundle?platform=android" -o "android/app/src/main/assets/index.android.bundle"`
### 3. adb reverse tcp:8081 tcp:8081 and it says error: closed
*	第一种情况你的platform-tools版本过低，这个命令只支持android 5.0以上
	*	解决办法：
		*	Android SDK Tool (update it to latest version)
		*	Android SDK Platform-tools (update it to latest version)
		*	Android SDK Build-tools (update it to latest version)
		*	Android Support Repository under Extra folder (update it to latest version)
* 第二种情况你的8081端口被占用了,而且无法禁止该端口号的时候:
	* 解决方案一：在运行react-native start时添加参数--port 8800
	* 解决方案二：package.json中修改"scripts"中参数, 添加端口号
	* 解决方案三：修改项目下的node_modules\react-native\local-cli\server\server.js下的方法_server的default 端口值