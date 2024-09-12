Q1.
mysql> CREATE TABLE departments (
    -> department_id int auto_increment primary key,
    -> name VARCHAR(20) NOT NULL,
    -> created_at timestamp default current_timestamp,
    -> updated_at timestamp default current_timestamp on update current_timestamp
    -> );

Q2.
ALTER TABLE people ADD department_id INT unsigned AFTER email;

Q3.

