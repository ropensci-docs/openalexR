# Get coverage of OpenAlex fields in openalexR

Get coverage of OpenAlex fields in openalexR

## Usage

``` r
get_coverage(entity = NULL)
```

## Arguments

- entity:

  The OA entity to inspect field coverage for. Returns information for
  all fields if \`NULL\` (default).

## Value

Data frame of field coverage information

## See also

oa_entities()

## Examples

``` r
oa_entities()
#> [1] "works"        "authors"      "institutions" "concepts"     "keywords"    
#> [6] "funders"      "sources"      "publishers"   "topics"      
head(get_coverage(entity = "works"))
#> # A tibble: 6 × 3
#>   original                oa2df          comment                          
#>   <chr>                   <chr>          <chr>                            
#> 1 abstract_inverted_index abstract       reconstructed from inverted index
#> 2 apc_list.currency       apc.currency   NA                               
#> 3 apc_list.provenance     apc.provenance NA                               
#> 4 apc_list.value          apc.value      NA                               
#> 5 apc_list.value_usd      apc.value_usd  NA                               
#> 6 apc_paid.currency       apc.currency   NA                               
```
