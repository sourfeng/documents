# 优雅引用第三方框架

很多时候，我们会引用第三方框架，比如网络加载框架
[Volley](https://github.com/google/volley)、[OkHttp](https://github.com/square/okhttp)、[Retrofit2](https://github.com/square/retrofit)。
现在最流行的也是`Retrofit2`,其是基于`OKHttp`进行的再次封装。      
![网络请求发展史](http://upload-images.jianshu.io/upload_images/4314397-f0840e52bb80478c.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240) 

还有一些图片加载框架：[Glide](https://github.com/bumptech/glide)、[Picasso](https://github.com/square/picasso)、
[ImageLoader](https://github.com/nostra13/Android-Universal-Image-Loader)、[Fresco](https://github.com/facebook/fresco)
`ImageLoader`几年前就已经停止维护了，但是其却是最早的图片加载框架。从流行程度上来说，现在是`Glide`使用最广泛。

## 那么，问题来了
某天，老板让做一个图片比较多的App，就是图片加载，没有其他的什么。然后你就马不停蹄的引入了一个框架，然后就刹不住车的使用了这个框架。一段时间过后，老板说，这个图片可不可以显示gif图呢？然后在老板的淫威之下，没办法，又只能改，这个时候改突然发现，卧槽，这个怎么哪哪都是呀。冥思苦想之后，完蛋，还得自己一个一个加，好像无解呀？命苦啊！

## 那么，怎么办呢？
从程序的角度出发，以防老板这些大佬再出幺蛾子，要杜绝这种事情的发生，那么就需要一次性解决，不然，以后就疲于奔命了。

**分析问题：**
1. 第一个框架（后面用A表示）不支持gif，那么就得找一个支持gif的框架（后面用B表示），但是支持gif框架的加载方式和不支持gif的加载方式不一样呀，如下所示：

```java
// A框架
ImageLoader.getInstance().displayImage(imgUrl, view, mImageOptions);

//B框架
Glide.with(context).load(url).into(imageView);
```
既然展示方式不一样，我们就自己写个方法，变成一样的就好了呀，所以又有了下面的方法：

```java
// 简单的封装A框架
private DisplayImageOptions mImageOptions;

    public ImageLoaderUtils(){
        //配置UIL的初始化
        ImageLoaderConfiguration configuration = ImageLoaderConfiguration.createDefault(this); 
        ImageLoader.getInstance().init(configuration);

        mImageOptions = DisplayImageOptions.createSimple();
    }

    //默认加载
    public static void loadImageView(Context context, String imgUrl, ImageView view) {
        ImageLoader.getInstance().displayImage(imgUrl, view, mImageOptions);
    }
```
那么所有对外的展示方式就变成了
```java
ImageLoaderUtils.loadImageView(context,url,imageView);
```
如果现在老板，再让我来替换gif的加载，我只想说 **So Easy！**

```java
/**
* 使用B框架替换A框架的工具类
**/
public class ImageLoaderUtils {    

    //默认加载
    public static void loadImageView(Context context, String imgUrl, ImageView view) {
        Glide.with(context).load(imgUrl).into(view);
    }
}
```
哇塞，突然发现自己慢慢都是成就感。现在有一种，走向人生巅峰的感觉，高处不胜寒啊！

## 麻烦不断
某天，老板
