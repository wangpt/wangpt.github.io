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

### DKNightVersion的使用

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
*直接设置对应主题*

```objc
    titleLabel.dk_textColorPicker = DKColorPickerWithRGB(0x343434, 0xffffff, 0xffffff,0x343434);

```

## Demo下载


[TJTheme](https://github.com/wangpt/TJTheme)
