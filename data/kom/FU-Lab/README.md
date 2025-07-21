# Данные для языка `kom` от вендора `FU-Lab`

## raw/
Содержит монокорпуса различных размеров (можно добавить любого размера, но описать количество в названии файла):
- kom_mono_100k.txt (Нет данных)
- kom_mono_1M.txt (Нет данных)
- kom_mono_10M.txt (Нет данных)
- kom_mono_100M.txt (Нет данных)
- kom_mono_1T.txt (Нет данных)

Если у вас есть монокорпус в другом месте, то прямо внутри файла единственной строкой добавьте прямую ссылку. Лучше всего хранить открытый датасет в Huggingface.co, потому что там легко анализируется частоты букв)

## stats/
Один файл lang_population.csv со столбцами (Не готов):
- year
- total_speakers_global
- total_speakers_rf
- source_name
- source_url

## keyboard/
JSON‑файлы с вариантами раскладок (Не готов):
- kom_key_default.json (обязательно)
- kom_key_4rows.json
- kom_key_complex.json

## frequencies/
- kom_monocorpus_freq.csv — частотности символов.

## mapping/
- kom_key_mapping.json (Не готов) — маппинг расширенных букв на русские клавиши.
- kom_key_mapping_extension.json – маппинг расширенных букв и **символов** на русские клавиши, **не обязательно**.

## metadata.json
Обязательные поля: version, vendor, source, date_collected, contact, description.
Допускаются дополнительные поля.

---  
**Подсказка:** можно добавлять аудиоданные, фонетику, примеры предложений, графики и др.
