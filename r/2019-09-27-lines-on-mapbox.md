---
description: How to draw a line on Map in R with plotly.
display_as: maps
language: r
layout: base
name: Lines on Mapbox
order: 10
output:
  html_document:
    keep_md: true
page_type: u-guide
permalink: r/lines-on-mapbox/
thumbnail: thumbnail/line_mapbox.jpg
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

### Mapbox Access Token

To plot on Mapbox maps with Plotly you `may` need a Mapbox account and a public [Mapbox Access Token](https://www.mapbox.com/studio), that you can add to your [Plotly Settings](https://plot.ly/settings/mapbox). See our [Mapbox Map Layers](/python/mapbox-layers/) documentation for more information. If you're using a Chart Studio Enterprise server, please see additional instructions [here](https://help.plot.ly/mapbox-atlas).

### How to draw a Line on a Map

To draw a line on your map, you either can use [Scattermapbox](https://plot.ly/r/reference/#scattermapbox) or [scattergeo](https://plot.ly/r/reference/#scattergeo) trace type in plotly. This example uses scattermapbox and defines the drawing [mode](https://plot.ly/python/reference/#scattermapbox-mode) to the combination of markers and line.


```r
library(plotly)

p <- plot_ly(
  type = 'scattermapbox',
  mode = "markers+lines",
  lon = c(10, 20, 30),
  lat = c(10, 20,30),
  marker = list(size = 10)) %>%
  add_trace(
    type = 'scattermapbox',
    mode = "markers+lines",
    lon = c(-50, -60,40),
    lat = c(30, 10, -20),
    marker = list(size = 10)) %>%
  layout(
    mapbox = list(
      style = "stamen-terrain",
      center = list(lon = 10, lat= 10),
      zoom = 1),
    margin =list(l=0,t=0,b=0,r=0))

p
```

<div id="htmlwidget-b301112b2ee49d8a2e6e" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-b301112b2ee49d8a2e6e">{"x":{"visdat":{"32d511a21284":["function () ","plotlyVisDat"]},"cur_data":"32d511a21284","attrs":{"32d511a21284":{"mode":"markers+lines","lon":[10,20,30],"lat":[10,20,30],"marker":{"size":10},"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scattermapbox"},"32d511a21284.1":{"mode":"markers+lines","lon":[-50,-60,40],"lat":[30,10,-20],"marker":{"size":10},"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scattermapbox","inherit":true}},"layout":{"margin":{"b":0,"l":0,"t":0,"r":0},"mapbox":{"style":"stamen-terrain","center":{"lon":10,"lat":10},"zoom":1},"hovermode":"closest","showlegend":true},"source":"A","config":{"showSendToCloud":false},"data":[{"mode":"markers+lines","lon":[10,20,30],"lat":[10,20,30],"marker":{"color":"rgba(31,119,180,1)","size":10,"line":{"color":"rgba(31,119,180,1)"}},"type":"scattermapbox","line":{"color":"rgba(31,119,180,1)"},"frame":null},{"mode":"markers+lines","lon":[-50,-60,40],"lat":[30,10,-20],"marker":{"color":"rgba(255,127,14,1)","size":10,"line":{"color":"rgba(255,127,14,1)"}},"type":"scattermapbox","line":{"color":"rgba(255,127,14,1)"},"frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

This example uses scattermapbox trace and shows how to customize hoverinfo in Mapbox.


```r
library(plotly)

us_cities = read.csv("https://raw.githubusercontent.com/plotly/datasets/master/us-cities-top-1k.csv")

df = us_cities[us_cities$State == c('Washington'),]


p <- plot_ly(
    df,
    lat= ~lat,
    lon= ~lon,
    type = 'scattermapbox',
    mode='markers+lines',
    marker=list(
      color = 'fuchsia',
      size = 10,
      opacity =0.8),
    color = list('color'),
    hovertext = ~City,
    hoverinfo = "lat+lon+text") %>%
  layout(
    mapbox=list(style = 'stamen-terrain',
                center = list(lat =47, lon = -122),
                zoom =5),
    margin=list(r = 0,t = 0, l = 0, b = 0))

p
```

<div id="htmlwidget-fc47d72418496c3a3f7e" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-fc47d72418496c3a3f7e">{"x":{"visdat":{"32d52a352493":["function () ","plotlyVisDat"]},"cur_data":"32d52a352493","attrs":{"32d52a352493":{"lat":{},"lon":{},"mode":"markers+lines","marker":{"color":"fuchsia","size":10,"opacity":0.8},"hovertext":{},"hoverinfo":"lat+lon+text","color":["color"],"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scattermapbox"}},"layout":{"margin":{"b":0,"l":0,"t":0,"r":0},"mapbox":{"style":"stamen-terrain","center":{"lat":47,"lon":-122},"zoom":5},"hovermode":"closest","showlegend":false},"source":"A","config":{"showSendToCloud":false},"data":[{"lat":[48.0517637,47.6587802,46.2112458,48.74908,47.1717649,47.4703767,47.1853785,47.5673202,47.7556531,47.8106521,47.3809335,47.6732281,47.0342629,46.6020711,47.9789848,45.6387281,47.6062095,47.610377,46.2856907,47.3073228,47.4828776,47.6814875,47.6162683,47.2528768,46.2395793,47.6739881,47.3223221,47.0378741],"lon":[-122.1770818,-117.4260466,-119.1372338,-122.4781473,-122.518458,-122.3467918,-122.2928974,-122.6329356,-122.3415178,-122.3773552,-122.2348431,-117.2393748,-122.8231915,-120.5058987,-122.2020794,-122.6614861,-122.3320708,-122.2006786,-119.2844621,-122.2284532,-122.2170661,-122.2087353,-122.0355736,-122.4442906,-119.1005657,-122.121512,-122.3126222,-122.9006951],"mode":"markers+lines","marker":{"color":"fuchsia","size":10,"opacity":0.8},"hovertext":["Marysville","Spokane","Kennewick","Bellingham","Lakewood","Burien","Puyallup","Bremerton","Shoreline","Edmonds","Kent","Spokane Valley","Lacey","Yakima","Everett","Vancouver","Seattle","Bellevue","Richland","Auburn","Renton","Kirkland","Sammamish","Tacoma","Pasco","Redmond","Federal Way","Olympia"],"hoverinfo":["lat+lon+text","lat+lon+text","lat+lon+text","lat+lon+text","lat+lon+text","lat+lon+text","lat+lon+text","lat+lon+text","lat+lon+text","lat+lon+text","lat+lon+text","lat+lon+text","lat+lon+text","lat+lon+text","lat+lon+text","lat+lon+text","lat+lon+text","lat+lon+text","lat+lon+text","lat+lon+text","lat+lon+text","lat+lon+text","lat+lon+text","lat+lon+text","lat+lon+text","lat+lon+text","lat+lon+text","lat+lon+text"],"type":"scattermapbox","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

#Reference

See [https://plot.ly/r/reference/#scattermapbox](https://plot.ly/r/reference/#scattermapbox) for more information and options!
