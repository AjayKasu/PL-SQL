# PL-SQL
-------------------------------------------------------------------------------------------------------------------
select * from Meta_data;
desc meta_data;
insert into meta_data values (01,'AJAY','KASU','26-10-2023');
insert into meta_data values (03,'Ram', 'JAY','12-11-2023');
-------------------------------------------------------------------------------------------------------------------
Create table Sub_meta_data(
sr_no number(2) REFERENCES Meta_data(sr_no), --column_nm <data_type> REFERENCES orginal_column_nm(<original_sr_no>)
salary number(7,2) );
desc Sub_meta_data;
insert into Sub_meta_data values(03,96000.99);
commit;
select * from Sub_meta_data;
commit;
select * from meta_data;
select * from sub_meta_data;
-----------------------------------------------------------------
select meta_data.SR_NO,meta_data.FIRST_NAME,Sub_meta_data.SALARY from meta_data 
 inner JOIN 
Sub_meta_data  ON Meta_data.SR_NO=Sub_meta_data.SR_NO; 
commit;
----------------------------------------------------------------------------------
BEGIN
    DBMS_OUTPUT.PUT_LINE ('HELLO ORACLE PL/SQL I am BACK');
END;
/
SET SERVEROUTPUT ON;-- THE MESSAGE DISPLAY ON SCREEN.
SET VERIFY OFF;-- TO REMOVE THE DISPLAY OF THE CODE.
-------------------------------------------------------------------------------
DECLARE 
  v_n1 int:=20;
  v_n2 int:=80;
  v_n3 int;
BEGIN
  v_n3:=v_n1+v_n2;
  DBMS_OUTPUT.PUT_LINE('THE SUM OF ' ||v_n1||' and ' ||v_n2||' is '||V_N3);
END;
/
--------------------------------------------------------------------------------
SELECT * FROM TAB;
SELECT * FROM EMP1;
DESC EMP1;
SET PAGES 50000
SET LINES 32767
-------------------------------------
--INSERT
BEGIN 
  insert into emp1 (
    EMPLOYEE_ID,FIRST_NAME,LAST_NAME,HIRE_DATE,SALARY,EMAIL,JOB_ID
    )
    VALUES(
    206,'RAMUDU','DHARMA', '23-10-2023', 980000.99,'RAMU@0306.COM','CEO');
END;
/
COMMIT; 
--------------------------------------------------------------------------------
--UPDATE
DECLARE
  V_PHONE_NUMBER EMP1.PHONE_NUMBER%TYPE;
BEGIN 
  UPDATE EMP1
  SET PHONE_NUMBER=7569745180
  WHERE FIRST_NAME = 'RAMUDU';
END;
/
COMMIT;
SELECT FIRST_NAME,PHONE_NUMBER FROM EMP1 WHERE FIRST_NAME='RAMUDU';
UPDATE EMP1 SET PHONE_NUMBER=75697456199 WHERE FIRST_NAME='RAMUDU';
COMMIT;
--------------------------------------------------------------------------------
SELECT * FROM EMP1;
--increase salary of all employess who job is clerk
--here we take v_sal_increase for assign increasing value
DECLARE 
  V_SAL_INCREMENT EMP1.salary%TYPE :=1000;
BEGIN 
  UPDATE EMP1 SET 
    SALARY = SALARY +V_SAL_INCREMENT
    WHERE JOB_ID='SH_CLERK';
END;
/
SET SERVEROUTPUT ON;
----------------------------------------------------------------------------
--Delete the rows of emp table where emp_id '333'
--variable to enter the emp_id 
DECLARE 
  v_employee_id emp1.employee_id%type :=333;
BEGIN
  delete from emp1
  where employee_id=v_employee_id;
END;
/
select * from emp1;
-----------------------------------------------------------------------------
/*CONTROL STRUCTURES:control the flow of the of execution statemetns.
*it can be catagories into 3-types:
1.condition control structures:-control the flow of execution of statement based on the condtion.*/
--A)IF..THEN:-
DECLARE 
  AGE INT;
BEGIN
  AGE:=&AGE;
  IF AGE>=18 THEN
    DBMS_OUTPUT.PUT_LINE(AGE ||' IS ' || 'Eligible for vote');
  END IF;
END;
/
SET SERVEROUTPUT ON;
set verify off;
--B)IF..ELSIF..THEN :-EVEN OR ODD
DECLARE 
  I INT:=&I;
BEGIN
  IF I>0 THEN
    DBMS_OUTPUT.PUT_LINE(I ||' IS POSITIVE');
  ELSIF I<0 THEN
    DBMS_OUTPUT.PUT_LINE(I || ' IS NEGATIVE');
  ELSE
    DBMS_OUTPUT.PUT_LINE(I || ' IS ZERO');
  END IF;
