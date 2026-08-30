# Checklist feed on a date at a region or hotspot

Returns checklist-level information reported in a given region or
hotspot. Note only bird information is species count.

## Usage

``` r
ebirdchecklistfeed(loc, date, max = 10, sleep = 0, key = NULL, ...)
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

- max:

  Maximum number of result rows to return in this request (between 1 and
  200, default 10)

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

"locId": unique identifier for the locations

"subId": submission (checklist) identifier

"userDisplayName": first and last name of the observer

"numSpecies": number of species reported

"obsDt": observation date formatted according to ISO 8601 (e.g.
'YYYY-MM-DD', or 'YYYY-MM-DD hh:mm'). Hours and minutes are excluded if
the observer did not report an observation time

"obsTime": observation time (24hr)

"isoObsDate": ISO observation date and time

"subID": deprecated submission identifier

"loc": delimited string of location descriptors

## References

<http://ebird.org/>

## Author

Marianna Foos <marianna.foos@gmail.com>

## Examples

``` r
if (FALSE) { # \dontrun{
ebirdchecklistfeed(loc = "L207391", date = "2020-03-24", max = 10)
} # }
```
