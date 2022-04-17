# Investigating NBA Teams' Style Of Play Over the Last Decade

The goal of this project is to tell the story of the last decade in the NBA through the lens of style of play.  Everything begins and ends with the three-point boom.  As the importance of data analytics has risen in front offices around the league, teams are embracing the "3 is more than 2" mantra.  Ten years ago, 22 % of an average nba team's shots were three pointers.  In 2022, that number has risen 67%, to 36.8 %.  That is a staggering overhaul in style of play!  The visuals below showcases this seismic shift in three point frequency and the resulting uptick in efficiency:

<p align="center">
  <img src="https://github.com/aothree/NBA-Style-of-Play/blob/master/Visuals/three%20point%20frequency%202013%20v%202022%20hist.png"/>
</p>

<p align="center">
  <img src="https://github.com/aothree/NBA-Style-of-Play/blob/master/Visuals/Points%20per%20100poss%20scatter.jpg"/>
</p>

This project uses a KMeans Clustering model to help contexualize exactly *how* teams have adjusted their style of play with the influx of data analytics.  Using results from the clusters, the final step was analyzing how team ultimately performed using the different styles of play.       

-----------------
# Executive Summary 
The data comes from `cleaningtheglass.com` in the form of various style of play statistics.  For the cluster model, I did not want to focus on performative statistics.  So how well a team shot, how many turnovers they averaged, things like this would influence the clusters beyond style of play.  To make sure the clusters were bourne out of stylistic differences rather than qualitative measures, I focused on the following statistics:  

* **Percent of plays in the Halfcourt**.  Out of all of a team's posessions, what percentage were played "in halfcourt" as opposed to in transition.

* **Offensive Rebound Percent**.  The percent of a teams total shots that turned into an offensive rebound.  This statistic only tracks shots that occur during a halfcourt possession.

* **Frequency of Transition**.  The percent of a team's possessions that occurred in transition.

* **Frequency of Shots at the Rim**.  The percent of a team's shots that occurred at the rim.

* **Frequency of Shots from Short Mid-Range**.  The percent of a team's shots that occurred from short mid-range.

* **Frequency of Shots from Long Mid-Range**.  The percent of a team's shots that occurred from long mid-range, or the dreaded long-two.  

* **Frequency of Shots from Mid-Range**. The percent of a team's shots that occurred from mid-range.

* **Frequency of Corner Threes**. The percent of a team's shots that were corner three pointers.

* **Frequency of Non-Corner Threes**. The percent of a team's shots that were non-corner three pointers.

* **Frequency of All Threes**. The percent of a team's shots that were three pointers.

I compiled a dataframe for these statistics, for each team over the last 10 seasons.  I fed this data into a KMeans Clusters model and plotted a range of inertia scores.  The 'elbow' on this plot occurred around 3, so `n_clusters` was to set to 3.    

----------------------------------

## Cluster Analysis

| Stat      | Cluster 0 | Cluster 1 | Cluster 2
| ----------- | ----------- |-----------|----------|
| Year   | 2020 | 2015 | 2017|
| Frequency of All Threes  | 36.0% | 23.9% | 28.0% |
| Frequency of Mid-Range Shots | 29.8% | 41.6% | 34.0% |
| Offensive Rebound Percent | 25.7% | 27.6% | 28.1% |
| Frequency of Transition | 14.7% | 13.0% | 16.6% |

### Cluster 0
This is clearly our analytics driven cluster.  Teams in this cluster shot by far the most threes, with an average frequency of 36% (50% more than Cluster 1!).  Hand in hand with this, only 29.8% of Cluster 0's shots were from the mid-range, the lowest frequency for any cluster.

Not surprisingly, the `year` makeup for this cluster skews newer--teams in this cluster had an average `year` of 2020.  This dataset had 90 different teams from 2020-2022 (30 teams x 3 seasons) and 85 of those 90 teams wound up in Cluster 0.  That alone showcases the lack of diversity in style of play in toady's NBA.  

It was very interesting to look at the oldest teams in Cluster 0.  Those teams were: 
* 2015 and 2016 Atlanta Hawks
* 2016 Cleveland Cavaliers
* 2016 Philadelphia 76ers

All four of those teams were memorable.  The 2015 Hawks were one of the great regular season teams in the last decade--they finished 60-22 and they did it without a major star.  Maybe there was a style of play advantage they were ahead of the pack on?  The 2016 76ers were memorable for the opposite reason--they were the 3rd worst team not of the decade, but of all time.  They were in the midst of "Trusting the Process", and finsihed 2016 with a record of 10-72.  Shameful, sure, but the style of play was ahead of its time.  The last team, the 2016 Cavaliers, was the only team in NBA history to come back from a 3-1 deficit in the NBA Finals.  Three consecutive versions of Lebron's Cavaliers (2017, 2018, and 2019) all showed up in Cluster 0.  

### Cluster 1
Cluster 1 is our old-style cluster.  Teams from this cluster shot 41.6% mid-range shots compared to only 23.9% threes.  They also had the least amount of transition in their gameplan--averaging 13% of their plays in transition compared to 16.6% in Cluster 2.

The average `year` for teams in the cluster is 2015.1.  Of the 109 teams in this cluster, only 5 came after 2018, and only two after 2019.  Those two teams were tremendously not-memorable, however it's still interesting to see who they were because they were two versions of the same team-- the 2020 and 2021 Spurs.  Gregg Poppovich is widely considered one of the best coaches of all time, and his resume backs it up.  But it's interesting to see him stick stubbornly to his preferred style of play while former assistants of his went the other way once they got head-coaching gigs.  Mike Budenholzer, a longtime assistant for Pop, was the coach of the aforementioned 2015-16 Hawks from Cluster 0.

