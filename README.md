**🏨 Hotel Booking Analysis – End-to-End Snowflake Data Engineering Project**

This project is a fully Snowflake-native data engineering pipeline that transforms raw, inconsistent hotel booking data into clean, structured, and analytics-ready insights.
The entire workflow — ingestion, cleaning, modeling, aggregation, and visualization — is built completely inside Snowflake, without any external ETL tools, Python notebooks, or BI platforms.

**📌 Problem Statement**

The hotel client provided monthly booking data in a single raw CSV file. The file contained several data quality issues:

Dates stored as plain text

Numbers stored as strings

Negative values in the total amount column

Misspelled city names and booking statuses

Records with checkout dates earlier than check-in dates

Missing or invalid email addresses

Inconsistent formatting across rows

Because of this, management couldn't reliably answer key business questions such as:

What is our monthly revenue?

How many bookings do we get each month?

Which cities generate the highest revenue?

How many bookings are confirmed, canceled, or pending?

What are the top-performing room types?

The business needed a clean, automated pipeline that produced accurate metrics and dashboards from inconsistent data.

**📌 Business Requirements**

The client specified the following requirements:

1. Clean and Standardized Data

Convert all columns into correct data types

Standardize text fields (city names, status)

Validate and correct email formats

Fix negative revenue amounts

Remove logically invalid records

Enforce consistent NULL handling

2. Monthly Trends

Monthly revenue

Monthly booking volume

Support for seasonal analysis

3. City-Level Revenue Insights

Total revenue per city

Ranking of top-performing cities

4. Booking Distribution

Room type distribution

Booking status breakdown

5. KPI Metrics

The dashboard needed to show:

Total Revenue

Total Bookings

Total Guests

Average Booking Value

6. Fully Snowflake-Native Dashboard

All visuals must be created using Snow Site, using only Snowflake tables as the backend.

**📌 What I Built**

I designed and implemented a complete Bronze → Silver → Gold Snowflake pipeline:

Bronze Layer: Raw ingestion

Silver Layer: Data cleaning, standardization, validation

Gold Layer: Aggregation tables for business reporting

Snow Site Dashboard: Monthly trends, city insights, booking analysis, and KPIs

Every step is implemented using SQL inside Snowflake, making it simple, maintainable, and scalable.

**📌 How I Built It**
1. Bronze Layer – Raw Ingestion

Created a Snowflake database and schema

Defined a CSV file format (skip header, handle NULLs, ignore quotes)

Uploaded the raw CSV file to a Snowflake Stage

Loaded data into a Bronze table with all columns stored as VARCHAR

Allowed partial loads using ON ERROR = CONTINUE

Preserved bad records for later inspection

This layer represents the untouched raw data exactly as received.

2. Silver Layer – Data Cleaning & Standardization

The Silver table was created with proper data types (DATE, INTEGER, FLOAT, etc.).

Cleaning steps applied:

Converted all date fields using TRY_TO_DATE

Converted numeric fields using TRY_TO_NUMBER

Standardized city names with INITCAP() and TRIM()

Fixed negative revenue using ABS()

Validated email addresses

Standardized booking statuses (corrected misspellings)

Removed 271 invalid records where checkout < check-in

The Silver layer ensures high data quality and consistency.

3. Gold Layer – Business Aggregations

Three business-focused Gold tables were created:

Gold Table 1: Monthly & Daily Metrics

Total bookings per day

Total revenue per day

Aggregated into month-level metrics

Gold Table 2: City Revenue Table

Total revenue per city

Sorted for identifying top cities

Gold Table 3: Master Clean Table

All 13 cleaned and standardized columns

Used for KPIs and detailed insights

These tables serve as the source of truth for all reporting and visualization.

**📌 Dashboard (Snow Site)**

The Hotel Bookings Analytics dashboard includes:

📈 Monthly Trends

Monthly revenue

Monthly booking count

🏙️ City Insights

Top 5 revenue-generating cities

🛏 Room & Status Analysis

Room type distribution

Booking status summary

🔢 KPI Scorecards

Total Revenue

Total Bookings

Total Guests

Average Booking Value

All visuals are powered directly from Gold tables to ensure accuracy.


**🧰 Tech Stack**

Snowflake Cloud Data Platform

Snowflake SQL

File Formats (CSV)

Snowflake Stages

Snowflake Medallion Architecture

Snow Site (Native Dashboarding)

**📌 Summary**

This project demonstrates:

End-to-end data engineering inside Snowflake

Scalable Medallion architecture

Automated cleaning + validation logic

Accurate business aggregation tables

A fully Snowflake-native dashboard

A clean SQL-only implementation

It is production-ready, easy to maintain, and suitable as a real-world data engineering solution.
