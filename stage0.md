# Конструкции

* [Фильтры](https://github.com/liquid-hub/insales-liquid-examples/blob/master/stage0.md#Фильтры)
* [Создание переменных](https://github.com/liquid-hub/insales-liquid-examples/blob/master/stage0.md#Создание-переменных)
* [Операторы сравнения](https://github.com/liquid-hub/insales-liquid-examples/blob/master/stage0.md#Операторы-сравнения)
* [Комментарии](https://github.com/liquid-hub/insales-liquid-examples/blob/master/stage0.md#Комментарии)
* [Цикл For](https://github.com/liquid-hub/insales-liquid-examples/blob/master/stage0.md#Цикл-For)
* [Чередование Cycle](https://github.com/liquid-hub/insales-liquid-examples/blob/master/stage0.md#Чередование-Cycle)
* [Include](https://github.com/liquid-hub/insales-liquid-examples/blob/master/stage0.md#Include)

В шаблонизаторе есть 2 основные кострукции:

> {{ code }} - вывод информации

> {% code %} - методы и теги

## Фильтры

Фильтры преобразовывают выходные данные

```twig
Привет, {{ name | upcase }}! => Привет, ПОЛЬЗОВАТЕЛЬ!
{{ 'sales' | append: '.jpg' }} => sales.jpg
```

## Создание переменных

```twig
{% assign new_var = 'Строка' %}
{{ new_var }} => Строка
{% assign new_var = 'СТРОКА' | downcase  %}
{{ new_var }} => строка
```

## Операторы сравнения

```twig
{% assign product_price = 10 %}
{% assign product_title = 'Телефон' %}
{% if product_price > 9 %}
  Дороже 9
  {% else %}
  Дешевле или равно 9
{% endif %}

{% unless product_title contains 'Телефон' %}
  Это не телефон
  {% else %}
  Это телефон  
{% endunless %}
```

## Комментарии

```twig
{% comment %} закомментированный текст {% endcomment %}
```

## Чередование Cycle

```twig
{% cycle 'odd', 'even' %}<br />
{% cycle 'odd', 'even' %}<br />
{% cycle 'odd', 'even' %}<br />
{% cycle 'odd', 'even' %}

odd
even
odd
even
```

## Цикл For

```twig
{% for item in array %}
  {{ item }}
{% endfor %}
```
> При обходе массива доступны дополнительные переменные:

```
forloop.length      # => количество элементов в массиве
forloop.index       # => номер текущей итерации
forloop.index0      # => номер текущей итерации (считая от нуля)
forloop.rindex      # => сколько элементов осталось
forloop.rindex0     # => сколько элементов осталось (считая от нуля)
forloop.first       # => первая итерация?
forloop.last        # => последняя итерация?
```

## Include
Тег include позволяет вставлять сниппеты шаблона в произвольные места лайаута, шаблонов и других сниппетов.

```twig
{% include 'head' %}
{% include 'header' %}
При включении сниппета можно передать параметры через запятую
{% include 'footer', show_phone: true %}
```

[<< Назад](https://github.com/liquid-hub/insales-liquid-examples/blob/master/readme.md)
