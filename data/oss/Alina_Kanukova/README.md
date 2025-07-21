# Данные для языка `oss` от вендора Alina Kanukova

## raw/
Содержит монокорпус на 100К символов:
- oss_mono_100k.txt

## stats/
Один файл oss_population.csv со столбцами:
- year
- total_speakers_global
- total_speakers_rf
- source_name
- source_url

## keyboard/
JSON‑файлы с вариантами раскладок: (Нет данных)
- oss_key_default.json (обязательно)
- oss_key_4rows.json
- oss_key_complex.json

## frequencies/
- oss_monocorpus_freq.csv — частотности символов.

## mapping/
- oss_key_mapping.json — маппинг расширенных букв на русские клавиши. (Нет данных)
- oss_key_mapping_extension.json – маппинг расширенных букв и **символов** на русские клавиши, **не обязательно**.

## metadata.json
Обязательные поля: version, vendor, source, date_collected, contact, description.
Допускаются дополнительные поля.

---  
**Подсказка:** можно добавлять аудиоданные, фонетику, примеры предложений, графики и др.
