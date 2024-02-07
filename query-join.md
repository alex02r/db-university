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

