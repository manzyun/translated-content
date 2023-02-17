---
title: Data URL
slug: Web/HTTP/Basics_of_HTTP/Data_URLs
translation_of: Web/HTTP/Basics_of_HTTP/Data_URIs
original_slug: Web/HTTP/Basics_of_HTTP/Data_URIs
---

{{HTTPSidebar}}

**Data URL**, URL имеющий приставку `data:`, делает возможным встраивание файлов небольшого размера прямо в документ.

> **Примечание:** современные браузеры обрабатывают Data URL, как неявный уникальный origin, и не заимствуют значение origin из объекта настроек ответственного за навигацию.

## Синтаксис

Data URL состоит из четырёх сегментов: приставки (`data:`), [MIME типа](/ru/docs/Web/HTTP/Basics_of_HTTP/MIME_types), описывающего тип данных, дополнительного ключевого слова `base64` для нетекстовых данных и самой строки данных:

```
data:[<тип данных>][;base64],<данные>
```

`тип данных` описывается строкой в формате [MIME типа](/ru/docs/Web/HTTP/Basics_of_HTTP/MIME_types), например `'image/jpeg'` для JPEG файла изображения. При не указывании типа данных, браузер автоматически будет интерпретировать строку данных, как `text/plain;charset=US-ASCII`

Если данные представляют собой какую-либо текстовую информацию, вы можете просто вставить эту текстовую строку в Data URL (используя соответствующие для типа данных сущности и знаки экранирования). В ином случае вам будет необходимо использовать ключевое слово `base64` перед вставкой base64-кодированных бинарных данных. Дополнительную информацию о MIME типах вы сможете найти [здесь](/ru/docs/Web/HTTP/Basics_of_HTTP/MIME_types) и [здесь](/ru/docs/Web/HTTP/Basics_of_HTTP/MIME_types/Complete_list_of_MIME_types).

Несколько примеров:

- `data:,Hello%2C%20World!`
  - : Простые text/plain данные
- `data:text/plain;base64,SGVsbG8sIFdvcmxkIQ%3D%3D`
  - : base64-кодированная версия примера выше
- `data:text/html,%3Ch1%3EHello%2C%20World!%3C%2Fh1%3E`
  - : HTML строка вида: `<h1>Hello, World!</h1>`
- `data:text/html,<script>alert('hi');</script>`
  - : HTML строка, вызывающая JavaScript alert функцию. Заметьте необходимость закрывающего \<script> тега.

## Кодирование данных в формат base64

Base64 относится к группе транспортных кодировок, и позволяет представлять бинарные данные в виде ASCII строк, переводя их в radix-64 представление. Состоя только из ASCII символов, base64 строки являются допустимыми для использования в URL, по этой причине они могут быть использованы и в Data URL.

### Кодирование в Javascript

Web API имеет встроенные методы для кодирования и декодирования формата base64: [Base64 кодирование и декодирование](/ru/docs/Web/API/WindowBase64/Base64_encoding_and_decoding).

### Кодирование на Unix системах

На Linux и Mac OS X системах, кодирование файлов или строк в формат Base64 может быть выполнено через программу `base64` в командной строке (или, в качестве альтернативы, программу `uuencode` с `-m` аргументом).

```bash
echo -n hello|base64
# выводит в консоль: aGVsbG8=

echo -n hello>a.txt
base64 a.txt
# выводит в консоль: aGVsbG8=

base64 a.txt>b.txt
# записывает в файл b.txt: aGVsbG8=
```

### Кодирование на Microsoft Windows

Кодирование на Windows может быть выполнено через powershell или какую-либо другую предназначенную для этого программу. Так же кодирование может быть выполнено и через программу `base64` (смотрите секцию Кодирование на Unix системах), при условии активированной технологии [WSL](https://en.wikipedia.org/wiki/Windows_Subsystem_for_Linux).

```
[convert]::ToBase64String([Text.Encoding]::UTF8.GetBytes("hello"))
# выводит в консоль: aGVsbG8=

bash -c "echo -n hello`|base64"
# выводит в консоль: aGVsbG8=
# обратный апостроф (`) используется здесь для экранирования символа вертикальной черты (|)
```

## Распространённые проблемы

Эта секция описывает ряд проблем, которые могут возникнуть при использовании Data URL.

Для примера рассмотрим Data URL вида:

```
data:text/html,lots of text...<p><a name%3D"bottom">bottom</a>?arg=val
```

результатом декодирования которого будет HTML строка:

```
lots of text...<p><a name="bottom">bottom</a>?arg=val
```

- Синтаксис
  - : Data URL представляет собой простой формат, но даже в нём можно забыть добавить запятую перед сегментом данных или произвести ошибку во время их base64 кодирования.
- Форматирование внутри документа
  - : Встраивание Data URL по сути является встраиванием файла внутрь файла, и длина его строки может быть намного шире, чем ширина заключающего его документа. Так же, несмотря на то, что использование пробелов считается обычной практикой при форматировании данных, есть вероятность, что у вас возникнут проблемы [при их base64 кодировании](http://bugzilla.mozilla.org/show_bug.cgi?id=73026#c12).
- Ограничения длины
  - : Хотя Firefox поддерживает Data URL практически неограниченных размеров, каждый отдельный браузер имеет свои ограничения на их длину. Например, Opera 11 ограничивает допустимую длину URL до 65535 символов, что означает ограничение сегмента данных в Data URL до 65529 символов (длина в 65529 символов взята из условия использования только только `data:` сегмента, без определения MIME типа данных).
- Нехватка возможности обработки ошибок
  - : Опечатки в определении MIME типа или написания ключевого слова `'base64'` будут проигнорированы без каких-либо уведомлений об ошибках.
- Отсутствие поддержки строки параметров
  - : В связи с неопределённостью типа сегмента данных в Data URL, строка параметров (характерные для страницы параметры, представляющиеся в виде `<url>?parameter-data`), добавленная к сегменту данных будет рассматриваться, как часть этих данных.
- Проблемы с безопасностью
  - : Несколько проблем с безопасностью (например: фишинг) связаны с Data URL и переходом по ним из корневого контекста документа. Чтобы избавиться от этих проблем, переход по URI, начинающихся со схемы `data://`, из корневого контекста документа перестал быть возможен в Firefox, начиная с версии 59 (и начиная с версии 58 в Nightly/Beta вариантах браузера). Надеемся, что остальные браузеры так же последуют этому примеру. Для дополнительной информации смотрите [Blocking Top-Level Navigations to data URLs for Firefox 58](https://blog.mozilla.org/security/2017/11/27/blocking-top-level-navigations-data-urls-firefox-58/).

## Спецификации

| Спецификация         | Заголовок             |
| -------------------- | --------------------- |
| {{RFC("2397")}} | The "data" URL scheme |

## Совместимость с браузерами

{{compat("http.data-url")}}

## Смотрите также

- [Base64 кодирование и декодирование](/ru/docs/Web/API/WindowBase64/Base64_encoding_and_decoding)
- {{domxref("WindowBase64.atob","atob()")}}
- {{domxref("WindowBase64.btoa","btoa()")}}
- [CSS `url()`](/ru/docs/Web/CSS/uri)
- [URI](/ru/docs/Glossary/URI)