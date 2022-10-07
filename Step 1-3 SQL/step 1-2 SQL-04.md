# Welcome to the Final Showdown !

You made it so far !

*Welcome to SQL-04*

Congratulations, you have gone through all the theoretical concepts and also many real-world examples with SQL-based queires so far and you have already become really apt in SQL !

<br>

***

<br>

## What is next ?

Even though now you are armed with advance knowledge about the inner workings of SQL based ecosystems and the language itself, as like everything in programming there is always new learnings you can pick up from practice and real-world implementations !

As a SQL programmer the best practice for you is to keep adding on new skills and logics and also new commands and functionalities to your SQL toolbelt !

So let us go through another problem and learn one final SQL command but being a programmer you must cultivate the habit of always being on the prowl for new commands and queries !

We must **write a query to get the current date in the following format.** Sounds simple right?

***Well it is!***

The SQL command for this query will look like : 

                                              SELECT curdate() 
                                              AS 'Current_date'; 
                                        
And it will look like the following picture in your Workbench:

![img](https://user-images.githubusercontent.com/67789350/88427659-feed8900-ce10-11ea-9c46-1fc069ad1eed.png)

As you notice the format of the output follows `YYYY-MM-DD` this is the default output of the **CURDATE()** , but let us assume we require the output to be the `Month DD,YYYY` 

To get this done, we make use of another function which compliments *CURDATE()*, which is the **DATE_FORMAT()** function 
                                   
The syntax to use DATE_FORMAT() goes like :

                                            DATA_FORMAT(date,format)
                                           
In our case the data is provided by the *CURDATE()* and the format can be provided like :

| Format | Description                                   |
|--------|-----------------------------------------------|
|   %a   | Abbreviated weekday name (Sun to Sat)         |
|   %c   | Numeric month name (0 to 12)                  |
|   %e   | Day of the month as a numeric value (0 to 31) |
|   %H   | Hour (00 to 23)                               |
|   %M   | Month name in full (January to December)      |

These are some example format types, to see the other format types please visit [here](https://www.w3schools.com/sql/func_mysql_date_format.asp) to see all possible formats available to you 

**BUT** for our required format, we are going to use `'%M %e, %Y'` 

So the SQL command would look like :

                                          SELECT DATE_FORMAT(CURDATE(),'%M %e, %Y') 
                                          AS 'Current_date';
                                          
The output to this query looks like :

![img](https://user-images.githubusercontent.com/67789350/88430433-11b68c80-ce16-11ea-85ed-47eb1854079c.png)

<br>

***

<br>

## Section V : Date/Time

1. **Write a query to extract the year from the current date.**
2. **Write a query to get the first name and hire date from employees table where hire date between '1987-06-01' and '1987-07-30'.**

<br>

***

<br>

## And that is a wrap up!

Congratualations ! 🎉🎉

You have successfully completed our strenuous courseware and came out victorious ! 

You have really come a long way from **SELECT** to **GROUP BY** and proficiencies in SQL is a major add on to your capabilities as programmer !

Before you move onto the next topics, do checkout how to connect SQL to your python! <br>
with [SQL - 05](https://github.com/Tech-i-s/data-science-course-wiki/blob/master/common/step%201-2%20(SQL)/step%201-2%20SQL-05.ipynb)

I wish you luck in your further learnings and wish you luck for your [Step 1-3](https://github.com/Tech-i-s/data-science-course-wiki/tree/ghaiyur-dev/common/step%201-3%20(NumPy))

