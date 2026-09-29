# Recent observations at a region or hotspot

Returns the most recent sighting information reported in a given region
or hotspot.

## Usage

``` r
ebirdregion(
  loc,
  species = NULL,
  back = NULL,
  max = NULL,
  locale = NULL,
  provisional = FALSE,
  hotspot = FALSE,
  simple = TRUE,
  sleep = 0,
  key = NULL,
  ...
)
```

## Arguments

- loc:

  (required) Region code or locID (for hotspots). Region code can be
  country code (e.g. "US"), subnational1 (states/provinces, e.g.
  "US-NV"), or subnational2 code (counties, e.g. "CA-BC-GV").

- species:

  eBird species code. See
  [`ebirdtaxonomy`](https://docs.ropensci.org/rebird/reference/ebirdtaxonomy.md)
  for a full list of scientific names, common names, and species codes.
  Alternatively, you can wrap the scientific name in the
  [`species_code`](https://docs.ropensci.org/rebird/reference/species_code.md)
  function which will return the eBird species code. Defaults to NULL,
  in which case sightings for all species are returned. See eBird
  taxonomy for more information:
  https://ebird.org/science/use-ebird-data/the-ebird-taxonomy

- back:

  Number of days back to look for observations (between 1 and 30,
  defaults to 14).

- max:

  Maximum number of result rows to return in this request (between 1 and
  10000, defaults to all)

- locale:

  Language/locale of response (when translations are available). See
  <https://docs.oracle.com/javase/6/docs/api/java/util/Locale.html> and
  <https://support.ebird.org/en/support/solutions/articles/48000804865-bird-names-in-ebird>
  (defaults to en_US).

- provisional:

  Should flagged records that have not been reviewed be included?
  (defaults to FALSE)

- hotspot:

  Should results be limited to sightings at birding hotspots? (defaults
  to FALSE).

- simple:

  Logical. Whether to return a simple (TRUE, default) or detailed
  (FALSE) set of results fields. Detailed results are only available if
  `loc` is a locID.

- sleep:

  Time (in seconds) before function sends API call (defaults to zero.
  Set to higher number if you are using this function in a loop with
  many API calls).

- key:

  eBird API key. You can obtain one from https://ebird.org/api/keygen.
  We strongly recommend storing it in your `.Renviron` file as an
  environment variable called `EBIRD_KEY` to avoid having to constantly
  supply the key, and to avoid accidentally sharing it publicly.

- ...:

  Curl options passed on to
  [`GET`](https://httr.r-lib.org/reference/GET.html)

## Value

A data.frame containing the collected information:

"speciesCode": species code

"comName": species common name

"sciName" species' scientific name

"locID": unique identifier for the location

"locName": location name

"obsDt": observation date formatted according to ISO 8601 (e.g.
'YYYY-MM-DD', or 'YYYY-MM-DD hh:mm'). Hours and minutes are excluded if
the observer did not report an observation time.

"howMany": number of individuals observed, NA if only presence was noted

"lat": latitude of the location

"lng": longitude of the location

"obsValid": TRUE if observation has been deemed valid by either the
automatic filters or a regional viewer, FALSE otherwise

"obsReviewed": TRUE if observation has been reviewed, FALSE otherwise

"locationPrivate": TRUE if location is not a birding hotspot

"subId": submission ID

## References

<http://ebird.org/>

## Author

Rafael Maia <rm72@zips.uakron.edu>

## Examples

``` r
if (FALSE) { # \dontrun{
ebirdregion(loc = 'US', species = 'btbwar')
ebirdregion(loc = 'US', species = species_code('Setophaga caerulescens')) # same as above
ebirdregion(loc = 'L196159', species = 'bkcchi', back = 30)
ebirdregion('US-OH', max = 10, provisional = TRUE, hotspot = TRUE)
} # }
```
