---
title: formatDate
---

Formats a Date object into a string.

<div class='spec' markdown='1'>
$.fullCalendar.formatDate( *date*, *formatString* [, *options* ] ) -> String
</div>

Prior to version 1.3, formatDate accepted a very different format. [See here](formatDate-pre-13).

`formatString` is a combination of any of the following commands:

- **s** - seconds
- **ss** - seconds, 2 digits
- **m** - minutes
- **mm** - minutes, 2 digits
- **h** - hours, 12-hour format
- **hh** - hours, 12-hour format, 2 digits
- **H** - hours, 24-hour format
- **HH** - hours, 24-hour format, 2 digits
- **d** - date number
- **dd** - date number, 2 digits
- **ddd** - date name, short
- **dddd** - date name, full
- **M** - month number
- **MM** - month number, 2 digits
- **MMM** - month name, short
- **MMMM** - month name, full
- **yy** - year, 2 digits
- **yyyy** - year, 4 digits
- **t** - 'a' or 'p'
- **tt** - 'am' or 'pm'
- **T** - 'A' or 'P'
- **TT** - 'AM' or 'PM'
- **u** - ISO8601 format
- **S** - 'st', 'nd', 'rd', 'th' for the date
- **W** - the [ISO8601 week number](https://en.wikipedia.org/wiki/ISO_8601#Week_dates)


Special Characters:

`'...'`
:   literal text

`''`
:   single quote (represented by two single quotes)

`(...)`
:   only displays format if one of the enclosed variables is non-zero


The `options` parameter can be used to override default locale options, such as [monthNames](monthNames), [monthNamesShort](monthNamesShort), [dayNames](dayNames), and [dayNamesShort](dayNamesShort).
