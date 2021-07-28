# Pseudoelements ::after and ::before

Inserts after/before an elements content **not** after/before the element itself. It cannot be used with `<img>` because there is no content with the `<img>` tag. The element is the content.

The pseudoelements are inline by default, but can be styled differently.

## url

It can be used to insert an image after/before content by using the url value:

```CSS
element::after {
  content: url(https://someurl.com);
}
```
