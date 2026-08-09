# ⚾ MLB SQL Analysis

A SQL data analysis project exploring historical Major League Baseball player data, schools, salaries, and career statistics using PostgreSQL.

## Overview

### The Situation
I've just been hired as a Data Analyst Intern for **Major League Baseball** (MLB), which has recently gotten access to a large amount of historical player data. 

### The Assignment
Using access to data including player statistics like schools attended, salaries, teams players for, height and weight, and more, my task is to use **advanced SQL querying techniques** to track how player stats have changed over time and across different teams in the league. 

### My Objectives
1. What **schools** do MLB players attend?
2. How much do teams spend on player **salaries**?
3. What does each player's **career** look like?
4. How do player **attributes** compare?

This project demonstrates advanced SQL querying skills including:

- Complex JOINs
- CTEs
- Window Functions
- Aggregate Functions
- Subqueries
- CASE Statements

## Dataset

Source:
MLB data: [https://drive.google.com/drive/folders/1UyeVh9taRzmMXkJgTeDJUEK74Y-a4ze9?usp=drive_link](https://drive.google.com/drive/folders/1UyeVh9taRzmMXkJgTeDJUEK74Y-a4ze9?usp=sharing)

Tables used:

- Players
- Salaries
- Schools

## Skills

- SQL
- PostgreSQL
- Data Cleaning
- Joins
- CTEs
- Window Functions
- Ranking
- Aggregate Analysis
- Business Reporting

## Business Questions

### School Analysis

- Which schools produced the most MLB players?
- What are the names of the top 3 schools that produced the most players?
- What are the names of the schools with the most decades of player contributions?

### Salary Analysis

- Which teams spend the most?
- Which teams reached $1 billion in cumulative spending first?

### Career Analysis

- Career length analysis by decade
- Players with over a decade-long career with loyalty to one team
- Teams with the highest percentage of switch hitters

## Some of the Key Findings (for more findings, see full report below)

- The number of schools contributing players to MLB increased from 2 in the 1860s to a peak of 494 in the 1990s, reflecting a substantial expansion    in the diversity of schools represented in the league. 
- The San Francisco Giants, Los Angeles Angels, and New York Yankees recorded the highest average annual payrolls, with an average annual spending     of approximately $371 million across the three teams.
- The longest career spent with a single team was 23 years, achieved by two players.
- The San Francisco Giants had the highest percentage of switch hitters, with 18.5% of players batting from both sides of the plate.

## Example SQL Query
### Finding teams with the highest percentage of switch hitters
SELECT	s.teamID,
		ROUND(SUM(CASE WHEN bats = 'R' THEN 1 ELSE 0 END) / COUNT(s.playerID) * 100, 1) AS bats_right_percent,
        ROUND(SUM(CASE WHEN bats = 'L' THEN 1 ELSE 0 END) / COUNT(s.playerID) * 100, 1) AS bats_left_percent,
        ROUND(SUM(CASE WHEN bats = 'B' THEN 1 ELSE 0 END) / COUNT(s.playerID) * 100, 1) AS bats_both_percent
FROM	salaries s INNER JOIN players p
	ON	s.playerID = p.playerID
GROUP BY 1
ORDER BY 4 DESC;

#### Query Results
<img width="946" height="342" alt="Screenshot 2026-08-09 at 12 54 38 PM" src="https://github.com/user-attachments/assets/07dfddcc-3151-4e48-8ca2-6ccd746b4594" />

## What I Learned

This project strengthened my ability to:

- Build complex SQL queries
- Break large business questions into manageable analyses
- Optimize joins across multiple tables
- Present findings in a business-focused format

  ## Future Improvements

- Build an interactive Tableau dashboard
- Create views for recurring reports

## Full Report (project introduction, dataset, findings, queries, and results)
[Amir Rahmani_Advanced SQL Project_ MLB.pdf](https://github.com/user-attachments/files/30879201/Amir.Rahmani_Advanced.SQL.Project_.MLB.pdf)

---

## 📬 Connect With Me

Thanks for checking out this project! I'm always interested in discussing data analytics, SQL, data visualization, and opportunities to collaborate or learn.

- 💼 LinkedIn: www.linkedin.com/in/amirrah
- 📂 GitHub: https://github.com/amirr-hub
- 📧 Email: amir.connect@outlook.com

If you have feedback, questions, or suggestions for improving this project, feel free to reach out or open an issue.
