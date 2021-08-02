# Styling radio buttons

It is not possible to style radiobuttons with CSS, but the following approach effectively results in styled radio buttons even though the HTML button are set to display: none.

```HTML
<div class="form__group u-margin-bottom-medium">
  <div class="form__radio-group">
    <input
      type="radio"
      name="size"
      id="small"
      class="form__radio-input"
    />
    <label for="small" class="form__radio-label">
      <span class="form__radio-button"></span>
      Small tour group
    </label>
  </div>
  <div class="form__radio-group">
    <input
      type="radio"
      name="size"
      id="large"
      class="form__radio-input"
    />
    <label for="large" class="form__radio-label">
      <span class="form__radio-button"></span>
      Large tour group
    </label>
  </div>
</div>
```

```SCSS
&__radio-group {
    width: 49%;
    display: inline-block;
  }

  &__radio-input {
    display: none;
  }

  &__radio-label {
    font-size: $default-font-size;
    cursor: pointer;
    position: relative;
    padding-left: 5rem;
  }

  &__radio-button {
    height: 3rem;
    width: 3rem;
    border: 5px solid $color-primary;
    border-radius: 50%;
    -webkit-border-radius: 50%;
    -moz-border-radius: 50%;
    -ms-border-radius: 50%;
    -o-border-radius: 50%;
    display: inline-block;
    position: absolute;
    left: 0;
    top: -0.4rem;

    &::after {
      content: '';
      display: block;
      height: 1.3rem;
      width: 1.3rem;
      background-color: $color-primary;
      border-radius: 50%;
      -webkit-border-radius: 50%;
      -moz-border-radius: 50%;
      -ms-border-radius: 50%;
      -o-border-radius: 50%;
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      -webkit-transform: translate(-50%, -50%);
      -moz-transform: translate(-50%, -50%);
      -ms-transform: translate(-50%, -50%);
      -o-transform: translate(-50%, -50%);
      opacity: 0;
      transition: opacity 0.4s ease;
      -webkit-transition: opacity 0.4s ease;
      -moz-transition: opacity 0.4s ease;
      -ms-transition: opacity 0.4s ease;
      -o-transition: opacity 0.4s ease;
    }
  }

  &__radio-input:checked ~ &__radio-label &__radio-button::after {
    opacity: 1;
  }
```
