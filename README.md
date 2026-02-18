# Data Platform Engineer – Skill Assessment

## Overview
This project demonstrates how I clean and normalize a CSV file containing 5,000 unclean records.

I approached the problem by first addressing fields with simpler rules, followed by names and addresses, which require more parsing and effort. Breaking the work down by field made validation easier and allowed for clear before and after comparisons during development.

A Dockerfile is included to allow the pipeline to be run in a reproducible local environment.

The final output CSV matches the desired output. Tests and validations are handled in comments! Any exploratory data analysis was handled during creation but mainly consisted of looking at the .head() or .tail() and understanding the shape. In most environments I would screenshot that the data had landed in the database/datawarehouse via a time based query.  

## Assumptions
-A few of the assumptions I made were based on the size and handling of the data, given the prompt. The size and shape of the csv did not seem to need pagination as the size of the file was not too large and is static. This is treated as batch processed. I did not assume this was a near real-time or coming from a rate limited API.
-Another assumption I made was that there are several avenues to identify the individuals on this list and therefore accurate information that is in proper format matters more than the volume of data one has collected on an individual. 
-I also am assuming that this is for single execution. In a production setting, I would add idempotency guarantees, validation checkpoints, datetime stamps and incremental reprocessing support. 
-I also am assuming this is a US based customer profile, mainly because of the phone number formatting and zip code format.
-These were made given my experience with unclean data and where human error or data entry can result in many different types of errors and inconsistencies. Also this information may have come from several different sources which is why the data does not seem to have the same prerequisites upon entry. Reg Ex has to be verbose and a thorough analysis has to be done to account for the variety of errors.

## Requirements
- Python 3.11+
- Dependencies in `requirements.txt`
- (Bonus)Docker for containerized execution



## Setup (Local Environment)

### 1. Ensure Python 3.11 or higher is installed:

python --version

### 2. Create and activate a virtual environment

python -m venv .venv
source .venv/bin/activate

### 3. Install dependencies

pip install -r requirements.txt

### 4. Place the provided input file in the project root

skill-assessment-202511.csv


Run this command
python clean_csv.py

Which generates cleaned output

I manually searched the ouput for correct format and I also left invalid rows as blank. 


