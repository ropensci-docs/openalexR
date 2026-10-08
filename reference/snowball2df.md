# Flatten snowball result

Flatten snowball result

## Usage

``` r
snowball2df(data, verbose = FALSE)
```

## Arguments

- data:

  List result from \`oa_snowball\`.

- verbose:

  Logical. If TRUE, print information on wrangling process.

## Value

Tibble/data.frame of works with additional columns: append \`citing\`,
\`backward_count\`, \`cited_by\`, \`forward_count\`, \`connection\`, and
\`connection_count.\` For each work/row, these counts are WITHIN one
data search, and so \`forward_count\` \<= \`cited_by_count\`.

Consider the universe of all works linked to a set of starting works,
(\`oa_input = TRUE\`) for each work/row i: - citing: works in the
universe that i cites - backward_count: number of works in the universe
that i cites - cited_by: works that i is cited by - forward_count:
number of works in the universe that i is cited by - connection: works
in the universe linked to i - connection_count: number of works in the
universe linked to i (degree of i)

## Examples

``` r
if (FALSE) { # \dontrun{
flat_snow <- snowball2df(oa_snowball(
  identifier = "W1516819724",
  verbose = TRUE
))

flat_snow[, c("id", "connection", "connection_count")]
} # }
```
