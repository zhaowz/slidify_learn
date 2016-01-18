---
title       : 学年总结
subtitle    : 毕业论文相关
author      : zz 2016.1.20
job         : 
framework   : io2012        # {io2012, html5slides, shower, dzslides, revealjs...}
highlighter : highlight.js      # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : [quiz,bootstrap,shiny, interactive]            # {mathjax, quiz, bootstrap}
ext_widgets : {rCharts: [libraries/nvd3]}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
logo        : google_developers_icon_128.png
---

## YAML标记语言

1. YAML是一种标记语言，也就是生成.Rmd的最开始部分，author、title、subtitle等
2. 这部分指定展示文件的一些属性
    + 比如framework，决定了生成html的方式,默认是io2012, 可以切换revealjs,[例子](http://lab.hakim.se/reveal-js/#/)
    + 注意：切换不同framework生成的子文件不会自动删除，可能导致文件夹越来越大
3. 一些slides展示

[非常好的tutorial](http://www.jvcasillas.com/slidify_tutorial/#1)
[简单教程](http://zevross.com/blog/2014/11/19/creating-elegant-html-presentations-that-feature-r-code/)
[官网教程](http://slidify.org/samples/intro/#13)

--- .class #id 

## 正文编辑
### `##`
- 两个#创建新slide的标题

### `---`
- 结束一个slide使用带空行的三个`---`
- 重要的是，当结束一张slide的同时，决定了下一张slide的类别
- 默认就像本张slide是 .class #id
- 所以表示成 `--- .class #id`

正文使用markdown语法

---

## 多级标题示例——1
1. 顺序1
    + 茶
2. 顺序2
    + 上茶
3. 顺序3
    + 上好茶

---

## 多级标题示例——2
* 顺序1
    + 茶
* 顺序2
    + 上茶
* 顺序3
    + 上好茶

---
## ggplot示例

```r
ggplot(diamonds, aes(carat, price))+geom_point(color="firebrick")
```

<img src="assets/fig/unnamed-chunk-1-1.png" title="plot of chunk unnamed-chunk-1" alt="plot of chunk unnamed-chunk-1" style="display: block; margin: auto;" />

---
## style设置
- 放在某个slide中，效果仅应用于某个slide
- 另命名一个.css 文件，放在assets文件夹中，应用在所有slides

```
<style>
.reveal h3 {
    color: #c1f192;
    text-align: left;
    padding-bottom: 50px;
    font-family: Impact, sans-serif;
}
</style>
```

--- #heh bg: yellow
## 修改layout

1. 写一个`layout_name.html`文件，设置一种特定的layout
2. 任何放在assets/layouts中的layout就能被.Rmd文件引用
3. 某个slide需要这种layout的话，就在slide开始的\-\-\-后跟一个`&layout_name`

--- &twoCol
## 双栏layout示例
现在是中间部分

*** =left
左边的图
![plot of chunk unnamed-chunk-2](assets/fig/unnamed-chunk-2-1.png) 

*** =right
右边的图
![plot of chunk unnamed-chunk-3](assets/fig/unnamed-chunk-3-1.png) 

*** =fullwidth
then is back fullwidth,(这里使用中文出错)

---
## 动态显现的效果

> * io2012 通过 \> \* 来进行动态显示
> * revealjs 通过.fragment进行动态效果（以及脚本）

.fragment io2012 通过 \> \* 来进行动态显示

.fragment revealjs 通过.fragment进行动态效果（以及脚本）

<script>
$('ul.incremental li').addClass('fragment')
$('ol.incremental li').addClass('fragment')
</script>

---
## 关于widget
+ widget可以让你：
    - 制作问卷
    - 使用数学公式
    - 使用 bootstrap framework
+ logo 放在 assets > img 文件夹（io2012文件夹有一个默认logo）
    - 该文件夹也是放其他展示图片的地方

---

--- &radio
## 交互式问答：示例

1+1等于？

1. 1
2. _2_
3. 3
4. 4

*** .hint

这是个提示

*** .explanation

这是一个解释

---

## 交互式问答：方法
- YAML 首页部分添加两个模块，widgets    : [quiz,bootstrap]
- quiz中的radio是一个交互问答的模块
- bootstrap是一个上色模块
- &radio表示本slide将使用该模块展示，所以不能再加入其他非格式正文
- \_2\_是隐藏正确结果所用

---
## 交互式图形：rCharts示例

<div id = 'chart1' class = 'rChart nvd3'></div>
<script type='text/javascript'>
 $(document).ready(function(){
      drawchart1()
    });
    function drawchart1(){  
      var opts = {
 "dom": "chart1",
"width":    800,
"height":    400,
"x": "Hair",
"y": "Freq",
"group": "Eye",
"type": "multiBarChart",
"id": "chart1" 
},
        data = [
 {
 "Hair": "Black",
"Eye": "Brown",
"Sex": "Male",
"Freq":             32 
},
{
 "Hair": "Brown",
"Eye": "Brown",
"Sex": "Male",
"Freq":             53 
},
{
 "Hair": "Red",
"Eye": "Brown",
"Sex": "Male",
"Freq":             10 
},
{
 "Hair": "Blond",
"Eye": "Brown",
"Sex": "Male",
"Freq":              3 
},
{
 "Hair": "Black",
"Eye": "Blue",
"Sex": "Male",
"Freq":             11 
},
{
 "Hair": "Brown",
"Eye": "Blue",
"Sex": "Male",
"Freq":             50 
},
{
 "Hair": "Red",
"Eye": "Blue",
"Sex": "Male",
"Freq":             10 
},
{
 "Hair": "Blond",
"Eye": "Blue",
"Sex": "Male",
"Freq":             30 
},
{
 "Hair": "Black",
"Eye": "Hazel",
"Sex": "Male",
"Freq":             10 
},
{
 "Hair": "Brown",
"Eye": "Hazel",
"Sex": "Male",
"Freq":             25 
},
{
 "Hair": "Red",
"Eye": "Hazel",
"Sex": "Male",
"Freq":              7 
},
{
 "Hair": "Blond",
"Eye": "Hazel",
"Sex": "Male",
"Freq":              5 
},
{
 "Hair": "Black",
"Eye": "Green",
"Sex": "Male",
"Freq":              3 
},
{
 "Hair": "Brown",
"Eye": "Green",
"Sex": "Male",
"Freq":             15 
},
{
 "Hair": "Red",
"Eye": "Green",
"Sex": "Male",
"Freq":              7 
},
{
 "Hair": "Blond",
"Eye": "Green",
"Sex": "Male",
"Freq":              8 
},
{
 "Hair": "Black",
"Eye": "Brown",
"Sex": "Female",
"Freq":             36 
},
{
 "Hair": "Brown",
"Eye": "Brown",
"Sex": "Female",
"Freq":             66 
},
{
 "Hair": "Red",
"Eye": "Brown",
"Sex": "Female",
"Freq":             16 
},
{
 "Hair": "Blond",
"Eye": "Brown",
"Sex": "Female",
"Freq":              4 
},
{
 "Hair": "Black",
"Eye": "Blue",
"Sex": "Female",
"Freq":              9 
},
{
 "Hair": "Brown",
"Eye": "Blue",
"Sex": "Female",
"Freq":             34 
},
{
 "Hair": "Red",
"Eye": "Blue",
"Sex": "Female",
"Freq":              7 
},
{
 "Hair": "Blond",
"Eye": "Blue",
"Sex": "Female",
"Freq":             64 
},
{
 "Hair": "Black",
"Eye": "Hazel",
"Sex": "Female",
"Freq":              5 
},
{
 "Hair": "Brown",
"Eye": "Hazel",
"Sex": "Female",
"Freq":             29 
},
{
 "Hair": "Red",
"Eye": "Hazel",
"Sex": "Female",
"Freq":              7 
},
{
 "Hair": "Blond",
"Eye": "Hazel",
"Sex": "Female",
"Freq":              5 
},
{
 "Hair": "Black",
"Eye": "Green",
"Sex": "Female",
"Freq":              2 
},
{
 "Hair": "Brown",
"Eye": "Green",
"Sex": "Female",
"Freq":             14 
},
{
 "Hair": "Red",
"Eye": "Green",
"Sex": "Female",
"Freq":              7 
},
{
 "Hair": "Blond",
"Eye": "Green",
"Sex": "Female",
"Freq":              8 
} 
]
  
      if(!(opts.type==="pieChart" || opts.type==="sparklinePlus" || opts.type==="bulletChart")) {
        var data = d3.nest()
          .key(function(d){
            //return opts.group === undefined ? 'main' : d[opts.group]
            //instead of main would think a better default is opts.x
            return opts.group === undefined ? opts.y : d[opts.group];
          })
          .entries(data);
      }
      
      if (opts.disabled != undefined){
        data.map(function(d, i){
          d.disabled = opts.disabled[i]
        })
      }
      
      nv.addGraph(function() {
        var chart = nv.models[opts.type]()
          .width(opts.width)
          .height(opts.height)
          
        if (opts.type != "bulletChart"){
          chart
            .x(function(d) { return d[opts.x] })
            .y(function(d) { return d[opts.y] })
        }
          
         
        
          
        

        
        
        
      
       d3.select("#" + opts.id)
        .append('svg')
        .datum(data)
        .transition().duration(500)
        .call(chart);

       nv.utils.windowResize(chart.update);
       return chart;
      });
    };
</script>
- YAML添加外部模块，ext_widgets : {rCharts: [libraries/nvd3]}
- 引入代码进行展示（这里需要rCharts包，github上下载）

---&interactive
## 交互式控制：示例

```r
require(googleVis)
M1 <- gvisMotionChart(Fruits, idvar = 'Fruit', timevar = 'Year')
print(M1, tag = 'charts')
```

```
## Error in print.gvis(M1, tag = "charts"): charts is not a valid option. Set tag to NULL or one of the following:
##  type, chartid, html, header, chart, jsHeader, jsData, jsDrawChart, jsDisplayChart, jsFooter, jsChart, divChart, caption, footer
```

---
