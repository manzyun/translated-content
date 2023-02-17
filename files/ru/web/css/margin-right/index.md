---
title: margin-right
slug: Web/CSS/margin-right
translation_of: Web/CSS/margin-right
---

{{CSSRef}}

Свойство [CSS](/en/CSS) **`margin-right`** устанавливает [внешний отступ](/ru/docs/Web/CSS/box_model) справа от элемента. Положительное значение увеличивает расстояние между соседними элементами, тогда как отрицательное - сокращает.

{{EmbedInteractiveExample("pages/css/margin-right.html")}}

Вертикальные внешние отступы двух соседних блоков могут схлопнуться. Это называется [схлопыванием внешних отступов](/ru/docs/Web/CSS/CSS_Box_Model/Mastering_margin_collapsing).

## Синтаксис

```css
/* <lenght> значение */
margin-right: 20px;  /* абсолютная длина */
margin-right: 1em;   /* относительно размера текста */
margin-right: 5%;    /* относительно ширины родительского блока */

/* Значения-ключевые слова */
margin-right: auto;

/* Глобальные значения */
margin-right: inherit;
margin-right: initial;
margin-right: unset;
```

Свойство `margin-right` может быть выражено как ключевое слово `auto`, как `<число>`, или как `<процент>`. Значение может быть положительным, нулевым или отрицательным.

### Значения

- {{cssxref("&lt;length&gt;")}}
  - : Размер отступа - фиксированная величина.
- {{cssxref("&lt;percentage&gt;")}}
  - : Размер отступа в процентах - размер относительно длины родительского блока.
- `auto`
  - | : Внешний отступ слева получает долю неиспользованного горизонтального пространства, определяется в основном [выбранным способом разметки](/ru/docs/Web/CSS/%D0%A1%D0%BF%D0%BE%D1%81%D0%BE%D0%B1_%D1%80%D0%B0%D1%81%D0%BF%D0%BE%D0%BB%D0%BE%D0%B6%D0%B5%D0%BD%D0%B8%D1%8F). Если значения `margin-left` и `margin-right` одновременно установлены как `auto`, расчётное пространство распределяется равномерно. Эта таблица кратко излагает различные: | Значение {{cssxref("display")}} | Значение {{cssxref("float")}} | Значение {{cssxref("position")}}                                                                                                                                                                           | Расчётное значение `auto`                                                                                          | Комментарий |
    | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------- | ------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------ | ----------- |
    | `inline`, `inline-block`, `inline-table`                                                                                                                                                                                                                                                                                                                                                                                                               | _любое_                               | `static` или `relative`               | `0`                                                                                                                                                                                                                 | Строчный способ разметки                                                                                           |
    | `block`, `inline`, `inline-block`, `block`, `table`, `inline-table`, `list-item`, `table-caption`                                                                                                                                                                                                                                                                                                                                                      | _любое_                               | `static` или `relative`               | `0`, кроме случаев, когда `margin-left` и `margin-right` установлены как `auto`. В этом случае устанавливается значение, центрирующее элемент внутри его родителя                                                   | Блочный способ разметки                                                                                            |
    | `block`, `inline`, `inline-block`, `block`, `table`, `inline-table`, `list-item`, `table-caption`                                                                                                                                                                                                                                                                                                                                                      | `left` или `right`                    | `static` или `relative`               | `0`                                                                                                                                                                                                                 | Блочный способ разметки (плавающие элементы)                                                                       |
    | _любое_ `table-*`_, кроме_ `table-caption`                                                                                                                                                                                                                                                                                                                                                                                                             | _любое_                               | _любое_                               | `0`                                                                                                                                                                                                                 | Внутренние `table-*` элементы не имеют отступов, вместо этого используйте {{ cssxref("border-spacing") }} |
    | _любое, кроме `flex`,_ `inline-flex`_, или_ `table-*`                                                                                                                                                                                                                                                                                                                                                                                                  | _любое_                               | _`fixed`_ или `absolute`              | `0`, кроме случаев, когда `margin-left` и `margin-right` установлены как `auto`. В этом случае, устанавливается значение центрирующее границы области внутри доступной `width` (ширины), если значение фиксировано. | Способ разметки абсолютным позиционированием                                                                       |
    | `flex`, `inline-flex`                                                                                                                                                                                                                                                                                                                                                                                                                                  | _любое_                               | _любое_                               | `0`, кроме случаев, когда есть положительное горизонтальное свободное пространство. В этом случае, распределяется равномерно по всем горизонтальным `auto` отступам.                                                | Способ разметки с помощью flexbox                                                                                  |

### Формальный синтаксис

{{csssyntax}}

## Примеры

```css
.content { margin-right: 5%; }
.sidebox { margin-right: 10px; }
.logo    { margin-right: -5px; }
```

## Спецификации

{{Specifications}}

{{cssinfo}}

## Поддержка браузерами

{{Compat}}