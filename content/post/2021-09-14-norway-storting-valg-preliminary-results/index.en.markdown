---
title: Norway Storting Valg
author: Daniyal
date: '2021-09-14'
slug: norway-storting-valg-preliminary-results
categories:
  - R
tags:
  - R Markdown
  - GGparliament
  - GGplot
subtitle: 'Preliminary Results'
summary: 'Preliminary Results'
authors: []
lastmod: '2021-09-14T12:00:34+02:00'
featured: no
image:
  caption: ''
  focal_point: ''
  preview_only: no
projects: []
---

***

#### Election Date: 13 Sept,2021

#### Analysis Date: 14 Sept,2021

***

Loading Libraries


```r
library(readxl) # for reading excel file
library(tidyverse) # for data wrangling
library(ggplot2) # for plotting
library(ggparliament) # for parliament plot
library(dplyr) # for pipes
```

***

Read excel file:

read_excel("...")



***

Take data and transform for ggparliament


```r
No_Valg <- parliament_data(election_data = Valg,
                    type = "semicircle",
                    parl_rows = 4,
                    party_seats = Valg$seats)
```

***

Plotting the data.


```r
ggplot(No_Valg, aes(x, y, colour = party_long)) +
    geom_parliament_seats() + 
    geom_highlight_government(government == 1) +
    # add bar showing proportion of seats by party in legislature
    geom_parliament_bar(colour = colour, party = party_long) + 
    theme(legend.position = 'bottom'
          ) +
    labs(colour = NULL, 
         title = "Norway Storting Valg 2021",
         subtitle = "Preliminary results") +
    scale_colour_manual(values = No_Valg$colour,
                        limits = No_Valg$party_long)
```

<img src="{{< blogdown/postref >}}index.en_files/figure-html/unnamed-chunk-4-1.png" width="1344" />
