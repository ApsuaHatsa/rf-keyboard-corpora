# Данные для Церковнославянского языка от [@Agisight](https://github.com/agisight)

## raw/
Содержит монокорпуса различных размеров:
- chu_mono_100k.txt

## stats/
Один файл chu_population.csv с информацией о числе носителей:
- year
- total_speakers_global
- total_speakers_rf
- source_name
- source_url

## frequencies/
chu_monocorpus_freq.csv — частотности символов (на основе nevmenandr/russian-old-orthography-ocr на **Hugging Face**). Анализ на HF: https://huggingface.co/datasets/nevmenandr/russian-old-orthography-ocr/sql-console/kPfhnda

## mapping/
chu_key_mapping.json — маппинг расширенных букв на русские клавиши из стандартной iOS клавиатуры.