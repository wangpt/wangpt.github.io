---
layout:     post
title:      "Swift学习笔记"
subtitle:   " \"Exmple for Swift\""
date:       2018-09-22 12:00:00
author:     "Wangpt"
header-img: "img/post-bg-2015.jpg"
catalog: true
tags:
    - Notes
    - Swift

---

> “欢迎关注和分享 ”


## 简介
*Swift，苹果于2014年WWDC（苹果开发者大会）发布的新开发语言，可与Objective-C 共同运行于Mac OS和iOS平台，用于搭建基于苹果平台的应用程序*

---


### 知识储备

* [swift教程](https://swift.org)
* [the-swift-programming-language-in-chinese](https://github.com/numbbbbb/the-swift-programming-language-in-chinese)
* [其他参考](http://www.runoob.com/swift/swift-basic-syntax.html)


### 概览

###### 简单值
*使用 let来声明一个常量，用 var来声明一个变量*

```
var myVariable = 10
myVariable = 20
let myConstant = 10
```
*常量和变量必须拥有赋予的值相同的类型。如果初始值不能提供足够的信息，则需要用冒号分隔*

```
let myConstantInteger = 10
let myConstantFloat = 10.0
let myConstantDouble:Double = 10.0
```
*值不能隐形的转化为其他类型，如果需要将一个类型装好，则需要对应类型显性的声明* 

```
let text = "the width is "
let width = 20
let textWidth = text + String(width)
```

*也可以将值加入字符串：将值写在圆括号，前面再添加反斜杠*

```
let width = 20
let space = 10
let textWidth = "the width is \(width + space)"
```

*为字符串使用三个双引号（"""）来输入多行内容*

```
let width = 3
let height = 5
let quotation = """
view width is \(width)"
And height is \(height)"
"""
```

*使用方括号创建数组或字典，并使用放火好按序号或者键访问对应元素*

```
var colorList =  ["yellow", "red", "white", "blue"]
colorList[1] = "gray"

var personInfo = ["name":"小明",
                  "age":"18"]
personInfo["name"] = "小红"
personInfo["sex"] = "1"
```

*初始化空数组或者字典,也可以用[]来表示空数组，用[:]来表示空字典*

```
var emptyArray = [String]()
var emptyDictionary = [String: Float]()
emptyArray = []
emptyDictionary = [:]
```


## 后记

此文档会不断更新
