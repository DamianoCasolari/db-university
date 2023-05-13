## exercise query in the database

1. Selezionare tutti gli studenti nati nel 1990 (160)

SELECT * 
FROM `students` 
WHERE YEAR(date_of_birth) = 1990;

2. Selezionare tutti i corsi che valgono più di 10 crediti (479)

SELECT * 
FROM `courses` 
WHERE `cfu` > 10;

3. Selezionare tutti gli studenti che hanno più di 30 anni

SELECT name, surname, FLOOR(DATEDIFF(NOW(), date_of_birth) / 365) AS age 
FROM `students` 
WHERE DATEDIFF(NOW(), date_of_birth) / 365 > 30;

4. Selezionare tutti i corsi del primo semestre del primo anno di un qualsiasi corso di
laurea (286)

SELECT name,period,year
FROM `courses`
WHERE `period` = 'I semestre' AND `year` = 1;


5. Selezionare tutti gli appelli d'esame che avvengono nel pomeriggio (dopo le 14) del
20/06/2020 (21)

SELECT *
FROM `exams`
WHERE DATE(`date`) = '2020-06-20' AND HOUR(`hour`) > 14;

6. Selezionare tutti i corsi di laurea magistrale (38)

SELECT name
FROM `degrees`
WHERE `level` = 'magistrale';

7. Da quanti dipartimenti è composta l'università? (12)

SELECT name, head_of_department, address, website
FROM `departments`;

8. Quanti sono gli insegnanti che non hanno un numero di telefono? (50)

SELECT COUNT(id) FROM teachers
WHERE `phone` IS NULL;


	


# Database University

## Data types

    - Strings: varchar(number) (max255), char(number), text, longtext
    - numbers: tinyint, small/medium int , int, bigint        
    - decimals: float(i,d), double(i,d), decimal(i,d)
    - dates: DATETIME, DATE, YEAR, TIME, TIMESTAMP


># Tables

- course_teacher          
-  courses                 
-  degrees                 
-  departments             
-  exam_student            
-  exams                   
-  students                
-  teachers     


># Table name : courses
>## Entity name: course


>## Table column 
 id           bigint(20) unsigned  NO    PRI  NULL     auto_increment 
 degree_id    bigint(20) unsigned  NO    MUL  NULL                    
 name         varchar(255)         NO         NULL                    
 description  text                 YES        NULL                    
 period       varchar(255)         NO         NULL                    
 year         tinyint(3) unsigned  NO         NULL                    
 cfu          tinyint(3) unsigned  NO         NULL                    
 website      varchar(255)         YES        NULL                    


># Table name : degreeses
 >## Entity name: degrees

>## Table column 
 Field          Type                 Null  Key  Default  Extra          
+---------------+---------------------+------+-----+---------
 
 id             bigint(20) unsigned  NO    PRI  NULL     auto_increment 
 department_id  bigint(20) unsigned  NO    MUL  NULL                    
 name           varchar(255)         NO         NULL                    
 level          varchar(255)         NO         NULL                    
 address        varchar(255)         NO         NULL                    
 email          varchar(255)         NO         NULL                    
 website        varchar(255)         NO         NULL                       

># Table name : departments
  >## Entity name: department

>## Table column 
 Field              Type                Null Key Default Extra         
+--------------------+---------------------+------+-----

id                 bigint(20) unsigned NO   PRI NULL    auto_increment
name               varchar(255)        NO       NULL                  
address            varchar(255)        NO       NULL                  
phone              varchar(255)        YES      NULL                  
email              varchar(255)        NO   UNI NULL                  
website            varchar(255)        NO       NULL                  
head_of_department varchar(255)        NO       NULL                    

># Table name : exams
>## Entity name: exam

>## Table column 
Field     Type                Null Key Default Extra          
+-----------+---------------------+------+-----+---------

id        bigint(20) unsigned NO   PRI NULL    auto_increment 
course_id bigint(20) unsigned NO   MUL NULL                   
date      date                NO       NULL                   
hour      time                NO       NULL                   
location  varchar(255)        NO       NULL                   
address   varchar(255)        NO       NULL                     

># Table name : studenst
>## Entity name: student

>## Table column 
 Field                Type                 Null  Key  Default  Extra          
+---------------------+---------------------+------+-----

 id                   bigint(20) unsigned  NO    PRI  NULL     auto_increment 
 degree_id            bigint(20) unsigned  NO    MUL  NULL                    
 name                 varchar(255)         NO         NULL                    
 surname              varchar(255)         NO         NULL                    
 date_of_birth        date                 NO         NULL                    
 fiscal_code          varchar(255)         NO         NULL                    
 enrolment_date       date                 NO         NULL                    
 registration_number  varchar(255)         NO         NULL                    
 email                varchar(255)         NO    UNI  NULL   


># Table name : teachers
>## Entity name: teacher

>## Table column 
 Field           Type                 Null  Key  Default  Extra          
+----------------+---------------------+------+-----

 id              bigint(20) unsigned  NO    PRI  NULL     auto_increment 
 name            varchar(255)         NO         NULL                    
 surname         varchar(255)         NO         NULL                    
 phone           varchar(255)         YES        NULL                    
 email           varchar(255)         NO    UNI  NULL                    
 office_address  varchar(255)         NO         NULL                    
 office_number   varchar(255)         NO         NULL                 