END;
/
--C)NEASTED IF: IF INSIDE ANOTHER IF
DECLARE
  X INT:=&X;
  Y INT:=&Y;
  Z INT:=&Z;
BEGIN 
  IF X>Y THEN
    IF X>Z THEN
      DBMS_OUTPUT.PUT_LINE(X || ' X IS GREATER');
    ELSE
      DBMS_OUTPUT.PUT_LINE(Z || ' Z IS GREATER');
    END IF;
  ELSE 
      IF Y>Z THEN
          DBMS_OUTPUT.PUT_LINE(Y ||' Y IS GREATER');
      ELSE
        DBMS_OUTPUT.PUT_LINE(Z || ' Z IS GREATER');
      END IF;
  END IF;
END;
/
/*C)CASE:
1.SIMPLE CASE:EQUALITY*/
DECLARE
  N INT:=15;
BEGIN
  CASE mod(N,2)
    WHEN 0 THEN
      DBMS_OUTPUT.PUT_LINE(N ||' IS EVEN ');
    WHEN 1 THEN 
      DBMS_OUTPUT.PUT_LINE(N || ' IS ODD');
  END CASE;
END;
/
/*2.SEARCHED CASE:
NON-EQUALITY
*/
DECLARE
  I INT:=&I;
BEGIN
  CASE
    WHEN I>0 THEN
      DBMS_OUTPUT.PUT_LINE(I || ' IS POSITIVE');
    WHEN I<0 THEN
      DBMS_OUTPUT.PUT_LINE(I || ' IS NEGATIVE');
    ELSE
      DBMS_OUTPUT.PUT_LINE(I || ' IS ZERO');
  END CASE;
END;
/
----------------------------------------------------------------------------------------------------
--NEASTED IF: IF INSIDE ANOTHER IF
DECLARE
  X INT:=&X;
  Y INT:=&Y;
  Z INT:=&Z;
BEGIN 
  IF X>Y THEN
    IF X>Z THEN
      DBMS_OUTPUT.PUT_LINE(X || ' X IS GREATER');
    ELSE
      DBMS_OUTPUT.PUT_LINE(Z || ' Z IS GREATER');
    END IF;
  ELSE 
      IF Y>Z THEN
          DBMS_OUTPUT.PUT_LINE(Y ||' Y IS GREATER');
      ELSE
        DBMS_OUTPUT.PUT_LINE(Z || ' Z IS GREATER');
      END IF;
  END IF;
END;
/
/*CASE:
1.SIMPLE CASE:EQUALITY*/
DECLARE
  N INT:=15;
BEGIN
  CASE mod(N,2)
    WHEN 0 THEN
      DBMS_OUTPUT.PUT_LINE(N ||' IS EVEN ');
    WHEN 1 THEN 
      DBMS_OUTPUT.PUT_LINE(N || ' IS ODD');
  END CASE;
END;
/
/*2.SEARCHED CASE:
NON-EQUALITY
*/
DECLARE
  I INT:=&I;
BEGIN
  CASE
    WHEN I>0 THEN
      DBMS_OUTPUT.PUT_LINE(I || ' IS POSITIVE');
    WHEN I<0 THEN
      DBMS_OUTPUT.PUT_LINE(I || ' IS NEGATIVE');
    ELSE
      DBMS_OUTPUT.PUT_LINE(I || ' IS ZERO');
  END CASE;
END;
/
-----------------------------------------------------------------
--2.looping control structures:-which is used for repeatedly execute the statemnets in the loop.
--a)simple loop:
DECLARE
  I INT;
BEGIN 
  i:=1;
  LOOP 
    dbms_output.put_line(i);
    i:=i+1;
    exit when i>=5;
  END LOOP;
END;
/
set serveroutput on;
--while loop:
DECLARE 
  I INT:=1;
BEGIN
  WHILE (I<=20)
    LOOP
      DBMS_OUTPUT.PUT_LINE('HERE YOU GO ' || I);
      I:=I+1;
    END LOOP;
END;
/
-------------------------------------------------------------------
--for loop:
DECLARE 
  N INT;
BEGIN 
  FOR N IN 1..10
  LOOP
    DBMS_OUTPUT.PUT_LINE(N);
  END LOOP;
END;
/
------------------------------------------------------------------------------
--for loop 
DECLARE 
  I INT;
BEGIN
  FOR I IN REVERSE 1..5
  LOOP
    DBMS_OUTPUT.PUT_LINE(I);
  END LOOP;
END;
/
---------------------------------------------------------------------------------------------
--3.jumping control structures:-used for jump from loop.
--GOTO :
--A)JUMPING BACKWARD;

