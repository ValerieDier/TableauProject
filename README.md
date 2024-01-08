# Final-Project-Tableau

## Project/Goals
Use Tableau to create visualizations from the FAA Wildlife Strike Dataset that help identify patterns, outliers and generate prompts for further investigations into the data.  

Consider the audiences who may be interested in such data and findings; create a dashboard to communicate insights to those audiences.

## Process
* Examine the data to understand the columns and data types therein.  
* Consider the possibility of creating hierarchies with the columns.  
* Determine the timespan of the data and whether aspects like "partial years" could impact analyses
* Verify how data is recorded:  one strike incident per row/record.  
* Create early visualizations to drive questions.  
* Create the visualizations to help answer those questions, or redirect the analysis. 
* Assemble a dashboard to present insights.  


## Results

### Early visualizations
The FAA Wildlife Strike Database was chosen as it presented an opportunity to examine a dataset that had both commercial and non-commercial impacts, while incorporating some
categorical data into the analyses, which hadn't been broached very much in the LHL material to date.

Several early visualizations were created such as a bubble chart of wildlife strikes per time of day and phase of flight.  It was quickly observed that most strikes occur during
the day and in the early and late phases of a flight.  Later analyses prompted a 'split' in this chart to show these numbers by quarter using the pages shelf (in the Marks card).

Early visualizations of strike counts against time of year showed strikes are highest in the third quarter; this is supported by the background reading done on the FAA's website.  This 
prompted further visualizations to examine which species are struck in what numbers in each quarter, with a (dense) ranking done over a year.  This demonstrated that largely
two species figure highly as the #1 ranked by strike count for the dataset.

A first map visualization displayed strike counts by state with the pages shelf used to show this for each year (being careful to exclude 2015 as data collection ended after May).
The data was later displayed to indicate a ranking (by colour) with percent of total displayed, which helped identify a core of four states that consistently top the strike ranking.

The first couple visualizations of damage severity from strikes by species revealed a density of data making it difficult to quickly select any given group of species for heaviest
impact.  Some species are larger, cause more damage, and may be struck less frequently while others may be smaller, struck more frequently (or in flocks), and cause a moderate
amount of damage.  This prompted some questions with regards to attaching any cost drivers to certain strike profiles.  Visualizations were created to get a sense of average cost per
strike on any given species regardless of damage severity incurred.  Clustering efforts were arduous given the categorical nature of the data - with relatively little instruction for
up-front handling or back-end metrics analysis - and the results obtained were difficult to reconcile with earlier visualizations indicating certain species and their strike profiles.

### Questions Prompted

#### 1.	During what phase of flight and time of day do most strikes occur?
Most strikes occur during the day.  Without flight data (number of flights on average taking off or landing per hour) it is hard to say if it’s simply due to the number of 
flights operating during the day as opposed to during the night.  The strikes are most numerous during approach, take-off and landing.  There are exceptions in Q1 and Q3 where
nighttime approach figures in the high-strike zone.

For further investigation:  Are costs higher in any given TOD? Cost per hour would be higher during daytime hours given the above observation.

#### 2.	Are there certain species struck more so than others, per quarter, over the span of the dataset?
There’s a strong pattern of strikes on Mourning Doves in the early 2000’s:  it is ranked the top most struck species in most years, and this is always in Q3.  By the latter half 
of the 2000’s (2007 onward), the Barn Swallow is ranked the top most species in most years out to 2015 (end of dataset), also consistently in Q3.

For further investigation:  where are the Mourning Dove strikes concentrated, if indeed they’re concentrated perhaps due to habitat habits.  Similarly for the Barn Swallow.  

Are the strikes for these two species happening largely in one or two states?  Has there been a change in their preferred habitats over time?  This data, paired with climate or 
migratory path data might yield insights for more effective strike mitigation.

#### 3.	Has the average cost per strike trended up, down or otherwise over the range of the dataset?
Running cost over time had two interesting spikes over the range of the dataset.  The first one in 2001 and the second in 2009.  In 2001 the number of strikes month over month 
from the start (December 2000) to the end of the spike (January 2001) weren’t much higher, but the cost was nearly double.  Similarly in 2009, the number of strikes at the start 
of the spike in December 2008 wasn’t much lower than the number of strikes in January 2009, but the cost climbed significantly (magnitudes, 100X).  Presumably those strikes 
involved larger species capable of inflicting more damage on an engine, or, a large flock of moderate-to-small species flying in a dense enough formation to severely damage an 
engine.

