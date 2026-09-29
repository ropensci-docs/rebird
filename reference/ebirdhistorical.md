# Historic observations on a date at a region or hotspot

Returns a list of taxa reported in a given region or hotspot on a
specific date

## Usage

``` r
ebirdhistorical(
  loc,
  date,
  sortKey = "mrec",
  categories = "all",
  max = 10000,
  fieldSet = "simple",
  provisional = FALSE,
  limitToHotspots = FALSE,
  sleep = 0,
  key = NULL,
  ...
)
```

## Arguments

- loc:

  (required) Region code or locID (if a hotspot). Region code can be
  country code (e.g. "US"), subnational1 code (states/provinces, e.g.
  "US-NV"), or subnational2 code (counties, e.g. "US-VA-003").

- date:

  (required) Date of historic observation date formatted according to
  ISO 8601 (e.g. 'YYYY-MM-DD', or 'YYYY-MM-DD hh:mm'). Hours and minutes
  are excluded.

- sortKey:

  \[mrec\|create\] Whether to order results by latest observation date
  or by latest creation date. The default is by observation date.

- categories:

  \[domestic\|form\|hybrid\|intergrade\|issf\|slash\|species\|spuh\]
  This is useful for limiting results to certain taxonomic categories.
  The default is all. Multiple categories may be comma-separated.

- max:

  Maximum number of result rows to return in this request. (A number
  between 1 and 10000. The default is 10000)

- fieldSet:

  \[simple\|full\] This is set to restrict results to either all or a
  subset of sighting fields. The default is simple.

- provisional:

  Should flagged records that have not been reviewed be included?

- limitToHotspots:

  Should results be limited to sightings at birding hotspots? The
  default is FALSE.

- sleep:

  Time (in seconds) before function sends API call. The defaults is
  zero. Set this to a higher number if you are using this function in a
  loop with many API calls.

- key:

  eBird API key. You can obtain one from https://ebird.org/api/keygen.
  We strongly recommend storing it in your `.Renviron` file as an
  environment variable called `EBIRD_KEY`.

- ...:

  Curl options passed on to
  [`GET`](https://httr.r-lib.org/reference/GET.html).

## Value

A data.frame containing the collected information:

"speciesCode": species codes

"comName": species common names

"sciName" species' scientific names

"locId": unique identifier for the locations

"locName": location name

"obsDt": observation date formatted according to ISO 8601 (e.g.
'YYYY-MM-DD', or 'YYYY-MM-DD hh:mm'). Hours and minutes are excluded if
the observer did not report an observation time

"howMany": "howMany": number of individuals observed, NA if only
presence was noted

"obsValid": TRUE if observation has been deemed valid by either the
automatic filters or a regional viewer, FALSE otherwise

"obsReviewed": TRUE if observation has been reviewed, FALSE otherwise

"locationPrivate": TRUE if location is not a birding hotspot

"subID": submission ID

"exoticCategory": exotic species category

"subnational2Code": county code (returned if simple=FALSE)

"subnational2Name": county name (returned if simple=FALSE)

"subnational1Code": state/province ISO code (returned if simple=FALSE)

"subnational1Name": state/province name (returned if simple=FALSE)

"countryCode": country ISO code (returned if simple=FALSE)

"countryName": country name (returned if simple=FALSE)

"userDisplayName": first and last name of the observer (returned if
simple=FALSE)

"obsID": observation ID (returned if simple=FALSE)

"checklistID": checklist ID (returned if simple=FALSE)

"presenceNoted": 'true' if user marked presence but did not count the
number of birds. 'false' otherwise (returned if simple=FALSE)

"hasComments": 'true' if comments are included (returned if
simple=FALSE)

"hasRichMedia": 'true' if rich media (e.g. photos/sounds) are included
(returned if simple=FALSE)

"firstName": observer's first name (returned if simple=FALSE)

"lastName": observer's last name (returned if simple=FALSE)

## References

<http://ebird.org/>

## Author

Guy Babineau <guy.babineau@gmail.com>

## Examples

``` r
if (FALSE) { # \dontrun{
ebirdhistorical(loc = 'US-VA-003', date='2019-02-14',max=10)
ebirdhistorical(loc = 'L196159', date='2019-02-14', fieldSet='full')
} # }
```
