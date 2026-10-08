# Convert OpenAlex collection of authors' records from list format to data frame

It converts bibliographic collection of authors' records gathered from
OpenAlex database <https://openalex.org/> into data frame. The function
converts a list of authors' records obtained using `oa_request` into a
data frame/tibble.

## Usage

``` r
authors2df(data, verbose = TRUE)
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

# Query to search information about all authors affiliated to the University of Naples Federico II
# which have authored at least 100 publications:

# University of Naples Federico II is associated to the OpenAlex id I71267560.


res <- oa_fetch(
  entity = "authors",
  last_known_institutions.id = "I71267560",
  works_count = ">700",
  output = "list"
)

df <- oa2df(res, entity = "authors")

df
} # }
```
