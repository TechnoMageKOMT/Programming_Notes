# CSS popup "modal"

```HTML
<div class="popup" id="popup">
      <div class="popup__content">
        <div class="popup__left">
          <img src="img/nat-8.jpg" alt="Tour photo" class="popup__img" />
          <img src="img/nat-9.jpg" alt="Tour photo" class="popup__img" />
        </div>
        <div class="popup__right">
          <a href="#section-tours" class="popup__close">&times;</a>
          <h2 class="heading-secondary u-margin-bottom-small">
            Start booking now
          </h2>
          <h3 class="heading-tertiary u-margin-bottom-small">
            Important &ndash; Please read these terms before booking
          </h3>
          <p class="popup__text">
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Beatae
            tempore qui doloribus facere illo sit deleniti rem eaque ullam at
            nisi in, accusamus nesciunt cumque fuga recusandae sequi ab possimus
            eius iure aliquam aut magni incidunt odio. Expedita consectetur
            tenetur eius porro tempora provident dolorum?
          </p>
          <a href="#" class="btn btn--green">Book now</a>
        </div>
      </div>
</div>
```

```SCSS
.popup {
  height: 100vh;
  width: 100%;
  position: fixed;
  top: 0;
  left: 0;
  background-color: rgba($color-black, 0.8);
  z-index: 9999;
  opacity: 0;
  visibility: hidden;
  transition: all 0.4s ease;
  -webkit-transition: all 0.4s ease;
  -moz-transition: all 0.4s ease;
  -ms-transition: all 0.4s ease;
  -o-transition: all 0.4s ease;

  &__content {
    @include absCenter;
    width: 75%;
    background-color: $color-white;
    box-shadow: 0 2.5rem 4rem rgba($color-black, 0.4);
    border-radius: 4px;
    -webkit-border-radius: 4px;
    -moz-border-radius: 4px;
    -ms-border-radius: 4px;
    -o-border-radius: 4px;
    display: table;
    overflow: hidden;
    opacity: 0;
    transform: translate(-50%, -50%) scale(0.5);
    -webkit-transform: translate(-50%, -50%) scale(0.5);
    -moz-transform: translate(-50%, -50%) scale(0.5);
    -ms-transform: translate(-50%, -50%) scale(0.5);
    -o-transform: translate(-50%, -50%) scale(0.5);
    transition: all 400ms ease 200ms;
    -webkit-transition: all 400ms ease 200ms;
    -moz-transition: all 400ms ease 200ms;
    -ms-transition: all 400ms ease 200ms;
    -o-transition: all 400ms ease 200ms;
  }

  &__left {
    width: 33.333333%;
    display: table-cell;
  }

  &__right {
    width: 66.666667%;
    display: table-cell;
    vertical-align: middle;
    padding: 3rem 5rem;
  }

  &__img {
    display: block;
    width: 100%;
  }

  &__text {
    font-size: 1.4rem;
    margin-bottom: 4rem;
    column-count: 2;
    column-gap: 4rem;
    column-rule: 1px solid $color-grey-light-2;
    hyphens: auto;
    -webkit-hyphens: auto;
    -moz-hyphens: auto;
    -ms-hyphens: auto;
  }

  &:target {
    opacity: 1;
    visibility: visible;
  }

  &:target &__content {
    opacity: 1;
    transform: translate(-50%, -50%) scale(1);
    -webkit-transform: translate(-50%, -50%) scale(1);
    -moz-transform: translate(-50%, -50%) scale(1);
    -ms-transform: translate(-50%, -50%) scale(1);
    -o-transform: translate(-50%, -50%) scale(1);
  }

  &__close {
    &:link,
    &:visited {
      color: $color-grey-dark;
      position: absolute;
      top: 2.5rem;
      right: 2.5rem;
      font-size: 3rem;
      text-decoration: none;
      display: inline-block;
      transition: all 400ms ease;
      -webkit-transition: all 400ms ease;
      -moz-transition: all 400ms ease;
      -ms-transition: all 400ms ease;
      -o-transition: all 400ms ease;
      line-height: 1;
    }

    &:hover {
      color: $color-primary;
    }
  }
}
```
