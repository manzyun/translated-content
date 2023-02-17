---
title: MouseEvent
slug: Web/API/MouseEvent
---

{{APIRef("DOM Events")}}

**`MouseEvent`** 介面表示了由使用者經指標裝置（如滑鼠）進行互動所發生的事件。常見的 `MouseEvent` 實作事件包括了 [`click`](/zh-TW/docs/Web/API/Element/click_event)、[`dblclick`](/zh-TW/docs/Web/API/Element/dblclick_event)、[`mouseup`](/zh-TW/docs/Web/API/Element/mouseup_event) 與 [`mousedown`](/zh-TW/docs/Web/API/Element/mousedown_event)。

`MouseEvent` 繼承自 {{domxref("UIEvent")}}，而 `UIEvent` 則繼承自 {{domxref("Event")}}。雖然 {{domxref("MouseEvent.initMouseEvent()")}} 方法仍然向下相容新的瀏覽器，但現今應該使用 {{domxref("MouseEvent.MouseEvent", "MouseEvent()")}} 建構式來建立 `MouseEvent` 物件。

另外還有一些特定的事件繼承自 `MouseEvent`：{{domxref("WheelEvent")}} 及 {{domxref("DragEvent")}}。

## 建構式

- {{domxref("MouseEvent.MouseEvent", "MouseEvent()")}}
  - : 建立一個 `MouseEvent` 物件。

## 屬性

_此介面也繼承了其父介面 {{domxref("UIEvent")}} 與 {{domxref("Event")}} 的屬性_

- {{domxref("MouseEvent.altKey")}} {{readonlyinline}}
  - : Returns `true` if the <kbd>alt</kbd> key was down when the mouse event was fired.
- {{domxref("MouseEvent.button")}} {{readonlyinline}}
  - : The button number that was pressed when the mouse event was fired.
- {{domxref("MouseEvent.buttons")}} {{readonlyinline}}
  - : The buttons being pressed when the mouse event was fired
- {{domxref("MouseEvent.clientX")}} {{readonlyinline}}
  - : The X coordinate of the mouse pointer in local (DOM content) coordinates.
- {{domxref("MouseEvent.clientY")}} {{readonlyinline}}
  - : The Y coordinate of the mouse pointer in local (DOM content) coordinates.
- {{domxref("MouseEvent.ctrlKey")}} {{readonlyinline}}
  - : Returns `true` if the <kbd>control</kbd> key was down when the mouse event was fired.
- {{domxref("MouseEvent.metaKey")}} {{readonlyinline}}
  - : Returns `true` if the <kbd>meta</kbd> key was down when the mouse event was fired.
- {{domxref("MouseEvent.movementX")}} {{readonlyinline}}
  - : The X coordinate of the mouse pointer relative to the position of the last [`mousemove`](/zh-TW/docs/Web/API/Element/mousemove_event) event.
- {{domxref("MouseEvent.movementY")}} {{readonlyinline}}
  - : The Y coordinate of the mouse pointer relative to the position of the last [`mousemove`](/zh-TW/docs/Web/API/Element/mousemove_event) event.
- {{domxref("MouseEvent.offsetX")}} {{readonlyinline}}{{experimental_inline}}
  - : The X coordinate of the mouse pointer relative to the position of the padding edge of the target node.
- {{domxref("MouseEvent.offsetY")}} {{readonlyinline}}{{experimental_inline}}
  - : The Y coordinate of the mouse pointer relative to the position of the padding edge of the target node.
- {{domxref("MouseEvent.pageX")}} {{readonlyinline}}{{experimental_inline}}
  - : The X coordinate of the mouse pointer relative to the whole document.
- {{domxref("MouseEvent.pageY")}} {{readonlyinline}}{{experimental_inline}}
  - : The Y coordinate of the mouse pointer relative to the whole document.
