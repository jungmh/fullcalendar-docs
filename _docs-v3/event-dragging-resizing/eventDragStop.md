---
title: eventDragStop
type: callback
---

Triggered when event dragging stops.

<div class='spec' markdown='1'>
function( *event*, *jsEvent*, *ui*, *view* ) { }
</div>

This callback is *guaranteed* to be triggered after the user drags an event, even if the event doesn't change date/time. It is triggered before the event's information has been modified (if moved to a new date/time) and before the [eventDrop](eventDrop) callback is triggered.

`event` is an [Event Object](event-object) that hold the event's information (date, title, etc).

`jsEvent` holds the jQuery event with low-level information such as mouse coordinates.

`ui` holds an empty object. Before version 2.1, the [jQuery UI object](https://jqueryui.com/demos/draggable/).

`view` holds the current [View Object](view-object).
