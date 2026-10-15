# Convert OpenAlex collection from list to data frame

It converts bibliographic collections gathered from OpenAlex database
<https://openalex.org/> into data frame. The function converts a
collection of records about works, authors, institutions, venues or
keywords obtained using `oa_request` into a data frame/tibble.

## Usage

``` r
oa2df(
  data,
  entity,
  options = NULL,
  count_only = FALSE,
  group_by = NULL,
  abstract = TRUE,
  verbose = TRUE
)
```

## Arguments

- data:

  List. Output of `oa_request`.

- entity:

  Character. Scholarly entity of the search. The argument can be one of
  c("works", "authors", "institutions", "keywords", "funders",
  "sources", "publishers", "topics").

- options:

  List or \`oa_options()\` object. Additional parameters to add to the
  query, such as \`select\`, \`sort\`, \`sample\`, \`seed\`, and the
  paging controls (\`per_page\`, \`paging\`, \`pages\`). See
  \[oa_options()\] for the full list of options, their defaults, and
  details. A plain named list (e.g. \`list(sort =
  "cited_by_count:desc")\`) is also accepted for backward compatibility.

- count_only:

  Logical. If TRUE, the function returns only the number of item
  matching the query. Defaults to FALSE.

- group_by:

  Character. Attribute to group by. For example: "oa_status" for works.
  See more at \<https://developers.openalex.org/guides/grouping\>.

- abstract:

  Logical. If TRUE, the function returns also the abstract of each item.
  Ignored if entity is different from "works". Defaults to TRUE.

- verbose:

  Logical. If TRUE, print information about the data frame conversion
  process. Defaults to TRUE.

## Value

A tibble/data frame result of the original OpenAlex result list.

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
  from_publication_date = "2021-01-01",
  to_publication_date = "2021-04-30"
)

res <- oa_request(
  query_url = query,
  count_only = FALSE,
  verbose = FALSE
)

oa2df(res, entity = "works")
} # }
```
