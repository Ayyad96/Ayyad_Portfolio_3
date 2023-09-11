# Ayyad_Portfolio_3
Third_Portfolio data analyst portfolio (Police_death_crime_analysis)


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
	year INT
)


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
	geography VARCHAR(100)
)



CREATE TABLE policedeath (
	name VARCHAR(100),
	death_cause VARCHAR(100),
	date DATE,
	year INT,
	canine VARCHAR(100),
	dept VARCHAR(100),
	state VARCHAR(100)
)





SELECT race, year, location, COUNT(race) OVER (PARTITION BY location) AS totalcount
FROM fatalencounter
ORDER BY totalcount DESC

SELECT race, COUNT(*)
FROM fatalencounter
GROUP BY race 
ORDER BY COUNT(*) DESC

SELECT year, COUNT(*)
FROM fatalencounter
WHERE year IS NOT NULL
GROUP BY year 
ORDER BY year 

SELECT DISTINCT use_of_force FROM fatalencounter

SELECT state, COUNT(*)
FROM fatalencounter
GROUP BY state
ORDER BY COUNT(*) DESC

SELECT age, COUNT(*)
FROM fatalencounter
WHERE age IS NOT NULL
GROUP BY age 
ORDER BY COUNT(*) DESC

SELECT DISTINCT mental_illness
FROM fatalencounter

SELECT mental_illness, COUNT(*)
FROM fatalencounter
WHERE mental_illness IS NOT NULL 
GROUP BY mental_illness
ORDER BY COUNT(*) DESC

SELECT gender, COUNT(*)
FROM fatalencounter
WHERE gender IS NOT NULL
GROUP BY gender
ORDER BY COUNT(*) DESC

SELECT * FROM fatalencounter WHERE age < 10

SELECT DISTINCT cause_of_death
FROM fatalencounter
















