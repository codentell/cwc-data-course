+++
title = "06. Data Relationship 👩‍🎓👨‍🎓"
weight = 6
tags = ["sql"] 
+++

In this activity, you will design a database model.

You are the database consultant at a new university. Your job is to design a database model for the registrar. The database will keep track of information on students, courses offered by the university, and the courses each student has taken.

## Instructions

* Create a `students` table that keeps track of the following:

  * Unique ID number of each student

  * Last and first names of each student

* Create a `courses` table that keeps track of the following:

  * Unique ID number of each course

  * Name of each course

* Create a `student_courses_junction` that keeps track of the following:

  * All courses that have been taken by each student

  * Term in which a course was taken by a student (spring or fall)

* Which data model is appropriate here: one to one, one to many, or many to many?

## Bonus

If time allows, join and query the tables to get all data on the students.

---


## ✅ Solutions
{{%expand "Solutions Click Here" %}}
```sql
-- Create a table of students
CREATE TABLE students (
  id SERIAL PRIMARY KEY,
  last_name VARCHAR NOT NULL,
  first_name VARCHAR NOT NULL
);

-- Create a table of courses
CREATE TABLE courses (
  id INTEGER NOT NULL PRIMARY KEY,
  course_name VARCHAR NOT NULL
);

-- Create a junction table.
CREATE TABLE student_courses_junction (
  student_id INTEGER NOT NULL,
  FOREIGN KEY (student_id) REFERENCES students(id),
  course_id INTEGER NOT NULL,
  FOREIGN KEY (course_id) REFERENCES courses(id),
  course_term VARCHAR NOT NULL,
  PRIMARY KEY (student_id, course_id)
);

-- Insert Data into table
INSERT INTO students (id, last_name, first_name)
VALUES
  (1, 'Skywalker', 'Luke'),
  (2, 'Skywalker', 'Leia'),
  (3, 'Solo', 'Han');

INSERT INTO courses (id, course_name)
VALUES
  (3201, 'Data modeling'),
  (3202, 'Data visualization'),
  (12101, 'Force utilization');

INSERT INTO student_courses_junction (student_id, course_id, course_term)
VALUES
  (1,12101, 'Spring'),
  (1,3201, 'Fall'),
  (1,3202, 'Fall'),
  (2,12101, 'Fall'),
  (2,3202, 'Spring'),
  (3,3201, 'Spring'),
  (3,3202, 'Fall');

  -- Query Tables
SELECT * FROM students;

SELECT * FROM courses;

SELECT * FROM student_courses_junction;

-- A join statement to query all courses taken by students
SELECT s.id, s.last_name, s.first_name, c.id, c.course_name, j.course_term
FROM students s
LEFT JOIN student_courses_junction j
ON s.id = j.student_id
LEFT JOIN courses c
ON c.id = j.course_id;

```
{{% /expand%}}


