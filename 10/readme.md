базовый код для нахождения слов:

import re

with open('11.txt', encoding='utf-8') as f:
    s = f.read()
result = re.findall(r'\w*ум\w*', s)      #если нужно без учета регистра то добавляем  flags=re.IGNORECASE   
print(len(result))
print(result)
