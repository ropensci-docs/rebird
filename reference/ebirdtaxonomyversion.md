# eBird Taxonomy Version

Returns a data.frame of available version numbers of the eBird taxonomy

## Usage

``` r
ebirdtaxonomyversion(key = NULL, ...)
```

## Arguments

- key:

  optional eBird API key. You can obtain one from
  https://ebird.org/api/keygen. We strongly recommend storing it in your
  `.Renviron` file as an environment variable called `EBIRD_KEY` to
  avoid having to constantly supply the key, and to avoid accidentally
  sharing it publicly.

- ...:

  Curl options passed on to
  [`GET`](https://httr.r-lib.org/reference/GET.html)

## Value

data.frame containing the collected information:

"authorityVer": Character of version.

"latest": Boolean indicating whether \`authorityVer\` is the latest
taxonomy version

## References

<http://ebird.org/>

## Author

Jordan Bradford <jrdnbradford@gmail.com>

## Examples

``` r
if (FALSE) { # \dontrun{
ebirdtaxonomyversion()
} # }
```
