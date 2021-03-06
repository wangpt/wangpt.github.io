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

> “常用的缓存总结，包含YYCache，PINCache ”


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

static YYCache *_dataCache;
static NSString *const TJCacheName = @"TJCacheName";

+ (void)initialize
{
    _dataCache = [YYCache cacheWithName:TJCacheName];
}

#pragma mark - 增改

+ (void)updataObject:(id<NSCoding>)object forKey:(NSString *)key{
    [_dataCache setObject:object forKey:key];
}

+ (void)updataObject:(id<NSCoding>)object forKey:(NSString *)key withBlock:(void (^)(void))block{
    [_dataCache setObject:object forKey:key withBlock:block];
}
#pragma mark - 删除

+ (void)removeObjectForKey:(NSString *)key{
    [_dataCache removeObjectForKey:key];
}

+ (void)removeObjectForKey:(NSString *)key withBlock:(void (^)(NSString *key))block{
    [_dataCache removeObjectForKey:key withBlock:block];
}

+ (void)removeAllObjects{
    [_dataCache.diskCache removeAllObjects];
}

+ (void)removeAllObjectsWithBlock:(void(^)(void))block {
    [_dataCache.diskCache removeAllObjectsWithBlock:block];
}

#pragma mark - 查找

+ (NSInteger)totalCost{
    return [_dataCache.diskCache totalCost];
}

+ (BOOL)containsObjectForKey:(NSString *)key{
    return [_dataCache containsObjectForKey:key];
}

+ (void)containsObjectForKey:(NSString *)key withBlock:(void (^)(NSString *key, BOOL contains))block {
    return [_dataCache containsObjectForKey:key withBlock:block];
}

+ (id<NSCoding>)objectForKey:(NSString *)key{
    return [_dataCache objectForKey:key];
}

+ (void)objectForKey:(NSString *)key withBlock:(void (^)(NSString *key, id<NSCoding> object))block {
    [_dataCache objectForKey:key withBlock:block];
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
### 代码下载
[TJCache](https://github.com/wangpt/TJCache)

