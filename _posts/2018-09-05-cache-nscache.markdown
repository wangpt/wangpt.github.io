---
layout:     post
title:      "iOS缓存管理"
subtitle:   " \"Exmple for YYCache PINCache\""
date:       2018-09-05 12:00:00
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

## YYCache
*通过YYCache缓存自定义对象*

*遵守NSCoding协议*


``` objc

@interface PersonInfoModel : NSObject<NSCoding>
@property (nonatomic, copy) NSString *name;
@property (nonatomic, copy) NSString *sex;
@property (nonatomic, assign) NSInteger age;
@end


```
---

*对象序列化*

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

## 增删改查

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

---

## PINCache
*前两步等同于YYCache*

## 增删改查
*同步方法*

``` objc
- (void)updataPersonObject:(id<NSCoding>)object{
    PINCache *cache = [[PINCache sharedCache] initWithName:TJCacheKey];
    [cache setObject:object forKey:TJCacheKey];
}

- (void)removePerson{
    PINCache *cache = [[PINCache sharedCache] initWithName:TJCacheKey];
    [cache removeObjectForKey:TJCacheKey];
}

- (void)removeAllObjects{
    PINCache *cache = [[PINCache sharedCache] initWithName:TJCacheKey];
    [cache removeAllObjects];
}

+ (BOOL)checkPerson{
    PINCache *cache = [[PINCache sharedCache] initWithName:TJCacheKey];
    return [cache containsObjectForKey:TJCacheKey];
}

- (PersonModel *)readPerson{
    PINCache *cache = [[PINCache sharedCache] initWithName:TJCacheKey];
    PersonModel *model = (PersonModel *)[cache objectForKey:TJCacheKey];
    return model;
}

```
*异步方法*

``` objc
- (void)updataAsynPersonObject:(id<NSCoding>)object withBlock:(void (^)(void))block{
    YYCache *cache = [YYCache cacheWithName:TJCacheName];
    [cache setObject:object forKey:TJCacheKey withBlock:block];
}

- (void)removeAsynPersonWithBlock:(void (^)(NSString *key))block{
    YYCache *cache = [YYCache cacheWithName:TJCacheName];
    [cache removeObjectForKey:TJCacheKey withBlock:block];
}

- (void)removeAllObjectsWithBlock:(void(^)(void))block{
    YYCache *cache = [YYCache cacheWithName:TJCacheName];
    [cache removeAllObjectsWithBlock:block];
}

+ (void)checkAsynPersonWithBlock:(void (^)(NSString *key, BOOL contains))block{
    YYCache *cache = [YYCache cacheWithName:TJCacheName];
    [cache containsObjectForKey:TJCacheKey withBlock:block];
}

- (void)readAsynPersonWithBlock:(void (^)(NSString *key, id<NSCoding> object))block{
    YYCache *cache = [YYCache cacheWithName:TJCacheName];
    [cache objectForKey:TJCacheKey withBlock:block];
}

```
### Demo下载
[TJCache](https://github.com/wangpt/TJCache)

## 后记

此文档会不断更新
