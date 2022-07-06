-- 
--Table and column making
-- 
CREATE TABLE departments (
dept_no VARCHAR(30),
dept_name VARCHAR(30));

CREATE TABLE dept_emp (
emp_no INTEGER,
dept_no VARCHAR(30)
);

CREATE TABLE dept_manager (
dept_no VARCHAR(30),
emp_no INTEGER
);

CREATE TABLE employees (
emp_no INTEGER,
emp_title_id VARCHAR(30),
birth_date DATE,
first_name VARCHAR(30),
last_name VARCHAR(30),
sex VARCHAR(1),
hire_date DATE
);

CREATE TABLE salaries (
emp_no INTEGER,
salary INTEGER
);
	
CREATE TABLE titles (
title_id VARCHAR(5),
title VARCHAR(30)
);
-- 

-- Imported given data manually.

-- 
-- Checking for duplicates to better model data.
-- 

--Checking for duplicates in employees column: emp_no: NO
SELECT emp_no, COUNT(emp_no)
FROM employees
GROUP BY emp_no
HAVING COUNT(emp_no) > 1

-- Checking for duplicates in dept_manager column: emp_no: NO
SELECT emp_no, COUNT(emp_no)
FROM dept_manager
GROUP BY emp_no
HAVING COUNT(emp_no) > 1

-- Checking for duplicates in dept_emp column: emp_no: YES
SELECT emp_no, COUNT(emp_no)
FROM dept_emp
GROUP BY emp_no
HAVING COUNT(emp_no) > 1

-- 
-- Creating primary keys and composite key.
-- 

-- Composite key for dept_emp
ALTER TABLE dept_emp
ADD CONSTRAINT PK_dept_emp PRIMARY KEY (emp_no,dept_no);

-- Primary Keys
ALTER TABLE departments
ADD CONSTRAINT PK_departments PRIMARY KEY (dept_no);

ALTER TABLE dept_manager
ADD CONSTRAINT PK_dept_manager PRIMARY KEY (emp_no);

ALTER TABLE employees
ADD CONSTRAINT PK_employees PRIMARY KEY (emp_no);

ALTER TABLE salaries
ADD CONSTRAINT PK_salaries PRIMARY KEY (emp_no);

ALTER TABLE titles
ADD CONSTRAINT PK_titles PRIMARY KEY (title_id);

-- 
-- 1.List the following details of each employee:
-- employee number, last name, first name, sex, and salary.
-- 
SELECT employees.emp_no, employees.last_name, employees.first_name, employees.sex, salaries.salary
FROM employees
INNER JOIN salaries ON employees.emp_no=salaries.emp_no;

-- 
-- 2.List first name, last name, and hire date for employees who were hired in 1986.
-- 
SELECT first_name, last_name, hire_date
FROM employees
WHERE hire_date >= '1986-1-1';

-- 
-- 3.List the manager of each department with the following information: department number,
-- department name, the manager's employee number, last name, first name.
-- 
SELECT dept_manager.dept_no, departments.dept_name, employees.emp_no,
employees.first_name, employees.last_name, employees.hire_date
FROM employees
INNER JOIN dept_manager ON employees.emp_no=dept_manager.emp_no
INNER JOIN departments ON dept_manager.dept_no=departments.dept_no;

-- 
-- 4.List the department of each employee with the following information:
-- employee number, last name, first name, and department name.
-- 
SELECT employees.emp_no, employees.last_name, employees.first_name, departments.dept_name
FROM employees
INNER JOIN dept_emp ON employees.emp_no=dept_emp.emp_no
INNER JOIN departments ON dept_emp.dept_no=departments.dept_no;

-- 
-- 5.List first name, last name, and sex for employees whose first name is:
-- "Hercules" and last names begin with "B."
-- 
SELECT first_name, last_name, sex
FROM employees
WHERE first_name='Hercules' AND last_name LIKE 'B%';
-- 

-- 
-- 6.List all employees in the Sales department, including their employee number,
-- last name, first name, and department name.
-- 
SELECT employees.emp_no, employees.last_name, employees.first_name, departments.dept_name
FROM employees
INNER JOIN dept_emp ON employees.emp_no = dept_emp.emp_no
INNER JOIN departments ON dept_emp.dept_no=departments.dept_no
WHERE dept_name = 'Sales'
-- 

-- 
-- 7.List all employees in the Sales and Development departments,
-- including their employee number, last name, first name, and department name.
-- 
SELECT employees.emp_no, employees.last_name, employees.first_name, departments.dept_name
FROM employees
INNER JOIN dept_emp ON employees.emp_no = dept_emp.emp_no
INNER JOIN departments ON dept_emp.dept_no=departments.dept_no
WHERE dept_name = 'Sales' OR dept_name = 'Development'
-- 

-- 
-- 8.List the frequency count of employee last names 
-- (i.e., how many employees share each last name) in descending order.
-- 
SELECT last_name, COUNT(*)
FROM employees
GROUP BY last_name
ORDER BY
COUNT(*) DESC
-- 



