# Vertical centering

1. display: table
2. Absolute positioning with transform
3. display: flex
4. display: grid
5. display grid with margin auto

## 4

```SCSS
.parent {
  display: grid;
  place-items: center;
}
```

## 5

```SCSS
.parent {
  display: grid;
}

.child {
  margin: auto;
}
```
