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
*最终效果*
![折线图](https://raw.githubusercontent.com/wangpt/TJCharts/master/Sources/1.png)
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
        
        lineChart.noDataText = @"暂无数据";//没有数据时的文字提示
        
        lineChart.rightAxis.enabled = NO;//不绘制右边轴
        
        lineChart.drawGridBackgroundEnabled = NO;//是否绘制网格背景的标志
        
        lineChart.chartDescription.enabled = NO;//是否显示图标描述
        
        lineChart.chartDescription.text = @"折现图";
        
        lineChart.scaleXEnabled = NO;//取消X轴缩放
        
        lineChart.scaleYEnabled = NO;//取消Y轴缩放
        
        lineChart.pinchZoomEnabled = NO;//XY轴是否同时缩放
        
        lineChart.doubleTapToZoomEnabled = NO;//取消双击缩放
        
        lineChart.dragEnabled = YES;//启用拖拽图表
        
        lineChart.dragDecelerationEnabled = YES;//拖拽饼状图后是否有惯性效果
       
        //3.设置x轴的样式
        
        ChartXAxis *xAxis = lineChart.xAxis;
        
        xAxis.drawGridLinesEnabled = NO;//不绘制网格线为NO 绘制为YES
        
        xAxis.axisLineWidth = 1.0/[UIScreen mainScreen].scale;//设置X轴线宽
        
        xAxis.labelPosition = XAxisLabelPositionBottom;//X轴的显示位置，默认是显示在上面的
        
        xAxis.labelTextColor = [UIColor blueColor];//label文字颜色
        
        xAxis.axisLineColor = [UIColor blueColor];//x轴线的颜色
        
        xAxis.valueFormatter = self;//用于设置x轴文字显示
        
        xAxis.spaceMin = 0.5;//设置坐标轴额外的最小空间
        
        xAxis.spaceMax = 0.5;//设置坐标轴额外的最大空间
        
        //4.设置y轴的样式
        
        ChartYAxis *leftAxis = lineChart.leftAxis;//获取左边Y轴
        
        leftAxis.drawGridLinesEnabled = NO;//不绘制网格线
        
        leftAxis.axisLineWidth = 1.0/[UIScreen mainScreen].scale;//Y轴线宽
        
        leftAxis.labelCount = 5;//Y轴label数量，数值不一定，如果forceLabelsEnabled等于YES, 则强制绘制制定数量的label, 但是可能不平均
        
        leftAxis.forceLabelsEnabled = NO;//不强制绘制指定数量的label
        
        //    leftAxis.axisMaximum = 150.0;//设置Y轴的最大值
        
        leftAxis.axisMinimum = 0.0;//设置Y轴的最小值
        
        leftAxis.drawZeroLineEnabled = NO;//从0开始绘画
        
        leftAxis.spaceTop = 0.05;//最大值到顶部的范围比
        
        leftAxis.drawLimitLinesBehindDataEnabled = YES;//设置限制线绘制在柱形图的后面
        
        leftAxis.labelPosition = YAxisLabelPositionOutsideChart;//label位置
        
        leftAxis.labelTextColor =  [UIColor blueColor];//label文字颜色
        
        leftAxis.axisLineColor = [UIColor blueColor];//轴线的颜色
        
        leftAxis.labelFont = [UIFont systemFontOfSize:10.0f];//文字字体
       
        //5.图例样式
        
        ChartLegend *l = lineChart.legend;//
       
        l.enabled = YES;//显示图例说明
        
        l.horizontalAlignment = ChartLegendHorizontalAlignmentCenter;//水平方向
        
        l.verticalAlignment = ChartLegendVerticalAlignmentTop;//垂直方向
        
        l.orientation = ChartLegendOrientationHorizontal;//方向
        
        l.drawInside = NO;
        l.xEntrySpace = 7.0;
        l.yEntrySpace = 0.0;
        l.yOffset = 0.0;
        l.formToTextSpace = 5;//文本间隔
        
        l.font = [UIFont systemFontOfSize:10];//字体大小
        
        l.form = ChartLegendFormCircle;//图示样式: 方形、线条、圆形
        
        l.formSize = 12;//图示大小
        
        l.textColor = [UIColor grayColor];//字体颜色
        
        lineChart;
    });

