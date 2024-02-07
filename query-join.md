1. Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia
    SELECT `students`.`name`, `students`.`surname`, `degrees`.`name` AS `degrees_name`
    FROM `students` 
    INNER JOIN `degrees`
    ON `students`.`degree_id` = `degrees`.`id`
    WHERE `degrees`.`name` LIKE 'Corso di Laurea in Economia';

2. Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze
    SELECT `degrees`.`name` AS `degree_name`, `degrees`.`level`, `degrees`.`address`,`departments`.`name` AS `department_name`
    FROM `degrees` 
    INNER JOIN `departments`
    ON `degrees`.`department_id` = `departments`.`id`
    WHERE `departments`.`name` LIKE 'Dipartimento di Neuroscienze' AND `degrees`.`name` LIKE 'Corso di Laurea Magistrale%';

3. Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)
    SELECT `courses`.`name`, `courses`.`description`
    FROM `courses` 
    INNER JOIN `course_teacher`
    ON `course_teacher`.`course_id` = `courses`.`id` AND `course_teacher`.`teacher_id` = '44';

4. Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui
sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e
nome
    SELECT `students`.`name`, `students`.`surname`, `degrees`.`name` AS `corso_di_laurea`, `departments`.`name` AS `department_name`
    FROM `students` 
    INNER JOIN `degrees`
    ON `students`.`degree_id` = `degrees`.`id`
    INNER JOIN `departments`
    ON `degrees`.`department_id` = `departments`.`id`
    ORDER BY `students`.`name`, `students`.`surname` ASC;

5. Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti
    SELECT `degrees`.`name` AS `degrees_name`, `courses`.`name` AS `course_name`, `teachers`.`name` AS `teacher_name`, `teachers`.`surname` AS `teacher_surname`
    FROM `degrees` 
    INNER JOIN `courses`
    ON `courses`.`degree_id` = `degrees`.`id`
    INNER JOIN `course_teacher`
    ON `course_teacher`.`course_id` = `courses`.`id`
    INNER JOIN `teachers`
    ON `course_teacher`.`teacher_id` = `teachers`.`id`;

6. Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54)
    SELECT DISTINCT(`teachers`.`id`), `teachers`.`name` AS `teacher_name`, `teachers`.`surname` AS `teacher_surname`, `departments`.`name` AS `department_name`
    FROM `teachers`
    INNER JOIN `course_teacher`
    ON `course_teacher`.`teacher_id` = `teachers`.`id`
    INNER JOIN `courses`
    ON `course_teacher`.`course_id` = `courses`.`id`
    INNER JOIN `degrees`
    ON `courses`.`degree_id` = `degrees`.`id`
    INNER JOIN `departments`
    ON `degrees`.`department_id` = `departments`.`id`
    WHERE `departments`.`name` LIKE 'Dipartimento di Matematica';

7. BONUS: Selezionare per ogni studente il numero di tentativi sostenuti
per ogni esame, stampando anche il voto massimo. Successivamente,
filtrare i tentativi con voto minimo 18.
    SELECT  `students`.`name`, `students`.`surname`, `exam_student`.*, `exams`.`course_id`, COUNT(`exam_student`.`exam_id`) AS `esami`, MAX(`exam_student`.`vote`) AS `max_vote` 
    FROM `exam_student`
    INNER JOIN `students`
    ON `exam_student`.`student_id` = `students`.`id`
    INNER JOIN `exams`
    ON `exam_student`.`exam_id` = `exams`.`id`
    GROUP BY `exams`.`course_id`, `students`.`id`
    HAVING `exam_student`.`vote` < 18;