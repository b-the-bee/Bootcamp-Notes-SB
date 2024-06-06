#databases #data-science #data-engineering 

# Overview
- An introduction to data normalisation
- Advantages and disadvantages
- Normal Forms

# Learning Objectives
- Be able to explain what data normalisation is
- Understand some of the problems that normalisation helps to fix
- Practice implementing the steps to reach first, second and third normal form
- List some of the Pros and Cons of normalisation

# What is data normalisation?
- **Formally**: The process of structuring a relational database in accordance with a series of defined **normal forms** in order to reduce data **redundancy** and increase data **integrity**
- **Informally**: Organising our data to make it easy to work with, reduce duplication, and increase accuracy

# Why do we Normalise data
The need to normalise is best seen by looking at the problems we might encounter when data is **not normalised!**

# Unnormalised Data - Example
![[Pasted image 20240606111558.png]]

- Duplicate data - extra storage is used and updates need to be made in multiple places when something is changed
- Multiple values in a single column - we cannot easily work with that data when searching or querying
- Different data types in a single column - we cannot predict what data will be held for a given row
- Data about different entities (Student, Course and Instructor) in the same row - can lead to unintentional loss of data when rows are removed 

# Anomalies

An `Anomaly` is a data problem caused by insufficient normalisation in our table, which can occur when we try to change the data that table holds.<br>

#### Three formal anomalies:

1. Insertion Anomaly
2. Update Anomaly
3. Deletion Anomaly

## Insertion Anomaly
- An inability to add data due to dependence on other data

Example scenario: A new Course Instructor starts work, but does not have any students enrolled yet
![[Pasted image 20240606112304.png]]


- Trying to add this data would result in empty (`null`) values for student fields
- Student number and course are both required in this table to uniquely identify a row as its `composite key`
- Adding the instructor is blocked until they have a student

Notes: Composite keys have not yet been mentioned in the course so far.

student_number and course fields are in this case two values that in conjunction form a composite key to uniquely identify a given row of data.

If we try to add instructor data without any student number, this constraint is violated.

Course itself is not enough to make the data unique because the same course can appear in the table multiple times.

## Update anomaly
- Inconsistency caused when duplicated data is only partially changed

Example scenario: An instructor updates their email address
![[Pasted image 20240606112616.png]]


- The email address must change in many records, but it is possible some of these records may be missed
- There are now two **different values** in the database for the same instructor's email

## Deletion anomaly
- Unintended loss of data when other unrelated data is removed

Example scenario: When a student's course ends, their row is deleted from the database
![[Pasted image 20240606112819.png]]

- If all students for a particular instructor are removed, there will be no copies of that instructor's name or email left, and that data has then been lost
- When `Matt Binns` is removed, we also delete information about `Tom New`

# Normalisation to the Rescue! 🎉

We can solve these problems with `Data Normalisation.`

After normalising:

- Redundant data (duplicate data) is eliminated
- Changes to data values are always consistent (because there is no duplication!)
    - Update Anomaly Fixed ✅
- Unintended removal of unrelated data is prevented
    - Deletion Anomaly Fixed ✅
- New data is always able to be added without inappropriately depending on other data
    - Insertion Anomaly Fixed ✅

## Further benefits of Normalisation
- **Storage space** on disk is reduced
- **Ordering** can be added to the data with `indexing` to speed up searching and access
- Data is **grouped together logically** in related tables, in a way that is easy for humans to understand and write code for

Notes: Indexing is a way of performing quick and efficient sorting on a given field in our data, without having to read all database records when searching.

Index data for a field (or multiple fields) is held in a separate data structure in the database and pre-sorted ahead of time, so that fast lookups can be performed on it (Binary search)


## The Normalisation Process

- Starting from an Unnormalised data set (UNF) we can proceed through each `normal form` applying rules at each stage until we reach Third Normal Form (3NF).

![[Pasted image 20240606113525.png]]

- If data already meets the rules for a given normal form, we may not need to do anything and can simply move to the next form!

Notes: Experienced designers may model data directly in 3NF, however we will work through each of the forms in turn.

### Rules for First Normal Form (1NF)

For a table to be in 1NF then:

1. **Unique name for attributes/columns**: Each column should have a unique name
2. **Order doesn't matter**: The order in which columns or rows appear should not affect the data
3. **Attribute Domain should not change**: Values stored in a column must represent the same sort of information for all rows/records
4. **Single Valued Attributes**: Each column in the table should hold a single value. (Formal term is to be `atomic`)

Notes: Examples with images are given for rules 3 and 4 in following slides.

### Applying 1NF

1. **Unique name for attributes/columns**
2. **Data order doesn't matter**

These requirements are usually trivial and we won't need to think about them much.

- The database software will prevent us from creating any tables that have duplicate column names.
- The database software will also always allow columns to be in any order or for rows to be retrieved based on queries, no matter the order those rows actually appear.

Let's move on to the next requirements.


3. **Attribute Domain should not change**: Values stored in a column must represent the same sort of information for all rows/records

![[Pasted image 20240606115153.png]]

Is the rule violated?

Violated because enrolled column holds both a date of student enrolment in the course, and also (presumably!) a reason why they were not able to enrol - that the column can't accurately describe what the data actually represents is a big part of the problem - we need to infer it from the value!

**Violation:** Mixed information for enrolled column <br>

![[Pasted image 20240606115205.png]]

What's the solution?

Notes: Specific purpose columns allow columns to be named ambiguously so we can tell what they are for

Data type for each column is now consistent. Where there is no data for a given column, it will be null-valued.

**Violation:** Mixed information for enrolled column

![[Pasted image 20240606115222.png]]<br>

**Solution:** Separate columns for separate purposes

![[Pasted image 20240606115233.png]]

Notes: Specific purpose columns allow columns to be named ambiguously so we can tell what they are for

Data type for each column is now consistent. Where there is no data for a given column, it will be null-valued.

**Violation:** Module column stores multiple modules


4. **Single Valued Attributes**: Each column in the table should hold a single value.

![[Pasted image 20240606115351.png]]

Violated because modules the students are taking for a given course are held as multi-value attributes

![[Pasted image 20240606115417.png]]

**Violation:** Module column stores multiple modules

**Solution:** Duplicate other row data to allow single value for module

![[Pasted image 20240606115454.png]]

Notes: In this case our composite key has now become THREE items (student_number, course, module) to allow us to uniquely reference a single row.

Applying 1NF has increased the `redundancy` (bad!) but decreased the `complexity` and made the data more structured and easier to work with.

After the violations are fixed we have a lot more data repetition, which is not great, but we've got rid of the violations!

