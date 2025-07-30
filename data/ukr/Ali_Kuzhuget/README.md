# Данные для языка `ukr` от вендора Ali Kuzhuget

## raw/
Содержит монокорпуса различных размеров:
- ukr_mono_384M.txt

## stats/
Один файл ukr_population.csv со столбцами:
- year
- total_speakers_global
- total_speakers_rf
- source_name
- source_url

## keyboard/
JSON‑файлы с вариантами раскладок:
- ukr_key_default.json (уже есть в iOS)

## frequencies/
- ukr_monocorpus_freq.csv — частотности символов.

## mapping/
- ukr_key_mapping.json — маппинг расширенных букв на русские клавиши.

## metadata.json
Обязательные поля: version, vendor, source, date_collected, contact, description.
Допускаются дополнительные поля.

---  
**Подсказка:** можно добавлять аудиоданные, фонетику, примеры предложений, графики и др.