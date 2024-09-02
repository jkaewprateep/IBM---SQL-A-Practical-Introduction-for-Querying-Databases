# IBM - IBM - SQL A Practical Introduction for Querying Databases
IBM - SQL A Practical Introduction for Querying Databases

* IBM Data Warehouse Engineer Professional Certificate [IBM]( https://github.com/jkaewprateep/Portfolio/blob/main/Coursera%204K7JZCI2I9XO.pdf )
* IBM Business Intelligence (BI) Analyst Professional Certificate [IBM]( https://github.com/jkaewprateep/Portfolio/blob/main/Coursera%200QO1U1C6S867.pdf )
* Meta Database Engineer Professional Certificate [META]( https://coursera.org/share/0b7133ceaec8027d53af1c74b7d8e47d )
* Meta Back-End Developer Professional Certificate [META]( https://coursera.org/share/bc30f508bcf68936d9028e9d0d6b9dfc )
* HackerRank SQL (Advance) [HackerRank]( https://www.hackerrank.com/certificates/f225fa371510 )

<p align="center" width="100%">
    <img width="47%" src="https://github.com/jkaewprateep/IBM---SQL-A-Practical-Introduction-for-Querying-Databases/blob/main/IBM%20-%20SQL%20A%20Practical%20Introduction%20for%20Querying%20Databases%20instructor.png">
    <img width="17.63%" src="https://github.com/jkaewprateep/IBM---SQL-A-Practical-Introduction-for-Querying-Databases/blob/main/kid_29.jpg"> </br>
    <b> Pictures from the Internet </b> </br>
</p>

## Practical quizzes - not a peer review ##

```
# Q1 List the case number, type of crime and community area for all crimes in community area number 18. # SELECT * FROM chicago_socioeconomic_data WHERE `COMMUNITY_AREA_NUMBER` = 18; # SELECT * FROM chicago_crime # SELECT * FROM chicago_public_schools # area SELECT * FROM chicago_public_schools A INNER JOIN ( SELECT * FROM chicago_socioeconomic_data ) B ON A.COMMUNITY_AREA_NUMBER = B.COMMUNITY_AREA_NUMBER
```

```
# Q2 List all crimes that took place at a school. Include case number, crime type and community name. SELECT * FROM chicago_crime A LEFT JOIN ( SELECT * FROM chicago_socioeconomic_data ) B ON A.COMMUNITY_AREA_NUMBER = B.COMMUNITY_AREA_NUMBER
```

```
# Q3 For the communities of Oakland, Armour Square, Edgewater and CHICAGO list the associated community_area_numbers and the case_numbers. SELECT * FROM chicago_crime A LEFT JOIN ( SELECT * FROM `chicago_socioeconomic_data` WHERE COMMUNITY_AREA_NAME IN ( 'Oakland', 'Armour Square', 'Edgewater', 'Chicago Lawn' )) B ON A.COMMUNITY_AREA_NUMBER = B.COMMUNITY_AREA_NUMBER
```


---

```

--- Query1A ---
select E.F_NAME,E.L_NAME, JH.START_DATE 
	from EMPLOYEES as E 
	INNER JOIN JOB_HISTORY as JH on E.EMP_ID=JH.EMPL_ID 
	where E.DEP_ID ='5'
;	
--- Query1B ---	
select E.F_NAME,E.L_NAME, JH.START_DATE, J.JOB_TITLE 
	from EMPLOYEES as E 
	INNER JOIN JOB_HISTORY as JH on E.EMP_ID=JH.EMPL_ID 
	INNER JOIN JOBS as J on E.JOB_ID=J.JOB_IDENT
	where E.DEP_ID ='5'
;
--- Query 2A ---
select E.EMP_ID,E.L_NAME,E.DEP_ID,D.DEP_NAME
	from EMPLOYEES AS E 
	LEFT OUTER JOIN DEPARTMENTS AS D ON E.DEP_ID=D.DEPT_ID_DEP
;	
--- Query 2B ---
select E.EMP_ID,E.L_NAME,E.DEP_ID,D.DEP_NAME
	from EMPLOYEES AS E 
	LEFT OUTER JOIN DEPARTMENTS AS D ON E.DEP_ID=D.DEPT_ID_DEP 
	where YEAR(E.B_DATE) < 1980
;
--- alt Query 2B ---
select E.EMP_ID,E.L_NAME,E.DEP_ID,D.DEP_NAME
	from EMPLOYEES AS E 
	INNER JOIN DEPARTMENTS AS D ON E.DEP_ID=D.DEPT_ID_DEP 
	where YEAR(E.B_DATE) < 1980
;
--- Query 2C ---
select E.EMP_ID,E.L_NAME,E.DEP_ID,D.DEP_NAME
	from EMPLOYEES AS E 
	LEFT OUTER JOIN DEPARTMENTS AS D ON E.DEP_ID=D.DEPT_ID_DEP 
	AND YEAR(E.B_DATE) < 1980
;
--- Query 3A ---

select E.F_NAME,E.L_NAME,D.DEP_NAME
	from EMPLOYEES AS E 
LEFT OUTER JOIN DEPARTMENTS AS D ON E.DEP_ID=D.DEPT_ID_DEP

UNION

select E.F_NAME,E.L_NAME,D.DEP_NAME
	from EMPLOYEES AS E 
RIGHT OUTER JOIN DEPARTMENTS AS D ON E.DEP_ID=D.DEPT_ID_DEP
--- Query 3B ---
select E.F_NAME,E.L_NAME,D.DEPT_ID_DEP, D.DEP_NAME
	from EMPLOYEES AS E 
	LEFT OUTER JOIN DEPARTMENTS AS D ON E.DEP_ID=D.DEPT_ID_DEP AND E.SEX = 'M'


UNION

select E.F_NAME,E.L_NAME,D.DEPT_ID_DEP, D.DEP_NAME
	from EMPLOYEES AS E 
	RIGHT OUTER JOIN DEPARTMENTS AS D ON E.DEP_ID=D.DEPT_ID_DEP AND E.SEX = 'M'
;
--- alt Query 3B ---
select E.F_NAME,E.L_NAME,D.DEPT_ID_DEP, D.DEP_NAME
	from EMPLOYEES AS E 
	LEFT OUTER JOIN DEPARTMENTS AS D ON E.DEP_ID=D.DEPT_ID_DEP AND E.SEX = 'M'
;
```
