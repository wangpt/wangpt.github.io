---
layout:     post
title:      "IOS缓存管理之PINCache"
subtitle:   " \"Exmple for PINCache\""
date:       2018-09-07 12:00:00
author:     "Wangpt"
header-img: "img/post-bg-2015.jpg"
catalog: true
tags:
    - iOS
    - OC
    - Cache

---

> “欢迎关注和分享 ”


## 简介
*高性能 iOS 缓存框架*

---

## 开发环境
iOS 6.0+

## 使用
*通过YYCache缓存自定义对象*

## 1.遵守NSCoding协议


``` objc

@interface PersonInfoModel : NSObject<NSCoding>
@property (nonatomic, copy) NSString *name;
@property (nonatomic, copy) NSString *sex;
@property (nonatomic, assign) NSInteger age;
@end


```
---

## 2.对象序列化

``` objc

- (instancetype)initWithCoder:(NSCoder *)aDecoder{
    self.name = [aDecoder decodeObjectForKey:@"name"];
    self.sex = [aDecoder decodeObjectForKey:@"sex"];
    self.age = [aDecoder decodeIntegerForKey:@"age"];
    return self;
}

- (void)encodeWithCoder:(NSCoder *)aCoder{
    [aCoder encodeObject:self.name forKey:@"name"];
    [aCoder encodeObject:self.sex forKey:@"sex"];
    [aCoder encodeInteger:self.age forKey:@"age"];
}

```

## 3.增删改查

``` objc

- (void)updataPersonObject:(id<NSCoding>)object{
    YYCache *cache = [YYCache cacheWithName:TJCacheName];
    cache.memoryCache.shouldRemoveAllObjectsOnMemoryWarning=YES;
    [cache setObject:object forKey:TJCacheKey];
}

- (void)removePerson{
    YYCache *cache = [YYCache cacheWithName:TJCacheName];
    [cache removeObjectForKey:TJCacheKey];
}

- (void)removeAllObjects{
    YYCache *cache = [YYCache cacheWithName:TJCacheName];
    [cache removeAllObjects];
}

+ (BOOL)checkPerson{
    YYCache *cache = [YYCache cacheWithName:TJCacheName];
    return [cache containsObjectForKey:TJCacheKey];
}

- (PersonModel *)readPerson{
    YYCache *cache = [YYCache cacheWithName:TJCacheName];
    PersonModel *model = (PersonModel *)[cache objectForKey:TJCacheKey];
    return model;
}

```

### Demo下载
[TJCache](https://github.com/wangpt/TJCache)

## 后记

此文档会不断更新
