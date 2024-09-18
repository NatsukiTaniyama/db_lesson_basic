Q1.
mysql> CREATE TABLE departments (
    -> department_id int unsigned auto_increment primary key,
    -> name VARCHAR(20) NOT NULL,
    -> created_at timestamp default current_timestamp,
    -> updated_at timestamp default current_timestamp on update current_timestamp
    -> );

Q2.
ALTER TABLE people ADD department_id INT unsigned AFTER email;

Q3.
mysql> INSERT INTO departments (name)
    -> VALUES
    -> ('営業'),
    -> ('開発'),
    -> ('経理'),
    -> ('人事'),
    -> ('情報システム');


mysql> INSERT INTO people (name, email, department_id, age, gender)
    -> VALUES
    -> ('佐藤ほのか', 'sato@gizumo.jp', 1, 25, 2),
    -> ('石川ひろし', 'ishikawa@gizumo.jp', 1, 42, 1),
    -> ('高橋ゆう', 'takahashi@gizumo.jp', 1, 34, 2),
    -> ('伊藤まさし', 'ito@gizumo.co.jp', 2, 61, 1),
    -> ('山田えりこ', 'yamada@gizumo.co.jp', 2, 50, 2),
    -> ('渡辺あおい', 'watanabe@gizumo.jp', 2, 35, 2),
    -> ('山本ゆうすけ', 'yamamoto@gizumo.jp', 2, 30, 1),
    -> ('木村みお', 'kimura@gizumo.jp', 3, 26, 2),
    -> ('吉田りく', 'yoshida@gizumo.co.jp', 4, 29, 1),
    -> ('松本しゅん', 'matsumoto@gizumo.co.jp', 5, 33, 1);

mysql> INSERT INTO reports (person_id, content)
    -> VALUES
    -> (1, '退勤'),
    -> (3, 'たいきん'),
    -> (4, '退勤しました'),
    -> (18, '退勤しました。'),
    -> (19, 'おわり'),
    -> (20, '出勤'),
    -> (21, '出勤しました'),
    -> (23, 'しゅっきん'),
    -> (25, '開始'),
    -> (26, '開始します');

Q4.
UPDATE people SET department_id = '1' WHERE person_id = 1;
UPDATE people SET department_id = '3' WHERE person_id = 2;
UPDATE people SET department_id = '3' WHERE person_id = 3;
UPDATE people SET department_id = '4' WHERE person_id = 4;
UPDATE people SET department_id = '5' WHERE person_id = 6;

Q5.
SELECT name, age FROM people WHERE gender = 1;

Q6.
peopleテーブルから営業部に所属する人のname、email、ageカラムを日報作成日時の昇順に取得する。

Q7.
SELECT name FROM people WHERE age BETWEEN 20 AND 29 AND gender = 2 OR age BETWEEN 40 AND 49 AND gender = 1;

Q8.
SELECT * FROM people WHERE department_id = 1 ORDER BY age ;

Q9.
SELECT AVG(age) AS average_age FROM people WHERE gender = 2 AND department_id = 2;

Q10.
mysql> SELECT people.name, departments.name, reports.content
    -> FROM people JOIN reports ON people.person_id = reports.person_id JOIN departments ON people.department_id = departments.department_id;

Q11.
mysql> SELECT people.name, reports.content = NULL
    -> FROM people JOIN reports ON people.person_id = reports.person_id;