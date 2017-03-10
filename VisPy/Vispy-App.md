Title: VisPy APP
Date: 2017-03-05
Category: VisPy
Tags: Python,VisPy,Data,Visualization
# VisPy 中文文档：APP模块[](http://vispy.org/app.html#module-vispy.app "Permalink to this headline")



APP 模块定义了三个类：应用程序 Application，画布 Canvas，以及计时器 Timer。VisPy 在载入的时候，会创建一个默认的应用程序实例，该实例可以在模块的命名空间内通过函数调用来使用。

* * *



### `vispy.app.use_app`(*backend_name=None*, *call_reuse=True*)[](http://vispy.org/app.html#vispy.app.use_app "Permalink to this definition")


获取/创建一个默认的应用程序对象。

多次调用这个函数也是安全的，只要后端名字 backend_name 设置为 None 或者匹配已选定的后端 backend 就行。


参数:  **backend_name** : str 字符串类型或者 None

> 该参数是设置要使用的后端应用的名字。如果没有指定，VisPy 会常识自动选择一个后端。更多内容参考vispy.use()。

**call_reuse** : 布尔值

> 该参数是设置是否调用后端的 reuse() 函数，默认设为 True。默认情况下是不执行的，不过某些后端需要用到这个函数。例如在 notebook 后端里面，调用了 user_app() 之后就需要立即注入某些 JavaScript 文件。

### `vispy.app.create`()[](http://vispy.org/app.html#vispy.app.create "Permalink to this definition")

创建本地应用程序。

### `vispy.app.run`()[](http://vispy.org/app.html#vispy.app.run "Permalink to this definition")

进入本地 GUI 事件循环。


### `vispy.app.quit`()[](http://vispy.org/app.html#vispy.app.quit "Permalink to this definition")

退出本地 GUI 事件循环。

### `vispy.app.process_envets`()[](http://vispy.org/app.html#vispy.app.process_envets)

处理等候中的事件。如果主循环没有云行，就要经常运行这个函数，来保持可视化界面的交互，并保证事件系统的运行。





* * *

### class `vispy.app.A.Application`(backend_name=None)[](http://vispy.org/app.html#vispy.app.Application)

代表了 VisPy 应用程序。

这个类打包了一个本地 GUI 应用程序的实例。 VisPy 有一个默认的该类的实例，可以通过* vispy.app.use_app()*来创建或者获取。


参数:  **backend_name** : str 字符串类型或者 None

> 该参数是设置要使用的后端应用的名字。如果没有指定，VisPy 会常识自动选择一个后端。更多内容参考vispy.use()。

#### 特别注意
创建一个应用程序对象的时候，会选择一个后端，但本地后端应用对象只在 *create()* 函数被调用或者 *native* 被使用的时候才会创建。Canvas 画布 和 Timer 计时器 会自动进行创建。

