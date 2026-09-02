# Convert OpenAlex collection of publishers' records from list format to data frame

It converts bibliographic collection of publishers' records gathered
from OpenAlex database <https://openalex.org/> into data frame. The
function converts a list of publishers' records obtained using
`oa_request` into a data frame/tibble.

## Usage

``` r
publishers2df(data, verbose = TRUE)
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

# Get publishers located in Canada with more than 100,000 citations

res <- oa_request(
  "https://api.openalex.org/publishers?filter=country_codes:ca"
)

df <- oa2df(res, entity = "publishers")

df
} # }
```
