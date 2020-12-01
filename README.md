Exploring the Factors of Song Popularity
================
by Louhavidandros

# Summary

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
making songs popular. Finally we planned to look at how the
characteristics of popular songs have changed over time, and to predict
what characteristics a popular song might have if it was released next
year.

Prior to conducting any analysis the data set was cleaned as best we
could by filtering for each genre and removing all repeated songs (there
were just shy of 5000 songs which appeared in more than one playlist in
a given genre). This way songs could appear multiple times if their
genre is ambiguous, but repeats will not impact the analysis of one
genre by itself.

To begin with, we decided to do a genre by genre analysis of each
variable by creating scatter plots with a `geom_smooth` line, as well as
a linear model which would use every numerical variable as an
explanatory variable to try and predict track popularity. The scatter
plots were unsuccessful however, and the linear model we produced had an
R squared value of 0.09 and an rmse value of 22.5 which means that
either the model does not explain the variable and another type of model
should have been used, or that the variables may not explain the data
well. However, since we have not learned other models we decided to
examine in further detail the second case.

## Density and Ridge Plots

Consequently, we changed the way we were approaching the problem. To
begin with, we created a new variable - `popularity_level` - by
categorising song’s popularity as high, fairly high, low and very low
based on which quartile they fell into. This was done separately for
each genre, this way there was a roughly even number of songs in each
popularity level in each genre. For every genre we then looked at only
the “High” and “Very Low” brackets of popularity, and for each variable
we created a density plot that showed what values were most frequent in
each popularity level. For example:

![](README_files/figure-gfm/pop-density-example-1.png)<!-- -->

This graph shows the distribution of danceability levels of pop songs in
the highest and lowest popularity brackets. The range of values where
the red line is higher than the blue was defined as the optimal range
for song popularity, as this is where if you picked a pop song at random
you would have a higher chance of it being very popular than being very
unpopular.

Ridge plots were made where each row was a density plot for a certain
variable and all genres were stacked on top of each other so that
comparisons could be made. For example:

![](README_files/figure-gfm/ridge-plot-1.png)<!-- -->

We can see that rock is on average the least danceable as its
distribution appears to have been shifted to the left. Danceability has
a negligible effect on the likelihood of popularity for EDM music, and
only a very small effect for R\&B. For pop, rap and latin and rock
however, a high danceability leads to a higher likelihood of a song
being popular.

These graphs were made for every variable which showed useful
information.

## Multiple Variable Analysis

After having looked at individual variables, we explored a combination
of variables; The combination of danceability, valence and energy into
one variable showed some interesting results.

![](README_files/figure-gfm/pop-multiple-variable-analysis-1-1.png)<!-- -->

![](README_files/figure-gfm/multiple-variable-analysis-2-1.png)<!-- -->

As shown in graphs, the songs in the “High” bracket for popularity also
had the highest value for this new variable in 4 out of the 6 genres.
The 2 genres in which “High” wasn’t were R\&B and Latin; for Latin
however it was a very close second. This shows that popular songs in
general, throughout most genres, are more danceable, energetic and
happy.

## Changes in Trends Over Time

Finally we decided to explore how the trends of popular songs have
changed over time. Models were fitted to predict each numeric variable
using the song release date as the explanatory variable to see whether
there was any relationship between when a song was released and the
level of a certain variable it had.

## Conclusion

Whilst we did not achieve our goal by the expected means, we
successfully identified many characteristics which would give a song the
highest likelihood of it being popular. For example, a song with a
duration between 180-220 seconds has a much higher chance of being
popular in all genres except rock.

## Evaluation

We did our best to make the data set as appropriate as possible, however
there were a few problems with our data set which we could not change
and that may have lead to inaccuracies in our result:

The dataset contained roughly 28,000 songs, a small fraction of the
songs released in the past 50 years.

Old songs released long before Spotify was released have their
popularity judged by modern standards rather than the standards of their
time.

The data categorized a song’s genre based on the genre of the playlist
it was in which lead to some song’s genres being mislabeled.

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
