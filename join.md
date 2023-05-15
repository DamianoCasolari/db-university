1. Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia

SELECT `students` . * 
FROM `students`
JOIN `degrees`  ON `students` . `degree_id` = `degrees`.`id`
WHERE `degrees`. `name` = 'Corso di Laurea in Economia';

2. Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze

SELECT `degrees` . `name` AS 'Corsi di Laurea Magistrale del Dipartimento di Neuroscienze', `degrees` . `email` 
FROM `degrees`
JOIN `departments`  ON `degrees` . `department_id` = `departments`.`id`
WHERE `departments`. `name` = 'Dipartimento di Neuroscienze' AND `degrees` . `level` = 'magistrale';

3. Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)

SELECT `courses` . `name` AS 'corsi in cui insegna Fulvio Amato', `courses` . `cfu` 
FROM `courses`
JOIN `course_teacher`  ON `courses`.`id` = `course_teacher` . `course_id`
JOIN `teachers`  ON `course_teacher` . `teacher_id` = `teachers`.`id`
WHERE `teachers`. `id` = 44;


4. Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il
relativo dipartimento, in ordine alfabetico per cognome e nome


SELECT `students` . `name` AS 'students_name',`students` . `surname` AS 'students_surname', `degrees` . `name` AS 'degree_name',  `departments`. `name` AS 'department_name'
FROM `students`
JOIN `degrees`  ON `students`.`degree_id` = `degrees` . `id`
JOIN `departments`  ON `degrees` . `department_id` = `departments`.`id`
ORDER BY `students` . `surname`, `students` . `name`;

5. Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti

SELECT DISTINCT `degrees` . `name` AS 'degree_name', `courses` . `name` AS 'course_name',  `teachers`. `name` AS 'teacher_name'
FROM `degrees`
JOIN `courses`  ON `degrees`.`id` = `courses` . `degree_id`
JOIN `course_teacher`  ON `courses` . `id` = `course_teacher`.`course_id`
JOIN `teachers`  ON `course_teacher` . `teacher_id` = `teachers`.`id`
ORDER BY `degrees` . `name`;

6. Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54)

SELECT DISTINCT `teachers`. * 
FROM `teachers`
JOIN `course_teacher`  ON `teachers`.`id` = `course_teacher` . `teacher_id`
JOIN `courses`  ON `courses` . `id` = `course_teacher`.`course_id`
JOIN `degrees`  ON `courses` . `degree_id` = `degrees`.`id`
JOIN `departments`  ON `degrees` . `department_id` = `departments`.`id`
WHERE `departments` . `name` = 'Dipartimento di Matematica'
ORDER BY `teachers` . `name`;



7. BONUS: Selezionare per ogni studente quanti tentativi d’esame ha sostenuto per
superare ciascuno dei suoi esam