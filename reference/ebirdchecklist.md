# View Checklist

View Checklist

## Usage

``` r
ebirdchecklist(subId, sleep = 0, key = NULL, other = FALSE, ...)
```

## Arguments

- subId:

  The checklist identifier

- sleep:

  Time (in seconds) before function sends API call (defaults to zero.
  Set to higher number if you are using this function in a loop with
  many API calls).

- key:

  eBird API key. You can obtain one from https://ebird.org/api/keygen.
  We strongly recommend storing it in your `.Renviron` file as an
  environment variable called `EBIRD_KEY`.

- other:

  FALSE (default) or TRUE. Whether to return some
  optional/deprecated/unsupported columns. Currently these are all
  columns in subAux, projId, howManyAt\*, hideFlags, present, and
  submissionMethod\*.

- ...:

  Curl options passed on to
  [`GET`](https://httr.r-lib.org/reference/GET.html)

## Value

A 'tibble' 'data.frame' containing checklist information:

"subId": submission ID

"protocolId": eBird protocol ID

"locId": location ID

"durationHrs": checklist duration, in hours

"allObsReported": whether all observations were reported, i.e., whether
it was a 'complete' checklist

"subComments": checklist comments

"creationDt": checklist creation date

"lastEditedDt": checklist last edited date

"obsDt": checklist date-time

"obsTimeValid": whether checklist date-time is valid

"checklistId" checklist ID

"numObservers" number of observers on checklist

"subnational1Code" country code and subnational1 code

"userDisplayName" eBird user display name

"numSpecies" number of species reported on checklist

"speciesCode" species codes reported on checklist

"obsId" observation IDs for each taxon on checklist

"howManyStr" number of individuals reported for each taxon

"exoticCategory" exotic species categories for each taxon

"obsComments" observation comments for each taxon

"photoCounts" number of photos for each taxon

"audioCounts" number of audio files for each taxon

"videoCounts" number of video files for each taxon

"auxCode" breeding code for each taxon

## References

<http://ebird.org/>

## Examples

``` r
if (FALSE) { # \dontrun{
ebirdchecklist("S121423354")
} # }
```
