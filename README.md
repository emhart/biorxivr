## biorxiv

##### *Quickly search and get details about papers on the pre-print server [biorxiv.org](http://www.biorxiv.org) in R*

**Quick Start**

Currently the package is only available on github and installable via `devtools`

```r
library(devtools)
install_github("emhart/biorxiv")
library(biorxiv)
```

**Searching**

The search functionality comes from the general search form interface, so the search may not be at the granularity you desire without further parsing of results.


```r
bxCC <- bx_search("climate change",limit = 10)
summary(bxCC)
```

```
## Search term: climate change 
## Number of results returned: 10 
## Number of results found: 236
```

This will return a search results object that has the URL's for your search results.  If you want to get details about all your search results we can extract basic features like DOI, Authors, e-mails, title, abstract text, date as well as metrics on views and downloads.


```r
bxCCDetails <-  bx_extract(bxCC)

bxCCDetails[[3]]
```

```
## $authors
## $authors$names
## [1] "Ben Phillips"
## 
## $authors$email
## [1] "phillipsb@unimelb.edu.au"
## 
## 
## $paper
## $paper$title
## [1] "Evolutionary processes make invasion speed difficult to predict"
## 
## $paper$abstract
## [1] "A capacity to predict the spread rate of populations is critical for understanding the impacts of climate change and invasive species. Despite sophisticated theory describing how populations spread, the prediction of spread rate remains a formidable challenge. As well as the inherent stochasticity in the spread process, spreading populations are subject to strong evolutionary forces (operating on dispersal and reproductive rates) that can cause accelerating spread. Despite these strong evolutionary forces, serial founder events and drift on the expanding range edge mean that evolutionary trajectories in the invasion vanguard may be highly stochastic. Here I develop a model of spatial spread in continuous space that incorporates evolution of continuous traits under a quantitative genetic model of inheritance. I use this model to investigate the potential role of evolution on the variation in spread rate between replicate model realisations. Models incorporating evolution exhibited more than four times the variance in spread rate across replicate invasions compared with non-evolving scenarios. Results suggest that the majority of this increase in variation is driven by evolutionary stochasticity on the invasion front rather than initial founder events: in many cases evolutionary stochasticity on the invasion front contributed more than 90% of the variance in spread rate over 30 generations. Our uncertainty around predicted spread rates -- whether for invasive species or those shifting under climate change -- may be much larger than we expect when the spreading population contains heritable variation in rates of dispersal and reproduction."
## 
## $paper$date
## [1] "2015-01-11"
## 
## $paper$DOI
## [1] "10.1101/013680"
## 
## $paper$fulltext_url
## [1] "http://www.biorxiv.org/content/biorxiv/early/2015/01/11/013680.full.pdf"
## 
## 
## $metrics
##         date Abstract PDF
## 1 2015-01-01      230  43
## 
## attr(,"class")
## [1] "biorxiv_paper"
```

There's also some basic plotting functionality that will allow you plot views and downloads

Plot views

```r
plot(bxCCDetails[[3]],type="abs")
```

![plot of chunk plotting views](figure/plotting views-1.png) 

Plot downloads

```r
plot(bxCCDetails[[3]],type="dl")
```

![plot of chunk plotting dl](figure/plotting dl-1.png) 

Finally, you can easily download PDF's from all your search results.


```r
bx_download(bxCC,"~/biorxiv_pdfs")
```


