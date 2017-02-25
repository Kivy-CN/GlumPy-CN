Title: VisPy Installation
Date: 2017-02-25
Category: VisPy
Tags: Python,VisPy,Data,Visualization


# VisPy 中文文档：简介与安装

VisPy 是一个高性能交互式 2D/3D 数据可视化库，通过 OpenGL 库来对目前的图形处理单元（GPU）的计算性能进行充分利用，用于超大规模数据集的显示。

# 译者前言

[Kivy 中文编程指南文档](https://github.com/cycleuser/Kivy-CN)快翻译完了，现在又开了一个新坑，就是这个 [VisPy](https://github.com/cycleuser/VisPy-CN)，这主要是因为我当前在开发的 [GeoPython](https://github.com/cycleuser/GeoPython) 项目中存在着超大规模数据呈现的需求，所以我决定用显卡绘图来试一试。我此前从来没有任何 OpenGL 相关的经验，也完全是从零起步，一边学习，一边翻译，所以难免导致翻译质量的波动，而且大部分时刻可能是翻译得挺差的。然而我是一个希望把事情做了就尽量做好的人，所以大家发现任何错误，请一定不吝赐教，让我有改正和提高的机会。


# 简单介绍

[英文原文](http://vispy.org/documentation.html#getting-started)

VisPy 的开发正在紧锣密鼓地展开，目前还没有完成一个完整的用户文档。VisPy 针对了以下两种用户作为目标群体：

* 懂得 OpenGL 的用户，或者是愿意去学习 OpenGL 的用户，这些人往往希望通过 Python 来实现尽可能简单的又好看又快速的交互式 2D/3D 可视化。这类用户可以通过 vispy.gloo 来创造自己的可视化方式（当然这需要有一定的 OpenGL或者GLSL的知识背景）。

* 一点也不了解 OpenGL 的科学家（译者表示自己就是>~<），寻求一些高层次、高性能的数据投图工具。使用 vispy.plot 和 vispy.scene 就可以进行高层次的工作了（注意：都是实验性质或者还在开发中的功能）。

可以看看[图像展示](http://vispy.org/gallery.html)，尝试来点灵感什么的。

# 安装指南

[原文地址](http://vispy.org/installation.html)

### 依赖包

VisPy 最标准的唯一依赖包，就是 [numpy](http://numpy.org/)。



## 后端需求


VisPy 要求至少要有一个工具能打开窗口并创建一个 OpenGL 环境。可以用 Qt, GLFW,SDL2, Wx, Pyglet。对于某些可视化，还可以在IPython notebook (version 3 或者之后的版本) 中来使用 WebGL。


#### 特别警告

只要有一个后端工具就可以了，不是要全部安装。


## 硬件需求


VisPy 会高强度地使用你机器上的显卡。更确切地说，VisPy 是通过着色器（shader）来利用图形处理单元（GPU）。所以 VisPy 就需要一个尽量比较新的显卡（最低也得是十二年内的），还需要一个更新到最近版本的显卡驱动，这样 VisPy 才能有权限使用可编程管线（而不能是固定管线）。


怎么查看系统信息呢？（在 Python 中）可以用下面的命令：

```Python
import vispy #这里一定要加上这句，否则必然报错，至于为什么，请参考 Python 基础知识

print(vispy.sys_info())
```
	（译者注：作者原文这里都没说要在 Python 中，也没有给出导入 vispy 的那句话，所以充分说明作者的文档原文是给有相当熟练的 Python 基础的人来阅读使用的，我这里为了新手来进行翻译，所以尽量都给标注上。感觉原文作者的逻辑有问题，还没给说明白怎么安装，查看系统信息就来了一个必须要安装好 VisPy 才能用的方式，太扯了吧？）

上面的命令输出的结果就是一大串子的信息了，都是和你的系统以及显卡驱动有关的。一定注意，OpenGL 的版本不能低于 2.1。



## 安装选项

要想安装**最新发行的稳定版的 VisPy **，就用如下命令就可以了：

```Bash
pip install --upgrade vispy
```






想要运行**最新开发版本**，只需要在你本地的机器上同步一下代码，然后在安装的时候标注一下`develop`就可以使用到最新的`master`版本的程序代码了：


```Bash
git clone git://github.com/vispy/vispy.git  # 这是同步代码到一个名为"vispy"的文件夹
cd vispy
python setup.py develop
```

当然不用同步代码的方式也可以，还是可以用 pip 来安装的：

```Bash
pip install -e git+https://github.com/vispy/vispy#egg=vispy-dev
```

### 测试安装

强烈推荐在安装之后马上运行一下测试工具，来检查一下安装是否成功。测试方法如下：

```Python
import vispy
vispy.test()
```
	（译者注：一定要注意，这个 vispy.test 必须在用 git 同步下来的 vispy 文件夹内进行才可以，否则一定会报错的！官方文档真是太粗糙了。。。）