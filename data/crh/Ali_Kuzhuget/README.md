# Данные для языка `crh` от вендора Ali Kuzhuget

## raw/
Содержит монокорпуса различных размеров (можно добавить любого размера, но описать количество в названии файла):
- crh_mono_1M.txt

Если у вас есть монокорпус в другом месте, то прямо внутри файла единственной строкой добавьте прямую ссылку. Лучше всего хранить открытый датасет в Huggingface.co, потому что там легко анализируется частоты букв)

## stats/
Один файл crh_population.csv со столбцами:
- year
- total_speakers_global
- total_speakers_rf
- source_name
- source_url

## keyboard/
JSON‑файлы с вариантами раскладок:
- crh_key_default.json

## frequencies/
- crh_monocorpus_freq.csv — частотности символов.

## mapping/
- crh_key_mapping.json — маппинг расширенных букв на русские клавиши.

## metadata.json
Обязательные поля: version, vendor, source, date_collected, contact, description.
Допускаются дополнительные поля.

---  
**Подсказка:** можно добавлять аудиоданные, фонетику, примеры предложений, графики и др.