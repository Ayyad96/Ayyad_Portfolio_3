# Ayyad_Portfolio_3
Third_Portfolio 
data analyst portfolio (Police_death_crime_analysis)

-- kaggle dataset on fatal encounter data record in united states
-- record data from 
-- cleaning the data in excel and done some data format and data wrangling
-- import the data to postgresql to view a better insight since this is a large data (excel is bit slow managing this data)
-- having a confusion regarding tha data 
-- need to reduce the scope and extract only a certain data in crime to view in dashboard


-- creating a table and column in postgresql to import tha data later
-- contain 3 table which contain different type of data regarding fatal encounter, police killing and police death
-- in this portfolio we'l be using crime data that were extracted from fatal encounter data

CREATE TABLE fatalencounter (
	id VARCHAR(50) PRIMARY KEY,
	name VARCHAR(50),
	age INTEGER,
	gender VARCHAR(50),
	race VARCHAR(50),
	date DATE,
	loc_of_death VARCHAR(200),
	state VARCHAR(50),
	address VARCHAR(300),
	respon_agency VARCHAR(300),
	cause_of_death VARCHAR(100),
	disposition VARCHAR(100),
	use_of_force VARCHAR(100),
	mental_illness VARCHAR(50),
	year INT);


CREATE TABLE policekilling (
	name VARCHAR(100),
	id VARCHAR(50),
	age INT,
	gender VARCHAR(50),
	race VARCHAR(50),
	date DATE,
	address VARCHAR(200),
	city VARCHAR(100),
	state VARCHAR(100),
	zipcode INT,
	country VARCHAR(100),
	respon_agency VARCHAR(300),
	death_cause VARCHAR(100),
	official_disposition VARCHAR(200),
	court_charges VARCHAR(200),
	mental_illness VARCHAR(200),
	weapon VARCHAR(100),
	threat_level VARCHAR(100),
	fleeing VARCHAR(100),
	body_camera VARCHAR(100),
	duty VARCHAR(100),
	geography VARCHAR(100));


CREATE TABLE policedeath (
	name VARCHAR(100),
	death_cause VARCHAR(100),
	date DATE,
	year INT,
	canine VARCHAR(100),
	dept VARCHAR(100),
	state VARCHAR(100));

-- checking the condition of the data in the table after we import it on sql(postgresql)
-- i did a few code here to get a better insight in this fatal encounter table
-- i realized that this data in fatal encounter table contain more than just crime data

SELECT race, year, location, COUNT(race) OVER (PARTITION BY location) AS totalcount
FROM fatalencounter
ORDER BY totalcount DESC;

SELECT race, COUNT(*)
FROM fatalencounter
GROUP BY race 
ORDER BY COUNT(*) DESC;

SELECT year, COUNT(*)
FROM fatalencounter
WHERE year IS NOT NULL
GROUP BY year 
ORDER BY year;

SELECT DISTINCT use_of_force FROM fatalencounter;

SELECT state, COUNT(*)
FROM fatalencounter
GROUP BY state
ORDER BY COUNT(*) DESC;

SELECT age, COUNT(*)
FROM fatalencounter
WHERE age IS NOT NULL
GROUP BY age 
ORDER BY COUNT(*) DESC;

SELECT DISTINCT mental_illness
FROM fatalencounter;

SELECT mental_illness, COUNT(*)
FROM fatalencounter
WHERE mental_illness IS NOT NULL 
GROUP BY mental_illness
ORDER BY COUNT(*) DESC;

SELECT gender, COUNT(*)
FROM fatalencounter
WHERE gender IS NOT NULL
GROUP BY gender
ORDER BY COUNT(*) DESC;

-- i realized that in order to create a dashboard using this data, i nedd to reduce the data into something that easier to understand in  a smaller context
-- i extract only crime data from the table after running and understanding some law research regarding the court trial in disposition since the data(disposition) recorded -- in the fatal encounter table

SELECT * FROM fatalencounter WHERE age < 10;

-- the point where i realized that this is  big data that are not only focusing on police and crime but also other case that are recorded as fatal encounter case that -- 
-- include killing a child and stuff

SELECT DISTINCT cause_of_death
FROM fatalencounter;

-- i extract and create a new table that focusing on crime fatal encounter only which i extract and recognized the crime data based on the disposition column of the table
-- disposition refer to the court final outcome of the case

CREATE TABLE crime AS
SELECT * FROM fatalencounter
WHERE disposition = 'Criminal/Civil suit/Pending' 
OR disposition = 'Criminal' 
OR disposition = 'Criminal/Civil suit/Family awarded money' 
OR disposition = '/Criminal'
OR disposition = 'Murder/suicide'
OR disposition = 'Criminal/Off-duty/Acquitted'
OR disposition = 'Criminal/Officer indicted/Guilty'
OR disposition = 'Murder/Suicide'
OR disposition = 'Criminal/Off-duty'
OR disposition = 'Grand jury/No bill or Cleared'
OR disposition = 'Grand jury/Referred to prosecutor'
OR disposition = 'Civil suit/Settled out of court'
OR disposition = 'Murder/Suicide';

-- then i start to analyze the crime data that were extracted from fatal encounter table

SELECT * FROM crime;

SELECT age, COUNT(age)
FROM crime
GROUP BY age
ORDER BY COUNT(age) DESC
LIMIT 6;


/*
<img width="614" alt="crime_report_fatalencounter_agecount_dashboard" src="https://github.com/Ayyad96/Ayyad_Portfolio_3/assets/140683898/614b245c-b3e5-4ef1-a6e7-8f09cc25648f">
*/


SELECT gender, COUNT(age)
FROM crime
GROUP BY gender
ORDER BY COUNT(age); 


/*
<img width="615" alt="crime_report_fatalencounter_genderpercentage_dashboard" src="https://github.com/Ayyad96/Ayyad_Portfolio_3/assets/140683898/a07d7bb7-a12a-44dc-83b2-ae6b97f2f200">
*/


SELECT race, COUNT(age)
FROM crime
GROUP BY race
ORDER BY COUNT(age) DESC;


/*
<img width="615" alt="crime_report_fatalencounter_totalcasebyrace_dashboard" src="https://github.com/Ayyad96/Ayyad_Portfolio_3/assets/140683898/eb29b690-a70d-455a-96a6-9f0146569255">
*/


SELECT state, COUNT(age)
FROM crime
GROUP BY state
ORDER BY COUNT(age) DESC;


/*
<img width="615" alt="crime_report_fatalencounter_totalcasebystate_dashboard" src="https://github.com/Ayyad96/Ayyad_Portfolio_3/assets/140683898/e70f7002-7c07-46ee-9fd2-9cf5e2947916">
*/


SELECT year, COUNT(age)
FROM crime
GROUP BY year
ORDER BY year;


/*
<img width="614" alt="crime_report_fatalencounter_totalcaseperyear_dashboard" src="https://github.com/Ayyad96/Ayyad_Portfolio_3/assets/140683898/bfa7f35f-2012-464d-8ca1-25b67bd06b5a">
*/


SELECT * FROM crime;


/*
<img width="615" alt="Full_report_crime_fatalencounter_dashboard" src="https://github.com/Ayyad96/Ayyad_Portfolio_3/assets/140683898/29d77ec2-87d5-4d99-b0ba-bcf8537fc096">
*/
















