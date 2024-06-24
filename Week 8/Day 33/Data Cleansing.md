#data-engineering 

## Overview
- Introduction to **Data Cleansing**
- Data quality
- Inspecting data
- How data is cleansed


## Learning Objectives

- Define what **Data Cleansing** is
- Explore areas to consider when assessing data quality
- Gain insight into the ways data is inspected
- Identify some approaches to cleansing data

---
## What is Data Cleansing?

Data Cleansing is the process of detecting and correcting data quality.

You can get all sorts of data issues:

- Inaccurate data
- Corrupt data
- Duplicated data
- Irrelevant data
- Personally Identifiable Information (PII) data that needs to be removed

---
## Data Quality

When assessing data quality, consider the following:

- Validity
- Accuracy
- Consistency
- Completeness
- Uniformity


### Validity

The degree to which the data conforms to defined business rules or constraints.

E.g. certain columns can't be empty, certain columns must be a particular data type such as a date.

### Accuracy

The degree to which the data is 'true'.

E.g. validating that a postcode actually exists.

### Consistency

The degree to which the data is consistent, within the same data set or across multiple data sets.

E.g. a customer has two different addresses in two different tables.

### Completeness

The degree to which all the data required is known.

E.g. missing data from a form that was filled in.

### Uniformity

Ensuring that data is using the same unit of measure.

E.g. 21/01/2020 or 01/21/2020.

---

## Mitigating against bad data

We can follow this process to help mitigate against bad data:

1. Inspect
2. Cleanse
3. Verify
4. Report


### 1. Inspect

Take a look at the data to see if there are any issues. It can be rather time-consuming, but luckily there are plenty of tools and methods to help out.

#### How to inspect data

- **Data profiling**: How many values are missing? How many unique values in a column, and their distribution?
- **Visualisations**: By analysing and visualising the data using statistical methods such as mean, standard deviation, range, or quantiles, one can find values that are unexpected.
- **Software packages**: Packages or libraries are available that let you specify constraints and check the data for violation of these constraints.


### 2. Cleanse

The most important part of data cleansing!

The aim of cleansing data is to not only **cleanse** the data, but also bring **consistency** to the data.

#### How do we cleanse data?

There are some steps in cleansing data:

- Parse
- Correct
- Standardise
- Match
- Consolidate

##### Parse

Parsing data means we are breaking up the source data into smaller bits following some rules. This allows us to 'do things' with the data easily.

E.g. splitting addresses so we can use only the postcode.


##### Correct

Now the data is in smaller chunks, we can now correct bits of it.

E.g. fixing typos like "Hel.o" to "Hello".

##### Standardise

Now it's cleansed, we want to make sure the data is consistent and all looks the same.

E.g. changing a date format from 04/29/2020 to 29/04/2020.

##### Match

Now we have cleansed and standardised data, we want to match it to our data definitions, and also rule out any duplicates.

E.g. are there similar names and addresses, like Mr Andrew Smith and Mr A. Smith at the same address.

##### Consolidate

Now we find relationships between all of our data and merging them into one.

E.g. The process of combining Mr Smith's data above into one correct record.


### 3. Verify

Now we've cleansed the data, we need to verify (inspect) it again to make sure we haven't made it worse!

E.g. all dates are the correct format, duplicates have been removed, typos corrected etc.

### 4. Report

After we've verified the data, we want to take a look to understand what changes we made, and maybe consider why they occurred in the first place!

How can we avoid these issues happening again?

Notes: Can we affect the input data? Do we need to build in some data processing?

---