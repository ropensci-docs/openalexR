# Convert OpenAlex collection of institutions' records from list format to data frame

It converts bibliographic collection of institutions' records gathered
from OpenAlex database <https://openalex.org/> into data frame. The
function converts a list of institutions' records obtained using
`oa_request` into a data frame/tibble.

## Usage

``` r
institutions2df(data, verbose = TRUE)
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

res <- oa_fetch(
  entity = "institutions",
  country_code = "it",
  type = "education",
  output = "list"
)

oa2df(res, entity = "institutions")
} # }
```
