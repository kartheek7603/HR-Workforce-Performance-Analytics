-- Q)CREATE DATABASE hr_workforce_analysis;
CREATE DATABASE hr_workforce_analysis;
USE hr_workforce_analysis;
-- create the employee table:
CREATE TABLE emp_info (
employee_id INT PRIMARY KEY, 
    employee_name VARCHAR(150), 
    date_of_birth DATE, 
    gender VARCHAR(50), 
    marital_status VARCHAR(50), 
    qualification VARCHAR(100), 
    location VARCHAR(100), 
    hire_date DATE, 
    active_status VARCHAR(50), 
    department_id INT, 
    role_id INT 
);
-- Create the salary table: 
CREATE TABLE emp_salaries ( 
    employee_id INT, 
    basic_salary DECIMAL(12,2), 
    pf DECIMAL(12,2), 
    esi DECIMAL(12,2), 
    performance_rating DECIMAL(5,2), 
    performance_bonus DECIMAL(12,2), 
    gross_salary DECIMAL(12,2), 
    net_salary DECIMAL(12,2) 
);
-- Create the department table: 
CREATE TABLE department ( 
    department_id INT PRIMARY KEY, 
    department_name VARCHAR(100), 
    cost_center VARCHAR(100) 
); 
-- Create the job roles table: 
CREATE TABLE job_roles ( 
    role_id INT PRIMARY KEY, 
    job_position VARCHAR(150), 
    base_salary_benchmark DECIMAL(12,2) 
); 
-- Total Employee  
SELECT 
    COUNT(*) AS total_employees 
FROM emp_info; 
-- Active Employees 
SELECT 
    COUNT(*) AS active_employees 
FROM emp_info 
WHERE LOWER(active_status) = 'active'; 
-- Employees by Department 
SELECT 
d.department_name, 
COUNT(*) AS employee_count 
FROM emp_info e 
JOIN department d 
ON e.department_id = d.department_id 
GROUP BY d.department_name 
ORDER BY employee_count DESC; 
-- Employees by Location 
SELECT 
location, 
COUNT(*) AS employee_count 
FROM emp_info 
GROUP BY location 
ORDER BY employee_count DESC; 
-- Employees by Gender 
SELECT 
gender, 
COUNT(*) AS employee_count 
FROM emp_info 
GROUP BY gender; 
-- Average Basic Salary 
SELECT 
AVG(basic_salary) AS average_basic_salary 
FROM emp_salaries; 
-- Average Gross Salary 
SELECT 
AVG(gross_salary) AS average_gross_salary 
FROM emp_salaries; 
-- Average Net Salary 
SELECT 
AVG(net_salary) AS average_net_salary 
FROM emp_salaries; 
-- Average Salary by Department 
SELECT 
    d.department_name, 
    AVG(s.basic_salary) AS average_basic_salary 
FROM emp_info e 
JOIN emp_salaries s 
    ON e.employee_id = s.employee_id 
JOIN department d 
    ON e.department_id = d.department_id 
GROUP BY d.department_name 
ORDER BY average_basic_salary DESC; 
-- Total Payroll by Department 
SELECT 
    d.department_name, 
    SUM(s.gross_salary) AS total_payroll 
FROM emp_info e 
JOIN emp_salaries s 
    ON e.employee_id = s.employee_id 
JOIN department d 
    ON e.department_id = d.department_id 
GROUP BY d.department_name 
ORDER BY total_payroll DESC; 
-- Average Performance Rating by Department 
SELECT 
    d.department_name, 
    AVG(s.performance_rating) AS average_rating 
FROM emp_info e 
JOIN emp_salaries s 
    ON e.employee_id = s.employee_id 
JOIN department d 
    ON e.department_id = d.department_id 
GROUP BY d.department_name 
ORDER BY average_rating DESC; 
-- Performance Bonus by Department 
SELECT 
    d.department_name, 
    SUM(s.performance_bonus) AS total_bonus 
FROM emp_info e 
JOIN emp_salaries s 
    ON e.employee_id = s.employee_id 
JOIN department d 
    ON e.department_id = d.department_id 
GROUP BY d.department_name 
ORDER BY total_bonus DESC; 
-- Employees by Job Role 
SELECT 
    r.job_position, 
    COUNT(*) AS employee_count 
FROM emp_info e 
JOIN job_roles r 
    ON e.role_id = r.role_id 
GROUP BY r.job_position 
ORDER BY employee_count DESC; 
-- Average Salary by Job Role 
SELECT 
    r.job_position, 
    AVG(s.basic_salary) AS average_salary 
FROM emp_info e 
JOIN emp_salaries s 
    ON e.employee_id = s.employee_id 
JOIN job_roles r 
    ON e.role_id = r.role_id 
GROUP BY r.job_position 
ORDER BY average_salary DESC;
-- Salary Benchmark by Job Role 
SELECT 
    job_position, 
    base_salary_benchmark 
FROM job_roles 
ORDER BY base_salary_benchmark DESC; 
-- Average Bonus by Performance Rating 
SELECT 
    performance_rating, 
    AVG(performance_bonus) AS average_bonus 
FROM emp_salaries 
GROUP BY performance_rating 
ORDER BY performance_rating; 
-- Total PF and ESI 
SELECT 
    SUM(pf) AS total_pf, 
    SUM(esi) AS total_esi 
FROM emp_salaries; 
-- Hiring Trend 
SELECT 
    YEAR(hire_date) AS hire_year, 
    COUNT(*) AS employees_hired 
FROM emp_info 
GROUP BY YEAR(hire_date) 
ORDER BY hire_year; 
-- Highest Paid Employees 
SELECT 
    e.employee_id, 
    e.employee_name, 
    s.basic_salary, 
    s.gross_salary, 
    s.net_salary 
FROM emp_info e 
JOIN emp_salaries s 
    ON e.employee_id = s.employee_id 
ORDER BY s.gross_salary DESC 
LIMIT 10; 
-- Employees with Highest Performance Ratings 
SELECT 
    e.employee_id, 
    e.employee_name, 
    s.performance_rating, 
    s.performance_bonus 
FROM emp_info e 
JOIN emp_salaries s 
    ON e.employee_id = s.employee_id 
ORDER BY s.performance_rating DESC 
LIMIT 10;
