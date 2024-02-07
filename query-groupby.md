1. Contare quanti iscritti ci sono stati ogni anno
    SELECT YEAR(`enrolment_date`), COUNT(`id`) AS `numero_iscritti` 
    FROM `students` 
    GROUP BY YEAR(`enrolment_date`);

2. Contare gli insegnanti che hanno l'ufficio nello stesso edificio
    SELECT `office_address` , COUNT(`id`) AS `numero_insegnanti`
    FROM `teachers` 
    GROUP BY `office_address`;

3. Calcolare la media dei voti di ogni appello d'esame
    SELECT `exam_id`, AVG(`vote`) AS `media_voti`
    FROM `exam_student` 
    GROUP BY `exam_id`;
