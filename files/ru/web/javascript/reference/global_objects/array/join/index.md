---
title: Array.prototype.join()
slug: Web/JavaScript/Reference/Global_Objects/Array/join
tags:
  - Array
  - JavaScript
  - Method
  - Prototype
  - Reference
  - Массив
  - метод
translation_of: Web/JavaScript/Reference/Global_Objects/Array/join
---

{{JSRef("Global_Objects", "Array")}}

## Сводка

Метод **`join()`** объединяет все элементы массива (или [массивоподобного объекта](/ru/docs/Web/JavaScript/Guide/Indexed_collections#Working_with_array-like_objects)) в строку.

{{EmbedInteractiveExample("pages/js/array-join.html")}}

## Синтаксис

```
arr.join([separator])
```

### Параметры

- `separator` {{optional_inline}}
  - : Определяет строку, разделяющую элементы массива. В случае необходимости тип разделителя приводится к типу Строка. Если он не задан, элементы массива разделяются запятой '**,**'. Если разделитель - пустая строка, элементы массива ничем не разделяются в возвращаемой строке.

### Возвращаемое значение

Строка, содержащая все элементы массива. Если _`arr.length`_ == `0`, то будет возвращена пустая строка.

## Описание

Преобразует все элементы массива в строки и объединяет их в одну большую строку. Элемент массива с типом `undefined` или `null` преобразуется в пустую строку.

## Примеры

### Соединение массива четырьмя различными способами

В следующем примере создаётся массив `a` с тремя элементами, затем они четыре раза объединяются в строку: с использованием разделителя по умолчанию, запятой с пробелом, плюса, окружённого пробелами, и пустой строки.

```js
var a = ['Ветер', 'Дождь', 'Огонь'];
var myVar1 = a.join();      // присвоит 'Ветер,Дождь,Огонь' переменной myVar1
var myVar2 = a.join(', ');  // присвоит 'Ветер, Дождь, Огонь' переменной myVar2
var myVar3 = a.join(' + '); // присвоит 'Ветер + Дождь + Огонь' переменной myVar3
var myVar4 = a.join('');    // присвоит 'ВетерДождьОгонь' переменной myVar4
```

### Соединение элементов массивоподобного объекта

В следующем примере соединяется массивоподобный объект (в данном случае список [аргументов](/ru/docs/Web/JavaScript/Reference/Functions/arguments) функции) с использованием вызова {{jsxref("Function.prototype.call")}} `для Array.prototype.join`.

```js
function f(a, b, c) {
  var s = Array.prototype.join.call(arguments);
  console.log(s); // '1,a,true'
}
f(1, 'a', true);
```

## Спецификации

{{Specifications}}

## Совместимость с браузерами

{{Compat}}

## Смотрите также

- {{jsxref("String.prototype.split()")}}
- {{jsxref("Array.prototype.toString()")}}
- {{jsxref("TypedArray.prototype.join()")}}