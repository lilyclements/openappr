
<!-- README.md is generated from README.Rmd. Please edit that file -->

# openappr

<!-- badges: start -->

[![R-CMD-check](https://github.com/IDEMSInternational/openappr/workflows/R-CMD-check/badge.svg)](https://github.com/IDEMSInternational/openappr/actions)
[![Codecov test
coverage](https://codecov.io/gh/IDEMSInternational/openappr/branch/main/graph/badge.svg)](https://app.codecov.io/gh/IDEMSInternational/openappr?branch=main)
[![Lifecycle:
experimental](https://img.shields.io/badge/lifecycle-experimental-orange.svg)](https://lifecycle.r-lib.org/articles/stages.html#experimental)
[![Project Status: WIP – Initial development is in progress, but there
has not yet been a stable, usable release suitable for the
public.](https://www.repostatus.org/badges/latest/wip.svg)](https://www.repostatus.org/#wip)
[![CRAN
status](https://www.r-pkg.org/badges/version/openappr)](https://CRAN.R-project.org/package=openappr)
[![license](https://img.shields.io/badge/license-LGPL%20(%3E=%203)-lightgrey.svg)](https://www.gnu.org/licenses/lgpl-3.0.en.html)
<!-- badges: end -->

The goal of `openappr` is to import app data from the open-app builder.

## Installation

You can install the development version of openappr from
[GitHub](https://github.com/) with:

``` r
# install.packages("devtools")
devtools::install_github("IDEMSInternational/openappr")
```

## Example

The use of `openappr` begins by establishing a connection to the
PostgresSQL website. This can be achieved using the
`get_app_connection()` function, which is simply a wrapper to the
`dbconnect` function from the `DBI` package. By using the
`get_app_connection()` function, the connection is stored in the package
environment, ensuring that subsequent calls to retrieve the app data
uses this connection.

The primary functionality of `openappr` revolves around two main types
of data retrieval:

- Notification Data: Users can retrieve notification-related data using
  the function `get_nf_data()`. This function is optimised for quick
  access to notifications generated by the system, structured to provide
  immediate insights into user engagement and system performance.

- User Data: The function `get_user_data()` is designed to access
  detailed information about users. This is particularly useful for
  analysis that requires a deep dive into user behaviour and
  demographics.

Both functions utilise the underlying capabilities of the `RPostgres`
package but are tailored to provide a more user-friendly interface that
requires minimal SQL knowledge.

This is a basic example which shows you how can import notification and
user data from open-app builder into R:

``` r
# Setting up the database connection
openappr::set_app_connection(host = "YOUR_DATABASE_HOST", 
                              port = "YOUR_DATABASE_PORT", 
                              dbname = "YOUR_DATABASE_NAME",
                              user = "YOUR_USERNAME", 
                              password = "YOUR_PASSWORD")

# Fetching notification data
notifications <- openappr::get_nf_data()

# Fetching user data
users <- openappr::get_user_data()
```
