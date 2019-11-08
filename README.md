# EDMAinR - Euclidean Distance Matrix Analysis in R

[![CRAN version](http://www.r-pkg.org/badges/version/EDMAinR)](http://cran.rstudio.com/web/packages/EDMAinR/index.html)
[![CRAN download stats](http://cranlogs.r-pkg.org/badges/grand-total/EDMAinR)](https://www.rdocumentation.org/packages/EDMAinR/)
[![Linux build Status](https://travis-ci.org/psolymos/EDMAinR.svg?branch=master)](https://travis-ci.org/psolymos/EDMAinR)
[![Windows build status](https://ci.appveyor.com/api/projects/status/5y5fwgv90f8i84ck?svg=true)](https://ci.appveyor.com/project/psolymos/EDMAinR)
[![License: GPL v2](https://img.shields.io/badge/License-GPL%20v2-blue.svg)](https://www.gnu.org/licenses/old-licenses/gpl-2.0.en.html)

> A coordinate‐free approach for comparing biological shapes using landmark data

## Install

```R
devtools::install_github("psolymos/EDMAinR")
```

## Usage

```R
K <- 3 # number of landmarks
D <- 2 # dimension, 2 or 3

sig <- 0.2
rho <- -0.5
SigmaK <- sig^2*diag(1, K, K) + sig^2*rho*(1-diag(1, K, K))

M <- matrix(c(0,1,0,0,0,1), 3, 2)
M[,1] <- M[,1] - mean(M[,1])
M[,2] <- M[,2] - mean(M[,2])

n <- 1000
Z <- matrix(nrow = n * K, ncol = D)
for (i in 1:n) {
    Z[((i - 1) * K + 1):(i * K), ] <- matrix(rnorm(K * D), nrow = K,
        ncol = D)
}
C <- chol(SigmaK)
X <- matrix(nrow = n * K, ncol = D)
for (i in 1:n) {
    X[((i - 1) * K + 1):(i * K), ] <- crossprod(C, Z[((i - 1) * K + 1):(i *
        K), ]) + M
}

(fit <- edma_fit(X, n, K, D))
SigmaK_fit(fit, "sig")$optim
SigmaK_fit(fit, "sig_rho")$optim

```

## References

Lele, S. R., and Richtsmeier, J. T., 1991.
Euclidean distance matrix analysis: A coordinate‐free approach for 
comparing biological shapes using landmark data.
American Journal of Physical Anthropology 86(3):415--27.
DOI: [10.1002/ajpa.1330860307](https://doi.org/10.1002/ajpa.1330860307).

Hu, L., 2007. Euclidean Distance Matrix Analysis of Landmarks Data:
Estimation of Variance. Thesis, Master of Science in Statistics,
Department of Mathematical and Statistical Sciences, 
University of Alberta, Edmonton, Alberta, Canada. Pp. 49.
