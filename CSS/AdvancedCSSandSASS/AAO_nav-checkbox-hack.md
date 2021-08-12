# Navigation button with checkbox hack

```HTML
<div class="navigation">
      <input
        type="checkbox"
        name=""
        id="navi-toggle"
        class="navigation__checkbox"
      />
      <label for="navi-toggle" class="navigation__button">MENU</label>
      <div class="navigation__background">&nbsp;</div>
      <nav class="navigation__nav">
        <ul class="navigation__list">
          <li class="navigation__item">
            <a href="#" class="navigation__link"
              ><span>01</span>About Natours</a
            >
          </li>
          <li class="navigation__item">
            <a href="#" class="navigation__link"
              ><span>02</span>Your benefits</a
            >
          </li>
          <li class="navigation__item">
            <a href="#" class="navigation__link"
              ><span>03</span>Popular tours</a
            >
          </li>
          <li class="navigation__item">
            <a href="#" class="navigation__link"><span>04</span>Stories</a>
          </li>
          <li class="navigation__item">
            <a href="#" class="navigation__link"><span>05</span>Book now</a>
          </li>
        </ul>
      </nav>
    </div>
```

```SCSS
.navigation {
  &__checkbox {
    display: none;
  }

  &__button {
    background-color: $color-white;
    height: 7rem;
    width: 7rem;
    position: fixed;
    top: 6rem;
    right: 6rem;
    border-radius: 50%;
    -webkit-border-radius: 50%;
    -moz-border-radius: 50%;
    -ms-border-radius: 50%;
    -o-border-radius: 50%;
    z-index: 2000;
    box-shadow: 0 1rem 3rem rgba($color-black, 0.1);
    text-align: center;
    cursor: pointer;
  }

  &__background {
    height: 6rem;
    width: 6rem;
    border-radius: 50%;
    -webkit-border-radius: 50%;
    -moz-border-radius: 50%;
    -ms-border-radius: 50%;
    -o-border-radius: 50%;
    position: fixed;
    top: 6.5rem;
    right: 6.5rem;
    background-image: radial-gradient(
      $color-primary-light,
      $color-primary-dark
    );
    z-index: 1000;
    transition: transform 0.8s cubic-bezier(0.86, 0, 0.07, 1);
    -webkit-transition: transform 0.8s cubic-bezier(0.86, 0, 0.07, 1);
    -moz-transition: transform 0.8s cubic-bezier(0.86, 0, 0.07, 1);
    -ms-transition: transform 0.8s cubic-bezier(0.86, 0, 0.07, 1);
    -o-transition: transform 0.8s cubic-bezier(0.86, 0, 0.07, 1);
  }

  &__nav {
    height: 100vh;
    position: fixed;
    top: 0;
    right: 0;
    z-index: 1500;
    opacity: 0;
    width: 0;
    transition: all 0.8s cubic-bezier(0.68, -0.55, 0.265, 1.55);
    -webkit-transition: all 0.8s cubic-bezier(0.68, -0.55, 0.265, 1.55);
    -moz-transition: all 0.8s cubic-bezier(0.68, -0.55, 0.265, 1.55);
    -ms-transition: all 0.8s cubic-bezier(0.68, -0.55, 0.265, 1.55);
    -o-transition: all 0.8s cubic-bezier(0.68, -0.55, 0.265, 1.55);
  }

  &__list {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    -webkit-transform: translate(-50%, -50%);
    -moz-transform: translate(-50%, -50%);
    -ms-transform: translate(-50%, -50%);
    -o-transform: translate(-50%, -50%);
    list-style: none;
    text-align: center;
    width: 100%;
  }

  &__item {
    margin: 1rem;
  }

  &__link {
    &:link,
    &:visited {
      display: inline-block;
      font-size: 3rem;
      font-weight: 300;
      padding: 1rem 2rem;
      color: $color-white;
      text-decoration: none;
      text-transform: uppercase;
      background-image: linear-gradient(
        120deg,
        transparent 0%,
        transparent 50%,
        $color-white 50%
      );
      background-size: 220%;
      transition: all 0.4s ease;
      -webkit-transition: all 0.4s ease;
      -moz-transition: all 0.4s ease;
      -ms-transition: all 0.4s ease;
      -o-transition: all 0.4s ease;

      span {
        margin-right: 1.5rem;
        display: inline-block;
      }
    }

    &:hover,
    &:active {
      background-position: 100%;
      color: $color-primary;
      transform: translateX(1rem);
      -webkit-transform: translateX(1rem);
      -moz-transform: translateX(1rem);
      -ms-transform: translateX(1rem);
      -o-transform: translateX(1rem);
    }
  }

  &__checkbox:checked ~ &__background {
    transform: scale(80);
    -webkit-transform: scale(80);
    -moz-transform: scale(80);
    -ms-transform: scale(80);
    -o-transform: scale(80);
  }

  &__checkbox:checked ~ &__nav {
    opacity: 1;
    width: 100%;
  }

  &__icon {
    position: relative;
    margin-top: 3.5rem;

    &,
    &::after,
    &::before {
      width: 3rem;
      height: 2px;
      background-color: $color-grey-dark-3;
      display: inline-block;
    }

    &::after,
    &::before {
      content: '';
      position: absolute;
      left: 0;
      transition: all 0.4s ease;
      -webkit-transition: all 0.4s ease;
      -moz-transition: all 0.4s ease;
      -ms-transition: all 0.4s ease;
      -o-transition: all 0.4s ease;
    }

    &::after {
      top: 0.8rem;
    }

    &::before {
      top: -0.8rem;
    }
  }

  &__button:hover &__icon::before {
    top: -1rem;
  }

  &__button:hover &__icon::after {
    top: 1rem;
  }

  &__checkbox:checked + &__button &__icon {
    background-color: transparent;
  }

  &__checkbox:checked + &__button &__icon::before {
    top: 0;
    transform: rotate(135deg);
    -webkit-transform: rotate(135deg);
    -moz-transform: rotate(135deg);
    -ms-transform: rotate(135deg);
    -o-transform: rotate(135deg);
  }

  &__checkbox:checked + &__button &__icon::after {
    top: 0;
    transform: rotate(-135deg);
    -webkit-transform: rotate(-135deg);
    -moz-transform: rotate(-135deg);
    -ms-transform: rotate(-135deg);
    -o-transform: rotate(-135deg);
  }
}
```
