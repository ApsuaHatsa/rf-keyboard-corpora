# Данные для языка `ani` от вендора Ali Kuzhuget

## raw/
Содержит монокорпуса различных размеров:
- ani_mono_125K.txt

## stats/
Один файл ani_population.csv со столбцами:
- year
- total_speakers_global
- total_speakers_rf
- source_name
- source_url

## keyboard/
JSON‑файлы с вариантами раскладок:
- ani_key_default.json

## frequencies/
ani_monocorpus_freq.csv — частотности символов.

## mapping/
ani_key_mapping.json — маппинг расширенных букв на русские клавиши.

## metadata.json
Обязательные поля: version, source, date_collected, contact, description.
Допускаются дополнительные поля.

---  
**Подсказка:** можно добавлять аудиоданные, фонетику, примеры предложений, графики и др.

## Код для подсчета частот букв: 

```sql
WITH raw_text AS (
  SELECT UPPER(text) AS text
  FROM ani_cyrl_train
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
      '(ГӀ)|(ГЬ)|(ГЪ)|(ГЪӀ)|(ЖЪ)|(ЖЪӀ)|(КӀ)|(КЬ)|(КЪ)|(КЪӀ)|(ЛӀ)|(ЛЬ)|(ЛЪ)|(ЛЪӀ)|(ПӀ)|(ТӀ)|(ХӀ)|(ХЬ)|(ХЪ)|(ЦӀ)|(ЦЪӀ)|(ЧӀ)|(ЧЪӀ)|([АБВГДЕЁЖЗИЙКЛМНОПРСТУФХЦЧШЩЪЫЬЭЮЯӀ])'
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