Alexandros - Rap
================

``` r
library(tidyverse)
```

    ## ── Attaching packages ─────────────────────────────────────── tidyverse 1.3.0 ──

    ## ✓ ggplot2 3.3.2     ✓ purrr   0.3.4
    ## ✓ tibble  3.0.4     ✓ dplyr   1.0.2
    ## ✓ tidyr   1.1.2     ✓ stringr 1.4.0
    ## ✓ readr   1.3.1     ✓ forcats 0.5.0

    ## ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
    ## x dplyr::filter() masks stats::filter()
    ## x dplyr::lag()    masks stats::lag()

``` r
library(here)
```

    ## here() starts at /cloud/project

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

\#\#Check popularity of a song with key

``` r
spotify_songs %>%
  filter(playlist_genre == "rap") %>%
  group_by(key) %>%
  ggplot(aes(y = track_popularity, x = key)) +
  geom_col()
```

![](Alex-s-final_files/figure-gfm/popularity-vs-key-1.png)<!-- -->

c = 0, c\# = 1, d = 2, d\# = 3,E = 4, F = 5, F\# = 6, G = 7, G\# = 8, A
= 9, A\# = 10, B = 11, NA = -1

\#\#Check popularity of a song with instrumentalness

``` r
spotify_songs %>%
  filter(playlist_genre == "rap") %>%
  #group_by(instrumentalness) %>%
  ggplot(aes(y = track_popularity, x = instrumentalness)) +
  geom_hex() #+
```

![](Alex-s-final_files/figure-gfm/popularity-vs-instrumentalness-1.png)<!-- -->

``` r
  #geom_smooth()
```

``` r
spotify_songs %>%
  filter(playlist_genre == "rap") %>%
  filter(track_popularity > 75) %>%
  ggplot(aes(y = track_popularity, x = instrumentalness)) +
  geom_hex() #+
```

![](Alex-s-final_files/figure-gfm/popularity-vs-instrumentalness-popular-1.png)<!-- -->

``` r
  #geom_smooth()
```

\#\#Check popularity of a song with duration

``` r
spotify_songs %>%
  filter(playlist_genre == "rap") %>%
  mutate(duration_minutes = duration_ms/(1000*60)) %>%
  ggplot(aes(x = duration_minutes, y = track_popularity)) +
  geom_point() +
  geom_smooth()
```

    ## `geom_smooth()` using method = 'gam' and formula 'y ~ s(x, bs = "cs")'

![](Alex-s-final_files/figure-gfm/popularity-vs-duration-1.png)<!-- -->
We can see that between 2.5-3.3 there are the most popular songs, which
makes sense since very long songs tend not to be so popular.

\#\#Check popularity of a song with tempo

``` r
spotify_songs %>%
  filter(playlist_genre == "rap") %>%
  #filter(track_popularity < 25) %>%
  ggplot(aes(x = tempo, y = track_popularity)) +
  geom_point() +
  geom_smooth()
```

    ## `geom_smooth()` using method = 'gam' and formula 'y ~ s(x, bs = "cs")'

![](Alex-s-final_files/figure-gfm/popularity-vs-tempo-general-1.png)<!-- -->

``` r
spotify_songs %>%
  filter(playlist_genre == "rap") %>%
  filter(track_popularity > 75) %>%
  ggplot(aes(x = tempo, y = track_popularity)) +
  geom_point() +
  geom_smooth()
```

    ## `geom_smooth()` using method = 'loess' and formula 'y ~ x'

![](Alex-s-final_files/figure-gfm/popularity-vs-tempo-popular-1.png)<!-- -->

\#\#Check popularity of a song with speechiness

``` r
spotify_songs %>%
  filter(playlist_genre == "rap") %>%
  ggplot(aes(y = track_popularity, x = speechiness)) +
  geom_col()
```

![](Alex-s-final_files/figure-gfm/popularity-vs-speechiness-1.png)<!-- -->

Most popular songs are below 0.25. “Speechiness detects the presence of
spoken words in a track. The more exclusively speech-like the recording
(e.g. talk show, audio book, poetry), the closer to 1.0 the attribute
value. Values above 0.66 describe tracks that are probably made entirely
of spoken words. Values between 0.33 and 0.66 describe tracks that may
contain both music and speech, either in sections or layered, including
such cases as rap music. Values below 0.33 most likely represent music
and other non-speech-like tracks.”

\#\#Check popularity of a song with mode

``` r
spotify_songs %>%
  filter(playlist_genre == "rap") %>%
  #filter(track_popularity < 75) %>%
  ggplot(aes(y = track_popularity,  x = mode)) +
  geom_col()
```

![](Alex-s-final_files/figure-gfm/popularity-vs-mode-general-1.png)<!-- -->

``` r
spotify_songs %>%
  filter(playlist_genre == "rap") %>%
  filter(track_popularity > 75) %>%
  ggplot(aes(y = track_popularity,  x = mode)) +
  geom_col()
```

![](Alex-s-final_files/figure-gfm/popularity-vs-mode-popular-1.png)<!-- -->

\#\#Check popularity of a song with danceability

``` r
spotify_songs %>%
  filter(playlist_genre == "rap") %>%
  filter(track_popularity > 75) %>%
  ggplot(aes(y = track_popularity,  x = danceability)) +
  geom_col()
```

![](Alex-s-final_files/figure-gfm/popularity-vs-danceability-1.png)<!-- -->

\#\#Check popularity of a song with release date

``` r
spotify_songs %>%
  filter(playlist_genre == "rap") %>%
  #filter(track_popularity > 75) %>%
  ggplot(aes(y = track_popularity,  x = track_album_release_date)) +
  geom_col()
```

![](Alex-s-final_files/figure-gfm/popularity-vs-releasedate-1.png)<!-- -->

``` r
spotify_songs %>%
  filter(playlist_genre == "rap") %>%
  filter(track_popularity > 75) %>%
  ggplot(aes(y = track_popularity,  x = track_album_release_date)) +
  geom_col()
```

![](Alex-s-final_files/figure-gfm/popularity-vs-releasedate-popular-1.png)<!-- -->

\#\#Check popularity of a song with energy

``` r
spotify_songs %>%
  filter(playlist_genre == "rap") %>%
  #filter(track_popularity > 75) %>%
  ggplot(aes(y = track_popularity,  x = energy)) +
  geom_col()
```

![](Alex-s-final_files/figure-gfm/popularity-vs-energy-1.png)<!-- -->

Seems like most popular are between 0.50 - 0.75. Not sure how useful it
is since we don’t have good definition of “energy”

\#\#Check popularity of a song with valence

``` r
spotify_songs %>%
  filter(playlist_genre == "rap") %>%
  #filter(track_popularity > 75) %>%
  ggplot(aes(y = track_popularity,  x = valence)) +
  geom_col()
```

![](Alex-s-final_files/figure-gfm/popularity-vs-valence-1.png)<!-- -->

``` r
spotify_songs %>%
  filter(playlist_genre == "rap") %>%
  filter(track_popularity > 75) %>%
  ggplot(aes(y = track_popularity,  x = valence)) +
  geom_col()
```

![](Alex-s-final_files/figure-gfm/popularity-vs-valence-popular-1.png)<!-- -->

\#\#Check popularity of a song with liveliness INTERESTING

``` r
spotify_songs %>%
  filter(playlist_genre == "rap") %>%
  #filter(track_popularity > 75) %>%
  ggplot(aes(y = track_popularity,  x = liveness)) +
  geom_col()
```

![](Alex-s-final_files/figure-gfm/popularity-vs-livileness-1.png)<!-- -->
