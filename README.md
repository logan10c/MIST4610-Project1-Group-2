# MIST4610-Project1-Group-2
MIST4610 NFL 2024 Season Project 1

Team Members:

- Logan Collins
- Eli Burt
- Austin Middlebrooks
- Noelle Rocheteau
- Rett Sams


Problem Description:
The objective of this project is to design, model, and implement a comprehensive relational database for the 2024 NFL season. The core focus of the system is the NFL Team entity, which is connected to related entities such as Players, Coaches, Referees, Broadcasters, and other operational components of the league.
The project focuses on:
Developing a complete Entity-Relationship model that accurately represents the structure and interactions of NFL organizations during the 2024 season.


Populating the database with detailed and realistic season data, including team rosters, game schedules, officiating crews, broadcast assignments, and statistical outcomes.


Writing and executing SQL queries to efficiently retrieve meaningful insights from the database, such as team performance metrics, player statistics, and game reporting details.
By the end of the project, we will have a fully functioning database system that provides valuable visibility into the dynamics and analytics of the 2024 NFL season.
Note that we could not find complete accurate data for Broadcasting Crews and Player Start +  End Dates.

Data Model:
Model Explanation:

Our model is based on the structure of the NFL, particularly for the 2024 season. The team entity represents one of the thirty-two NFL teams. Each team can have many players, and a player can also have many teams (if a player gets cut or traded), which is shown by a many-to-many relationship. We used the associative entity team_has_player to track the start and end dates of when the player joined each team.
A team also has a stadium, but in some instances, teams share a stadium (NYJ and NYG or LAC and LAR). This is represented by a one-to-many relationship from stadium to team. Further, a team also has multiple coaches, and coaches can have only one team. Coaches do not get traded during a season, so they cannot be part of multiple teams. This is shown by a one-to-many relationship from team to coaches. Coaches also have a hierarchy—a coach can be the boss of many other coaches, but a coach can only have one boss. This is identified through a one-to-many recursive relationship.
A team plays 18 regular-season games each year. Therefore, in our model, a team has many games. A game can only have one winner and one loser. This is modeled by two one-to-many relationships. A game must also have referees. A game can have only one referee crew and a referee crew can officiate many games over the season. This is shown by a one to many relationship from refereeCrew to game. A referee Crew can have many referees but a referee can only have one referee crew that they work with. A referee crew also has one chief referee.
Similarly, a game can have more than one broadcaster, and a broadcaster can call more than one game each season. This is yet another many-to-many relationship, which creates the associative entity broadCastCrew, tracking which broadcasters call each game.
Players in the NFL can have mentors throughout the league who help them develop their game. A player can only have one mentor but can have many other players whom they mentor. This is shown by a one-to-many recursive relationship between players. We also modeled the 2024 NFL draft. A player can be only one draft pick, and a draft pick can be only one player, so we showed this relationship using a one-to-one relationship labeled draft pick. Teams, however, can have more than one draft pick, so to show this relationship, there is a one-to-many from team to draft.

Data Dictionary:
Table: player
Table: team_has_player
Table: stadium
Table: coach
Table: team
Table: draftPick
Table: game
Table: refereeCrew
Table: referee
Table: broadcastCrew
Table: broadcaster
Queries:

























Write a query to list the coach, total number of players, and average player age by team.




This query is meaningful because it shows roster and coaching information to provide information about the composition of each team. It highlights how team size and player age may differ under different coaches, which can be valuable for identifying roster balance, experience distribution, and potential leadership styles within each organization


Write a query that finds the top 3 teams with the most first round picks.


This query identifies which teams have had the most first round draft selections. By grouping draft data by team and filtering for only first round picks, it reveals which organizations have had the greatest access to top tier talent. This information is meaningful because it can help analyze how draft opportunities relate to team performance, roster strength, and overall franchise strategy.

Write a query that lists the avg years of experience by team & position (only show positions with ≥ 2 active players).



This query calculates the average years of experience for each position within every team, while only including positions that have at least two active players. It is meaningful because it provides insight into roster depth and experience balance across positions. Teams can use this data to evaluate whether certain positions rely more on seasoned veterans or less experienced players, which is valuable for assessing player development and recruitment strategies.

4) Write a query that retrieves players earning below average salary.


This query retrieves all players whose salaries are below the league wide average. It uses a subquery to calculate the average salary and compares each player’s pay against that benchmark. This information is meaningful because it helps identify undervalued or budget efficient players, which can assist teams and analysts in evaluating payroll distribution, player value, and potential opportunities for salary adjustments or contract negotiations.


5) Write a query that lists referee crews that officiated above-league-average scoring games.

This query finds referee crews that have officiated games where the combined total points scored were higher than the league average. It joins the refereeCrew and game tables and compares each game’s total points to the league wide average calculated in a subquery. This is meaningful because it helps identify officiating crews associated with higher-scoring games, which can offer insights into game tempo, officiating tendencies, or styles that may influence scoring outcomes.


6) Write a query to find teams with below average payroll.


This query calculates each team’s total payroll by summing the salaries of active players, then compares those totals to the league-wide average payroll. It uses a subquery to determine the average across all teams. This is meaningful because it identifies organizations operating with lower payrolls, offering insight into financial efficiency, team spending strategies, and how resource allocation might correlate with overall team performance.

7) Write a query that lists mentors whose mentees (on average) out-earn the mentor.


This query identifies mentors whose mentees have a higher average salary than they do. It uses a self join on the player table to link each mentor with their mentees and compares the mentor’s salary to the average of their mentees’ salaries. This is meaningful because it highlights mentorship relationships where mentees have advanced beyond their mentors financially, offering insights into the effectiveness of player development, mentorship success, and potential leadership influence within teams.


8) Write a query to retrieve teams that lost even when scoring > 20, and where the winning team scored more than 28 points.


In games where the other team scored more than 28 points, this query returns teams that lost even though they scored more than 20 points. It focuses on high scoring losses, exposing teams with strong offenses but weak defenses. This is significant because it sheds light on game results and defensive flaws that may not be visible from win and loss records. This can assist analysts and coaches in identifying areas that require improvement.


9) Retrieve the names of parent categories that have subcategories.

Because it shows which coaches hold leadership positions within their organizations, this query is helpful. It gives information about the coaching hierarchy of the team and the division of duties by displaying which coaches have subordinates. Analysts and management can use this data to track mentorship relationships, comprehend organizational structure, and determine which coaches might have more management or influence over their teams.

10) Write a query to list the stadiums with a turf surface and capacity greater than 70,000.


This query retrieves all stadiums that have a turf playing surface and can hold more than 70,000 spectators. It filters data on surface type and seating capacity, then orders the results from largest to smallest. This is meaningful because it highlights the biggest turf based stadiums in the league, which can be useful for event planning, monitoring fan capacity, and identifying potential venues where the Superbowl and Pro Bowl may be played.

Database Information

Name of the database: cs_jam37624

