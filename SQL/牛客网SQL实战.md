1. 查找最晚入职员工的所有信息，所有员工的入职时间都不是同一天。

    ```sqlite
    --思路一：按照时间进行降序排序，然后选择第一条记录。
    select * from employees e order by e.hire_date desc limit 1;
    
    --思路二：通过子查询实现，可以先找到，入职时间最晚的日期，然后查找对应日期的记录。
    select * from employees where hire_date = (select max(hire_date) from employees );
    ```

    

2. 查找入职员工时间排名倒数第三的员工所有信息，所有员工的入职时间都不是同一天。

    ```sqlite
    --思路一：按照时间排序，然后选择第三条记录
    --取第 3 条记录的方法，结合 limit 和 offset
    -- limit y 表示读取 y 条数据
    -- limit x,y 跳过 x 条数据，读取 y 条数据
    -- limit y offset x 跳过 x 条数据，读取 y 条数据
    select * from employees e order by e.hire_date desc limit 1 offset 2;
    ```

    

3. 

