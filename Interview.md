## 基础部分
### 一 java基础
1. equals与==的区别
2. 面向对象设计原则
3. 静态块的作用是什么？
4. try catch finally，try里有return，finally还执行么？
3. include 标签和 merge标签
4. android:gravity与android:layout_gravity的区别

### 二 四大组件
1. Activity 的生命周期（ActivityA->ActivityB -> ActivityA）
2. 当前Activity转到新的Activity界面或按Home键回到主屏经过的生命周期
3. Activity返回前台经过的生命周期
4. Activity退居后台，且系统内存不足， 系统会杀死这个后台状态的Activity，此时这个Activity的引用还在栈中吗？
   若再次回到这个页面会经过生命生命周期
5. Activity的启动模式有几种，分别是
6. 若singleTop 启动了如果新Activity已经位于任务栈的栈顶,那么此Activity会调用onCreate，onStart，onResume吗？
7. singleInstance启动的activity启动之后，后续请求会重启再次创建此Activity吗？
8. Service 是运行在主线程吗？能在service中做耗时操作吗？
9. 一个Activity可以关联多个Fragment，那么Activity的onCreate() 和 Fragment的onCreate() 方法谁先调用？
10. 如果ActivityA启动ActivityB时，ActivityA的onPause()进行了耗时操作，那么这个启动能成功吗？能成功会出现一种什么样的现象？

### Context
1. 创建对话框时能够传Application的context吗？
2. Context的数量
3. Activity和Service以及Application的Context是一样的吗？

### 三 线程
1. 线程间通信依靠什么？Handler Looper MessageQueue Message
2. 非UI线程能够是否能够更新UI？
3. 线程安全和线程非安全的区别

### 四 存储
1. android中的存储有哪些？
2. SharedPreferences commit和apply的区别（同步和异步）

### 五 View
1. View的绘制流程 measure，layout,draw
2. 为什么 view的 onLayout()方法是空的？

### 六 内存
1. Java 程序运行时的分配的内存存储空间有哪几种？（静态区，栈，堆）
2. String A = new String("A") 分别存储在哪儿？
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

