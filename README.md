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
