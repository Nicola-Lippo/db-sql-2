/*GRUP BY*/
1. Contare quanti iscritti ci sono stati ogni anno
SELECT
    YEAR(`enrolment_date`) AS `year_inscription`,
    COUNT(*) AS `number_inscription`
FROM
    `students`
GROUP BY
    YEAR(`enrolment_date`)
*********************
2. Contare gli insegnanti che hanno l'ufficio nello stesso edificio
SELECT
    `office_address`,
    COUNT(`id`) AS `number_teachers`
FROM
    `teachers`
GROUP BY
    `office_address`
*********************
3. Calcolare la media dei voti di ogni appello d'esame
//ROUND: Arrotonda un numero, in numero dopo indica di quanto dopo la ,
//AVG: Restituisce il valore medio di un'espressione.
SELECT
    `exam_id`,
    ROUND(AVG(`vote`),
    2) AS `media_vote`
FROM
    `exam_student`
GROUP BY
    `exam_id`
*********************
4. Contare quanti corsi di laurea ci sono per ogni dipartimento
SELECT
    `department_id`,
    //NO * dentro ()
    COUNT(`id`) AS `number_courses`
FROM
    `degrees`
GROUP BY
    `department_id`
ORDER BY
    `department_id`


/*JOIN*/
1. Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia
SELECT
    `students`.`name`,
    `students`.`surname`,
    `degrees`.`name`
FROM
    `degrees`
INNER JOIN `students` ON `degrees`.`id` = `students`.`degree_id`
WHERE
    `degrees`.`name` = 'Corso di Laurea in Economia'
*********************
2. Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze
SELECT
    `degrees`.`level`,
    `departments`.`name`,
    `degrees`.`name`
FROM
    `departments`
INNER JOIN `degrees` ON `departments`.`id` = `degrees`.`department_id`
WHERE
    `departments`.`name` LIKE '%Neuroscienze'
*********************
3. Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)
*********************
4. Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome
*********************
5. Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti
*********************
6. Selezionare tutti i docenti che insegnano nel Dipartimento di
Matematica (54)
*********************
7. BONUS: Selezionare per ogni studente il numero di tentativi sostenuti
per ogni esame, stampando anche il voto massimo. Successivamente,
filtrare i tentativi con voto minimo 18.