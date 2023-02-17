---
title: Переменные - место хранения необходимой информации
slug: Learn/JavaScript/First_steps/Variables
translation_of: Learn/JavaScript/First_steps/Variables
original_slug: Learn/JavaScript/Первые_шаги/Variables
---
{{LearnSidebar}}{{PreviousMenuNext("Learn/JavaScript/Первые_шаги/Что_пошло_не_так", "Learn/JavaScript/Первые_шаги/Math", "Learn/JavaScript/Первые_шаги")}}

После прочтения последних двух статей вы знаете, что такое JavaScript, что он может сделать для вас, как использовать его вместе с другими веб-технологиями и какими он обладает функциями высокого уровня. В этой статье мы перейдём к реальным основам, рассмотрим, как работать с большинством базовых блоков JavaScript — Переменными.

| Необходимые навыки: | Базовая компьютерная грамотность, базовое понимание HTML и CSS, понимание того, что такое JavaScript. |
| ------------------- | ----------------------------------------------------------------------------------------------------- |
| Цель:               | Ознакомиться с основами переменных в JavaScript.                                                      |

## Инструменты, которые вам нужны

В этой статье вам будет предложено ввести строки кода, чтобы проверить ваше понимание материала. Если вы используете браузер для настольных компьютеров, лучшим примером для ввода кода примера является консоль JavaScript вашего браузера (см. [What are browser developer tools](/ru/docs/Learn/Common_questions/What_are_browser_developer_tools) для получения дополнительной информации о том, как получить доступ к этому инструменту).

Также мы предоставили простую консоль JavaScript, встроенную ниже в странице, для ввода кода, если вы не используете браузер с консолью JavaScript или консоль на странице окажется для вас более комфортной.

## Что такое переменные?

Переменные — это контейнер для таких значений, как числа, используемые в сложении, или строка, которую мы могли бы использовать как часть предложения. Но одна из особенностей переменных — их значение может меняться. Давайте взглянем на простой пример:

```html
<button>Нажми на меня</button>
```

```js
const button = document.querySelector('button');

button.onclick = function() {
  let name = prompt('Как вас зовут?');
  alert('Привет ' + name + ', рады видеть вас!');
}
```

{{ EmbedLiveSample('What_is_a_variable', '100%', 50, "", "", "hide-codepen-jsfiddle") }}

В примере, по нажатию кнопки выполнится несколько строк кода. Первая строка в функции покажет пользователю окно, где попросит ввести его имя и сохранит значение в переменной. Вторая строка отобразит приветствие с включённым введённым именем, взятым из значения переменной.

Чтобы лучше понять действие переменной здесь, давайте подумаем о том, как мы будем писать этот пример без использования переменной. Это будет выглядеть примерно так:

```plain example-bad
var name = prompt('Как вас зовут?');

if (name === 'Адам') {
  alert('Привет, Адам, рады тебя видеть!');
} else if (name === 'Алан') {
  alert('Привет, Алан, рады тебя видеть!');
} else if (name === 'Белла') {
  alert('Привет, Белла, рады тебя видеть!');
} else if (name === 'Бьянка') {
  alert('Привет, Бьянка, рады тебя видеть!');
} else if (name === 'Крис') {
  alert('Привет, Крис, рады тебя видеть!');
}

// ... и так далее ...
```

Вам сейчас не обязательно понимать синтаксис, который мы используем (пока!), но вы должны понять идею: если бы у нас не было доступных переменных, нам пришлось бы реализовать гигантский блок кода, который проверял, какое имя было введено, а затем отображал соответствующее сообщение для этого имени. Очевидно, что это неэффективно (код намного больше, даже для четырёх вариантов), и он просто не сработает, так как вы не можете хранить все возможные варианты.

Переменные имеют смысл, и, когда вы узнаете больше о JavaScript, они начнут становиться второй натурой.

Ещё одна особенность переменных заключается в том, что они могут содержать практически все, а не только строки и числа. Переменные могут также содержать сложные данные и даже целые функции. Об этом вы узнаете больше при дальнейшем изучении курса..

