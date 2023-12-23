---
title: 字符串转Unicode
description: 使用python将字符串转为Unicode
tag: 工具
categories: 工具
top: false
---

# 字符串转Unicode（python）

## 为什么要做这个

事情的起因很简单，我买了一张专辑，叫做“繋(jì)宙歌”，然后这个“繋”字我在微软输入法里面怎么都找不到，最后我就想着能不能用Unicode的方式把它打出来

## 在知道Unicode码的情况下怎么打出这个字

非常简单，只需要输入“VUC”然后紧接着直接输入对应的Unicode码即可（十六进制）

## 代码部分

### 字符串转Unicode

首先介绍一个基本的函数：`ord()`：返回一个字符的ASCII码数值

举个例子

```python
word = '东'
result = ord(word)
print(result)
```

这样它就会输出“东”这个字的ASCII编码值，是19996

但是前面说了，VUC只能用十六进制，所以我们还要转为16进制

这里再介绍一个基本的函数：`hex()`

它的作用就很简单了，就是将整数转换为十六进制字符串

所以完整的代码为：

```python
word = '东'
result = hex(ord(word))
print(result)
```

这样就会输出对应的十六进制的Unicode码，为0x4e1c

### Unicode转字符串

首先要了解一个基本的函数：`chr()`：将整数转换为对应的ASCII字符

举个例子

```python
unicode = 19996
word = chr(unicode)
print(word)
```

这样他就会输出“东”

但是如果你只知道这个字的十六进制的Unicode编码的话，这个方法就不太行了

所以我们可以使用这个函数：`eval()`：执行一个字符串表达式，并返回表达式的值

它可以执行字符串里面的代码，如:

`eval("print('1')")`输出的就是1

或者单纯的把参数中最外层引号去掉

这里我们要的是十六进制的数字，所以直接使用`int()`是不行的

我们要稍微做一个修改

`int(x, 16)`

x就是你的数字，16就是对应的进制，比如：`int('4e1c', 16)`

所以完整的代码就是：

```python
unicode = int('4e1c', 16)
Unicode = hex(Unicode)
Unicode = eval(Unicode)
word = chr(Unicode)
print(word)
```

这样，它就会输出东这个字了

那么问题来了，明明我已经存储了对应的十六进制码了，为什么我还要转换这么多次呢？

1.虽然我们存储的是十六进制的数据，但是他还是属于int类型，而eval传入只能是str类型

2.如果使用str类型，就会报错invalid decimal literal，在这里是因为python默认识别的是10进制，然而十进制中并没有字母，如果恰好你的Unicode中没有字母，那么它的值也发生的变化

3.用`hex()`可以完美的避开上面的问题

### 现成能用的下载链接

[GitHub](https://github.com/myncdw/str2unicode/releases)
