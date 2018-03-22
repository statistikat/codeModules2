codeModules
================

About
-----

This R package consists of several [shiny modules](https://shiny.rstudio.com/articles/modules.html) that return R code in the form of `reactive` characters. All those modules represent common operations regarding

-   Import of data (`read.csv`, `read.xlsx`, `data()`, ...)
-   ~~Manipulation of data (either with `dplyr` or `data.table`)~~
-   ~~export of data (`write.csv`, `read.xlsx`, ...)~~

Usage
-----

Always save the output from `callModule` into a variable when working with modules from this package. The modules can then be parsed as R code using `eval(parse(text = code()))`.

``` r
## context: server.R
code <- callModule(libData, assignTo = "dt")
output$table <- renderTable({
  eval(parse(text = code()))
  return(dt)
})
```

Implemented Modules
-------------------

-   **libData**: read data from `R` packages using `utils::data`
-   **readData**: read data from a file using `read.csv`, `read.xlsx` or others depending on the fileextension.