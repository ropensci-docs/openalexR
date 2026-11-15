# Convert keywords from list to data frame

The function converts a list of keywords obtained using `oa_request` or
`oa_fetch(output = "list")` into a data frame/tibble. More on keyword at
\<https://help.openalex.org/hc/en-us/articles/24736201130391-Keywords\>.

## Usage

``` r
keywords2df(data, verbose = TRUE)
```

## Arguments

- data:

  List. Output of `oa_request`.

- verbose:

  Logical. If TRUE, print information about the data frame conversion
  process. Defaults to TRUE.

## Value

a data.frame.

## Examples

``` r
if (FALSE) { # \dontrun{

x <- oa_fetch(
  entity = "keywords",
  options = list(sample = 5),
  output = "list"
)

df <- oa2df(x, entity = "keywords")

df
} # }
```
