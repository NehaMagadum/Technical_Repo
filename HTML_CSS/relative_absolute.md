# Positioning- Relative and Absolute

- CSS positioning determines how an HTML element is placed on a webpage.

- The CSS position property controls the positioning method of an element.

## Types of CSS positioning

| Position | Description                                                               |
| -------- | ------------------------------------------------------------------------- |
| static   | Default positioning                                                       |
| relative | Positioned relative to its original position                              |
| absolute | Positioned relative to its nearest positioned ancestor                    |
| fixed    | Positioned relative to the browser viewport                               |
| sticky   | Behaves like relative until a scrolling threshold is reached, then sticks |

## Position: Static

- It is the default position of every HTML element.
- Elements follow the normal document flow.
- top, right, bottom, and left do not affect its position.

```bash
.box {
    position: static;
}
```

## Position: Relative

An element with position: relative is positioned relative to its original position.

- The element remains in the normal document flow.
- Its original space is preserved.
- We can use top, right, bottom, and left to move it.
- Other elements behave as if the element is still in its original position.

HTML

```bash
<div class="box">Relative Box</div>
```

CSS

```bash
.box {
    width: 150px;
    height: 100px;
    background-color: lightblue;
    position: relative;
    top: 20px;
    left: 30px;
}
```

Explanation:

- top: 20px moves the element 20px down.
- left: 30px moves the element 30px right.

## Position: Absolute

An element with position: absolute is positioned relative to its nearest ancestor that has a position other than static.

- It is removed from the normal document flow.
- Its original space is not preserved.
- It can overlap other elements.
- If no positioned ancestor exists, it is positioned relative to the initial containing block.

HTML

```bash
<div class="parent">
    Parent
    <div class="child">Absolute Box</div>
</div>
```

CSS

```bash
.parent {
    width: 300px;
    height: 200px;
    background-color: lightgray;
    position: relative;
}

.child {
    width: 100px;
    height: 50px;
    background-color: orange;
    position: absolute;
    top: 20px;
    right: 10px;
}
```

Explanation:

- Parent has position: relative.
- Child has position: absolute.
- Child is positioned 20px from the parent's top and 10px from its right edge.

### Difference between Relative and Absolute

| Relative                                        | Absolute                                           |
| ----------------------------------------------- | -------------------------------------------------- |
| Positioned relative to its original position    | Positioned relative to nearest positioned ancestor |
| Remains in normal document flow                 | Removed from normal document flow                  |
| Original space is preserved                     | Original space is not preserved                    |
| Can overlap other elements                      | Can overlap other elements                         |
| Commonly used as a parent for absolute children | Commonly used for overlays and badges              |

## Position: Fixed

A fixed element stays at a particular position relative to the viewport while scrolling.

```bash
.header {
    position: fixed;
    top: 0;
    width: 100%;
}
```

Use cases: Fixed navigation bars, floating buttons, chat icons.

## Position: Sticky

Sticky positioning combines relative and fixed behavior.

```bash
.header {
    position: sticky;
    top: 0;
}
```

The element behaves normally until it reaches the specified scrolling position. Then it sticks within its containing block.  
Use cases: Sticky navigation, table headers, section headings.

### Refference

https://www.w3schools.com/htmlcss/
