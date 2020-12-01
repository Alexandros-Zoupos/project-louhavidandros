Project proposal
================
Louhavidandros

## 1\. Introduction

We have decided that for our project, it would be interesting to try and
find what makes a song popular in its genre. We hypothesize that the
characteristics that make a song popular change in each genre.

For this, we will use `spotify_songs` which gets its data from the
`spotifyr` package which in turn gets its data from spotify. In this
data set the cases are songs and the variables include the `track_name`,
the `track_album_name`, the `track_artist`, the `paylist_name` it was
taken from, the `playlist_genre` and `playlist_subgenre`, the
`track_album_release_date`, the `track_popularity` and a selection of
variables calculated by spotify to represent an aspect of a song such as
its `energy` or `tempo`, as well as more general information like the
song’s `key`.

The songs are from the top 20 playlists from the top 4 sub-genres from
the top 6 genres. This means that the genre used is based on the
playlist the song was found in, not the genre of the track itself. This
means that we will have to take our results with “a pinch of salt” since
the playlist genre may not be identical to the track genre.

## 2\. Data

``` r
spotify_songs <- read_csv(here('data/Spotify.csv'))
```

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

## 3\. Data analysis plan

Since the aim of the project is to examine what aspects make a song
popular the response variable will always be the popularity of a song
(`track_popularity`). Each genre of music will be studied separately,
using all the numeric variables as well as the artist of each song. The
comparison groups are the genres of music.

    ## # A tibble: 6 x 2
    ##   playlist_genre     n
    ##   <chr>          <int>
    ## 1 edm             6043
    ## 2 rap             5746
    ## 3 pop             5507
    ## 4 r&b             5431
    ## 5 latin           5155
    ## 6 rock            4951

![](proposal_files/figure-gfm/popularity-plot-1.png)<!-- -->

From the plot we can see that on average, pop music is the most popular
and Latin music is close behind. Electronic Dance Music is the least
popular on average.

The goal of our project is to examine what makes a song popular and
whether it changes in each genre. Therefore, we will examine the
different variables and how they affect popularity in each genre,
comparing the genres against one another to find differences. The
statistical methods we aim to use will be multiple forms of graphs,
mainly scatter plots, bar plots and density curves. The graphs will
involve the popularity of a song compared to the characteristics,
mentioned in the introduction.

We have a lot of numerical data to use so we will aim to get as much
useful data onto our graphs as possible. We may also use histograms for
some specific cases such as grouping songs by length. We also plan on
using `summarise()` to show condensed data while making comparisons
between variables. One specific idea we have is grouping songs by `mode`
(whether the song is in a major or minor key) and calculating their mean
popularity to observe any difference. Lastly, a timeline of sorts is to
be made to see the change in characteristics of songs over time.

If the results were to support our hypothesis, we would expect different
characteristics making a song popular in each genre. For example, the
density plots would show a different distribution for different genres.
