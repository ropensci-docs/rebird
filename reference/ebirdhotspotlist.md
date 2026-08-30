# Hotspots in a region or nearby coordinates

Get the list of hotspots within a region, or within a radius of up to 50
kilometers, from a given set of coordinates.

## Usage

``` r
ebirdhotspotlist(
  regionCode = NULL,
  lat = NULL,
  lng = NULL,
  dist = NULL,
  back = NULL,
  sleep = 0,
  key = NULL,
  ...
)
```

## Arguments

- regionCode:

  The country, subnational1 or subnational2 code. If \`regionCode\` is
  provided then latitude and longitude are ignored.

- lat:

  Decimal latitude. value between -90.00 and 90.00, up to two decimal
  places of precision. Defaults to latitude based on IP if neither
  \`regionCode\` nor \`lat\` and \`lng\` are provided.

- lng:

  Decimal longitude. value between -180.00 and 180.00, up to two decimal
  places of precision. Defaults to longitude based on IP if neither
  \`regionCode\` nor \`lat\` and \`lng\` are provided.

- dist:

  The search radius from the given set of coordinates, in kilometers
  (between 0 and 500, defaults to 25).

- back:

  Only fetch hotspots which have been visited up to 'back' days ago
  (defaults to \`NULL\`).

- sleep:

  Time (in seconds) before function sends API call (defaults to zero.
  Set to higher number if you are using this function in a loop with
  many API calls).

- key:

  eBird API key. You can obtain one from https://ebird.org/api/keygen.
  We strongly recommend storing it in your `.Renviron` file as an
  environment variable called `EBIRD_KEY`.

- ...:

  Curl options passed on to
  [`GET`](https://httr.r-lib.org/reference/GET.html)

## Value

A data.frame with ten columns containing:

"locId": unique identifier for the hotspot

"locName": hotspot name

"countryCode": country code

"subnational1Code": subnational1 code (state/province level)

"subnational2Code": subnational2 code (county/municipality level)

"lat": latitude of the hotspot

"lng": longitude of the hotspot

"latestObsDt": Date of latest observation

"numSpeciesAllTime": Total number of species recorded in the hotspot

## References

<http://ebird.org/>

## Author

Sebastian Pardo <sebpardo@gmail.com>, David Bradnum <dbradnum@gmail.com>

## Examples

``` r
if (FALSE) { # \dontrun{
ebirdhotspotlist("CA-NS-HL")
ebirdhotspotlist("VA")
ebirdhotspotlist(lat = 30, lng = -90, dist = 10)
library(httr)
ebirdhotspotlist("CA-NS-HL", config = verbose())
} # }
```
