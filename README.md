# RDBMS_ASSIGNMENT
THIS IS MY RDBMS ASSIGNMENT.



### QUESTION 1 :- Create a database named employee, then import data_science_team.csv , proj_table.csv  and emp_record_table.csv into the employee database from the given resources.
               
     -- Creating database named RDBMS_ASSIGNMENT USING THIS COMMAND        
     CREATE DATABASE RDBMS_ASSIGNMENT;
     -- Command for using this 
     USE RDBMS_ASSIGNMENT;
                            
     After this, I imported data_science_team.csv, proj_table.csv and emp_record_table.csv into the  RDBMS_ASSIGNMENT database 
     from the given resources using MySQLWorkbench.
     
     
### QUESTION 2 :- Create an ER diagram for the given employee database.

![image](https://user-images.githubusercontent.com/122514232/220903026-764e8d33-ac44-4ef0-b265-07e39587068c.png)


### QUESTION 3 :- Write a query to fetch EMP_ID, FIRST_NAME, LAST_NAME, GENDER, and DEPARTMENT from the employee record table, and make a list of employees and details of their department. 

###  QUERY:
SELECT EMP_ID, FIRST_NAME,LAST_NAME,GENDER,DEPT 
FROM emp_record_table;


<img width="323" alt="Screenshot 2023-02-23 at 4 28 03 PM" src="https://user-images.githubusercontent.com/122514232/220904679-802fa81a-8f85-4a51-a95b-29824e419fe0.png">


### QUESTION 4 :-  Write a query to fetch EMP_ID, FIRST_NAME, LAST_NAME, GENDER,DEPARTMENT, and EMP_RATING if the EMP_RATING is:
###                (a) less than two
###                (b) greater than four
###                (c) between two and four 

###         QUERY (a):
             SELECT EMP_ID, FIRST_NAME,LAST_NAME,GENDER,DEPT ,EMP_RATING
 			       FROM emp_record_table
   			     WHERE EMP_RATING<2;
             
<img width="455" alt="Screenshot 2023-02-23 at 6 05 02 PM" src="https://user-images.githubusercontent.com/122514232/220907302-612e7e2a-e671-45a9-962b-a021e0180b3d.png">

###         QUERY (b):
               SELECT EMP_ID, FIRST_NAME,LAST_NAME,GENDER,DEPT ,EMP_RATING
               FROM emp_record_table
               WHERE EMP_RATING>4;

             
             
<img width="455" alt="Screenshot 2023-02-23 at 6 06 22 PM" src="https://user-images.githubusercontent.com/122514232/220907654-75411edc-234c-4541-b01b-7f038678056a.png">

###         QUERY (c):
                 
                   SELECT EMP_ID, FIRST_NAME,LAST_NAME,GENDER,DEPT ,EMP_RATING
                   FROM emp_record_table
                   WHERE EMP_RATING BETWEEN 2 AND 4;


            
            
            
<img width="453" alt="Screenshot 2023-02-23 at 6 08 55 PM" src="https://user-images.githubusercontent.com/122514232/220908314-ea1acdc2-52e4-4ea6-a496-219e34dbf42a.png">


###   QUESTION 5 :- Write a query to concatenate the FIRST_NAME and the LAST_NAME of employees in the  Finance department from the employee table and then                     give the resultant column alias as NAME.


###   QUERY:

             SELECT CONCAT(FIRST_NAME,' ',LAST_NAME) AS NAME 
             FROM emp_record_table
             WHERE DEPT='FINANCE';
             
<img width="186" alt="Screenshot 2023-02-23 at 6 19 31 PM" src="https://user-images.githubusercontent.com/122514232/220911232-1393a1ba-4449-496e-9c73-5cf02873ae5c.png">


###   QUESTION 6 :- Write a query to list only those employees who have someone reporting to them. Also, show the number of reporters (including the President).

###   QUERY:

                SELECT  M.EMP_ID , M.FIRST_NAME ,M.LAST_NAME , COUNT(*) AS CNT
                FROM emp_record_table  E INNER JOIN emp_record_table M
                ON E.MANAGER_ID=M.EMP_ID 
                GROUP BY M.EMP_ID;
                
<img width="268" alt="Screenshot 2023-02-23 at 6 22 44 PM" src="https://user-images.githubusercontent.com/122514232/220911855-89d0857c-41fd-4735-805a-65af4239e524.png">
          

###   QUESTION 7 :- Write a query to list down all the employees from the healthcare and finance departments  using union. Take data from the employee record table. 

###   QUERY:


             SELECT * 
             FROM emp_record_table 
             WHERE DEPT='HEALTHCARE'
             UNION
             SELECT * 
             FROM emp_record_table 
             WHERE DEPT ='FINANCE';




<img width="992" alt="Screenshot 2023-02-23 at 6 26 52 PM" src="https://user-images.githubusercontent.com/122514232/220912732-4b874b4d-50a5-49bf-bb27-1c3e17fbfa53.png">


###   QUESTION 8 :- Write a query to list down employee details such as EMP_ID, FIRST_NAME, LAST_NAME,ROLE, DEPARTMENT, and EMP_RATING grouped by dept. 
###                 Also include the respective  employee rating along with the max emp rating for the department. 

###         QUERY:

                 SELECT EMP_ID,FIRST_NAME,LAST_NAME,ROLE,DEPT,EMP_RATING,
                 MAX(EMP_RATING)  OVER(PARTITION BY DEPT) AS MAX_RATING_BY_DEPT
                 FROM emp_record_table;

<img width="695" alt="Screenshot 2023-02-23 at 6 32 54 PM" src="https://user-images.githubusercontent.com/122514232/220914067-55baae33-3471-446e-8d01-84c44c5d8cb6.png">


###  QUESTION 9 :- Write a query to calculate the minimum and the maximum salary of the employees in each role. Take data from the employee record table. 

###        QUERY:     
                       SELECT DISTINCT ROLE, MAX(SALARY) OVER(PARTITION BY ROLE) AS 
                       MAX_SALARY ,MIN(SALARY)    OVER(PARTITION BY ROLE) 
                       AS MIN_SALARY  FROM emp_record_table;

<img width="336" alt="Screenshot 2023-02-23 at 6 35 45 PM" src="https://user-images.githubusercontent.com/122514232/220914706-67ccbd36-dcbb-4572-943f-ae26f252435d.png">


###   QUESTION 10 :- Write a query to assign ranks to each employee based on their experience.Take data from the employee record table. 

###       QUERY:
               SELECT EMP_ID ,EXP, DENSE_RANK() OVER(ORDER BY EXP DESC) AS RANK_BY_EXP
               FROM emp_record_table ;
               
<img width="465" alt="Screenshot 2023-02-23 at 6 41 48 PM" src="https://user-images.githubusercontent.com/122514232/220916008-07bd446d-30be-4ba1-93bb-7bcb2502a238.png">




###  QUESTION 11 :- Write a query to create a view that displays employees in various countries whose salary is more than six thousand. Take data from    the employee record table. 


 ###         QUERY:

                  CREATE OR REPLACE VIEW SALAR_GREATER_THEN_SIX_THOUSAND AS
                  SELECT EMP_ID,COUNTRY,SALARY FROM emp_record_table 
                  WHERE SALARY>6000;

                  SELECT * FROM SALAR_GREATER_THEN_SIX_THOUSAND;
                  
<img width="405" alt="Screenshot 2023-02-23 at 6 45 40 PM" src="https://user-images.githubusercontent.com/122514232/220917223-ceb89f47-5d19-43ef-a478-24b081418988.png">



###   QUESTION 12 :- Write a nested query to find employees with experience of more than ten years. Take data  from the employee record table. 
 

###                QUERY:

                        SELECT * 
                        FROM emp_record_table
                        WHERE EXP IN (SELECT EXP FROM emp_record_table WHERE EXP>10);
                        
<img width="1152" alt="Screenshot 2023-02-23 at 6 47 45 PM" src="https://user-images.githubusercontent.com/122514232/220917565-2e98762d-ce08-41dd-bdaf-4aa5e6422f52.png">



###   QUESTION 13 :- Write a query to create a stored procedure to retrieve the details of the employees whose  experience is more than three years. Take                       data from the employee record table. 

###    QUERY:

                    DELIMITER $$
                    CREATE PROCEDURE Solve()
                    BEGIN
                    SELECT * 
                    FROM emp_record_table
                    WHERE EXP>3;
                    END
                    $$ DELIMITER ;

                    CALL Solve();
                    
<img width="1152" alt="Screenshot 2023-02-23 at 6 49 50 PM" src="https://user-images.githubusercontent.com/122514232/220918358-7a1f9be8-e0a3-4b4a-88dc-bdde137c55cc.png">


       
       
###      QUESTION 14:- Write a query using stored functions in the project table to check whether the Job profile  assigned to each employee in the data                          science team matches the 
###                         organization’s set  standard.
###                         The standard being:
###                         For an employee with experience less than or equal to 
###                         2 years assign 'JUNIOR DATA SCIENTIST',
###                         For an employee with the experience of 2 to 5 years assign 
###                         'ASSOCIATE DATA  SCIENTIST', 
###                         For an employee with the experience of 5 to 10 years assign 
###                         'SENIOR DATA SCIENTIST',
###                         For an employee with the experience of 10 to 12 years assign 
###                         'LEAD DATA SCIENTIST',
###                          For an employee with the experience of 12 to 16 years assign
###                          'MANAGER'. 

###      QUERY: 


                    DELIMITER $$  
                    CREATE FUNCTION SCIENTIST_EXP2()  
                    RETURNS TINYINT(1)  
                    DETERMINISTIC  
                    BEGIN  
                    DECLARE RES INT DEFAULT 1;  
                    DECLARE RL VARCHAR(30);  
                    DECLARE SETEND INTEGER DEFAULT 0;  
                    DECLARE EP INT;  
                    DECLARE CURNAME CURSOR FOR  
                    SELECT ROLE,EXP FROM emp_record_table;  
                    DECLARE CONTINUE HANDLER FOR NOT FOUND   
                    SET SETEND=1;  

                   OPEN CURNAME;  
                   MY_LOOP:LOOP  
                   FETCH CURNAME INTO RL,EP;  
                   IF SETEND=1 THEN  
                   LEAVE MY_LOOP;  
                   END IF;  

                   IF(RL='JUNIOR DATA SCIENTIST' AND EP>2) THEN  
                   SET RES=0;  
                   LEAVE MY_LOOP;  
                   ELSEIF(RL='ASSOCIATE DATA SCIENTIST' AND (EP<=2 OR EP>5)) THEN  
                   SET RES=0;  
                   LEAVE MY_LOOP;  
                   ELSEIF(RL='SENIOR DATA SCIENTIST' AND (EP<=5 OR EP>10)) THEN  
                   SET RES=0;  
                   LEAVE MY_LOOP;  
                   ELSEIF(RL='LEAD DATA SCIENTIST' AND (EP<=10 OR EP>12)) THEN  
                   SET RES=0;  
                   LEAVE MY_LOOP;  
                   ELSEIF(RL='MANAGER' AND (EP<=12 OR EP>16)) THEN  
                   SET RES=0;  
                   LEAVE MY_LOOP;  
                   END IF;  
                   END LOOP MY_LOOP;  
                   CLOSE CURNAME;  
                   IF(RES=1) THEN  
                   RETURN TRUE;  
                   ELSE  
                   RETURN FALSE;  
                   END IF;  
                   END 
                   $$  
                   DELIMITER ;  




                   DELIMITER $$
                   CREATE PROCEDURE Helper_Procedure()
                   BEGIN
                  IF SCIENTIST_EXP2() THEN
                  SELECT 'THE PROFILE ASSIGNED TO EACH EMPLOYEE IN THE DATA SCIENCE
                  TEAM MATCHES THE ORGANIZATION SET STANDARD.' AS MESSAGE;
                  ELSE
                 SELECT 'THE PROFILE ASSIGNED TO EACH EMPLOYEE IN THE DATA SCIENCE 
                 TEAM DOES NOT MATCH THE ORGANIZATION SET STANDARD.' AS MESSAGE;     
                  END IF;
                  END $$
                  DELIMITER ;

                 CALL Helper_Procedure();

<img width="832" alt="Screenshot 2023-02-23 at 6 55 31 PM" src="https://user-images.githubusercontent.com/122514232/220919675-33890104-895f-4d86-9244-0511f784ae56.png">




   ###   QUESTION 15 :- Create an index to improve the cost and performance of the query to find the employee whose FIRST_NAME is ‘Eric’ in the employee                          table after checking the execution plan.
  
    
 ###                   QUERY:
                                      CREATE INDEX Eric_Index 
                                      ON emp_record_table(FIRST_NAME);

                                      SELECT FIRST_NAME 
                                      FROM emp_record_table 
                                      WHERE FIRST_NAME='Eric';
 
 <img width="323" alt="Screenshot 2023-02-23 at 7 00 02 PM" src="https://user-images.githubusercontent.com/122514232/220920698-fde2d67f-925d-4a77-92d0-3d7d48f52492.png">

<img width="1137" alt="Screenshot 2023-02-23 at 7 00 58 PM" src="https://user-images.githubusercontent.com/122514232/220921019-b3ecb4ac-8940-4e5f-adfd-ae5943b0afcc.png">



###     QUESTION 16 :-Write a query to calculate the bonus for all the employees,based on their ratings and salaries 
###     (Use the formula: 5% of salary * employee rating). 

 ###    QUERY:

                   SELECT EMP_ID,SALARY,EMP_RATING, (SALARY*0.05*EMP_RATING)   
                   AS BONUS FROM emp_record_table ; 
                   
<img width="346" alt="Screenshot 2023-02-23 at 7 07 12 PM" src="https://user-images.githubusercontent.com/122514232/220922642-c92869ab-f36b-4282-856c-096c39a9f370.png">


###  QUESTION 17 :- Write a query to calculate the average salary distribution based on the continent and country.Take data from the employee record table.



 ###        QUERY:
                                       SELECT DISTINCT CONTINENT,COUNTRY , 
                                       AVG(SALARY) OVER(PARTITION BY CONTINENT) AS     
                                       AVG_SALARY_BY_CONTINENT,
                                       AVG(SALARY) OVER(PARTITION BY COUNTRY) AS   
                                       AVG_SALARY_BY_COUNTRY
                                       FROM emp_record_table;
                                       
                                       
                                       
<img width="600" alt="Screenshot 2023-02-23 at 7 10 10 PM" src="https://user-images.githubusercontent.com/122514232/220923640-701ea0e6-50f0-4326-9dd2-0a088dc9e1e0.png">
                                

             



      



                       
                       
                       






     
     
                           



