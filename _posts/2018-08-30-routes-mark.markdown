---
layout:     post
title:      "iOS组件化设计"
subtitle:   " \"Exmple for JLRoutes\""
date:       2018-08-30 12:00:00
author:     "Wangpt"
header-img: "img/post-bg-2015.jpg"
catalog: true
tags:
    - iOS   
    - Route
---

> “欢迎关注和收藏 ”


## 组件化
*用于拆分复杂的业务逻辑，加快代码的编译时间，也是为了更高的复用性和可维护性等目的。*

### 常用的组件化工具
[JLRoutes](https://github.com/joeldev/JLRoutes)
[DeepLinkKit](https://github.com/button/DeepLinkKit)
[MGJRouter](https://github.com/meili/MGJRouter)

### 文章描述
[蘑菇街 App 的组件化之路](https://www.jianshu.com/p/cdf94a963c27)
[蘑菇街 App 的组件化之路·续](https://blog.csdn.net/daiyelang/article/details/51648004)
[滴滴的组件化实践与优化](http://www.infoq.com/cn/articles/xiaojukeji-component-practice-and-optimization)

---

## 内容
### 对于JLRoutes进行组件化
*JLRoutes原理：它是通过url scheme来实现app内部，web到app，app与app之间跳转的第三方库*

## 应用场景
## 1.APP内部跳转
``` objc
// push
// 路由 /TJPushRoute/:controller
[[JLRoutes globalRoutes] addRoute:TJPushRoute handler:^BOOL(NSDictionary<NSString *,id> * _Nonnull parameters) {
    dispatch_async(dispatch_get_main_queue(), ^{
        UIViewController *currentVc = [self currentViewController];
        UIViewController *v = [[NSClassFromString(parameters[@"controller"]) alloc] init];
        [self paramToVc:v param:parameters];
        [currentVc.navigationController pushViewController:v animated:YES];
    });
    return YES;
}];
// present
[[JLRoutes globalRoutes] addRoute:TJPresentRoute handler:^BOOL(NSDictionary<NSString *,id> * _Nonnull parameters) {
    dispatch_async(dispatch_get_main_queue(), ^{
        UIViewController *currentVc = [self currentViewController];
        UIViewController *v = [[NSClassFromString(parameters[@"controller"]) alloc] init];
        [self paramToVc:v param:parameters];
        [currentVc.navigationController presentViewController:v animated:YES completion:nil];

    });
    return YES;
}];
// sb push
[[JLRoutes globalRoutes] addRoute:TJStoryBoardPushRoute handler:^BOOL(NSDictionary<NSString *,id> * _Nonnull parameters) {
    UIViewController *currentVc = [self currentViewController];
    UIStoryboard *storyboard = [UIStoryboard storyboardWithName:parameters[@"sbname"] bundle:nil];
    UIViewController *v  = [storyboard instantiateViewControllerWithIdentifier:parameters[@"bundleid"]];
    [self paramToVc:v param:parameters];
    [currentVc.navigationController pushViewController:v animated:YES];
    return YES;
}];

```

---
### Demo下载地址
[TJRoutes](https://github.com/wangpt/TJRoutes)
## 后记

此文档会不断更新 
