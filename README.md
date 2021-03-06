# 控件不显示可能是哪些原因？

控件不显示可能是哪些原因？
是日常开发中,特别是对于初学者而言,我们编写代码,一步一步的验证的时候,时常会出现控件无法显示的情况, 这里我总结了几种可能出现控件不显示的情况和原因, 希望能对iOS初学者能提供一些解决问题的思路和有更多的帮助:

*某个控件显示不出来可能导致的原因：
### 1. frame属性，是否为0，或者设置的位置不对
在开发中,特别是在自定义某些控件的属性的时候, 对于控件的frame如果没有设置,或者设置错误了,控件肯定是不会显示正常的,所以当你遇到控件显示不正常的时候,第一个需要思考的就是控件本身的frame属性是否正常;

### 2. hidden =YES
多数情况下,我们需要对控件的hidden属性,也就是是否隐藏,作一些自定义, 所以,如果你检查了frame属性,确定是对的,但是控件还是不能显示,那么你可以来考虑一下是不是在某个时刻我们对这个控件的hidden属性做了设置;

### 3.是否添加到了父控件中
还有一种情况,那就是,当我们需要把某个控件添加到一个父容器(父控件)中才会显示的时候,如果,我们忘记了添加的步骤,也是不会显示控件的,所以,这个时候,你不妨来检查一下这个方面;

### 4. Alpha <= 0.01
通过苹果的官方文档,我们知道,当一个控件的透明度大于>0.01的时候,是可以监听事件的,否则(<=0.01),是无法监听事件的, 所以,如果Alpha<= 0.01.系统就认为这个控件不存在,此时不能监听事件,当然,也就在运行的是无法查看到控件了,
### 5.被其他控件挡住了。 
 控件与控件之间都是有先后层叠次序的, 如果我们需要显示的控件被其他控件给挡住了,那肯定是看不到控件的显示的,也就是我们常说的:后添加的控件默认是添加在最上层的;

这个时候,我们可以去检查一下控件的层叠次序,如果,你已经可以固定某一个控件在最上面,你可以调用一个方法,把它始终置于最上层: 如:

   [self.view bringSubviewToFront:redView];
   通过bringSubviewToFront:这个方法,你就可以始终把某一个控件置于最上层, 当然,有最上层也就有最下层,如下:
   //把中间图片按钮放置在所有图层的最上面

   [self.viewbringSubviewToFront:self.minidleIamgeViewButton];

   //把背景图片始终置于最下面一层

   [self.viewsendSubviewToBack:self.downImageView];

### 6.检查父控件的上面这5种情况。
如果,上面5中情况,你都检查了,还是没有找出原因,那么可能出现问题的是你的父控件了,所以,你可以在逐步的检查父控件的这几种情况;



上面的小总结,是我日常开发中的一些思考,希望能给大家带来帮助,
