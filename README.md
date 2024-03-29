# Determining the most valuable attackers in Europe's Top 5 Soccer Leagues based on the percentage of Goals and Assists they contributed to their team in the 2018-19 season.

How does one truly measure the impact of an attacker on their team? While people in the Sports Analytics world would point you to all sorts of advanced metrics (which certainly help with painting a picture of a player), sometimes it’s also helpful to look at the 2 most well known categories: Goals and Assists. As you could tell by the title, this article will look at the best attacker on each team by doing exactly that. For each of the top 5 leagues in the 2018/19 season, I created a dataset that lists that player with the most combined Goals and assists for their team, and then I took that number as a percentage of the team’s total Goals and Assists.  I originally was going to look at the top Goal scorer and Assister for each team separately, but I feel that combining the two categories can give a better picture of who not only excels at one category but can do both jobs well. Teams are also color-coded according to their final position in their respective leagues; what was accomplished by this was examining how teams at all levels of their league table had players who were producing similar G+A percentages, but doing so at different scales of total G+A. For this analysis I will be examining and visualizing the data from each league separately from each other, in order to make the data easier to read and to allow myself to make some observations that might pertain only to a certain league. Teams and players are organized based on how they placed in the 2018-19 season: either Champion, Qualified for European Competition (either through their final league position or by them/another team winning a cup competition), Upper half of the table, Lower half of the table, and finally the relegated teams. If two players tied in their total numbers for G+A for a single team, then they’re listed together  on the graph as a single dot.

### La Liga
```{r plotly1, fig.width=8, fig.height=6, message = FALSE}
# Generating a Graph of La Liga's Top Attackers

library(plotly)
pal <- c("blue", "green", "purple", "yellow", "orange", "red")
pal <- setNames(pal, c("Champion", "Qualified for European Competition", "Qualified for European Competition (Cup Competition)", "Upper Mid-Table", "Lower Mid-Table", "Relegated"))

x <- list(
  title = "Goals"
)
y <- list(
  title = "Assists"
)
p <- plot_ly(data = Goals.Assists.La.Liga2, x = ~Individual.Goals, y = ~Individual.Assists, text = ~paste("Player: ", X.U.FEFF.Top.Goalscorer.Assister ,'<br>Team:', Club, '<br>', Percentage*100, "% of Total Team G+A"), color = ~Result, colors = pal) %>%
  layout(title = "Top attacker for each La Liga team", xaxis = x, yaxis = y)

ggplotly(p)

options(browser = 'false')
api_create(p, filename = "La-Liga")

```
### [Link to La Liga Graph](https://plot.ly/~bdominique/13)

It’s no secret that Lionel Messi is Barcelona’s best attacker, but the graph above clearly illustrates just how much of a monster he is. He carries about a third of Barcelona’s offensive creation, which is unheard of at any level in the top 5 leagues. What makes that even more impressive is that Messi is doing this at a championship-contender level, while the players who are even remotely close to him in terms of percentage are doing it at a lower tier. 
It’s a shame that one of Karim Benzema’s best seasons in a Real Madrid shirt came during one of their worst years in recent history. The Frenchman proved to be integral to Madrid’s offense in its first season without Cristiano Ronaldo, providing his team with 26% of its total G+A last season.
The last team that caught my attention at the top of the table was Valencia. They were able to secure 4th, led by Dani Parejo with 18% of their total offense. What’s interesting about this is that no other team was placing this high with a midfielder as their main G+A leader; this was a trend that was seen more so in mid-table teams, not in teams that finished in European spots. What’s even more eye-opening about this is that Parejo didn’t enter double digits for either his Goals or Assists, which illustrates the idea that Valencia’s league offense isn’t necessarily tied to one player but rather a team effort. Perhaps with increased output from their strikers for the 2019/20 season they can make a serious challenge for one of the spots of the Big 3 in La Liga.
Elsewhere in the table there were some interesting cases this season. Cristhian Stuani, despite scoring 19 goals, still saw his Girona side get relegated. He is one of the only players on this list to make it with 0 assists, and despite this still has a G+A total that’s Eight(!) higher than the second-best attacker on Girona’s squad. In comparison, Real Valladolid’s Enes Ünal had a G+A total of 9… and they were still able to stay up, finishing in 16th. 
The importance of Iago Aspas to Celta de Vigo cannot be stated enough; he put up G+A numbers that rivaled Messi’s in terms of percentage (30 to 32), but were just enough to put Celta in 17th place and save them from relegation. 
Raul de Tomás did very well for a Rayo Vallecano side that was, quite frankly, doomed from the start of the season. Despite not making the full 38 appearance (He made 33), he had a total G+A of 15 and a G+A% of 23. Not bad for the former Real Madrid loanee, who hopefully will excel after his permanent move to Portuguese giants Benfica.
We end our analysis of La Liga with Real Betis, whose two highest scorers were both midfielders (Lo Celso and Canales). After the loss of Lo Celso and the Acquisition of both Nabil Fekir from Lyon and Borja Iglesias from RCD Espanyol (Iglesias led his team in G+A), it will be interesting to see how the Betis team learn to adapt their offense to two great attackers. They are almost certainly going to be a fun team to watch in La Liga when they’re in the final third. 

