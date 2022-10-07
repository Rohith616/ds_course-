# Getting serious with SQL !

Welcome to SQL-03 !

In this tutorial we will encounter more advance commands and navigate through the SQL language 

<br>

***

<br>

## You made it !

Congratulations on making to this section !

We will be working with more advanced concepts in SQL

To get started, let us try to **write a query to get the number of employees with the same job**

Alright, so the problem requires us to get the COUNT of all employees and the GROUP them according their job, now I know the employee table has a job_id column , so we going to use that column to GROUP our employees together.

So my SQL command should look something like 

                                              SELECT job_id, COUNT(*)
                                              FROM employees
                                              GROUP BY job_id;


![img](https://user-images.githubusercontent.com/67789350/88322300-26bfec80-cd3e-11ea-8aa3-3e768f45af52.png)


## Did you get it?

So that is an successful implementation of **GROUP BY** in SQL !

So **GROUP BY** is a command that helps you perform aggregations and other complex filters to have greater control over your database ! 

Now let us do a few more challenges with **GROUP BY**:

<br>

## Section III : GROUP BY

1. **Write a query to find the manager ID and the salary of the lowest-paid employee for that manager.**
2. **Write a query to get the average salary for each job ID excluding programmer.**
3. **Write a query to get the total salary, maximum, minimum, average salary of employees (job ID wise), for department ID 90 only.**
4. **Write a query to get the job ID and maximum salary of the employees where maximum salary is greater than or equal to $4000.**
5. **Write a query to get the average salary for all departments employing more than 10 employees.**

<br>

***

<br>

## Let's use more than one Table!

So far we have been using only one table for our queries, but what if we use more than one? 🤔

Let us create a question taht requires us to query from two tables in the same query **to find the addresses (location_id, street_address, city, state_province, country_name) of all the departments.**

So in our case,`location_id, street_address, city, state_province` are in the `locations` table <br>
Where as `country_name` is a column in the `countries` table 

So the SQL query would be :

                           SELECT location_id, street_address, city, state_province, country_name
                           FROM locations
                           JOIN countries;
                           
So here we use a new command called **JOIN** 

**JOIN** clause is used to combine records from two or more tables in a database. A **JOIN** is a means for combining fields from two tables by using values common to each.

![img](https://user-images.githubusercontent.com/67789350/88347059-71a22a00-cd67-11ea-9dcc-bc096e4592ba.png)

Let's see how you fare in this challenge !

## Section IV : JOINS

1. **Write a query to find the name (first_name, last name), department ID and name of all the employees.**
2. **Write a query to find the name (first_name, last_name), job, department ID and name of the employees who works in London.**
4. **Write a query to get the department name and number of employees in the department**

See you in the final [SQL-04](https://github.com/Tech-i-s/data-science-course-wiki/blob/ghaiyur-dev/common/step%201-2%20(SQL)/step%201-2%20SQL-04.md)!
