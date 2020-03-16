# Kirill Mikhailov
## Contacts
email: [mikhailau.kiryl@gmail.com](mailto:mikhailau.kiryl@gmail.com)  
phone: [+375 (44) 575-25-01](tel:+375445752501)
## Summary
I like to learn something new and keep my technical level up to par with developers.
Now I work as a project manager, and web development is a hobby for me.
In general, I want to learn js in order to use cooler things in my projects, or maybe even to implement some useful online service that everyone could use, and I proudly add it to my resume line.
## Skills
* python
* web server
* html
* css
* js
* project managment

## Code example

An example of my code that parses data from a price list, and then replaces the part numbers in it from a file containing replacement rules, and the code independently processes exceptions by replacing it with regular expressions according to a given rule.  

```python
import pandas as pd
import xml.etree.ElementTree as ET

# файл с прайсом
filename = 'pricelist.csv'
# файл для замены артикулов Brand1
tree = ET.parse('replace_rules.xml')
root = tree.getroot()
# словарь по которому будет определяться соответсвие между артикулами
replacement_dict = {}
# парсим данные из файла во фрейм
df = pd.read_csv(filename, sep=';', quotechar='\"')
# приводим поле актикул к тексту, чтобы не потерять нули впереди и избежать конвертации числа из-за символа "E"
df.ARTIKUL.astype('str')
# проходим по всем вариантам замены из файла и формируем словарь, по которому будет подстановка
for replacement in root.iter('Replacement'):
    finding_var = replacement.attrib['Find']
    replacement_dict[finding_var] = replacement.attrib['ReplaceWith']
# фильтруем список всех позиций по полю Бренд и значению Brand1
bosch_filtered = df[df.BRAND == 'Brand1']
# выполняем замену значений поля Артикул в соответствии со словарем подстановки
second_slice = bosch_filtered.ARTIKUL.replace(replacement_dict)
# обрабатываем оставшиеся не соотнесенные по словарю пункты согласно правилу (1 символ . 3 символа . 3 символа . 3 символа )
third = bosch_filtered.ARTIKUL.replace(r'^(.{1})(.{3})(.{3})(.{3})$', r'\1.\2.\3.\4', regex=True)
# Обновляем список по значения среза с замененными значениями
df.update(third)
# удаляем пустые значения после объединения
df.dropna(subset=['ARTIKUL'], inplace=True)
# эта строчка формирует выгрузку в кодировке для импорта на сайт
df.to_csv('price_complited.csv', sep=';')

```

## Experience
My latest projects:
* [mahc.by](https://mahc.by)
* [hashtag.by](https://hashtag.by)
* [itconsult.by](https://itconsult.by)

## Education

### Stepik
[Python basic](https://stepik.org/cert/34680)  
[Python development](https://stepik.org/cert/30197)  
[Web-technologies](https://stepik.org/cert/40195)  

### Codeacedemy
[My profile](https://www.codecademy.com/profiles/IL1ne)

### Codewars
[My profile](https://www.codewars.com/users/IL1ne)

## English
My English Level A2  
I read technical documentation, stackoverflow posts and I understand speech quite well, but can't speak without same practice.