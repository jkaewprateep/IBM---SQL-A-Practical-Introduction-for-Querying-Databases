# IBM - SQL A Practical Introduction for Querying Databases
IBM - SQL A Practical Introduction for Querying Databases

* IBM Data Warehouse Engineer Professional Certificate [IBM]( https://github.com/jkaewprateep/Portfolio/blob/main/Coursera%204K7JZCI2I9XO.pdf )
* IBM Business Intelligence (BI) Analyst Professional Certificate [IBM]( https://github.com/jkaewprateep/Portfolio/blob/main/Coursera%200QO1U1C6S867.pdf )
* Meta Database Engineer Professional Certificate [META]( https://github.com/jkaewprateep/Portfolio/blob/main/Coursera%20VVUULL2PK26V.pdf )
* Meta Back-End Developer Professional Certificate [META]( https://coursera.org/share/bc30f508bcf68936d9028e9d0d6b9dfc )
* HackerRank SQL (Advance) [HackerRank]( https://www.hackerrank.com/certificates/f225fa371510 )

<p align="center" width="100%">
    <img width="47%" src="https://github.com/jkaewprateep/IBM---SQL-A-Practical-Introduction-for-Querying-Databases/blob/main/IBM%20-%20SQL%20A%20Practical%20Introduction%20for%20Querying%20Databases%20instructor.png">
    <img width="17.63%" src="https://github.com/jkaewprateep/IBM---SQL-A-Practical-Introduction-for-Querying-Databases/blob/main/kid_29.jpg"> </br>
    <b> Pictures from the Internet </b> </br>
</p>

## Practical quizzes - not a peer review ##

### Select, where cause condition, and inner join ###
<p align="center" width="100%">
    <img width="47%" src="https://github.com/jkaewprateep/IBM---SQL-A-Practical-Introduction-for-Querying-Databases/blob/main/kid_35.jpg"> </br>
    <b> Pictures from the Internet </b> </br>
</p>

🧸💬 There are many names I recognize from this game somebody says it is tele-games, overy as shape and catch-n-tail where they are developed into some meaningful word and action to find the friend who needs most help to track the line. In the game selection create by turn player enter and leave of the filter made by two children older apply to selection tail player from the same line. </br> 
🐯💬 We have traditional-brands that sound the same to catch and become the group leader of the same business. </br> 

```
# Q1 List the case number, type of crime and community area for all crimes in community area number 18.
# SELECT * FROM chicago_socioeconomic_data WHERE `COMMUNITY_AREA_NUMBER` = 18;
# SELECT * FROM chicago_crime
# SELECT * FROM chicago_public_schools

# area
SELECT * FROM chicago_public_schools A INNER JOIN ( SELECT * FROM chicago_socioeconomic_data ) B
	ON A.COMMUNITY_AREA_NUMBER = B.COMMUNITY_AREA_NUMBER
;
```

### Select, where cause condition, and left join ###
<p align="center" width="100%">
    <img width="37%" src="https://github.com/jkaewprateep/IBM---SQL-A-Practical-Introduction-for-Querying-Databases/blob/main/cat_02.png"> </br>
    <b> Pictures from the Internet </b> </br>
</p>

🐑💬 ➰ By each recording process primarily from the left side finding relation records by selecting condition on the right side, they are processed by iteration and target table process at the same time because using join with condition and sub-query are processes separate from the primary SQL statement by default. </br>
🐐💬 There is a process time delay response to confirm the process running and continuing and the database may require temporary tables, query cache, disk space, or memory to perform a long query. In guarantee mode no result return but in first answer you have some information from the query return and may not completed of the result set but they will have some descrtiption and warning message programmer and database administrators need to handle it correct behaviour. </br>

```
# Q2 List all crimes that took place at a school. Include case number, crime type and community name.

SELECT * FROM chicago_crime A LEFT JOIN ( SELECT * FROM chicago_socioeconomic_data ) B
	ON A.COMMUNITY_AREA_NUMBER = B.COMMUNITY_AREA_NUMBER
;
```

### Select, where cause condition, and left join sub-query ###
<p align="center" width="100%">
    <img width="47%" src="https://github.com/jkaewprateep/IBM---SQL-A-Practical-Introduction-for-Querying-Databases/blob/main/cat_01.png"> </br>
    <b> Pictures from the Internet </b> </br>
</p>

🦭💬 There are small to large datasets and they have different time query result returns by default this technique will have the answer when both sub-queries have the result set and perform outer join operation and filter for the results. There are possible errors when one or a required sub-query are not return the answer if the sib-query are not the main objective it may be left blank without error or message because database caches need to respond in query time fashionally as the other sub-queries that is known problem when we joined multiple tables from different sources and communication method. A driver and database cache perform work this way and refresh database caches to refresh the fetching result and start filling into the resultset to have the full answer. Refresh caches is not the method but the selection mode is the data return guarantee. </br>
🦁💬 We saved time by requesting audit reports that required detail and reference numbers and you can work at a single time with full joined conditions for both standard and audit reports. </br>

```
# Q3 For the communities of Oakland, Armour Square, Edgewater and CHICAGO list the associated
# community_area_numbers and the case_numbers.

SELECT * FROM chicago_crime A LEFT JOIN ( SELECT * FROM `chicago_socioeconomic_data` WHERE COMMUNITY_AREA_NAME
	IN ( 'Oakland', 'Armour Square', 'Edgewater', 'Chicago Lawn' )) B
	ON A.COMMUNITY_AREA_NUMBER = B.COMMUNITY_AREA_NUMBER
;
```

### Create table view object ###
<p align="center" width="100%">
    <img width="40%" src="https://github.com/jkaewprateep/IBM---SQL-A-Practical-Introduction-for-Querying-Databases/blob/main/needle_practice_01.jpg"> </br>
    <b> Pictures from the Internet </b> </br>
</p>

🐨🎁🎵🎶 A composite view is the structure of data selection, filters, joined, transform, merged, and display capable of multiple purposes. Portability, flexibility, parameterize, and data format standardized return as resultset or records, it is composite views because they can composed of multiple selection views to create a usability matrix for evaluation and performance tuning of query and database from user work adaptations and requirements. </br>
👧💬 🎈 The composite view can be selected from the database table, incremental database table, system table, and SQL selectable objects when applied with a filter some tasks can be performed by the user and controlled by user permissions accessibility for the particular material views or composite views object with high-performance design by the database administrator, sources control, users permission groups, database object limitation, and exporting level. </br>
🐐💬 You just cannot copy values from the result set to return in the SQL database administrator tool or its IDE because of an experienced database administrator, it is an observation meeting for IT project requirements surveys. </br>

```
CREATE VIEW view_chicagopublicschools(
    School_Name, Safety_Rating, Family_Rating, Environment_Rating, Instruction_Rating,
    Leaders_Rating, Teachers_Rating
    )
AS SELECT ALL `NAME_OF_SCHOOL`, `Safety_Icon`, `Family_Involvement_Icon`, `Environment_Icon`,
	`Instruction_Icon`, `Leaders_Icon`, `Teachers_Icon` FROM chicago_public_schools

SELECT `School_Name`, `Teachers_Rating` FROM view_chicagopublicschools
;
```

### Select and switch-cases conditions in the programming store PROCEDURE ###
<p align="center" width="100%">
    <img width="47%" src="https://github.com/jkaewprateep/IBM---SQL-A-Practical-Introduction-for-Querying-Databases/blob/main/cat_03.png"> </br>
    <b> Pictures from the Internet </b> </br>
</p>

💃( 👩‍🏫 )💬 SQL query needs to perform performance evaluation and selecting conditions indent display and/or create as switch-cases condition and monitor logging debugging of switch-cases condition for problem solution debugging of SQL selection message communications. </br>
🦤💬 Not all conditions can perform switch-case they are singular problems, and common and unique, the steps to procedure guarantee the tasks contained inside perform priority, logging of the input and results or debugging setting for evaluation backlog or performance improvement forward into the future. </br>

```
DELIMITER //
CREATE PROCEDURE UPDATE_LEADERS_SCORE 
(
   in_School_ID varchar(128),
   in_Leader_Score varchar(128)
) 
BEGIN 

DECLARE ICON VARCHAR(50);
DECLARE TEMP_ICON VARCHAR(50);

SELECT Leaders_Icon 
FROM chicago_public_schools
WHERE in_School_ID = School_ID LIMIT 1
INTO TEMP_ICON;

SELECT (
    CASE 
        WHEN in_Leader_Score > 80 AND in_Leader_Score THEN 'Very strong'
        WHEN in_Leader_Score > 60 AND in_Leader_Score <= 79 THEN 'Strong'
        WHEN in_Leader_Score > 40 AND in_Leader_Score <= 59 THEN 'Average'
        WHEN in_Leader_Score > 20 AND in_Leader_Score <= 39 THEN 'Weak'
        WHEN in_Leader_Score >  0 AND in_Leader_Score <= 19 THEN 'Very Weak'
        ELSE TEMP_ICON
    END) INTO ICON;

UPDATE chicago_public_schools
SET Leaders_Icon = ICON
WHERE in_School_ID = School_ID; 

SELECT School_ID, Leaders_Icon 
FROM chicago_public_schools
WHERE in_School_ID = School_ID; 

COMMIT;
END
```

### Select min-max from the remote data table ###
<p align="center" width="100%">
    <img width="47%" src="https://github.com/jkaewprateep/IBM---SQL-A-Practical-Introduction-for-Querying-Databases/blob/main/cat_04.jpg"> </br>
    <b> Pictures from the Internet </b> </br>
</p>

🧸💬 Aggregation on the remote table is one problem of the SQL selection performance because the SQL statement needs evaluation of the remote table finish to perform continue overall task and when this solution is introduced the local aggregate table, indexes, and statistics tables are created to perform the required operation by the required value and they can re-evaluation same as an application in some working place. There is a demand to create order and file the order into the cargo when we do not know exact number of quality but a chunk of cattrage can estimate number quantity and complete the exact number. </br>
🐑💬 ➰ We cannot make synchronized tables because they are controlled and the system performance of the cargo is the fastest lane, catching up with the speed for the same weight of integration. </br>

```
# Q9 Use a sub-query to determine which Community Area has the least value for school Safety Score?

SELECT * FROM "PYV10949".chicago_public_schools 
WHERE "SAFETY_SCORE" = ( SELECT MIN("SAFETY_SCORE") 
FROM "PYV10949".chicago_public_schools 
WHERE "SAFETY_SCORE" > 0 )
;
```

### Select data column value from the existence of value in the target data table ###
<p align="center" width="100%">
    <img width="47%" src="https://github.com/jkaewprateep/IBM---SQL-A-Practical-Introduction-for-Querying-Databases/blob/main/cat_05.jpg"> </br>
    <b> Pictures from the Internet </b> </br>
</p>

🦭💬 Evaluation needs to be performed after the SQL statement but categorization can be performed it before some applications apply the technique of database categorization by using a database filter with a database record trigger or interaction by category table using application or database process. This method helps determine the categorization faster but you need to be aware of the condition of the primary and secondary categories because full records are required of both categorized groups and their description. </br>
🦁💬 A single table index is enough for filter records selection but categorizes design support of composite messages display and user group authority because database object accessibility and table description cannot have full meaning without an authorized method. The categorize method is not an encryption method if you have access to all required objects you can read the full message but they are not fully joined if you are not authorized, the idea is found in many software applications and new generations of software design protected data by encryption and make the joining task simpler. </br>

```
# Q10 [Without using an explicit JOIN operator]
	Find the Per Capita Income of the Community Area which has a school Safety Score of 1.

SELECT "PER_CAPITA_INCOME" FROM "PYV10949".chicago_census_data
	WHERE "COMMUNITY_AREA_NUMBER" IN ( SELECT "COMMUNITY_AREA_NUMBER"
		FROM "PYV10949".chicago_public_schools WHERE "SAFETY_SCORE" = 1 )
;
```

---

## Practical quizzes - not a peer review, SQL joining ##

### Select, inner join and where cause conditions ###

```
--- Query1A ---
select E.F_NAME,E.L_NAME, JH.START_DATE 
	from EMPLOYEES as E 
	INNER JOIN JOB_HISTORY as JH on E.EMP_ID=JH.EMPL_ID 
	where E.DEP_ID ='5'
;
```

### Select, inner join and where cause conditions with multiple columns matching ###

```
--- Query1B ---	
select E.F_NAME,E.L_NAME, JH.START_DATE, J.JOB_TITLE 
	from EMPLOYEES as E 
	INNER JOIN JOB_HISTORY as JH on E.EMP_ID=JH.EMPL_ID 
	INNER JOIN JOBS as J on E.JOB_ID=J.JOB_IDENT
	where E.DEP_ID ='5'
;
```

### Select, and left outer join ###

```
--- Query 2A ---
select E.EMP_ID,E.L_NAME,E.DEP_ID,D.DEP_NAME
	from EMPLOYEES AS E 
	LEFT OUTER JOIN DEPARTMENTS AS D ON E.DEP_ID=D.DEPT_ID_DEP
;
```

### Select, left outer join and where conditions ###

```
--- Query 2B ---
select E.EMP_ID,E.L_NAME,E.DEP_ID,D.DEP_NAME
	from EMPLOYEES AS E 
	LEFT OUTER JOIN DEPARTMENTS AS D ON E.DEP_ID=D.DEPT_ID_DEP 
	where YEAR(E.B_DATE) < 1980
;
```

### Select, inner join and where conditions ###

```
--- alt Query 2B ---
select E.EMP_ID,E.L_NAME,E.DEP_ID,D.DEP_NAME
	from EMPLOYEES AS E 
	INNER JOIN DEPARTMENTS AS D ON E.DEP_ID=D.DEPT_ID_DEP 
	where YEAR(E.B_DATE) < 1980
;
```

### Select, left outer join and where conditions ###

```
--- Query 2C ---
select E.EMP_ID,E.L_NAME,E.DEP_ID,D.DEP_NAME
	from EMPLOYEES AS E 
	LEFT OUTER JOIN DEPARTMENTS AS D ON E.DEP_ID=D.DEPT_ID_DEP 
	AND YEAR(E.B_DATE) < 1980
;
```

### UNION sub-queries, joining ###

```
--- Query 3A ---

select E.F_NAME,E.L_NAME,D.DEP_NAME
	from EMPLOYEES AS E 
	LEFT OUTER JOIN DEPARTMENTS AS D ON E.DEP_ID=D.DEPT_ID_DEP

UNION

select E.F_NAME,E.L_NAME,D.DEP_NAME
	from EMPLOYEES AS E 
	RIGHT OUTER JOIN DEPARTMENTS AS D ON E.DEP_ID=D.DEPT_ID_DEP
;
```

### UNION sub-queries, joining on multiple matching conditions ###

```
--- Query 3B ---
select E.F_NAME,E.L_NAME,D.DEPT_ID_DEP, D.DEP_NAME
	from EMPLOYEES AS E 
	LEFT OUTER JOIN DEPARTMENTS AS D ON E.DEP_ID=D.DEPT_ID_DEP AND E.SEX = 'M'


UNION

select E.F_NAME,E.L_NAME,D.DEPT_ID_DEP, D.DEP_NAME
	from EMPLOYEES AS E 
	RIGHT OUTER JOIN DEPARTMENTS AS D ON E.DEP_ID=D.DEPT_ID_DEP AND E.SEX = 'M'
;
```

### Select, left outer join and where conditions ###

```
--- alt Query 3B ---
select E.F_NAME,E.L_NAME,D.DEPT_ID_DEP, D.DEP_NAME
	from EMPLOYEES AS E 
	LEFT OUTER JOIN DEPARTMENTS AS D ON E.DEP_ID=D.DEPT_ID_DEP AND E.SEX = 'M'
;
```

---

<p align="center" width="100%">
    <img width="30%" src="https://github.com/jkaewprateep/advanced_mysql_topics_notes/blob/main/custom_dataset.png">
    <img width="30%" src="https://github.com/jkaewprateep/advanced_mysql_topics_notes/blob/main/custom_dataset_2.png"> </br>
    <b> 🥺💬 รับจ้างเขียน functions </b> </br>
</p>