```

*添加数据*

```objc

- (void)updateChartData
{
    double range = 100;//最大随机数
    
    NSInteger lineCount = 2;//条数
    
    //添加随机数据
    
    NSMutableArray *all_vals = @[].mutableCopy;
    for (int count = 0; count<lineCount; count++) {
        NSMutableArray *yVals = [[NSMutableArray alloc] init];
        for (int i = 0; i < _months.count; i++)
        {
            double val = arc4random_uniform(range) + 10;
            [yVals addObject:[[ChartDataEntry alloc] initWithX:i y:val]];
        }
        [all_vals addObject:yVals];
    }
    
    if (_chartView.data.dataSetCount > 0)
    {//更新数据
        
        [all_vals enumerateObjectsUsingBlock:^(id  _Nonnull obj, NSUInteger idx, BOOL * _Nonnull stop) {
            LineChartDataSet *set = (LineChartDataSet *)_chartView.data.dataSets[idx];
            set.values = obj;
        }];
        [_chartView.data notifyDataChanged];
        [_chartView notifyDataSetChanged];
    
    }else{
        NSMutableArray *dataSets = [[NSMutableArray alloc] init];
        [all_vals enumerateObjectsUsingBlock:^(id  _Nonnull obj, NSUInteger idx, BOOL * _Nonnull stop) {
            NSString *label = [NSString stringWithFormat:@"第%lu条",(unsigned long)idx+1];
            LineChartDataSet *set = [[LineChartDataSet alloc] initWithValues:all_vals[idx] label:label];
            [set setColor:TJRandomColor];
            set.lineWidth = 1.0;//线条宽度
            
            set.drawCircleHoleEnabled =NO;
            [set setCircleColor:UIColor.redColor];//拐点颜色
            
            set.circleRadius = 3.0;//拐点半径
            
            set.drawCirclesEnabled = NO;//是否绘制拐点
            
            set.drawCubicEnabled = YES;
            
            //填充色
            
//            NSArray *gradientColors = @[(id)[ChartColorTemplates colorFromString:@"#FFFFFFFF"].CGColor,
            
//                                        (id)[ChartColorTemplates colorFromString:@"#FF007FFF"].CGColor];
            
//            CGGradientRef gradient = CGGradientCreateWithColors(nil, (CFArrayRef)gradientColors, nil);
            
//            set.fillAlpha = 0.3f;//透明度
            
//            set.fill = [ChartFill fillWithLinearGradient:gradient angle:90.f];//赋值填充颜色对象
            
//            set.drawFilledEnabled = YES;//是否填充颜色
            
//            CGGradientRelease(gradient);
            
            [dataSets addObject:set];
        }];
        LineChartData *data = [[LineChartData alloc] initWithDataSets:dataSets];
        [data setValueTextColor:UIColor.blackColor];//文字颜色
        
        [data setValueFont:[UIFont systemFontOfSize:9.f]];//文字大小
        
        _chartView.data = data;
    }
    
    [_chartView animateWithXAxisDuration:0.5];
}

```
*X轴文字代理*

```
- (NSString *)stringForValue:(double)value
                        axis:(ChartAxisBase *)axis
{
    NSInteger index = value;
    return _months[index];
}

