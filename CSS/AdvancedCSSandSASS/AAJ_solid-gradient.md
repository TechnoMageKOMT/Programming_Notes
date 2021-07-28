# Solid gradient technique

This technique will cover only a section of an image in a transparent layer leaving the rest of the background image exposed. See bookings page in the Natours page.

```HTML
<section class="section-book">
  <div class="row">
    <div class="book">

    </div>
  </div>
</section>
```

```SCSS
.section-book {
  padding: 15rem 0;
  background-image: linear-gradient(
    to right bottom,
    $color-primary-light,
    $color-primary-dark
  );
}

.book {
  background-image: linear-gradient(
      105deg,
      rgba($color-white, 0.9) 0%,
      rgba($color-white, 0.9) 50%,
      transparent 50%
    ),
    url(../../img/nat-10.jpg);
  background-size: cover;
  height: 50rem;
  border-radius: 4px;
  -webkit-border-radius: 4px;
  -moz-border-radius: 4px;
  -ms-border-radius: 4px;
  -o-border-radius: 4px;
  box-shadow: 0 2.5rem 4rem rgba($color-black, 0.4);
}
```
