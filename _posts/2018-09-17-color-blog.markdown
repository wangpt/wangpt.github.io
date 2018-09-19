---
layout:     post
title:      "iOS主题颜色"
subtitle:   " \"Exmple for DKNightVersion\""
date:       2018-09-17 12:00:00
author:     "Wangpt"
header-img: "img/post-bg-2015.jpg"
catalog: true
tags:
    - iOS
    - Theme
    - DKNightVersion

---

> “DKNightVersion的使用说明 ”


简介

*管理色彩，整合夜晚/多个主题*

---
### 1.DKNightVersion的使用

###### 基础用法
*修改DKColorTable.txt文件，创建颜色表文件*

```objc
NORMAL   NIGHT    RED      YELLOW
#ffffff  #343434  #FF0000  #ffff00  TJBG
#aaaaaa  #313131  #aaaaaa  #ffff00  SEP

```
*配置颜色选择器DKColorPickerWithKey*

```objc
    self.view.dk_backgroundColorPicker = DKColorPickerWithKey(TJBG);

```
*修改对应主题颜色*

```
    switch (button.tag) {
        case 0:
            [self.dk_manager dawnComing];
            break;
        case 1:
            [self.dk_manager nightFalling];
            break;
        case 2:
            self.dk_manager.themeVersion = @"RED";
            break;
        default:
            self.dk_manager.themeVersion = @"YELLOW";
            break;
    }
```
###### 高级用法
*设置文字颜色*

```objc
    titleLabel.dk_textColorPicker = DKColorPickerWithRGB(0x343434, 0xffffff, 0xffffff,0x343434);

```
*设置图片主题*

```objc
    imageView.dk_imagePicker = DKImagePickerWithNames(@"night", @"normal", @"night1",@"normal1");

```
*设置图片透明度*

```objc
    imageView.dk_alphaPicker = DKAlphaPickerWithAlphas(1.f, 0.8f, 0.1f,1.f);

```

### 2.TJTheme的实现和使用
###### 实现过程
*添加主题管理类*

```objc
+ (instancetype)sharedInstance {
    static dispatch_once_t onceToken;
    static TJThemeManager *instance = nil;
    dispatch_once(&onceToken,^{
        instance = [[TJThemeManager alloc] init];
    });
    return instance;
}

- (void)setCurrentTheme:(NSObject<TJThemeProtocol> *)currentTheme{
    if (_currentTheme != currentTheme && currentTheme) {
        NSObject<TJThemeProtocol> *themeBeforeChanged = _currentTheme;
        _currentTheme = currentTheme;
        [[NSNotificationCenter defaultCenter] postNotificationName:TJThemeChangedNotification object:self userInfo:@{TJThemeBeforeChangedData: themeBeforeChanged ?: [NSNull null], TJThemeAfterChangedData: _currentTheme ?: [NSNull null]}];
    }
}
```
*定义主题颜色协议*

```objc
@protocol TJThemeProtocol <NSObject>
@required
- (UIColor *)themeBgColor;
- (UIColor *)themeTextColor;
- (NSString *)themeImage;
@end
```

###### 使用方法
*添加主题模型，并需实现TJThemeProtocol协议*

```objc
#import "TJThemeProtocol.h"
@interface ThemeRedTemplate : NSObject<TJThemeProtocol>

@end

@implementation ThemeRedTemplate
- (UIColor *)themeTextColor{
    return [UIColor redColor];
}
- (UIColor *)themeBgColor{
    return [UIColor redColor];
}

- (NSString *)themeImage{
    return @"normal";
}
@end

```
*设置自定义主题*

```objc
	[TJThemeManager sharedInstance].currentTheme = [ThemeRedTemplate new];

```

*使用主题修改颜色*

```objc
    
    self.view.backgroundColor = [TJThemeManager sharedInstance].currentTheme.themeBgColor;

```
*监听改变状态*

```objc

	[[NSNotificationCenter defaultCenter] addObserver:self selector:@selector(handleThemeChangedNotification:) name:TJThemeChangedNotification object:nil];

```





## Demo下载


[TJTheme](https://github.com/wangpt/TJTheme)
