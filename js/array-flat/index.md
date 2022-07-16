---
title: "`.flat()`"
description: "Массив в массиве, в массиве, в массиве. А можно попроще? Превращает многомерный массив в плоский, одномерный."
authors:
  - agarkov
related:
  - js/arrays
  - js/number
  - js/recursion
tags:
  - doka
---

## Кратко

Метод `flat()` возвращает новый массив и уменьшает вложенность массива на заданное количество уровней.

## Пример

У нас есть массив с тремя уровнями вложенности:

```js
const nested = [
  'первый уровень',
  'первый уровень',
  [
    'второй уровень',
    'второй уровень',
    [
      'третий уровень',
      'третий уровень'
    ]
  ]
]
```

Вызовем метод `flat()` без аргументов:

```js
const flat = nested.flat()
console.log(flat)
```

Увидим что получившийся массив стал менее вложенным:

```js
[
  'первый уровень',
  'первый уровень',
  'второй уровень',
  'второй уровень',
  [
    'третий уровень',
    'третий уровень'
  ]
]
```

## Как пишется

Метод принимает необязательный аргумент `depth` — количество уровней, на которые нужно уменьшить вложенность. Значение по умолчанию — 1.

Результатом вызова метода `flat()` будет новый массив меньшей вложенности.

## Как это понять

Если массив содержит другие массивы в качестве своих элементов, то метод `flat()` позволяет уменьшить вложенность, вплоть до полного превращения массива в плоский.

### Если вложенность неизвестна

Если вложенность неизвестна, но нужно получить из массива с вложенными элементами плоский массив, то передайте аргумент `Infinity`. Тогда метод [рекурсивно](/js/recursion/) обойдёт массив и сделает на его основе новый плоский.

Возьмём массив с тремя уровнями вложенности:

```js
const nested = [
  'первый уровень',
  'первый уровень',
  [
    'второй уровень',
    'второй уровень',
    [
      'третий уровень',
      'третий уровень',
      [
        'четвертый уровень',
        'четвертый уровень'
      ]
    ]
  ]
]
```

Вызовем метод `flat()` с аргументом `Infinity`:

```js
const flat = nested.flat(Infinity)
console.log(flat)
```

Тогда массив превратится в плоский:

```js
[
  'первый уровень',
  'первый уровень',
  'второй уровень',
  'второй уровень',
  'третий уровень',
  'третий уровень',
  'четвертый уровень',
  'четвертый уровень'
]
```