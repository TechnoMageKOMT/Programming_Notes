# Counters

## Numbered headings or alternative ordered list numbering

This is a way of turning just about anything into an ordered list.

```HTML
<div class="counters">
  <h1>We can number sections!</h1>
  <h2 class="section">Section title here</h2>
  <p>Some paragraph to go with the section title here</p>
  <h2 class="section">Section title here</h2>
  <p>Some paragraph to go with the section title here</p>
  <h2 class="section">Section title here</h2>
  <p>Some paragraph to go with the section title here</p>
  <h2 class="section">Section title here</h2>
  <p>Some paragraph to go with the section title here</p>
  <h2 class="section">Section title here</h2>
  <p>Some paragraph to go with the section title here</p>
  <h2 class="section">Section title here</h2>
  <p>Some paragraph to go with the section title here</p>
</div>
```

```CSS
.counters {
background-color: lightgray;
text-align: left;
padding: 5em 8em;
margin-top: 7em;

counter-reset: counter-name; /*Any name can be used for the counter*/
}

.section {
  position: relative;
}

.section::before {
  counter-increment: counter-name;
  content: counter(counter-name) '. '; /*Any punctuation can be used here*/
  position: absolute;
  left: -2.5em;
  top: -0.5em;
  background-color: white;
  width: 2em;
  height: 2em;
  display: flex;
  justify-content: center;
  align-items: center;
  border-radius: 50%;
  border: 3px solid gray;
  color: gray;
}
```

This can also be done with actual ordered lists:

```CSS
.counter ol {
  list-style: none;
  counter-reset: ordered-list;
}

.counter li::before {
  counter-increment: ordered-list;
  content: counter(ordered-list);
}
```

Once this has been setup, the numbering of the ordered list can now be styled as needed.

**NB** A new counter-reset name is given to each unique list.
