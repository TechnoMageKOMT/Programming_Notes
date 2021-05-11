# CSS Grid Alignment

There are six properties used for alignment in the CSS Grid:

- Justify-content
- Align-content
- Justify-items
- Align-items
- Justify-self
- Align-self

These properties are identical to the flex-box properties of the same names.  

Most of the properties are applied to the grid container, but some can be applied to the items as well.  

There are two axis available during CSS Grid manipulation. The first is called the inline / row or X axis and uses the justify properties. The x axis runs from left to right.

The other axis is called the block / column or Y axis. It uses align properties. The y axis runs from top to bottom  

## justify-content  

The value for this propertyapplies to horizintal alignment and is applied to the grid container.

**center**
**left** 
**right** / **end**
**left** / **start**
**space-between**
**space-around**
**space-evenly**
**safe center** This allows overflow to just one side of the container upon resizing of the viewport
**unsafe center** Allows overflow to both sides of the grid container upon resizing

The safe and unsafe properties are rarely used but good to know about.

## align-content

The value for this propertyapplies to vertical alignment and is applied to the grid container.

**center**
**start** -Top of the container
**end** - Bottom of the container
**flex-end** Defaults to end value if flexbob items are not found
**flex-start** Same as above
**space-between**
**space-around**
**space-evenly**

The safe and unsafe keywords also applies as mentioned under the justify-content section.

## Justify-items

This property is also attached to the grid container. It centers the items horizintally within each grid cell relative to the columns within which they are situated.  

**center**
**left** / **start**
**right** / **end**
**flex-start** / **flex-end**  same as above.

The safe and unsafe keywaords also still apply.

## align-items

Similar to align-content but alignment is relative to the rows that they are in.

**center**
**start**
**end**

The safe and unsafe keywords also apply.

## justify-self

This allows for individual item alignment along the x-axis. It has the same properties and values as justify-items, but deals with individual items.

## align-self

Same as justify self, but for vertical alignment.

## place-content, place-item, place-self

These properties will allow setting positioning along both axis simultaneously.

### place-content

Shorthand for align-content and justify-content properties. The property accepts two values. The first is the align-content and the second the justify-content property. **NB** This is the spacing of the grid cells and **not** the items.

### place-items

Shorthand for align-items and justify-items properties. Same conventions as above. **NB** this aligns the grid items.

### place-self

This property is used for individual items. It is placed on the items and not the grid and also takes two values. The first is align-self and the second is justify-self.

### areas-alignmnet

**NBNBNB** If any of the align or justify self properties are used on an element, its size will be reduced to the minimum size of its content.