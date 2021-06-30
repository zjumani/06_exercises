---
title: 'Weekly Exercises #6'
author: "Zahra Jumani"
output: 
  html_document:
    keep_md: TRUE
    toc: TRUE
    toc_float: TRUE
    df_print: paged
    code_download: true
---





```r
library(tidyverse)     # for data cleaning and plotting
```

```
## ── Attaching packages ─────────────────────────────────────── tidyverse 1.3.0 ──
```

```
## ✓ ggplot2 3.3.2     ✓ purrr   0.3.4
## ✓ tibble  3.1.2     ✓ dplyr   1.0.2
## ✓ tidyr   1.1.3     ✓ stringr 1.4.0
## ✓ readr   1.4.0     ✓ forcats 0.5.0
```

```
## ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
## x dplyr::filter() masks stats::filter()
## x dplyr::lag()    masks stats::lag()
```

```r
library(gardenR)       # for Lisa's garden data
library(lubridate)     # for date manipulation
```

```
## 
## Attaching package: 'lubridate'
```

```
## The following objects are masked from 'package:base':
## 
##     date, intersect, setdiff, union
```

```r
library(openintro)     # for the abbr2state() function
```

```
## Loading required package: airports
```

```
## Loading required package: cherryblossom
```

```
## Loading required package: usdata
```

```r
library(palmerpenguins)# for Palmer penguin data
library(maps)          # for map data
```

```
## 
## Attaching package: 'maps'
```

```
## The following object is masked from 'package:purrr':
## 
##     map
```

```r
library(ggmap)         # for mapping points on maps
```

```
## Google's Terms of Service: https://cloud.google.com/maps-platform/terms/.
```

```
## Please cite ggmap if you use it! See citation("ggmap") for details.
```

```r
library(gplots)        # for col2hex() function
```

```
## 
## Attaching package: 'gplots'
```

```
## The following object is masked from 'package:stats':
## 
##     lowess
```

```r
library(RColorBrewer)  # for color palettes
library(sf)            # for working with spatial data
```

```
## Linking to GEOS 3.4.2, GDAL 2.4.2, PROJ 4.8.0
```

```r
library(leaflet)       # for highly customizable mapping
library(ggthemes)      # for more themes (including theme_map())
library(plotly)        # for the ggplotly() - basic interactivity
```

```
## 
## Attaching package: 'plotly'
```

```
## The following object is masked from 'package:ggmap':
## 
##     wind
```

```
## The following object is masked from 'package:ggplot2':
## 
##     last_plot
```

```
## The following object is masked from 'package:stats':
## 
##     filter
```

```
## The following object is masked from 'package:graphics':
## 
##     layout
```

```r
library(gganimate)     # for adding animation layers to ggplots
library(transformr)    # for "tweening" (gganimate)
```

```
## 
## Attaching package: 'transformr'
```

```
## The following object is masked from 'package:sf':
## 
##     st_normalize
```

```r
library(shiny)         # for creating interactive apps
library(patchwork)     # for nicely combining ggplot2 graphs  
library(gt)            # for creating nice tables
```

```
## 
## Attaching package: 'gt'
```

```
## The following object is masked from 'package:openintro':
## 
##     sp500
```

```r
library(rvest)         # for scraping data
```

```
## Loading required package: xml2
```

```
## 
## Attaching package: 'rvest'
```

```
## The following object is masked from 'package:gt':
## 
##     html
```

```
## The following object is masked from 'package:purrr':
## 
##     pluck
```

```
## The following object is masked from 'package:readr':
## 
##     guess_encoding
```

```r
library(robotstxt)     # for checking if you can scrape data
theme_set(theme_minimal())
```


```r
# Lisa's garden data
data("garden_harvest")

#COVID-19 data from the New York Times
covid19 <- read_csv("https://raw.githubusercontent.com/nytimes/covid-19-data/master/us-states.csv")
```

```
## 
## ── Column specification ────────────────────────────────────────────────────────
## cols(
##   date = col_date(format = ""),
##   state = col_character(),
##   fips = col_character(),
##   cases = col_double(),
##   deaths = col_double()
## )
```

## Put your homework on GitHub!

