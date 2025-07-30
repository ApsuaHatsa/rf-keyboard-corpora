# Данные для языка `kpt` от вендора Timbo Karatinets

## raw/
Содержит монокорпуса различных размеров (можно добавить любого размера, но описать количество в названии файла. Удалить лишние):
- kpt_mono_100k.txt

## stats/
Один файл kpt_population.csv со столбцами:
- year
- total_speakers_global
- total_speakers_rf
- source_name
- source_url

## keyboard/
JSON‑файлы с вариантами раскладок:
- kpt_key_default.json (вариант по умолчанию)

## frequencies/
- kpt_monocorpus_freq.csv — частотности символов.

## mapping/
- kpt_key_mapping.json — маппинг расширенных букв на русские клавиши.

## metadata.json
Обязательные поля: version, vendor, source, date_collected, contact, description.
Допускаются дополнительные поля.

---  
**Подсказка:** можно добавлять аудиоданные, фонетику, примеры предложений, графики и др.