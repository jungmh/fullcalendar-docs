---
title: aspectRatio
since_version: 1.3
---

Determines the width-to-height aspect ratio of the calendar.

<div class='spec' markdown='1'>
Float, *default*: `1.35`
</div>

A calendar is a block-level element that fills its entire available width. The calendar’s height, however, is determined by this ratio of width-to-height. (Hint: larger numbers make smaller heights).

The following example will initialize a calendar who's width is twice its height:

```js
$('#calendar').fullCalendar({
  aspectRatio: 2
});
```

## Setter

You can dynamically set a calendar's aspectRatio after initialization:

```js
$('#calendar').fullCalendar('option', 'aspectRatio', 1.8);
```

<div class='version-info' markdown='1'>
The *setter* only works in version 1.4.2 and later.
</div>
