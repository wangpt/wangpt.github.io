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

## 通过Charts框架绘制

###### 绘制折线图
*对象初始化*

```objc
    _chartView = ({
        //1.初始化对象
        
        LineChartView *lineChart = [[LineChartView alloc] init];
        [self.view addSubview:lineChart];
        [lineChart mas_makeConstraints:^(MASConstraintMaker *make) {
            make.size.mas_equalTo(CGSizeMake(width, height));
            make.center.mas_equalTo(self.view);
        }];
        //2.设置交互样式
        
        lineChart.noDataText = @"暂无数据";
        lineChart.rightAxis.enabled = NO;
        lineChart.drawGridBackgroundEnabled = NO;
        lineChart.chartDescription.enabled = NO;
        lineChart.chartDescription.text = @"折现图";
        lineChart.scaleXEnabled = NO;
        lineChart.scaleYEnabled = NO;
        lineChart.pinchZoomEnabled = NO;
        lineChart.doubleTapToZoomEnabled = NO;
        lineChart.dragEnabled = YES;
        lineChart.dragDecelerationEnabled = YES;
       
        //3.设置x轴的样式
        
        ChartXAxis *xAxis = lineChart.xAxis;
        xAxis.drawGridLinesEnabled = NO;
        xAxis.axisLineWidth = 1.0/[UIScreen mainScreen].scale;
        xAxis.labelPosition = XAxisLabelPositionBottom;
        xAxis.labelTextColor = [UIColor blueColor];
        xAxis.granularity = 1.0; 
        xAxis.axisLineColor = [UIColor blueColor];
        xAxis.valueFormatter = self;
        xAxis.spaceMin = 0.5;
        xAxis.spaceMax = 0.5;
        
        //4.设置y轴的样式
        
        ChartYAxis *leftAxis = lineChart.leftAxis;
        leftAxis.drawGridLinesEnabled = NO;
        leftAxis.axisLineWidth = 1.0/[UIScreen mainScreen].scale;
        leftAxis.labelCount = 5;
        leftAxis.forceLabelsEnabled = NO;
        leftAxis.axisMinimum = 0.0;
        leftAxis.drawZeroLineEnabled = NO;
        leftAxis.spaceTop = 0.05;
        leftAxis.drawLimitLinesBehindDataEnabled = YES;
        leftAxis.labelPosition = YAxisLabelPositionOutsideChart;
        leftAxis.labelTextColor =  [UIColor blueColor];
        leftAxis.axisLineColor = [UIColor blueColor];
        leftAxis.labelFont = [UIFont systemFontOfSize:10.0f];
       
        //5.图例样式
        
        ChartLegend *l = lineChart.legend;
        l.enabled = YES;
        l.horizontalAlignment = ChartLegendHorizontalAlignmentCenter;
        l.verticalAlignment = ChartLegendVerticalAlignmentTop;
        l.orientation = ChartLegendOrientationHorizontal;
        l.drawInside = NO;
        l.xEntrySpace = 7.0;
        l.yEntrySpace = 0.0;
        l.yOffset = 0.0;
        l.formToTextSpace = 5;
        l.font = [UIFont systemFontOfSize:10];
        l.form = ChartLegendFormCircle;
        l.formSize = 12;
        l.textColor = [UIColor grayColor];
        lineChart;
    });

```

*添加数据*

