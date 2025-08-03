# Данные для языка `sah` от вендора Sargy_A

## raw/
Содержит монокорпуса различных размеров:
- sah_mono_231M.txt

## stats/
Один файл sah_population.csv со столбцами:
- year
- total_speakers_global
- total_speakers_rf
- source_name
- source_url

## keyboard/
JSON‑файлы с вариантами раскладок:
- sah_key_default.json
- sah_key_4rows.json
- sah_key_complex.json

## frequencies/
sah_monocorpus_freq.csv — частотности символов.

## mapping/
sah_key_mapping.json — маппинг расширенных букв на русские клавиши.

## metadata.json
Обязательные поля: version, source, date_collected, contact, description.
Допускаются дополнительные поля.

---  
**Подсказка:** можно добавлять аудиоданные, фонетику, примеры предложений, графики и др.

## Код для подсчета частот

```sql
WITH raw_text AS (
  SELECT UPPER(text) AS text
  FROM sah_cyrl_train
),
normalized_text AS (
  SELECT
    regexp_replace(text, '[I1l|]', 'Ӏ', 'g') AS norm_text
  FROM raw_text
),
extracted_letters AS (
  SELECT
    regexp_extract_all(
      norm_text,
      '([АБВГҔДДьЕЁЖЗИЙКЛМНҤНьОӨПРСҺТУҮФХЦЧШЩъЫьЭЮЯ])'
    ) AS letter
  FROM normalized_text
),
flattened AS (
  SELECT unnest(letter) AS letter
  FROM extracted_letters
),
grouped AS (
  SELECT
    letter,
    COUNT(*) AS frequency
  FROM flattened
  GROUP BY letter
),
total_count AS (
  SELECT SUM(frequency) AS total_chars
  FROM grouped
)
SELECT
  letter,
  frequency,
  ROUND((frequency * 100.0) / total_chars, 4) AS percent
FROM grouped
CROSS JOIN total_count
ORDER BY frequency DESC;
```