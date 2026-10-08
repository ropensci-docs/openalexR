# oa_fetch but for a random query

oa_fetch but for a random query

## Usage

``` r
oa_random(
  entity = oa_entities(),
  output = c("tibble", "dataframe", "list"),
  endpoint = "https://api.openalex.org"
)
```

## Arguments

- entity:

  Character. Scholarly entity of the search. The argument can be one of
  c("works", "authors", "institutions", "keywords", "funders",
  "sources", "publishers", "topics"). If not provided, \`entity\` is
  guessed from \`identifier\`.

- output:

  Character. Type of output, one of \`"tibble"\`, \`"dataframe"\`,
  \`"list"\`, or \`"raw"\`.

  tibble

  :   a tibble tidy data

  dataframe

  :   a base data.frame tidy data

  list

  :   a list of parsed JSON contents

  raw

  :   a list of raw JSON strings (length depends on query)

- endpoint:

  Character. URL of the OpenAlex Endpoint API server. Defaults to
  endpoint = "https://api.openalex.org".

## Value

A data.frame or a list. One row or one element. Result of the random
query. If you would like to select more than one random entity, say, 10,
use \`options = list(sample = 10)\` argument in \`oa_fetch\`.

## Examples

``` r
if (FALSE) { # \dontrun{
oa_random()
} # }
```
