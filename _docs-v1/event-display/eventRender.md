---
title: eventRender
type: callback
---

Triggered while an event is being rendered.

<div class='spec' markdown='1'>
function( *event*, *element*, *view* ) { }
</div>

`event` is the [Event Object](event-object) that is attempting to be rendered.

`element` is a newly created jQuery `<div>` that will be used for rendering.
It has already been populated with the correct time/title.

The `eventRender` callback function can modify `element`, return a brand new DOM element that will be used for rendering instead, or it can return `false`, which will prevent the event from being rendered at all.

`eventRender` is a great way to attach other jQuery plugins to event elements, such as a [qTip](https://craigsworks.com/projects/qtip/) tooltip effect:

```js
$('#calendar').fullCalendar({
  events: [
    {
      title: 'My Event',
      start: '2010-01-01',
      description: 'This is a cool event'
    }
    // more events here
  ],
  eventRender: function(event, element) {
    element.qtip({
      content: event.description
    });
  }
});
```

Note that `description` is a non-standard Event Object field, which is allowed.
