# Construct a set of options for an OpenAlex query

\`oa_options()\` builds the \`options\` argument of \[oa_fetch()\] and
\[oa_query()\]. It gathers the "power-user" parameters of an OpenAlex
query — field selection, sorting, random sampling, and paging — into a
single, validated object. Using \`oa_options()\` (instead of a bare
\`list()\`) gives you argument autocompletion, sensible defaults, and
early errors on typos or invalid values.

## Usage

``` r
oa_options(
  select = NULL,
  sort = NULL,
  sample = NULL,
  seed = NULL,
  per_page = 200,
  paging = c("cursor", "page"),
  pages = NULL,
  ...
)
```

## Arguments

- select:

  Character vector. Top-level fields to show in output. Defaults to
  NULL, which returns all fields.
  \<https://developers.openalex.org/guides/selecting-fields\>

- sort:

  Character. Attribute to sort by. For example: "display_name" for
  sources or "cited_by_count:desc" for works. See more at
  \<https://developers.openalex.org/guides/sort\>.

- sample:

  Integer. Number of (random) records to return. Should be no larger
  than 10,000. Defaults to NULL, which returns all records satisfying
  the query. Read more at
  \<https://developers.openalex.org/api-reference/works/list-works\>.

- seed:

  Integer. A seed value in order to retrieve the same set of random
  records in the same order when used multiple times with \`sample\`.
  IMPORTANT NOTE: Depending on your query, random results with a seed
  value may change over time due to new records coming into OpenAlex.
  This argument is likely only useful when queries happen close together
  (within a day).

- per_page:

  Numeric. Number of items to download per page. The per-page argument
  can assume any number between 1 and 200. Defaults to 200.

- paging:

  Character. Either "cursor" for cursor paging or "page" for basic
  paging. When used with \`sample\` and/or \`pages\`, paging is
  automatically set to basic paging (\`paging = "page"\`) to avoid
  duplicates and get the right page. See
  \<https://developers.openalex.org/guides/page-through-results\>.

- pages:

  Integer vector. The range of pages to return. If NULL, return all
  pages.

- ...:

  Additional query parameters forwarded to the OpenAlex API verbatim.
  Unknown parameters trigger a warning, since they are most often typos;
  supply them here only if you intend to use a parameter not yet wrapped
  by openalexR.

## Value

A named list of query options with class \`oa_options\`.

## Details

Passing a plain \`list()\` to \`options\` is still supported for
backward compatibility, but unknown keys in a plain list are forwarded
to the API verbatim and therefore silently ignored if misspelled.
\`oa_options()\` warns you about unknown keys instead.

## Examples

``` r
oa_options(select = c("id", "doi"), sort = "cited_by_count:desc")
#> $select
#> [1] "id"  "doi"
#> 
#> $sort
#> [1] "cited_by_count:desc"
#> 
#> $per_page
#> [1] 200
#> 
#> $paging
#> [1] "cursor"
#> 
#> attr(,"class")
#> [1] "oa_options" "list"      
oa_options(sample = 50, seed = 1)
#> $sample
#> [1] 50
#> 
#> $seed
#> [1] 1
#> 
#> $per_page
#> [1] 200
#> 
#> $paging
#> [1] "cursor"
#> 
#> attr(,"class")
#> [1] "oa_options" "list"      
oa_options(per_page = 50)
#> $per_page
#> [1] 50
#> 
#> $paging
#> [1] "cursor"
#> 
#> attr(,"class")
#> [1] "oa_options" "list"      
```