- {{domxref("MouseEvent.region")}} {{readonlyinline}}
  - : Returns the id of the hit region affected by the event. If no hit region is affected, `null` is returned.
- {{domxref("MouseEvent.relatedTarget")}} {{readonlyinline}}
  - : The secondary target for the event, if there is one.
- {{domxref("MouseEvent.screenX")}} {{readonlyinline}}
  - : The X coordinate of the mouse pointer in global (screen) coordinates.
- {{domxref("MouseEvent.screenY")}} {{readonlyinline}}
  - : The Y coordinate of the mouse pointer in global (screen) coordinates.
- {{domxref("MouseEvent.shiftKey")}} {{readonlyinline}}
  - : Returns `true` if the <kbd>shift</kbd> key was down when the mouse event was fired.
- {{domxref("MouseEvent.which")}} {{non-standard_inline}} {{readonlyinline}}
  - : The button being pressed when the mouse event was fired.
- {{domxref("MouseEvent.mozPressure")}} {{non-standard_inline()}} {{readonlyinline}}
  - : The amount of pressure applied to a touch or tablet device when generating the event; this value ranges between `0.0` (minimum pressure) and `1.0` (maximum pressure).
- {{domxref("MouseEvent.mozInputSource")}} {{non-standard_inline()}} {{readonlyinline}}
  - : The type of device that generated the event (one of the `MOZ_SOURCE_*` constants listed below). This lets you, for example, determine whether a mouse event was generated by an actual mouse or by a touch event (which might affect the degree of accuracy with which you interpret the coordinates associated with the event).
- {{domxref("MouseEvent.webkitForce")}} {{non-standard_inline()}} {{readonlyinline}}
  - : The amount of pressure applied when clicking
- {{domxref("MouseEvent.x")}} {{experimental_inline}}{{readonlyinline}}
  - : Alias for {{domxref("MouseEvent.clientX")}}.
- {{domxref("MouseEvent.y")}} {{experimental_inline}}{{readonlyinline}}
  - : Alias for {{domxref("MouseEvent.clientY")}}

## Constants

- {{domxref("MouseEvent.WEBKIT_FORCE_AT_MOUSE_DOWN")}} {{non-standard_inline}}{{readonlyinline}}
  - : Minimum force necessary for a normal click
- {{domxref("MouseEvent.WEBKIT_FORCE_AT_FORCE_MOUSE_DOWN")}} {{non-standard_inline}}{{readonlyinline}}
  - : Minimum force necessary for a force click

## 方法

_此介面也繼承了其父介面 {{domxref("UIEvent")}} 與 {{domxref("Event")}} 的方法_

- {{domxref("MouseEvent.getModifierState()")}}
  - : Returns the current state of the specified modifier key. See the {{domxref("KeyboardEvent.getModifierState")}}() for details.
- {{domxref("MouseEvent.initMouseEvent()")}} {{deprecated_inline}}
  - : Initializes the value of a `MouseEvent` created. If the event has already being dispatched, this method does nothing.

## 範例

This example demonstrates simulating a click (that is programmatically generating a click event) on a checkbox using DOM methods.

```js
function simulateClick() {
  var evt = new MouseEvent("click", {
    bubbles: true,
    cancelable: true,
    view: window
  });
  var cb = document.getElementById("checkbox"); //element to click on
  var canceled = !cb.dispatchEvent(evt);
  if(canceled) {
    // A handler called preventDefault
    alert("canceled");
  } else {
    // None of the handlers called preventDefault
    alert("not canceled");
  }
}
document.getElementById("button").addEventListener('click', simulateClick);
```

```html
<p><label><input type="checkbox" id="checkbox"> Checked</label>
<p><button id="button">Click me</button>
```

Click on the button to see how the sample works:

{{ EmbedLiveSample('範例') }}

## 規範

{{Specifications}}

## 瀏覽器相容性

{{Compat}}

## 參見

- Its direct parent, {{domxref("UIEvent")}}.