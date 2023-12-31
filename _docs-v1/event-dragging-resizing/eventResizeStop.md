---
title: eventResizeStop
type: callback
since_version: 1.3
---

Triggered when event resizing stops.

<div class='spec' markdown='1'>
function( *event*, *jsEvent*, *ui*, *view* ) { }
</div>

This callback is *guaranteed* to be triggered after the user resizes an event, even if the event doesn't change in duration. It is triggered before the event's information has been modified (if changed in duration) and before the [eventResize](eventResize) callback is triggered.

`event` is an [Event Object](event-object) that hold the event's information (date, title, etc).

`jsEvent` holds the native JavaScript event with low-level information such as mouse coordinates.

`ui` holds the [jQuery UI object](https://jqueryui.com/demos/resizable/).

`view` holds the current [View Object](view-object).
