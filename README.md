# EDMAinR - Euclidean Distance Matrix Analysis in R

[![CRAN
version](http://www.r-pkg.org/badges/version/EDMAinR)](http://cran.rstudio.com/web/packages/EDMAinR/index.html)
[![CRAN download
stats](http://cranlogs.r-pkg.org/badges/grand-total/EDMAinR)](https://www.rdocumentation.org/packages/EDMAinR/)
[![License: GPL
v2](https://img.shields.io/badge/License-GPL%20v2-blue.svg)](https://www.gnu.org/licenses/old-licenses/gpl-2.0.en.html)

[![Linux build
Status](https://travis-ci.org/psolymos/EDMAinR.svg?branch=master)](https://travis-ci.org/psolymos/EDMAinR)
[![Windows build
status](https://ci.appveyor.com/api/projects/status/5y5fwgv90f8i84ck?svg=true)](https://ci.appveyor.com/project/psolymos/EDMAinR)
[![codecov](https://codecov.io/gh/psolymos/EDMAinR/branch/master/graph/badge.svg)](https://codecov.io/gh/psolymos/EDMAinR)

> A coordinate‐free approach for comparing biological shapes using
> landmark data

## Install

``` r
if (!require("remotes")) install.packages("remotes")
remotes::install_github("psolymos/EDMAinR")
```

See what is new in the [NEWS](NEWS.md) file.

## License

[GPL-2](https://www.gnu.org/licenses/old-licenses/gpl-2.0.html)

## Contributing

Feedback and contributions are welcome:

  - submit feature request or report issues
    [here](https://github.com/psolymos/EDMAinR/issues),
  - fork the project and submit pull request, see
    [CoC](CODE_OF_CONDUCT.md).

## Usage

``` r
library(EDMAinR)
#> EDMAinR 0.1-3     2020-06-12

file1 <- system.file("extdata/crouzon/Crouzon_P0_Global_MUT.xyz",
    package="EDMAinR")
x1 <- read_xyz(file1)
x1
#> EDMA data: Crouzon P0 MUT
#> 3 dimensions, 47 landmarks, 28 specimens

file2 <- system.file("extdata/crouzon/Crouzon_P0_Global_NON-MUT.xyz",
    package="EDMAinR")
x2 <- read_xyz(file2)
x2
#> EDMA data: Crouzon P0 UNAFF
#> 3 dimensions, 47 landmarks, 31 specimens

B <- 9

fit <- edma_fit(x1, B=B)
fit
#> EDMA nonparametric fit: Crouzon P0 MUT
#> Call: edma_fit(x = x1, B = B)
#> 3 dimensions, 47 landmarks, 28 replicates, 9 bootstrap runs
```

## References

Lele, S. R., 1991. Some comments on coordinate-free and scale-invariant
methods in morphometrics. American Journal of Physical Anthropology
85:407–417. <doi:10.1002/ajpa.1330850405>

Lele, S. R., and Richtsmeier, J. T., 1991. Euclidean distance matrix
analysis: A coordinate-free approach for comparing biological shapes
using landmark data. American Journal of Physical Anthropology
86(3):415–27. <doi:10.1002/ajpa.1330860307>

Lele, S. R., and Richtsmeier, J. T., 1992. On comparing biological
shapes: detection of influential landmarks. American Journal of Physical
Anthropology 87:49–65. <doi:10.1002/ajpa.1330870106>

Lele, S. R., and Richtsmeier, J. T., 1995. Euclidean distance matrix
analysis: confidence intervals for form and growth differences. American
Journal of Physical Anthropology 98:73–86. <doi:10.1002/ajpa.1330980107>

Hu, L., 2007. Euclidean Distance Matrix Analysis of Landmarks Data:
Estimation of Variance. Thesis, Master of Science in Statistics,
Department of Mathematical and Statistical Sciences, University of
Alberta, Edmonton, Alberta, Canada. Pp. 49.
