---
title: events (as a json feed)
---

A URL of a JSON feed that the calendar will fetch [Event Objects](event-object) from.

FullCalendar will visit the URL whenever it needs new event data. This happens when the user clicks prev/next or changes views. FullCalendar will determine the date-range it needs events for and will pass that information along in GET parameters.

The GET parameter names will be determined by the [startParam](startParam) and [endParam](endParam) options. (`"start"` and `"end"` by default).

The value of the parameters will always be UNIX timestamps (seconds since 1970).

Consider the following script:

```js
$('#calendar').fullCalendar({
  events: '/myfeed.php'
});
```

Here is a URL that FullCalendar might visit:

`/myfeed.php?start=1262332800&end=1265011200&_=1263178646`

The `_` parameter is automatically inserted to prevent the browser from caching the result ([more below](#caching)).

If you need to access a feed that is in a different domain, you can use JSONP with a `?` in your URL (see the JSONP discussion in [$.ajax](https://api.jquery.com/jQuery.ajax/)).

## Extended Form

Since version 1.5, you are able to specify [Event Source options](event-source-object#options).
This often comes in handy when you are using the [eventSources](eventSources) option to
specify multiple event sources and you want certain options to only apply to certain sources.
However, to do this, you must write things a little differently:

```js
$('#calendar').fullCalendar({

  eventSources: [

    // your event source
    {
      url: '/myfeed.php', // use the `url` property
      color: 'yellow',    // an option!
      textColor: 'black'  // an option!
    }

    // any other sources...

  ]

});
```

A list of general Event Source options can be found [here](event-source-object#options).
<span id='options'>However, there are additional options that apply specifically to JSON feeds:</span>

<table>
<tr>
<th>
startParam
</th>
<td>
Sets the <a href='startParam'>startParam</a> option, but only for this source.
</td>
</tr>
<tr>
<th>
endParam
</th>
<td>
Sets the <a href='endParam'>endParam</a> option, but only for this source.
</td>
</tr>
</table>

## jQuery $.ajax options

You can also specify any of the [jQuery $.ajax](https://api.jquery.com/jQuery.ajax/) options within the same object! This allows you to easily pass additional parameters to your feed script, as well as listen to ajax callbacks:

```js
$('#calendar').fullCalendar({

  eventSources: [

    // your event source
    {
      url: '/myfeed.php',
      type: 'POST',
      data: {
        custom_param1: 'something',
        custom_param2: 'somethingelse'
      },
      error: function() {
        alert('there was an error while fetching events!');
      },
      color: 'yellow',   // a non-ajax option
      textColor: 'black' // a non-ajax option
    }

    // any other sources...

  ]

});
```

Here is the same example, but using the single-source `events` option instead:

```js
$('#calendar').fullCalendar({

  events: {
    url: '/myfeed.php',
    type: 'POST',
    data: {
      custom_param1: 'something',
      custom_param2: 'somethingelse'
    },
    error: function() {
      alert('there was an error while fetching events!');
    },
    color: 'yellow',   // a non-ajax option
    textColor: 'black' // a non-ajax option
  }

});
```

## Dynamic `data` parameter

The `data` parameters, which sends information to your JSON script through either GET or POST, can also be specified as a function, in order to send dynamic values:

```js
$('#calendar').fullCalendar({

  events: {
    url: '/myfeed.php',
    data: function() { // a function that returns an object
      return {
        dynamic_value: Math.random()
      };
    }
  }

});
```

The `startParam` and `endParam` values will still automatically be included.
This feature is new in version 1.6.3.

## Caching

By default, FullCalendar will insert a `_` parameter into the URL of the request to prevent the browser from caching the response. FullCalendar achieves this internally by setting the $.ajax parameter to `false`.

If you would like to counteract this and prevent the `_` parameter, you can set the `cache` option to `true`:

```js
$('#calendar').fullCalendar({

  events: {
    url: '/myfeed.php',
    cache: true
  }

});
```
