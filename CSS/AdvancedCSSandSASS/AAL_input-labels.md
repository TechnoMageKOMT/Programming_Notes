# Dynamic input labels

## Invisible labels

With this effect the label will be invinsible unless the input field is focussed. I.e., When not focussed there will be placeholder text and while entering the information, the label will be visible as a guide to the user.

To do this the `immediate sibling after` selector is needed to do this. So,

```SCSS
&__label {
    font-size: 1.2rem;
    font-weight: 700;
    margin-left: 2rem;
    margin-top: 0.7rem;
    display: block;
    transition: all 0.4s ease-out;
    -webkit-transition: all 0.4s ease-out;
    -moz-transition: all 0.4s ease-out;
    -ms-transition: all 0.4s ease-out;
    -o-transition: all 0.4s ease-out;
  }

  &__input:placeholder-shown + &__label {
    opacity: 0;
    visibility: hidden;
    transform: translateY(-4rem);
    -webkit-transform: translateY(-4rem);
    -moz-transform: translateY(-4rem);
    -ms-transform: translateY(-4rem);
    -o-transform: translateY(-4rem);
  }
```
