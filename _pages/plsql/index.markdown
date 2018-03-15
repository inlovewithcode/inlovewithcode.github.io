---
author: guidedmissile
comments: true
date: 2014-11-18 05:35:26+00:00
layout: page
link: https://inlovewithcode.wordpress.com/plsql/
slug: plsql
title: PL SQL
wordpress_id: 248
---

http://bobby-tables.com/img/xkcd.png


#### PL/SQL


Simply SQL mean - Structural Query Language ; PL is an extension to Sql, for making it as Programming Language Sql. PL/SQL combines the data-manipulating power of SQL with the processing power of procedural languages.


#### Variables


NAME is same as name and Name. The size of an identifier cannot exceed 30 characters. Identifiers should be descriptive. When possible, avoid obscure names such as cpm. Instead, use meaningful names such as cost_per_thousand.



	
  * %ROWTYPE and %TYPE - special data structures are provided by Oracle;

	
  * %TYPE has two advantages. First, you need not know the exact datatype of the table columns. Second, if you change the database definition of columns, such as employee_id or last_name. The data types of empid and emplname in Example: Using %TYPE With Table Columns change accordingly at run time.


Assignment operator (:=), a colon followed by an equal to sign.

Examples:

    
    country := 'France'; -- single quotes !!
    country := UPPER('Canada');
    valid_id := TRUE; -- boolean
    done := (counter > 100); -- boolean
    deviation := -9.5e-3;


Boolean Values- can be one of TRUE, FALSE, and NULL.

Usage:

    
    active_employee BOOLEAN NOT NULL := TRUE; -- value cannot be NULL
    monthly_salary NUMBER(6) NOT NULL := 2000; -- value cannot be NULL


**Datetime** literals have various formats depending on the datetime data types like '4-Mar-2012 10:26 AM' or '4-Mar-2012'


#### PL/Sql body structure



    
    Declare
    -- here define variables require + at the end of each var a semicolon(;)
    Begin
    NULL; -- NULL statement does nothing, allows this block to executed and tested
    End; -- semicolon(;)
    


Note: Inside body "select" can be used and "into" is used to fill up defined variables. An anonymous block always expects a select statement with 'into' - keyword.

If you are using older version of sql-developer to display on the screen before body structure add **SET SERVEROUTPUT ON**.

    
    DBMS_OUTPUT.PUT_LINE( 'The answer is: ' || answer ); -- command to test display in sql-developer
    




#### Usage of "UPDATE" and "SET"



    
    UPDATE employees SET salary = salary + bonus WHERE employee_id = emp_id;
    



    
    FOR i in 1..10 LOOP
    DBMS_OUTPUT.PUT_LINE(' Hello world(1)');
    END LOOP;
    



    
    WHILE sal <= 15000 LOOP
    DBMS_OUTPUT.PUT_LINE('Hello world(2) ')
    END LOOP;
    



    
    LOOP
    counter := counter + 1; -- increment counter variable
    total := total + counter * counter; -- compute total
    -- exit loop when condition is true
    EXIT WHEN total > 25000; -- LOOP until condition is met
    END LOOP;
    EXCEPTION
    WHEN NO_DATA_FOUND THEN
    INSERT INTO temp VALUES (NULL, NULL, 'Not found'); -- insert NULLs
    COMMIT;
    END;
    --




#### While loop format



    
    WHILE <> LOOP
    .......................
    END LOOP;




#### Goto



    
    BEGIN
    ...............
    GOTO print_now;
    ............
    <>
    .............
    END;




### Functions/Methods/Procedures


_Cursor_ -- this is like a pointer to table, points to only one row at a time
_Function _-- function like add/Sub/ ,... SO..ON ; Like we send parameters and we get a return;
_Procedure_ -- use this when a lot of things to do .... and finally need to return one single value; generally select statement - proc for finding a person's name with his id ;


#### UDD - user defined datatypes




#### Collections


collection types enable you to declare high-level data types similar to arrays, sets, and hash tables found in other languages.

    
    DECLARE
    -- declaring variables
    TYPE jobids_array IS VARRAY(12) OF VARCHAR2(10); -- declare VARRAY
    jobids jobids_array; -- declare a variable
    BEGIN
    jobids := jobids_array('AC_ACCOUNT', 'AC_MGR', 'AD_ASST', 'AD_PRES', 'AD_VP', 
     'FI_ACCOUNT', 'FI_MGR', 'HR_REP', 'IT_PROG', 'SH_CLERK',
     'ST_CLERK', 'ST_MAN');
    END LOOP;
    END;


How about now accessing our newly defined array?

    
    variable_name=jobids(3);




#### Records


Records are composite data structures whose fields can have different data types. You can use records/collections to hold related items and pass them to sub-programs with a single parameter. When declaring records, you use the TYPE definition.

Declaration:

    
    TYPE meeting_record
    IS RECORD (
    date_held DATE,
    duration timerec, -- nested record
    location VARCHAR2(20),
    purpose VARCHAR2(50)
    );


Usage:

    
    meeting_record.location = Delhi;
    FOR someone IN (SELECT * FROM employees WHERE employee_id < 120 )
    LOOP
    DBMS_OUTPUT.PUT_LINE('First name = ' || someone.first_name || ', Last name = ' || someone.last_name);
    END LOOP;
