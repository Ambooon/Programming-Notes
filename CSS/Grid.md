# Grid Container Properties

1. **`display: grid;`**
    
    - Defines an element as a grid container.

2. **`grid-template-columns`**
    - Defines the number and size of columns in the grid.
    - Example: `grid-template-columns: 100px 200px;` (creates two columns with widths of 100px and 200px).
    
3. **`grid-template-rows`**
    - Defines the number and size of rows in the grid.
    - Example: `grid-template-rows: 50px 100px;` (creates two rows with heights of 50px and 100px).
    
4. **`grid-template-areas`**
    - Defines a grid template by referencing grid areas.
    - Example:
        
```css
grid-template-areas:   "header header"   "sidebar content"   "footer footer";
```

5. **`grid-column-gap`** (or **`column-gap`**)
    - Defines the gap between columns.
    - Example: `grid-column-gap: 10px;`
    
6. **`grid-row-gap`** (or **`row-gap`**)
    - Defines the gap between rows.
    - Example: `grid-row-gap: 10px;
    
7. **`grid-gap`** (or **`gap`**)
    - Defines the gap between rows and columns simultaneously.
    - Example: `grid-gap: 10px 20px;` (first value is for row gap, second for column gap).
    
8. **`grid-auto-rows`**
    - Defines the size of rows that are automatically created.
    - Example: `grid-auto-rows: 100px;`
    
1. **`grid-auto-columns`**
    - Defines the size of columns that are automatically created.
    - Example: `grid-auto-columns: 100px;`
    
1. **`grid-auto-flow`**
    - Controls how auto-placed items are flowed into the grid.
    - Example: `grid-auto-flow: row;` (places items by row, then column).

# Grid Item Properties

1. **`grid-column-start`**
    - Specifies where an item starts on the column axis.
    - Example: `grid-column-start: 1;`
2. **`grid-column-end`**
    - Specifies where an item ends on the column axis.
    - Example: `grid-column-end: 3;`
3. **`grid-row-start`**
    - Specifies where an item starts on the row axis.
    - Example: `grid-row-start: 1;`
4. **`grid-row-end`**
    - Specifies where an item ends on the row axis.
    - Example: `grid-row-end: 3;`
5. **`grid-column`**
    - A shorthand for `grid-column-start` and `grid-column-end`.
    - Example: `grid-column: 1 / 3;`
6. **`grid-row`**
    - A shorthand for `grid-row-start` and `grid-row-end`.
    - Example: `grid-row: 1 / 3;`
7. **`justify-self`**
    - Aligns an item inside its grid area along the inline (row) axis.
    - Example: `justify-self: center;`
8. **`align-self`**
    - Aligns an item inside its grid area along the block (column) axis.
    - Example: `align-self: start;`
9. **`place-self`**
    - A shorthand for `align-self` and `justify-self`.
    - Example: `place-self: center;`
10. **`justify-items`**
    - Aligns all items inside their respective grid areas along the inline (row) axis.
    - Example: `justify-items: start;`
11. **`align-items`**
    - Aligns all items inside their respective grid areas along the block (column) axis.
    - Example: `align-items: end;`
12. **`place-items`**
    - A shorthand for `align-items` and `justify-items`.
    - Example: `place-items: center;`