Looking at the running average cost per strike displayed annually, there was a spike in 2001, after which it trended *almost* monotonically downward to 2015:  there was one 
exception in 2009, then the descent resumed.  Overall, it’s a downward trend.  However, more granularity in the inputs delivers more granular observations, as explained below.

Looking at the running average cost per strike displayed monthly, the two aforementioned spikes are seen again.  However, it’s important to note that the first couple months of 
running average cost per strike in the trendline may not be very informative as the average would have been comprised of far fewer datapoints as compared to the running average 
calculated as one advances through the dataset.  They have therefore been excluded using a filter on the visual. 

There has been increased reporting in aviation-related wildlife strikes, particularly after US Airways 1549 in January 2009 where a passenger plane was forced to land on the 
Hudson river following a wildlife strike.  Increased reporting normally leads to increased study of the data (provided there’s a budget), and the accompanying mitigation efforts 
may be paying dividends.  This may help to explain the overall downward trend in running average cost per strike. 

For further investigation: it would be good to examine whether it’s the really expensive strikes that are trending down or if it’s a collection of moderately-costly strikes that 
are decreasing.  It depends which species they’re seeing the most success with.

#### 4.	Do some species do more damage than others?  
The simple answer is the larger ones do seem to fall under the more severe damage categories, such as elk, deer, Canada goose, coyotes, eagles, hawks and egrets.  The more complex
answer has to first ask what’s considered “more damage”: cost in one strike?  Cost over a quarter or year?  Cost in a given location or over several states?
 
For further investigation: One could focus on the two most severe categories and put them in one ‘bucket’ and then the two less severe categories in another ‘bucket’, bring in 
the cost information, and see what drives cost more.  It could be useful to see if the strikes in the more severe categories tend to be lower-frequency and higher-cost, and 
similarly see if the lower severity strikes tend to be higher-frequency and lower-cost, or if, in fact, there are strikes that occur more frequently in the more severe categories 
and if there are low-frequency strikes in the less severe categories.  The challenge is in finding the right axes along which to unpack the cost drivers behind the strikes.  A 
clustering effort was started in earnest but required a greater understanding of the algorithm used (the distance and variance measures) to reconcile the model results against the
visualizations generated up to that point.

#### 5.	What would clustering tell us in terms of typical “strike profiles”? 
The clusters taking Species into account, alongside Phase of Flight and Time of Day, or just Species and one or the other of the two dimensions, rarely show the Barn Swallow 
(only the clustering effort with 12 clusters).  The Barn Swallow featured highly in the ranking of the sum of Number of Strikes by quarter every year.  If the Barn Swallow is 
quite frequently hit, which would run up a high number of strikes in any given quarter of any given year, these strike incidents could be spread throughout all or many of the 
Phase of Flight values and Time of Day values available, forming no clear pattern for strikes on the Barn Swallow.

Clusters2 results were set aside as potentially lower value as only the first four clusters contained thousands of items while all other clusters (there are 12 including the “not 
clustered”) contained fewer than 300 items, some reaching as low as 22.  This is considered against a 28,298 record dataset.

It is important to note that in examining the Describe Clusters table, the “Most Common” header shows the most common value for a given categorical feature within each cluster.  
Having examined these values for the Clusters 1 and Clusters 3 results, it was interesting to see that Mourning Dove and Hermit Thrush figured in the “Most Common” section of the 
cluster description.  The Mourning Dove was highlighted as a highly struck species in prior visualizations, however the Hermit Thrush was not.  It was the Barn Swallow that 
surfaced as the number 1 ranked species for strikes after the mid-2000’s.  As proposed above, it could be that the Barn Swallow simply does not present a profile, but rather, is 
struck in such numbers throughout many times of day and phases of flight, explaining its rank but lack of clear pattern.

The ”Most Common” results in the cluster descriptions, however, defy what is observed in the bubble visualizations.  The Mourning Dove is featured as struck mainly during the day 
while the Hermit Thrush is shown as being struck mainly at night.  The opposite seems true in the cluster descriptions’ “Most Common” information.  This remains to be understood.

For further investigation: How do the strike distributions of the top-struck species from the highlight table look when Phase of Flight and Time of Day are taken into account?  
  