```

###### 绘制柱状图
![柱状图](https://raw.githubusercontent.com/wangpt/TJCharts/master/Sources/2.png)


###### 绘制饼状图

![饼状图](https://raw.githubusercontent.com/wangpt/TJCharts/master/Sources/3.png)
*对象初始化*

```objc
_chartView = ({
        PieChartView *pieChart = [PieChartView new];
        
        [self.view addSubview:pieChart];
        
        [pieChart mas_makeConstraints:^(MASConstraintMaker *make) {
            make.size.mas_equalTo(CGSizeMake(chartW, chartH));
            make.center.mas_equalTo(self.view);
        }];
        
        //基础属性
        
        [pieChart setExtraOffsetsWithLeft:5.f top:10.f right:5.f bottom:5.f];//饼状图距离边缘的间隙

        pieChart.usePercentValuesEnabled = YES;//是否根据所提供的数据, 将显示数据转换为百分比格式
        
        pieChart.dragDecelerationEnabled = YES;//拖拽饼状图后是否有惯性效果
        
        pieChart.drawSliceTextEnabled = YES;//是否显示区块文本
        
        pieChart.chartDescription.enabled = NO;//饼状图描述文字

        
        //空心圆样式(空心有两个圆组成, 一个是hole, 一个是transparentCircle, transparentCircle里面是hole, 所以饼状图中间的空心也就是一个同心圆)
        
        pieChart.drawHoleEnabled = YES;//饼状图是否是空心
        
        pieChart.rotationAngle = 0.0;//开始角度
        
        pieChart.rotationEnabled = YES;//是否可以旋转
        
        pieChart.highlightPerTapEnabled = NO;//是否可以点击
        
        pieChart.holeRadiusPercent = 0.38;//空心半径占比
        
        pieChart.holeColor = [UIColor clearColor];//空心颜色
        
        pieChart.transparentCircleRadiusPercent = 0.41;//半透明空心半径占比
        
        
        if (pieChart.isDrawHoleEnabled == YES) {
            pieChart.drawCenterTextEnabled = YES;//是否显示中间文字
            
            //普通文本
            
            pieChart.centerText = @"";//中间文字

            //富文本
            
            NSMutableAttributedString *centerText = [[NSMutableAttributedString alloc] initWithString:@"饼状图"];
            [centerText setAttributes:@{NSFontAttributeName: [UIFont boldSystemFontOfSize:16],
                                        NSForegroundColorAttributeName: [UIColor orangeColor]}
                                range:NSMakeRange(0, centerText.length)];
            pieChart.centerAttributedText = centerText;
        }
        
        //饼状图描述
        
        ChartLegend *l = pieChart.legend;
        
        l.enabled = YES;//隐藏描述
        
        l.form = ChartLegendFormCircle;//图示样式: 方形、线条、圆形
        
        l.formToTextSpace = 5;//文本间隔
        
        l.font = [UIFont systemFontOfSize:10];//字体大小
        
        l.textColor = [UIColor grayColor];//字体颜色

        l.position = ChartLegendPositionBelowChartCenter;//图例在饼状图中的位置
        
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
        
        double randomVal = arc4random_uniform(range) + range / 2;//产生 50~150 的随机数
        [entries addObject:[[PieChartDataEntry alloc] initWithValue:randomVal label:parties[i % parties.count]]];
    }
    
    PieChartDataSet *dataSet = [[PieChartDataSet alloc] initWithValues:entries label:@""];
    dataSet.sliceSpace = 2.0;//相邻区块之间的间距
    
    dataSet.drawValuesEnabled = YES;//是否绘制显示数据
    // add a lot of colors
    NSMutableArray *colors = [[NSMutableArray alloc] init];
    [colors addObjectsFromArray:ChartColorTemplates.vordiplom];
    [colors addObjectsFromArray:ChartColorTemplates.joyful];
    [colors addObjectsFromArray:ChartColorTemplates.colorful];
    [colors addObjectsFromArray:ChartColorTemplates.liberty];
    [colors addObjectsFromArray:ChartColorTemplates.pastel];
    [colors addObject:[UIColor colorWithRed:51/255.f green:181/255.f blue:229/255.f alpha:1.f]];
    //添加折现
    dataSet.colors = colors;//区块颜色
    dataSet.valueLinePart1OffsetPercentage = 0.8;//折线中第一段起始位置相对于区块的偏移量, 数值越大, 折线距离区块越远
    dataSet.valueLinePart1Length = 0.2;//折线中第一段长度占比
    dataSet.valueLinePart2Length = 0.4;//折线中第二段长度最大占比
    dataSet.valueLineWidth = 1;//折线的粗细
    dataSet.valueLineColor = [UIColor brownColor];//折线颜色
//    dataSet.xValuePosition = PieChartValuePositionOutsideSlice;//名称位置
    dataSet.yValuePosition = PieChartValuePositionOutsideSlice;//数据位置
    
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

![雷达图](https://raw.githubusercontent.com/wangpt/TJCharts/master/Sources/4.png)

Demo下载

[TJCache](https://github.com/wangpt/TJCache)


后记


此文档会不断更新
