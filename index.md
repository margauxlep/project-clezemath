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

Gun control is one of the most controversial political topics in the United States. Being one of the world’s most liberal countries in the world, freedom one of its core values. But some could say: **“My freedom stops when that of others begins”**. And indeed, the US are regularly torn apart by mass shootings. Gun ownership and the need for regulation can seem incompatible at times. 

**How is this political debate linked to the occurrences of mass shootings? This is what we intend to find out.** This could help us understand the underlying mechanisms of this societal problem, and provide us with tools to help predict future controversy on the matter.

Analyzing quotes emanating from American newspapers in the [Quotebank dataset](https://quotebank.dlab.tools) combined with [additional data](https://www.motherjones.com/politics/2012/12/mass-shootings-mother-jones-full-data/) will help us study how these tragic events influence the media coverage and the political debate. 


<div align="center">
<img src="guns_comic.gif" />
</div>

<h1 style="color: #990000;">Are quotes about guns related to the occurence of mass shootings?</h1>

> This sickening and senseless gun violence must stop. (Bernie Sanders)

Between 2015 and 2020, **48 mass shootings** were registered, killing 396 people and injuring 895. In the same timeframe, we collected more than **79'000 quotes** from American news that were about guns and shootings in general [^1]. The first thing we wanted to see is if the occurences of these quotes was linked to the events.

[^1]: First we selected these quotes using three keywords: "gun", "shooting", "firearm" (quotes needed to contain at least one of the three in order to be selected). Once we had noticed that many quotations containing these key words were still unrelated to our topics, we decided to apply a supervised learning method to remove them from our analysis. We manually classified and labelled 1500 quotes to train the chosen Bert model (taken from Transformers library), which was used later on for the target prediction.

<iframe src="time_fatalities.html" width="100%" height=620 frameBorder="0"></iframe>

This plot shows us several interesting things. For instance, some **clear peaks in quotes seem to follow after most of the shootings**. The largest peak in fatalities happens around October 2017 and is followed by the second largest peak in quotes talking about guns.

The plot seems to make it clear that there is a correlation between the occurences of mass shootings and the number of quotes in the following days. **To confirm our intuition, we performed a Pearson correlation test** between the number of quotes on a given day and the number of days since the last shooting. This revealed a highly significant (p-value << 0.05) negative correlation between the number of quotes on a given day and the days since the last shooting. This was the expected result: **the more days since the last shooting, the rarer the quotes talking about guns and firearms**.

<h1 style="color: #990000;">What words were used the most after the shootings?</h1>


![](deco1.jpg)

We tried a machine learning approach to isolate the words that were the most related to the mass shootings. Using random forests, we selected words by features importance. This is what we got : 

<div align="center" style="width:80%, margin-left: auto; margin-right: auto;">
<img src="gun_words_feat_importances_mdpi.png" />
</div>

Es expected, we see words related to **gun shootings** in general : 
- gun, gunfire, guns, shooting, mass, etc, of course  **victims**

And also words related to the **time or place** of the event :
- school, week, wednesday, las, vegas, el, paso

But what it interesting is that we also wee words related to **law and regulation** :
- law, enforcement, illegal, congress, democrat



<h1 style="color: #990000;">What shootings generated the most reaction?</h1>

> Shocking that The Times believes a known or suspected terrorist should be able to legally purchase firearms and explosives. (Dianne Feinstein)

For each shooting, we defined a **reaction score**. The reaction score was computed as the **relative increase** between the total number of quotes during the 10 days before the shooting and the total number of quotes during the 10 days after the shooting. Although imperfect, it captures how much more (or less) the media have been talking about guns after the shooting.

The following map shows all 48 shootings by location. **The larger the circle, the larger the corresponding media outrage**. You can hover each point to get extra information about the shooting (location type, weapon type, gender of shooter...).
<iframe src="map.html" width="100%" height=500 frameBorder="0"></iframe>

<h1 style="color: #990000;">What features are likely to influence the reaction?</h1>

> 91 percent of suspected terrorists who attempted to buy guns in America walked away with the weapon they wanted. (Patrick Murphy)


Some shootings made it very clear, **the number of fatalities is not the only factor that influences the amount of reaction generated** by a shooting. Indeed, the most influential shooting according to our reaction score had only 3 fatalities. Differences like the location of the shooting (e.g. School, Religious place, Workplace) and the weapon type can influence the following media outrage, covering and debate.

<div align="center" style="width:70%, margin-left: auto; margin-right: auto;">
<img src="features.jpg" />
</div>

We ran **correlation tests** between the features and the reaction score. Very few showed to be significant (p-values were mostly larger than 0.05). But we have little data: for example, their are only three School shootings, so it is hard to find a pattern. The take-home message is simply that there are many factors that influence the amount of reaction a shooting generates, and that an exact correlation can not be found partly because of the lack of data and the lack of correlation simply.

The **shooting situation that should generate the most reaction**: shooting in airport with a high number of fatalities, shooter is an Asian male with a legal automatic weapon.<br>
The **shooting situation that should generate the least reaction**: shooting in workplace with a small number of fatalities, shooter is a white female with an illegal  weapon.

Disclaimer: these predictions are probably incorrect. Indeed, there are probably correlations between the features as well, and it might be that it is the combination of features that trigger large reactions, rather than the sum of individual influences. For example, the fact that the reaction score is on average higher for male shooters does not mean that the media is taking the gender of the shooter into account. Although there might be a link between the media's interest and the gender of the shooter, there might also be a correlation between the gender and other features, such as the number of fatalities (male shooters generating more fatalities on average).

However, these results still give an insight on some things that can trigger a larger reaction.

<h1 style="color: #990000;">Who speaks the most about guns?</h1>

> I'm a strong Second Amendment supporter as well, but I believe in responsible gun ownership (Charles Brunner)



In this section we will provide insights about profiles of speakers. As we did before, we will consider only quotes that are linked with the gun debate 10 days following each shooting recorded in the [additional data](https://www.motherjones.com/politics/2012/12/mass-shootings-mother-jones-full-data/). We focused on the 2 main following categories : gender and political party. As we wanted to highlight the polarization of the debate, we kept categories binary. Namely, looking only at male and female genders and Republican and Democratic parties.

<div align="center">
<img src="Party.png" /><img src="Gender.png" />
</div>

We can observe that views in the quotes following shootings are mostly male. However, the debate seems to split equally between democrats and republicans. The media sphere seems to be equally occupied by these two parties after shootings. Further analysis has been performed in order to see whether there was a correlation between reaction score and the share of quotes of a specific party on single shootings. It turned out to be irrelevant.

<h1 style="color: #990000;">Conclusion</h1>


With our analysis, we have given a quantitative overview of the **political debate over firearms and gun control in the US**. We have shown that **talk on the matter is related to occurences of mass shootings**, but also that the mediatic reaction for a given shooting is **not only proportional to the number of victims**. Our word occurences analysis confirmed our intuition that after a shooting has happened, quotes about it don't only focus on the nature of the event (gun shooting, victims where and when) but also **engages political and legal questions**. On this matter, we saw that public speaking on the matter comprises quite equally Democrats and Republicans. However, even though the subject of the debate is the same, their opinions on the matter may well not be the same! This may be a good avenue for further inquiries.

![](deco2.jpg)


----

## Thank you for your interest!
The Cle(ment)Ze(wei)Ma(rgaux)Th(omas) team
<div align="center" style="width:70%">
<img src="clezemath.jpg" />
</div>
