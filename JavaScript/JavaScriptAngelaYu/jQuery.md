# jQuery

## What is jQuery

The most popular JavaScript Library.

Library of code written externally that can be incorporated into own code to improve one's own efficiency or even the efficiency of one's own code.  

```JavaScript
document.querySelector('h1');
```

```jQuery
jQuery('h1);
```

or even better:

```jQuery
$('h1')
```

## How to make use of it (CDN)

The most popular Content Delivery Network (CDN) for jQuery is Google's (there is a link to the snippets on the jquery.com download section). Use the `<script>` tag with the latest version of jQuery (3.6.0 at the writing of this document March 2021).

Reminder: Great thing about a CDN is that if a user has visit a particular CDN for some other website, it is likely to already be cached in their browser's memory.

The position of the `<scrip>` tag is **very NB**. It must be above the local js scripts. This is so that the library is available for the excecution of the code written in jQuery in the local js scripts. If this is not done, the browser will simply give not defined errors on all jQuery commands encountered.  