### Cluster 2
Cluster 2 ended up in the middle of Clusters 0 and 1 in most key statistics.  Teams in this cluster shot threes at a 28% frequency while they shot 34% of the time from mid-range.  Interestingly, these teams did run the most--with a 16.6% frequency of transition play.  They also shot most frequently at the rim, 37.7% frequency vs 34.4% and 34.0% in the other two clusters.    

The `year` makeup was right in the middle of the other two clusters, with the average for Cluster 2 being 2016.7.  What was interesting here were two teams showing up from this current season (2022)--Toronto and Memphis.  Both of these teams had successful regular seasons, particularly Memphis who took the league by storm.  The Grizzlies were projected to finish ~8th in the West before the season, and they ended up in the 2nd spot with a 56-26 record.  Another intriguing aspect of this--Memphis' head coach is Taylor Jenkins, a former Mike Budenholzer assistant.  Again, a link back to the 'ahead-of-their-time' '15-'16 Hawks.  Maybe Jenkins and his Grizzlies are ahead of their time just like his former boss, but in a different way.  The Grizzlies are rejecting the all-in approach to analytics.  It's a more modified approach--yes they shoot more threes and less mid-range shots, but not to the extreme degree that Cluster 0 teams do.  

-------------
## Looking at Performance
I intentionally excluded performance metrics from the clustering model but ultimately I wanted to know what the best style of play was over the last decade.  

I added three performance features to the dataframe to evaluate each cluster's performance.  
* `made_playoffs` tracks whether or not the team qualified for the playoffs.
* `made_finals` tracks whether or not they made the Finals.
* `won_championship` tracks whether or not they won the title.

| Stat      | Cluster 0 | Cluster 1 | Cluster 2
| ----------- | ----------- |-----------|----------|
| Made Playoffs   | 57% | 51% | 51% |
| Made Finals  | 8.7% | 2.7% | 10% |
| Won Championship | 3.2% | 1.8% | 5.7% |

For a GM deciding on style of play for their team, of course it depends what stage your team is at.  Cluster 0 teams made the playoffs at the highest rate--57% vs 51% in the other two clusters.  So if you were a team that had not had recent success and you were trying to turn the tide and make a playoff push--the analytics style of play seems to be the best bet.  

However if you have higher goals like making the Finals and/or winning a ring, it actually appears Cluster 2's style of play is the way to go.  Teams in Cluster 2 had the highest rate of making the finals (10%) and winning the championship (5.7%).  This is refreshing information and should give some pause to the herd mentality in the league surrounding style of play.  

## Conclusions

![basketball markers viz]('https://github.com/aothree/NBA-Style-of-lay/blob/master/Visuals/basketball%20markers.png')

<p align="center">
  <img src="https://github.com/aothree/NBA-Style-of-Play/blob/master/Visuals/basketball%20markers.png" />
</p>

The rush to eschew the midrange in favor of shooting globs of threes has happened, and it's understandable.  The math behind the strategy make sense.  If you shoot 100 two point shots, and make 50% of them, you're scoring 100 points per 100 possessions.  If you shoot 100 three pointers, and make just 34% of them, you wind up with a more efficient 102 points per 100 possessions.  If you are a team in the NBA that hasn't had much success, it's hard to argue this might be the quickest way to turn things around--to be as efficient as possible and play with a data-driven approach. After all, Cluster 0 teams made the playoffs at the highest rate.  

But, this isn't the only way.  As the performance metrics for Cluster 2 show--it seems like the extreme analytical Cluster 0 style actually may not be the best way to get to the Finals and win championships.  A more moderate approach to shot selection may beneficial.  

If you're still not convinced and think nuance of style of play is a thing of the past, look no further than the 2022 Phoenix Suns.  The Suns just finished the regular season with a league-best 64-18 record, and are the favorites in Vegas to win the championship.  What did their style of play look like?  They shot the 5th *fewest* threes in the league this year--at only a 33% frequency.  What about dreaded inefficient mid-range shots?  Phoenix shot 41.7% of their shots from the midrange--the most in the league.  

Basketball is like music.  At its best when flowing with creativity.  The data analytics revolution in the NBA has tried to assert that there is one way to play.  This year, the Phoenix Suns have shown that's not true.  

## Next Steps

There are a few different roads I'd like to go down as a result of this project:

1. Try to predict how the frequency of threes will look over the next decade.  Based on the recent success of teams that don't shoot as many threes as the rest of the league (ie the 2022 Phoenix Suns), my hypothesis would be we've reached a plateau in terms of three point frequency.  I don't think average frequency will rise much higher than it currently is, there are already some signs of pullback in the visual below.  Around 2020, it seems the rate of increase is leveling off some.  But exactly where it will level off would be fun to try and predict.

<p align="center">
  <img src="https://github.com/aothree/NBA-Style-of-Play/blob/master/Visuals/resized%20requency%20three%20pointers%20shades%20of%20orange.png" />
</p>

2. Investigate how this three-point boom has changed roster composition.  Before the analytics boom, the NBA had a lot of Dennis Rodman types--players whose impact on the game had nothing to do with their ability to shoot.  Nowadays, the ability to shoot feels like a pre-requisite to playing in the NBA.  I would guess the aggregate field goal % has gone up as there are simply more shooters on the floor than their used ot be.  

3. Do a similar clustering analysis--but analyzing style of play on the defensive end.  The defensive end is often ignored (guilty!) but isjust as important to winning as offense.  How have defensive strategies evolved during the three-point boom?  How does this tie in with roster composition?  More three point threats = the need for more mobile defenders = the death of the big man?