```objc

- (void)updateChartData
{
    double range = 100;
    NSInteger lineCount = 2;
    NSMutableArray *allLine_vals = @[].mutableCopy;
    for (int count = 0; count<lineCount; count++) {
        NSMutableArray *yVals = [[NSMutableArray alloc] init];
        for (int i = 0; i < _months.count; i++)
        {
            double val = arc4random_uniform(range) + 10;
            [yVals addObject:[[ChartDataEntry alloc] initWithX:i y:val]];
        }
        [allLine_vals addObject:yVals];
    }
    
    if (_chartView.data.dataSetCount > 0)
    {
        [allLine_vals enumerateObjectsUsingBlock:^(id  _Nonnull obj, NSUInteger idx, BOOL * _Nonnull stop) {
            LineChartDataSet *set = (LineChartDataSet *)_chartView.data.dataSets[idx];
            set.values = obj;
        }];
        [_chartView.data notifyDataChanged];
        [_chartView notifyDataSetChanged];
    
    }else{
        NSMutableArray *dataSets = [[NSMutableArray alloc] init];
        [allLine_vals enumerateObjectsUsingBlock:^(id  _Nonnull obj, NSUInteger idx, BOOL * _Nonnull stop) {
            NSString *label = [NSString stringWithFormat:@"第%lu条",(unsigned long)idx+1];
            LineChartDataSet *set = [[LineChartDataSet alloc] initWithValues:allLine_vals[idx] label:label];
            [set setColor:TJRandomColor];
            set.lineWidth = 1.0;
            set.drawCircleHoleEnabled =NO;
            [set setCircleColor:UIColor.redColor];
            set.circleRadius = 3.0;
            set.drawCirclesEnabled = NO;
            set.mode = LineChartModeCubicBezier;
            [dataSets addObject:set];
        }];
        LineChartData *data = [[LineChartData alloc] initWithDataSets:dataSets];
        [data setValueTextColor:UIColor.blackColor];
        [data setValueFont:[UIFont systemFontOfSize:9.f]];
        _chartView.data = data;
    }
    [_chartView animateWithXAxisDuration:0.5];
}

```

###### 绘制柱状图
*对象初始化*

```objc

    _chartView = ({
    	 //1.初始化对象
    	 
        BarChartView *barChartView = [[BarChartView alloc] initWithFrame:CGRectMake(0, 0, 320, 320)];
        [self.view addSubview:barChartView];
        [barChartView mas_makeConstraints:^(MASConstraintMaker *make) {
            make.size.mas_equalTo(CGSizeMake(chartW, chartH));
            make.center.mas_equalTo(self.view);
        }];
        //2.设置交互样式
        
        barChartView.extraBottomOffset = 20;
        barChartView.fitBars = YES;
        barChartView.noDataText = @"暂无数据";
        barChartView.drawValueAboveBarEnabled = YES;
        barChartView.drawBarShadowEnabled = NO;
        barChartView.rightAxis.enabled = NO;
        barChartView.chartDescription.enabled = NO;
        barChartView.drawGridBackgroundEnabled = NO;
        barChartView.scaleYEnabled = NO;
        barChartView.doubleTapToZoomEnabled = NO;
        barChartView.dragEnabled = NO;
        barChartView.dragDecelerationEnabled = YES;
        [barChartView setScaleEnabled:YES];
        barChartView.pinchZoomEnabled = NO;
        barChartView.maxVisibleCount = 60;
        //3.X轴样式
        
        ChartXAxis *xAxis = barChartView.xAxis;
        xAxis.granularity = 1.0; 
        xAxis.drawGridLinesEnabled = NO;
        xAxis.labelPosition = XAxisLabelPositionBottom;
        xAxis.valueFormatter = self;
        xAxis.axisLineColor = [UIColor blueColor];
        xAxis.axisLineWidth = 0.5;
        xAxis.labelTextColor = [UIColor blueColor];
        //4.左边Y轴样式
        
        ChartYAxis *leftAxis = barChartView.leftAxis;
        leftAxis.drawGridLinesEnabled = NO;
        leftAxis.forceLabelsEnabled = NO;
        leftAxis.labelCount = 8;
        leftAxis.labelFont = [UIFont systemFontOfSize:10.f];
        leftAxis.labelTextColor = [UIColor blueColor];
        leftAxis.spaceTop = 0.15;
        leftAxis.labelPosition = YAxisLabelPositionOutsideChart;
        leftAxis.axisMinimum = 0;
        leftAxis.inverted = NO;
        leftAxis.axisLineWidth = 0.5;
        leftAxis.axisLineColor = [UIColor blueColor];
        //5.图例样式
        
        ChartLegend *l = barChartView.legend;
        l.enabled = YES;//不显示图例说明
        barChartView;
    });


```
*添加数据*

