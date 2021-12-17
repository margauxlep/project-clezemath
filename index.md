<head>
 <style>
    
  .main-content {max-width: 100%;}
  .large_content {max-width:100%;}
  
  .page-header {
  color: #ffffff;
  text-align: center;
  background-color: #870000;
  background-image: url("background.jpg");
  background-size: 100%;
  
  @include large {
    padding: 5rem 6rem;
  }

  @include medium {
    padding: 3rem 4rem;
  }

  @include small {
    padding: 2rem 1rem;
  }
}
  
  h1 {
    font-weight: normal;
  }
   
 </style>
</head>

Gun control is one of the most controversial political topics in the United States. Being one of the world’s most liberal countries in the world, freedom one of its core values. But gun ownership and the need for regulation can seem incompatible at times.

**How is this political debate linked to the occurrences of mass shootings? This is what we intend to find out.**

![](guns_comic.gif)

Analyzing quotes emanating from American newspapers in the [Quotebank dataset](https://quotebank.dlab.tools) combined with [additional data](https://www.motherjones.com/politics/2012/12/mass-shootings-mother-jones-full-data/) will help us study how these tragic events influence the media coverage and the political debate. 

<h1 style="color: red;">Are quotes about guns related to the occurence of mass shootings?</h1>

Between 2015 and 2020, 48 shootings were registered, killing 396 people and injuring 895. In the same timeframe, we collected more than 79'000 quotes from American news that were about guns and shootings in general (LINK to how we collected these quotes). The first thing we wanted to see is if the occurences of these quotes was linked to the events.

<iframe src="time_fatalities.html" width="100%" height=620 frameBorder="0"></iframe>

This plot shows us several interesting things. For example, the largest peak in fatalities happens around october 2017. It is followed by the second largest peak in quotes talking about guns. We can also see that the peak of quotes is generally maximal two days after the shooting.

The plot seems to make it clear that there is a correlation between the occurences of mass shootings and the number of quotes in the following days. To confirm our intuition, we performed a Pearson correlation test between the number of quotes in the subset and the number of days since the last shooting. This revealed a highly significant (p-value << 0.05) **negative correlation** between the number of quotes on a given day and the days since the last shooting. This was the expected result: **the more days since the last shooting, the rarer the quotes talking about guns and firearms**.

<h1>What words were used the most after the shootings?</h1>

We tried a machine learning approach to isolate the words that were the most related to the mass shootings. Using random forests, we selected words by features importance. This is what we got : 

[insert image]

even though the results are not very significative, we may be seing some pattern emerging. **Talk about state** and words like '**help**'. 

## What shootings generated the most reaction?

The following map shows all 48 shootings by location. The larger the circle, the larger the corresponding media outrage.
<iframe src="map.html" width="100%" height=500 frameBorder="0"></iframe>

## What features are likely to influence the reaction?

List of features and show plots about average reaction score by feature

## Who speaks the most about guns?

Clement.

----

## More on our methods : 

## How we selected the quotes
Firstly, we filtered the Quotebank dataset through the key words "gun", "shooting" and "firearm".
Once we had noticed that many quotations containing these key words were still unrelated to our topics, we decided to apply a supervised learning method to remove them from our analysis. We manually classified and labelled 1500 quotes to train the chosen Bert model, which was used later on for the target prediction.

## Data used
As our goal was to analyse the relationship between mass shootings and _ _talk_ _ about mass shootings we had to use two different datasets. For the shootings, we used the **"Mother Jone's" dataset**, that we got from https://data.world/awram/us-mass-shootings. This dataset gave us basic information (e.g. date, number of fatalities) about each shooting that occured in the USA between 2015 and 2020, adding also some interesting features such as location, age and gender of the shooter, etc. Our other source of data was the **Quotebank data set** [INSERT REF], consisting of over 170 mio of quotes emanating from american newspapers. We focused our research on the time lapse between 2015 and 2020.

