Title: GlumPy-Installation
Date: 2017-03-10
Category: Work
Tags: Python,GlumPy,Data,Visualization


# GlumPy 中文文档翻译：安装指南

## 译者前言

我弃坑了 VisPy，因为在不同操作系统上面运行的效果差距比较大，可能是因为不同操作系统的相关组件和依赖包的版本差别，或者是其他的原因吧。而且好像 GlumPy 就是对 VisPy 的继承， VisPy 的代码提交已经是几个月之前甚至几年前，GlumPy 目前还在活跃。从文档来看这二者也很相似，尤其是这部分安装指南几乎就是修改了一下的 VisPy 安装指南。

GlumPy 给我的印象很棒，因为官方开发人员很及时地跟我互动讨论[一些运行错误产生的原因](https://github.com/glumpy/glumpy/issues/87)，虽然他们的 example 里面的一些一两年的 bug 也没有修改，比如 earth.py 似乎需要把 Arcball 替换成 Trackball，而且对 numpy 的特定版本的需求也需要提示一些，参考[这里查看更多内容](https://github.com/glumpy/glumpy/issues/106)。

## 安装方法

最简单直接的安装方法就是用 pip 了：

```Bash
pip install glumpy
```

还可以对已经安装的版本进行升级：

```Bash
pip install --upgrade glumpy
```

## 依赖包

GlumPy 常规需要的标准依赖包就是下面这几个：


> * numpy: [http://numpy.org](http://numpy.org/)
> * pyopengl: [http://pyopengl.sourceforge.net](http://pyopengl.sourceforge.net/)
> * cython: [http://cython.org](http://cython.org/)
> * triangle: [http://dzhelil.info/triangle/](http://dzhelil.info/triangle/)


安装这些依赖包最简单的方法莫过于用 pip 了：

```Bash
pip install numpy
pip install cython
pip install pyopengl
pip install triangle
```
（译者注：推荐你先安装 cython ，然后是 numpy 接着是 pyopengl 和 triangle。在安装 triangle 的时候可能遇到报错，比如缺少 packaging ，解决方案是用 `pip install packaging` 这样的命令来把缺少的包安装上就行。）



如果已经安装过上面这些包，可以用下面的命令来升级到最新版本：


```Bash
pip install --upgrade numpy
pip install --upgrade pyopengl
pip install --upgrade cython
pip install --upgrade triangle
```




## 后端需求

GlumPy 需要至少一个工具链来打开窗口创建 OpenGL 环境。这可以用很多标准的 C/C++ 工具链来实现，比如 Qt, GLFW, glut, pygame, SDL2, Wx, GTK2 or GTK3，所以就需要对应的 Python 绑定，或者类似 pyglet 这样的纯 Python 工具链。

#### 特别警告

上面这些后端的包只需要有一个就可以了，不是都要安装！




| **目前常用的后端** | Qt | GLFW | Pyglet | SDL2 | GTK3 | Wx3 |
| ------------- |:-------------:|:-------------:|:-------------:|:-------------:|:-------------:| -----:|
| 多窗口| ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| 无修饰窗口 | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| 窗口尺寸调整 | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| 窗口移动 | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
|设定 GL API | ✓ | ✓ | — | ✓ | ✓ | ✓ |
| 设定 GL Profile | ✓ | ✓ | — | ✓ | ✓ | ✓ |
| 分享 GL Context | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| 全屏 | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| 处理使用 Unicode | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |






| **老古董后端** | Wx2 | Glut | Freeglut | Pygame | GTK 2.x |
| ------------- |:-------------:|:-------------:|:-------------:|:-------------:| -----:|
| 多窗口 | ✓ | — | — | — | ✓ |
| 无修饰窗口 | ✓ | ✓ | ✓ | ✓ | ✓ |
| 窗口尺寸调整 | ✓ | ✓ | ✓ | — | ✓ |
| 窗口移动| ✓ | ✓ | ✓ | — | ✓ |
| 设定 GL API | — | — | — | — | — |
| 设定 GL Profile | — | — | — | — | — |
| 分享 GL Context | — | — | — | — | ✓ |
| 全屏 | ✓ | ✓ | ✓ | ✓ | ✓ |
| 处理使用 Unicode| ✓ | — | — | ✓ | ✓ |
| 滚轮事件 | ✓ | — | ✓ | — | ✓ |




## 硬件需求


GlumPy 会对显卡造成很大符合。更确切地说， GlumPy 会通过着色器（shader）来高强度使用图形处理单元（GPU）。所以 GlumPy 需要起码稍微新一点的显卡（只要是最近十二年以来的估计都可以）还需要一个最新版本的显卡驱动，这样 GlumPy 才能使用可编程管线（而不是固定化的管线）。


在 Linux 或者 OSX 平台，输入下面这个命令：

```Bash
glxinfo
```

上面这个命令执行之后会显示出一大堆结果，就是和你显卡相关的信息了。这时候最重要的是要看看你能否有权限直接使用显卡（direct ），以及你的显卡支持的 GL 版本以及 着色器语言（ shading language ） 的版本。


```Bash
...
direct rendering: Yes
...
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: NVIDIA GeForce GT 650M OpenGL Engine
OpenGL version string: 2.1 NVIDIA-8.24.9 310.40.25f01
OpenGL shading language version string: 1.20
...
```


译者注：上面这样子现实的内容太繁杂了，完全可以用 `glxinfo |grep direct && glxinfo |grep OpenGL` 这样一个命令，在我的机器上输出如下所示：
```Bash
direct rendering: Yes
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: NVIDIA GeForce GTX TITAN OpenGL Engine
OpenGL version string: 2.1 NVIDIA-10.15.20 367.15.10.35f01
OpenGL shading language  version string: 1.20
```

OpenGL 版本最低是 2.1，着色器语言的版本至少要 1.1。如果不符合的话，你需要安装最新版本的对应软件。可以看看你的操作系统是否提供了文档，或者在线搜索一下怎么来操作吧。


## 在 Windows 7，8，10  x64 bit 操作系统中安装的步骤

#### 首先是安装 Python3：

> * 从[ Python 官方网站下载页面](https://www.python.org/downloads/)来下载 Python。（译者更推荐从[清华开源镜像](https://mirrors.tuna.tsinghua.edu.cn/anaconda/archive/)下载使用 anaconda3 ，这样一来是下载速度快一些，而来也方便使用 conda 安装管理一些包。另外 GlumPy 官方推荐 Python3， 我很钦佩，因为我特别讨厌 2，没什么合理的具体理由，可能因为个人比较 2 吧。）
> * 运行安装文件，安装到一个短一点的路径里面，比如`C:\python3`。
> * 把 Python 可执行文件所在的目录添加到系统的环境变量 PATH 中（通常在安装过程中这一步就会完成了，一般不用人手动操作）。
> * **重启操作系统，之后安装好的 Python 就可以用了。**
> 重启了之后，在命令行里面输入 `python` 然后回车，试试能不能运行。如果能得到一个`>>>`这样的 Python 命令行控制台解释器的提示符，就没有问题了。如果没出现这个，而是报错了，那有 99% 的可能都需要你在系统的环境变量中添加 Python 所在路径。

#### 然后是安装依赖包（一定要从管理员权限的 cmd 控制台或者 powershell）：

```Bash
C:\Windows\system32> pip install numpy
C:\Windows\system32> pip install cython
C:\Windows\system32> pip install pyopengl
C:\Windows\system32> pip install triangle
```

#### 接下来安装 GlumPy（一定要从管理员权限的 cmd 控制台或者 powershell）：

```Bash
C:\Windows\system32> pip install glumpy
```

#### 关键部分了，安装 FreeType：

> * 从 [这个链接](https://github.com/ubawurinna/freetype-windows-binaries) 下载一份编译好的 FreeType 文件。
> * 把 Zip 文件解压缩出来。
> * 把 freetype 字样的 dll 从 win64 这个目录里面复制到你的 Python3 安装目录。
> * 把其中的一个 `freetype**.dll` 文件重命名成为 `freetype.dll`。
> 下载的压缩包中附带的一个 README 文件会详细解释区别，推荐用带有 MT 字样的那个 DLL 文件。

（译者注：一定注意重命名这一步，文档一定要仔细读。遇到过某些学生不好好读文档，弄半天都出现找不到 freetype 的错误，然后抓狂问我怎么办。所以一定仔细阅读，而且一定注意细节，比如别把名字错误改成 fretype 等等。）

#### 另一个关键，安装 GLFW：


> * 首先是去下载了，链接地址在 [这里](http://www.glfw.org/download.html)。
> * 还是把 Zip 文件解压缩处理。
> * 从带有 `lib-xxxxx` 字样的文件夹中复制出来一份 glfw.dll 等等文件到你的 Python3 安装目录。
> 推荐使用 `lib-mingw-w64` 这一个，另外这里不用重新命名，所以别修改文件名哦。



