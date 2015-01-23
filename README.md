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
bxEco <- bx_search("Ecology",limit = 10)
summary(bxEco)
```

```
## Search term: Ecology 
## Number of results returned: 10 
## Number of results found: 110
```

This will return a search results object that has the URL's for your search results.  If you want to get details about all your search results we can extract basic features like DOI, Authors, e-mails, title, abstract text, date as well as metrics on views and downloads.


```r
bxEcoDetails <-  bx_extract(bxEco)

bxEcoDetails[[1]]
```

```
## $authors
## $authors$names
## [1] "Stefan Siebert"          "Freya E. Goetz"         
## [3] "Samuel H. Church"        "Pathikrit Bhattacharyya"
## [5] "Felipe Zapata"           "Steven H.D. Haddock"    
## [7] "Casey W. Dunn"          
## 
## 
## $paper
## $paper$title
## [1] "Stem cells in a colonial animal with localized growth zones"
## 
## $paper$abstract
## [1] "Siphonophores (Hydrozoa) have unparalleled colony-level complexity, precision of organization, and functional specialization between zooids (i.e., the units that make up colonies). Previous work has shown that, unlike other colonial animals, most growth in siphonophores is restricted to one or two well-defined growth zones that are the sites of both elongation and zooid budding. To understand this unique growth at the cellular level, we characterize the distribution of interstitial stem cells (i-cells) in the siphonophore Nanomia bijuga. Within the colony we find that i-cells are present at the tips of the growth zones, at well-defined sites where new zooid buds will arise, and in the youngest zooid buds. As each zooid matures, i-cells become progressively restricted to specific regions until they are mostly absent from the oldest zooids. We find no evidence of the migratory i-cells that have been observed in colonial cnidarian relatives. The restriction of i-cells to particular developing structures and sites of growth suggest a plant-like model of growth for siphonophores, where the growth zones function much like meristems. This spatial restriction of stem cells could also explain the precision of colony-level organization in siphonophores as a consequence of restricted growth potential."
## 
## $paper$date
## [1] "2014-01-06"
## 
## $paper$DOI
## [1] "10.1101/001685"
## 
## $paper$fulltext_url
## [1] "http://www.biorxiv.org/content/biorxiv/early/2014/01/06/001685.full.pdf"
## 
## 
## $metrics
##          date Abstract PDF
## 1  2014-01-01      202  99
## 2  2014-02-01      250  71
## 3  2014-03-01       39  27
## 4  2014-04-01       70  22
## 5  2014-05-01       79  35
## 6  2014-06-01       46  46
## 7  2014-07-01       69  45
## 8  2014-08-01       35  12
## 9  2014-09-01       62  18
## 10 2014-10-01       56  46
## 11 2014-11-01       61  22
## 12 2014-12-01       57  21
## 13 2015-01-01       38  13
## 
## attr(,"class")
## [1] "biorxiv_paper"
```

There's also some basic plotting functionality that will allow you plot views and downloads

Plot views

```r
plot(bxEcoDetails[[1]],type="abs")
```

![plot of chunk plotting views](figure/plotting views-1.png) 

Plot downloads

```r
plot(bxEcoDetails[[1]],type="dl")
```

![plot of chunk plotting dl](figure/plotting dl-1.png) 

Finally, you can easily download PDF's from all your search results.


```r
bx_download(bxEco,"~/biorxiv_pdfs")
```


