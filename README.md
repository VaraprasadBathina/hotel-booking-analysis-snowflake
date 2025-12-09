# 🏨 Hotel Booking Analysis – End-to-End Snowflake Data Engineering Project

This project demonstrates how to build a complete Snowflake-native data engineering pipeline that transforms messy hotel booking data into clean, structured, and analytics-ready insights.
Every step — ingestion, cleaning, modeling, aggregation, and dashboarding — is performed entirely inside Snowflake, without Python, dbt, Airflow, PowerBI, or Tableau.

# 📐 Architecture Overview

Below is the architecture used for this project. The pipeline follows the Medallion model (Bronze → Silver → Gold), all implemented within Snowflake.

<img width="2912" height="1472" alt="Gemini_Generated_Image_ig5l2tig5l2tig5l" src="https://github.com/user-attachments/assets/6cd644ff-4265-447b-8f8e-94e8ea4d4ebb" />


# 🧩 Problem Statement

The hotel chain provided booking data in a single raw CSV file containing structural inconsistencies and data quality issues. This prevented management from generating reliable reports and understanding core business performance metrics.

Key issues in the raw data:

Dates stored as plain strings

Numeric values stored as text

Negative revenue values

Typos in city names and booking status

Missing or invalid email formats

Logical errors (checkout < check-in)

Nulls and empty strings used interchangeably

Because of these issues, the business could not answer:

What is the monthly revenue?

How many bookings were made each month?

Which cities contribute the most revenue?

What is the distribution across room types?

What percentage of bookings are confirmed vs canceled?

What is the Average Booking Value?

The goal was to build a fully automated pipeline that delivers clean, trusted, analytics-ready data.

# 📌 Business Requirements

The client required the following:

1. High-quality, standardized booking data

Convert all fields to correct data types

Standardize text formatting (city names, status)

Validate and correct emails

Replace negative amounts using business logic

Remove invalid bookings

2. Monthly performance reporting

Monthly revenue trend

Monthly booking counts

3. City-level revenue insights

Identify top revenue-generating cities

Compare performance across branches

4. Operational analytics

Room type distribution

Booking status breakdown

Guest counts

5. Executive KPIs

The dashboard must show:

Total Revenue

Total Bookings

Total Guests

Average Booking Value

6. 100% Snowflake implementation

All ingestion, transformation, and visualization must remain inside Snowflake, using:

Snowflake Stage

Snowflake File Format

Snowflake SQL

Medallion Architecture

Snowsight (Snowflake’s native dashboarding tool)

# 🏗️ What I Built

I developed a complete Snowflake Medallion Pipeline:

## 🟤 Bronze Layer

Ingest raw CSV data exactly as received.

## ⚪ Silver Layer

Clean, validate, and standardize the dataset:

Date conversions

Numeric transformations

City name formatting

Email validation

Negative revenue correction

271 invalid rows removed

## 🟡 Gold Layer

Create analytics-ready tables:

Monthly metrics

City-level revenue table

Master cleaned dataset for KPIs

# 📊 Dashboard (Snowsight)

A final business dashboard that displays:

Monthly revenue

Monthly bookings

Top revenue cities

Room type analysis

Booking status distribution

KPI scorecards

# 🔄 How the Pipeline Works
1. Data Ingestion (Bronze Layer)

Created FILE FORMAT to correctly parse CSV

Loaded file into a Snowflake Stage

Used COPY INTO Bronze_Hotel_Booking

All fields stored as VARCHAR

Error-tolerant ingestion (ON ERROR = CONTINUE)

2. Data Cleaning (Silver Layer)

Steps applied:

Convert text fields into proper DATE, INTEGER, FLOAT

Standardize city names: INITCAP(TRIM(city))

Convert negative total amounts using ABS()

Validate email format using pattern matching

Fix booking status typos

Remove 271 rows where checkout < check-in

The Silver layer contains clean, validated, trustworthy data.

3. Business Aggregations (Gold Layer)
Gold Table 1 — Daily/Monthly Metrics

Total bookings per day

Total revenue per day

Supports monthly trend charts

Gold Table 2 — City Revenue Table

Revenue grouped by city

Ranked for top-5 city charts

Gold Table 3 — Master Clean Table

All cleaned columns

Used for KPIs and detailed analytics

# 📊 Dashboard (Snowsight)

The Hotel Booking Analytics Dashboard includes:

📈 Monthly Trends

Monthly Revenue

Monthly Bookings

🏙️ City-Level Analysis

Top 5 Revenue-Generating Cities

🛏 Room Types

Booking distribution by room type

📊 Booking Status

Confirmed

Canceled

No-show

🔢 KPIs

Total Revenue

Total Bookings

Total Guests

Average Booking Value

All visuals are built inside Snowsight, sourced directly from Gold tables.


# 🧰 Tech Stack

Snowflake

Snowflake SQL

Snowflake Stage

File Format (CSV)

Snowsight Dashboard

Medallion Architecture

# 📬 Contact

If you’d like to connect or discuss data engineering projects:

LinkedIn: https://www.linkedin.com/in/lakshmi-prasad-b-91a67b198/

Email: blaxmiprasad6@gmail.com
