---
title: render
type: method
since_version: 1.3.1
---

Immediately forces the calendar to render and/or readjusts its size.

<div class='spec' markdown='1'>
.fullCalendar( 'render' )
</div>

This method is useful in the scenario where a tab setup might hide/show a calendar. Call this method whenever the tabs are shown. Here is an example with the [jQuery UI tab plugin](https://jqueryui.com/demos/tabs/):

```js
$('#my-tabs').tabs({
  activate: function(event, ui) {
    $('#calendar').fullCalendar('render');
  }
});
```

Notice that this example calls `render` whenever *any* tab is shown, not just the tab that the calendar is within. This is okay, because FullCalendar is smart enough to only render calendars that are visible to the user.

<div class='version-info' markdown='1'>
Prior to version 1.4.2, the *render* method did not readjust the size of the calendar. It only
rendered the calendar if it was not already rendered.
</div>
