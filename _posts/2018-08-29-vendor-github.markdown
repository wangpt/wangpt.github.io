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
- [文字](#文字)
- [测试](#测试)
- [UIKit](#UIKit) 
- [扩展](#扩展)
- [引导页](#引导页)
- [WebSocket](#WebSocket)
- [包管理](#包管理)
- [工具](#工具)
- [插件](#插件)
- [发布](#发布)
- [应用商城](#应用商城)


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

## 文字
*富文本框架*

* [nimbus](https://github.com/jverkoey/nimbus) - Nimbus是经验丰富的iOS软件设计人员的工具包
* [DTCoreText](https://github.com/Cocoanetics/DTCoreText) - 允许在CoreText中使用HTML代码的方法
* [YYText](https://github.com/ibireme/YYText) - 强大的iOS文本框架，用于显示和编辑富文本
* [FormatterKit](https://github.com/mattt/FormatterKit) - stringWithFormat:用于复杂的格式

## 测试
*测试框架*

* [Kiwi](https://github.com/kiwi-bdd/Kiwi) - 用于iOS开发的行为驱动开发库
* [Quick](https://github.com/Quick/Quick) - Swift和Objective-C的行为驱动开发框架
* [OHHTTPStubs](https://github.com/AliSoftware/OHHTTPStubs) - 轻松存取您的网络请求！使用虚假网络数据和自定义响应时间，响应代码和标题测试您的应用程序！
* [Nimble](https://github.com/Quick/Nimble) -  Swift和Objective-C的匹配框架

## UIkit
*UI框架*

* [FlatUIKit](https://github.com/Grouper/FlatUIKit) - 适用于iOS的精美平面UI组件的集合
* [Texture](https://github.com/TextureGroup/Texture) - iOS应用程序的平滑异步用户界面
* [iCarousel](https://github.com/nicklockwood/iCarousel) - 适用于iOS和Mac OS的简单，高度可定制，数据驱动的3D轮播
* [tapkulibrary](https://github.com/devinross/tapkulibrary) - tap + haiku = tapku，一个精心设计的开源iOS框架
* [RKNotificationHub](https://github.com/cwRichardKim/RKNotificationHub)- 让任何UIView成为一个完整的通知中心
* [nui](https://github.com/tombenner/nui) - iOS应用程序，带有样式表，类似于CSS
* [Material](https://github.com/CosmicMind/Material) - Material是一个动画和图形框架，允许开发人员轻松创建漂亮的应用程序
* [FSPagerView](https://github.com/WenchaoD/FSPagerView) - FSPagerView是一个优雅的屏幕幻灯片库。它对制作横幅，产品展示，欢迎/指南页面，屏幕/ ViewController滑块非常有帮助
* [panelkit](https://github.com/louisdh/panelkit) - 在iOS上启用面板的UI框架

### 进度条
*各式美观的进度指示器HUD*

* [NVActivityIndicatorView](https://github.com/ninjaprox/NVActivityIndicatorView) - 精美加载动画的集合
* [MBProgressHUD](https://github.com/jdg/MBProgressHUD) - 用于在后台线程中完成工作时显示带有指示符和/或标签的半透明HUD
* [SVProgressHUD](https://github.com/SVProgressHUD/SVProgressHUD) - 适用于iOS应用程序的简洁进度HUD
* [M13ProgressSuite](https://github.com/Marxon13/M13ProgressSuite) - 一个包含许多工具的套件，用于显示iOS上的进度信息
* [PKHUD](https://github.com/pkluz/PKHUD) -  基于Swift的iOS 8及更高版本的Apple HUD（音量，振铃，旋转......）重新实现
* [NJKWebViewProgress](https://github.com/ninjinkun/NJKWebViewProgress) - UIWebView的进度界面库。您可以使用此模块为应用程序内浏览器实施进度条
* [SkeletonView](https://github.com/Juanpe/SkeletonView) - 向用户显示正在发生的事情的优雅方式，并为他们准备等待的内容做好准备

### 动画
* [pop](https://github.com/facebook/pop) -  可扩展的iOS和macOS动画库，适用于基于物理的交互
* [Spring](https://github.com/MengTo/Spring) - 简化Swift中iOS动画的库
* [Canvas](https://github.com/CanvasPod/Canvas) -  Xcode中的Animate，无需代码
* [IBAnimatable](https://github.com/IBAnimatable/IBAnimatable) -  使用IBAnimatable为Interface Builder中的App Store准备应用程序设计和原型UI，交互，导航，转换和动画。
* [Advance](https://github.com/timdonnelly/Advance) - 适用于iOS的强大动画框架
* [Shimmer](https://github.com/facebook/Shimmer) - 一种为iOS应用中的任何视图添加简单闪烁效果的简单方法
* [JHChainableAnimations](https://github.com/jhurray/JHChainableAnimations) - 在Objective-C中易于阅读和编写可链接的动画
* [Keyframes](https://github.com/facebookincubator/Keyframes) - 用于将基于Adobe AE形状的动画转换为数据格式并在Android和iOS设备上播放的库
* [lottie-ios](https://github.com/airbnb/lottie-ios) - 用于从Adobe After Effects实时渲染本机矢量动画的iOS库
* [AnimatedCollectionViewLayout](https://github.com/KelvinJin/AnimatedCollectionViewLayout) - 一个UICollectionViewLayout子类，用于向UICollectionView添加自定义过渡/动画
* [Pastel](https://github.com/cruisediary/Pastel) - 像Instagram一样的渐变动画效果
* [ViewAnimator](https://github.com/marcosgriselli/ViewAnimator) -  ViewAnimator只需一行即可实现您的用户界面

### 过渡
*过渡效果*

* [Hero](https://github.com/HeroTransitions/Hero) - 适用于iOS的Supercharged过渡引擎。根本没有代码构建自定义视图过渡。灵感来自Keynote的Magic Move

### 弹出框
*Alert & Action Sheet*
* [SCLAlertView-Swift](https://github.com/vikmeup/SCLAlertView-Swift) - 一个Swift库，用于设计自定义提示，提供多种选项供您选择
* [JDStatusBarNotification](https://github.com/calimarkus/JDStatusBarNotification) - 在状态栏顶部显示简单，可自定义的通知
* [Whisper](https://github.com/hyperoslo/Whisper) - 是一个使显示消息和应用内通知的任务变得简单的组件。它里面有三个不同的视图
* [CRToast](https://github.com/cruffenach/CRToast) - 可满足您的通知需求
* [SwiftMessages](https://github.com/SwiftKickMobile/SwiftMessages) - 一个用Swift编写的非常灵活的iOS消息栏
* [BulletinBoard](https://github.com/alexaubry/BulletinBoard) - 在iOS上生成和显示底部卡接口
* [alerts-and-pickers](https://github.com/dillidon/alerts-and-pickers) - 使用TextField，DatePicker，PickerView，TableView和CollectionView对本机UIAlertController进行高级使用。

### 按钮
*button*

* [DOFavoriteButton](https://github.com/okmr-d/DOFavoriteButton) - 用Swift编写的可爱动画按钮
* [VBFPopFlatButton](https://github.com/victorBaro/VBFPopFlatButton) - 使用POP的9种不同状态的平面按钮
* [LiquidFloatingActionButton](https://github.com/yoavlt/LiquidFloatingActionButton) - 材料设计浮动动作按钮处于液态

### 日历
*Calendar*
* [CVCalendar](https://github.com/CVCalendar/CVCalendar) - 编写的iOS 8+自定义可视日历
* [JTAppleCalendar](https://github.com/patchthecode/JTAppleCalendar) - 非官方的Swift Apple日历库。视图。控制。适用于iOS和tvOS

### 卡片 
*Cards*

* [Koloda](https://github.com/Yalantis/Koloda) -  KolodaView是一个旨在简化iOS上Tinder卡的实现的课程
* [Cards](https://github.com/PaoloCuscela/Cards) - AppStore的卡片视图

### 表格设置页
*Form*
 
* [XLForm](https://github.com/xmartlabs/XLForm) - XLForm是最灵活，最强大的iOS库，用于创建动态表视图表单。与Swift和Obj-C完全兼容
* [Eureka](https://github.com/xmartlabs/Eureka) - 纯粹的Swift中优雅的iOS表单构建器

### 键盘
*Keyboard*

* [IQKeyboardManager](https://github.com/hackiftekhar/IQKeyboardManager) - 无代码插入式通用库允许防止键盘滑动问题并覆盖UITextField / UITextView
* [TPKeyboardAvoiding](https://github.com/michaeltyson/TPKeyboardAvoiding) - 一种插入式通用解决方案，用于在iOS中将文本字段移出键盘

### 文字
*label*

* [LTMorphingLabel](https://github.com/lexrus/LTMorphingLabel) - 用Swift编写的UILabel的优美变形效果
* [TTTAttributedLabel](https://github.com/TTTAttributedLabel/TTTAttributedLabel) - UILabel的替代品，支持属性，数据检测器，链接等

### 菜单
*menu*

* [RESideMenu](https://github.com/romaonthego/RESideMenu) - iOS 7/8风格的侧面菜单，具有由Dribbble镜头启发的视差效果
* [SlideMenuControllerSwift](https://github.com/dekatotoro/SlideMenuControllerSwift) -  iOS幻灯片菜单基于Google+，iQON，Feedly，Ameba iOS应用程序查看。它是用纯粹的Swift编写的。
* [PageMenu](https://github.com/PageMenu/PageMenu) - 从滚动视图内部的其他视图控制器构建的分页菜单控制器
* [Persei](https://github.com/Yalantis/Persei) - 用Swift编写的UITableView / UICollectionView / UIScrollView的动画顶级菜单
* [ViewDeck](https://github.com/ViewDeck/ViewDeck) - Path 2.0或Facebook iOS应用程序中的滑动功能的实现

### 导航栏
*Navigation Bar*

* [TLYShyNavBar](https://github.com/telly/TLYShyNavBar) - 与所有那些傲慢的UINavigationBar不同，这个很害羞而且很谦虚！轻松创建自动滚动导航栏
* [LTNavigationBar](https://github.com/ltebean/LTNavigationBar) - UINavigationBar类别，允许您动态更改其外观
* [AMScrollingNavbar](https://github.com/andreamazz/AMScrollingNavbar) - 滚动UIScrollView之后的可滚动UINavigationBar

### 刷新
*Refresh*

* [MJRefresh](https://github.com/CoderMJLee/MJRefresh) - 使用pull-to-refresh的简单方法
* [SVPullToRefresh](https://github.com/samvermette/SVPullToRefresh) - 使用1行代码为任何UIScrollView提供pull-to-refresh和无限滚动。
* [CBStoreHouseRefreshControl](https://github.com/coolbeet/CBStoreHouseRefreshControl) - 完全可定制的pull-to-refresh控件

### 评星
*Rating*

* [HCSStarRatingView](https://github.com/hsousa/HCSStarRatingView) - 用Objective-C编写的iOS简单星级评级视图
* [Cosmos](https://github.com/evgenyneu/Cosmos) - iOS / Swift的星级评级控件

### ScrollView
*ScrollView*

* [VegaScroll](https://github.com/AppliKeySolutions/VegaScroll) - VegaScroll是一个用于UICollectionView的轻量级动画流程布局，完全用Swift 4编写，与iOS 11和Xcode 9兼容

### 分段
*Segmented*

* [HMSegmentedControl](https://github.com/HeshamMegid/HMSegmentedControl) - UISegmentedControl的替代品，用于模仿Google Currents和其他各种Google产品中使用的分段控件的样式。

### 状态栏
*StatusBar*

* [Bartinter](https://github.com/MaximKotliar/Bartinter) -  状态栏色调取决于后面的内容，动态更新

### 步进器
*Stepper*

* [GMStepper](https://github.com/gmertk/GMStepper) - 

### 开关
*Switch*

* [DGRunkeeperSwitch](https://github.com/gontovnik/DGRunkeeperSwitch) - Runkeeper设计开关控制
* [paper-switch](https://github.com/Ramotion/paper-switch) - RAMPaperSwitch是一个Swift模块，它在开关打开时绘制父视图

### TabBar
*TabBar*

* [animated-tab-bar](https://github.com/Ramotion/animated-tab-bar) -  RAMAnimatedTabBarController是一个Swift模块，用于向tabbar项添加动画。
* [FoldingTabBar.iOS](https://github.com/Yalantis/FoldingTabBar.iOS) - 折叠标签栏和标签栏控制器
* [XLPagerTabStrip](https://github.com/xmartlabs/XLPagerTabStrip) - 适用于iOS的Android PagerTabStrip
* [CYLTabBarController](https://github.com/ChenYilong/CYLTabBarController) - 最低只需传两个数组即可完成主流App框架搭建
* [ESTabBarController](https://github.com/eggswift/ESTabBarController) - iOS的标签栏控制器，允许突出显示按钮并为其设置自定义操作
* [RDVTabBarController](https://github.com/robbdimitrov/RDVTabBarController) - 高度自定义Tabbar

### 表视图
*TableView*

* [MGSwipeTableCell](https://github.com/MortimerGoro/MGSwipeTableCell) - UITableViewCell子类，允许显示具有各种过渡的可切换按钮
* [SWTableViewCell](https://github.com/CEWendel/SWTableViewCell) - 一个易于使用的UITableViewCell子类，它实现了一个可刷新的内容视图，该视图公开了实用工具按钮
* [MCSwipeTableViewCell](https://github.com/alikaragoz/MCSwipeTableViewCell) - 方便的UITableViewCell子类，实现可交换内容以触发操作
* [SwipeCellKit](https://github.com/SwipeCellKit/SwipeCellKit) - 基于Mail.app的Swipeable UITableViewCell，在Swift中实现
* [TimelineTableViewCell](https://github.com/kf99916/TimelineTableViewCell) - 编写的UITableViewCell实现的简单时间线视图

### 集合视图
*CollectionView* 

* [IGListKit](https://github.com/Instagram/IGListKit) - 一个数据驱动的UICollectionView框架，用于构建快速灵活的列表
* [CollectionKit](https://github.com/SoySauceLab/CollectionKit) - 用于构建可重用数据驱动的集合组件的现代Swift框架

### Cell

*Cell*

* [folding-cell](https://github.com/Ramotion/folding-cell) - FoldingCell是一种不断扩展的内容单元，灵感来自折叠纸质材料
* [expanding-collection](https://github.com/Ramotion/expanding-collection) - ExpandingCollection是一个卡片查看/弹出控制器

### 头部
*Header*

* [CSStickyHeaderFlowLayout](https://github.com/CSStickyHeaderFlowLayout/CSStickyHeaderFlowLayout) - UICollectionView替换UITableView。甚至更像Parallax Header，Sticky Section Header
* [GSKStretchyHeaderView](https://github.com/gskbyte/GSKStretchyHeaderView) - UITableView和UICollectionView的可配置且易于使用的弹性标题视图

### 占位符
*Placeholder*

* [DZNEmptyDataSet](https://github.com/dzenbot/DZNEmptyDataSet) - 一个插入式UITableView / UICollectionView超类类别，用于在视图没有要显示的内容时显示空数据集。

### CollectionViewLayout
*CollectionViewLayout*

* [CHTCollectionViewWaterfallLayout](https://github.com/chiahsien/CHTCollectionViewWaterfallLayout) - UICollectionView的瀑布（即类似Pinterest）布局
* [BouncyLayout](https://github.com/roberthein/BouncyLayout) - BouncyLayout是一个集合视图布局，使您的单元格反弹

### TextField
*TextField*

* [JVFloatLabeledTextField](https://github.com/jverdi/JVFloatLabeledTextField) -  带有浮动标签的UITextField子类
* [TextFieldEffects](https://github.com/raulriera/TextFieldEffects) - 使用Swift构建的受Codrops启发的自定义UITextFields效果
* [PYSearch](https://github.com/ko1o/PYSearch) -  一个优雅的搜索控制器，取代了iOS（iPhone和iPad）的UISearchController

### UIPageControl
*UIPageControl*

* [CHIPageControl](https://github.com/ChiliLabs/CHIPageControl) - 一组很酷的动画页面控件来取代枯燥的UIPageControl

### WebView
*WebView*

* [SVWebViewController](https://github.com/TransitApp/SVWebViewController) - 适用于iOS应用的嵌入式内联浏览器

## 扩展
*Utility*

* [libextobjc](https://github.com/jspahrsummers/libextobjc) - 一个扩展Objective-C编程语言的Cocoa库
* [BlocksKit](https://github.com/BlocksKit/BlocksKit) - Objective-C块实用程序
* [SwifterSwift](https://github.com/SwifterSwift/SwifterSwift) - 一个包含400多个原生Swift 4扩展的便捷集合，可提高您的工作效率
* [MMWormhole](https://github.com/mutualmobile/MMWormhole) -  iOS应用和扩展之间的消息传递

## 引导页
*Intro*

* [Onboard](https://github.com/mamaral/Onboard) - 只需几行代码即可轻松创建美观且引人入胜的引导体验
* [EAIntroView](https://github.com/ealeksandrov/EAIntroView) - 高度可定制的引入视图插入式解决方案
* [JazzHands](https://github.com/IFTTT/JazzHands) - Jazz Hands是一个简单的基于关键帧的UIKit动画框架。可以通过手势，滚动视图，KVO或ReactiveCocoa来控制动画。
* [RazzleDazzle](https://github.com/IFTTT/RazzleDazzle) - 一个简单的基于关键帧的iOS动画框架，用Swift编写。适合滚动应用程序介绍
* [Instructions](https://github.com/ephread/Instructions) - 轻松将可自定义的教练标记添加到iOS项目中

## WebSocket
*WebSocket*

* [SocketRocket](https://github.com/facebook/SocketRocket) - 符合Objective-C的WebSocket客户端库
* [Starscream](https://github.com/daltoniam/Starscream) - 适用于iOS和macOS的swift中的Websockets

## 包管理
*Package Manager*

* [CocoaPods](https://github.com/CocoaPods/CocoaPods) - CocoaPods是Objective-C项目的依赖管理器。它有数千个库，可以帮助您优雅地扩展项目
* [Carthage](https://github.com/Carthage/Carthage) - Cocoa的简单，分散的依赖管理器
* [swift-package-manager](https://github.com/apple/swift-package-manager) - Swift编程语言的包管理器

## 工具
*Tools*

* [R.swift](https://github.com/mac-cain13/R.swift) - 在Swift项目中获取强大类型，自动完成的资源（如图像，单元格和segue）的工具
* [SwiftGen](https://github.com/SwiftGen/SwiftGen) - 用于生成Swift代码的Swift工具集合
* [jazzy](https://github.com/realm/jazzy) -  Swift和Objective-C的Soulful文档
* [appledoc](https://github.com/tomaz/appledoc) - ObjectiveC代码Apple风格的文档集生成器
* [infer](https://github.com/facebook/infer) - 用于Java，C和Objective-C的静态分析器
* [Sourcery](https://github.com/krzysztofzablocki/Sourcery) - 一个为Swift带来元编程的工具，允许您编写生成Swift代码的代码
* [Tweaks](https://github.com/facebook/Tweaks) - 在开发过程中微调和调整iOS应用程序参数的简便方法
* [Lona](https://github.com/airbnb/Lona) - 用于定义设计系统并使用它们生成跨平台UI代码，草图文件，图像和其他工件的工具

## 插件
*Injection*

* [injectionforxcode](https://github.com/johnno1962/injectionforxcode)

## 发布
* Distribution*

* [fastlane](https://github.com/fastlane/fastlane) - 将所有iOS部署工具连接到一个简化的工作流程中

## 应用商店
*App Store*

* [Harpy](https://github.com/ArtSabintsev/Harpy) - 当您的iOS应用程序的新版本可用时通知用户，并使用App Store链接提示他们
* [iRate](https://github.com/nicklockwood/iRate) - 一个方便的类，提示您的iPhone或Mac App Store应用程序的用户在使用它一段时间后对您的应用程序进行评级
* [appirater](https://github.com/arashpayan/appirater) - 一个实用程序，可以提醒您的iPhone应用程序的用户查看该应用程序
* [Siren](https://github.com/ArtSabintsev/Siren) -  当您的应用程序的新版本可用时通知用户并提示他们升级



---
## 后记

此文档会不断更新
