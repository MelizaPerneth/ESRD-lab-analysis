-- Either run the whole script as one block 
-- or you can run line 6 first, followed by lines 10-32 all as one block.

-- Creates a Schema called "real_data".
-- This will seperate content that is real from our test Synthea data
CREATE SCHEMA IF NOT EXISTS real_data;

-- This creates a table for our HAIs dataset
-- After it gets created, we will import data into it
CREATE TABLE IF NOT EXISTS real_data.hai_prod
(
facility_id character varying(100),
facility_name character varying(255),
address character varying(255),
city character varying(100),
state character varying(10),
zip_code character varying(10),
county character varying(100),
telephone_number character varying(20),
measure_id character varying(100),
measure_name character varying(255),
compared_to_national character varying(100),
infection_type text,
sir float,
predicted_cases float,
observed_cases int,
central_line_days int,
catheter_days int,
patient_days int,
start_date date,
end_date date
);
