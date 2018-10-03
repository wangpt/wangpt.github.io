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
*Editor->Create NSManagedObject  Subclass..，然后全选，下一步，即可完成*

![](/img/in-post/post-coredata/coredata_3.png)

4.编译出错解决方案
*使用xcode8以上工具编译代码会出现报错，你可以根据不同的entity去分别选择启用还是关闭自动生成机制；选择model file中特定的entity，打开其Data Model Inspector窗口，将其中的Codegen选项设置为Manual／None*

[Xocde8编译错误解决方案](https://www.jianshu.com/p/a344394b38cc)
[Xocde8编译错误解决方案](https://www.jianshu.com/p/7899ddaff26b)

![](/img/in-post/post-coredata/coredata_4.png)

### 新增实体

```objc
+ (void)savePersonId:(NSString *)id name:(NSString *)name sex:(NSString *)sex{
    PersonEntity *person = [self readPersonId:id];
    if(!person){
        person = [PersonEntity MR_createEntity];
    }
    PersonInfoEntity *personInfo = [PersonInfoEntity MR_createEntity];
    person.infoEntity = personInfo;
    person.name = name;
    person.id = id;
    person.infoEntity.infoSex = sex;
    [[NSManagedObjectContext MR_defaultContext] MR_saveToPersistentStoreAndWait];
}
```

### 删除实体

```objc
+ (void)removeAllObjects{
    [PersonEntity MR_truncateAll];
}

+ (void)removePerson:(NSString *)id{
    NSArray *personArr = [PersonEntity MR_findByAttribute:@"id" withValue:id];
    for (PersonEntity *person in personArr) {
        [person MR_deleteEntity];
    }
    [[NSManagedObjectContext MR_defaultContext] MR_saveToPersistentStoreAndWait];
}
```
### 修改实体

```objc
+ (void)updataPersonId:(NSString *)id name:(NSString *)name sex:(NSString *)sex{
    PersonEntity *updatePerson = [self readPersonId:id];
    PersonInfoEntity *personInfo = [PersonInfoEntity MR_createEntityInContext:[NSManagedObjectContext MR_defaultContext]];
    updatePerson.infoEntity = personInfo;
    updatePerson.name =name;
    personInfo.infoSex = sex;
    [[NSManagedObjectContext MR_defaultContext] MR_saveToPersistentStoreAndWait];
}
```

### 查找实体

```objc
+ (NSArray *)readAllData{
    return [PersonEntity MR_findAll];
}

+ (NSArray *)readAllDataByAscending:(BOOL)ascending{
    NSArray *persons = [PersonEntity MR_findAllSortedBy:@"id" ascending:ascending];
    return persons;
}

+ (PersonEntity *)readPersonId:(NSString *)id{
    PersonEntity* person = [PersonEntity MR_findFirstByAttribute:@"id" withValue:id];
    return person;
}

+ (PersonEntity *)readFirstPerson{
    return [PersonEntity MR_findFirst];
}
```

###  

## 代码下载

[TJCache](https://github.com/wangpt/TJCache)
