---
title: eventDrop
type: callback
---

Triggered when dragging stops and the event has moved to a *different* day/time.

<div class='spec' markdown='1'>
function( *event*, *dayDelta*, *minuteDelta*, *allDay*, *revertFunc*, *jsEvent*, *ui*, *view* ) { }
</div>

`event` is an [Event Object](event-object) that hold the event's information (date, title, etc).

`dayDelta` holds the number of days the event was moved forward (a positive number) or backwards (a negative number).

`minuteDelta` holds the number of minutes the event was moved forward (a positive number) or backwards (a negative number). Only useful for the agenda views. In other views, `0` is passed in.

`dayDelta` and `minuteDelta` are elegant for dealing with multi-day and repeating events. If updating a remote database, just add these values to the start and end times of all events with the given `event.id`.

`allDay` is `true` if the event has been dropped on a day in month view, or the "all-day" slot in the agenda views. It will be `false` if dropped on a slot in the agenda views (meaning it has been assigned a time).

`revertFunc` is a function that, if called, reverts the event's start/end date to the values before the drag. This is useful if an ajax call should fail.

`jsEvent` holds the native JavaScript event with low-level information such as mouse coordinates.

`ui` holds the [jQuery UI object](https://jqueryui.com/demos/draggable/).

`view` holds the current [View Object](view-object).

Here is an example demonstrating most of these arguments:

```js
$('#calendar').fullCalendar({
  events: [
    // events here
  ],
  editable: true,
  eventDrop: function(event,dayDelta,minuteDelta,allDay,revertFunc) {

    alert(
      event.title + " was moved " +
      dayDelta + " days and " +
      minuteDelta + " minutes."
    );

    if (allDay) {
      alert("Event is now all-day");
    }else{
      alert("Event has a time-of-day");
    }

    if (!confirm("Are you sure about this change?")) {
      revertFunc();
    }

  }
});
```

<div class='version-info' markdown='1'>
Prior to version 1.4, the *allDay* paramameter was not included.

Prior to version 1.3, the *revertFunc* parameter was not included.
</div>
