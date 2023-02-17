---
title: Комментарии
slug: Web/CSS/Comments
tags:
  - Beginner
  - CSS
  - CSS Reference
  - Комментарии
  - Новичку
  - Руководство
translation_of: Web/CSS/Comments
original_slug: Web/CSS/Тихий
---
{{CSSRef}}

## Описание

Комментарии используются для добавления поясняющих заметок или для того, чтобы предотвратить интеграцию части кода в браузер.

## Синтаксис

```css
/* Комментарий */
```

## Примеры

```css
/* Однострочный комментарий */

/*
Комментарий
который содержит
несколько
строк
*/
```

## Замечания

Данный `/* */` синтаксис комментария используется для обоих вариантов, и однострочного и многострочного комментария. Нет других способов добавить комментарий во внешнюю таблицу стилей. Также, когда используется элемент \<style>, вы можете использовать \<!-- -->, чтобы спрятать CSS от старых браузеров, но это не рекомендуется. Как и в большинстве языков программирования, которые используют синтаксис комментариев /\* \*/ , комментарии нельзя вкладывать друг в друга. Другими словами, данная часть синтаксиса \*/, которая следует за /\* закрывает комментарий.

## Спецификации

- [CSS 2.1 Синтаксис и базовые типы данных #комментарии](http://www.w3.org/TR/CSS21/syndata.html#comments)

## Смотрите также

- [Руководство по CSS](/ru/docs/Web/CSS/Reference)
- Ключевые концепции CSS
  - [Синтаксис CSS](/ru/docs/Web/CSS/Syntax)
  - [@-правила](/ru/docs/Web/CSS/At-rule)
  - [комментарии](/ru/docs/Web/CSS/Comments)
  - [специфичность](/ru/docs/Web/CSS/Specificity)
  - [наследование](/ru/docs/Web/CSS/inheritance)
  - [блочная модель](/ru/docs/Web/CSS/CSS_Box_Model/Introduction_to_the_CSS_box_model)
  - [режимы компоновки](/ru/docs/Web/CSS/Layout_mode)
  - [модели визуального форматирования](/ru/docs/Web/CSS/Visual_formatting_model)
  - [Схлопывание отступов](/ru/docs/Web/CSS/CSS_Box_Model/Mastering_margin_collapsing)
  - Значения
    - [начальные](/ru/docs/Web/CSS/initial_value)
    - [вычисленные](/ru/docs/Web/CSS/computed_value)
    - [используемые](/ru/docs/Web/CSS/used_value)
    - [действительные](/ru/docs/Web/CSS/actual_value)
  - [Синтаксис определения значений](/ru/docs/Web/CSS/Value_definition_syntax)
  - [Сокращённые свойства](/ru/docs/Web/CSS/Shorthand_properties)
  - [Замещаемые элементы](/ru/docs/Web/CSS/Replaced_element)