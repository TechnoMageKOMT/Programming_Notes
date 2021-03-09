# Responsive Web Design (RWD)

Two options:

- Separate mobile website
- Media queries to accomodate all devices. Advantage one website creation

## RWD Meta Tag Required

```
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

This meta tag makes the page accept responsive webdesign styling.

The main target of responsive web design is page **width** not height
Example:
```
@media(max-width: 1000px){
  #test{
    background-color: blue;
  }
}
```
Smallest viewport to accomodate is 320px.
Example of setting up a media query to not print certain sections of the page:
```
@media print {
  .nav,
  .footer,
  .left-column,
  .right-column {
    display:none;
  }
}
```
# Accessibility

## <figure>, <figcaption>

`<figure></figure>` together with `<figcaption></figcaption>` wraps an image, diagram or chart with its caption. 

Example: 
```
<figure>
  <img src="#" alt="Some Description"/>
  <br>
  <figcaption>
    Caption to accompany diagram, image etc.
  </figcaption>
</figure>
```

## <fieldset>

Surrounds grouping of radio button. The legend tag provides a description of the grouping.

```
<form>
  <fieldset>
    <legend>Choose one of these three items:</legend>
    <input id="one" type="radio" name="items" value="one">
    <label for="one">Choice One</label><br>
    <input id="two" type="radio" name="items" value="two">
    <label for="two">Choice Two</label><br>
    <input id="three" type="radio" name="items" value="three">
    <label for="three">Choice Three</label>
  </fieldset>
</form>
```


**VERY NB Accessability is built into HTML5 semantically without the need of CSS so it is important to write these elements into the HTML "Skeleton" of a page
