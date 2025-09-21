# Задание 1. Шифр Цезаря

Задаем российский алфавит как константу:


```python
ALPHABET = 'абвгдеёжзийклмнопрстуфхцчшщъыьэюя'
```

Код для шифра Цезаря:


```python
# вводим ключ
k = int(input())

if 0 > k:  # обработка ошибок для случая когда ключ меньше нуля
    raise(ValueError('k must be more then 0 in Russian alphabet!'))
if len(ALPHABET) < k:  # обработка ошибок для случая, когда ключ больше, чем длинна алфавита
    raise(ValueError('k must be less then 32 in Russian alphabet!'))
# составление маппера
cypher = {orig: cyph for orig, cyph in zip(ALPHABET, ALPHABET[k:] + ALPHABET[:k])}

# ввод сообщения
message = input().replace(' ', '').lower()
if all(map(lambda x: x not in ALPHABET + ' ', message)):  # проверка на допустимые элементы сообщения
    raise(ValueError('Message symbols must be from alphabet or space!'))

# вывод:
print(f'Ключ:\t{k}')
print(f'Сообщение для шифрования:\t{message}')
print(f'Зашифрованное сообщение:\t{''.join(map(lambda x: cypher[x], message))}')
```

    Ключ:	28
    Сообщение для шифрования:	яхорошопокушалсутра
    Зашифрованное сообщение:	ърйлйуйкйёоуыжмонлы
    

___
# Задание 2. Шифр Атбаш

Код для шифра Атбаш:


```python
# составления маппера
cypher = {orig: cyph for orig, cyph in zip(ALPHABET + " ", (ALPHABET + " ")[::-1])}

# ввод сообщения
message = input().lower()
if all(map(lambda x: x not in ALPHABET + ' ', message)):  # проверка на допустимые значения
    raise(ValueError('Message symbols must be from alphabet or space!'))

# вывод:
print(f'Сообщение для шифрования:\t{message}')
print(f'Зашифрованное сообщение:\t{''.join(map(lambda x: cypher[x], message))}')
```

    Сообщение для шифрования:	я сегодня также хорошо покушал и в обед
    Зашифрованное сообщение:	баоыэсьтбан хщыакспсзсарсхмз фачаюасяыь
    
