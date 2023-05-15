1. Contare quanti iscritti ci sono stati ogni anno

SELECT COUNT(id) AS 'number_of_subscribers', YEAR(`enrolment_date`) AS 'year_of_enrolment'
FROM `students`
GROUP BY YEAR(`enrolment_date`);


2. Contare gli insegnanti che hanno l'ufficio nello stesso edificio

SELECT COUNT(id) AS 'number_of_teachers',`office_address`
FROM `teachers`
GROUP BY `office_address`;

3. Calcolare la media dei voti di ogni appello d'esame

SELECT AVG(`vote`) AS average_vote, `exam_id` 
FROM `exam_student` 
GROUP BY `exam_id`;

4. Contare quanti corsi di laurea ci sono per ogni dipartimento

SELECT COUNT( `degrees` . `id`) AS 'number_of_degrees',`departments`.`name` AS 'name_of_departments'
FROM `degrees`
JOIN `departments`  ON `degrees` . `department_id` = `departments`.`id`
GROUP BY `degrees` . `department_id`;