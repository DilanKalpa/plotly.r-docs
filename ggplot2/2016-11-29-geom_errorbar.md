---
name: geom_errorbar
permalink: ggplot2/geom_errorbar/
description: Examples of geom_errobar in R and ggplot2
layout: base
thumbnail: thumbnail/error-bar.jpg
language: ggplot2
page_type: example_index
display_as: statistics
order: 2
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

### Basic Error Bar


```r
library(plotly)

df <- data.frame(x = 1:10,
                 y = 1:10,
                 ymin = (1:10) - runif(10),
                 ymax = (1:10) + runif(10),
                 xmin = (1:10) - runif(10),
                 xmax = (1:10) + runif(10))

p <- ggplot(data = df,aes(x = x,y = y)) + 
    geom_point() + 
    geom_errorbar(aes(ymin = ymin,ymax = ymax)) + 
    geom_errorbarh(aes(xmin = xmin,xmax = xmax))

p <- ggplotly(p)

p
```

<div id="htmlwidget-71f63bce27b5261ec578" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-71f63bce27b5261ec578">{"x":{"data":[{"x":[1,2,3,4,5,6,7,8,9,10],"y":[1,2,3,4,5,6,7,8,9,10],"text":["x:  1<br />y:  1","x:  2<br />y:  2","x:  3<br />y:  3","x:  4<br />y:  4","x:  5<br />y:  5","x:  6<br />y:  6","x:  7<br />y:  7","x:  8<br />y:  8","x:  9<br />y:  9","x: 10<br />y: 10"],"type":"scatter","mode":"markers","marker":{"autocolorscale":false,"color":"rgba(0,0,0,1)","opacity":1,"size":5.66929133858268,"symbol":"circle","line":{"width":1.88976377952756,"color":"rgba(0,0,0,1)"}},"hoveron":"points","showlegend":false,"xaxis":"x","yaxis":"y","hoverinfo":"text","frame":null},{"x":[1,2,3,4,5,6,7,8,9,10],"y":[1,2,3,4,5,6,7,8,9,10],"text":["ymin: 0.9826087<br />ymax:  1.144372<br />x:  1<br />y:  1","ymin: 1.4879835<br />ymax:  2.855421<br />x:  2<br />y:  2","ymin: 2.6925589<br />ymax:  3.438225<br />x:  3<br />y:  3","ymin: 3.2534331<br />ymax:  4.111678<br />x:  4<br />y:  4","ymin: 4.2281251<br />ymax:  5.070214<br />x:  5<br />y:  5","ymin: 5.7701915<br />ymax:  6.670966<br />x:  6<br />y:  6","ymin: 6.0493040<br />ymax:  7.385810<br />x:  7<br />y:  7","ymin: 7.8527362<br />ymax:  8.596087<br />x:  8<br />y:  8","ymin: 8.3121036<br />ymax:  9.643104<br />x:  9<br />y:  9","ymin: 9.5263723<br />ymax: 10.162563<br />x: 10<br />y: 10"],"type":"scatter","mode":"lines","opacity":1,"line":{"color":"transparent"},"error_y":{"array":[0.144372386857867,0.855421250453219,0.438225151738152,0.111678343499079,0.0702139621134847,0.670966040575877,0.385809800121933,0.596087426645681,0.643103824928403,0.162563195917755],"arrayminus":[0.0173913491889834,0.512016521999612,0.307441103970632,0.746566944289953,0.771874904166907,0.229808509349823,0.950695978710428,0.147263786522672,0.687896379036829,0.473627723520622],"type":"data","width":18.275408208782,"symmetric":false,"color":"rgba(0,0,0,1)"},"showlegend":false,"xaxis":"x","yaxis":"y","hoverinfo":"text","frame":null},{"x":[1,2,3,4,5,6,7,8,9,10],"y":[1,2,3,4,5,6,7,8,9,10],"text":["xmin: 0.9067402<br />xmax:  1.683923<br />x:  1<br />y:  1","xmin: 1.5101681<br />xmax:  2.883588<br />x:  2<br />y:  2","xmin: 2.9304828<br />xmax:  3.679410<br />x:  3<br />y:  3","xmin: 3.0418143<br />xmax:  4.440528<br />x:  4<br />y:  4","xmin: 4.1402373<br />xmax:  5.128970<br />x:  5<br />y:  5","xmin: 5.9031718<br />xmax:  6.646703<br />x:  6<br />y:  6","xmin: 6.9465664<br />xmax:  7.577521<br />x:  7<br />y:  7","xmin: 7.3276556<br />xmax:  8.161420<br />x:  8<br />y:  8","xmin: 8.1505828<br />xmax:  9.305976<br />x:  9<br />y:  9","xmin: 9.8801901<br />xmax: 10.578379<br />x: 10<br />y: 10"],"type":"scatter","mode":"lines","opacity":1,"line":{"color":"transparent"},"error_x":{"array":[0.683922668453306,0.883588045369834,0.67941035144031,0.440527998376638,0.128970164805651,0.646702884463593,0.577521403552964,0.161420131335035,0.305975840659812,0.578379403566942],"arrayminus":[0.093259809538722,0.489831872982904,0.0695171982515603,0.958185698604211,0.859762687701732,0.0968281922396272,0.0534335502889007,0.672344369580969,0.849417177028954,0.119809869443998],"type":"data","width":13.2231404958678,"symmetric":false,"color":"rgba(0,0,0,1)"},"showlegend":false,"xaxis":"x","yaxis":"y","hoverinfo":"text","frame":null}],"layout":{"margin":{"t":26.2283105022831,"r":7.30593607305936,"b":40.1826484018265,"l":48.9497716894977},"plot_bgcolor":"rgba(235,235,235,1)","paper_bgcolor":"rgba(255,255,255,1)","font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187},"xaxis":{"domain":[0,1],"automargin":true,"type":"linear","autorange":false,"range":[0.048581029821653,11.0797983737453],"tickmode":"array","ticktext":["2.5","5.0","7.5","10.0"],"tickvals":[2.5,5,7.5,10],"categoryorder":"array","categoryarray":["2.5","5.0","7.5","10.0"],"nticks":null,"ticks":"outside","tickcolor":"rgba(51,51,51,1)","ticklen":3.65296803652968,"tickwidth":0.66417600664176,"showticklabels":true,"tickfont":{"color":"rgba(77,77,77,1)","family":"","size":11.689497716895},"tickangle":-0,"showline":false,"linecolor":null,"linewidth":0,"showgrid":true,"gridcolor":"rgba(255,255,255,1)","gridwidth":0.66417600664176,"zeroline":false,"anchor":"y","title":{"text":"x","font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187}},"hoverformat":".2f"},"yaxis":{"domain":[0,1],"automargin":true,"type":"linear","autorange":false,"range":[0.0550000000000001,10.945],"tickmode":"array","ticktext":["2.5","5.0","7.5","10.0"],"tickvals":[2.5,5,7.5,10],"categoryorder":"array","categoryarray":["2.5","5.0","7.5","10.0"],"nticks":null,"ticks":"outside","tickcolor":"rgba(51,51,51,1)","ticklen":3.65296803652968,"tickwidth":0.66417600664176,"showticklabels":true,"tickfont":{"color":"rgba(77,77,77,1)","family":"","size":11.689497716895},"tickangle":-0,"showline":false,"linecolor":null,"linewidth":0,"showgrid":true,"gridcolor":"rgba(255,255,255,1)","gridwidth":0.66417600664176,"zeroline":false,"anchor":"x","title":{"text":"y","font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187}},"hoverformat":".2f"},"shapes":[{"type":"rect","fillcolor":null,"line":{"color":null,"width":0,"linetype":[]},"yref":"paper","xref":"paper","x0":0,"x1":1,"y0":0,"y1":1}],"showlegend":false,"legend":{"bgcolor":"rgba(255,255,255,1)","bordercolor":"transparent","borderwidth":1.88976377952756,"font":{"color":"rgba(0,0,0,1)","family":"","size":11.689497716895}},"hovermode":"closest","barmode":"relative"},"config":{"doubleClick":"reset","showSendToCloud":false},"source":"A","attrs":{"373534d81d01":{"x":{},"y":{},"type":"scatter"},"373538a79582":{"ymin":{},"ymax":{},"x":{},"y":{}},"37351035cea9":{"xmin":{},"xmax":{},"x":{},"y":{}}},"cur_data":"373534d81d01","visdat":{"373534d81d01":["function (y) ","x"],"373538a79582":["function (y) ","x"],"37351035cea9":["function (y) ","x"]},"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

