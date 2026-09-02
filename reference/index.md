# Package index

## Main functions

- [`oa_fetch()`](https://docs.ropensci.org/openalexR/reference/oa_fetch.md)
  : Fetching records
- [`oa_snowball()`](https://docs.ropensci.org/openalexR/reference/oa_snowball.md)
  : A function to perform a snowball search and convert the result to a
  tibble/data frame.
- [`oa_ngrams()`](https://docs.ropensci.org/openalexR/reference/oa_ngrams.md)
  : Get N-grams of works
- [`oa_random()`](https://docs.ropensci.org/openalexR/reference/oa_random.md)
  : oa_fetch but for a random query
- [`oa_options()`](https://docs.ropensci.org/openalexR/reference/oa_options.md)
  : Construct a set of options for an OpenAlex query

## Utility functions

- [`show_authors()`](https://docs.ropensci.org/openalexR/reference/show_authors.md)
  : Simplify the OpenAlex authors result
- [`show_works()`](https://docs.ropensci.org/openalexR/reference/show_works.md)
  : Simplify the OpenAlex works result

## Low-level functions

- [`oa_query()`](https://docs.ropensci.org/openalexR/reference/oa_query.md)
  : Generate an OpenAlex query from a set of parameters
- [`oa_request()`](https://docs.ropensci.org/openalexR/reference/oa_request.md)
  : Get bibliographic records from OpenAlex database
- [`oa_generate()`](https://docs.ropensci.org/openalexR/reference/oa_generate.md)
  : Iterating through records

## To dataframe

convert the JSON object to tibble/dataframe

- [`authors2df()`](https://docs.ropensci.org/openalexR/reference/authors2df.md)
  : Convert OpenAlex collection of authors' records from list format to
  data frame
- [`concepts2df()`](https://docs.ropensci.org/openalexR/reference/concepts2df.md)
  : Convert OpenAlex collection of concepts' records from list format to
  data frame
- [`funders2df()`](https://docs.ropensci.org/openalexR/reference/funders2df.md)
  : Convert OpenAlex collection of funders' records from list format to
  data frame
- [`institutions2df()`](https://docs.ropensci.org/openalexR/reference/institutions2df.md)
  : Convert OpenAlex collection of institutions' records from list
  format to data frame
- [`keywords2df()`](https://docs.ropensci.org/openalexR/reference/keywords2df.md)
  : Convert keywords from list to data frame
- [`oa2df()`](https://docs.ropensci.org/openalexR/reference/oa2df.md) :
  Convert OpenAlex collection from list to data frame
- [`publishers2df()`](https://docs.ropensci.org/openalexR/reference/publishers2df.md)
  : Convert OpenAlex collection of publishers' records from list format
  to data frame
- [`snowball2df()`](https://docs.ropensci.org/openalexR/reference/snowball2df.md)
  : Flatten snowball result
- [`sources2df()`](https://docs.ropensci.org/openalexR/reference/sources2df.md)
  : Convert OpenAlex collection of sources' records from list format to
  data frame
- [`topics2df()`](https://docs.ropensci.org/openalexR/reference/topics2df.md)
  : Convert OpenAlex collection of topics' records from list format to
  data frame
- [`works2df()`](https://docs.ropensci.org/openalexR/reference/works2df.md)
  : Convert OpenAlex collection of works from list format to data frame

## Data and others

- [`countrycode`](https://docs.ropensci.org/openalexR/reference/countrycode.md)
  : Index of Countries and their alpha-2 and alpha-3 codes.
- [`concept_abbrev`](https://docs.ropensci.org/openalexR/reference/concept_abbrev.md)
  : Concepts and abbreviations.
- [`oa_entities()`](https://docs.ropensci.org/openalexR/reference/oa_entities.md)
  : Available entities in the OpenAlex database
- [`get_coverage()`](https://docs.ropensci.org/openalexR/reference/get_coverage.md)
  : Get coverage of OpenAlex fields in openalexR
- [`oa2df_coverage`](https://docs.ropensci.org/openalexR/reference/oa2df_coverage.md)
  : Coverage of OpenAlex entity fields after converting to data frame.
- [`oa2bibliometrix()`](https://docs.ropensci.org/openalexR/reference/oa2bibliometrix.md)
  : Convert OpenAlex collection from data frame to bibliometrix object
