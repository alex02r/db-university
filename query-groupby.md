1. Contare quanti iscritti ci sono stati ogni anno
    SELECT YEAR(`enrolment_date`), COUNT(`id`) AS `numero_iscritti` 
    FROM `students` 
    GROUP BY YEAR(`enrolment_date`);
