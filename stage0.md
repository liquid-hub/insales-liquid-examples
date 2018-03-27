# Синтаксис и переменные liquid

* [Строки](https://github.com/liquid-hub/insales-liquid-examples/blob/master/stage0.md#%D0%A1%D1%82%D1%80%D0%BE%D0%BA%D0%B8)
* [Числа](https://github.com/liquid-hub/insales-liquid-examples/blob/master/stage0.md#Числа)
* [Объекты](https://github.com/liquid-hub/insales-liquid-examples/blob/master/stage0.md#Объекты)
* [Массивы](https://github.com/liquid-hub/insales-liquid-examples/blob/master/stage0.md#Массивы)
* [Булевые](https://github.com/liquid-hub/insales-liquid-examples/blob/master/stage0.md#Булевые)

## Синтаксис

В шаблонизаторе есть 2 кострукции:

> {{ code }} - вывод информации

> {% code %} - методы и теги


## Типы переменных

### Строки

> Строками могут быть текстовые поля бэк-офиса, поля содержащие html разметку, поля типа `select` и так далее.

> [Строки в списке отмечены лейблами - string,html](http://liquidhub.ru/collection/shpargalka-liquid)

```twig
{{ title }} - название магазина

{{ page.title }} - название страницы

{{ product.title }} - название продукта

{{ product.first_image.medium_url }} - ссылка изображение

{% assign string_variable = 'Переменная с текстом' %}

{{ string_variable }} - Локальная переменная

```

> Строки можно приводить к числам.

```twig
{% assign number = 220 %}
{% assign string_number = '239' | times: 1 %}
{% if string_number > number %}
  Строка умноженная на 1 приводится к числу.
  Данный код отработает
{% endif %}

{% assign string_number2 = '239' %}
{% if string_number2 > number %}
  Код выдаст ошибку при сравнении строки с числом.
{% endif %}
```

> Из строки можно создать массив.

```twig
{% assign string_for_array = '1|2|3|4' | split: '|' %}

{% for i in string_for_array %}
  {{ i }}
{% endfor %}
=> 1 2 3 4

{% comment %}page.url = page/contacts{% endcomment %}
{% assign page_handle = page.url | split: '/' | last %}
{{ page_handle }}
=> contacts
```

> К строке можно применить фильтр или метод size, таким образом можно проверить строку на пустоту

```twig
{% assign new_string = '' %}

{% if new_string == '' %}
  Строка пуста
{% endif %}

{% if new_string.size == 0 %}
  Строка пуста
{% endif %}
```

### Числа

Числами могут быть id, цены, количество и т.д.

Помимо математических операций числа можно подставлять в строки.

```twig
{% assign number = 2 %}
{{ number | plus: 2 }}
=> 4

{{ product.price | money }}
=> 1 000 руб.

{{ 2000 | money }}
=> 2 000 руб.

{{ product.price | money | prepend: 'Цена: ' }}
=> Цена: 1 000 руб.
```

### Объекты

Объекты это структура данных похожая на ассоциативные массивы. Значение объектов можно получить по ключу.

> Практически все выводимые из бэк-офиса данные заключаются в объекты. Например account, product, blog и т.д..

```twig
{{ объект.ключ.значение }}
{{ объект.ключ.ключ.значение }}

{{ account.phone }}
{{ product.title }}
{{ product.properties.handle.characteristics.first.name }}
```

> Объекты могут быть итерируемыми

```twig
{% for property in product.properties %}
  {{property.name}}: {% for item in property.characteristics %}{{item.name}},{% endfor %}
{% endfor %}
```
