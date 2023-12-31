---
title: dropAccept
since_version: 1.4.7
---

Provides a way to filter which elements can be dropped onto the calendar.

<div class='spec' markdown='1'>
String/Function, *default*: `"*"`
</div>

By default, after setting a calendar' [droppable](droppable) option to `true`, the calendar will accept any draggables that are dropped onto the calendar. The `dropAccept` option allows the calendar be more selective about which elements can/can't be dropped.

The value of `dropAccept` can be a string [jQuery selector](https://api.jquery.com/category/selectors/). It can also be a function that accepts the draggable item as a single argument, and returns `true` if the element can be dropped onto the calendar.

In the following example, the first draggable (with id `"draggable1"`) can be dropped on the calendar, while the second draggable (with id `"draggable2"`) cannot:

```js
...
<div id='calendar'></div>

<div id='draggable1' class='cool-event'></div>
<div id='draggable2'></div>
...
```

and here is the JavaScript:

```js
$('#calendar').fullCalendar({
  droppable: true,
  dropAccept: '.cool-event',
  drop: function() {
    alert('dropped!');
  }
});

$('#draggable1').draggable();
$('#draggable2').draggable();
```