#### 方法：
[`create()`](http://vispy.org/app.html#vispy.app.Application.create) 创建本地应用
[`is_interactive()`](http://vispy.org/app.html#vispy.app.Application.is_interactive) 探知用户是否要求类交互模式
[`process_events()`](http://vispy.org/app.html#vispy.app.Application.process_events) 处理所有等待中的 GUI 事件
[`quit()`](http://vispy.org/app.html#vispy.app.Application.quit) 退出本地 GUI 事件循环
[`reuse()`](http://vispy.org/app.html#vispy.app.Application.reuse) 在交互对话中重新使用应用程序时再次对应用进行调用
[`run([allow_interactive])`](http://vispy.org/app.html#vispy.app.Application.run) 进入本地 GUI 事件循环
[`sleep(duration_sec)`](http://vispy.org/app.html#vispy.app.Application.sleep) 沉睡指定的秒数


### `backend_module`[](http://vispy.org/app.html#vispy.app.Application.backend_module)

定义后端的模块对象。

### `backend_name`[](http://vispy.org/app.html#vispy.app.Application.backend_name)

应用打包的 GUI 后端名。
#### 方法：
[`create()`](http://vispy.org/app.html#vispy.app.Application.create) 创建本地应用
[`is_interactive()`](http://vispy.org/app.html#vispy.app.Application.is_interactive) 探知用户是否要求类交互模式
[`process_events()`](http://vispy.org/app.html#vispy.app.Application.process_events) 处理所有等待中的 GUI 事件
[`quit()`](http://vispy.org/app.html#vispy.app.Application.quit) 退出本地 GUI 事件循环
[`reuse()`](http://vispy.org/app.html#vispy.app.Application.reuse) 在交互对话中重新使用应用程序时再次对应用进行调用
[`run([allow_interactive])`](http://vispy.org/app.html#vispy.app.Application.run) 进入本地 GUI 事件循环
[`sleep(duration_sec)`](http://vispy.org/app.html#vispy.app.Application.sleep) 沉睡指定的秒数


### `backend_module`[](http://vispy.org/app.html#vispy.app.Application.backend_module)

定义后端的模块对象。

### `backend_name`[](http://vispy.org/app.html#vispy.app.Application.backend_name)

应用打包的 GUI 后端名。

### `creat()`[](http://vispy.org/app.html#vispy.app.Application.create)

创建本地应
### `creat()`[](http://vispy.org/app.html#vispy.app.Application.create)

创建本地应用程序。


### `is_interactive()`[](http://vispy.org/app.html#vispy.app.Application.is_interactive)

探知用户是否要求使用交互模式。

### `native`[](http://vispy.org/app.html#vispy.app.Application.native)

本地 GUI 应用程序实例。

### `process_events()`[](http://vispy.org/app.html#vispy.app.Application.process_events)

处理等候中的 GUI 事件。如果主循环没有云行，就要经常运行这个函数，来保持可视化界面的交互，并保证事件系统的运行。


### `quit()`[](http://vispy.org/app.html#vispy.app.Application.quit)

退出本地 GUI 事件循环。

### `reuse()`[](http://vispy.org/app.html#vispy.app.Application.reuse)

在交互对话中重新使用应用程序时再次对应用进行调用。当用户多次调用*use_app()*的时候，这允许后端可以在客户端内进行一些任务。例如在 notebook 后端里面，调用了 user_app() 之后就需要立即注入某些 JavaScript 文件。

### `run(allow_interactive=True)`[](http://vispy.org/app.html#vispy.app.Application.run)

进入本地 GUI 事件循环。
参数： **allow_interactive** : 布尔值

>这个参数用来表示是否允许在控制台终端下使用交互模式。默认输入 `python -i main.py` 就可以进入一个交互式的 shell，也会调用 VisPy 事件循环。在这种情况下，run() 函数会立即终结，然后在脚本执行之后，根据解释器内的输入循环来判定是否继续运行。

### `sleep(duration_sec)`[](http://vispy.org/app.html#vispy.app.Application.sleep)
休眠指定的事件（秒数）。
这是为了在 VisPy 以交互模式运行的时候降低 CPU 的负荷。更多内容可以参考 inputhook.py。

参数：  **duration_sec**: float 浮点数
>这个变量就是休眠的秒数。


### class `vispy.app.A.Canvas`(title='Vispy canvas', size=(800, 600), position=None, show=False, autoswap=True, app=None, create_native=True, vsync=False, resizable=True, decorate=True, fullscreen=False, config=None, shared=None, keys=None, parent=None, dpi=None, always_on_top=False, px_scale=1)[](http://vispy.org/app.html#vispy.app.Canvas)

这个类表示一个含有 OpenGL 环境的 GUI 元素。




参数:  **title** : str 字符串

控件的标题。

**size** : (width, height)


> 窗口的尺寸。（宽度，高度）


**position** : (x, y)

> 窗口在屏幕坐标系中的位置。

**show** : bool 布尔值

> 是否立即显示控件，默认为 False。

**autoswap** : bool

> 在一次绘制事件之后是否自动交换缓冲区。默认为 True。如果为 True，则在 `canvas.draw` 事件处理器之后，将会紧接着就调用 `swap_buffers` 这一 Canvas 方法。
**app** : Application 应用程序  或者 str 字符串


> 提供一个 VisPy 的应用程序实例，来用作后端。（默认使用 vispy.app。）如果用字符串，则根据这个字符串选择某一个应用程序作为后端，例如可用`pyglet`。可以注意一下这里的 Canvas 应用可以通过 `canvas.app` 来读取。

**create_native** : bool 布尔值

> 判断是否立即创建控件。默认为 True。

**vsync** : bool 布尔值

> 是否开启垂直同步。

**resizable** : bool 布尔值

> 是否允许窗口重新调整大小。

**decorate** : bool 布尔值

> 是否装饰你窗口。默认为 True。

**fullscreen** : bool 布尔值 或者 int 整形

> 如果是 False，则默认使用窗口模式。如果为 True，会在默认显示器上全屏。如果给出 int 值，则用此值编号的显示器来全屏显示。

**config** : dict 词典


> 含有 OpenGL 配置选项的一个词典，包含在默认配置选项中，用于环境初始化。参考 `canvas.context.config` 来看可选的选项。


**shared** : Canvas 或者  GLContext 或者  None

> 一个已经存在的 Canvas 对象，或者可分享 OpenGL 对象的环境。


**keys** : str 字符串 或  dict 词典 或 None


> 要使用的默认键映射。 如果是 `interactive`，则 ESC 和 F11 这两个键分别对应了关闭画布和切换全屏这两个功能。 如果是 `dict`，就把键映射到函数。 如果 `dict` 中都是字符串，就当做是 `Canvas` 的方法，要么就得是可调用的。


**parent** : widget-object 控件对象

> 父控件，如果对选用的后端来说这个对象存在的话。


**dpi** : float 浮点数 或 None


> Canvas 画布使用的分辨率，单位英寸的像素数。如果设置为 None，那就优先根据全局设定来探测，其次就是采用操作系统的设定。


**always_on_top** : bool 布尔值

> 是否让图像总在最顶层，如果设为 True，创建的窗口就会始终在顶层。

**px_scale** : int > 0 正整数


> 对应逻辑和物理像素之间关系的缩放参数，对后端确定的实际缩放参数的一补充。 此选项允许调整缩放参数进行测试。


#### 特别注意

Canvas 接收下列事件：

> * initialize 初始化
> * resize 重新调整大小
> * draw 绘制
> * mouse_press 鼠标按下
> * mouse_release 鼠标释放
> * mouse_double_click 鼠标双击
> * mouse_move 鼠标移动
> * mouse_wheel 鼠标滚轮
> * key_press 按键按下
> * key_release 按键释放
> * stylus 手写笔？
> * touch 触碰
> * close 关闭？接近？

mouse_double_click 鼠标双击，mouse_press 鼠标按下 和 mouse_release 鼠标释放 事件的顺序在后端之间无法保证一致。 目前只有某些后端（ Qt 和 WX ）原生支持双击; 在其他后端，要对这些鼠标事件以某一个固定的时间延迟来进行手动检测。 这可能会导致易用性问题，因为会增加操作系统在检测上话费的时间，或者又不能使用一种专门的双击按钮。




#### 方法：

[`close`](http://vispy.org/app.html#vispy.app.Canvas.close "vispy.app.Canvas.close")()  关闭当前画布 Canvas。

[`connect`](http://vispy.org/app.html#vispy.app.Canvas.connect "vispy.app.Canvas.connect")(fun)  把某个函数连接到一个事件上。

[`create_native`](http://vispy.org/app.html#vispy.app.Canvas.create_native "vispy.app.Canvas.create_native")()  如果没有创建原生控件则进行创建。

[`measure_fps`](http://vispy.org/app.html#vispy.app.Canvas.measure_fps "vispy.app.Canvas.measure_fps")([window, callback])  显示当前每秒钟帧数 FPS。

[`set_current`](http://vispy.org/app.html#vispy.app.Canvas.set_current "vispy.app.Canvas.set_current")([event])  设置当前 Canvas 为活动 GL Canvas。

[`show`](http://vispy.org/app.html#vispy.app.Canvas.show "vispy.app.Canvas.show")([visible, run])  显示或者隐藏 Canvas。

[`swap_buffers`](http://vispy.org/app.html#vispy.app.Canvas.swap_buffers "vispy.app.Canvas.swap_buffers")([event])  交换GL缓冲区，使屏幕外缓冲区可见。

[`update`](http://vispy.org/app.html#vispy.app.Canvas.update "vispy.app.Canvas.update")([event])  通知后端对当前 Canavas 进行重绘。


`app`[](http://vispy.org/app.html#vispy.app.Canvas.app "Permalink to this definition") 当前 Canvas 基于的 VisPy 应用程序实例。


`close`()[](http://vispy.org/app.html#vispy.app.Canvas.close "Permalink to this definition") 关闭当前 Canvas。

#### 特别注意


`close` 这个函数一旦调用了，通常会清除 GL 环境。以 QT 为例，如果当前控件是顶层控件，这就会清除 GL 环境和控件。想要和 QT 的标准行为一致，避免摧毁控件，建议把控件设置成子控件。





`connect`(*fun*)[](http://vispy.org/app.html#vispy.app.Canvas.connect "Permalink to this definition")

把某个函数连接到一个事件上。这里的函数名字应该是 on_X 模式的，X 在这里表示的是事件名字，例如绘制事件就是 `on_draw`。

此方法通常是装饰器，在事件处理程序的函数定义中。



参数:  **fun** : callable 可调用的函数

> 就是要连接的那个函数啦。

`context`[](http://vispy.org/app.html#vispy.app.Canvas.context "Permalink to this definition")

原生控件的 OpenGL 环境。

在 Canvas 对象中通过调用这个属性来使用 OpenGL 函数，以及分享环境的命名空间。

`create_native`()[](http://vispy.org/app.html#vispy.app.Canvas.create_native "Permalink to this definition")

若未创建原生控件则进行创建。如果已经创建了，则该函数不进行任何操作。

`dpi`[](http://vispy.org/app.html#vispy.app.Canvas.dpi "Permalink to this definition")

Canvas 画布中每英寸上的像素数，物理分辨率。


`fps`[](http://vispy.org/app.html#vispy.app.Canvas.fps "Permalink to this definition")

Canvas 画布或者窗口的帧率，每秒钟的帧数，events.draw 执行的频率。


`measure_fps`(*window=1*, *callback='%1.1f FPS'*)[](http://vispy.org/app.html#vispy.app.Canvas.measure_fps "Permalink to this definition")

测试当前 FPS。设置更新的窗口，连接到 draw 绘制事件到 update_fps 函数并设置回调函数。

参数:  **window** : float 浮点数

> 窗口计算 FPS 的时间，单位是秒，默认是1.0。


**callback** : function  函数 或 str 字符串

> 伴随浮点数 FPS 值而要调用的函数，如果是字符串的话，就是 fps 值的格式化字符串。默认的是`'%1.1f FPS'`。如果回调为 False 了，则停止 FPS 检测。

`native`[](http://vispy.org/app.html#vispy.app.Canvas.native "Permalink to this definition")

当前 Canvas 画布所处的原生控件对象。


`physical_size`[](http://vispy.org/app.html#vispy.app.Canvas.physical_size "Permalink to this definition")

当前 Canvas 画布或者 Window 窗口的物理尺寸，各种不同后端提供的 HiDPI 不同所以有不同的尺寸属性。


`pixel_scale`[](http://vispy.org/app.html#vispy.app.Canvas.pixel_scale "Permalink to this definition")

像素比例，逻辑像素（点数）与显示设备上的物理像素的比值。通常都是1.0，不过有的后端可能会比 1 大。当用户自己用 Gloo 来编写自己的可视化方案时，可以设置成一个缩放参数，（复制并乘以所有逻辑像素值），但尽量少这样做，除非你要构建自己的视觉（Visuals）或场景可视化（SceneGraph）; 而应该在SceneGraph画布中应用canvas_fb_transform。


`position`[](http://vispy.org/app.html#vispy.app.Canvas.position "Permalink to this definition")

当前 Canvas 画布或在 Window 窗口相对屏幕的位置。

`set_current`(*event=None*)[](http://vispy.org/app.html#vispy.app.Canvas.set_current "Permalink to this definition")

设置当前 Canvas 为活动 GL Canvas。


参数:  **event** : None

> 不使用。



`show`(*visible=True*, *run=False*)[](http://vispy.org/app.html#vispy.app.Canvas.show "Permalink to this definition")

显示或隐藏 Canvas 画布。


参数:  **visible** : bool 布尔值

> 使 Canvas 画布可见。

**run** : bool 布尔值

> 运行后端事件循环。



`size`[](http://vispy.org/app.html#vispy.app.Canvas.size "Permalink to this definition")

Canvas 画布或 Window 窗口的尺寸。

`swap_buffers`(*event=None*)[](http://vispy.org/app.html#vispy.app.Canvas.swap_buffers "Permalink to this definition")

交换GL缓冲区，使屏幕外缓冲区可见。


参数:  **event** : None

> 不使用。




`title`[](http://vispy.org/app.html#vispy.app.Canvas.title "Permalink to this definition")

> Canvas 画布或 Window 窗口的标题






`update`(*event=None*)[](http://vispy.org/app.html#vispy.app.Canvas.update "Permalink to this definition")

> 通知后端对 Canvas 画布进行重绘。

参数:  **event** : None

> 不使用。



* * *



*class* ### `vispy.app.Timer`(*interval='auto'*, *connect=None*, *iterations=-1*, *start=False*, *app=None*)[](http://vispy.org/app.html#vispy.app.Timer "Permalink to this definition")


计时器 Timer 用来规划未来事件或重复事件。

参数:  **interval** : float 浮点数 或者 'auto'

> 事件之间的时间间隔。默认是 `auto`，就是让程序去查找当前屏幕的刷新率所匹配的时间间隔。目前一般就是 1/60。（译者注：因为通常的显示器刷新率是 60Hz。）


**connect** : function 函数 或者  None

> 调用的函数

**iterations** : int 整形

> 迭代次数。如果设为 -1 则无限进行下去。

**start** : bool 布尔值

> 判断是否启动计时器。

**app** : instance of vispy.app.Application

> vispy.app.Appllicantion 的实例，要附加计时器 Timer 的对象。


#### 方法：


 [`connect`](http://vispy.org/app.html#vispy.app.Timer.connect "vispy.app.Timer.connect")(callback)  self.events.timeout.connect() 的别名
 [`disconnect`](http://vispy.org/app.html#vispy.app.Timer.disconnect "vispy.app.Timer.disconnect")([callback]) self.events.timeout.disconnect() 的别名
 [`start`](http://vispy.org/app.html#vispy.app.Timer.start "vispy.app.Timer.start")([interval, iterations])  启动计时器。
 [`stop`](http://vispy.org/app.html#vispy.app.Timer.stop "vispy.app.Timer.stop")()  停止计时器。



`app`[](http://vispy.org/app.html#vispy.app.Timer.app "Permalink to this definition")

Timer 计时器所处的 VisPy 应用程序实例。


`connect`(*callback*)[](http://vispy.org/app.html#vispy.app.Timer.connect "Permalink to this definition")

self.events.timeout.connect()  的别名。


`disconnect`(*callback=None*)[](http://vispy.org/app.html#vispy.app.Timer.disconnect "Permalink to this definition")

self.events.timeout.disconnect()  的别名。


`native`[](http://vispy.org/app.html#vispy.app.Timer.native "Permalink to this definition")

Timer 所基于的原生计时器。

`start`(*interval=None*, *iterations=None*)[](http://vispy.org/app.html#vispy.app.Timer.start "Permalink to this definition")

启动计时器。每间隔指定的*秒数 interval*，计时器事件就会被生成。如果*间隔的秒数 interval*设为 None，就会使用 self.interval 来替代 *interval*。

如果指定了 *迭代次数 iterations*，那么计时器 Timer 在完成了这些次数后就会停止。如果没有指定这个次数，就会使用 self.iterations 里面存储的上一次的值。如果给 *iterations* 设一个负值，计时器就会一直运行下去，知道 stop() 函数被调用了才停止。

如果这个函数调用的时候计时器早已经在运行了，就不会有任何效果。（计时器还会跟之前一样继续运行，对迭代的间隔和次数都不影响，也不会开始一个新的计时器启动事件。）




`stop`()[](http://vispy.org/app.html#vispy.app.Timer.stop "Permalink to this definition")


停止计时器。

