# Complex DOM rendering

## Location Object

The location object contains information about the current URL. The location object is part of the window object and is accessed through the window.location property.

The method `location.assign('url')` can be used to redirect to either a relative local URL or to an external URL.

The method `location.hash.substring(1)` would produce the string after the # symbol in the url.

## The global 'window' object

`window.innerHeight` - The browser's current inner height
`window.innerWidth` - The browser's current inner width
`window.concole.log` - Same as console.log
`window.document` - Same as document

The window object is often used to attach event listeners to if the event is not attached to a specific DOM element. A specific example is the `storage` event which fires whenever any data in `localstorage` is changed. Specifically if two tabs are open with the same application and there is a change on tab 1, the event will fire on tab 2.
