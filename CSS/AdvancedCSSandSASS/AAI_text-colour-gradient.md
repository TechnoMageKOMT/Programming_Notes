# Text: Colour gradient

This effect results in coloured text with a gradient inside the lettering.

```SCSS
.some-text-selector-here {
  font-size: 3.5rem;
  background-image: linear-gradient(
    to right,
    $color-primary-light,
    $color-primary-dark
  );
  color: transparent;
  background-clip: text;
  -webkit-background-clip: text;
```
