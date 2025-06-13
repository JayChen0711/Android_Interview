# 设置键盘快捷键
- File -> Settings -> Keymap

# 集成其它服务的账号
- Settings -> Version Control -> GitHub -> Add Account
- Tools -> Firebase -> Crashlytics 可直接查看线上的crash报告

# 集成插件
- Azure DevOps or Jira
- Github Workflows
- JsonToKotlin
- Dart, Flutter and Kotlin Multiplatform
- 查看已安装插件 Settings -> Plugins -> Installed

# 加速构建
- 设置全局内存使用量 Appearance & Behavior -> System Settings -> Memory Settings
- 设置项目的内存使用量


    org.gradle.jvmargs=-Xmx2g -XX:MaxMetaspaceSize=512m -XX:+UseParallelGC
    org.gradle.daemon=true
    org.gradle.parallel=true
    org.gradle.caching=true
    org.gradle.configureondemand=true

# 创建自定义的代码文件模板
- Preferences -> Editor -> File and Code Templates


    package ${PACKAGE_NAME}
    
    class ${CLASS_NAME}UseCase {
        suspend fun execute(): kotlin.Result<${RESULT_NAME}> {
            TODO("Not yet implemented")
        }
    }

# 导入/导出IDE Settings
- Settings -> Manage IDE Settings -> Export Settings