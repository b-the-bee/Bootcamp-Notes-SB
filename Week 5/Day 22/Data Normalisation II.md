#databases #data-engineering #data-science 
## Rules for Second Normal Form (2NF)

For a table to be in 2NF then:

1. The table should already be in `1NF`
2. The table should have **no** `Partial Dependency`

(For simplicity, we will no longer considering course 'modules' in our example table)

#### Dependency

- Let's understand `Dependency` before discussing `Partial Dependency`
- Now that `modules` have been removed, `student_number` and `course` are the columns which allow us to uniquely identify a row. These together are the table's `composite key`

![[Pasted image 20240606133318.png]]

Notes: Remind learners that either student number by itself or course by itself are not sufficient to identify a record.

Same student takes more than one course, and same course is taken by multiple students so we need both.

#### Dependency

Table properties are `dependent` on the **whole key** if they need **all parts** of the key to be determined.

![[Pasted image 20240606133348.png]]

- `enroll_date` is the date when a particular student enrolled on a particular course. It does not relate only to the course or the student, but to **both**
- `enroll_date` is therefore `dependent` on the **whole key**

Notes: The same is true for deferred_reason.

deferred_reason is a reason for a particular student not to start on a particular course


#### Partial Dependency

Table properties are `Partially Dependent` when they relate only to **part** of the key.

![[Pasted image 20240606133625.png]]

- A course always has the same instructor
- This means `course_instructor` and `instructor_email` can be determined by `course` **only**, and do not need `student_number` at all
- These properties are `partially dependent`

Notes: There is another partial dependency in this table which the learners may spot, but we aren't covering it now (student name depends only on student number, not course)

#### Applying 2NF

**Violation:** Instructor information is `Partially Dependent` on `course` <br><br>

**Solution:** Split things that depend on `course` out to a new table 👌

![[Pasted image 20240606133800.png]]

- We will give the new course table a unique number-based `course_id` at the same time, to avoid duplicating the course name between tables
- Records in the student table can refer to the new course table using the `course_id` as a `foreign key`

Notes:

The columns in the new table are now wholly dependent on the `course_id` primary key.

Highlight that by adding a numeric ID for courses, it allows us to be able to update a course name in only 1 location if needed, rather than in every row in the student table. Also, IDs are far less likely to change than a name might.


## Third Normal Form

For a table to be in 3NF, then:

1. The table should already be in `2NF`
2. There should be **no** `Transitive Dependency`

#### Transitive Dependency

- A non-key column in a table has `Transitive Dependency` if it depends on some other non-key column, rather than depending on the key.
- **Reminder:** A column 'A' is dependent on another column 'B' if when the value of B changes, A should change too.

!![[Pasted image 20240606141635.png]]

Given `course_id` is the table key, does the new Course table have any transitive dependency?

Notes: Go through the properties one by one if the learners are not sure what each depends on. Course name and instructor depend on course_id (which is a sort of proxy for name) but instructor email does not.

Instructor email is dependant more closely on the instructor, rather than directly on the course_id. If the instructor changes to a different person, the email would need to change too.

#### Applying 3NF

If the instructor for a course changes to a new person, then the instructor email is also going to need to change.

![[Pasted image 20240606141852.png]]

- This shows that `instructor_email` depends on `course_instructor` and **not** on the key `course_id`
- `instructor_email` is therefore `Transitively Dependent`

**Violation:** `instructor_email` is `Transitively Dependent` on `course_instructor` <br><br>

**Solution:** Split things that depend on `course_instructor` out to a new table 👌

![[Pasted image 20240606142411.png]]

We will also assign a new `instructor_id` numeric identifier. Records in the course table can refer to the instructor by this ID.

Notes: The use of a numeric identifier is again to prevent data redundancy across tables. Even if the same instructor changes name (e.g. gets married, other legal name change) then we only need to update one place in the database, even if the instructor is assigned to many courses.

What can we learn about **Good Normalisation** from the final design?

- Columns all store the **same sort of data**, with **single values** per field
- Related data is grouped together in a table **named after the entity** it belongs to (instructor, course, student, enrolment)
- Data in each table **depends only on that table's key**, not on any other data in the table
- When one table links to another, it's good practice to link it with **IDs** instead of using data that might change, such as names
  

Each course has just one instructor assigned to it, but each instructor can teach many courses. This is a one-to-many relationship.

## Pros
- Querying for **individual** data records can be faster as we benefit from multiple smaller tables with well-designed indexes
- Better and more logical database organisation makes it easier to build new functionality to the application
- Reduces redundant data
- Improves data consistency
- The database design itself enforces good data, and prevents inconsistencies, or `orphans`

For **Transactional** workloads like a shopping cart or a booking system where data INTEGRITY is critical, normalisation is a great choice.

## Cons
- Processing **all** data as a batch can be slower, due to the need to join between tables
- Table joins are needed on reading data which increases complexity of query operations
- Overly normalised data can be difficult to correctly join and put together without domain knowledge of its layout

For **Analytical** workloads like bulk data processing where SPEED is critical, allowing some amount of denormalisation may sometimes be preferred!