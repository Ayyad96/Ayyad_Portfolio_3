# Ayyad_Portfolio_3
Third_Portfolio data analyst portfolio (Police_death_crime_analysis)


CREATE TABLE fatalencounter (
	id VARCHAR(50) PRIMARY KEY,
	name VARCHAR(50),
	age INTEGER,
	gender VARCHAR(50),
	race VARCHAR(50),
	date_of_death DATE,
	loc_of_death VARCHAR(200),
	location VARCHAR(50),
	address VARCHAR(200),
	respon_agency VARCHAR(200),
	cause_of_death VARCHAR(100),
	official_disposition VARCHAR(100),
	use_of_force VARCHAR(100),
	mental_illness VARCHAR(50),
	year INT
)



CREATE TABLE policekilling (
	name VARCHAR(100),
	id VARCHAR(50) REFERENCES fatalencounter(id),
	age INT,
	gender VARCHAR(50),
	race VARCHAR(50),
	date DATE,
	address VARCHAR(200),
	city VARCHAR(100),
	state VARCHAR(100),
	zipcode INT,
	country VARCHAR(100),
	respon_agency VARCHAR(200),
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