```objc
#pragma mark - 单组数据

- (void)updateChartData
{

    double range = 50;
    NSMutableArray *yVals = [[NSMutableArray alloc] init];
    for (int i = 0; i < 5; i++)
    {
        double mult = (range + 1);
        double val = (double) (arc4random_uniform(mult));
        [yVals addObject:[[BarChartDataEntry alloc] initWithX:i y:val]];
    }
    BarChartDataSet *set1 = nil;
    if (_chartView.data.dataSetCount > 0)
    {
        set1 = (BarChartDataSet *)_chartView.data.dataSets[0];
        set1.values = yVals;
        [_chartView.data notifyDataChanged];
        [_chartView notifyDataSetChanged];
    }
    else
    {
        set1 = [[BarChartDataSet alloc] initWithValues:yVals label:@"The year 2017"];
        [set1 setColors:ChartColorTemplates.material];
        
        NSMutableArray *dataSets = [[NSMutableArray alloc] init];
        [dataSets addObject:set1];
        
        BarChartData *data = [[BarChartData alloc] initWithDataSets:dataSets];
        [data setValueFont:[UIFont fontWithName:@"HelveticaNeue-Light" size:10.f]];
        
        data.barWidth = 0.9f;
        _chartView.data = data;
    }
    [_chartView animateWithYAxisDuration:1.5];

}

#pragma mark - 多组数据

- (void)updateMultipleChartData{
    double range = 100;
    NSInteger lineCount = 2;
    NSInteger groupCount = 5;
    int startX = 0;
    float groupSpace = 0.2f;
    float barSpace = 0.03f;
    float barWidth = ( 1- groupSpace)/lineCount -barSpace;
    
    NSMutableArray *all_vals = @[].mutableCopy;
    for (int count = 0; count < lineCount; count++) {
        NSMutableArray *yVals = [[NSMutableArray alloc] init];
        for (int i = 0; i < groupCount; i++)
        {
            double val = arc4random_uniform(range) + 10;
            [yVals addObject:[[BarChartDataEntry alloc] initWithX:i y:val]];
        }
        [all_vals addObject:yVals];
    }
    
    if (_chartView.data.dataSetCount > 0)
    {
        [all_vals enumerateObjectsUsingBlock:^(id  _Nonnull obj, NSUInteger idx, BOOL * _Nonnull stop) {
            BarChartDataSet *set = (BarChartDataSet *)_chartView.data.dataSets[idx];
            set.values = obj;
        }];
        BarChartData *data = _chartView.barData;
        _chartView.xAxis.axisMinimum = startX;
        _chartView.xAxis.axisMaximum = [data groupWidthWithGroupSpace:groupSpace barSpace: barSpace] * groupCount + startX;
        [data groupBarsFromX: startX groupSpace: groupSpace barSpace: barSpace];
        [_chartView.data notifyDataChanged];
        [_chartView notifyDataSetChanged];
    }
    else
    {
        NSMutableArray *dataSets = [[NSMutableArray alloc] init];
        [all_vals enumerateObjectsUsingBlock:^(id  _Nonnull obj, NSUInteger idx, BOOL * _Nonnull stop) {
            NSString *label = [NSString stringWithFormat:@"第%lu条",(unsigned long)idx+1];
            BarChartDataSet *set = [[BarChartDataSet alloc] initWithValues:all_vals[idx] label:label];
            [set setColor:TJRandomColor];
            
            [dataSets addObject:set];
        }];

        BarChartData *data = [[BarChartData alloc] initWithDataSets:dataSets];
        [data setValueFont:[UIFont fontWithName:@"HelveticaNeue-Light" size:10.f]];
        data.barWidth = barWidth;
        _chartView.xAxis.axisMinimum = startX;
        _chartView.xAxis.axisMaximum = startX + [data groupWidthWithGroupSpace:groupSpace barSpace: barSpace] * groupCount;
        [data groupBarsFromX: startX groupSpace: groupSpace barSpace: barSpace];
        _chartView.data = data;
    }
    [_chartView animateWithYAxisDuration:1.5];

}

```

###### 绘制饼状图
*对象初始化*