### Premier League
```{r plotly2, fig.width=8, fig.height=6, message = FALSE}
# Generating a Graph of the EPL's Top Attackers

library(plotly)
pal <- c("blue", "green", "purple", "yellow", "orange", "red")
pal <- setNames(pal, c("Champion", "Qualified for European Competition", "Qualified for European Competition (Cup Competition)", "Upper Mid-Table", "Lower Mid-Table", "Relegated"))

x <- list(
  title = "Goals"
)
y <- list(
  title = "Assists"
)

p <- plot_ly(data = Goals.Assists.EPL2, x = ~Individual.Goals, y = ~Individual.Assists, text = ~paste("Player: ", X.U.FEFF.Top.Goalscorer.Assister ,'<br>Team:', Club, '<br>', Percentage*100, "% of Total Team G+A"), color = ~Result, colors = pal) %>%
  layout(title = "Top attacker for each EPL team", xaxis = x, yaxis = y)

ggplotly(p)

options(browser = 'false')
api_create(p, filename = "EPL")
```
### [Link to EPL Graph](https://plot.ly/~bdominique/15)

The scariest part of Sergio Agüero being the G+A leader for Manchester City is that there’s a very real argument he isn’t even the most important piece of their offense. City have so many different players who can hurt you in the final third that I was a bit surprised to see Agüero top this list but seeing his contribution amount to 18% of City’s total G+A makes sense; no single player carries City’s offense by himself, and this is reflected in that number.
Speaking of carrying offenses, allow me to introduce you all to Eden Hazard, formerly of Chelsea. In his final season for the Blues he led them in both Goals (16) and Assists (15), and by some distance in each category. He was the only Chelsea player with Double Digit Goals and only one with Double Digit Assists in the EPL, which really puts into perspective how much value he had to them. To see how they replace the void he left in their offense this season will be… interesting to say the least.
Liverpool and Tottenham are more in line with City in the sense that their offensive loads are distributed. Mohamed Salah puts up similar Goal figures as Sadio Mané and Roberto Firmino but makes this list because he has better Assist numbers, and Christian Erisken had a G+A total that was only one behind Kane’s 21 for the season.
Rounding out the Top 6 is Manchester United, who have Paul Pogba as their highest contributor at 21%. Pogba breaks the trend of teams with a forward as their highest contributor, with 7th place wolves (Raúl Jiménez) and 8th place Everton (Gylfi Sigurdsson) following suit.
One standout player in the middle of the table to me Jamie Vardy put up very impressive numbers for a decent Leicester City side, who by most accounts should remain at that level in 2019/20. Another was Gerard Deulofeu, who tied for G+A at Watford with Troy Deeney despite Deulofeu playing only 30 games (Deeney had 32).
The bottom of the EPL table brings us to the perhaps the most troubling team in Europe, certainly in England. Throughout the top 5 leagues, I don’t think that there was a team as poor as Huddersfield in terms of offensive creation. As a team they had a total 34 G+A, with Steve Mounie leading the way with 2 Goals and 3 Assists. 

### Ligue 1
```{r plotly3, fig.width=8, fig.height=6, message = FALSE}
# Generating a Graph of Ligue 1's Top Attackers

library(plotly)
pal <- c("blue", "green", "purple", "yellow", "orange", "red")
pal <- setNames(pal, c("Champion", "Qualified for European Competition", "Qualified for European Competition (Cup Competition)", "Upper Mid-Table", "Lower Mid-Table", "Relegated"))

x <- list(
  title = "Goals"
)
y <- list(
  title = "Assists"
)

p <- plot_ly(data = Goals.Assists.Ligue.12, x = ~Individual.Goals, y = ~Individual.Assists, text = ~paste("Player: ", X.U.FEFF.Top.Goalscorer.Assister ,'<br>Team:', Club, '<br>', Percentage*100, "% of Total Team G+A"), color = ~Result, colors = pal) %>%
  layout(title = "Top attacker for each Ligue 1 team", xaxis = x, yaxis = y)

ggplotly(p)

options(browser = 'false')
api_create(p, filename = "Ligue-1")
```
### [Link to Ligue 1 Graph](https://plot.ly/~bdominique/17)

