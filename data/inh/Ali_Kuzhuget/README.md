# Данные для языка `inh` от вендора Ali Kuzhuget

## raw/
Содержит монокорпуса различных размеров:
- inh_mono_319K.txt => https://huggingface.co/datasets/parchiev/ingush-russian/sql-console/F_R4Lsu


## stats/
Один файл inh_population.csv со столбцами:
- year
- total_speakers_global
- total_speakers_rf
- source_name
- source_url

## keyboard/
JSON‑файлы с вариантами раскладок:
- inh_key_default.json

## frequencies/
- inh_monocorpus_freq.csv — частотности символов.

## mapping/
- inh_key_mapping.json — маппинг расширенных букв на русские клавиши.

## metadata.json
Обязательные поля: version, vendor, source, date_collected, contact, description.
Допускаются дополнительные поля.

---  
**Подсказка:** можно добавлять аудиоданные, фонетику, примеры предложений, графики и др.


## Код для подсчета частотного алфавита

```sql
WITH raw_text AS (
  SELECT UPPER(gh) AS text
  FROM train
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
      '((АЬ)|(ЯЬ)|(ГӀ)|(КХ)|(КЪ)|(КӀ)|(ПӀ)|(ТӀ)|(ХЬ)|(ХӀ)|(ЦӀ)|(ЧӀ)|[АБВГДЕЁЖЗИЙКЛМНОПРСТУФХШЩЪЫЬЭЮЯӀ])'
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