---
name: Error Bars
permalink: r/error-bars/
description: How to add error bars to plots in R.
layout: base
thumbnail: thumbnail/error-bar.jpg
language: r
page_type: example_index
display_as: statistical
order: 4
output:
  html_document:
    keep_md: true
---



### New to Plotly?

Plotly's R library is free and open source!<br>
[Get started](https://plot.ly/r/getting-started/) by downloading the client and [reading the primer](https://plot.ly/r/getting-started/).<br>
You can set up Plotly to work in [online](https://plot.ly/r/getting-started/#hosting-graphs-in-your-online-plotly-account) or [offline](https://plot.ly/r/offline/) mode.<br>
We also have a quick-reference [cheatsheet](https://images.plot.ly/plotly-documentation/images/r_cheat_sheet.pdf) (new!) to help you get started!

### Version Check

Version 4 of Plotly's R package is now [available](https://plot.ly/r/getting-started/#installation)!<br>
Check out [this post](http://moderndata.plot.ly/upgrading-to-plotly-4-0-and-above/) for more information on breaking changes and new features available in this version.

```r
library(plotly)
packageVersion('plotly')
```

```
## [1] '4.9.1'
```

### Bar Chart with Error Bars


```r
library(plotly)
library(plyr)

data_mean <- ddply(ToothGrowth, c("supp", "dose"), summarise, length = mean(len))
data_sd <- ddply(ToothGrowth, c("supp", "dose"), summarise, length = sd(len))
data <- data.frame(data_mean, data_sd$length)
data <- rename(data, c("data_sd.length" = "sd"))
data$dose <- as.factor(data$dose)

p <- plot_ly(data = data[which(data$supp == 'OJ'),], x = ~dose, y = ~length, type = 'bar', name = 'OJ',
        error_y = ~list(array = sd,
                        color = '#000000')) %>%
  add_trace(data = data[which(data$supp == 'VC'),], name = 'VC')

p
```

<div id="htmlwidget-609ea2e110213f871f7e" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-609ea2e110213f871f7e">{"x":{"visdat":{"1c5f39a07d71":["function () ","plotlyVisDat"],"1c5f98a78c1":["function () ","data"]},"cur_data":"1c5f98a78c1","attrs":{"1c5f39a07d71":{"x":{},"y":{},"error_y":{},"name":"OJ","alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"bar"},"1c5f98a78c1":{"x":{},"y":{},"error_y":{},"name":"VC","alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"bar","inherit":true}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"xaxis":{"domain":[0,1],"automargin":true,"title":"dose","type":"category","categoryorder":"array","categoryarray":["0.5","1","2"]},"yaxis":{"domain":[0,1],"automargin":true,"title":"length"},"hovermode":"closest","showlegend":true},"source":"A","config":{"showSendToCloud":false},"data":[{"x":["0.5","1","2"],"y":[13.23,22.7,26.06],"error_y":{"color":"#000000","array":[4.45970851065403,3.91095327964367,2.65505806590615]},"name":"OJ","type":"bar","marker":{"color":"rgba(31,119,180,1)","line":{"color":"rgba(31,119,180,1)"}},"error_x":{"color":"rgba(31,119,180,1)"},"xaxis":"x","yaxis":"y","frame":null},{"x":["0.5","1","2"],"y":[7.98,16.77,26.14],"error_y":{"color":"#000000","array":[2.74663430401646,2.51530868439199,4.79773094516796]},"name":"VC","type":"bar","marker":{"color":"rgba(255,127,14,1)","line":{"color":"rgba(255,127,14,1)"}},"error_x":{"color":"rgba(255,127,14,1)"},"xaxis":"x","yaxis":"y","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

### Scatterplot with Error Bars


```r
library(plotly)
library(plyr)

data_mean <- ddply(ToothGrowth, c("supp", "dose"), summarise, length = mean(len))
data_sd <- ddply(ToothGrowth, c("supp", "dose"), summarise, length = sd(len))
data <- data.frame(data_mean, data_sd$length)
data <- rename(data, c("data_sd.length" = "sd"))
data$dose <- as.factor(data$dose)

p <- plot_ly(data = data[which(data$supp == 'OJ'),], x = ~dose, y = ~length, type = 'scatter', mode = 'markers',
        name = 'OJ',
        error_y = ~list(array = sd,
                        color = '#000000')) %>%
  add_trace(data = data[which(data$supp == 'VC'),], name = 'VC')

p
```

<div id="htmlwidget-a77f6c640651382246e6" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-a77f6c640651382246e6">{"x":{"visdat":{"1c5f1a20777e":["function () ","plotlyVisDat"],"1c5f6261b830":["function () ","data"]},"cur_data":"1c5f6261b830","attrs":{"1c5f1a20777e":{"x":{},"y":{},"mode":"markers","error_y":{},"name":"OJ","alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatter"},"1c5f6261b830":{"x":{},"y":{},"mode":"markers","error_y":{},"name":"VC","alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatter","inherit":true}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"xaxis":{"domain":[0,1],"automargin":true,"title":"dose","type":"category","categoryorder":"array","categoryarray":["0.5","1","2"]},"yaxis":{"domain":[0,1],"automargin":true,"title":"length"},"hovermode":"closest","showlegend":true},"source":"A","config":{"showSendToCloud":false},"data":[{"x":["0.5","1","2"],"y":[13.23,22.7,26.06],"mode":"markers","error_y":{"color":"#000000","array":[4.45970851065403,3.91095327964367,2.65505806590615]},"name":"OJ","type":"scatter","marker":{"color":"rgba(31,119,180,1)","line":{"color":"rgba(31,119,180,1)"}},"error_x":{"color":"rgba(31,119,180,1)"},"line":{"color":"rgba(31,119,180,1)"},"xaxis":"x","yaxis":"y","frame":null},{"x":["0.5","1","2"],"y":[7.98,16.77,26.14],"mode":"markers","error_y":{"color":"#000000","array":[2.74663430401646,2.51530868439199,4.79773094516796]},"name":"VC","type":"scatter","marker":{"color":"rgba(255,127,14,1)","line":{"color":"rgba(255,127,14,1)"}},"error_x":{"color":"rgba(255,127,14,1)"},"line":{"color":"rgba(255,127,14,1)"},"xaxis":"x","yaxis":"y","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

### Line Graph with Error Bars


```r
library(plotly)
library(plyr)

data_mean <- ddply(ToothGrowth, c("supp", "dose"), summarise, length = mean(len))
data_sd <- ddply(ToothGrowth, c("supp", "dose"), summarise, length = sd(len))
data <- data.frame(data_mean, data_sd$length)
data <- rename(data, c("data_sd.length" = "sd"))
data$dose <- as.factor(data$dose)

p <- plot_ly(data = data[which(data$supp == 'OJ'),], x = ~dose, y = ~length, type = 'scatter', mode = 'lines+markers',
        name = 'OJ',
        error_y = ~list(array = sd,
                        color = '#000000')) %>%
  add_trace(data = data[which(data$supp == 'VC'),], name = 'VC')

p
```

<div id="htmlwidget-3c8f9860bea9d2c43fa6" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-3c8f9860bea9d2c43fa6">{"x":{"visdat":{"1c5f2ef00e4f":["function () ","plotlyVisDat"],"1c5f6b06be95":["function () ","data"]},"cur_data":"1c5f6b06be95","attrs":{"1c5f2ef00e4f":{"x":{},"y":{},"mode":"lines+markers","error_y":{},"name":"OJ","alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatter"},"1c5f6b06be95":{"x":{},"y":{},"mode":"lines+markers","error_y":{},"name":"VC","alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatter","inherit":true}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"xaxis":{"domain":[0,1],"automargin":true,"title":"dose","type":"category","categoryorder":"array","categoryarray":["0.5","1","2"]},"yaxis":{"domain":[0,1],"automargin":true,"title":"length"},"hovermode":"closest","showlegend":true},"source":"A","config":{"showSendToCloud":false},"data":[{"x":["0.5","1","2"],"y":[13.23,22.7,26.06],"mode":"lines+markers","error_y":{"color":"#000000","array":[4.45970851065403,3.91095327964367,2.65505806590615]},"name":"OJ","type":"scatter","marker":{"color":"rgba(31,119,180,1)","line":{"color":"rgba(31,119,180,1)"}},"error_x":{"color":"rgba(31,119,180,1)"},"line":{"color":"rgba(31,119,180,1)"},"xaxis":"x","yaxis":"y","frame":null},{"x":["0.5","1","2"],"y":[7.98,16.77,26.14],"mode":"lines+markers","error_y":{"color":"#000000","array":[2.74663430401646,2.51530868439199,4.79773094516796]},"name":"VC","type":"scatter","marker":{"color":"rgba(255,127,14,1)","line":{"color":"rgba(255,127,14,1)"}},"error_x":{"color":"rgba(255,127,14,1)"},"line":{"color":"rgba(255,127,14,1)"},"xaxis":"x","yaxis":"y","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

### Reference

See [https://plot.ly/r/reference](https://plot.ly/r/reference) for more information and chart attribute options!