Even at his young age Kylian Mbappé is already putting up Goal numbers that are comparable to Messi’s, although his assists are a bit lacking. 22% of his team’s offense went though him, which sounds about right when you consider how many different players contributed offensively to PSG as they waltzed to the title last season.
Following Mbappé is Nicolas Pépé of Lille (now Arsenal) and Memphis Depay of Lyon. Pépé is one of the only players who plays for a top team and contributes to his team’s offense at 30% or higher, which puts him within touching distance of Messi (although Pépé’s G+A total is 34, while Messi’s is 49). How Lille recuperate from losing both him and Rafael Leão (to AC Milan) will be interesting to see; when a single player contributes this much to your offense, it’s hard to see it going successfully. Depay was the highest contributor on a much more balanced Lyon team where he contributed 17% of his teams G+A. Lyon is comparable to Valencia in this aspect, although Lyon as a team have a much higher G+A total – 121 compared to Valencia’s 89. In fact, Ligue 1’s top teams were very high in this aspect: PSG, Lille and Lyon combined for 412 total G+A and are the only league besides the EPL (421) to surpass 400 G+A with their top 3 teams.
One of the strangest names to appear on this list is Kenny Lala of Strausbourg, who (according to every website I checked) is a Right Back. As far as I’m aware this is the only defender who makes this list and does so mainly because of his assists; he provided 9 of them last season (team high) and was 4th on his team in terms of Goals with 5 of them.
Despite playing only 19 games this season, the late Emiliano Sala still led Nantes’ offense with a contribution of 19%. 2018-19 was one of Sala’s best in terms of Goals, where he tied his previous two seasons of 12 goals for Nantes but did so with only 19 games (34 in 2016-17 and 36 in 2017-18).

### Bundesliga
```{r plotly4, fig.width=8, fig.height=6, message = FALSE}
# Generating a Graph of the Bundesliga's Top Attackers

library(plotly)
pal <- c("blue", "green", "purple", "yellow", "orange", "red")
pal <- setNames(pal, c("Champion", "Qualified for European Competition", "Qualified for European Competition (Cup Competition)", "Upper Mid-Table", "Lower Mid-Table", "Relegated"))

x <- list(
  title = "Goals"
)
y <- list(
  title = "Assists"
)

p <- plot_ly(data = Goals.Assists.Bundesliga2, x = ~Individual.Goals, y = ~Individual.Assists, text = ~paste("Player: ", X.U.FEFF.Top.Goalscorer.Assister ,'<br>Team:', Club, '<br>', Percentage*100, "% of Total Team G+A"), color = ~Result, colors = pal) %>%
  layout(title = "Top attacker for each Bundesliga team", xaxis = x, yaxis = y)

ggplotly(p)

options(browser = 'false')
api_create(p, filename = "Bundesliga")
```
### [Link to Bundesliga Graph](https://plot.ly/~bdominique/19)

Across the board there is no single player who seems to be carrying his team in Germany. On average a player contributed about to about 18% of their team’s offense with no player having a contribution of above 25%, which at first I thought was because of the lesser amount of games in the Bundesliga (34 compared to 38 in the other 4 leagues). I realized later that rather than affecting the percentages, the 4 less games would affect the total amount that each player/team scored.
An interesting trend that I started to notice around this time was just how many players benefited from using both Goals and Assists, rather than just goals. Because the percentages of the Bundesliga are so low, this means that each team most likely have a more creative player as their top contributor, where other teams in other leagues might have pure Goal scorers. Here are a couple players who made this list because I decided to include both Goals and Assists together (This is not every single example but I believe the Bundesliga has either the most or the second most who benefit from this):
  -	La Liga: J.Calleri has the most goals but only two assists and gets replaced by Jony     with 5 goals and 12 assists for Deportivo Alavés. Same with Ekambi(10G,0A) replaced     by S.Cazorla(4,10) for Villareal
-	Premier League: A.Perez(12,2) gets passed by S.Rondon(11,7) for Newcastle, D.Ings(7,2) passed by N.Redmond(6,4) for Southampton, 3 Players on Huddersfield passed by S. Mounie
-	Ligue 1: M. Dembele(15,4) passed by M. Depay(10,10) for Lyon, 3 Players on Nimes passed by T. Savanier(6,13) 
-	**Bundesliga: J. Sancho(12,14) passes M. Reus(17,8) and P. Alcacer(18,0) for Borussia Dortmund, K.Volland(14,8) passes K.Havertz(17,4) for Bayer Leverkusen, S. Haller (15,9) passes M.Kruse(11,9) and L. Jovic(17,5) for Eintracht Frankfurt**
-	Serie A: S. El Shaarawy(11,3) passed by E. Dzeko(9,6) for Roma, G. Simeone(6,3) passes 2 players because of his assists alone

