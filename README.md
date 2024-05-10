# Introduction
## Background
This Jupyter Notebook aims to predict the popularity of a song based on its characteristics. This problem matters because knowing what makes songs popular helps musical artists share their work and connect with as many fans as possible. Music is fundamental in uniting communities and enriching culture, and it is by maximizing its popularity that a song reaches its true potential to transform the lives of its listeners.

Results of this model could not only be used to predict how a song is likely to spread worldwide, but they can also be used to analyze cultural trends over time. What makes a song popular now will likely not be what makes it popular in a decade, and especially with an increasingly connected digital world, information flows more quickly than ever. Comparing song popularity indicators over time can be used to indicate how historical events and trends influence what music the general population likes to consume, as well as where this consumption desire is likely to head in the future. Predicting this song popularity will help musicians most effectively connect with a changing global listening population.
## Dataset
The source dataset for this notebook can be accessed [here](https://www.kaggle.com/datasets/maharshipandya/-spotify-tracks-dataset/data). The original dataset consists of 114,000 records of songs pulled directly from the Spotify API. Spotify is the most popular music-streaming platform in the world, and it also maintains high-quality information about each of its audio files. Each song contains the following information, not all-inclusive:


*   Identification information such as its title, artist/s, attatched album, and genre
*   Quantitative information such as song duration, beats per minute, and volume distribution
*   Qualitative attributes, such as danceability, energy, and vocalness, translated into a normalized score


For this notebook, the 'popularity' attribute is being separated and used as the label because this is what the model will predict.

# Analysis and Conclusions


In this project, we performed a variety of models on a feature engineered dataset on Spotify data to predict a song's popularity. We found that our regression models were marginally improved when ensembled, though we still found the results underwhelming. However, there are a couple of explanations for the poor performance.

1. As seen in our data exploration, much of our features are not normally distributed and have little correlation with popularity. Furthermore, many of our features do not necessarily have a linear relationship with popularity, which can also contribute to poor model performance.
2. Some of our features are inherently categorical. Genre, for example, is a categorical feature, and though we one-hot encoded it, regression models may not handle these features well.
3. Regression models are heavily skewed by outliers. Song popularity inherently has a lot of outliers, since there several big big international hits and a lot of songs that are incredibly obscure. These songs can easily lead to poor performance.

After seeing underwhelming performance with regression models, we shifted to looking at classification models. We opted to us a threshold of 50 since it was an easy choice to make. We also looked at the histogram of popularity in our dataset and found that the majority of songs have incredibly low popularity. Thus, we decided that songs with a popularity above 50 could be considered "popular." We found that classification models performed pretty well on our dataset, though ensembling the models we chose only marginally improved performance. However, we found that GNB performed considerably worse than the other models. There are a few explanations for this.

1. GNB has been found to perform much better on categorical data than numerical data. Most of our data is numerical, which means that the model is inherently not suited for the work we want to do.
2. Even if GNB could perform well on numerical data, we did not normalize our features, which could have negatively impacted the model's performance.

While these may not necessarily be the reason why GNB performed poorly on our dataset, they may explain the discrepancy compared to our other models, which performed better. There are a couple explanations why

1. AdaBoost and Random Forest are both better suited for non-linear relationships, which as shown in our data exploration, our data has.
2. Both classifiers are also based on ensembling techniques, which may inherently lead to better performance

Regardless of the data, we can conclude that our classification performed significantly better than our regression models.
