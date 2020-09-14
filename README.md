# dbplyrExtra
A set of functions adding features to dbplyr

# Installation
This package is not yet on CRAN, so install using

`remotes::install_github("EeethB/dbplyrExtra")`

# Motivation
[`dbplyr`](https://dbplyr.tidyverse.org/) is a fantastic package, which allows users to apply `dplyr` verbs to database tables. The verbs are translated into SQL, the table gets queried, and results are returned as a data frame. Often this is useful when a whole database table is too large to fit into the physical memory of a local machine, but a summary or subset does fit. While this can be wonderfully helpful, there are a few difficulties:

  - Troubleshooting can be difficult, since it's not always possible to break up a pipeline due to size constraints.
  - Often the data wrangling portion of an analysis requires several steps before fitting into physical memory. This is nearly impossible to do with a single `dbplyr` pipeline.
  
# Solution
`dbplyrExtra` solves this by adding the function `as_db_tibble()`. To move a `dbplyr` object into physical memory, it must be passed to `as_tibble()`. On the other hand, if a table is still too large, `as_db_tibble()` executes the generated SQL *and writes results to the database*.

