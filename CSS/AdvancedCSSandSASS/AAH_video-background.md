# Video looping in the background of a section

```HTML
<div class="bg-video">
  <video class="bg-video__content" autoplay muted loop>
    <source src="img/video.mp4" type="video/mp4" />
    <source src="img/video.webm" type="video/webm" />
    Your browser is not supported!
  </video>
</div>
```

```SCSS
.section-stories {
  padding: 15rem 0;
  position: relative; /*Parent should have relative positioning*/
}

.bg-video {
  position: absolute;
  top: 0;
  left: 0;
  height: 100%; //Same as parent
  width: 100%; //Same as parent
  z-index: -1;
  opacity: 0.15;
  overflow: hidden;

  &__content {
    height: 100%;
    width: 100%;
    object-fit: cover;
  }
}
```
