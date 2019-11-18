# Project 5: Natural disasters and FEMA payouts in the USA


## Introduction

In this project we looked into the financial aspect of disasters in the United States. We used four different data sets from three different sources: FEMA, Census Bureau, and SBA. FEMA data was gathered through the API, and the Census Bureau and SBA data is located in the folder 'data_imports'.

1) The first was to use the Federal Emergency Management Agency’s housing assistance API. We were able to get close to 90,000 rows that had data from 2004 to the present. The data provided granularity by zip code level. The data that we used includes the disaster code, the number of FEMA registrations by zip code, the total home damage recorded by FEMA at the time of inspection, and the total approved amount under the individuals and household program that includes the repair and replace amount for the home, any rental assistance if they cannot be in their home, and any other needs such as medical or transportation. The individual and household program (IHP) provides financial and direct assistance to people who, as result of a disaster, have necessary expenses and serious needs that are not met through insurance or other means.

2) The FEMA disaster details were pulled from the API to gather data from 2004 to present. The granularity was by disaster code. Each disaster code provided the incident type (such as hurricane, flood) as well as the start and end dates for each disaster.

3) We used Census Bureau data to gather the mean and median income as well as population for each zip code. 

4) We gathered data from the Small Business Administration on their 504 loans from 2004 to present. The 504 loans are typically used to buy commercial real estate or large equipment. We used the SBA approval amount by zip code.

The statistical analysis is located in the jupyter notebook - feature_engineering_modeling.ipynb

A PDF of the presentation is also included in the project 5 folder. 



## Problem Statement

FEMA has a significant amount of data to sift through when it comes to disaster impact and relief prioritization. We are seeking to assist FEMA in building out a process and prototype vizualization toolkit that will better enable them to navigate such decisions. Specifically, our goals are two-fold:

1) To understand historical FEMA support in the context of average income and population sizes per zipcode. Has the organization correctly prioritized zipcodes that may not be able to, on average, lean on private insurance for disaster coverage? Can the SBA be leaning in further to help stimulate economies after disaster strikes?
 - Zipcode Explorer: https://public.tableau.com/profile/owen.curtis3576#!/vizhome/DisasterDashZipcodeExplorer/PrioritizationDash?publish=yes

 
2) To arm FEMA with a vizualization toolkit which enables them to assess priority zipcodes when disaster strikes. This includes a tool to estimate payouts at the zipcode level, and easily explore disaster and socioeconomic data at the zipcode level
 - Prediction Dash: https://public.tableau.com/profile/owen.curtis3576#!/vizhome/DisasterDashZipcodeExplorer/HurricaneTool


## Data Dictionary
| Variable                 | Type     | Description                                                                      |
|--------------------------|----------|----------------------------------------------------------------------------------|
| disaster_number          | int64    | FEMA disaster ID                                                                 |
| incident_type            | object   | Type of disaster (hurricane, flood)                                              |
| incident_begin           | datetime | Start date of disaster                                                           |
| incident_end             | datetime | End date of disaster                                                             |
| state                    | object   | State where disaster occurred                                                    |
| county                   | object   | County where disaster occurred                                                   |
| city                     | object   | City where disaster occurred                                                     |
| zipCode                  | int64    | Zipcode where disaster occurred                                                  |
| valid_registration       | int64    | Number of valid FEMA registrations in zipcode                                    |
| avg_damage               | int64    | Average damage experience by zipcode                                             |
| tot_damage               | int64    | Total damage at the zipcode level for a zipcode                                  |
| approve_assistance       | float64  | Approved assistance for disaster relief (not synonymous with below feature)      |
| tot_approve_ihp_amt      | float64  | Total approved funds provided by FEMA for disaster relief (TARGET)               |
| replair_replace_amt      | float64  | Initial repair support provided by FEMA ($)                                      |
| rental_amt               | float64  | Ongoing rental support provided by fema ($)                                      |
| other_needs_amt          | float64  | Other support provided by FEMA not covered by initial repair funds, rental funds |
| tot_max_grants           | int64    | Total max grants given by FEMA                                                   |
| Median                   | int32    | Income Median for each zipcode                                                   |
| Mean                     | int32    | Income Average for each zipcode                                                  |
| Pop                      | int32    | Population at the zipcode level                                                  |
| duration                 | float64  | Duration of disaster Event                                                       |
| registrations_per_capita | float64  | Number of FEMA registrants per zipcode populatoin                                |
| BorrState                | object   | SBA borrower state                                                               |
| BorrZip                  | int64    | SBA borrower zip code                                                            |
| GrossApproval            | float64  | SBA approval amount for borrower                                                 |

## Executive Summary

*Data Wrangling and Merging*
 - A number of different data sources were leveraged here including: FEMA Housing Disaster Assistance API, FEMA Disaster Details API, Census socioeconomic Data
 - In the case of FEMA API data, a majority of this data was joined on Disaster Number. For more granular joins, zipcode and date were also leveraged

*Feature Engineering*
 - To assist with predictive power of our model, a number of additional features were engineered. This included: Disaster Duration, FEMA Registrations Per Capita, Average Disaster Damage ($)
 

*EDA*
 - Initial EDA of the relationship between disaster support fund distribution and income (average and median) at the zipcode level did not reveal any glaring relationships. This suggests that this is a guiding factor in determining where funds are allocated **at the zipcode level**


*Modeling*
 - A number of different models were leveraged here including LogisticRegression, KNN Regressor, Adaboost, RandomForest, etc.
 - A train/test approach was taken to validate the resultant R^2 scores from our model.

*Tool Development*
 - We sought to create two primary views: a Zipcode Prioritization Dashboard, and Estimated Payout Dashboard.
 - The Zipcode Prioritization Dashboard includes all historical data from FEMA's disaster database, in addition to census level data. Analysts can dynamically filter at the state level to find zipcodes that have been significantly impacted, and the zipcodes that are most populous with lowest average income for prioritization.
 - The Estimated Payout Dashboard: includes model predictions against the dataset we were able to retrieve from FEMA. While this is currently based on historical data, it can be applied to future estimates with some additional tweaking. 

## What's Next?

*Establishing a Live Feed*
 - Currently our Tableau dashboard is sitting on historicals through mid 2019. In the coming month we will work to build a livestream from the FEMA API ontop of which our tools will sit

*Model Refinement / Estimate Tool Enhancements*
 - While we believe our prototype is an interesting and effective tool to assist FEMA analysts with payout predictions, we believe there is significant room for refinement. The incorporation of deeper data cuts (week level) and additional historical data (pre 2004) will enable this
 -The incorporation of confidence levels against each of our estimates. Because this is at the zipcode level, sample is problematic here and estimates at the level of granularity are unstable in the current iteration.
 - In addition to this, our next goal will be to integrate the estimation tool with real time hurricane tracker data. This will enable us to tie the hurricane track to the map functionality in place




