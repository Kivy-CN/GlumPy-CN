Title: GlumPy-Getting started
Date: 2017-10-01
Category: Work
Tags: Python,GlumPy,Data,Visualization


# GlumPy 中文文档翻译：上手简介

[本文档原文地址](http://glumpy.readthedocs.io/en/latest/quickstart.html)

开始上手使用一个新的库或者框架有时候可能会让人头大，尤其是要阅读超级多的参考资料的情况下。本章就仅对 GlumPy 进行一下非常简要的介绍，而不去纠结各种细节。



**主要内容**



* 创建窗口
* 绘制四边形
* 生成动画



## 创建窗口

创建一个新的窗口，这个过程代码看起来应该是比较好理解的，如下所示：
（译者注：这里的代码每一个步骤之间都是连贯的，建议读者在 ipython 里面逐个粘贴，不要错过漏掉中间的，否则运行肯定出错。所以当你遇到运行出错的时候建议先检查一下是不是中间有漏掉的。）

```Python
from glumpy import app
window = app.Window()
app.run()
```


这时候你就能在桌面上马上看到这个窗口了，可能窗口上还有一些乱七八糟的内容。这是因为我们没有对创口进行清空。所以下面这个带窗口清空的代码就更好一些：

```Python
from glumpy import app

window = app.Window()

@window.event
def on_draw(dt):
    window.clear()

app.run()
```




在这个版本的代码中，使用了 on_draw() 这个事件，每当窗口需要重绘（redraw）的时候，就会调用这个事件。在 on_draw  这个 handler 中，窗口（window）区域被清理到了默认的背景颜色—黑色。

最后调用了 app.run()，这就将控制器交给了 GlumPy 应用循环体，可以对鼠标和键盘之类的应用事件进行响应。

#### 特别注意


只有当所有的应用窗口都关闭的情况下，**run** 方法才会返回（return），除非整个程序是运行在**交互模式（interactive mode）**下。如果你使用了  --interactive 这样的参数来切换到交互模式下运行，那么 app.run() 就可能不会显示出一整块。（译者注：这句话翻译得有问题，原文是 If you start the program using the --interactive switch, the app.run() is no longer blocking，回头我再详细润色。）






## 绘制四边形

现代的 OpenGL 非常强大，但是理解起来挺难的，编写相关程序也是如此。任何的绘制操作都需要一系列的准备步骤，这就使得在不使用第三方库的情况下，绘制过程会繁琐无比。GlumPy 通过 gloo 界面，提供了一些非常简单的使用体验，gloo 可以看做是将 NumPy 和 OpenGL 结合起来的一种“胶水（glue）”。（译者注：这也是 GlumPy 名字的意义所在，GL +  NumPy = GlumPy）


接下来咱们就用 GlumPy 来绘制一个彩色的四边形吧。第一步自然还是要导入相关的模块然后创建窗口：



```Python
from glumpy import app, gloo, gl

window = app.Window()
```


然后我们要创建爱你一个 GLSL 程序，用来显示这个四边形。这就要我们先来写一个顶点（vertex）和一个片段着色器（fragment shader），这两个是要用来告诉 OpenGL 要绘制什么，以及如何绘制。目前你还不用纠结去理解这些名词概念和细节，但是要注意到一个重要的点，就是这些 OpenGL 程序都是文本形式的字符串（text strings）。


```Python
vertex = """
         attribute vec2 position;
         void main()
         {
             gl_Position = vec4(position, 0.0, 1.0);
         } """

fragment = """
           uniform vec4 color;
           void main() {
               gl_FragColor = color;
           } """

quad = gloo.Program(vertex, fragment, count=4)
```

gloo 界面的一个好处就是可以直接上传使用非常直观易于人类理解的记号来表达的数据给 GPU（图形处理单元）。position 参数直接关联到了顶点着色器（vertex shader）的位置属性，而 color 参数则直接关联了片段着色器（fragment shader）中的颜色分布。




```Python
quad['position'] = [(-0.5, -0.5),
                    (-0.5, +0.5),
                    (+0.5, -0.5),
                    (+0.5, +0.5)]
quad['color'] = 1,0,0,1  # 红色
```

最后，在 on_draw() 方法中通过 gl.GL_TRIANGLE_STRIP 来渲染这个四边形。代码如下所示：

```Python
@window.event
def on_draw(dt):
    window.clear()
    quad.draw(gl.GL_TRIANGLE_STRIP)

app.run()
```

## 生成动画

动画（animation）其实只是每个时间步长中对显示内容逐渐调整而实现的。我们还利用上面的四边形这个例子，让这个四边形随着时间而扩大和缩小。第一步需要在 on_draw() 函数中提供 dt 这个参数来跟踪记录时间，这个 dt 参数给出的是自从上次调用之后经过的时间。接下来我们首先要对顶点着色器的代码进行修改，使四边形的坐标随着时间变量的正弦值而变化。


```Python
vertex = """
         uniform float time;
         attribute vec2 position;
         void main()
         {
             vec2 xy = vec2(sin(2.0*time));
             gl_Position = vec4(position*(0.25 + 0.75*xy*xy), 0.0, 1.0);
         } """

quad = gloo.Program(vertex, fragment, count=4)
```


然后还需要对时间变量进行初始化，在每次绘制调用的时候对该变量进行更新。


```Python
@window.event
def on_draw(dt):
    window.clear()
    quad["time"] += dt
    quad.draw(gl.GL_TRIANGLE_STRIP)

quad["time"] = 0.0
quad['color'] = 1,0,0,1
quad['position'] = [(-1, -1), (-1, +1), (+1, -1), (+1, +1)]
app.run()
```







#### 特别注意


如果你想要把动画录制下来，可以在运行程序的时候添加 --record filename 这样的后缀来实现。



