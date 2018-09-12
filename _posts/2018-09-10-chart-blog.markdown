---
layout:     post
title:      "iOS图表"
subtitle:   " \"Exmple for Charts\""
date:       2018-09-10 12:00:00
author:     "Wangpt"
header-img: "img/post-bg-2015.jpg"
catalog: true
tags:
    - iOS
    - Charts

---

> “Charts的使用 ”


简介

*iOS功能强大的图表/图表框架*

---

##Charts框架的使用

###### 绘制折线图
*最终效果*
![折线图](https://raw.githubusercontent.com/wangpt/TJCharts/master/Sources/1.png)
*对象初始化*

```objc
    //初始化对象
    CGFloat chartW =[self getScreenSize].width - 20;
    CGFloat chartH =[self getScreenSize].height - 300;
    self.chartView = ({
        LineChartView *chartView = [[LineChartView alloc] init];
        [self.view addSubview:chartView];
        [chartView mas_makeConstraints:^(MASConstraintMaker *make) {
            make.size.mas_equalTo(CGSizeMake(chartW, chartH));
            make.center.mas_equalTo(self.view);
        }];
        chartView;
    });
    
```







### 柱状图
![柱状图](https://raw.githubusercontent.com/wangpt/TJCharts/master/Sources/2.png)

### 饼状图

![饼状图](https://raw.githubusercontent.com/wangpt/TJCharts/master/Sources/3.png)

### 雷达图

![雷达图](https://raw.githubusercontent.com/wangpt/TJCharts/master/Sources/4.png)

Demo下载

[TJCache](https://github.com/wangpt/TJCache)


后记


此文档会不断更新
