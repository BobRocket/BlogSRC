---
title: EasyX入门篇
date: 2021-12-19 09:14:01
index_img: https://pic1.imgdb.cn/item/634c167216f2c2beb1bb7b00.jpg
tags:
- EasyX
- C++
- 花里胡哨
categories: 
- 语言编程
---

# EasyX入门篇

EasyX
在学习C语言时，很多同学抱怨说C只能写最简单的Demo程序，通过printf在屏幕上打印字符来验证代码。这样的编程很枯燥，一点没觉得自己在设计软件。

EasyX是针对C++的第三方图形库，通过它我们能够在屏幕上绘制出自己喜欢的各种颜色的图形。有了它，自己编写好玩的小游戏不是梦哦。

使用EasyX有下面几点要求：

只能在Windows下使用
建议使用Visual Studio作为IDE
必须写C++代码（文件后缀名为cpp）

## EasyX安装

#### 下载路径

[download](https://easyx.cn/downloads/)

#### 安装

解压下载目录 EasyX_20151015(beta).zip 如下：

双击 setup.hta 文件

找到需要的VS版本点击安装即可。

PS：在解压缩的文件中，有个EasyX_help.chm文件，它是EasyX的文档，所有API的介绍都在里面。

作为一个软件开发人员，阅读文档是最基本的技能，希望大家从现在开始培养自己这方面的能力。如果你通读了这个文档之后，相信你完全能够自己完成在屏幕上画出自己想要的图案。

## EasyX基本API

在EasyX的文档中，有一节是“超简单的使用预览”，里面有这样一段代码。

```c++
#include <iostream>
#include <graphics.h>
#include <conio.h>

void main()
{
    initgraph(640, 480);   // 创建图形界面
    circle(200, 200, 100); // 画圆，圆心(200, 200)，半径 100
    getch();               // 按任意键继续
    closegraph();          // 关闭图形界面
}
```

这段代码的执行结果如下：

![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly91cGxvYWQtaW1hZ2VzLmppYW5zaHUuaW8vdXBsb2FkX2ltYWdlcy8xNDU5MDItZGZmZDJjZjQ2Mzc3MjU3Ny5wbmc?x-oss-process=image/format,png)

语法

1. #### 画布的创建和销毁

  main函数中，第一行和最后一行代码是创建和删除图形界面，这个图形界面常常被叫做“画布”。

initgraph()
创建画布时，需要输入目标窗口的长宽值。

closegraph()
和C语言中一样，C++也强调代码的对称性，申请资源和释放资源的代码总是成对出现的。

2. #### 坐标系

  在 EasyX 中，坐标分为：逻辑坐标和物理坐标。

我们这里只介绍逻辑坐标。

逻辑坐标是在程序中用于绘图的坐标体系。

坐标默认的原点在屏幕的左上角，X 轴向右为正，Y 轴向下为正，度量单位是象素。

坐标的原点，方向和单位都可以通过特定函数修改。我们一般只采用默认设置。

3. #### 圆形绘制

  #### circle这个函数用于画圆。

```c++
void circle(
int x,
int y,
int radius
);
```

参数：
x
圆的圆心 x 坐标。
y
圆的圆心 y 坐标。
radius
圆的半径。
Demo程序中就是用这个函数绘制了一个圆心为（200, 200），半径为100的圆形。

4. #### 直线绘制

  这个函数用于画线。还可以用 linerel 和 lineto 画线。

```c++
void line(
int x1,
int y1,
int x2,
int y2
);
```

参数
x1
线的起始点的 x 坐标。

y1
线的起始点的 y 坐标。

x2
线的终止点的 x 坐标。

y2
线的终止点的 y 坐标。

5. #### 矩形绘制

  这个函数用于画空心矩形。

```c++
void rectangle(
int left,
int top,
int right,
int bottom
);
```

参数
left
矩形左部 x 坐标。

top
矩形上部 y 坐标。

right
矩形右部 x 坐标。

bottom
矩形下部 y 坐标。

6. #### 椭圆绘制

  这个函数用于画椭圆。

```c++
void ellipse(
int left,
int top,
int right,
int bottom
);
```

参数
left
椭圆外切矩形的左上角 x 坐标。

top
椭圆外切矩形的左上角 y 坐标。

righ椭圆外切矩形的右下角 x 坐标。

bottom
椭圆外切矩形的右下角 y 坐标。

上面是几个基本图形的绘制方法，它们有个特点是画出的都是空心的图形。与之对应的是一组绘制带有填充颜色图形的接口。

fillcircle(), fillellipse(), fillrectangle()
它们的参数和画空心的接口完全一样，只不过使用前需要调用下面这个接口设置填充颜色。

setfillcolor()
下面我们来看看这些函数究竟能做什么。

## EasyX实战

![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly91cGxvYWQtaW1hZ2VzLmppYW5zaHUuaW8vdXBsb2FkX2ltYWdlcy8xNDU5MDItZjk4NDE4NmJkNWViZDgxYi5wbmc?x-oss-process=image/format,png)

上面这幅图就是用EasyX实现的。哈哈，貌似有点丑， 不过假如你能独立写出这个功能，说明你已经基本掌握了EasyX的用法。

提供一个代码框架：

```c++
#include <iostream>
#include <graphics.h>

void main()
{
    initgraph(800, 600);

    // Add your code

    closegraph(); 
}
```

这里请先自己思考一下，不要急往下看。

（… 15分钟过去了 …）
分析
这幅图主要是由圆形、椭圆形、矩形和直线组成的，这几个形状的API我们都已经介绍过了。我们只要按顺序把它们画在屏幕上就好了。

代码实现
在C++工程的main.cpp文件中输入下面代码。

```c++
#include <iostream>
#include <graphics.h>
#include <conio.h>

void main()
{
    initgraph(800, 600);

    // 记录当前填充颜色
    COLORREF save_color = getfillcolor();

    // 绘制矩形框
    rectangle(50, 50, 550, 550);

    // 画空心圆
    circle(200, 150, 50);
    circle(400, 150, 50);

    // 画空心椭圆    
    ellipse(100, 100, 500, 300);

    // 填充椭圆内的绿色部分
    setfillcolor(GREEN);
    floodfill(300, 200, getlinecolor());

    // 填充一个白色的椭圆
    setfillcolor(WHITE);
    fillellipse(200, 210, 400, 290);

    // 填充一个绿色的矩形
    setfillcolor(GREEN);
    fillrectangle(150, 300, 450, 500);

    // 画一条直线
    line(300, 500, 300, 550);

    // 按任意键继续
    getch();

    // 恢复填充颜色
    setfillcolor(save_color);

    closegraph(); 
}
```

好了，按一下Ctrl + F5，是不是看到效果了？

对大多数人来说，椭圆内部的不规则的绿色面积应该是最难实现的，floodfill()这个函数就是帮助我们将一个点所在的封闭范围内全部用填充颜色涂掉。除了设置点坐标之外还要输入这个封闭区域边框的颜色。

这里需要强调的是，在初始化画布之后，我们获取了当前的填充颜色，在绘制完成后又把当前填充颜色恢复到了我们程序执行之前的状态。

这个习惯非常重要，就是要让我们的程序在运行过之后，系统环境没有任何变化。否则在未来负责的工程中，很可能因为某个模块乱改系统设置产生很多不必要的bug。

好了，现在是不是比较有成就感呢？

由于EasyX的使用会贯穿于我们这个系列的项目中，因此这里就不过多介绍了，后面用到了新内容我们再讲。
