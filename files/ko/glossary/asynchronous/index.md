---
title: 비동기(Asynchronous)
slug: Glossary/Asynchronous
---

**비동기**는 주로 두 개 이상의 객체나 이벤트가 동시에 **존재하지 않거나 발생하지 않는 것**을 의미합니다 (여러 관련된 작업이 원래의 일이 끝날 때까지 기다리지 않는 것도 포함됩니다). 프로그래밍에서 비동기는 다음 두 가지 맥락에서 사용됩니다.

**네트워크와 통신**

  비동기 통신은 둘 이상의 통신자 사이에서 메시지를 교환하는 방법으로 메시지를 받음과 동시에 처리할 필요 없이, 각자 처리할 수 있는 적절한 때에 메시지를 받고 처리하는 방식입니다. 또한, 문제가 발생하더라도 수신자가 따로 수정을 요청하거나 문제를 처리할 것이라는 가정하에 별도의 승인 없이 메시지를 보낼 수 있습니다.

  이메일은 비동기 통신의 예시입니다. 발신자가 메일을 보내면 수신자는 받은 즉시 메일을 확인하지 않고 적당한 때에 메일을 읽고 답장을 보냅니다. 또한, 양쪽 모두 상대방의 시간에 맞출 필요 없이 아무 때나 메일을 주고받을 수 있습니다.

  소프트웨어가 비동기적으로 통신한다면 프로그램은 서버와 같은 다른 프로그램에 정보를 요청하고 응답을 기다리면서 다른 작업을 할 수 있습니다. [AJAX](/en-US/docs/Web/Guide/AJAX)(또는 ajax)라는 "비동기적인 자바스크립트와 {{Glossary("XML")}}" 프로그래밍 기법이 있습니다(요즘에는 XML 보다 {{Glossary("JSON")}}을 더 많이 사용하긴 합니다). 이 기법은 서버에 {{Glossary("HTTP")}}를 사용하여 상대적으로 적은 양의 데이터를 요청하고, 결과를 사용 가능할 때에만 반환하는 메커니즘입니다.

**소프트웨어 설계**

 비동기 소프트웨어 설계는 작업이 완료되는 걸 프로그램이 기다릴 필요 없이 기존의 작업과 함께 처리되도록 요청할 수 있게 코드를 작성하여 그 개념을 확장합니다. 보조 작업이 완료되면 기존 작업에 알림을 보내 작업을 완료시키고, 결과가 있는 경우에는 그 결과를 사용할 수 있음을 알립니다.

 비동기 소프트웨어를 구현하는 여러 프로그래밍 기법이 있습니다. 이에 대한 소개는 [비동기 자바스크립트](/ko/docs/Learn/JavaScript/Asynchronous)에서 볼 수 있습니다.

## 같이 보기

- [서버에서 데이터 가져오기](/en-US/docs/Learn/JavaScript/Client-side_web_APIs/Fetching_data)
- {{glossary("Synchronous")}}