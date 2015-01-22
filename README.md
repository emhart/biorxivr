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
## Number of results found: 235
```

This will return a search results object that has the URL's for your search results.  If you want to get details about all your search results we can extract basic features like DOI, Authors, e-mails, title, abstract text, date as well as metrics on views and downloads.


```r
bxCCDetails <-  bx_extract(bxCC)

bxCCDetails[[1]]
```

```
## $authors
## $authors$names
## [1] "Edmund Hart"      "Nicholas Gotelli"
## 
## 
## $paper
## $paper$title
## [1] "Climate change triggers morphological and life-history evolution in response to predators"
## 
## $paper$abstract
## [1] "Although climate change is expected to reorganize entire communities, this restructuring might reflect either direct ecological or evolutionary responses to abiotic conditions or indirect effects mediated through altered species interactions. We tested the hypothesis that changes in trophic interaction strength due to altered predator abundance have a cascading evolutionary response in a prey species (Daphnia pulex). Using a multiyear / multigenerational field experiment, we manipulated 12 open aquatic mesocosms to simulate hydrological conditions under climate change. After a three-year press manipulation, we collected Daphnia pulex from each pond and raised them in a common garden. Using quantitative genetic methods, we measured a series of quantitative traits every other day on 108 individuals for eight weeks. There was a significant decrease in tail spine length and population growth rate in groups exposed to the most extreme future climate scenarios. Structural equation models demonstrated that trait changes were best explained as an indirect effect of climate change treatments mediated through changes in predator abundance. Our results suggest climate change can trigger a cascade of ecological and evolutionary forces by reducing predator density, which in turn acts as a selective force leading to evolutionary change in prey morphology and life history."
## 
## $paper$date
## [1] "2013-12-10"
## 
## $paper$DOI
## [1] "10.1101/001263"
## 
## $paper$fulltext_url
## [1] "http://www.biorxiv.org/content/biorxiv/early/2013/12/05/001263.full.pdf"
## 
## 
## $metrics
##          date Abstract PDF
## 1  2013-12-01      146  35
## 2  2014-01-01       34  30
## 3  2014-02-01       25  17
## 4  2014-03-01       34   2
## 5  2014-04-01       17  30
## 6  2014-05-01       36   5
## 7  2014-06-01       22   9
## 8  2014-07-01       56  15
## 9  2014-08-01       35   8
## 10 2014-09-01       64  11
## 11 2014-10-01       43  20
## 12 2014-11-01       24  12
## 13 2014-12-01       25  14
## 14 2015-01-01        9   2
## 
## attr(,"class")
## [1] "biorxiv_paper"
```

There's also some basic plotting functionality that will allow you plot views and downloads

Plot views

```r
plot(bxCCDetails[[1]],type="abs")
```

![plot of chunk plotting views](figure/plotting views-1.png) 

Plot downloads

```r
plot(bxCCDetails[[1]],type="dl")
```

![plot of chunk plotting dl](figure/plotting dl-1.png) 


