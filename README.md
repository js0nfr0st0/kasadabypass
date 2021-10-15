# Nike web如何登陆|协议登录|nike bot

## how to login nike|Bypass kasada 429




​        众所周知，如何用协议的方式登录nike web端，需要以下几部分，_abck，bmsz；

当然也可以说sensor-data；

当然还有4.3号加入的x-kpsdk-ct、x-kpsdk-cd；那么我们逐项的说；

1、abck，bmsz的方式登录，废话少说，我们直接上效果；

[![gYQoSx.png](https://z3.ax1x.com/2021/05/09/gYQoSx.png)](https://imgtu.com/i/gYQoSx)

​	这里会遇到几个问题，分别是；abck，bmsz，和x-kpsdk-ct、x-kpsdk-cd

由于和之前帖子有重叠部分，我们就详细说一下abck，bmsz的生成原理；

1、首先说，abck，bmsz的用途，基本上全篇无法绕过的是他从登录、到下单到底一系列流程。均会涉及到这两个值；也就是俗称到底过盾，这里主要探讨下他是如何才能过。

步骤

a、访问任意地址，获取abck,bmsz；

b、通过staticweb的GET,POST,POST请求去验证对应的sensor

c、验证后，可用。



那么在探讨sensor如何产生，其实我们很容易就可以看到sensor其实是staticweb的get请求的js；

那么这里你会发现，实际上这里涉及非常非常多的fingerprint 也就是很多指纹信息；

那么问题就衍生出2个问题；

1、如何模拟一个正确的sensor，和如何模拟多个sensor；

-----

首先说如何模拟第一个sensor，这个又有N种方法，我先说个看起来最lowB的；

也就是你只需要把这个js，反混淆一下。就可以基本上拿到比较可读的，然后在browser环境下执行即可；

当然这里又涉及，他必须要两次sensor验证，而且第二个sensor的生成，需要第一个sensor的内容；

我们完全可以在broswer环境执行两次即可；

2、写累了。而且有点跑题，我们接着说回登录。

3、首先我们可以抓取一个登陆的数据包；

[![gYlJhR.png](https://z3.ax1x.com/2021/05/09/gYlJhR.png)](https://imgtu.com/i/gYlJhR)



我们可以很清晰的看到，他有N个cookie和header，非常烦人；

通过反复测试，我们可以确认基本上仅有四项是需要注意的，abck,bmsz、x-kpsdk-ct、x-kpsdk-cd

前面的abck、bmsz会造成403问题

后面的x-kpsdk-ct、x-kpsdk-cd会造成429问题；



流程：

当我们准备好这四项的时候，只需要模拟数据包既可做到登录了；





效果展示：

[![gY3awD.png](https://z3.ax1x.com/2021/05/09/gY3awD.png)](https://imgtu.com/i/gY3awD)
[![gY3dTe.png](https://z3.ax1x.com/2021/05/09/gY3dTe.png)](https://imgtu.com/i/gY3dTe)
[![gY3UeO.png](https://z3.ax1x.com/2021/05/09/gY3UeO.png)](https://imgtu.com/i/gY3UeO)






