# CTE-s
```
-- which departments have a max salary below 60000    cte older software and simpler queries
select * from (
	select department,max(salary )as max_salary
	from employees
	group by department)

where max_salary < 60000


-- as a cte  -- cleaner look ,used for complex queries
with ms as (select department, max(salary) as max_salary
			from employees
			group by department)

select * from ms 
where max_salary <(select avg(max_salary )from ms)

-- multiple tables
--  wanting to look at employees with age above 30 and  compare max salary in  their departments
with ms as (select department, max(salary) as max_salary
			from employees
			group by department),

     age as (select * 
           from employees
           where age > 30)
select * 
from age left join ms on age.department =ms.department

```




