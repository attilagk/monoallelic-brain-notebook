---
layout: default
#featimg: "Q-Dx-RIN-MEST-density-1.png"
---

This article produces a data table for presentation purposes (see results/data-table-for-regression.csv).  Note that these data were used for previous regression analyses.


```r
source("../../src/import-data.R")
```


```r
gene.ids <- unlist(read.csv("../../data/genes.regression.new", as.is = TRUE))
names(gene.ids) <- gene.ids
Y <- data.frame(lapply(get.readcounts(gene.ids)[gene.ids], getElement, "S"))
X <- get.predictors()[1:13]
write.csv(Z <- cbind(Y, X), "../../results/data-table-for-regression.csv")
```
<!-- MathJax scripts -->
<script type="text/javascript" src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML"></script>
