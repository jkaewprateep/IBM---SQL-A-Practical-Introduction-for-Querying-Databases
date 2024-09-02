# IBM - IBM - SQL A Practical Introduction for Querying Databases
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
```
# Q2 List all crimes that took place at a school. Include case number, crime type and community name.

SELECT * FROM chicago_crime A LEFT JOIN ( SELECT * FROM chicago_socioeconomic_data ) B
	ON A.COMMUNITY_AREA_NUMBER = B.COMMUNITY_AREA_NUMBER
;
```

### Select, where cause condition, and left join sub-query ###
```
# Q3 For the communities of Oakland, Armour Square, Edgewater and CHICAGO list the associated
# community_area_numbers and the case_numbers.

SELECT * FROM chicago_crime A LEFT JOIN ( SELECT * FROM `chicago_socioeconomic_data` WHERE COMMUNITY_AREA_NAME
	IN ( 'Oakland', 'Armour Square', 'Edgewater', 'Chicago Lawn' )) B
	ON A.COMMUNITY_AREA_NUMBER = B.COMMUNITY_AREA_NUMBER
;
```

### Create table view object ###
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

```
# Q9 Use a sub-query to determine which Community Area has the least value for school Safety Score?

SELECT * FROM "PYV10949".chicago_public_schools 
WHERE "SAFETY_SCORE" = ( SELECT MIN("SAFETY_SCORE") 
FROM "PYV10949".chicago_public_schools 
WHERE "SAFETY_SCORE" > 0 )
;
```

### Select data column value from the existence of value in the target data table ###

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
