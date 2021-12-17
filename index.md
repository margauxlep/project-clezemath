<head>
 <style>
    
  .main-content {max-width: 100%;}
  .large_content {max-width: 100%;}
  
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
   
 </style>
</head>

Gun control is one of the most controversial political topics in the United States. Being one of the world’s most liberal countries in the world, freedom one of its core values. But gun ownership and the need for regulation can seem incompatible at times.

**How is this political debate linked to the occurrences of mass shootings? This is what we intend to find out.**

![](guns_comic.gif)

Analyzing quotes emanating from American newspapers in the [Quotebank dataset](https://quotebank.dlab.tools) combined with [additional data](https://www.motherjones.com/politics/2012/12/mass-shootings-mother-jones-full-data/) will help us study how these tragic events influence the media coverage and the political debate. 

<h1 style="color: #990000;">Are quotes about guns related to the occurence of mass shootings?</h1>

Between 2015 and 2020, 48 shootings were registered, killing 396 people and injuring 895. In the same timeframe, we collected more than 79'000 quotes from American news that were about guns and shootings in general (LINK to how we collected these quotes). The first thing we wanted to see is if the occurences of these quotes was linked to the events.

<iframe src="time_fatalities.html" width="100%" height=620 frameBorder="0"></iframe>

This plot shows us several interesting things. For instance, some clear peaks in quotes (in blue) seem to follow after most of the shootings (in red). the largest peak in fatalities happens around October 2017 and is followed by the second largest peak in quotes talking about guns.

The plot seems to make it clear that there is a correlation between the occurences of mass shootings and the number of quotes in the following days. To confirm our intuition, we performed a Pearson correlation test between the number of quotes on a given day and the number of days since the last shooting. This revealed a highly significant (p-value << 0.05) negative correlation between the number of quotes on a given day and the days since the last shooting. This was the expected result: **the more days since the last shooting, the rarer the quotes talking about guns and firearms**.

<h1 style="color: #990000;">What words were used the most after the shootings?</h1>

We tried a machine learning approach to isolate the words that were the most related to the mass shootings. Using random forests, we selected words by features importance. This is what we got : 

[insert image]

even though the results are not very significative, we may be seing some pattern emerging. **Talk about state** and words like '**help**'. 

<h1 style="color: #990000;">What shootings generated the most reaction?</h1>

For each shooting, we defined a reaction score. The reaction score was computed as the relative increase between the total number of quotes before the shooting and the total number of quotes after the shooting. Although imperfect, it captures how much more (or less) the media have been talking about guns after the shooting.

The following map shows all 48 shootings by location. The larger the circle, the larger the corresponding media outrage. You can hover each point to get extra information about the shooting (location type, weapon type, gender of shooter...).
<iframe src="map.html" width="100%" height=500 frameBorder="0"></iframe>

<h1 style="color: #990000;">What features are likely to influence the reaction?</h1>

List of features and show plots about average reaction score by feature

<h1 style="color: #990000;">Who speaks the most about guns?</h1>

Clement.

