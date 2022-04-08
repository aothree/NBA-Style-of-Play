# Investigating Style Of Play In The NBA

The goal of this project is to tell the story of the last decade in the NBA, through the lens of style of play.  Using a clustering model, we can contexualize and group how  teams played over the last 10 seasons.  

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


I compiled a dataframe looking at these statistics for every team in each of the last 10 seasons.  The first season, I looked at was 2013

 

