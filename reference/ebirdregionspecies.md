# Get a list of species codes ever seen in a location.

Returns the eBird codes for all species-level taxa recorded in a
particular region or location. Codes are returned in taxonomic order.

## Usage

``` r
ebirdregionspecies(location, key = NULL, ...)
```

## Arguments

- location:

  Any valid location, USFWS region, subnational2, subnational1, country,
  or custom region code. (Location can be a hotspot or personal
  location).

- key:

  eBird API key. You can obtain one from https://ebird.org/api/keygen.
  We strongly recommend storing it in your `.Renviron` file as an
  environment variable called `EBIRD_KEY`.

- ...:

  Curl options passed on to
  [`GET`](https://httr.r-lib.org/reference/GET.html)

## Value

A single column data.frame containing the collected information:

"speciesCode": eBird species code, suitable for joining to the
[`ebirdtaxonomy`](https://docs.ropensci.org/rebird/reference/ebirdtaxonomy.md)

## References

<http://ebird.org/>

## Author

David Bradnum <david.bradnum@gmail.com>

## Examples

``` r
if (FALSE) { # \dontrun{
ebirdregionspecies("GB") # all in Great Britain
ebirdregionspecies("GB-ENG") # all in England
ebirdregionspecies("GB-ENG-LND") # all in London

library(dplyr)
taxonomy <- ebirdtaxonomy()
localSpecies <- ebirdregionspecies("L5803024") # specific hotspot
inner_join(localSpecies, taxonomy)
} # }
```
