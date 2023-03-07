---
title: OI杂记
date: 2023-03-05 23:35:23
index_img: https://pic.imgdb.cn/item/634c167216f2c2beb1bb7b00.jpg
tags:
- 杂项
categories: 
- OI
---

## for循环跳出

1.`continue`跳入for的下一次循环

2.`break`跳出整个for循环

## 条件运算符

对于有些选择分支结构,可以使用简单的条件运算符来代替. 如:

```c++
if(a<b)
	min=a;
else
	min=b;
```

可以用下面的条件运算符来处理

```c++
min=(a<b)?a:b;
```


其中**"(a<b)?a:b"**是一个**"条件表达式"**,它是这样执行的:　如果a<b为真,则表达式取a值,否则取b值.