One comparison I found was the similarity between the numbers that the Hazard brothers put up for their respective teams. Thorgan also had double digit Goals and double digit Assists for his 5th place Borussia Monchengladbach team, but only contributed 22% compared to Eden’s 27.  Thorgan also wasn’t the highest Goas scorer for his team; he got beat out by Alassane Pléa (Thorgan’s 10 to Pléa’s 12).


### Serie A
```{r plotly5, fig.width=8, fig.height=6, message = FALSE}
# Generating a Graph of Serie A's Top Attackers

library(plotly)
pal <- c("blue", "green", "purple", "yellow", "orange", "red")
pal <- setNames(pal, c("Champion", "Qualified for European Competition", "Qualified for European Competition (Cup Competition)", "Upper Mid-Table", "Lower Mid-Table", "Relegated"))

x <- list(
  title = "Goals"
)
y <- list(
  title = "Assists"
)

p <- plot_ly(data = Goals.Assists.Serie.A2, x = ~Individual.Goals, y = ~Individual.Assists, text = ~paste("Player: ", X.U.FEFF.Top.Goalscorer.Assister ,'<br>Team:', Club, '<br>', Percentage*100, "% of Total Team G+A"), color = ~Result, colors = pal) %>%
  layout(title = "Top attacker for each Serie A team", xaxis = x, yaxis = y)

ggplotly(p)

options(browser = 'false')
api_create(p, filename = "Serie-A")
```
### [Link to Serie A Graph](https://plot.ly/~bdominique/21)

21 league Goals represents Cristiano Ronaldo’s lowest total in about a decade, but combined with his 7 Assists is enough to see him contribute to ¼ of all Juventus league G+A. Juventus have the lowest G+A total of all champions (111) by quite some margin; with no real attackers brought in over the summer, all eyes will be on new manager Maurizio Sarri to raise this number by modifying his predecessor Massimiliano Allegri’s more defensive approach.
It didn’t surprise me to see Mauro Icardi‘s  name on this list for Inter Milan, but what did is the fact that he only contributed to 16% of his team’s total G+A. For a player that has put up stellar numbers in the seasons prior (29 league goals in 2017-18, 24 in 2016-17), it’s a bit weird to see him dip this low. But when you consider the number of off the field issues that Icardi faced (some of his own doing, some not) it begins to make more sense. New manager Antonio Conte will need him at his very best if Inter aim to dethrone Juventus in the league.
Serie A is home to the player who has the highest contribution to his team in all of Europe: Fabio Quagiarella of Sampdoria, who finished last season with 34% of his team’s G+A. At 36 years old it’s almost unheard of to put together contributions such as this, much less the best one in Europe’s top 5 leagues. Whether or not this type of contribution can be done again by him remains to be seen but based on Quagiraella’s last couple of seasons it’s not unreasonable to believe that he will hit double digit Goal tallies again. 

### Conclusion

Compiling this data made me realize how important it is to have a well-balanced team. Over-relying on a player to carry more than a certain percentage of your team’s G+A will only spell trouble if that player isn’t available for whatever reason. While it’s always fun to create graphs like these to illustrate the dominance of a player like Messi, it’s apparent to almost anyone that watches Barcelona how weak their attack is without him playing. A team should always have multiple attackers that can be relied upon for any situation, and no other team comes to mind for me other than Manchester City. The point I made about Aguero earlier is something that I think shows just how well-prepared City are for something as grueling as the English Football campaign: City have multiple players who are talented enough to be carrying 27+% of other top team’s total G+A, but instead have all bought into the vision that Pep Guardiola has laid out for them. With what seems like a new cup or competition every week, English teams and their players are generally pushed harder because of the extra amount of games that they play, and the less time they have in between them. City’s accomplishments since the 2017-18 league season have been nothing short of astonishing, and it doesn’t seem as though they’ll be stopping anytime soon.

Looking back on this project, I’m satisfied with my decision to use combined Goals and Assists rather than just Goals. I think that this gave some insights that wouldn’t have been possible with just one category and, as I said above, helps to show which players can do multiple jobs for their team rather than just one. As anyone in the field of Sports Analytics will tell you however, data can never tell the whole story by itself; it can only aid you in trying to tell the story that you create from it. While I think that this data that I compiled helps to paint a better picture of teams and their best attackers,  this could’ve been a bit more insightful if advanced metrics (Expected Goals+ Assists rather than Actual G+A, for example) were used to determine the best attackers. With that being said this project was still very insightful for me; I was able to go through the process of being a Data Analyst (Collect Data, Clean Data, Visualize Data, Share Results) in a field that will never cease to interest me. I hope you enjoyed reading this as much as I enjoyed making this!
