# Making SQL Work !

In this section we are going to visit some intermediate concepts in SQL

<br>

## Things that you know now !

You know how to **SELECT** : `select * from your_database;`

And take data out from multiple tables and then do special conditional queries and so much more!

But the only way to remember so many important concepts is to keep practicing !

For future references you can always refer to this [cheatsheet](https://www.sqltutorial.org/sql-cheat-sheet/)

![image](https://user-images.githubusercontent.com/67789350/88316225-16574400-cd35-11ea-8cbc-0050fa510a51.png)


***


## Let’s get our very own database!

Now that you are done with your basics, let us use the Workbench we set up in your machine!

**Step 1** : Download your SQL data dump from [CLOUD](https://drive.google.com/file/d/1qY-gIWEQxN6pkZzyBuVDOQmIpd7-mzvj/view?usp=sharing) (HR data)

**Step 2** : Once you have your `hr.sql` , open your Workbench and run the SQL script in it 

**Step 3** : And that's it! You have set up a ‘hrdata’ database in your local MySQL server


***


## Let’s try it out 

After you are done uploading the HR data into your database `hrdata` , let us try to query it from Workbench 

You will notice in your SQL command we have **comments** which are invoked by calling in `--` followed by content you want your SQL system not to run 

Try the query 

		 use hrdata; -- use <database>; is always a good first command
		 select * from hrdata.employees;

You should get something similar to the picture

![image](https://user-images.githubusercontent.com/67789350/88316859-0db33d80-cd36-11ea-86f8-2f67045943a2.png)


***


## What other tables do I have ?

So we know in our hrdata Database we have a table called `employees` , but what other tables do we have?

You can use the command : 

  `show tables;`
  
A more in-dept structure of the database can be understood from the diagram

![img](https://user-images.githubusercontent.com/67789350/88317018-4bb06180-cd36-11ea-8399-7d094b68b4bd.png)


***


## Welcome to our new playground!

Now that we have this database let's try to do some queries !

The first task I have for you is **write a query to display the names (first_name, last_name) using alias name "First Name", "Last Name".**

Now, I will accompany you to find the solution to this task, 

Alright, so the question wants us to get the first name and last name and in the output we want to give our query output some **nickname or alias**

I know the last name and first name are columns that are available in the `employee` table !

So my SQL command should be :

			SELECT first_name "First Name",  last_name "Last Name" FROM employees;
			
The words in the quotes become the column names of your query output !

![img](https://user-images.githubusercontent.com/67789350/88317429-dee99700-cd36-11ea-9f56-f0ef0e93aeae.png)


***


## More exercises !

Now that you have had your first taste of SQL programming , I have some more queries for you! 

You can always refer to the SQLBolt material and the cheatsheet given to you while you go through these challenges.

If you ever feel a challenge is too much for you , a tutor is a just a [Slack](http://techistalk.slack.com) message away !

Will meet you at the end of next section  !


***


## Section I Novice: Basic Select Statements

1. Write a query to get unique department ID from employee table
2. Write a query to get all employee details from the employee table order by first name, descending
3. Write a query to get the names (first_name, last_name), salary, PF of all the employees (PF is calculated as 15% of salary)
4. Write a query to get the employee ID, names (first_name, last_name), salary in ascending order of salary
5. Write a query to get the total salaries payable to employees
6. Write a query to get the maximum and minimum salary from employees table
7. Write a query to get the average salary and number of employees in the employees table
8. Write a query to get the number of employees working with the company

### Optional Expert Questions !!

9x. Write a query to get the number of jobs available in the employees table <br>
10x. Write a query get all first name from employees table in upper case <br>


***


## Congratulations! 

You have successfully completed your first SQL exercises all on your own!

It will only get more fun and interesting from here, now that we have mastered the `SELECT` command

Let us try to explore a bit more intermediate commands that we can make SQL run and get jobs done for us !

Let me get you started with another problem, we have to **write a query to display the names (first_name, last_name) and salary for all employees whose salary is not in the range $10,000 and $15,000.**

Now, as we read the question we find that we got to print our last name and first name as before, but there is a condition added that last name and first name should only be of the employees whose salary is **NOT** in range of 10000 and 15000, so for everything conditional in SQL , we use `WHERE` clause 

So my SQL command should be :

			SELECT first_name, last_name, salary
			FROM employees
			WHERE salary NOT BETWEEN 10000 AND 15000;
			
So here you can see, I use the `WHERE` clause to only target my selects if they satisfy the condition !

![img](https://user-images.githubusercontent.com/67789350/88317952-a39b9800-cd37-11ea-83d7-8288f6748ecf.png)


***


## Section II Intermediate:Restricting and Sorting data

1. Write a query to display the name (first_name, last_name) and department ID of all employees in departments 30 or 100 in ascending order.
2. Write a query to display the name (first_name, last_name) and salary for all employees whose salary is not in the range $10,000 through $15,000 and are in department 30 or 100
3. Write a query to display the name (first_name, last_name) and hire date for all employees who were hired in 1987
4. Write a query to display the first_name of all employees who have both "b" and "c" in their first name
5. Write a query to display the last name, job, and salary for all employees whose job is that of a Programmer or a Shipping Clerk, and whose salary is not equal to $4,500, $10,000, or $15,000
6. Write a query to display the last name of employees whose names have exactly 6 characters
7. Write a query to display the last name of employees having 'e' as the third character
8. Write a query to display the jobs/designations available in the employees table

### Optional Expert Questions !!

9x. Write a query to display the name (first_name, last_name), salary and PF (15% of salary) of all employees <br>
10x. Write a query to select all record from employees where last name in 'BLAKE', 'SCOTT', 'KING' and 'FORD' <br>


***


## One step closer to Mastering SQL !

Congratulations for finishing another section of ***SQL challenges !***
                           
What you just finished is considered quite an advance level of SQL implementation, most databases require you to create complex queries such as these to extract meaningful data to be worked upon by various departments and team members who create further solutions on these outputs !

We have come very far since starting our SQL adventure already  

In the next section we are going to make use of more inbuilt SQL commands to accomplish more advanced implementations!

See you in [SQL-3](https://github.com/Tech-i-s/data-science-course-wiki/blob/ghaiyur-dev/common/step%201-2%20(SQL)/step%201-2%20SQL-03.md) 
