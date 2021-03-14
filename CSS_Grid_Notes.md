# CSS Grid

## Grid: Basics

### Grid Container

The first step is to create a grid container and to set the `display` property to the value `grid`:

```CSS
.grid-container {
  display: grid;
}
```

### Grid Track: Column

These are also assigned to the grid container class. In its most basic form the `grid-template-columns` property accept lengths specified per column and the number of columns:

```CSS
.grid-container {
  display: grid;
  grid-template-columns: 200px 200px;
}
```

This specification is for two columns each 200px wide. Relative values, such as percentage, em, rem or viewport lengths could also be used. Measurement units can also be mixed. In the following code the columns with size auto allocated to them would automatically take up the available remaining space relative to the grid container's width.

```CSS
.grid-container {
  display: grid;
  grid-template-columns: auto auto 200px 200px;
}
```

There is also a max-content value which will take up the maximum width based on the inner content of the column as well as a min-content value which will set the width of the column to the minimum allowable by its inner content.

```CSS
.grid-container {
  display: grid;
  grid-template-columns: auto auto max-content min-content;
}
```

There are also some more advanced feature which can be applied, but these will be dealt with in later sections.

### Grid Track: Row

The grid horizonal track or rows are handled with the `grid-template-rows` property and this property follows the same basic rules and operations as the `grid-template-columns` property above.

**NB** If there are more than one row (based on the number of columns and grid items), and only the first has a height assigned to it, the other rows will default to auto. This depends on content and the available space in the grid-container, so it is best to explicitly assign heights to all rows.

**NB** When using relative measurement units make sure a fixed height value is set for the grid container. If this is not done, auto values will be used for the row heights, which will probably be based on their contents.

The syntax and rules are the same for both the `grid-template-columns` and `grid-template-rows`.

### Grid Fraction

A fr (pronounced var) represents a fraction of space within a grid container. Specifying only 1fr widths or heights would, for instance result in equal column or row widths or heights:

```CSS
.grid-container {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
```

A specification of 2fr on one of these columns would mean it would take up twice as much space as the other two.
A specification of 3fr 1fr 1fr 1fr 3fr would mean the 3fr columns each takes up 3 times as much space as the one 1fr column. Another way of viewing this is that a 3fr column takes up 3/9 units of space and a 1fr column 1/9 units of available space.

The fr units can also be combined with other length values. When combined with fixed length the remaining space will be devided by between the fr units as specified. So if the container width is 400px and the specification is 200px 1fr 1fr, then the first column would be fixed at 200px and each fr unit column would take up 100px. Added together this would then be 400px.

**Responsive Web Design** The fr unit is extremely important when applying the grid to responsive web design, so it should be used as the preferred method of measurement and the other, especially fixed units, should only be used when needed for specific reasons.

### Grid Gaps

### Grid Repeat Function

### Grid Column Start, Grid Column End and the Shorthand Property

### Grid Row Start, Grid Row End and the Shorthand Property

### Grid Minmax Function

### Grid Name Lines

### Grid Auto-Fill

### Grid: Difference Between Auto-Fill and Auto-Fit

### Grid Auto Rows

### Grid Auto Columns

### Grid: Explicit vs Implicit

### Grid Auto Flow

### Grid Template Areas

### Inline-grid and Grid Shorthand Property