```objc
       _chartView = ({
        //1.初始化对象
        
        PieChartView *pieChart = [PieChartView new];
        [self.view addSubview:pieChart];
        [pieChart mas_makeConstraints:^(MASConstraintMaker *make) {
            make.size.mas_equalTo(CGSizeMake(chartW, chartH));
            make.center.mas_equalTo(self.view);
        }];
        //2.设置交互样式
        
        [pieChart setExtraOffsetsWithLeft:5.f top:10.f right:5.f bottom:5.f];
        pieChart.usePercentValuesEnabled = YES;
        pieChart.dragDecelerationEnabled = YES;
        pieChart.chartDescription.enabled = NO;
        pieChart.drawHoleEnabled = YES;
        pieChart.rotationAngle = 0.0;
        pieChart.rotationEnabled = YES;
        pieChart.highlightPerTapEnabled = NO;
        pieChart.holeRadiusPercent = 0.38;
        pieChart.holeColor = [UIColor clearColor];
        pieChart.transparentCircleRadiusPercent = 0.41;
        if (pieChart.isDrawHoleEnabled == YES) {
            pieChart.drawCenterTextEnabled = YES;
            pieChart.centerText = @"";
            NSMutableAttributedString *centerText = [[NSMutableAttributedString alloc] initWithString:@"饼状图"];
            [centerText setAttributes:@{NSFontAttributeName: [UIFont boldSystemFontOfSize:16],
                                        NSForegroundColorAttributeName: [UIColor orangeColor]}
                                range:NSMakeRange(0, centerText.length)];
            pieChart.centerAttributedText = centerText;
        }
        //3.图例样式
        
        ChartLegend *l = pieChart.legend;
        l.enabled = YES;
        l.form = ChartLegendFormCircle;
        l.formToTextSpace = 5;
        l.font = [UIFont systemFontOfSize:10];
        l.textColor = [UIColor grayColor];
        pieChart;
    });

```
*添加数据*

```objc
- (void)updateChartData
{
    int count = 5;
    double range = 100;
    NSMutableArray *entries = [[NSMutableArray alloc] init];
    NSArray *parties;
    parties = @[
                @"丽江", @"贵阳", @"北京", @"上海", @"广州", @"深圳",
                @"香港", @"澳门", @"天津", @"重庆", @"成都", @"杭州",
                @"武汉", @"南京", @"西安", @"长沙", @"青岛", @"沈阳",
                @"大连", @"厦门", @"苏州", @"宁波", @"无锡"
                ];
    
    for (int i = 0; i < count; i++)
    {
        
        double randomVal = arc4random_uniform(range) + range / 2;
        [entries addObject:[[PieChartDataEntry alloc] initWithValue:randomVal label:parties[i % parties.count]]];
    }
    
    PieChartDataSet *dataSet = [[PieChartDataSet alloc] initWithValues:entries label:@""];
    dataSet.sliceSpace = 2.0;
    dataSet.drawValuesEnabled = YES;
    NSMutableArray *colors = [[NSMutableArray alloc] init];
    [colors addObjectsFromArray:ChartColorTemplates.vordiplom];
    [colors addObjectsFromArray:ChartColorTemplates.joyful];
    [colors addObjectsFromArray:ChartColorTemplates.colorful];
    [colors addObjectsFromArray:ChartColorTemplates.liberty];
    [colors addObjectsFromArray:ChartColorTemplates.pastel];
    [colors addObject:[UIColor colorWithRed:51/255.f green:181/255.f blue:229/255.f alpha:1.f]];
    dataSet.colors = colors;
    dataSet.valueLinePart1OffsetPercentage = 0.8;
    dataSet.valueLinePart1Length = 0.2;
    dataSet.valueLinePart2Length = 0.4;
    dataSet.valueLineWidth = 1;
    dataSet.valueLineColor = [UIColor brownColor];
    dataSet.yValuePosition = PieChartValuePositionOutsideSlice;
    PieChartData *data = [[PieChartData alloc] initWithDataSet:dataSet];
    NSNumberFormatter *pFormatter = [[NSNumberFormatter alloc] init];
    pFormatter.numberStyle = NSNumberFormatterPercentStyle;
    pFormatter.maximumFractionDigits = 1;
    pFormatter.multiplier = @1.f;
    pFormatter.percentSymbol = @" %";
    [data setValueFormatter:[[ChartDefaultValueFormatter alloc] initWithFormatter:pFormatter]];
    [data setValueFont:[UIFont fontWithName:@"HelveticaNeue-Light" size:11.f]];
    [data setValueTextColor:UIColor.blackColor];
    _chartView.data = data;
    [_chartView highlightValues:nil];
    [_chartView animateWithXAxisDuration:1.4 easingOption:ChartEasingOptionEaseOutBack];

}

```


###### 绘制雷达图
*对象初始化*

