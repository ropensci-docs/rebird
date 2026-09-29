# Region and hotspot info

Region and hotspot info

## Usage

``` r
ebirdregioninfo(loc, format = "full", key = NULL, ...)
```

## Arguments

- loc:

  The location or hotspot code to be checked. A single location only.

- format:

  Different options for displaying hierarchy of the region's name:
  \[nameonly\|namequal\|detailed\|detailednoqual\|revdetailed\|full\],
  defaults to full. Not used for hotspots.

- key:

  eBird API key. You can obtain one from https://ebird.org/api/keygen.
  We strongly recommend storing it in your `.Renviron` file as an
  environment variable called `EBIRD_KEY`.

- ...:

  Curl options passed on to
  [`GET`](https://httr.r-lib.org/reference/GET.html)

## Value

When region is a hotspot, a data frame (with some redundant information)
containing:

"locId", "locID": hotspot ID

"name", "locName": hotspot name

"latitude", "longitude", "lat", "long": hotspot latitude and longitude
(point location)

"countryCode", "countryName": code and name of the country where hotspot
is located

"subnational1Code", "subnational1Name": code and name of the
subnational1 area (e.g. state or province) where hotspot is located

"subnational2Code", "subnational2Name": code and name of the
subnational2 area (e.g. county) where hotspot is located

"isHotspot": logical, whether region is a hotspot (should always be
TRUE)

"hierarchicalName": full hotspot name including subnational1,
subnational2, and country info

When region is a subnational1, subnational2, or country code, a data
frame containing:

"region": name of the region, varies depending on value of "format"
provided

"minX", "maxX", "minY", "maxY": lat/long bounds of the region

## References

<http://ebird.org/>

## Author

Sebastian Pardo <sebpardo@gmail.com>, Andy Teucher
<andy.teucher@gmail.com>, Guy Babineau <guy.babineau@gmail.com>

## Examples

``` r
if (FALSE) { # \dontrun{
ebirdregioninfo("US")
ebirdregioninfo("CA-BC-GV")
ebirdregioninfo("CA-BC-GV", format = "revdetailed") # reverse order of region name
ebirdregioninfo("L196159")
} # }
```
