---
title: RTCRtpTransceiver.direction
slug: Web/API/RTCRtpTransceiver/direction
---

{{APIRef("WebRTC")}}

The {{domxref("RTCRtpTransceiver")}} property **`direction`** is a string which indicates the transceiver's preferred directionality. Its value must be one of the strings defined by the {{domxref("RTCRtpTransceiverDirection")}} enumeration.

The transceiver's _current_ direction is indicated by the {{domxref("RTCRtpTransceiver.currentDirection", "currentDirection")}} property.

### 值

A {{domxref("DOMString")}} whose value is one of the strings which are a member of the `RTCRtpTransceiverDirection` enumerated type, indicating the transceiver's preferred direction.

<table class="standard-table">
  <thead>
    <tr>
      <th scope="row">值</th>
      <th scope="col"><code>RTCRtpSender</code> 的行为</th>
      <th scope="col"><code>RTCRtpReceiver</code> 的行为</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th scope="row"><code>"sendrecv"</code></th>
      <td>
        可以发送 {{Glossary("RTP")}} 数据，如果另一个对等节点接受了连接，且至少有一个 sender 的处于编码状态，则发送数据。
      </td>
      <td>
        可以接收 RTP 数据，如果有其它的对等节点接受数据，则接收数据。
      </td>
    </tr>
    <tr>
      <th scope="row"><code>"sendonly"</code></th>
      <td>
        可以发送 {{Glossary("RTP")}} 数据，如果另一个对等节点接受了连接，且至少有一个 sender 的处于编码状态，则发送数据。
      </td>
      <td><em>不</em>可以接收 RTP 数据，无论如何都不会接收数据。</td>
    </tr>
    <tr>
      <th scope="row"><code>"recvonly"</code></th>
      <td><em>不</em>可以发送 RTP 数据，无论如何都不会发送数据。</td>
      <td>
        可以接收 RTP 数据，如果有其它的对等节点接受数据，则接收数据。
      </td>
    </tr>
    <tr>
      <th scope="row"><code>"inactive"</code></th>
      <td><em>不</em>可以接收 RTP 数据，无论如何都不会接收数据。</td>
      <td><em>不</em>可以接收 RTP 数据，无论如何都不会接收数据。</td>
    </tr>
  </tbody>
</table>

### 异常

When setting the value of `direction`, the following exceptions can occur:

- `InvalidStateError`
  - : Either the receiver's {{domxref("RTCPeerConnection")}} is closed or the {{domxref("RTCRtpReceiver")}} is stopped.

## Usage notes

### Setting the direction

When you change the value of `direction`, an `InvalidStateError` exception will occur if the connection is closed or the receiver is stopped.

If the new value of `direction` is in fact different from the existing value, renegotiation of the connection is required, so a {{DOMxRef("RTCPeerConnection/negotiationneeded_event", "negotiationneeded")}} event is sent to the {{domxref("RTCPeerConnection")}}.

### Effect on offers and answers

The value of `direction` is used by {{domxref("RTCPeerConnection.createOffer()")}} or {{domxref("RTCPeerConnection.createAnswer()")}} in order to generate the SDP generated by each of those methods. The SDP contains an a-line which specifies the directionality. For example, if the `direction` is specified as `"sendrecv"`, the corresponding SDP a-line is:

```plain
a=sendrecv
```

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 参见

- {{domxref("RTCRtpTransceiver.currentDirection")}}