Go [here](https://github.com/llendway/github_for_collaboration/blob/master/github_for_collaboration.md) or to previous homework to remind yourself how to get set up. 

Once your repository is created, you should always open your **project** rather than just opening an .Rmd file. You can do that by either clicking on the .Rproj file in your repository folder on your computer. Or, by going to the upper right hand corner in R Studio and clicking the arrow next to where it says Project: (None). You should see your project come up in that list if you've used it recently. You could also go to File --> Open Project and navigate to your .Rproj file. 

## Instructions

* Put your name at the top of the document. 

* **For ALL graphs, you should include appropriate labels.** 

* Feel free to change the default theme, which I currently have set to `theme_minimal()`. 

* Use good coding practice. Read the short sections on good code with [pipes](https://style.tidyverse.org/pipes.html) and [ggplot2](https://style.tidyverse.org/ggplot2.html). **This is part of your grade!**

* **NEW!!** With animated graphs, add `eval=FALSE` to the code chunk that creates the animation and saves it using `anim_save()`. Add another code chunk to reread the gif back into the file. See the [tutorial](https://animation-and-interactivity-in-r.netlify.app/) for help. 

* When you are finished with ALL the exercises, uncomment the options at the top so your document looks nicer. Don't do it before then, or else you might miss some important warnings and messages.

## Your first `shiny` app 

  1. This app will also use the COVID data. Make sure you load that data and all the libraries you need in the `app.R` file you create. Below, you will post a link to the app that you publish on shinyapps.io. You will create an app to compare states' cumulative number of COVID cases over time. The x-axis will be number of days since 20+ cases and the y-axis will be cumulative cases on the log scale (`scale_y_log10()`). We use number of days since 20+ cases on the x-axis so we can make better comparisons of the curve trajectories. You will have an input box where the user can choose which states to compare (`selectInput()`) and have a submit button to click once the user has chosen all states they're interested in comparing. The graph should display a different line for each state, with labels either on the graph or in a legend. Color can be used if needed. 
  
## Warm-up exercises from tutorial

  2. Read in the fake garden harvest data. Find the data [here](https://github.com/llendway/scraping_etc/blob/main/2020_harvest.csv) and click on the `Raw` button to get a direct link to the data. 

```r
fake_garden_harvest <- read_csv("https://raw.githubusercontent.com/llendway/scraping_etc/main/2020_harvest.csv")
```

```
## Warning: Missing column names filled in: 'X2' [2], 'X3' [3], 'X4' [4], 'X5' [5],
## 'X6' [6]
```

```
## 
## ── Column specification ────────────────────────────────────────────────────────
## cols(
##   `This is my awesome data!` = col_logical(),
##   X2 = col_character(),
##   X3 = col_character(),
##   X4 = col_character(),
##   X5 = col_character(),
##   X6 = col_character()
## )
```
  
  3. Read in this [data](https://www.kaggle.com/heeraldedhia/groceries-dataset) from the kaggle website. You will need to download the data first. Save it to your project/repo folder. Do some quick checks of the data to assure it has been read in appropriately.

```r
groceries <- read_csv("Groceries_dataset.csv")
```

```
## 
## ── Column specification ────────────────────────────────────────────────────────
## cols(
##   Member_number = col_double(),
##   Date = col_character(),
##   itemDescription = col_character()
## )
```

  4. CHALLENGE(not graded): Write code to replicate the table shown below (open the .html file to see it) created from the `garden_harvest` data as best as you can. When you get to coloring the cells, I used the following line of code for the `colors` argument:
  

```r
colors = scales::col_numeric(
      palette = paletteer::paletteer_d(
        palette = "RColorBrewer::YlGn"
      ) %>% as.character()
```




  5. Create a table using `gt` with data from your project or from the `garden_harvest` data if your project data aren't ready.

```r
g2 <- garden_harvest %>%
  filter(vegetable %in% c("lettuce", "spinach")) %>%
  group_by(vegetable, date) %>%
  summarize(daily_harvest_lb = sum(weight)*0.00220462) %>%
  mutate(cum_harvest_lb = cumsum(daily_harvest_lb)) %>%
  gt(
    groupname_col = "date"
  ) %>%
  tab_header(
    title = "Daily harvest of Lettuce and Spinach",
    subtitle = md("Cumulative Weights of Spinach and Lettuce")
  ) %>%
  cols_label(
    vegetable = "Vegetable",
    daily_harvest_lb = "Daily Harvest (lb)",
    cum_harvest_lb= "Cumulative Harvest (lb)"
  ) %>%
  data_color(columns = vars(cum_harvest_lb),
             colors =  scales::col_numeric(palette = "magma",
                                           domain = NULL)) %>%
  tab_options(column_labels.background.color = "navy")
```

```
## `summarise()` regrouping output by 'vegetable' (override with `.groups` argument)
```

```
## Warning: `columns = vars(...)` has been deprecated in gt 0.3.0:
## * please use `columns = c(...)` instead
```
  
  6. Use `patchwork` operators and functions to combine at least two graphs using your project data or `garden_harvest` data if your project data aren't read.

```r
graph1 <- garden_harvest %>%
  filter(vegetable == "tomatoes") %>%
  mutate(tomatoes_title = str_to_title(variety)) %>%
  mutate(weightlbs = weight * .00220462) %>% #creating a new variable that converts the weight to pounds
  mutate(tomatoes2 = fct_reorder(tomatoes_title, weightlbs, .desc = FALSE)) %>% #reordering tomatoes in increasing median weight
  ggplot(aes(x = weightlbs, y = tomatoes2)) + 
  geom_boxplot() + # Specifying that I want to build boxplots
  theme_classic() + # Choosing a theme
  theme(plot.title.position = "plot",
        plot.caption = element_text(size = 10, face = "italic")) +
  labs(title = "Tomato Harvest Weight Distributions (lbs)",
       caption = "Visualization Created by Brian Lee",
       x = "", y = "") +
  geom_vline(aes(xintercept = median(weightlbs, na.rm = TRUE)), color = "royalblue") # Adding a vertical line indicating the median weight for all tomatoes

graph2 <- garden_harvest %>%
  mutate(weightlb = weight * .00220462) %>%
    filter(vegetable == "beets",
           variety %in% c("Sweet Merlin", "Gourmet Golden")) %>%
  group_by(variety, date) %>%
  summarize(daily_weight = sum(weightlb)) %>%
  mutate(cumWeight = cumsum(daily_weight)) %>%
  ggplot(aes(x = date, y = cumWeight, color = variety)) +
  geom_line() +
  labs(title = "The Cumulative Weight (lb) of Gourmet Golden & Sweet Merlin beets", x = "", y = "")
```

```
## `summarise()` regrouping output by 'variety' (override with `.groups` argument)
```
  

**DID YOU REMEMBER TO UNCOMMENT THE OPTIONS AT THE TOP?**
