---
layout:     post
title:      "iOS数据库之CoreData"
subtitle:   " \"Exmple for MagicalRecord\""
date:       2018-09-18 12:00:00
author:     "Wangpt"
header-img: "img/post-bg-2015.jpg"
catalog: true
tags:
    - iOS
    - coredata

---

> “CoreData的使用说明 ”


简介

*使用CoreData进行数据的增删改查功能*

---

## MagicalRecord的使用

### 安装

使用Carthage


1.将以下行添加到您的Cartfile：

 ```
github "MagicalPanda/MagicalRecord"
 
 ```

2.carthage update在项目目录中运行

3.将适合MagicalRecord.framework您的平台（位于“Carthage / Build /``”）拖到应用程序的Xcode项目中，并将其添加到相应的目标中

使用CocoaPods

1.将以下行添加到您的Podfile

 ```
pod "MagicalRecord"
 ```
 
2.在项目目录中，运行 pod update
 
 
### 创建模型

1.创建data model
*首先创建一个数据Model，->file->new->CoreData ->选择data model，取名TJPersonModel*

![](/img/in-post/post-coredata/coredata_1.png)

2.创建模型model
*分别创建两个实体，PersonEntity和PersonInfoEntity*

![](/img/in-post/post-coredata/coredata_2.png)


3.进行建模
*Editor->Create NSManagedObject  Subclass..，然后全选，下一步到完成即可，生成对应4个文件，即可完成*

![](/img/in-post/post-coredata/coredata_3.png)



### 删除实体


### 获取实体

###  

## 代码下载

[TJCache](https://github.com/wangpt/TJCache)
