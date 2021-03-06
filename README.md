Watching Liverpool and Man City fighting for the top spot in the the ongoing EPL and bored on a weekend I got curious to come up with metrics to quantify such intense rivalry across the length of a long season. Who likes a dull league where the top spot gets sealed only after a few games. Metrics are useful as an analysis tool and a way to look at subjective elemtents of past data (competition in the league in this case). These representations can be useful in certain modeling tasks such as a regression model of TRP (viewership etc).

I used the historical EPL data here: https://datahub.io/sports-data/english-premier-league to compute the metrics over previous seasons. The raw data has information about teams and results of each match. I aggreated this data and prepared results table at the end of each week/round across all seasons.

__Metric 1__ (_Rank change_): <br>
Given the results table over two consequetive weeks this metric computes the the sum of changes in the leader board positions compared with the previous week. For example given this data over two weeks:


| Week-1 | Week-2 |
| --- | --- |
| a | a |
| b | c |
| c | d |


the metric outputs a value of 2 for round 2.

__Metric-2__ (_Bag size_): <br>
This metric computes how many teams are within a certain points difference of each position, summed across every position on the leader board. The intuition behind the metric goes that more the teams are closer to each other in term of number of points more the interest in the league is alive (Man United, Arsenal, Tottenham and Chelsea fighting for the position in top 4 and a chance to play the champions league. Consider the leaderboard for week k.


| Club | Points |
| --- | --- |
| a | 80 |
| b | 78 |
| c | 75 |
| d | 70 |



with the points diff of 3 (one match) the metric outputs a value of (1 + 2 + 1 + 0) = 4 for this round. a's bag has {b} in it; b has {a, c} while d has none.

__Metric-3__ (_Rank weight bag size_): <br>

Bag sizes are inverse weighted as per the position on the leaderboard. Intuitively there is most interest in fight for higher ranks up the leaderboard. Time decay weights could be useful to highlight changes in the end of season but wasn't implemented here (time weight bag size).

The plots in the ipyhon notebook and the attached html (aggregated across season and variation in a single season) compare each metric values across seasons and for sections of the leaderboard (top position, top 4, relegation zone and full leaderboard) in search of interesting insights across seasons. Higher the y-axis metric value in the plot signifies higher competition for the season/round etc.

Invite the subject matter experts and fans to comment send feedback/validate/in-validate the findings in the plots for this fun little project.

See the ipython notebook for implementaiton of the metrics and the markdown directory for the output plots.