DECLARE
  I INT:=1;
BEGIN
  <<LABEL_TEST>>
    DBMS_OUTPUT.PUT_LINE(I);
    I:=I+1;
    IF I<4 THEN
  GOTO LABEL_TEST;
    END IF;
END;
/
SET SERVEROUTPUT ON;
--B)JUMPING FORWARD;
BEGIN
  DBMS_OUTPUT.PUT_LINE('HI');
  GOTO TEST1;
    DBMS_OUTPUT.PUT_LINE('HI');-- GOTO WORKING AS SKIP THIS LABEL AND EXECUTE ANOTHER LABEL.
  <<TEST1>>
    DBMS_OUTPUT.PUT_LINE('WELCOME TO GOTO FORWARD');
END;
/
-------------------------------------------------------------------------------
--EXIT: WHICH IS USED FOR TERMINATE LOOP IN THE MIDDLE OF THE EXECUTION;
BEGIN
  FOR I IN 1..10
    LOOP
      DBMS_OUTPUT.PUT_LINE(I);
      IF I=5 THEN
          EXIT;
      END IF;
    END LOOP;
END;
/
SET SERVEROUTPUT ON;
--EXIT WHEN: TERMINATE THE LOOP 
BEGIN
  FOR I IN 1..20
  LOOP
    DBMS_OUTPUT.PUT_LINE(I);
    EXIT WHEN I=10;
  END LOOP;
  DBMS_OUTPUT.PUT_LINE('HERE THE SERIAL NUMBERS STOP');
END;
/
-----------------------------------------------------------------------------
--1.IN THE PL/SQL DML,DQL AND TCL ARE USED.
--2.If we want used the DDL commands use DYNAMIC SQL in the PLS/SQL.
--3. All sysntax same as SQL in PL/SQL. But DQL -SELECT command sysntax is different.
/*select <col_list> into <var_list>
  from <table_nm> where <condition>;
  */
  SELECT * FROM EMP1;
--find data of employee first name and salary where employee id
DECLARE
  V_EMPLOYEE_ID EMP1.EMPLOYEE_ID%TYPE;
  V_FIRST_NAME EMP1.FIRST_NAME%TYPE;
  V_SALARY EMP1.SALARY%TYPE;
BEGIN
  V_EMPLOYEE_ID := &employee_id;
  SELECT FIRST_NAME,SALARY INTO V_FIRST_NAME,V_SALARY 
    FROM EMP1 
        WHERE EMPLOYEE_ID=V_EMPLOYEE_ID;
  DBMS_OUTPUT.PUT_LINE('EMPLOYEE NAME:' || V_FIRST_NAME ||' SALARY:' || V_SALARY || ' At EMPLOYEE ID: ' ||V_EMPLOYEE_ID );
END;
/
set serveroutput on;
--find employee experience in years where employee id
DECLARE
  V_EMPLOYEE_ID EMP1.EMPLOYEE_ID%TYPE;
  v_hire_date EMP1.hire_date%type;
  v_expr int;
Begin
  v_employee_id:=&employee_id;
  select hire_date into v_hire_date 
    from emp1
      where employee_id =v_employee_id;
  v_expr:=(sysdate-V_hire_date)/365;
  DBMS_OUTPUT.PUT_LINE(v_hire_date || ' experience of employee: '||v_expr);
END;
/
------------------------------------------------------------------------------
--delete record of employee who's experinec greaterthan 40 .
DECLARE
  V_EMPLOYEE_ID EMP1.EMPLOYEE_ID%TYPE;
  V_HIRE_DATE EMP1.HIRE_DATE%TYPE;
  V_EXPR INT;
BEGIN
  V_EMPLOYEE_ID:=&EMPLOYEE_ID;
  SELECT HIRE_DATE INTO V_HIRE_DATE FROM EMP1
    WHERE EMPLOYEE_ID=V_EMPLOYEE_ID;
  --FIND EXPERIENCE
  V_EXPR :=(SYSDATE-V_HIRE_DATE)/365;
  DBMS_OUTPUT.PUT_LINE('EXPERIENCE OF EMPLOYEE:' || V_EXPR || ' YEARS');
   
  -- DELETE RECORD WHO'S >40 EXPR
  IF V_EXPR>35 THEN
    DELETE FROM EMP1 WHERE EMPLOYEE_ID=V_EMPLOYEE_ID;
    commit;
    DBMS_OUTPUT.PUT_LINE('DELETE THE RECORD SUCCESSFULLY' || ' AT EMPLOYEE ID:' || V_EMPLOYEE_ID);
  END IF;  
END;
/
SET SERVEROUTPUT ON;
select * from emp1;

