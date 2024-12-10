-- Run all this code at once in PostgreSQL to create 15 (fake) EHR data tables --

CREATE TABLE IF NOT EXISTS allergies
(
    start date,
    stop date,
    patient character varying(1000),
    encounter character varying(1000),
    code character varying(1000),
    description character varying(1000),
    type character varying(1000),
    category character varying(1000),
    reaction1 character varying(1000),
    severity1 character varying(1000),
    reaction2 character varying(1000),
    severity2 character varying(1000) 
);

CREATE TABLE IF NOT EXISTS careplans
(
    id character varying(1000),
    start character varying(1000),
    stop character varying(1000),
    patient character varying(1000),
    encounter character varying(1000),
    code character varying(1000),
    description character varying(1000) 
);

CREATE TABLE IF NOT EXISTS conditions
(
    start date,
    stop date,
    patient character varying(1000),
    encounter character varying(1000),
    code character varying(1000),
    description character varying(200) 
);

CREATE TABLE IF NOT EXISTS devices
(
    start timestamp without time zone,
    stop timestamp without time zone,
    patient character varying(200),
    encounter character varying(200),
    code character varying(200),
    description character varying(200),
    udi character varying(100) 
);

CREATE TABLE IF NOT EXISTS encounters
(
    id character varying(100),
    start timestamp without time zone,
    stop timestamp without time zone,
    patient character varying(100),
    organization character varying(100),
    provider character varying(100),
    payer character varying(100),
    encounterclass character varying(100),
    code character varying(100),
    description character varying(100),
    base_encounter_cost double precision,
    total_claim_cost double precision,
    payer_coverage double precision,
    reasoncode character varying(100) 
);

CREATE TABLE IF NOT EXISTS immunizations
(
    date timestamp without time zone,
    patient character varying(100),
    encounter character varying(100),
    code integer,
    description character varying(500) 
);

CREATE TABLE IF NOT EXISTS medications
(
    start timestamp without time zone,
    stop timestamp without time zone,
    patient character varying(100),
    payer character varying(100),
    encounter character varying(100),
    code character varying(100),
    description character varying(500),
    base_cost double precision,
    payer_coverage double precision,
    dispenses double precision,
    totalcost double precision
);

CREATE TABLE IF NOT EXISTS observations
(
    date timestamp without time zone,
    patient character varying(100),
    encounter character varying(100),
    category character varying(100),
    code character varying(100),
    description character varying(500),
    value character varying(500),
    units character varying(100),
    type character varying(100) 
);

CREATE TABLE IF NOT EXISTS organizations
(
    id character varying(100),
    name character varying(100),
    address character varying(100),
    city character varying(50),
    state character varying(3),
    zip integer,
    lat double precision,
    lon double precision,
    phone character varying(100),
    revenue double precision,
    utilization integer
);

CREATE TABLE IF NOT EXISTS patients
(
    id character varying(100),
    birthdate date,
    deathdate date,
    ssn character varying(100),
    drivers character varying(100),
    passport character varying(100),
    prefix character varying(100),
    first character varying(100),
    last character varying(100),
    suffix character varying(100),
    maiden character varying(100),
    marital character varying(100),
    race character varying(100),
    ethnicity character varying(100),
    gender character varying(100),
    birthplace character varying(100),
    address character varying(100),
    city character varying(100),
    state character varying(100),
    county character varying(100),
    fips integer,
    zip integer,
    lat double precision,
    lon double precision,
    healthcare_expenses double precision,
    healthcare_coverage double precision,
    income integer,
    mrn integer
);

CREATE TABLE IF NOT EXISTS payer_transitions
(
    patient character varying(100),
    memberid character varying(100),
    start_date timestamp without time zone,
    end_date timestamp without time zone,
    payer character varying(100),
    secondary_payer character varying(100),
    plan_ownership character varying(100),
    owner_name character varying(100) 
);

CREATE TABLE IF NOT EXISTS payers
(
    id character varying(100),
    name character varying(100),
    ownership character varying(100),
    address character varying(100),
    city character varying(100),
    state_headquartered character varying(100),
    zip character varying(100),
    phone character varying(100),
    amount_covered double precision,
    amount_uncovered double precision,
    revenue double precision,
    covered_encounters integer,
    uncovered_encounters integer,
    covered_medications integer,
    uncovered_medications integer,
    covered_procedures integer,
    uncovered_procedures integer,
    covered_immunizations integer,
    uncovered_immunizations integer,
    unique_customers integer,
    qols_avg double precision,
    member_months integer
);

CREATE TABLE IF NOT EXISTS procedures
(
    start timestamp without time zone,
    stop timestamp without time zone,
    patient character varying(100),
    encounter character varying(100),
    code character varying(10),
    description character varying(500),
    base_cost double precision
);

CREATE TABLE IF NOT EXISTS providers
(
    id character varying(100),
    organization character varying(100),
    name character varying(100),
    gender character varying(2),
    speciality character varying(100),
    address character varying(100),
    city character varying(80),
    state character varying(3),
    zip integer,
    lat double precision,
    lon double precision,
    encounters integer,
    procedures integer
);

CREATE TABLE IF NOT EXISTS supplies
(
    date date,
    patient character varying(100),
    encounter character varying(100),
    quantity integer,
    description character varying(100),
    code character varying(100) 
);

