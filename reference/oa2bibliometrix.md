# Convert OpenAlex collection from data frame to bibliometrix object

It converts bibliographic collections gathered from OpenAlex database
<https://openalex.org/> into a bibliometrix data frame
(<https://www.bibliometrix.org/>) Column names follow
https://images.webofknowledge.com/images/help/WOS/hs_wos_fieldtags.html.

## Usage

``` r
oa2bibliometrix(df)
```

## Arguments

- df:

  is bibliographic collection of works downloaded from OpenAlex.

## Value

a data.frame with class "bibliometrix".

## Details

Use `bibliometrix::convert2df()` (bibliometrix R package) instead.

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
  entity = "works",
  cites = "W2755950973",
  from_publication_date = "2021-10-01",
  to_publication_date = "2021-12-31"
)

res <- oa_request(
  query_url = query,
  count_only = FALSE,
  verbose = FALSE
)

df <- oa2df(res, entity = "works")

M <- oa2bibliometrix(df)
} # }
```
