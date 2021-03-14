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

To apply gutters or gaps between rows and columns use the `row-gap` and `column-gap` (used to be called grid-row-gap and grid-column-gap). Any of the measurement units can be used. Fixed or relative.

There is also a shorthand version `gap` (used to be grid-gap). If a single value is specified, the row and column gaps will be equal. If two values are specified, the first will be the row-gap and the second the column-gap.

It is best practice to use the shorthand method with a single value unless there is a specific reason to use the gaps in the styling of the page.

### Grid Repeat Function

If dealing with equal column or row sizes the repeat function can be used to speed things up and avoid repetitive code.

Instead of specifying the `grid-template-column` and `grid-template-row` dimensions individually for every respective row and column. The following function is used

```CSS
.grid-container {
  display: grid;
  grid-template-columns: repeat(5, 1fr);
}
```

The first value is the number of repeats and the second, the width or height respectively.

It can also be used for repeating sequences of differing dimension:

```CSS
.grid-container {
  display: grid;
  grid-template-columns: repeat(2, 100px 20rem 10%);
```

This sequence will be repeated twice so there will be 6 columns in total.

### Grid Column Start, Grid Column End and the Shorthand Property

These properties allow control over individual columns. These are applied to the individual items or cells of the grid. (Usually by way of a class and styling of that class).

`grid-column-start` Specifies the starting position of a cell.

```CSS
.custom-column {
  background-color: lawngreen;
  grid-column-start: 2;
}
```

This code will move the first cell so that it starts at line two. The other cells will move one column over as well. Any starting position can be specified, but be aware that if starting positions larger than the existing grid will cause additional column(s) to be created.

`grid-column-end` Specifies the ending position of a cell.

```CSS
.custom-column {
  background-color: lawngreen;
  grid-column-start: 1;
  grid-column-end: 4;
}
```

This code specifies that the first cell take up the space of the first 3 horizontal cells in the top row spanning columns 1, 2 and 3.

There is a shorthand for both properties, `grid-column`. It accepts two values. The first is the starting point and the second the end point and they are seperated by a forward slash (/).

```CSS
.custom-column {
  background-color: lawngreen;
  grid-column: 1 / 4;
}
```

The keyword span can also be used instead of the ending position. This will be the number of columns that the cell should span. The code below will start at the first line and span two columns.

```CSS
.custom-column {
  background-color: lawngreen;
  grid-column: 1 / span 2;
}
```

Good practice: Choose a syntax that works for you and then stick to that syntax.

### Grid Row Start, Grid Row End and the Shorthand Property

Grid rows are controlled in the same way by the `grid-row-start`, `grid-row-end` and the shorthand `grid-row`. All rules and usage are the same except that it is applied to rows and not columns.

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
