

# Investigating NBA Teams' Style Of Play Over the Last Decade

The goal of this project is to tell the story of the last decade in the NBA, through the lens of style of play.  Using a clustering model, we can contexualize and group how  teams played over the last 10 seasons.  Data analytics has had a huge impact on the game, will this be apparent in our clusters?

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

I compiled a dataframe for these statistics, for each team over the last 10 seasons.  I fed this data into a KMeans Clusters model and plotted a range of inertia scores.  The 'elbow' on this polot occurred around 3, therefore `n_clusters` was to set to 3.    

----------------------------------

## Cluster Analysis

| Stat      | Cluster 0 | Cluster 1 | Cluster 2
| ----------- | ----------- |-----------|----------|
| Year   | 2020 | 2015 | 2017|
| Frequency of All Threes  | 36.0 % | 23.9 % | 28.0 % |
| Frequency of Mid-Range Shots | 29.8 % | 41.6 % | 34.0 % |
| Offensive Rebound Percent | 25.7 % | 27.6 % | 28.1 % |
| Frequency of Transition | 14.7 % | 13.0 % | 16.6 % |

### Cluster 0
This is clearly our analytics driven cluster.  Teams in this cluster shot by far the most threes, with an average frequency of 36% (50% more than Cluster 1!).  Hand in hand with this, Cluster 0 teams shot the least amount of mid-range shots, they only shot mid-range shots at a 29.8% frequency.

Not surprisingly, the `year` makeup for this cluster is the newest--coming in at an average of 2020.  From 2020-2022 there are 90 different teams (30 teams x 3 seasons) and 85 of those 90 teams wound up in Cluster 0.  

It was very interesting to look at the oldest teams in Cluster 0.  Those were: 2015 and 2016 Atlanta Hawks, 2016 Cleveland Cavaliers, 2016 Philadelphia 76ers.  All four of those teams were memorable.  The 2015 Hawks were one of the great regular season teams in the last decade--they finished 60-22 and did it without a major star.  Maybe there was a style of play advantage they were ahead of the pack on?  The 2016 76ers were memorable for the opposite reason--they were the 3rd worst team not of the decade, but of all time.  They were in the midst of "Trusting the Process", and wound up with a 2016 record of 10-72.  Shameful, sure, but the style of play was ahead of its time.  The last team, the 2016 Cavaliers, was the only team in NBA history to come back from a 3-1 deficit in the NBA Finals.  

### Cluster 1
Cluster 1 is our old-style cluster.  Teams from this cluster shot 41.6% mid-range shots compared to only 23.9% threes.  They also had the least amount of transition in their gameplan.  They averaged transition plays 13% of the time compared to 16.6% in Cluster 2.

The average `year` for teams in the cluster is 2015.1.  Of the 109 teams in this cluster, only 5 came after 2018, and only two after 2019.  Those two teams were tremendously not-memorable, however it's still interesting to see who they were because they were two versions of the same team-- the 2020 and 2021 Spurs.  Gregg Poppovich is widely considered one of the best coaches of all time, and his resume backs it up.  But it's interesting to see him stick stubbornly to his preferred style of play while former assistants of his went the other way once they got head-coaching gigs.  Mike Budenholzer, a longtime assistant for Pop, was the coach of the aforementioned 2015-16 Hawks from Cluster 0.

### Cluster 2
Cluster 2 ended up in the middle of Clusters 0 and 1 in most key statistics.  Teams in this cluster shot threes at a 28% frequency while they shot 34% of the time from mid-range.  Interestingly, these teams did run the most--with a 16.6% frequency of transition play.  They also shot most frequently at the rim, 37.7% frequency vs 34.4% and 34.0% in the other two clusters.    

The `year` makeup was right in the middle of the other two clusters, with the average for Cluster 2 being 2016.7.  What was interesting here were two teams showing up from this current season (2022)--Toronto and Memphis.  Both of these teams had successful regular seasons, particularly Memphis who took the league by storm.  The Grizzlies were projected to finish ~8th in the West before the season, and they ended up in the 2nd spot with a 56-26 record.  Another intriguing aspect of this--Memphis' head coach is Taylor Jenkins, a former Mike Budenholzer assistant.  Again, a link back to the ahead of their time 15-16 Hawks.  Maybe Jenkins and his Grizzlies are ahead of their time in rejecting the all-in approach to analytics.  It's a more modified approach--yes they shoot more threes and less mid-range shots, but not to the extreme degree that Cluster 0 teams do.  I for one am very curious how these Grizzlies end up doing in the 2022 playoffs.

-------------

Although I intentionally excluded performance metrics from the clustering model--ultimately I wanted to know what the best style of play was over the last decade?  And what might it tell us about the best style of play for the next decade?

I added three performance metrics do the data frame to evaluate each cluster.  
* `made_playoffs` tracks whether or not the team qualified for the playoffs.
* `made_finals` tracks whether or not they made the Finals.
* `won_championship` tracks whether or not they won the title.



Everything begins and ends with the rise in popularity of the three-pointer.  As the importance of data analytics has risen in most front offices around the league, teams are embracing the "3 is more than 2" mantra.  In just 5 years (the difference in average `year` between Cluster 0 and Cluster 1), three-point frequency went up from ~24% to 36% for a 50% increase.  That is a massive overhaul in style of play!  The visual below showcases the seismic shift in three-point frequency over the last ten years:

![three point frequency by cluster](https://git.generalassemb.ly/ao/NBA_Capstone/blob/master/Visuals/Frequency%20Threes%20by%20Cluster.jpg)

The effects of the three-point boom can be seen in other, non three-point shooting, statistics.  For example, teams are punting more often on going for offensive rebounds.  Cluster 1 teams rebounded 27.6% of their own shots, whereas Cluster 0 teams only rebounded 2% less of their shots.  Why?  Going for offensive rebounds leaves your defense vulnerable to transition.  This has always been the case, but what's changed is what teams are looking to do in transition.  Instead of trying for a layup or a foul, they're hunting wide-open three point shots (efficiency!).  So our data-driven teams in Cluster 0 are deciding more often that they'd rather forego an offensive rebound in the hopes to guard against these open three-point looks.

### Efficiency, efficiency, efficiency! Is this the only way?  When does it end?
Overall, data-analytics has pushed the league to get more efficient on the offensive end.  Ten years ago the average points-per-100-possessions was 106.  That number has risen to 112 over the last decade.  

![pts/100possessions](https://git.generalassemb.ly/ao/NBA_Capstone/blob/master/Visuals/100%20Possessions%20boxplots.jpg)






