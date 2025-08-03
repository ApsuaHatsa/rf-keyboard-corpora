# Данные для языка `bua` от вендора Sarana Abidueva

## raw/
Содержит монокорпуса различных размеров:
- bua_mono_291k.txt

## stats/
Один файл bua_population.csv со столбцами:
- year
- total_speakers_global
- total_speakers_rf
- source_name
- source_url

## keyboard/
-

## frequencies/
bua_monocorpus_frequency.csv — частотности символов.

## mapping/
bua_key_mapping.json — маппинг расширенных букв на русские клавиши.

## metadata.json
Обязательные поля: version, source, date_collected, contact, description.
Допускаются дополнительные поля.

---  
**Подсказка:** можно добавлять аудиоданные, фонетику, примеры предложений, графики и др.

## Код для подсчета частот

```python
from datasets import load_dataset
import pandas as pd
import re
from collections import Counter

access_token = '...' # hugging face token

ds_bua_rus = load_dataset('buryat-translation/buryat_russian_parallel_corpus')
ds_bua_mono = load_dataset("buryat-translation/buryat_monocorpus")
bua_culturax = load_dataset("uonlp/CulturaX", 'bxr', token=access_token)  # requires access, just fill in survey
bxr_wiki = load_dataset("wikimedia/wikipedia", "20231101.bxr")
bxr_glot = load_dataset("cis-lmu/GlotCC-V1", "bxr-Cyrl")

bua_mono_set = set(ds_bua_mono['train']['text'])
bua_mono_set = bua_mono_set.union(set(ds_bua_rus['train']['bxr']))
bua_mono_set = bua_mono_set.union(set(bua_culturax['train']['text']))
bua_mono_set = bua_mono_set.union(set(bxr_wiki['train']['text']))
bua_mono_set = bua_mono_set.union(set(bxr_glot['train']['content']))
print(len(bua_mono_set))


all_text = ' '.join(bua_mono_set).upper().replace('H', 'Һ')

# Извлекаем только кириллические буквы бурятского алфавита
raw_extracted = re.findall(r'[А-ЯЁҺһҮүӨө]', all_text)
unique_letters_in_data = sorted(set(raw_extracted))

# Считаем
freq_counter = Counter(raw_extracted)
total_chars = sum(freq_counter.values())
# В pandas
result_df = pd.DataFrame([
    {
        'letter': letter,
        'frequency': freq_counter[letter],
        'percent': round((freq_counter[letter] * 100.0) / total_chars, 4)
    }
    for letter in unique_letters_in_data
])
result_df = result_df.sort_values(by='frequency', ascending=False).reset_index(drop=True)

output_file = 'bua_monocorpus_frequency.csv'
result_df.to_csv(output_file, index=False, encoding='utf-8')
```