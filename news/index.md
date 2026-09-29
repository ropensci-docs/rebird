# Changelog

## rebird 1.3.9006

- Added
  [`ebirdtaxonomyversion()`](https://docs.ropensci.org/rebird/reference/ebirdtaxonomyversion.md)
  which retrieves data on available taxonomy versions. The version is
  added as an attribute to
  [`rebird::tax`](https://docs.ropensci.org/rebird/reference/tax.md)
  ([\#131](https://github.com/ropensci/rebird/issues/131)).
- Added
  [`ebirdchecklist()`](https://docs.ropensci.org/rebird/reference/ebirdchecklist.md),
  which lets you view individual checklists (thanks
  [@RichardLitt](https://github.com/RichardLitt) and
  [@Rafnuss](https://github.com/Rafnuss),
  [\#108](https://github.com/ropensci/rebird/issues/108)).
- Made
  [`ebirdregioncheck()`](https://docs.ropensci.org/rebird/reference/ebirdregioncheck-defunct.md),
  [`ebirdhotspot()`](https://docs.ropensci.org/rebird/reference/ebirdhotspot-defunct.md),
  [`ebirdloc()`](https://docs.ropensci.org/rebird/reference/ebirdloc-defunct.md)
  defunct.
- API tests now use `vcr`, which saves “cassettes” of the tests which
  can be played in CI when running tests during CI, instead of storing
  an API key and having to run tests remotely with every PR (thanks
  [@slager](https://github.com/slager)).
- Updated `rebird`’s internal taxonomy after 2023 taxonomic update.

## rebird 1.3.0

CRAN release: 2021-09-20

- Updated `rebird`’s internal taxonomy after 2021 taxonomic update.
- Fix tests.

## rebird 1.2.0

CRAN release: 2021-01-27

- Added
  [`ebirdsubregionlist()`](https://docs.ropensci.org/rebird/reference/ebirdsubregionlist.md)
  which lists sub-regions within a specified region (thanks
  [@dbradnum](https://github.com/dbradnum),
  [\#90](https://github.com/ropensci/rebird/issues/90)).
- Disabled
  [`ebirdfreq()`](https://docs.ropensci.org/rebird/reference/ebirdfreq.md)
  (now throws an informative error) as the frequency data request can’t
  be done through the website anymore without logging in first. This
  request might be added to the eBird API in the near future
  ([\#88](https://github.com/ropensci/rebird/issues/88)).
- Added
  [`ebirdhotspotlist()`](https://docs.ropensci.org/rebird/reference/ebirdhotspotlist.md)
  which provides a list of hotspots in a region or nearby coordinates
  ([\#87](https://github.com/ropensci/rebird/issues/87)).
- Added
  [`ebirdregionspecies()`](https://docs.ropensci.org/rebird/reference/ebirdregionspecies.md)
  which provides a list of species codes seen in a location (thanks
  [@dbradnum](https://github.com/dbradnum),
  [\#86](https://github.com/ropensci/rebird/issues/86)).
- Added
  [`ebirdchecklistfeed()`](https://docs.ropensci.org/rebird/reference/ebirdchecklistfeed.md)
  which provides a list of checklists submitted on a given date at a
  region or hotspot (thanks [@mfoos](https://github.com/mfoos),
  [\#79](https://github.com/ropensci/rebird/issues/79)).

## rebird 1.1.0

CRAN release: 2019-10-24

- Updated internal taxonomy to reflect changes in the [2019 Taxonomy
  Update](https://ebird.org/news/2019-ebird-taxonomy-update)
  ([\#76](https://github.com/ropensci/rebird/issues/76)).
- Updated
  [`ebirdregioninfo()`](https://docs.ropensci.org/rebird/reference/ebirdregioninfo.md)
  to also provide information of hotspots (thanks
  [@gbabineau](https://github.com/gbabineau),
  [\#72](https://github.com/ropensci/rebird/issues/72)).
- Added
  [`ebirdhistorical()`](https://docs.ropensci.org/rebird/reference/ebirdhistorical.md)
  which provides historic observations on a date at a region or hotspot
  (thanks [@gbabineau](https://github.com/gbabineau),
  [\#74](https://github.com/ropensci/rebird/issues/74)).
- Fixed broken API links in README (thanks
  [@mfoos](https://github.com/mfoos),
  [\#75](https://github.com/ropensci/rebird/issues/75)).

## rebird 1.0.0

CRAN release: 2018-09-27

This version switches all functions over the the [new eBird
API](https://documenter.getpostman.com/view/664302/S1ENwy59?version=latest),
given that the one previously used by `rebird` will be retired on
October 1st. As such, many of the functions in `rebird` have changed,
and the previous versions of the package will not work correctly.

#### Breaking changes

- The biggest change in the new API is that most queries (with the
  exception of
  [`ebirdtaxonomy()`](https://docs.ropensci.org/rebird/reference/ebirdtaxonomy.md))
  require users to provide an API key, which is linked to your eBird
  user account. See the README.md or the package vignette for more info
  on how to set up a key. Alternatively, the key can be provided as an
  argument in all functions.
- The new API requests, and thus `rebird` functions, now use species
  codes rather than scientific names for species-specific requests.

#### Major changes

- New
  [`species_code()`](https://docs.ropensci.org/rebird/reference/species_code.md)
  function that converts from scientific name to species code and can be
  called within other functions.
- New
  [`ebirdregioninfo()`](https://docs.ropensci.org/rebird/reference/ebirdregioninfo.md)
  function that provides detailed information on a given eBird region .

#### Minor changes

- [`ebirdregion()`](https://docs.ropensci.org/rebird/reference/ebirdregion.md)
  now uses `loc` as its first argument instead of `region` as it allows
  for both regions and hotspots to be specified.

#### Deprecated functions

- Given the changes to the eBird API, the functions
  [`ebirdloc()`](https://docs.ropensci.org/rebird/reference/ebirdloc-defunct.md),
  [`ebirdhotspot()`](https://docs.ropensci.org/rebird/reference/ebirdhotspot-defunct.md),
  and
  [`ebirdregioncheck()`](https://docs.ropensci.org/rebird/reference/ebirdregioncheck-defunct.md)
  have been deprecated and will be removed in future releases. These
  functions still work in the updated API, but might cease to do so in
  the near future.
  [`ebirdregion()`](https://docs.ropensci.org/rebird/reference/ebirdregion.md)
  has the same functionality as the first two functions, while
  [`ebirdregioninfo()`](https://docs.ropensci.org/rebird/reference/ebirdregioninfo.md)
  provides a more informative interface than
  [`ebirdregioncheck()`](https://docs.ropensci.org/rebird/reference/ebirdregioncheck-defunct.md).

## rebird 0.5.0

CRAN release: 2018-07-09

#### MINOR IMPROVEMENTS AND BUG FIXES

- Now all API queries use https, which is needed to avoid double
  encoding urls (see
  [\#62](https://github.com/ropensci/rebird/issues/62)).
- Added information about
  [`auk`](https://github.com/CornellLabofOrnithology/auk), an R package
  that helps extracting and processing the whole eBird dataset
  ([\#60](https://github.com/ropensci/rebird/issues/60)).
- Updated package documentation
  ([\#61](https://github.com/ropensci/rebird/issues/61)).

## rebird 0.4.0

CRAN release: 2017-04-26

#### MINOR IMPROVEMENTS AND BUG FIXES

- Fix for `ebirdfreq` which stopped working due to changes on the eBird
  website ([\#52](https://github.com/ropensci/rebird/issues/52)).
- Replaced deprecated `dplyr::rbind_all` function with
  [`dplyr::bind_rows`](https://dplyr.tidyverse.org/reference/bind_rows.html)
  ([\#43](https://github.com/ropensci/rebird/issues/43)).

## rebird 0.3.0

CRAN release: 2016-03-23

#### MINOR IMPROVEMENTS AND BUG FIXES

- Fix for
  [`httr::content`](https://httr.r-lib.org/reference/content.html) after
  changes in httr v1.0.0
  ([\#38](https://github.com/ropensci/rebird/issues/38)).

## rebird 0.2

CRAN release: 2015-07-09

#### NEW FEATURES

- Added two new functions `ebirdfreq` and `ebirdregioncheck`, which
  provide historical frequency of observation data and check whether a
  region is valid under eBird, respectively.

#### MINOR IMPROVEMENTS

- Passed along curl options to httr functions
- Replaced RJSONIO with jsonlite
- Replaced plyr with dplyr
