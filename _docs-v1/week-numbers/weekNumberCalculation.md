---
title: weekNumberCalculation
since_version: 1.6
---

The method for calculating week numbers that are displayed with the [weekNumbers](weekNumbers) setting.

<div class='spec' markdown='1'>
String/Function, *default*:`"iso"`
</div>

The default (`"iso"`) causes [ISO8601 week numbers](https://en.wikipedia.org/wiki/ISO_8601#Week_dates).

You may also specify a function, which accepts a single native Date object and returns an integer week number. Since FullCalendar currently lacks a built-in internationlization system, this is only way to implement localized week numbers.
