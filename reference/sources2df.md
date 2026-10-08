# Convert OpenAlex collection of sources' records from list format to data frame

It converts bibliographic collection of sources' records gathered from
OpenAlex database <https://openalex.org/> into data frame. The function
converts a list of sources' records obtained using `oa_request` into a
data frame/tibble.

## Usage

``` r
sources2df(data, verbose = TRUE)
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

# Get sources from Nature

res <- oa_request(
  "https://api.openalex.org/sources?search=nature"
)

df <- oa2df(res, entity = "sources")

df
} # }
```
