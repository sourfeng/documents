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
某天，老板说，这个加载gif好是好呀，但是加载静态图片的时候不清醒呀？我还是想用原来的那个方式加载静态图片。估计听到这里，心里有一万只草泥马呼啸而过。
牢骚发完，还的继续改呀。    
还是按照原来的方式？那就在原来的基础上在加一个状态
```java
public class ImageLoaderUtils {    

    public static void loadImageView(Context context, String imgUrl, ImageView view,int status) {
        if(status ==1){
            ImageLoader.getInstance().displayImage(imgUrl, view, mImageOptions);
        }else if(status == 2){
            Glide.with(context).load(imgUrl).into(view);
        }else{
        ...
        }
    }
}
```
这样写也没有问题，但是如果后面有人来膜拜你的代码的时候，发现到处都是这些个 1，2，3状态的时候，那得多尴尬，后面维护的时候自己都想抽自己两个大嘴巴子，着血的都是啥！！！

## 引入策略模式

怎么解决上面的问题呢？需要一个方式方法，让我能够随意的切换那种模式。所以引入了策略模式。

**首先，我们定义一个策略接口，用于存放框架之间会共同使用的方法，例如：默认加载图片，加载GIf等等。**
```java
public interface BaseImageLoaderStrategy {
    /**
    * 默认方式加载图片
    * @param context 上下文
    * @param view View 控件
    * @param imgUrl 图片URL
    */
    void loadImage(Context context, ImageView view, Object imgUrl);

}
```
**接下来写实现类，这里我使用A为例，简单写一个实现类。**
```java
/**
* A的实现类
**/
public class UniversalLoaderStrategy implements BaseImageLoaderStrategy {

   private DisplayImageOptions mImageOptions;
   public static final int UNIVERSAL_STRATEGY =1;
   /**
   * 初始化加载配置
   */
   private void initOptions() {   
        ImageLoaderConfiguration configuration = ImageLoaderConfiguration.createDefault(this); 
        ImageLoader.getInstance().init(configuration);

        mImageOptions = DisplayImageOptions.createSimple();
   }   

    @Override
    public void loadImage(Context context, ImageView view, Object imgUrl) {
        ImageLoader.getInstance().displayImage(imgUrl, view, mImageOptions);
    }

}
```

**完成实现类后，最后写一个调用的工具类就完成了封装。**

```java
public class ImageLoaderUtils {

    private BaseImageLoaderStrategy mImageLoaderStrategy;
    
    
    private ImageLoaderUtils() {
            //默认使用A
            mImageLoaderStrategy = new UniversalLoaderStrategy();   
        }

   /**
    * 设置图片框架策略
    * @param strategy  图片框架策略
    **/
    public static void setImageLoaderStrategy(BaseImageLoaderStrategy strategy) {
        if (strategy != null) {
            mImageLoaderStrategy = strategy;
        }
    }


   /**
    * 调用默认加载图片
    **/
    public static void loadImage( Context context, ImageView view, Object imgUrl) {
        mImageLoaderStrategy.loadImage(context,view,imgUrl);
    }
}
```
**最后就可以调用**
```java
ImageLoaderUtils.loadImage(context, imageView, imgUrl);
```
## 怎么随意所欲呢？

首先还得写一个B框架的策略
```
public class GlideLoaderStrategy implements BaseImageLoaderStrategy {

   private RequestOptions mOptions;
   private ImageLoaderConfig mConfig;
   
   public static final int GLIDE_STRATEGY =2;
   /**
   * 初始化加载配置
   */
   private RequestOptions getOptions() {
    if (mOptions == null) {
        mOptions = new RequestOptions();
        mOptions.error(mConfig.getErrorPicRes())
                .placeholder(mConfig.getPlacePicRes())
                //下载的优先级
                .priority(Priority.NORMAL)
                //缓存策略
                .diskCacheStrategy(DiskCacheStrategy.ALL);
       }
     return mOptions;
   }   

    @Override
    public void loadImage(Context context, ImageView view, Object imgUrl) {
       Glide.with(context)
                .load(imgUrl)
                .apply(getOptions())
                //先加载缩略图 然后在加载全图
                .thumbnail(Contants.THUMB_SIZE)
                .into(view);
    }

}
```
如上就是今天的分享内容，欢迎指正错误～


