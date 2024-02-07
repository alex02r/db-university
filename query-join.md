1. Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia
    SELECT `students`.`name`, `students`.`surname`, `degrees`.`name` AS `degrees_name`
    FROM `students` 
    INNER JOIN `degrees`
    ON `students`.`degree_id` = `degrees`.`id`
    WHERE `degrees`.`name` LIKE 'Corso di Laurea in Economia';