### Margin Error Bar


```r
library(plotly)

population <- data.frame(Year=seq(1790, 1970, length.out=length(uspop)), 
                         Population=uspop, 
                         Error=rnorm(length(uspop), 5))

library(ggplot2)
p <- ggplot(population, aes(x=Year, y=Population, 
                       ymin=Population-Error, ymax=Population+Error))+
  geom_line()+
  geom_point(pch=2)+
  geom_errorbar(width=0.9)

p <- ggplotly(p)

p
```

<div id="htmlwidget-5c1607bc300dcfd499ba" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-5c1607bc300dcfd499ba">{"x":{"data":[{"x":[1790,1800,1810,1820,1830,1840,1850,1860,1870,1880,1890,1900,1910,1920,1930,1940,1950,1960,1970],"y":[3.93,5.31,7.24,9.64,12.9,17.1,23.2,31.4,39.8,50.2,62.9,76,92,105.7,122.8,131.7,151.3,179.3,203.2],"text":["Year: 1790<br />Population:   3.93<br />Population - Error:  -0.8673286<br />Population + Error:   8.727329","Year: 1800<br />Population:   5.31<br />Population - Error:   1.0189287<br />Population + Error:   9.601071","Year: 1810<br />Population:   7.24<br />Population - Error:   2.5467532<br />Population + Error:  11.933247","Year: 1820<br />Population:   9.64<br />Population - Error:   5.2524720<br />Population + Error:  14.027528","Year: 1830<br />Population:  12.90<br />Population - Error:  10.3616518<br />Population + Error:  15.438348","Year: 1840<br />Population:  17.10<br />Population - Error:  14.1346846<br />Population + Error:  20.065315","Year: 1850<br />Population:  23.20<br />Population - Error:  15.5303507<br />Population + Error:  30.869649","Year: 1860<br />Population:  31.40<br />Population - Error:  27.1220965<br />Population + Error:  35.677903","Year: 1870<br />Population:  39.80<br />Population - Error:  36.3402013<br />Population + Error:  43.259799","Year: 1880<br />Population:  50.20<br />Population - Error:  44.7375323<br />Population + Error:  55.662468","Year: 1890<br />Population:  62.90<br />Population - Error:  56.1274891<br />Population + Error:  69.672511","Year: 1900<br />Population:  76.00<br />Population - Error:  71.2145390<br />Population + Error:  80.785461","Year: 1910<br />Population:  92.00<br />Population - Error:  88.0723163<br />Population + Error:  95.927684","Year: 1920<br />Population: 105.70<br />Population - Error: 100.8424139<br />Population + Error: 110.557586","Year: 1930<br />Population: 122.80<br />Population - Error: 116.7652809<br />Population + Error: 128.834719","Year: 1940<br />Population: 131.70<br />Population - Error: 125.7404155<br />Population + Error: 137.659585","Year: 1950<br />Population: 151.30<br />Population - Error: 146.6348094<br />Population + Error: 155.965191","Year: 1960<br />Population: 179.30<br />Population - Error: 174.0456230<br />Population + Error: 184.554377","Year: 1970<br />Population: 203.20<br />Population - Error: 199.1057987<br />Population + Error: 207.294201"],"type":"scatter","mode":"lines+markers","line":{"width":1.88976377952756,"color":"transparent","dash":"solid"},"hoveron":"points","showlegend":false,"xaxis":"x","yaxis":"y","hoverinfo":"text","marker":{"autocolorscale":false,"color":"rgba(0,0,0,1)","opacity":1,"size":5.66929133858268,"symbol":"triangle-up-open","line":{"width":1.88976377952756,"color":"rgba(0,0,0,1)"}},"opacity":1,"error_y":{"array":[4.79732859324792,4.29107126706362,4.69324676757119,4.3875280333004,2.53834819239626,2.96531539148981,7.66964927859228,4.27790348407951,3.45979868210173,5.46246767376668,6.77251085797658,4.78546100479441,3.92768368656644,4.85758613414482,6.03471912946368,5.95958450888935,4.66519056852607,5.2543770384155,4.09420131729749],"arrayminus":[4.79732859324792,4.29107126706362,4.69324676757119,4.3875280333004,2.53834819239626,2.96531539148982,7.66964927859229,4.27790348407951,3.45979868210173,5.46246767376668,6.77251085797657,4.78546100479441,3.92768368656644,4.85758613414482,6.0347191294637,5.95958450888936,4.66519056852607,5.2543770384155,4.09420131729749],"type":"data","width":1.01311623699693,"symmetric":false,"color":"rgba(0,0,0,1)"},"frame":null}],"layout":{"margin":{"t":26.2283105022831,"r":7.30593607305936,"b":40.1826484018265,"l":43.1050228310502},"plot_bgcolor":"rgba(235,235,235,1)","paper_bgcolor":"rgba(255,255,255,1)","font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187},"xaxis":{"domain":[0,1],"automargin":true,"type":"linear","autorange":false,"range":[1780.505,1979.495],"tickmode":"array","ticktext":["1800","1850","1900","1950"],"tickvals":[1800,1850,1900,1950],"categoryorder":"array","categoryarray":["1800","1850","1900","1950"],"nticks":null,"ticks":"outside","tickcolor":"rgba(51,51,51,1)","ticklen":3.65296803652968,"tickwidth":0.66417600664176,"showticklabels":true,"tickfont":{"color":"rgba(77,77,77,1)","family":"","size":11.689497716895},"tickangle":-0,"showline":false,"linecolor":null,"linewidth":0,"showgrid":true,"gridcolor":"rgba(255,255,255,1)","gridwidth":0.66417600664176,"zeroline":false,"anchor":"y","title":{"text":"Year","font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187}},"hoverformat":".2f"},"yaxis":{"domain":[0,1],"automargin":true,"type":"linear","autorange":false,"range":[-11.2754050887752,217.702277812825],"tickmode":"array","ticktext":["0","50","100","150","200"],"tickvals":[0,50,100,150,200],"categoryorder":"array","categoryarray":["0","50","100","150","200"],"nticks":null,"ticks":"outside","tickcolor":"rgba(51,51,51,1)","ticklen":3.65296803652968,"tickwidth":0.66417600664176,"showticklabels":true,"tickfont":{"color":"rgba(77,77,77,1)","family":"","size":11.689497716895},"tickangle":-0,"showline":false,"linecolor":null,"linewidth":0,"showgrid":true,"gridcolor":"rgba(255,255,255,1)","gridwidth":0.66417600664176,"zeroline":false,"anchor":"x","title":{"text":"Population","font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187}},"hoverformat":".2f"},"shapes":[{"type":"rect","fillcolor":null,"line":{"color":null,"width":0,"linetype":[]},"yref":"paper","xref":"paper","x0":0,"x1":1,"y0":0,"y1":1}],"showlegend":false,"legend":{"bgcolor":"rgba(255,255,255,1)","bordercolor":"transparent","borderwidth":1.88976377952756,"font":{"color":"rgba(0,0,0,1)","family":"","size":11.689497716895}},"hovermode":"closest","barmode":"relative"},"config":{"doubleClick":"reset","showSendToCloud":false},"source":"A","attrs":{"3735726bfb5e":{"x":{},"y":{},"ymin":{},"ymax":{},"type":"scatter"},"3735763707a4":{"x":{},"y":{},"ymin":{},"ymax":{}},"37352a88d14a":{"x":{},"y":{},"ymin":{},"ymax":{}}},"cur_data":"3735726bfb5e","visdat":{"3735726bfb5e":["function (y) ","x"],"3735763707a4":["function (y) ","x"],"37352a88d14a":["function (y) ","x"]},"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>
