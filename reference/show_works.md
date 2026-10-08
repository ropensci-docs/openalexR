# Simplify the OpenAlex works result

This function is mostly for the package's internal use, but we export it
so you can try it out. However, we expect that you'll likely write your
own function to simplify the result however you want.

## Usage

``` r
show_works(x, simp_func = utils::head)
```

## Arguments

- x:

  Dataframe/tibble. Result of the OpenAlex query for authors already
  converted to data frame/tibble.

- simp_func:

  R function to simplify the result. Default to \`head\`. If you want
  the entire table, set \`simp_fun = identity\`.

## Value

Simplified tibble to display. The first column, \`id\` is the short-form
OpenAlex ID of the works. If \`x\` is \`NULL\` (which is what
\[oa_fetch()\] returns when a query matched no records or the API
request failed) or has zero rows, a zero-row tibble with these columns
is returned, with a warning in the \`NULL\` case.

## Examples

``` r
if (FALSE) { # \dontrun{
show_works(oa_fetch(
  identifier = c("W2741809807", "W2755950973"),
  verbose = TRUE
))
} # }
```
