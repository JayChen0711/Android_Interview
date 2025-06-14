# 什么是安卓架构组件，有什么用途？
- 安卓架构组件是一组由谷歌开发的软件包，用于帮助开发者设计出具备健壮性、可测试、可维护性的安卓应用。
- 这些软件包为开发者共同面临的一些问题提供了解决方案，例如管理UI的生命周期变化、高效地处理数据持久化。

# 安卓架构组件是如何在App复杂性管理上面起作用的？
- 生命周期感知：这些组件都可以感知到生命周期的变化，有助于避免内存泄漏与崩溃。它们通过感知Activity/Fragment的生命周期的方式自动管理数据更新。
- 数据一致性：ViewModel与LiveData可以保证在App配置变化的时候保持数据的一致，例如屏幕方向变化。避免了在Activity/Fragment里面进行手动处理。
- 可测试性：架构组件提供的结构有利于模块化，让开发者更容易对其编写单元测试。
- 减少样板代码：通过Room与其它组件，大大减少了样板代码，让代码库更干净更容易维护。
- 有利于MVVM架构：这些组件天然地符合Model-View-ViewModel架构的要求，这个广泛应用的架构维护了一个清晰的UI与数据逻辑之间的分离。

# 安卓架构组件主要包含了哪些？
- ViewModel：使用基于生命周期的方式保存与管理UI相关的数据。它保证了数据在App配置变化（例如屏幕方向变化）前后的一致性，避免了没必要的数据重新加载或重新创建过程。
- LiveData：一种生命周期感知的可观察数据持有者。它确保了UI组件只有在活跃状态下才能观察到LiveData的数据变化。避免了内存泄露或者是控件在后台时收到数据更新导致的奔溃。
- Room：一个对SQLite做了抽象化层的数据库软件包，让开发者更容易地去管理本地数据。Room包含编译时对SQL查询语句的检查，使用注解简化了对数据库的操作，更减少了一些SQL的样板代码。
- Repository：尽管Repository不是一个正式的软件包，它确实一个流行的抽象化的数据访问的架构模式。它工作时就像是一个唯一的数据源，管理着来自不同源头的数据，例如本地数据库、网络数据。并提供简洁的数据访问API。
- Navigation Component：用于管理App内部的跳转。支持多种复杂的跳转行为，例如底部导航、标签导航、屏幕边抽屉导航。同时也提供了参数类型安全检查。
- WorkManager：一个可靠的后台计划任务规划的软件包。特别是需要确保任务必须执行的情况下会很有用，例如在后台同步数据。

# LivecycleOwner
- LivecycleOwner是一个接口，它代表一个具备安卓生命周期的实体。这类组件具备了明确的生命周期定义，例如Activity与Fragment，这样它就具备了去持有并观察其它具备生命周期感知的组件的能力，例如LiveData与ViewModel。既提高了资源管理的效率，又避免了内存泄漏，因为只有在活跃状态下，它才会观察到数据更新。

# 为什么要使用生命周期感知的控件？
- 配合LifecycleOwner使用生命周期感知的组件（例如LiveData）可以避免内存泄露，这是因为当观察者的生命周期不在活跃状态的时候，它会被自动移除，减少了手动去清理的工作。
- 当一个LifecycleOwner（例如Activity）观察LiveData时，UI的更新只有在组件处于活跃状态才会发生。如果组件是停止或者销毁状态，更新会被暂停或者抛弃。
- 配合LifecycleOwner时，组件可以对生命周期的变化做出精确的反应，保证用户可以得到一致的体验。例如用户输入的数据不会因为屏幕方向改变而丢失。