```objc
 _chartView = ({
        //1、对象初始化
        
        RadarChartView *radarChartView = [[RadarChartView alloc] init];
        [self.view addSubview:radarChartView];
        [radarChartView mas_makeConstraints:^(MASConstraintMaker *make) {
            make.size.mas_equalTo(CGSizeMake(chartW, chartH));
            make.center.mas_equalTo(self.view);
        }];
        //2.设置交互样式
        
        radarChartView.rotationEnabled = YES;
        radarChartView.highlightPerTapEnabled = NO;
        radarChartView.chartDescription.enabled = NO;
        radarChartView.webLineWidth = 1.0;
        radarChartView.innerWebLineWidth = 1.0;
        radarChartView.webColor = [self colorWithHexString:@"#c2ccd0"];
        radarChartView.innerWebColor =  [self colorWithHexString:@"#c2ccd0"];
        radarChartView.webAlpha = 1.0;
        //3.X轴label样式
        
        ChartXAxis *xAxis = radarChartView.xAxis;
        xAxis.labelFont = [UIFont systemFontOfSize:15];
        xAxis.xOffset = 0.0;
        xAxis.yOffset = 0.0;
        xAxis.valueFormatter = self;
        xAxis.labelTextColor = [self colorWithHexString:@"#057748"];
        //4.Y轴label样式
        
        ChartYAxis *yAxis = radarChartView.yAxis;
        yAxis.labelFont = [UIFont systemFontOfSize:9];
        yAxis.labelTextColor = [UIColor lightGrayColor];
        yAxis.labelCount = 5;
        yAxis.axisMinimum = 0.0;
        yAxis.axisMaximum = 100.0;
        yAxis.drawLabelsEnabled = NO;
        //5.设置标注
        
        radarChartView.legend.enabled = NO;
        //6.设置marker
        
        RadarMarkerView *marker = (RadarMarkerView *)[RadarMarkerView viewFromXibIn:[NSBundle mainBundle]];
        marker.chartView = radarChartView;
        radarChartView.marker = marker;
        radarChartView;
    });
```
*添加数据*

```objc
- (void)updateChartData
{
    _chartView.yAxis.axisMinimum = 0.0;
    _chartView.yAxis.axisMaximum = 100.0;
    int lineCount = 1;
    double mult = 80;
    double min = 20;
    int cnt = 5;
    NSMutableArray *allLine_vals = @[].mutableCopy;
    for (int count = 0; count<lineCount; count++) {
        NSMutableArray *entries = [[NSMutableArray alloc] init];
        for (int i = 0; i < cnt; i++)
        {
            double randomVal =(arc4random_uniform(mult) + min); 
            [entries addObject:[[RadarChartDataEntry alloc] initWithValue:randomVal]];
        }
        [allLine_vals addObject:entries];
    }
    
    NSMutableArray *dataSets = [[NSMutableArray alloc] init];
    [allLine_vals enumerateObjectsUsingBlock:^(id  _Nonnull obj, NSUInteger idx, BOOL * _Nonnull stop) {
        RadarChartDataSet *set = [[RadarChartDataSet alloc] initWithValues:obj label:[NSString stringWithFormat:@"第%lu条",(unsigned long)idx+1]];
        UIColor *color = TJRandomColor;
        [set setColor:color];
        set.fillColor = color;
        set.drawFilledEnabled = YES;
        set.fillAlpha = 0.25;
        set.lineWidth = 0.5;
        set.drawHighlightCircleEnabled = YES;
        [set setDrawHighlightIndicators:NO];
        set.valueFont = [UIFont systemFontOfSize:9];
        set.valueTextColor = [UIColor grayColor];
        [dataSets addObject:set];
    }];
    
    RadarChartData *data = [[RadarChartData alloc] initWithDataSets:dataSets];
    [data setValueFont:[UIFont fontWithName:@"HelveticaNeue-Light" size:8.f]];
    [data setDrawValues:YES];
    data.valueTextColor = UIColor.blackColor;
    _chartView.data = data;
    [_chartView animateWithXAxisDuration:1.4 yAxisDuration:1.4 easingOption:ChartEasingOptionEaseOutBack];
    
}
```
## Demo下载

[TJCache](https://github.com/wangpt/TJCache)


## 后记


此文档会不断更新
