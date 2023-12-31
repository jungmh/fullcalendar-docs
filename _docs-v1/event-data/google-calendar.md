---
title: events from Google Calendar
excerpt_separator: <!--more-->
---

FullCalendar can display events from a public [Google Calendar](https://calendar.google.com/).<!--more--> Google Calendar can serve as a backend that manages and persistently stores event data (a feature that FullCalendar currently lacks).

<div class='warning'>
On Nov 17th 2014, Google shut down V1 and V2 of their Calendar APIs, which FullCalendar relied upon.
Please upgrade to the latest version of FullCalendar or at least replace <code>gcal.js</code> with
<strong><a href='https://github.com/arshaw/fullcalendar/blob/v1.x/gcal.js'>this file</a></strong>
(will work from FullCalendar v1.5.0 until the latest v1.x).
Your own Google Calendar API key is now required.
<strong>Also, the way you specify your event feed is different!</strong>
Read below about <code>googleCalendarApiKey</code> and <code>googleCalendarId</code>.
</div>

## Before you code...

**You must first have a Google Calendar API Key**:

1. Go to the [Google Developer Console](https://console.developers.google.com/) and create a new project (it might take a second).
2. Once in the project, go to **APIs & auth > APIs** on the sidebar.
3. Find "Calendar API" in the list and turn it ON.
4. On the sidebar, click **APIs & auth > Credentials**.
5. In the "Public API access" section, click "Create new Key".
6. Choose "Browser key".
7. If you know what domains will host your calendar, enter them into the box. Otherwise, leave it blank. You can always change it later.
8. Your new API key will appear. It might take second or two before it starts working.

**Make your Google Calendar public:**

1. In the Google Calendar interface, locate the "My calendars" area on the left.
2. Hover over the calendar you need and click the downward arrow.
3. A menu will appear. Click "Share this Calendar".
4. Check "Make this calendar public".
5. Make sure "Share only my free/busy information" is **unchecked**.
6. Click "Save".

**Obtain your Google Calendar's ID:**

1. In the Google Calendar interface, locate the "My calendars" area on the left.
2. Hover over the calendar you need and click the downward arrow.
3. A menu will appear. Click "Calendar settings".
4. In the "Calendar Address" section of the screen, you will see your Calendar ID. It will look something like "abcd1234@group.calendar.google.com".

## Dependencies

Next, you must have all the required js/css files. This includes the standard fullcalendar.js and fullcalendar.css, **in addition to gcal.js**:

```js
<script type='text/javascript' src='fullcalendar/gcal.js'></script>
```

## Writing the code

Now it's time to initialize your calendar in JavaScript. You pass an object into the `events` parameter, with two required properties, `googleCalendarApiKey` and `googleCalendarId`:

```js
<script type='text/javascript'>

$(function() {
  $('#calendar').fullCalendar({
    events: {
      googleCalendarApiKey: '<YOUR API KEY>',
      googleCalendarId: 'abcd1234@group.calendar.google.com',
    }
  });
});

</script>
```

You can also specify some [Event Source options](event-source-object#options):

```js
<script type='text/javascript'>

$(function() {
  $('#calendar').fullCalendar({
    events: {
      googleCalendarApiKey: '<YOUR API KEY>',
      googleCalendarId: 'abcd1234@group.calendar.google.com',
      className: 'gcal-event',           // an option!
      currentTimezone: 'America/Chicago' // an option!
    }
  });
});

</script>
```

## Options

<table>
<tr>
<th>
currentTimezone
</th>
<td>
a string like "America/Chicago".
Consult <a href='https://php.net/manual/en/timezones.php'>https://php.net/manual/en/timezones.php</a> for a full list.
</td>
</tr>
<tr>
<th>
editable
</th>
<td>
whether to allow dragging/resizing (default: <code>false</code>)
</td>
</tr>
<tr>
<th>
className
</th>
<td>
CSS class to attach to each event
</td>
</tr>
<tr>
<th>
&nbsp;
</th>
<td>
<a href='event-source-object#options'>Any of the other Event Source options...</a>
</td>
</tr>
</table>

## Timezones Gotchas

Sometimes it can be confusing as to why FullCalendar displays event times differently than the Google Calendar interface. There are the two factors involved in this:

- *the calendar's timezone*, accessed through "Calendar settings" after clicking the arrow next to the calendar's name
- *your Google Account's timezone*, accessed through the "Settings" link at the top right of the Google Calendar screen (near the "Sign out" link)

When both timezones are the same, you should have no problems. When they are different, FullCalendar will display times in the *calendar's* timezone. Thus, times will be different than what you see in the Google Calendar interface because they are being adjusted to the GMT of the calendar. The solution is to use the `currentTimezone` option. If this is set to the same timezone as your Google Account, all dates should appear consistent.

## Multiple Google Calendars

You can specify multiple Google Calendars by using the `eventSources` option:

```js
<script type='text/javascript'>

$(function() {
  $('#calendar').fullCalendar({
    eventSources: [
      {
        googleCalendarApiKey: "<YOUR API KEY>",
        googleCalendarId: "abcd1234@group.calendar.google.com"
      },
      {
        googleCalendarApiKey: "<YOUR API KEY>",
        googleCalendarId: "ijkl5678@group.calendar.google.com"
      }
    ]
  });
});

</script>
```
