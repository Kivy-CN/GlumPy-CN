Title: VisPy Basic
Date: 2017-03-4
Category: VisPy
Tags: Python,VisPy,Data,Visualization


# VisPy 中文文档：基础内容

VisPy 是一个**高性能交互式 2D/3D 数据可视化库**，通过 **OpenGL** 库来对目前的**图形处理单元（GPU**）的计算性能进行充分利用，用于超大规模数据集的显示。


更多信息可以参考 [http://vispy.org](http://vispy.org/index.html).



###`vispy.``use`(*app=None*, *gl=None*)[](http://vispy.org/vispy.html#vispy.use "Permalink to this definition")

设置 VisPy 的使用选项，指定使用的应用后端和 GL 后端。


 参数:  **app** : str 字符串类型

> 选择应用程序使用的后端（不区分大小写）标准后端包括：
> * 'PyQt4': 使用 Qt 控件工具链，通过 PyQt4。
> * 'PyQt5': 使用 Qt 控件工具链，通过 PyQt5。
> * 'PySide': 使用 Qt 控件工具链，通过 PySide。
> * 'PyGlet': 使用 Pyglet 后端。
> * 'Glfw': 使用 Glfw 后端（继承了 Glut）。在 Linux 系统上比较广泛。
> * 'SDL2': 使用 SDL v2 后端。
> 附加的后端：
> * 'ipynb_vnc': 在 IPython notebook 中进行渲染，通过 VNC 连接（实验阶段不稳定）

**gl** : str 字符串类型


> 选择应用程序使用的 GL 后端（不区分大小写），有如下选项：
> * 'gl2':  使用 Vispy 的桌面 OpenGL API。
> * 'pyopengl2': 使用 PyOpenGL 的桌面 OpenGL API，总体都是测试状态
> * 'es2': （计划中尚未实现）在 Windows 上通过 Angle来使用真正的 OpenGL ES 2.0 。ES 2.0 的可用性主要在 Windows 上，因为要基于 DirectX。
> * 'gl+': 使用你操作系统上的完整的 OpenGL 函数（通过 PyOpenGL）。




更多信息参考：

[`vispy.app.use_app`](http://vispy.org/app.html#vispy.app.use_app "vispy.app.use_app"), `vispy.gloo.gl.use_gl`



#### 特别注意

如果设置了 app 选项，那么就调用了 vispy.app.use_app() 。如果设置了 gl 选项，那么就调用了 vispy.gloo.use_gl() 。

如果设置了某个应用程序后端的名字，而这个后端又不能加载，就会抛出一个错误了。

如果没有给出后端名字， VisPy 辉县检查一下对应的 GUI 工具链，检查一下每个已经导入的后端，然后尝试使用第一个。如果不成功， VisPy 会尝试使用配置文件中的`默认后端`。如果还是不成功，VisPy 就会一个接一个按照预设的顺序来尝试每一个后端。



###`vispy.``sys_info`(*fname=None*, *overwrite=False*)[](http://vispy.org/vispy.html#vispy.sys_info "Permalink to this definition")


获取相关的系统信息和调试信息

参数：**fname** : str 字符串类型| None

> 输出信息的文件名，用 None 来简化输出。


**overwrite** : bool 布尔值


> 如果为 True，则覆盖文件（如果文件已经存在的话）


返回值：**out** : str 字符串类型


>  以一个字符串的方式返回系统信息。


###`vispy.``set_log_level`(*verbose*, *match=None*, *return_old=False*)[](http://vispy.org/vispy.html#vispy.set_log_level "Permalink to this definition")

设定日志级别的一个函数，便于开发中的调试。

参数：
**verbose** : bool 布尔值, str 字符串, int 整形, 或者 None

> 这个是控制输出信息的冗余复杂程度。如果是用字符串，可以是 DEBUG，INFO，WARNING，ERROR 或者 CRITICAL。要注意这些只是为了方便，传入日志的时候，DEBUG等等都是同等对待的。如果用布尔值， True 的效果就跟用字符串 `INFO` 一样，而 False 就相当于字符串 `WARNING`。

**match** : str 字符串或者 None

> 这里是提供要去匹配的字符串。只有包含了通过正则表达式对比后匹配该`match`字符串的子串才会被显示出（当然还要符合刚刚设置的 verbose level）。

**return_old** : bool 布尔值

> 如果为 True， 则返回旧的冗余度和旧的匹配字符串。



更多信息参考：

`vispy.util.use_log_level`



#### 特别注意

如果 verbose=='debug'，那么 VisPy 方法发送日志消息时会返回每一个日志消息，这对于调试很有用处。如果 verbose=='debug' 或者 match 匹配字符串设置为 None，这就可能会增加一些额外的性能开销。所以除非性能问题不太重要，其他情况下不建议使用这些选项。

###`vispy.``test`(*label='full'*, *extra_arg_string=''*, *coverage=False*)[](http://vispy.org/vispy.html#vispy.test "Permalink to this definition")


测试 VisPy 的工具


参数：
**label** : str 字符串类型

> 可以是`full`， `unit`，`nobackend`，`extra`， `lineendings`， `flake`， `docs`这些字符串其中的一个，也可以是后端名，比如 `qt`等等。


**extra_arg_string** : str 字符串类型

> 传递给 `pytest` 的额外的参数。

**coverage** : bool 布尔值

> 如果为 True，则收集覆盖率数据。（译者注：这个我没弄明白，等以后试试。）