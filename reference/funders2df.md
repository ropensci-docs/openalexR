# Convert OpenAlex collection of funders' records from list format to data frame

It converts bibliographic collection of funders' records gathered from
OpenAlex database <https://openalex.org/> into data frame. The function
converts a list of funders' records obtained using `oa_request` into a
data frame/tibble.

## Usage

``` r
funders2df(data, verbose = TRUE)
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

# Get funders located in Canada with more than 100,000 citations

res <- oa_request(
  "https://api.openalex.org/funders?filter=country_code:ca,cited_by_count:>100000"
)

df <- oa2df(res, entity = "funders")

df
} # }
```