Do the species primarily appear in certain times or are their strikes spread throughout the day and flight phases, offering no clear path to mitigation?

#### 6.	Have the high-strike regions changed much over the range of time in the dataset?

Results and analysis from the map visualization must be discounted (i.e. tempered).  The dataset only gave “Origin State”, not “Destination State”, which will wrongly attribute 
approach and landing-related strikes to the airport from which the aircraft departed.

The strikes reported are highest in California, Texas, Florida, and New York, with the occasional interior state appearing in the top five by total annual strikes.  The first 
four are consistently in the top five ranking throughout the range of the dataset.  

For further investigation:  Could it be the same four states and one ‘variable’ due to volume of flights?  Would need flight data here again.  Additionally, destination state 
should be provided to correctly attribute the strikes to the state of the strike location.



## Challenges 

#### Some datasets present questions and insights for many groups
The over-arching question that comes to mind after viewing charts displaying most-struck species, high-strike states by year, running average cost per strike, etc, is what’s 
driving the analysis?  If it’s regulatory drivers, then the focus is on ecological analyses in terms of most-struck species and the regions it’s occurring, whether the 
trend is changing over time, etc.  An environmental team would have to demonstrate its compliance to mitigation programs regulating efforts to protect the local fauna.  If the 
focus is on safety impacts, the emphasis will be on those strikes that have severely hampered operation of the aircraft.  If it’s commercial impacts driving the analysis, the 
focus is on costs over time as mitigation efforts are applied, and where budgets might be better spent to obtain the greatest gains.

The good news is that in building the dashboards - one for environmental compliance/strike reduction and one for commercial teams - some intersections were uncovered and this 
demonstrates an opportunity to have often-siloed teams collaborate on goals.

#### Heavy on Categorical Data
Categorical data lends itself less obviously to forecasting or regression, and is still challenging in a clustering exercise.  Visualizing the results of a clustering exercise
on categorical data is also a challenge.

#### Location Ambiguity
The LHL-provided cleaned dataset contains “Origin State”, but not a destination state.  The original FAA Wildlife Strike database contained somewhat more detailed and accurate 
information around suspected location of strike, which is particularly significant for strikes on approach and landing.  In those cases, the assigned Origin State is getting a 
wildlife strike erroneously.
a.	Unfortunately, I do not have landing location, and therefore cannot apply logic to assign strikes and their associated data (damage, etc) to the proper location.
b.	The original FAA Wildlife Strike Database had this information, albeit perhaps not in a Tableau-friendly format (might have required some string cleaning first).

#### Hierarchy would not respect taxonomy
The Wildlife columns need to be understood for hierarchal purposes, as they do not respect taxonomy (classification rules).  The wildlife columns given were: 
a.	Wildlife: Animal Category
b.	Wildlife: Species Order
c.	Wildlife: Species Group
d.	Wildlife: Species

“Wildlife: Species” was selected for analyses and it was decided *not* to create a hierarchy out of these somewhat disparate columns, i.e. "Wildlife: Species" at times it 
represents a more granular identification on the "Wildlife Species: Group" column (e.g. going from Doves to Mourning Dove).  At other times, it seems to 
represent a selection where multiple other species were identified in the "Wildlife Species: Group" column (e.g. going from Dogs, wolves and foxes narrowed to domestic dog).  

“Wildlife: Species” could be the result of the lab testing done on snarge, or simply a final identification on a carcass, to confirm the species, which would be applicable in 
both cases described above.

Given the taxonomic incongruence and the limited utility in the other Wildlife columns, it was decided not to create a hierarchy out of these columns as they would not prove 
useful in the analyses.

#### Dataset timespan
The collection of data ends after May 2015, often requiring that 2015 data be filtered out to avoid impacting annual tallies.


## Future Goals
The questions explored in the sections above offer avenues for further investigation.  The main points to highlight follow:

1. Location data for a strike needs to be more accurate than simply supplying the point of departure of a flight.
2. Cost drivers need to be further explored to give more of a defined framework for investigation how financial impacts may be reduced.
3. Clustering efforts need to be informed by other studies done with a heavy reliance on categorical data to help establish a 'strike profile' that may help predict a given
damage severity or costs.  This could, in the same effort, give a sense to environmental teams which species pose the most risk to aircraft operational safety so that their 
inputs may be used to reduce the risks.
