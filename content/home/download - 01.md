+++
# A Recent Blog Posts section created with the Pages widget.
# This section displays recent blog posts from `content/post/`.

widget = "pages"  # See https://sourcethemes.com/academic/docs/page-builder/
headless = true  # This file represents a page section.
active = false  # Activate this widget? true/false
weight = 15  # Order that this section will appear.

title = "Get the PR2 database"
subtitle = ""

[content]
  # Page type to display. E.g. post, talk, or publication.
  page_type = "post"

  # Choose how much pages you would like to display (0 = all pages)
  count = 0

  # Choose how many pages you would like to offset by
  offset = 0

  # Page order. Descending (desc) or ascending (asc) date.
  order = "desc"

  # Filter posts by a taxonomy term.
  [content.filters]
    tag = ""
    category = "download"
    publication_type = ""
    exclude_featured = false

[design]
  # Toggle between the various page layout types.
  #   1 = List
  #   2 = Compact
  #   3 = Card
  #   4 = Citation (publication only)
  view = 1

[design.background]
  # Apply a background color, gradient, or image.
  #   Uncomment (by removing `#`) an option to apply it.
  #   Choose a light or dark text color by setting `text_color_light`.
  #   Any HTML color name or Hex value is valid.

  # Background color.
  # color = "navy"

  # Background gradient.
  # gradient_start = "DeepSkyBlue"
  # gradient_end = "SkyBlue"

  # Background image.
  # image = "background.jpg"  # Name of image in `static/img/`.
  # image_darken = 0.6  # Darken the image? Range 0-1 where 0 is transparent and 1 is opaque.

  # Text color (true=light or false=dark).
  # text_color_light = true  

[advanced]
 # Custom CSS.
 css_style = ""

 # CSS class.
 css_class = ""
+++
Current version : 4.12.0  
Last update : 8 August 2019  
DOI : [10.6084/m9.figshare.5913181](https://doi.org/10.6084/m9.figshare.5913181)  

The PR<sup>2</sup> database is provided in 3 different formats:  

###### **Flat files** for use with mothur, dada2, blast etc..   
* [Download latest release](https://github.com/pr2database/pr2database/releases)
* [Details of file provided](./post/documentation/03-pr2-files/)

###### R package **pr2database**  
* Use the following code under R
``` r
install.packages(devtools)
devtools::install_github("pr2database/pr2database")
```
* [Examples of use](./post/documentation/pr2-r-database-package/)

###### **SQLite** database file  
* [Download](https://github.com/pr2database/pr2database/releases/download/v4.12.0/pr2_version_4.12.0.sqlite.gz)
