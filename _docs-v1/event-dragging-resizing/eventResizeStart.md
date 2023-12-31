---
title: eventResizeStart
type: callback
since_version: 1.3
---

Triggered when event resizing begins.

<div class='spec' markdown='1'>
function( *event*, *jsEvent*, *ui*, *view* ) { }
</div>

`event` is an [Event Object](event-object) that hold the event's information (date, title, etc).

`jsEvent` holds the native JavaScript event with low-level information such as mouse coordinates.

`ui` holds the [jQuery UI object](https://jqueryui.com/demos/resizable/).

`view` holds the current [View Object](view-object).
