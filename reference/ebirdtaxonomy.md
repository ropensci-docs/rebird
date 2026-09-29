# eBird Taxonomy

Returns a data.frame of all taxa in the eBird taxonomy for the given
combination of categories. Defaults to all categories. Any taxon with
the category of 'species' may be used as a parameter in service calls
that take a species code. Any taxon not in this category will be
rejected by these services at this time.

## Usage

``` r
ebirdtaxonomy(cat = NULL, locale = NULL, species = NULL, key = NULL, ...)
```

## Arguments

- cat:

  Species category. String or character vector with one of more of:
  "domestic", "form", "hybrid", "intergrade", "issf", "slash",
  "species", "spuh". If not specified, defaults to all. For more info
  about the meaning of species categories, see
  <https://ebird.org/science/use-ebird-data/the-ebird-taxonomy>.

- locale:

  Language/locale of response (when translations are available). See
  <https://docs.oracle.com/javase/6/docs/api/java/util/Locale.html> and
  <https://support.ebird.org/en/support/solutions/articles/48000804865-bird-names-in-ebird>
  (defaults to en_US).

- species:

  Character vector of eBird taxonomy species code(s). Limits query
  results to only these taxa. Default is NULL, which does not limit
  taxa.

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

"sciName": Taxon's scientific name.

"comName": Taxon's common name.

"speciesCode": Unique species code.

"category": Taxon's species category.

"taxonOrder": Numeric value determining the order in which taxonomic
lists are presented.

"bandingCodes": Taxon's ABA banding code(s).

"comNameCodes": Taxon's common name code(s).

"sciNameCodes": Taxon's scientific name code(s).

"order": Taxon's order.

"familyComName": Family's common name.

"familySciName": Family's scientific name.

"reportAs": Species code to report taxon as.

"extinct": Logical, whether the taxon is considered extinct.

"extinctYear": Year taxon became extinct. Currently unavailable.

## References

<http://ebird.org/>

## Author

Andy Teucher <andy.teucher@gmail.com>, Sebastian Pardo
<sebpardo@gmail.com>

## Examples

``` r
if (FALSE) { # \dontrun{
ebirdtaxonomy()
ebirdtaxonomy(cat = c("spuh", "slash")) 
} # }
```
