# List sub-regions within a specified region.

List sub-regions within a specified region.

## Usage

``` r
ebirdsubregionlist(
  regionType = c("country", "subnational1", "subnational2"),
  parentRegionCode,
  key = NULL,
  ...
)
```

## Arguments

- regionType:

  The type of region to search for. Must be one of 'country',
  'subnational1' or 'subnational2'.

- parentRegionCode:

  The region to search within. Must be a valid country or subnational1
  code. If \`regionType\` is 'country' then this parameter is ignored
  (since the search will automatically be world-wide).

- key:

  eBird API key. You can obtain one from https://ebird.org/api/keygen.
  We strongly recommend storing it in your `.Renviron` file as an
  environment variable called `EBIRD_KEY`.

- ...:

  Curl options passed on to
  [`GET`](https://httr.r-lib.org/reference/GET.html)

## Value

A data.frame containing:

"code": eBird code for the subregion

"name": full name for the subregion

## References

<http://ebird.org/>

## Author

David Bradnum <dbradnum@gmail.com>

## Examples

``` r
if (FALSE) { # \dontrun{
ebirdsubregionlist("country")
ebirdsubregionlist("subnational1", "US")
ebirdsubregionlist("subnational2", "US-NY")
} # }
```
