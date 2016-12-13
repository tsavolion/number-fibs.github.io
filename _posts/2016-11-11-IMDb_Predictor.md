IMDb Predictor:

Among the top 250 movies by IMDb Ratings, I created a tool able to approximate the IMDb rating of a movie based on the talent attached.

I created a metric for Director, Writer, and Actor success. These metrics were fairly simple. I gave each talent a “credit” for each time they appeared in a top 250 movie in that capacity. Below, please see the scores of leading men:

![](https://tsavolion.github.io/images/project6images/p61.png)

Here we see Leonardo DiCaprio, with 6 appearances as a leading man in the top 250 movies, as the lead actor most indicative of a good film.

You can see the second billed actor’s here:

![](https://tsavolion.github.io/images/project6images/p62.png)

Third billed:

![](https://tsavolion.github.io/images/project6images/p63.png)

And fourth billed actors:

 ![](https://tsavolion.github.io/images/project6images/p64.png)

The higher the count, the more top movies this talent has appeared in. Thus, my interpretation is that these actors being included in a movie indicate its quality. So if an actor that is frequently in top movies is cast in a new movie, it’s a good sign that the movie will succeed.

Similarly we can see the influence writers or writer teams have on the quality of movies.

![](https://tsavolion.github.io/images/project6images/p65.png)

And finally, the influence of top directors:

![](https://tsavolion.github.io/images/project6images/p66.png)

This method could be scaled to a wider range of movies by using an average of the Rotten Tomatoes Score scaled between -1 and 1 in place of appearances in the Top 250 Films.

I created an aggregate score called “Starpower” which adds up all the “counts” of the talent in a film. This is operating on the logic that the more times talent has been in good movies, the higher the likelihood of the movie containing them being good.

From this, I derived a correlation between “Starpower” and “IMDb Ratings”:

 ![](https://tsavolion.github.io/images/project6images/p67.png)

For comparison, I also found the correlation of all the other factors to IMDb Rating.

Director:

![](https://tsavolion.github.io/images/project6images/p68.png)

Writer:

![](https://tsavolion.github.io/images/project6images/p69.png)

First Billed Actor:

![](https://tsavolion.github.io/images/project6images/p610.png)

Second Billed Actor:

![](https://tsavolion.github.io/images/project6images/p611.png)

Third Billed Actor:

![](https://tsavolion.github.io/images/project6images/p612.png)

Fourth Billed Actor:

![](https://tsavolion.github.io/images/project6images/p613.png)


The value of “Starpower” is far more correlated to the IMDb Rating than any other factor, with “Director” being the next most correlated.  

Below is a scatter plot of “starpower” vs “IMDbRating”:

![](https://tsavolion.github.io/images/project6images/p614.png)



And here is “dircount” vs “IMDbRating”:

![](https://tsavolion.github.io/images/project6images/p615.png)



Through this, I am able to input “Starpower” in order to predict the IMDb Rating of a film based on the talent attached using a Random Forest Regressor:

![](https://tsavolion.github.io/images/project6images/p616.png)



Looking at the importance of each of the features used to predict IMDb Rating reveals that Starpower is the most important feature, followed by “dircount”:

![](https://tsavolion.github.io/images/project6images/p617.png)


When we remove “starpower” altogether, we can see how the features’ importance changes without the aggregator:

![](https://tsavolion.github.io/images/project6images/p618.png)



Dircount comes out to be the most important feature remaining. When we attempt to predict IMDb Rating without Starpower as a feature, we see the following:

![](https://tsavolion.github.io/images/project6images/p619.png)



 Removing one factor (starpower) shows that the key factor (dircount) is so important. This shows that starpower is not significantly more helpful than just the dircount.
