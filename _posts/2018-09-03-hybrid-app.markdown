---
layout:     post
title:      "iOS混合开发"
subtitle:   " \"Exmple for WebViewJavascriptBridge\""
date:       2018-09-03 12:00:00
author:     "Wangpt"
header-img: "img/post-bg-2015.jpg"
catalog: true
tags:
    - Hybrid
    - OC

---

> “欢迎关注和分享 ”


## 简介
*Hybrid App是指介于web-app、native-app这两者之间的app，对于iOS涉及的就是JS与OC之间的交互*

---

## 利用WebViewJavascriptBridge实现Hybrid
*在UIWebViews / WebViews中在Obj-C和JavaScript之间发送消息的桥接*
### 原理
*监听decidePolicyForNavigationAction或shouldStartLoadWithRequest方法，判断URL是否是需要bridge的URL，注入JS进行处理*
### 开始
*属于轻量级嵌入，需要JS和OC端分别进行处理*
### JS端嵌入方式
1.这段代码是固定的，必须要放到js中

``` objc
    function setupWebViewJavascriptBridge(callback) {
        if (window.WebViewJavascriptBridge) { return callback(WebViewJavascriptBridge); }
        if (window.WVJBCallbacks) { return window.WVJBCallbacks.push(callback); }
        window.WVJBCallbacks = [callback];
        var WVJBIframe = document.createElement('iframe');
        WVJBIframe.style.display = 'none';
        WVJBIframe.src = 'https://__bridge_loaded__';
        document.documentElement.appendChild(WVJBIframe);
        setTimeout(function() { document.documentElement.removeChild(WVJBIframe) }, 0)
    }
```
---
2.与OC交互位置编写位置

``` objc
     setupWebViewJavascriptBridge(function(bridge) {
    })
```
---
3.JS给OC提供的API

``` objc
    bridge.registerHandler('JSAlertEmaple', function() {
        alert("调用JS无参数和返回值")
    })
    bridge.registerHandler('getJSUserInfo', function(data, responseCallback) {
        var responseData = {}
        if (data.userId == 'tj001') {
            responseData.userName = '小明'
        } else {
            responseData.userName = '小红'
        }
        alert("返回用户："+responseData.userName)
        responseCallback(responseData)
    })
```
---
4.OC给JS提供的API

``` objc
    document.getElementById('btn').onclick = function () {
        bridge.callHandler('fromjsExample', {'check': 'isuiwebview'}, function responseCallback(responseData) {
            alert('OC中返回的参数:'+ responseData)
        })
    }
```

### iOS端如何使用

1.OC注册JS调用

``` objc
    [_bridge registerHandler:@"fromjsExample" handler:^(id data, WVJBResponseCallback responseCallback) {
        if ([data[@"check"] isEqualToString:@"isuiwebview"]) {
            responseCallback(@"success");
        }else{
            responseCallback(@"error");

        }
    }];
```
---
2.JS注册OC调用

``` objc
- (void)buttonClick:(UIButton *)button{
    if (button.tag == 100) {
        [self.bridge callHandler:@"JSAlertEmaple" data:nil];
    }else{
        [self.bridge callHandler:@"getJSUserInfo" data:@{@"userId":@"tj001"} responseCallback:^(id responseData) {
            NSLog(@"from js: %@", responseData[@"userName"]);
        }];
    }

}
```
---
### Demo下载
[TJBridge](https://github.com/wangpt/TJBridge)

## 后记

此文档会不断更新
