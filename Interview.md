## 基础部分
### 一 布局
1. LinearLayout 和 RelativeLayout的性能（层级有关）
2. ViewStub的作用
3. include 标签和 merge标签
4. android:gravity与android:layout_gravity的区别

### 二 四大组件
1. Activity 的启动模式（ActivityA->ActivityB -> ActivityA）
2. activity的startActivity和context的startActivity区别
   如果从其他Context中启动Activity则必须给intent设置Flag
3. Context的个数   
4. Service 是运行在主线程吗？能在service中做耗时操作吗？

### 三 线程
1. 非UI线程能够是否能够更新UI？
2. 线程安全和线程非安全的区别

### 四 存储
1. android中的存储有哪些？
2. SharedPreferences commit和apply的区别（同步和异步）

### 五 View
1. View的绘制流程 measure，layout,draw
2. 为什么 view的 onLayout()方法是空的？

### 六 内存
1. 什么是内存泄漏？常见有哪些方面？
2. 如何处理OOM？
3. java中有几种引用类型？分别在什么情况下回被回收

## 综合：
1. OkHttp中涉及的设计模式
2. 如果在无网络的时候想看以前的内容怎么处理？
3. 如果应该的方法数超过64K怎么办？（multiDexEnabled true）
4. Retrofit2.0 网络请求，返回结果如果类型不能保证一致
	（空的时候是列表，不为空是对象）能够解析吗，如果能怎么处理？
5. compileSdkVersion 和 targetSdkVersion的区别？
   2.1 compileSdkVersion 和 supportLibrary 之间的版本必须保持一致么？
6. 架构MVP和MVC之间的区别
7. 你在项目中遇到的最大的困难是什么，怎么解决的？
