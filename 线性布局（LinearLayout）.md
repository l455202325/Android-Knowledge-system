#### 线性布局,顾名思义,指的是整个Android布局中的控件摆放方式是以线性的方式摆放的
线性布局排列方式有：
* 纵向：android:orientation="vertical"
效果

![](http://upload-images.jianshu.io/upload_images/938571-5c0dd8ed3469fc44.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

* 横向：android:orientation="horizontal"
 效果
 
![](http://upload-images.jianshu.io/upload_images/938571-a54af9ab9a776e16.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

> 上面是线性布局的基本样式，平时在开发中线性布局使用也是相对较多的一种布局方式
其中现象布局还有一个属性使用较多就是layout_weight，这个是占用剩余空间的权重
一般在使用时是针对LinearLayout的子元素，当然LinearLayout也可以设置父容器的总权重值

##### 下面来看看 两个子元素的设置效果

![布局文件.png](http://upload-images.jianshu.io/upload_images/938571-f33ce6b64919eb82.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/720)![样式效果.png](http://upload-images.jianshu.io/upload_images/938571-badf8c686107e647.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

> 上面的样式及效果说明：
首先线性布局是横向布局你，子元素中所有元素的宽度都设置为0，然后在设置对应的权重值，第一个为1，第二个为2，那么他们就各自占父元素的1/3和2/3。

##### 现在给父元素设置一个android:weightSum="5"，再看看效果


![布局文件.png](http://upload-images.jianshu.io/upload_images/938571-f72908bb13f06895.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)![效果.png](http://upload-images.jianshu.io/upload_images/938571-fc08320480625c7f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

> 这样给父元素设置了weightSum之后 子元素的权重值就受到父元素的权重值得影响，子元素的权重值之和不能大于父元素的权重，如果子元素的权重值大于父元素的weightSum值，那么只取前面的，后面的元素就不会出现，页面也就看不到了。这种情况我也就不截图了，大家可以自行尝试。

##### 下面再看看不给子元素设置默认宽度值为0dp，设置为wrap_content

![布局文件.png](http://upload-images.jianshu.io/upload_images/938571-841aa44ec6b0d0be.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)![效果.png](http://upload-images.jianshu.io/upload_images/938571-ae1e7feddda90cb1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> 看到这种情况，回想到是不是我这权重不起作用了呢，怎么没有达到预期的效果，为什么第一个明明应该占1/3，为啥成这个样子了呢？其实是没有问题的，一开始我们就说了，这个layout_weight是占**剩余空间**的权重，出现这种情况就不奇怪了。

> ### 总结：
> 在实际开发中我们用的最多的就是线性布局，再现性布局中，我个人认为最应该掌握的就是线性布局的权重值的使用。我一般使用的时候都会按照开始的那个效果，让所有子元素对应的宽或者高设置为0dp，这样就会按照咋们所想的效果来展示了，当然后面这样了例子在某些特殊场景下还是可以起到很好的作用的。

> #### 代码只会按照你所写的方式运行，不会按照你想的方式运行
