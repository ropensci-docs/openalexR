# Convert OpenAlex collection of concepts' records from list format to data frame

It converts bibliographic collection of concepts' records gathered from
OpenAlex database <https://openalex.org/> into data frame. The function
converts a list of concepts' records obtained using `oa_request` into a
data frame/tibble.

## Usage

``` r
concepts2df(data, verbose = TRUE)
```

## Arguments

- data:

  List. Output of `oa_request`.

- verbose:

  Logical. If TRUE, print information about the data frame conversion
  process. Defaults to TRUE.

## Value

a data.frame.

For more extensive information about OpenAlex API, please visit:
\<https://developers.openalex.org/\>

## Examples

``` r
if (FALSE) { # \dontrun{

# Query to search information about all Italian educational institutions


res <- oa_query(
  entity = "concepts",
  display_name.search = "electrodynamics",
  output = "list"
)

df <- oa2df(res, entity = "concepts")

df
} # }
```
