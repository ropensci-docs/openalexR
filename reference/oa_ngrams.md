# Get N-grams of works

Some work entities in OpenAlex include N-grams (word sequences and their
frequencies) of their full text. The N-grams are obtained from Internet
Archive, which uses the spaCy parser to index scholarly works. See
\<https://developers.openalex.org/guides/deprecations\> for coverage and
more technical details.

## Usage

``` r
oa_ngrams(
  works_identifier,
  ...,
  endpoint = "https://api.openalex.org",
  verbose = FALSE
)
```

## Arguments

- works_identifier:

  Character. OpenAlex ID(s) of "works" entities as item identifier(s).
  These IDs start with "W". See more at
  \<https://developers.openalex.org/api-reference/works\>.

- ...:

  Unused.

- endpoint:

  Character. URL of the OpenAlex Endpoint API server. Defaults to
  endpoint = "https://api.openalex.org".

- verbose:

  Logical. If TRUE, print information on querying process. Default to
  `verbose = FALSE`. To shorten the printed query URL, set the
  environment variable openalexR.print to the number of characters to
  print: `Sys.setenv(openalexR.print = 70)`.

## Value

A data frame of paper metadata and a list-column of ngrams.

## Note

A faster implementation is available for \`curl\` \>= v5.0.0, and
\`oa_ngrams\` will issue a one-time message about this. This can be
suppressed with \`options("oa_ngrams.message.curlv5" = FALSE)\`.

## Examples

``` r
if (FALSE) { # \dontrun{

ngrams_data <- oa_ngrams(c("W1963991285", "W1964141474"))

# 10 most common ngrams in the first work
first_paper_ngrams <- ngrams_data$ngrams[[1]]
first_paper_ngrams[
  order(first_paper_ngrams$ngram_count, decreasing = TRUE),
][
  1:10,
]

# Missing N-grams are `NULL` in the `ngrams` list-column
oa_ngrams("https://openalex.org/W2284876136")
} # }
```
