# LiveData
- 一种自带生命周期感知的可观察的数据持有类。它保证了UI控件只有在活跃状态才能观察到数据变化，避免了UI在后台遇到数据更新时可能发生的内存泄漏或奔溃。
- map是把一个A类型的LiveData转变成B类型的LiveData。switchMap是把A类型的LiveData的每个数据都转变成一个新的B类型的LiveData。适用于不关心旧的B类型LiveData的返回的情况。例如进行地名搜索的时候，String类型的地名数据switchMap成地址实体类型的LiveData，每次输入新的关键词都会生成新的LiveData并忽略上次搜索的结果。
- LiveData一般用于单数据源的情况。MediatorLiveData适用于多数据源的情况，它可以把多个LiveData源合并成单一的LiveData来使用。通过addSource方法的Observer onChanged方法体对新到的数据进行整合并set到MediatorLiveData的Value。
- 

