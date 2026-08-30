# Return species code

Returns the species code for a given scientific name. Uses an
internally-stored version of the taxonomy. Also provides a message with
the common name, scientific name, and species code of the species.

## Usage

``` r
species_code(sciname = NULL)
```

## Arguments

- sciname:

  (required) Character string of length 1 with the scientific name to
  look for. Case insensitive.

## Value

A character string with the eBird species code.

## References

<http://ebird.org/>

## Author

Sebastian Pardo <sebpardo@gmail.com>

## Examples

``` r
species_code("Anhinga anhinga")
#> Anhinga (Anhinga anhinga): anhing
#> [1] "anhing"
```
