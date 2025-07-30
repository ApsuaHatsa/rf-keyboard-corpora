# Данные для языка `mhr` от вендора FU-lab

## raw/
Содержит монокорпуса различных размеров:
- mhr_mono_1M.txt

Если у вас есть монокорпус в другом месте, то прямо внутри файла единственной строкой добавьте прямую ссылку. Лучше всего хранить открытый датасет в Huggingface.co, потому что там легко анализируется частоты букв)

## stats/
Один файл mhr_population.csv со столбцами:
- year
- total_speakers_global
- total_speakers_rf
- source_name
- source_url

## keyboard/
JSON‑файлы с вариантами раскладок:
- mhr_key_default.json (не готово)

## frequencies/
- mhr_monocorpus_freq.csv — частотности символов.

## mapping/
- mhr_key_mapping.json — маппинг расширенных букв на русские клавиши.

## metadata.json
Обязательные поля: version, vendor, source, date_collected, contact, description.
Допускаются дополнительные поля.

---  
**Подсказка:** можно добавлять аудиоданные, фонетику, примеры предложений, графики и др.