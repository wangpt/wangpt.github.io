---
layout:     post
title:      "iOS常用第三方框架"
subtitle:   " \"Github上关于iOS的各种开源项目集合\""
date:       2018-08-29 12:00:00
author:     "Wangpt"
header-img: "img/post-bg-2015.jpg"
catalog: true
tags:
    - iOS   
    - vendor
---

> “这里会涉及一些介绍和总结 ”


## 关于

对于常用的iOS框架的总结，基于[Awesome-iOS](https://github.com/vsouza/awesome-ios)

---

### 概览

- [应用路由](#应用路由)
- [实景增强](#实景增强)
- [混合](#混合)
- [缓存](#缓存)
- [图表](#图表)
- [代码质量](#代码质量)
- [代码分析](#代码分析)
- [颜色](#颜色)
- [CoreData](#CoreData)
- [数据库](#数据库)
- [数据结构算法](#数据结构算法)
- [时间](#时间)
- [调试](#调试)
- [开发异步](#开发异步)
- [文件](#文件)
- [函数式编程](#函数式编程)
- [GCD](#GCD)
- [手势](#手势)
- [图像](#图像)
- [硬件](#硬件)
- [布局](#布局)
- [记录](#记录)
- [机器学习](#机器学习)
- [算法](#算法)
- [消息](#消息)
- [网络](#网络)
- [通知](#通知)
- [解析](#解析)
- [支付](#支付)
- [权限](#权限)
- [响应式编程](#响应式编程)
- [SDK](#SDK)
- [加密](#加密)
- [秘钥](#秘钥)
- [服务器](#服务器)
 
## 内容
### 应用路由
*优雅的URL路由，导航框架，深层链接等*
* [JLRoutes](https://github.com/joeldev/JLRoutes) - iOS的URL路由库.
* [DeepLinkKit](https://github.com/button/DeepLinkKit) - 出色的路由匹配.
* [MGJRouter](https://github.com/meili/MGJRouter) -  高效/灵活的路由库

### 实景增强

*可帮助您构建无与伦比的增强现实体验*

* [Awesome-ARKit](https://github.com/olucurious/Awesome-ARKit) -ARKit项目和资源的精选列表.

### 混合

*在Objective-C和Swift，iOS和macOS，Javascript和Objective-C之间共享代码.*

* [react-native](https://github.com/facebook/react-native) - React Native完美兼容使用Objective-C、Java或是Swift编写的组件。 如果你需要针对应用的某一部分特别优化，中途换用原生代码编写也很容易
* [JSPatch](https://github.com/bang590/JSPatch) - 使用Objective-C运行时的JSPatch桥接Objective-C和Javascript。您可以通过包含一个小引擎来调用JavaScript中的任何Objective-C类和方法。JSPatch通常用于修补程序iOS App.
* [WebViewJavascriptBridge](https://github.com/marcuswestin/WebViewJavascriptBridge) - 在UIWebViews / WebViews中在Obj-C和JavaScript之间发送消息的桥接


### 缓存
*高性能缓存库和框架*

* [HanekeSwift](https://github.com/Haneke/HanekeSwift) - 用Swift编写的轻量级通用缓存
* [PINCache](https://github.com/pinterest/PINCache) - 适用于iOS和macOS的平台，安全的对象缓存
* [YYCache](https://github.com/ibireme/YYCache) - 适用于iOS的高性能缓存框架.

### 图表
*美观，简单，完全定制的图表*

* [Charts](https://github.com/danielgindi/Charts) -  iOS功能强大的图表/图表框架，相当于[MPAndroidChart](https://github.com/PhilJay/MPAndroidChart).
* [PNChart](https://github.com/kevinzhow/PNChart) - iOS中使用的简单而美观的图表库
* [Scrollable-GraphView](https://github.com/philackm/ScrollableGraphView) - 自适应可滚动图形视图，可视化简单的离散数据集。用Swift写的.
* [AAChartKit](https://github.com/AAChartKit/AAChartKit) - 多达几十种的信息图图表

### 代码质量

 *质量总是很重要。代码检查器 内存管理检测*

 * [MLeaksFinder](https://github.com/Tencent/MLeaksFinder) - 查找在开发时iOS应用中的内存泄漏.
* [FBMemoryProfiler](https://github.com/facebook/FBMemoryProfiler) - 帮助分析iOS内存使用情况的iOS工具.
* [FBRetainCycleDetector](https://github.com/facebook/FBRetainCycleDetector) - 帮助检测运行时保留周期的iOS库.


### 代码分析

*静态代码分析器*

* [Swiftlint](https://github.com/realm/SwiftLint) - 强制执行Swift风格和约定的工具.
* [OCLint](https://github.com/oclint/oclint) - 用于提高质量和减少缺陷的静态代码分析工具.


## 颜色
*十六进制颜色扩展，主题，颜色选择器和其他令人敬畏的颜色工具.*

* [Chameleon](https://github.com/ViccAlexander/Chameleon) - 适用于iOS（ObjC和Swift）的轻量级但功能强大的平面颜色框架.
* [Colours](https://github.com/bennyguitar/Colours) - 漂亮的预定义颜色和一组颜色方法，使您的iOS / macOS开发生活更轻松.
* [DKNightVersion](https://github.com/Draveness/DKNightVersion) - 管理色彩，整合夜晚/多个主题
* [SwiftTheme](https://github.com/jiecao-fm/SwiftTheme) - 主题/换肤, 夜间模式

## CoreData
*Core Data框架*

* [MagicalRecord](https://github.com/magicalpanda/MagicalRecord) - 可以帮助轻松的使用CoreData框架

## 数据库
*用于处理短暂和持久的数据*

* [Realm](https://github.com/realm/realm-cocoa) - 作为CoreData和SQLite的替代品，使用简单快速
* [YapDatabase](https://github.com/yapstudios/YapDatabase) - 是iOS和Mac的可扩展数据库
* [FMDB](https://github.com/ccgus/fmdb) - 封装SQLite的框架
* [SwiftyUserDefaults](https://github.com/radex/SwiftyUserDefaults) - 静态类型的NSUserDefaults
* [SQLite.swift](https://github.com/stephencelis/SQLite.swift) - 基于SQLite3安全的框架使用Swift编写
* [WCDB](https://github.com/Tencent/wcdb) - 是一个高效，完整，易于使用的iOS，macOS移动数据库框架

## 数据结构算法
*令人惊叹的数据结构包装器和库*

* [Dollar](https://github.com/ankurp/Dollar) - Swift语言的功能工具带，类似于Javascript中的Lo-Dash或Underscore.js
* [swift-algorithm-club](https://github.com/raywenderlich/swift-algorithm-club) - Swift中的算法和数据结构，带有解释

## 时间
*时间和NSCalendar库,以及NSDate扩展等*

* [SwiftDate](https://github.com/malcommac/SwiftDate) - Swift中管理日期和时区的最佳方式
*  [DateTools](https://github.com/MatthewYork/DateTools) - Objective-C中的日期和时间变得简单

## 调试
*调试工具，崩溃报告，日志和控制台UI*

* [FLEX](https://github.com/Flipboard/FLEX) - 适用于iOS的应用内调试和探索工具
* [chisel](https://github.com/facebook/chisel) - Chisel是LLDB命令的集合，用于帮助调试iOS应用程序
* [PonyDebugger](https://github.com/square/PonyDebugger) - 使用Chrome开发者工具为您的原生iOS应用程序进行远程网络和数据调试
* [GodEye](https://github.com/zixun/GodEye) - 使用基于Swift的一行代码自动显示日志，崩溃，网络，ANR，泄漏，CPU，RAM，FPS，NetFlow，文件夹等

## 开发异步
*可以帮助您在Swift中编写更好的异步代码*

* [PromiseKit](https://github.com/mxcl/PromiseKit) - 专门针对 Swift 和 Objective-C 语言的解决方案
* [Bolts-ObjC](https://github.com/BoltsFramework/Bolts-ObjC) - 库的集合，旨在使开发移动应用程序更容易

## 文件
*文件管理，zip处理*

* [ZipArchive](https://github.com/ZipArchive/ZipArchive) - ZipArchive是一个简单的实用程序类，用于在iOS和Mac上压缩和解压缩文件

## 函数式编程
*Swift函数编程工具的集合*

* [Swiftz](https://github.com/typelift/Swiftz) - Swift中的函数式编程
* [Argo](https://github.com/thoughtbot/Argo) - 函数式JSON解析库

## GCD
*GCD工具*

* [Async](https://github.com/duemunk/Async) - GCD在swift上的体现

## 手势
*用于处理手势的库和工具*

* [FDFullscreenPopGesture](https://github.com/forkingdog/FDFullscreenPopGesture) - UINavigationController的类别，启用iOS7 +系统风格的全屏弹出手势

## 图像
*CoreGraphics，CoreAnimation，SVG，CGContext库*

* [SVGKit](https://github.com/SVGKit/SVGKit) - 可缩放的矢量图形
* [Macaw](https://github.com/exyte/macaw) -  功能强大且易于使用的矢量图形库

## 硬件
*蓝牙,用于处理附近设备*

* [BabyBluetooth](https://github.com/coolnameismy/BabyBluetooth) - 一个非常容易使用的蓝牙库

*ImagePickers和可自定义相机实现的多个选项*

* [ImagePicker](https://github.com/hyperoslo/ImagePicker) - 对于ImagePicker的封装

*位置管理*

* [LocationManager](https://github.com/intuit/LocationManager) - 提供基于块的异步API，以便一次或连续地请求当前位置

## 布局
*系统布局封装*

* [Masonry](https://github.com/SnapKit/Masonry) - 简单的使用AutoLayout NSLayoutConstraints的强大功能
* [PureLayout](https://github.com/PureLayout/PureLayout) - UIView类别，可以轻松地在代码中创建布局约束
* [SnapKit](https://github.com/SnapKit/SnapKit) - 适用于iOS和macOS的Swift Autolayout
* [Cartography](https://github.com/robb/Cartography) - Swift的声明性自动布局
* [Neon](https://github.com/mamaral/Neon) - 一个强大的Swift编程UI布局框架
* [UITableView-FDTemplateLayoutCell](https://github.com/forkingdog/UITableView-FDTemplateLayoutCell) - 用于自动UITableViewCell高度计算的模板自动布局单元格
* [Bond](https://github.com/DeclarativeHub/Bond) - Bond是一个Swift绑定框架，它将绑定概念提升到一个全新的水平。它简单，强大，类型安全，多范式
* [MyLinearLayout](https://github.com/youngsoft/MyLinearLayout) - MyLayout是一个由Objective-C实现的强大的iOS UI框架
* [yoga](https://github.com/facebook/yoga/tree/master/YogaKit) - 强大的布局引擎，实现Flexbox。由Facebook开发和维护。

## 记录
*调试,记录工具，框架，集成等*

* [CocoaLumberjack](https://github.com/CocoaLumberjack/CocoaLumberjack) - 简单但功能强大且灵活的日志框架
* [NSLogger](https://github.com/fpillet/NSLogger) - 一种高性能日志记录实用程序
* [SwiftyBeaver](https://github.com/SwiftyBeaver/SwiftyBeaver) - 开发和发布期间的便捷日志记录
* [XCGLogger](https://github.com/DaveWoodCom/XCGLogger) - 用于Swift项目的调试日志框架。允许您将详细信息记录到控制台（以及可选的文件），就像使用NSLog或println一样

## 机器学习
*机器学习框架*

* [tensorflow](https://github.com/tensorflow/tensorflow/tree/master/tensorflow/examples/ios) - 官方Google构建的强大神经网络库端口
* [caffe2](https://github.com/caffe2/caffe2) - 轻量级，模块化和可扩展的深度学习框架
* [Awesome-CoreML-Models](https://github.com/likedan/Awesome-CoreML-Models) - 一系列独特的Core ML模型
* [Swift-AI](https://github.com/Swift-AI/Swift-AI) - Swift机器学习库

## 算法
*常用算法*

* [Surge](https://github.com/mattt/Surge) - 一个Swift库，它使用Accelerate框架为矩阵数学，数字信号处理和图像处理提供高性能函数。


## 媒体
*音频*

* [AudioKit](https://github.com/audiokit/AudioKit) - 用于合成，处理和分析声音的强大工具包
* [EZAudio](https://github.com/syedhali/EZAudio) - 基于Core Audio构建的iOS / macOS音频可视化框架

*GIF*

* [FLAnimatedImage](https://github.com/Flipboard/FLAnimatedImage) - 适用于iOS的Performant动画GIF引擎

*图片*

* [GPUImage](https://github.com/BradLarson/GPUImage) - 基于GPU的图像和视频处理的开源iOS框架
* [SDWebImage](https://github.com/rs/SDWebImage) - 具有UIImageView类别的缓存支持的异步图像下载程序
* [PINRemoteImage](https://github.com/pinterest/PINRemoteImage) - 线程安全，高性能，功能丰富的图像获取器
* [FastImageCache](https://github.com/path/FastImageCache) - 用于在滚动时快速显示图像的iOS库
* [AlamofireImage](https://github.com/Alamofire/AlamofireImage) - Alamofire的图像组件库
* [Nuke](https://github.com/kean/Nuke) - 图像加载，处理，缓存和预热
* [YYWebImage](https://github.com/ibireme/YYWebImage) - 异步图像加载框架
* [Kingfisher](https://github.com/onevcat/Kingfisher) - 轻量级和纯Swift实现的库，用于从Web下载和缓存图像
* [MWPhotoBrowser](https://github.com/mwaterfall/MWPhotoBrowser) - 一个简单的iOS照片和视频浏览器，带有网格视图，标题和选择
* [GPUImage2](https://github.com/BradLarson/GPUImage2) - GPUImage 2是一个获得BSD许可的Swift框架，用于GPU加速视频和图像处理

*媒体处理*

* [SwiftOCR](https://github.com/garnele007/SwiftOCR) - 用Swift编写的快速简单的OCR库

*PDF*

* [Reader](https://github.com/vfr/Reader) - 适用于iOS的PDF阅读器核心

*媒体流*

* [LFLiveKit](https://github.com/LaiFengiOS/LFLiveKit) - H264和AAC硬编码，支持GPUImage Beauty，rtmp传输，弱网络丢帧，动态切换速率

*视频*

* [ZFPlayer](https://github.com/renzifeng/ZFPlayer) - 支持定制任何播放器SDK和控制层


## 消息
*消息*

* [XMPPFramework](https://github.com/robbiehanson/XMPPFramework) - 适用于Mac和iOS的Objective-C中的XMPP框架
* [Chatto](https://github.com/badoo/Chatto) - 适用于Mac和iOS的Objective-C中的XMPP框架
* [SlackTextViewController](https://github.com/slackhq/SlackTextViewController) - 一个插入式UIViewController子类，具有不断增长的文本输入视图和其他有用的消息传递功能
* [Atlas-iOS](https://github.com/layerhq/Atlas-iOS) - 聊天SDK iOS - 开源移动信使
* [Messenger](https://github.com/relatedcode/Messenger) - 适用于iOS的流畅，响应灵活的消息UI库

## 网络
*网络封装*

* [AFNetworking](https://github.com/AFNetworking/AFNetworking) - 一个令人愉快的iOS和macOS网络框架
* [RestKit](https://github.com/RestKit/RestKit) - RestKit是一个在iOS和OS X上使用和RESTful Web资源的框架
* [Alamofire](https://github.com/Alamofire/Alamofire) - Alamofire是一个用Swift编写的HTTP网络库，来自AFNetworking的创建者
* [CocoaAsyncSocket](https://github.com/robbiehanson/CocoaAsyncSocket) - 适用于Mac和iOS的异步套接字网络库
* [Reachability.swift](https://github.com/ashleymills/Reachability.swift) - 用Swift重写了用Swift重写的Apple的Reachability
* [Moya](https://github.com/Moya/Moya) - 用Swift编写的网络抽象层
* [YTKNetwork](https://github.com/yuantiku/YTKNetwork) - YTKNetwork是基于AFNetworking的高级请求工具

## 通知
*通知消息*

* [fastlane](https://github.com/fastlane/fastlane/tree/master/pem) - 自动生成和更新推送通知配置文件
* [Knuff](https://github.com/KnuffApp/Knuff) - Apple推送通知服务（APNS）的调试应用程序
* [NWPusher](https://github.com/noodlewerk/NWPusher) - 使用Apple推送通知服务（APN）的macOS和iOS应用程序和框架

## 解析
*数据解析*

* [json-framework](https://github.com/stig/json-framework) - 框架在Objective-C中实现了严格的JSON解析器和生成器
* [Mantle](https://github.com/Mantle/Mantle) - Cocoa和Cocoa Touch的模型框架
* [jsonmodel](https://github.com/JSONModel/JSONModel) - JSON的神奇数据建模框架。创建快速强大的原子和智能数据模型类
* [SwiftyJSON](https://github.com/SwiftyJSON/SwiftyJSON) - 在Swift中处理JSON数据的更好方法
* [ObjectMapper](https://github.com/Hearst-DD/ObjectMapper) - 用Swift编写的框架，使您可以轻松地将Model对象（Classes和Structs）转换为JSON和从JSON转换
* [YYModel](https://github.com/ibireme/YYModel) - iOS / macOS的高性能模型框架
* [JSONExport](https://github.com/Ahmed-Ali/JSONExport) - JSONExport是一个用于macOS的桌面应用程序，它使您能够将JSON对象作为模型类导出，并使用您喜欢的语言创建相关的构造函数
* [MJExtension](https://github.com/CoderMJLee/MJExtension) - JSON和模型之间的快速，方便和非侵入式转换。您的模型类不需要扩展另一个基类。您无需修改​​任何模型文件。


## 支付
*应用程序购买*

* [SwiftyStoreKit](https://github.com/bizz84/SwiftyStoreKit) - 轻量级应用程序购买适用于iOS 8.0+和macOS 9.0+的Swift框架

## 权限
*应用程序权限*

* [Permission](https://github.com/delba/Permission) - 在iOS上请求权限的统一API

## 响应式编程
*响应式编程框架*

* [RxSwift](https://github.com/ReactiveX/RxSwift) - Swift中的响应式编程
* [ReactiveCocoa](https://github.com/ReactiveCocoa/ReactiveCocoa) - 函数响应式编程框架
* [ReSwift](https://github.com/ReSwift/ReSwift) - Swift中的单向数据流
* [JASONETTE-iOS](https://github.com/Jasonette/JASONETTE-iOS) - 基于HTTP的Native App。只用JSON创建你自己的原生iOS应用程序

## SDK
*优秀的SDK框架*

* [facebook-objc-sdk](https://github.com/facebook/facebook-objc-sdk) - Facebook iOS SDK
* [ResearchKit](https://github.com/ResearchKit/ResearchKit) - ResearchKit是一个开源软件框架，可以轻松地为医学研究或其他研究项目创建应用程序

## 加密
*加密库*

* [CryptoSwift](https://github.com/krzyzanowskim/CryptoSwift) - 第三方加密库
* [RNCryptor](https://github.com/RNCryptor/RNCryptor) - 用于Swift中iOS和Mac的CCCryptor（AES加密）包装器

## 秘钥
*秘钥保存信息*

* [Valet](https://github.com/square/Valet) - 安全地将数据存储在iOS或macOS Keychain中，而无需了解Keychain的工作原理
* [KeychainAccess](https://github.com/kishikawakatsumi/KeychainAccess) - 适用于iOS和macOS的Keychain的简单Swift包装器
* [SAMKeychain](https://github.com/soffes/SAMKeychain) - 适用于Mac和iOS的钥匙串的简单Objective-C包装器

## 服务器
*服务器端项目支持协同程序，Linux，MacOS，iOS，Apache模块，异步调用，libuv等。*

* [Perfect](https://github.com/PerfectlySoft/Perfect) - 服务器端Swift。完美的库，应用程序服务器，连接器和示例应用程序
* [CocoaHTTPServer](https://github.com/robbiehanson/CocoaHTTPServer) - 用于macOS或iOS应用程序的小型，轻量级，可嵌入的HTTP服务器
* [vapor](https://github.com/vapor/vapor) - 适用于iOS，macOS和Ubuntu的Swift优雅Web框架
* [Kitura](https://github.com/IBM-Swift/Kitura) - Swift Web框架和HTTP服务器
* [GCDWebServer](https://github.com/swisspol/GCDWebServer) - 用于macOS和iOS的基于轻量级GCD的HTTP服务器（包括基于Web的上传器和WebDAV服务器）

---
## 后记

此文档会不断更新
