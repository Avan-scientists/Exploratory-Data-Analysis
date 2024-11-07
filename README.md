# Companies-layoffs-Analysis

### Project Overview
 This data Analysis Project aim to provide the insights into company's layoffs in the world over the past years. By Analyzing various aspects of data layoffs, we seek to identify trends, makw data-driven recommendations.

 ### Data Sources
  Layoffs data: The primary dataset used for this analysis is the "layoffs.csv" file, containing detailed information about each company's layoffs.

  ### Tools
    1.mySQL server- Data cleaning and Data Analysis
    2.PowerBI-creating a report

   ### Data cleaning and Preparaion
    1.Data inspections
    2.Remove Duplicates
    3.Standardize the data
    4.Remove Null/blank Values
    5.Remove all rows and columns tha aren't necessary
    
### Exploratory Data Analysis
 EDA involved exploring the layoffs data to answer the key questions, such as:
   1.What is overall layoffs trend?
   2.Which company are top layoffs?
   3.What are the total percentage laid_offs


Let start 

```sql
SELECT *
FROM layoffs;
```
Let create some type of staging
```sql
CREATE TABLE layoffs_stage
LIKE layoffs;
```
Inserting values into our new table
```sql
INSERT INTO layoffs_stage
SELECT *
FROM layoffs;
 ----------
SELECT *
FROM layoffs_stage;
```
Find the row_number that will help to find the matches against all of these columns and help to determine duplicated values
```sql
SELECT *;
ROW_NUMBER() OVER(
PARTITION BY company,location,total_laid_off,percentage_laid_off,`date`) AS row_num
FROM layoffs_stage
)
```
Create CTEs(Common Table Expressions) to define sub query block that you can then reference within the main query
```sql
WITH duplicate_cte AS(
SELECT *;
ROW_NUMBER() OVER(
PARTITION BY company,location,industry,total_laid_off,percentage_laid_off,country,`date`) AS row_num
FROM layoffs_stage
)
SELECT *
FROM duplicate_cte
WHERE row_num > 1;
```
```sql
SELECT *
FROM layoffs_stage
WHERE company='Casper';
```
Let create another staging table
















   