Заметьте: мы говорим, что переменные содержат значения. Это важное различие. Переменные не являются самими значениями; они представляют собой контейнеры для значений. Представьте, что они похожи на маленькие картонные коробки, в которых вы можете хранить вещи.

![](boxes.png)

## Объявление переменной

Чтобы использовать переменную, вы сначала должны её создать, или, если быть точнее, объявить переменную. Чтобы сделать это, мы вводим ключевое слово var, за которым следует имя, которое вы хотите дать своей переменной:

```js
var myName;
var myAge;
```

Здесь мы создаём две переменные myName и myAge. Попробуйте ввести эти строки сейчас в консоли вашего веб-браузера или в консоли ниже (можно открыть эту консоль в отдельной вкладке или в новом окне). После этого попробуйте создать переменную (или две) с вашими именами.

```html hidden
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>JavaScript console</title>
    <style>
      * {
        box-sizing: border-box;
      }

      html {
        background-color: #0C323D;
        color: #809089;
        font-family: monospace;
      }

      body {
        max-width: 700px;
      }

      p {
        margin: 0;
        width: 1%;
        padding: 0 1%;
        font-size: 16px;
        line-height: 1.5;
        float: left;
      }

      .input p {
        margin-right: 1%;
      }

      .output p {
        width: 100%;
      }

      .input input {
        width: 96%;
        float: left;
        border: none;
        font-size: 16px;
        line-height: 1.5;
        font-family: monospace;
        padding: 0;
        background: #0C323D;
        color: #809089;
      }

      div {
        clear: both;
      }

    </style>
  </head>
  <body>


  </body>

  <script>
    var geval = eval;
    function createInput() {
      var inputDiv = document.createElement('div');
      var inputPara = document.createElement('p');
      var inputForm = document.createElement('input');

      inputDiv.setAttribute('class','input');
      inputPara.textContent = '>';
      inputDiv.appendChild(inputPara);
      inputDiv.appendChild(inputForm);
      document.body.appendChild(inputDiv);

      if(document.querySelectorAll('div').length > 1) {
        inputForm.focus();
      }

      inputForm.addEventListener('change', executeCode);
    }

    function executeCode(e) {
      try {
        var result = geval(e.target.value);
      } catch(e) {
        var result = 'error — ' + e.message;
      }

      var outputDiv = document.createElement('div');
      var outputPara = document.createElement('p');

      outputDiv.setAttribute('class','output');
      outputPara.textContent = 'Result: ' + result;
      outputDiv.appendChild(outputPara);
      document.body.appendChild(outputDiv);

      e.target.disabled = true;
      e.target.parentNode.style.opacity = '0.5';

      createInput()
    }

    createInput();

  </script>
</html>
```

{{ EmbedLiveSample('Hidden_code', '100%', 300) }}

> **Примечание:** в JavaScript все инструкции кода должны заканчиваться точкой с запятой (;) - ваш код может работать правильно для отдельных строк, но, вероятно, не будет, когда вы пишете несколько строк кода вместе. Попытайтесь превратить написание точки с запятой в привычку.

Теперь проверим, существуют ли эти значения в среде выполнения. Для этого введём только имя переменной.

```js
myName;
myAge;
```

В настоящее время они не содержат значения, это пустые контейнеры. В этом случае, когда вы вводите имена переменных, вы должны получить значение `undefined` . Если они не существуют, вы получите сообщение об ошибке - попробуйте сейчас ввести в консоли имя переменной ниже:

```js
scoobyDoo;
```

> **Примечание:** Не путайте переменную, которая существует, но не имеет значения, с переменной, которая вообще не существует - это разные вещи.

## Присвоение значения переменной

Как только переменная объявлена, ей можно присвоить значение. Для этого пишется имя переменной, затем следует знак равенства (`=`), а за ним значение, которое вы хотите присвоить. Например:

