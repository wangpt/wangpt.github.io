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

> “欢迎关注和分享”


## 简介
*组件化用于拆分复杂的业务逻辑，解决模块之间的相互依赖，加快代码的编译时间，也是为了更高的复用性和可维护性。*

### 常用工具
[JLRoutes](https://github.com/joeldev/JLRoutes)

[DeepLinkKit](https://github.com/button/DeepLinkKit)

[MGJRouter](https://github.com/meili/MGJRouter)

### 文章描述
[蘑菇街 App 的组件化之路](https://www.jianshu.com/p/cdf94a963c27)

[蘑菇街 App 的组件化之路·续](https://blog.csdn.net/daiyelang/article/details/51648004)

[滴滴的组件化实践与优化](http://www.infoq.com/cn/articles/xiaojukeji-component-practice-and-optimization)

---

## 利用JLRoutes实现组件化
*通过url scheme来实现app内部，web到app，app与app之间跳转的第三方库，它旨在使用最少的代码轻松处理应用程序中的复杂URL方案*

### 说明
*LRoutes 2.x需要iOS 8.0+或macOS 10.10+*
### 文档
[JLRoutes地址](https://github.com/joeldev/JLRoutes)

[官方API](http://cocoadocs.org/docsets/JLRoutes/2.0.5/)
### 开始
[在Info.plist中配置您的URL schemes](https://developer.apple.com/library/archive/documentation/iPhone/Conceptual/iPhoneOSProgrammingGuide/Inter-AppCommunication/Inter-AppCommunication.html#//apple_ref/doc/uid/TP40007072-CH6-SW2)

1.进行url拦截

``` objc
- (BOOL)application:(UIApplication *)app openURL:(NSURL *)url options:(NSDictionary<UIApplicationOpenURLOptionsKey,id> *)options{
    NSString *str = url.absoluteString;
    NSArray *arr = [str componentsSeparatedByString:@"://"];
    if ([[arr.firstObject lowercaseString] isEqualToString:@"tjroutesschemesthing"]) {
        return [[JLRoutes routesForScheme:@"TJRoutesSchemesThing"]routeURL:url];
    }else if ([[arr.firstObject lowercaseString] isEqualToString:@"tjroutesschemesstuff"]){
        return [[JLRoutes routesForScheme:@"TJRoutesSchemesStuff"]routeURL:url];
    }
    else{
        return NO;
    }
}

```
---
2.进行Route注册

``` objc
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
    [self registerNavgationRouter];
    [self registerSchemaRouter];
    [self registerWildcardsRouter];
    return YES;
}

- (void)registerNavgationRouter
{
    [JLRoutes setVerboseLoggingEnabled:NO];
    JLRoutes.globalRoutes[@"/user/view/:userID"] = ^BOOL(NSDictionary *parameters) {
        NSString *userID = parameters[@"userID"];
        return YES;
    };
    [[JLRoutes globalRoutes] addRoute:@"/:object/:action/:primaryKey" handler:^BOOL(NSDictionary *parameters) {
        NSString *object = parameters[@"object"];
        NSString *action = parameters[@"action"];
        NSString *primaryKey = parameters[@"primaryKey"];
        return YES;
    }];
}

- (void)registerSchemaRouter
{
    [[JLRoutes routesForScheme:@"TJRoutesSchemesThing"] addRoute:@"/foo/view/:user" handler:^BOOL(NSDictionary<NSString *,id> * _Nonnull parameters) {
        return YES;
    }];
    [[JLRoutes routesForScheme:@"TJRoutesSchemesStuff"] addRoute:@"/foo/view" handler:^BOOL(NSDictionary<NSString *,id> * _Nonnull parameters) {
        return YES;
    }];
    [JLRoutes routesForScheme:@"TJRoutesSchemesThing"].shouldFallbackToGlobalRoutes = YES;
    [[JLRoutes globalRoutes] addRoute:@"/foo/view2" handler:^BOOL(NSDictionary *parameters) {
        return YES;
    }];
}

- (void)registerWildcardsRouter{
    [[JLRoutes globalRoutes] addRoute:@"/wildcard/*" handler:^BOOL(NSDictionary *parameters) {
        NSArray *pathComponents = parameters[JLRouteWildcardComponentsKey];
        if (pathComponents.count > 0 && [pathComponents[0] isEqualToString:@"joker"]) {
            return YES;
        }
        return NO;
    }];
}
```
---
3.实现跳转

``` objc
- (void)globalExample:(NSString *)path{
    [JLRoutes routeURL:[NSURL URLWithString:path]];
}

- (void)schemesExample:(NSString *)path{
    [[UIApplication sharedApplication] openURL:[NSURL URLWithString:path]];
}
```
---
### Demo下载
[TJRoutes](https://github.com/wangpt/TJRoutes)
## 后记

此文档会不断更新 
