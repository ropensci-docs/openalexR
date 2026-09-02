# Convert OpenAlex collection of works from list format to data frame

It converts bibliographic collection of works gathered from OpenAlex
database <https://openalex.org/> into data frame. The function converts
a list of works obtained using `oa_request` into a data frame/tibble.

## Usage

``` r
works2df(data, abstract = TRUE, verbose = TRUE)
```

## Arguments

- data:

  List. Output of `oa_request`.

- abstract:

  Logical. If TRUE, the function returns also the abstract of each item.
  Defaults to TRUE.

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

# Query to search all works citing the article:
#  Aria, M., & Cuccurullo, C. (2017). bibliometrix:
#   An R-tool for comprehensive science mapping analysis.
#   Journal of informetrics, 11(4), 959-975.

#  published in 2021.
#  The paper is associated to the OpenAlex id W2755950973.

#  Results have to be sorted by relevance score in a descending order.

query <- oa_query(
  identifier = NULL,
  entity = "works",
  cites = "W2755950973",
  from_publication_date = "2021-01-01",
  to_publication_date = "2021-12-31",
  search = NULL,
  endpoint = "https://api.openalex.org"
)

res <- oa_request(
  query_url = query,
  count_only = FALSE,
  verbose = FALSE
)

df <- oa2df(res, entity = "works")

df
} # }
```
