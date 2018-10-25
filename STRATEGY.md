# 优雅引用第三方框架

很多时候，我们会引用第三方框架，比如网络加载框架
[Volley](https://github.com/google/volley)、[OkHttp](https://github.com/square/okhttp)、[Retrofit2](https://github.com/square/retrofit)。
现在最流行的也是`Retrofit2`,其是基于`OKHttp`进行的再次封装。      
![网络请求发展史](http://upload-images.jianshu.io/upload_images/4314397-f0840e52bb80478c.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240) 

还有一些图片加载框架：[Glide](https://github.com/bumptech/glide)、[Picasso](https://github.com/square/picasso)、
[ImageLoader](https://github.com/nostra13/Android-Universal-Image-Loader)、[Fresco](https://github.com/facebook/fresco)
`ImageLoader`几年前就已经停止维护了，但是其却是最早的图片加载框架。从流行程度上来说，现在是`Glide`使用最广泛。

## 那么，问题来了
某天，老板让做一个图片比较多的App，就是图片加载，没有其他的什么。然后你就马不停蹄的引入了一个框架，然后就刹不住车的使用了这个框架。
一段时间过后，老板说，这个图片可不可以显示gif图呢？然后在老板的淫威之下，没办法，又只能改，这个时候改突然发现，卧槽，这个怎么哪哪都是呀。

怎么
