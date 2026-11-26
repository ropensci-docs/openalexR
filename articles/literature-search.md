# Literature search

While
[`oa_fetch()`](https://docs.ropensci.org/openalexR/reference/oa_fetch.md)
offers a convenient and flexible way of retrieving results from queries
to the OpenAlex API, we may want to specify some of its arguments to
optimize your API calls for certain use cases.

This vignette shows how to perform an efficient literature search,
comparing to a similar search in PubMed using the
[**rentrez**](https://github.com/ropensci/rentrez) package.

``` r

library(openalexR)
library(dplyr)
library(rentrez)
```

## Motivating example

Suppose you’re interested in finding publications that explore the links
between the **BRAF** gene and **melanoma**.

With the **rentrez** package, we can use the `entrez_search` function,
which retrieves up to 10 records matching the search query from the
PubMed database.

``` r

braf_pubmed <- entrez_search(db = "pubmed", term = "BRAF and melanoma", retmax = 10)
braf_pubmed
#> Entrez search result with 9238 hits (object contains 10 IDs and no web_history object)
#>  Search term (as translated):  "BRAF"[All Fields] AND ("melanoma"[MeSH Terms] OR  ...
braf_pubmed$ids |> 
  entrez_summary(db = "pubmed") |> 
  extract_from_esummary("title") |> 
  tibble::enframe("id", "title")
#> # A tibble: 10 × 2
#>    id       title                                                               
#>    <chr>    <chr>                                                               
#>  1 42675868 Comprehensive genomic profiling of mucosal melanoma reveals novel f…
#>  2 42674934 Are Metabolic Imaging Biomarkers Ready for Clinical Translation in …
#>  3 42674721 Exploring the Role of TERT Promoter Mutations in Advanced Melanoma …
#>  4 42671758 IGF1-IGF1R signaling in tumor-associated macrophages regulates extr…
#>  5 42667537 Real-World Use of Adjuvant Nivolumab for Resected Stage III-IV Mela…
#>  6 42663979 Successful retreatment with dabrafenib and trametinib for cardiac m…
#>  7 42660910 Small-molecule RAS/RAF inhibitors target RAS-driven cancers via all…
#>  8 42657315 Venous thromboembolism and bleeding in advanced melanoma: a propens…
#>  9 42650005 Clinicopathological Predictors of Recurrence in Resected Stage IIB-…
#> 10 42645086 Association Between BRAF Mutation Status and Clinicopathological Fe…
```

On the other hand, with **openalexR**, we can use the `search` argument
of
[`oa_fetch()`](https://docs.ropensci.org/openalexR/reference/oa_fetch.md):

``` r

braf_oa <- oa_fetch(
  search = "BRAF AND melanoma",
  options = oa_options(pages = 1, per_page = 10),
  verbose = TRUE
)
#> Requesting url: <https://api.openalex.org/works?search=BRAF%20AND%20melanoma>
#> Using basic paging...
#> ℹ Getting 1 page of results with a total of 10 records...
braf_oa |> 
  show_works(simp_func = identity) |> 
  select(1:2)
#> # A tibble: 10 × 2
#>    id          display_name                                                     
#>    <chr>       <chr>                                                            
#>  1 W2163188200 Mutations of the BRAF gene in human cancer                       
#>  2 W2128542677 Improved Survival with Vemurafenib in Melanoma with BRAF V600E M…
#>  3 W2128035403 Nivolumab in Previously Untreated Melanoma without BRAF Mutation 
#>  4 W2106543129 Inhibition of Mutated, Activated BRAF in Metastatic Melanoma     
#>  5 W2156078931 Combined BRAF and MEK Inhibition in Melanoma with BRAF V600 Muta…
#>  6 W2121545342 Combined Vemurafenib and Cobimetinib in BRAF -Mutated Melanoma   
#>  7 W2096387850 Combined BRAF and MEK Inhibition versus BRAF Inhibition Alone in…
#>  8 W2136474966 Improved Survival with MEK Inhibition in BRAF-Mutated Melanoma   
#>  9 W2168143310 Survival in BRAF V600–Mutant Advanced Melanoma Treated with Vemu…
#> 10 W2166662937 Combined Nivolumab and Ipilimumab or Monotherapy in Untreated Me…
```

This call performs a search using the OpenAlex API, retrieving the 10
most relevant results for the query “BRAF AND melanoma”.

By default, an
[`oa_fetch()`](https://docs.ropensci.org/openalexR/reference/oa_fetch.md)
call will return all records associated with a search, for example,
querying “BRAF AND melanoma” in OpenAlex may return tens of thousands of
records. Fetching all of these records would be unnecessarily slow,
especially when we are often only interested in the top, say, 10 results
(based on citation count or relevance — more on sorting below).

We can limit the number of results with the paging options `per_page`
(number of records to return per page, between 1 and 200, default 200)
and `pages` (range of pages to return, *e.g.*, `1:3` for the first 3
pages, default NULL to return all pages), supplied via
`options = oa_options(...)`. For example, if you want the top 250
records, you can set

- `options = oa_options(per_page = 50, pages = 1:5)` to get exactly 250
  records; or
- `options = oa_options(per_page = 200, pages = 1:2)` to get 400
  records, then you can slice the dataframe one more time to get the
  first 250.

## Sorting results

By default, the results from `oa_fetch` are sorted based on
*relevance_score*, a measure of how closely each result matches the
query.[^1] If a different ordering is desired, such as sorting by
citation count, you can specify `sort` in the `options` argument.

Here are the commonly used sorting options:

- `relevance_score`: Default, ranks results based on query match
  relevance.
- `cited_by_count`: Sorts results based on the number of times the work
  has been cited.
- `publication_date`: Sorts by publication date.

``` r

results <- openalexR::oa_fetch(
  search = "BRAF AND melanoma",
  options = oa_options(pages = 1, per_page = 10, sort = "cited_by_count:desc"),
  verbose = TRUE
)
#> Requesting url:
#> <https://api.openalex.org/works?search=BRAF%20AND%20melanoma&sort=cited_by_count%3Adesc>
#> Using basic paging...
#> ℹ Getting 1 page of results with a total of 10 records...
```

## Conclusion

The `openalexR` package provides a powerful and flexible interface for
conducting academic literature searches using the OpenAlex API. By
controlling the number of results and the sorting order, you can tailor
your search to retrieve the most relevant or impactful publications. In
cases where large datasets are involved, it’s useful to limit the number
of results returned to ensure efficient and timely searches.

We encourage users to explore further options provided by `openalexR` to
refine their search and retrieve the specific data they need for their
research projects:

- <https://developers.openalex.org/guides/searching>
- <https://developers.openalex.org/guides/searching>

[^1]: *relevance_score* also includes a weighting term for citation
    counts: more highly-cited entities score higher.
