# sql-challenge

## Data Modeling

![ERD](EmployeeSQL/data/QuickDBD-export.png)

## Data Engineering

## Data Analysis

After completing the importing process a Postgresql analysiss was perfomed and you can find the full query in this file [Employees_db_Query.sql](EmployeeSQL/Employees_db_Query.sql)   

The analysis query performed, and cascaded in the following formats: 

1. The query to list the following details of each employee: employee number, last name, first name, sex, and salary

```SELECT employees.emp_no, employees.last_name, employees.first_name, employees.sex, salaries.salary
FROM employees
JOIN salaries
ON employees.emp_no = salaries.emp_no;

```
   
2. The query to list first name, last name, and hire date for employees who were hired in 1986.

```
SELECT first_name, last_name, hire_date 
FROM employees
WHERE hire_date BETWEEN '1986-01-01' AND '1987-01-01';

 ```

3. The query list the manager of each department with the following information: department number, department name, the manager's employee number, last name, first name.
```employee number, last name, first name.
SELECT departments.dept_no, departments.dept_name, dept_manager.emp_no, employees.last_name, employees.first_name
FROM departments
JOIN dept_manager
ON departments.dept_no = dept_manager.dept_no
JOIN employees
ON dept_manager.emp_no = employees.emp_no;
 ```

4. The query to list the department of each employee with the following information: employee number, last name, first name, and department name.
 ```SELECT dept_emp.emp_no, employees.last_name, employees.first_name, departments.dept_name
FROM dept_emp
JOIN employees
ON dept_emp.emp_no = employees.emp_no
JOIN departments
ON dept_emp.dept_no = departments.dept_no;
 
 ```
5. The query to list first name, last name, and sex for employees whose first name is "Hercules" and last names begin with "B."

```SELECT first_name, last_name,sex
FROM employees
WHERE first_name = 'Hercules'
AND last_name LIKE 'B%';

 ```

6. The query to list all employees in the Sales department, including their employee number, last name, first name, and department name.

```SELECT dept_emp.emp_no, employees.last_name, employees.first_name, departments.dept_name
FROM dept_emp
JOIN employees
ON dept_emp.emp_no = employees.emp_no
JOIN departments
ON dept_emp.dept_no = departments.dept_no
WHERE departments.dept_name = 'Sales';

 ```
7. The query to list all employees in the Sales and Development departments, including their employee number, last name, first name, and department name.

```SELECT dept_emp.emp_no, employees.last_name, employees.first_name, departments.dept_name
FROM dept_emp
JOIN employees
ON dept_emp.emp_no = employees.emp_no
JOIN departments
ON dept_emp.dept_no = departments.dept_no
WHERE departments.dept_name = 'Sales' 
OR departments.dept_name = 'Development'
 ```

8. In descending order, list the frequency count of employee last names, i.e., how many employees share each last name.

```SELECT last_name,
COUNT(last_name) AS "frequency"
FROM employees
GROUP BY last_name
ORDER BY
COUNT(last_name) DESC;

 ```