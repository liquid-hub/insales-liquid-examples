# Синтаксис и переменные liquid


## Синтаксис

В шаблонизаторе есть 2 кострукции:

> {{ code }} - вывод информации

> {% code %} - методы и теги


## Типы переменных

### Строки

> Строками могут быть текстовые поля бэк-офиса, поля содержащие html разметку, поля типа `select` и так далее.

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
