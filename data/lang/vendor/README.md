# Данные для языка `lang` от вендора <Vendor>

## raw/
Содержит монокорпуса различных размеров (можно добавить любого размера, но описать количество в названии файла):
- lang_mono_100k.txt
- lang_mono_1M.txt
- lang_mono_10M.txt
- lang_mono_100M.txt
- lang_mono_1T.txt

Если у вас есть монокорпус в другом месте, то прямо внутри файла единственной строкой добавьте прямую ссылку. Лучше всего хранить открытый датасет в Huggingface.co, потому что там легко анализируется частоты букв)

## stats/
Один файл lang_population.csv со столбцами:
- year
- total_speakers_global
- total_speakers_rf
- source_name
- source_url

## keyboard/
JSON‑файлы с вариантами раскладок:
- lang_key_default.json (обязательно)
- lang_key_4rows.json
- lang_key_complex.json

## frequencies/
lang_monocorpus_freq.csv — частотности символов.

## mapping/
lang_key_mapping.json — маппинг расширенных букв на русские клавиши.
lang_key_mapping_extension.json – маппинг расширенных букв и **символов** на русские клавиши, **не обязательно**.

## metadata.json
Обязательные поля: version, vendor, source, date_collected, contact, description.
Допускаются дополнительные поля.

---  
**Подсказка:** можно добавлять аудиоданные, фонетику, примеры предложений, графики и др.