```js
myName = 'Chris';
myAge = 37;
```

Попробуйте вернуться в консоль и ввести эти строки. Вы должны увидеть значение, которое вы назначили переменной, возвращаемой в консоли. Чтобы посмотреть значения переменных, нужно набрать их имя в консоли:

```js
myName;
myAge;
```

Вы можете объявить переменную и задать ей значение одновременно:

```js
var myName = 'Chris';
```

Скорее всего, так вы будете писать большую часть времени, так как запись и выполнения кода с одно строки происходит быстрее, чем выполнение двух действий на двух отдельных строках.

> **Примечание:** Если вы пишете многострочную программу JavaScript, которая объявляет и инициализирует (задаёт значение) переменную, вы можете объявить её после её инициализации, и она всё равно будет работать. Это связано с тем, что объявления переменных обычно выполняются первыми, прежде чем остальная часть кода будет выполнена. Это называется **hoisting** - прочитайте [var hoisting](/ru/docs/Web/JavaScript/Reference/Statements/var#var_hoisting) для более подробной информации по этому вопросу.

## Обновление переменной

Когда переменной присваивается значение, вы можете изменить (обновить) это значение, просто указав другое значение. Попробуйте ввести следующие строки в консоль:

```js
myName = 'Bob';
myAge = 40;
```

### Правила именования переменных

Вы можете назвать переменную как угодно, но есть ограничения. Как правило, вы должны придерживаться только латинских символов (0-9, a-z, A-Z) и символа подчёркивания.

- Не рекомендуется использование других символов, потому что они могут вызывать ошибки или быть непонятными для международной аудитории.
- Не используйте символы подчёркивания в начале имён переменных - это используется в некоторых конструкциях JavaScript для обозначения конкретных вещей.
- Не используйте числа в начале переменных. Это недопустимо и приведёт к ошибке.
- Общепринято придерживаться так называемый ["lower camel case"](https://en.wikipedia.org/wiki/CamelCase#Variations_and_synonyms), где вы склеиваете несколько слов, используя строчные буквы для всего первого слова, а затем заглавные буквы последующих слов. Мы использовали это для наших имён переменных в этой статье.
- Делайте имена переменных такими, чтобы было интуитивно понятно, какие данные они содержат. Не используйте только отдельные буквы / цифры или большие длинные фразы.
- Переменные чувствительны к регистру, так что `myage` и `myAge` - разные переменные.
- И последнее - вам также нужно избегать использования зарезервированных слов JavaScript в качестве имён переменных - под этим мы подразумеваем слова, которые составляют фактический синтаксис JavaScript! Таким образом, вы не можете использовать слова типа `var`, `function`, `let`, и `for` для имён переменных. Браузеры распознают их как разные элементы кода, и поэтому возникают ошибки.

> **Примечание:** По ссылке можно найти довольно полный список зарезервированных ключевых слов: [Lexical grammar — keywords](/ru/docs/Web/JavaScript/Reference/Lexical_grammar#Keywords).

Примеры хороших имён переменных:

```plain example-good
age
myAge
init
initialColor
finalOutputValue
audio1
audio2
```

Примеры плохих имён переменных:

```plain example-bad
1
a
_12
myage
MYAGE
var
Document
skjfndskjfnbdskjfb
thisisareallylongstupidvariablenameman
```

Примеры имён переменных, которые вызовут ошибки:

```plain example-bad
var
Document
```

Попытайтесь создать ещё несколько переменных прямо сейчас, используя знания, изложенные выше.

## Типы переменных

Есть несколько различных типов данных, которые мы можем хранить в переменных. В этом разделе мы кратко опишем их, а затем в будущих статьях вы узнаете о них более подробно.

### Числа (Numbers)

Вы можете хранить числа в переменных (целые числа, такие как 30, или десятичные числа, такие как 2.456, также называемые числами с плавающей точкой или с плавающей запятой). Вам не нужно объявлять типы переменных в JavaScript, в отличие от некоторых других языков программирования Если давать переменной значение числа,кавычки не используются:

```js
var myAge = 17;
```

### Строки ('Strings')

Строки - это фрагменты текста. Когда вы даёте переменной значение строки, вам нужно обернуть её в одиночные или двойные кавычки, в противном случае JavaScript попытается проиндексировать её как другое имя переменной.

```js
var dolphinGoodbye = 'So long and thanks for all the fish';
```

### Логические (Booleans)

Booleans - истинные / ложные значения - они могут иметь два значения: true или false. Они обычно используются для проверки состояния, после чего код запускается соответствующим образом. Вот простой пример:

```js
var iAmAlive = true;
```

В действительности вы чаще будете использовать этот тип переменных так:

```js
var test = 6 < 3;
```

Здесь используется оператор «меньше» (<), чтобы проверить, является ли 6 меньше 3. В данном примере, он вернёт false, потому что 6 не меньше 3! В дальнейшем вы узнаете больше о таких операторах.

### Массивы (Arrays)

Массив - это один объект, который содержит несколько значений, заключённых в квадратные скобки и разделённых запятыми. Попробуйте ввести следующие строки в консоль:

```js
var myNameArray = ['Chris', 'Bob', 'Jim'];
var myNumberArray = [10,15,40];
```

Как только эти массивы определены, можно получить доступ к каждому значению по их местоположению в массиве. Наберите следующие строки:

```js
myNameArray[0]; // should return 'Chris'
myNumberArray[2]; // should return 40
```

Квадратные скобки указывают значение индекса, соответствующее позиции возвращаемого значения. Возможно, вы заметили, что массивы в JavaScript индексируются с нулевой отметкой: первый элемент имеет индекс 0.

В следующей статье вы узнаете больше о массивах.

### Объекты (Objects)

В программировании объект представляет собой структуру кода, который моделирует объект реальной жизни. У вас может быть простой объект, представляющий автостоянку, и содержит информацию о её ширине и длине; или вы можете иметь объект, который представляет человека, и содержит данные о его имени, росте, весе, на каком языке он говорит, как сказать ему привет и многое другое.

Попробуйте ввести следующую строку в консоль:

```js
var dog = { name : 'Spot', breed : 'Dalmatian' };
```

Чтобы получить информацию, хранящуюся в объекте, вы можете использовать следующий синтаксис:

```js
dog.name
```

Мы больше не будем рассматривать объекты в данном курсе - вы можете больше узнать о них в будущем модуле.

## Динамическая типизация

JavaScript - это «динамически типизируемый язык», что означает, что в отличие от некоторых других языков вам не нужно указывать, какой тип данных будет содержать переменная (например, числа, строки, массивы и т. д.).

Например, если вы объявите переменную и присвоите ей значение, заключённое в кавычки, браузер будет обрабатывать переменную как строку:

```js
var myString = 'Привет';
```

Он всё равно будет строкой, даже если он содержит числа, поэтому будьте осторожны:

```js
var myNumber = '500'; // упс, это все ещё строка (string)
typeof(myNumber);
myNumber = 500; // так-то лучше, теперь это число (number)
typeof(myNumber);
```

Попробуйте ввести четыре строки выше в консоль одну за другой и посмотреть результаты. Вы заметите, что мы используем специальную функцию `typeof()` - она возвращает тип данных переменной, которую вы передаёте в неё. В первый раз, когда она вызывается, она должа возвращать строку, так как переменная `myNumber` содержит строку `'500'`. Посмотрите, что она вернёт во второй раз, когда вы её вызовите.

## Подведение итогов

К настоящему времени вы должны знать достаточно о переменных JavaScript и о том, как их создавать. В следующей статье мы остановимся на числах более подробно, рассмотрев, как сделать базовую математику в JavaScript.

{{PreviousMenuNext("Learn/JavaScript/Первые_шаги/Что_пошло_не_так", "Learn/JavaScript/Первые_шаги/Math", "Learn/JavaScript/Первые_шаги")}}