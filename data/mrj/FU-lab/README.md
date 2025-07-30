# Данные для языка `mrj` от вендора FU-lab

## raw/
Содержит монокорпуса различных размеров:
- mrj_mono_5.7M.txt

Если у вас есть монокорпус в другом месте, то прямо внутри файла единственной строкой добавьте прямую ссылку. Лучше всего хранить открытый датасет в Huggingface.co, потому что там легко анализируется частоты букв)

## stats/
Один файл mrj_population.csv со столбцами:
- year
- total_speakers_global
- total_speakers_rf
- source_name
- source_url

## keyboard/
JSON‑файлы с вариантами раскладок:
- mrj_key_default.json (не готово)

## frequencies/
- mrj_monocorpus_freq.csv — частотности символов.

## mapping/
- mrj_key_mapping.json — маппинг расширенных букв на русские клавиши.

## metadata.json
Обязательные поля: version, vendor, source, date_collected, contact, description.
Допускаются дополнительные поля.

---  
**Подсказка:** можно добавлять аудиоданные, фонетику, примеры предложений, графики и др.