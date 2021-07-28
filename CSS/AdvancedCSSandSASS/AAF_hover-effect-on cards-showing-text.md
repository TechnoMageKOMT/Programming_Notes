# Hover effect on cards

This effect will show text appearing on cards or images when the mouse hovers over the cards:

```HTML
<div class="container">
  <div class="card">
    <img src="#" alt="" class="card__img">
    <div class="card__text">
      <h3 class="card__title">Card Title</h3>
      <p class="card__body">And here is some text</p>
    </div>
  </div>
  <div class="card">
    <img src="#" alt="" class="">
    <div class="card__text">
      <h3 class="card__title">Card Title</h3>
      <p class="card__body">And here is some text</p>
    </div>
  </div>
</div>
```

```SCSS
.card {
  position: relative;
  margin: 1em;
  background-color: grey;

  &::after,
  &::before {
    content: '';
    position: absolute;
    top: 1.25em;
    bottom: 1.25em;
    left: 1.25em;
    right: 1.25em;
  }

  &::before{
    transform: scale(0, 1); /*I.e., scaleX = 0 and scaleY = 1*/
    transition: transform 250ms ease-out;
    border-top: 1px solid white;
    border-bottom: 1px solid white;
  }

  &::after {
    transform: scale(1, 0); /*I.e., scaleX = 1 and scaleY = 0*/
    transition: transform 250ms ease-out;
    border-left: 1px solid white;
    border-right: 1px solid white;
  }

  &:hover::before {
    transform: scale(1.05, 1); /*I.e., scaleX=1 and scaleY=1*/
  }

  &:hover::after {
    transform: scale(1, 1.05)
  }

}

.card__img {
  max-width: 100%;
  display: block;
  transition: opacity 250ms ease-out;
  opacity: 1;
}

.card:hover .card__img {
  opacity: 0.4;
}

.card__text {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  color: white;
  opacity: 0;
  transition: opacity 250ms ease-out;
}

.card:hover .card__text {
  opacity: 1;
}

.card__title {
  font-size: 2rem;
  color: white;
  margin-bottom: 0;
}
```
