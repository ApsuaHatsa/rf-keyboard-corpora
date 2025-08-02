# Данные для языка `uzb` от вендора Ali Kuzhuget

## raw/
Содержит монокорпуса различных размеров:
- uzb_mono_175M.txt => https://huggingface.co/datasets/Agisight/uzb_data/sql-console/Q-u3gwh


## stats/
Один файл uzb_population.csv со столбцами:
- year
- total_speakers_global
- total_speakers_rf
- source_name
- source_url

## keyboard/
JSON‑файлы с вариантами раскладок:
- uzb_key_default.json

## frequencies/
- uzb_monocorpus_freq.csv — частотности символов.

## mapping/
- uzb_key_mapping.json — маппинг расширенных букв на русские клавиши.

## metadata.json
Обязательные поля: version, vendor, source, date_collected, contact, description.
Допускаются дополнительные поля.

---  
**Подсказка:** можно добавлять аудиоданные, фонетику, примеры предложений, графики и др.


## Код для подсчета частотного алфавита для Узбекского языка

```sql
WITH raw AS (
  SELECT UPPER(text) AS txt
  FROM train
),
ex AS (
  SELECT
    unnest(
      regexp_extract_all(
        regexp_replace(txt, '[1]', '1', 'g'),
        '([АБВГҒДЕЁЖЗИЙКҚЛМНОПРСТУЎФХҲЦЧШЩЪЬЭЮЯ])'
      )
    ) AS letter
  FROM raw
)
SELECT
  letter,
  COUNT(*)            AS frequency,
  ROUND(
    COUNT(*) * 100.0 /
    SUM(COUNT(*)) OVER (), 
    4
  )                    AS percent
FROM ex
GROUP BY letter
ORDER BY frequency DESC
;

```