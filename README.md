nneo
====



[![Project Status: WIP - Initial development is in progress, but there has not yet been a stable, usable release suitable for the public.](http://www.repostatus.org/badges/latest/wip.svg)](http://www.repostatus.org/#wip)
[![Build Status](https://travis-ci.org/ropenscilabs/nneo.svg?branch=master)](https://travis-ci.org/ropenscilabs/nneo)
[![codecov.io](https://codecov.io/github/ropenscilabs/nneo/coverage.svg?branch=master)](https://codecov.io/github/ropenscilabs/nneo?branch=master)
[![rstudio mirror downloads](https://cranlogs.r-pkg.org/badges/nneo)](https://github.com/metacran/cranlogs.app)


`nneo` - R client for [NEON API](http://data.neonscience.org/data-api)

Routes and R methods

* `/products` - `nneo_products()`/`nneo_product()`
* `/sites` - `nneo_sites()`/`nneo_site()`
* `/locations` - `nneo_locations()`/`nneo_location()`
* `/data` - `nneo_data()`/`nneo_file()`

## installation


```r
devtools::install_github("ropenscilabs/nneo")
```


```r
library("nneo")
```

## list products


```r
nneo_products()
#> # A tibble: 181 × 14
#>     keywords productStatus
#> *     <list>         <chr>
#> 1  <chr [7]>        FUTURE
#> 2  <chr [8]>        ACTIVE
#> 3  <chr [8]>        FUTURE
#> 4  <chr [1]>        FUTURE
#> 5     <NULL>        ACTIVE
#> 6  <chr [2]>        FUTURE
#> 7     <NULL>        ACTIVE
#> 8     <NULL>        FUTURE
#> 9  <chr [6]>        FUTURE
#> 10 <chr [9]>        FUTURE
#> # ... with 171 more rows, and 12 more variables: productDescription <chr>,
#> #   productCode <chr>, productCategory <chr>, themes <list>,
#> #   productScienceTeam <chr>, productName <chr>,
#> #   productCodePresentation <chr>, specs <list>,
#> #   productScienceTeamAbbr <chr>, productCodeLong <chr>,
#> #   productHasExpanded <lgl>, siteCodes <list>
```

## list sites


```r
nneo_sites()
#> # A tibble: 53 × 11
#>                          siteDescription siteLongitude    siteType
#> *                                  <chr>         <dbl>       <chr>
#> 1                           Jornada LTER    -106.84254 RELOCATABLE
#> 2      Ordway-Swisher Biological Station     -81.99343        CORE
#> 3  Niwot Ridge Mountain Research Station    -105.58237        CORE
#> 4                                  Healy    -149.21334 RELOCATABLE
#> 5                 LBJ National Grassland     -97.57000        CORE
#> 6           Rocky Mountain National Park    -105.54592 RELOCATABLE
#> 7               Blandy Experimental Farm     -78.07164 RELOCATABLE
#> 8                               Sterling    -103.02930 RELOCATABLE
#> 9                                 Toolik    -149.37047        CORE
#> 10      Konza Prairie Biological Station     -96.56309        CORE
#> # ... with 43 more rows, and 8 more variables: stateName <chr>,
#> #   stateCode <chr>, siteLatitude <dbl>, domainName <chr>,
#> #   domainCode <chr>, siteCode <chr>, dataProducts <list>, siteName <chr>
```

## list a location


```r
res <- nneo_location("HARV")
names(res)
#>  [1] "locationChildren"         "locationElevation"       
#>  [3] "locationDescription"      "locationType"            
#>  [5] "locationProperties"       "locationDecimalLatitude" 
#>  [7] "locationName"             "domainCode"              
#>  [9] "siteCode"                 "locationDecimalLongitude"
#> [11] "locationParent"
```

## data


```r
nneo_data(product_code = "DP1.00098.001", site_code = "HEAL",
          year_month = "2016-05")
#> $status
#> [1] 200
#> 
#> $data
#> $data$files
#> # A tibble: 4 × 4
#>        crc32                                                       name
#> *      <chr>                                                      <chr>
#> 1 0xb2506dd5  NEON.D19.HEAL.DP1.00098.001.00000.003.000.001.RH_1min.csv
#> 2 0xd6e86fd9  NEON.D19.HEAL.DP1.00098.001.00000.000.040.001.RH_1min.csv
#> 3  0x560b9ba NEON.D19.HEAL.DP1.00098.001.00000.003.000.030.RH_30min.csv
#> 4 0x78a83344 NEON.D19.HEAL.DP1.00098.001.00000.000.040.030.RH_30min.csv
#> # ... with 2 more variables: url <chr>, size <chr>
#> 
#> $data$productCode
#> [1] "DP1.00098.001"
#> 
#> $data$urls
#> [1] "http://data.neonscience.org:80/api/v0/data/DP1.00098.001/HEAL/2016-05/NEON.D19.HEAL.DP1.00098.001.00000.003.000.001.RH_1min.csv?package=basic" 
#> [2] "http://data.neonscience.org:80/api/v0/data/DP1.00098.001/HEAL/2016-05/NEON.D19.HEAL.DP1.00098.001.00000.000.040.001.RH_1min.csv?package=basic" 
#> [3] "http://data.neonscience.org:80/api/v0/data/DP1.00098.001/HEAL/2016-05/NEON.D19.HEAL.DP1.00098.001.00000.003.000.030.RH_30min.csv?package=basic"
#> [4] "http://data.neonscience.org:80/api/v0/data/DP1.00098.001/HEAL/2016-05/NEON.D19.HEAL.DP1.00098.001.00000.000.040.030.RH_30min.csv?package=basic"
#> 
#> $data$month
#> [1] "2016-05"
#> 
#> $data$siteCode
#> [1] "HEAL"
```

## Meta

* Please [report any issues or bugs](https://github.com/ropenscilabs/nneo/issues).
* License: MIT
* Get citation information for `nneo` in R doing `citation(package = nneo')`
* Please note that this project is CONDUCT.md). By participating in this project you agree to abide by its terms.

[![ropensci_footer](http://ropensci.org/public_images/github_footer.png)](http://ropensci.org)
