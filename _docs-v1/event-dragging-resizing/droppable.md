---
title: droppable
since_version: 1.4.7
---

Determines if jQuery UI draggables can be dropped onto the calendar.

<div class='spec' markdown='1'>
Boolean, *default*: `false`
</div>

This option operates with jQuery UI draggables. You must [download](https://jqueryui.com/download) the appropriate jQuery UI files and initialize a [draggable](https://jqueryui.com/demos/draggable/) element. Additionally, you must set the calendar's `droppable` option to `true`.

Here is how you might initialize an element that can be dragged onto a calendar:

```js
$('#my-draggable').draggable({
  revert: true,      // immediately snap back to original position
  revertDuration: 0  //
});

$('#calendar').fullCalendar({
  droppable: true,
  drop: function(date, allDay) {
    alert("Dropped on " + date + " with allDay=" + allDay);
  }
});
```

## How can I use this to add events???

Good question. It is a common need to have an "external list of events" that can be dragged onto the calendar.

While the `droppable` option deals with generic jQuery UI draggables and is not specifically tailored to adding events, it is possible to achieve this with a few lines of code. Follow the **external-dragging.html** example in FullCalendar's download. You can also view the [example online](/releases/fullcalendar/1.6.6/demos/external-dragging.html).

In short, you must call [renderEvent](renderEvent) yourself in the [drop](drop) callback.

<div class='version-info' markdown='1'>
Hopefully, this task will become more convenient with future API changes.
</div>
