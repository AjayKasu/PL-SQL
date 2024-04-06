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

          
        
      
-----------------------------------------------------
--SIMPLE LOOP:
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
--2.looping control structures:-which is used for repeatedly execute the statemnets in the loop.
--3.jumping control structures:-used for jump from loop.


