# CSS Inline VS Block Elements

In HTML, elements are classified based on how they are displayed on a webpage. The two common types are Block-level elements and Inline elements.

## Block Elements

A block-level element always starts on a new line and occupies the full available width of its parent container by default.

**Characteristics:**

- Starts on a new line.
- Occupies the full available width by default.
- We can set width and height.
- We can apply margin and padding on all sides.
- Multiple block elements appear vertically, one below another.  
  Examples: `<div>`, `<p>`, `<h1>`, `<section>`, `<header>`, `<footer>`.

HTML Example

```bash
<div>Block Element 1</div>
<div>Block Element 2</div>
<p>This is a paragraph</p>
```

CSS Example

```bash
div {
    background-color: lightblue;
    width: 200px;
    height: 50px;
    margin: 10px;
}
```

## Inline Elements

Inline elements do not start on a new line. They occupy only the space required by their content.

**Characteristics:**

- Does not start on a new line.
- Takes only the required width.
- width and height properties do not apply normally.
- Horizontal margin and padding work.
- Vertical padding and margin do not affect the surrounding line layout in the same way as block elements.  
  Examples: `<span>`, `<a>`, `<strong>`, `<em>`, `<label>`.

HTML Example:

```bash
<span>Inline Element 1</span>
<span>Inline Element 2</span>
<a href="#">Click Here</a>
```

CSS Example:

```bash
span {
    background-color: lightgreen;
    margin: 10px;
    padding: 10px;
}
```

### Difference between Inline and Block Elements

| Property       | Block                           | Inline                                                             |
| -------------- | ------------------------------- | ------------------------------------------------------------------ |
| New line       | Starts on a new line            | Does not start on a new line                                       |
| Width          | Full available width by default | Content width                                                      |
| Height         | Can be set                      | Does not apply normally                                            |
| Width property | Supported                       | Not supported                                                      |
| Margin         | All sides                       | Horizontal margins work normally                                   |
| Padding        | All sides                       | Horizontal and vertical padding, with special line-layout behavior |
| Examples       | div, p, h1                      | span, a, strong                                                    |

### Refference

https://www.w3schools.com/htmlcss/
