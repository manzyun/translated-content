---
title: Параллельная модель и цикл событий.
slug: Web/JavaScript/EventLoop
tags:
  - Руководство
translation_of: Web/JavaScript/EventLoop
---

{{JsSidebar("Advanced")}}

Параллелизм/Многопоточность в JavaScript работает за счёт цикла событий (**event loop**), который отвечает за выполнение кода, сбора и обработки событий и выполнения под-задач из очереди (**queued sub-tasks**). Эта модель весьма отличается от других языков программирования, таких как C и Java.

## Концепция жизненного цикла

В следующей секции объясняется теоретическая модель. Современные JavaScript движки внедряют/имплементируют и существенно оптимизируют этот процесс.

### Визуальное представление

![Stack, heap, queue](/en-US/docs/Web/JavaScript/EventLoop/the_javascript_runtime_environment_example.svg)

Для лучшего **визуального** представления работы **Event loop**, Вы можете ознакомиться с данным видео: <https://www.youtube.com/watch?v=8aGhZQkoFbQ&t=389s>

### Стек

Вызов любой функции создаёт контекст выполнения ([Execution Context](/ru/docs/Web/API/HTML_DOM_API/Microtask_guide/In_depth#JavaScript_execution_contexts)). При вызове вложенной функции создаётся новый контекст, а старый сохраняется в специальной структуре данных - стеке вызовов (Call Stack).

```js
function f(b) {
  var a = 12;
  return a + b + 35;
}

function g(x) {
  var m = 4;
  return f(m * x);
}

g(21);
```

Когда вызывается функция `g`, создаётся первый контекст выполнения, содержащий аргументы функции `g` и локальные переменные. Когда `g` вызывает `f`, создаётся второй контекст с аргументами `f` и её локальными переменными. И этот контекст выполнения `f` помещается в стек вызовов выше первого. Когда `f` возвращает результат, верхний элемент из стека удаляется. Когда `g` возвращает результат, её контекст также удалится, и стек становится пустым.

### Куча

Объекты размещаются в [куче](<https://ru.wikipedia.org/wiki/%D0%9A%D1%83%D1%87%D0%B0_(%D0%BF%D0%B0%D0%BC%D1%8F%D1%82%D1%8C)>). Куча — это просто имя для обозначения большой неструктурированной области памяти.

### Очередь

Среда выполнения JavaScript содержит очередь задач. Эта очередь — список задач, подлежащих обработке. Каждая задача ассоциируется с некоторой функцией, которая будет вызвана, чтобы обработать эту задачу.

Когда стек полностью освобождается, самая первая задача извлекается из очереди и обрабатывается. Обработка задачи состоит в вызове ассоциированной с ней функции с параметрами, записанными в этой задаче. Как обычно, вызов функции создаёт новый контекст выполнения и заносится в стек вызовов.

Обработка задачи заканчивается, когда стек снова становится пустым. Следующая задача извлекается из очереди и начинается её обработка.

## Цикл событий

Модель событийного цикла (`event loop`) называется так потому, что отслеживает новые события в цикле:

```js
while(queue.waitForMessage()){
  queue.processNextMessage();
}
```

`queue.waitForMessage` ожидает поступления задач, если очередь пуста.

### Запуск до завершения

Каждая задача выполняется полностью, прежде чем начнёт обрабатываться следующая. Благодаря этому мы точно знаем: когда выполняется текущая функция – она не может быть приостановлена и будет целиком завершена до начала выполнения другого кода (который может изменить данные, с которыми работает текущая функция). Это отличает JavaScript от такого языка программирования как C. Поскольку в С функция, запущенная в отдельном потоке, в любой момент может быть остановлена, чтобы выполнить какой-то другой код в другом потоке.

У данного подхода есть и минусы. Если задача занимает слишком много времени, то веб-приложение не может обрабатывать действия пользователя в это время (например, скролл или клик). Браузер старается смягчить проблему и выводит сообщение _"скрипт выполняется слишком долго" ("a script is taking too long to run")_ и предлагает остановить его. Хорошей практикой является создание задач, которые исполняются быстро, и если возможно, разбиение одной задачи на несколько мелких.

### Добавление событий в очередь

В браузерах события добавляются в очередь в любое время, если событие произошло, а так же если у него есть обработчик. В случае, если обработчика нет – событие потеряно. Так, клик по элементу, имеющему обработчик события по событию `click`, добавит событие в очередь, а если обработчика нет – то и событие в очередь не попадёт.

Вызов [setTimeout](/ru/docs/Web/API/WindowTimers/setTimeout) добавит событие в очередь по прошествии времени, указанного во втором аргументе вызова. Если очередь событий на тот момент будет пуста, то событие обработается сразу же, в противном случае событию функции `setTimeout` придётся ожидать завершения обработки остальных событий в очереди. Именно поэтому второй аргумент `setTimeout` корректно считать не временем, через которое выполнится функция из первого аргумента, а минимальное время, через которое она сможет выполниться.

### Нулевые задержки

Нулевая задержка не даёт гарантии, что обработчик выполнится через ноль миллисекунд. Вызов {{domxref("WindowTimers.setTimeout", "setTimeout")}} с аргументом 0 (ноль) не завершится за указанное время. Выполнение зависит от количества ожидающих задач в очереди. Например, сообщение ''this is just a message'' из примера ниже будет выведено на консоль раньше, чем произойдёт выполнение обработчика _cb1_. Это произойдёт, потому что задержка – это минимальное время, которое требуется среде выполнения на обработку запроса.

```js
(function () {

  console.log('this is the start');

  setTimeout(function cb() {
    console.log('this is a msg from call back');
  });

  console.log('this is just a message');

  setTimeout(function cb1() {
    console.log('this is a msg from call back1');
  }, 0);

  console.log('this is the end');

})();

// "this is the start"
// "this is just a message"
// "this is the end"
// "this is a msg from call back"
// "this is a msg from call back1"
```

### Связь нескольких потоков между собой

Web Worker или кросс-доменный фрейм имеют свой собственный стек, кучу и очередь событий. Два отдельных событийных потока могут связываться друг с другом, только через отправку сообщений с помощью метода `postMessage`. Этот метод добавляет сообщение в очередь другого, если он конечно принимает их.

## Никогда не блокируется

Очень интересное свойство цикла событий в JavaScript, что в отличие от множества других языков, поток выполнения никогда не блокируется. Обработка I/O обычно осуществляется с помощью событий и колбэк-функций, поэтому даже когда приложение ожидает запрос от [IndexedDB](/ru/docs/IndexedDB) или ответ от [XHR](/ru/docs/Web/API/XMLHttpRequest), оно может обрабатывать другие процессы, например пользовательский ввод.

Существуют хорошо известные исключения как `alert` или синхронный XHR, но считается хорошей практикой избегать их использования.