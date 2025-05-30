# 编译打包
    ./gradlew assembleDebug

# 查看Gradle版本
    ./gradlew -version

# 查看所有模拟器
    emulator -list-avds

# 启动模拟器
    emulator -avd <emulator_name>
    emulator -avd Medium_Phone_API_35

# 安装APK
    adb install -r app/build/outputs/apk/debug/app-debug.apk

# 启动App
    adb shell am start -n <package_name>/<activity_name>
    adb shell am start -n com.example.myapp/.MainActivity

# Windows PowerShell 一行命令打包+安装+启动
    ./gradlew assembleDebug ; adb install -r app/build/outputs/apk/debug/app-debug.apk ; adb shell am start -n com.jayc.countdownlocker.debug/com.jayc.countdownlocker.MainActivity