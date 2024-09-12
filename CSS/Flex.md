### Flex Container Properties

1. **`display: flex`**  
    Establishes a flex container and enables flex context for its children.
    
2. **`flex-direction`**  
    Defines the direction of the main axis (row or column).
    
    - `row` (default): Horizontal axis.
    - `column`: Vertical axis.
    - `row-reverse`: Horizontal axis, reversed.
    - `column-reverse`: Vertical axis, reversed.
3. **`flex-wrap`**  
    Controls whether flex items should wrap onto multiple lines.
    
    - `nowrap` (default): All items stay on one line.
    - `wrap`: Items wrap onto multiple lines.
    - `wrap-reverse`: Items wrap onto multiple lines, but in reverse order.
4. **`flex-flow`**  
    A shorthand for `flex-direction` and `flex-wrap`.
    
5. **`justify-content`**  
    Aligns flex items along the main axis.
    
    - `flex-start`: Items are packed at the start.
    - `center`: Items are centered.
    - `flex-end`: Items are packed at the end.
    - `space-between`: Items are distributed with space between them.
    - `space-around`: Items are distributed with space around them.
    - `space-evenly`: Items are distributed with equal space between them.
6. **`align-items`**  
    Aligns flex items along the cross axis.
    
    - `stretch` (default): Items stretch to fill the container.
    - `flex-start`: Items align at the start of the cross axis.
    - `center`: Items align at the center of the cross axis.
    - `flex-end`: Items align at the end of the cross axis.
    - `baseline`: Items align along their baseline.
7. **`align-content`**  
    Aligns flex lines within the flex container.
    
    - `stretch` (default): Lines stretch to fill the container.
    - `flex-start`: Lines align at the start of the cross axis.
    - `center`: Lines align at the center of the cross axis.
    - `flex-end`: Lines align at the end of the cross axis.
    - `space-between`: Lines are distributed with space between them.
    - `space-around`: Lines are distributed with space around them.
    - `space-evenly`: Lines are distributed with equal space between them.
8. **`align-items`**  
    Aligns items along the cross axis.
    

### Flex Item Properties

1. **`flex`**  
    A shorthand for `flex-grow`, `flex-shrink`, and `flex-basis`.
    
    - `flex: 1` is the same as `flex: 1 1 0%`, which means items can grow and shrink, with a base size of 0.
    - `flex: 0 1 auto` means items cannot grow but can shrink and have a base size of `auto`.
2. **`flex-grow`**  
    Defines the ability of a flex item to grow if necessary.
    
    - Default is `0`, meaning the item will not grow beyond its base size.
3. **`flex-shrink`**  
    Defines the ability of a flex item to shrink if necessary.
    
    - Default is `1`, meaning the item can shrink to fit within the container.
4. **`flex-basis`**  
    Defines the initial size of a flex item before space distribution.
    
    - Default is `auto`, which means the size is based on the item's content or specified width/height.
5. **`align-self`**  
    Allows the default alignment (or the one specified by `align-items`) to be overridden for individual flex items.
    
    - Values are similar to `align-items`: `auto`, `flex-start`, `center`, `flex-end`, `baseline`, `stretch`.