Код для анализа частот букв (Частотный алфавит) на монокорпусе: 
– имя таблицы – train
– имя столбца – text
– список букв языка представлен в виде [АӘБВГҒДЕЁЖЗИЙКҚЛМНҢОӨПРСТУҰҮФХҺЦЧШЩЪЫІЬЭЮЯ]. Для некоторых СевКав языков парные буквы нужно сначала собрать, по ним собрать категорию для посчета их, а потом применять категоризацию букв в тексте.

  
```
WITH raw_text AS (
  SELECT UPPER(text) AS text FROM train
),
normalized_text AS (
  SELECT
    regexp_replace(text, '[1]', '1', 'g') AS norm_text
  FROM raw_text
),
extracted_letters AS (
  SELECT
    regexp_extract_all(
      norm_text,
      '([АӘБВГҒДЕЁЖЗИЙКҚЛМНҢОӨПРСТУҰҮФХҺЦЧШЩЪЫІЬЭЮЯ])'
    ) AS letter
  FROM normalized_text
),
flattened AS (
  SELECT unnest(letter) AS letter FROM extracted_letters
),
grouped AS (
  SELECT letter, COUNT(*) AS frequency
  FROM flattened
  GROUP BY letter
),
total_count AS (
  SELECT SUM(frequency) AS total_chars FROM grouped
)
SELECT 
  letter,
  frequency,
  ROUND((frequency * 100.0) / total_chars, 4) AS percent
FROM grouped, total_count
ORDER BY frequency DESC;
```
