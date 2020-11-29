Exploring the Factors of Song Popularity
================
by Louhavidandros

## Summary

    ## ── Attaching packages ─────────────────────────────────────── tidyverse 1.3.0 ──

    ## ✓ ggplot2 3.3.2     ✓ purrr   0.3.4
    ## ✓ tibble  3.0.4     ✓ dplyr   1.0.2
    ## ✓ tidyr   1.1.2     ✓ stringr 1.4.0
    ## ✓ readr   1.3.1     ✓ forcats 0.5.0

    ## ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
    ## x dplyr::filter() masks stats::filter()
    ## x dplyr::lag()    masks stats::lag()

    ## Parsed with column specification:
    ## cols(
    ##   .default = col_double(),
    ##   track_id = col_character(),
    ##   track_name = col_character(),
    ##   track_artist = col_character(),
    ##   track_album_id = col_character(),
    ##   track_album_name = col_character(),
    ##   track_album_release_date = col_character(),
    ##   playlist_name = col_character(),
    ##   playlist_id = col_character(),
    ##   playlist_genre = col_character(),
    ##   playlist_subgenre = col_character()
    ## )

    ## See spec(...) for full column specifications.

We chose to use the `spotify_songs` which gets its data from the
`spotifyr`package, whose data comes from Spotify. The data set contains
32833 observations each of which is a song, and 23 variables, which
range from information about the song such as name, artist and genre as
well as a number of numerical variables which each look at aspects of
the songs character such as its energy, its danceability or its
popularity. Our goal was to explore every genre of music in the data set
and see for each genre how the numerical variables affected a song’s
popularity; once we had this we then wanted to compare this across the
genres to see whether they had different factors that contributed to
making songs popular.

To begin with, we did some very general analysis and looked at which
genres and subgenres of music were the most popular overall and we found
that pop songs had the highest median popularity, and post-teen pop was
on average the most popular subgenre of music.

We then decided to do a genre by genre analysis of each variable by
creating scatter plots with a `geom_smooth` line, as well as a linear
model which would use every numerical variable as an explanatory
variable to try and predict track popularity. The scatter plots were so
widely spread that a correlation could not be claimed to exist for
certain, and the linear model we produced had an R squared value of 0.09
and an rmse value of 23.8 which are clearly undesirable values when
searching for a correlation.

Consequently, we changed the way we were approaching the problem. To
begin with, we created a new variable - `popularity_level` - by finding
the quartile values of track popularity separately for each genre and
then categorising song’s popularity as high, fairly high, low and very
low based on which quartile they fell into. This way there was a roughly
even number of songs in each popularity level in each genre. For every
genre we then looked at only the “High” and “Very Low” brackets of
popularity, and for each variable we created a density plot that showed
what values were most frequent in each popularity level. For example:

    ## Warning in popularity_level == c("High", "Very Low"): longer object length is
    ## not a multiple of shorter object length

![](README_files/figure-gfm/pop-density-example-1.png)<!-- -->

This graph shows the distribution of danceability levels of pop songs in
the highest and lowest popularity brackets. The range of values where
the red line is higher than the blue was defined as the optimal range,
as this is where if you picked a pop song at random you would have a
higher chance of it being very popular than being very unpopular.

These density graphs were made for every variable for each genre and
once these were created and we found which variables had interesting
information, we used ridge plots to be able to compare

Write-up of your project and findings go here. Think of this as the text
of your presentation. The length should be roughly 5 minutes when read
out loud. Although pacing varies, a 5-minute speech is roughly 750
words. To use the word count addin, select the text you want to count
the words of (probably this is the Summary section of this document, go
to Addins, and select the `Word count` addin). This addin counts words
using two different algorithms, but the results should be similar and as
long as you’re in the ballpark of 750 words, you’re good\! The addin
will ignore code chunks and only count the words in prose.

You can also load your data here and present any analysis results /
plots, but I strongly urge you to keep that to a minimum (maybe only the
most important graphic, if you have one you can choose). And make sure
to hide your code with `echo = FALSE` unless the point you are trying to
make is about the code itself. Your results with proper output and
graphics go in your presentation, this space is for a brief summary of
your project.

## Presentation

Our presentation can be found [here](presentation/presentation.html).

## Data

Include a citation for your data here. See
<http://libraryguides.vu.edu.au/c.php?g=386501&p=4347840> for guidance
on proper citation for datasets. If you got your data off the web, make
sure to note the retrieval date.

## References

List any references here. You should, at a minimum, list your data
source.
