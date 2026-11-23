# CSS Responsive Queries (Media Queries)

Responsive web design means creating websites that automatically adjust their layout and appearance according to different screen sizes.

For example:

- Desktop
- Laptop
- Tablet
- Mobile  
  CSS Media Queries are used to apply different CSS styles based on screen size or device features.

## Media Query

A media query is a CSS technique that allows us to apply styles only when a particular condition is satisfied.

**Syntax:**

```bash
@media media-type and (condition) {
    /* CSS properties */
}
```

Example:

```bash
@media screen and (max-width: 600px) {
    body {
        background-color: lightblue;
    }
}
```

Explanaion:

- @media defines a media query.
- screen targets screen-based devices.
- max-width: 600px means the viewport width must be 600px or less.
- The background becomes light blue when the condition matches.

## Types Of Media Queries

### A. Max-width

Applies CSS when the viewport width is less than or equal to the specified value.

```bash
@media (max-width: 600px) {
    .container {
        width: 100%;
    }
}
```

### B. Min-width

Applies CSS when the viewport width is greater than or equal to the specified value.

```bash
@media (min-width: 768px) {
    .container {
        width: 750px;
    }
}
```

### C. Orientation

Used to detect whether the device is in portrait or landscape orientation.

```bash
@media (orientation: portrait) {
    body {
        background-color: lightblue;
    }
}

@media (orientation: landscape) {
    body {
        background-color: lightgreen;
    }
}
```

### Comman Responsive Breakpoints

| Device       | Example Width  |
| ------------ | -------------- |
| Mobile       | Up to 600px    |
| Tablet       | 601px – 768px  |
| Small laptop | 769px – 1024px |
| Desktop      | Above 1024px   |

### Example:

HTML

```bash
<div class="container">
    <div class="box">A</div>
    <div class="box">B</div>
    <div class="box">C</div>
</div>
```

CSS

```bash
.container {
    display: flex;
    gap: 20px;
}

.box {
    background-color: lightblue;
    padding: 30px;
    flex: 1;
}

/* Tablet */
@media (max-width: 768px) {
    .container {
        display: grid;
        grid-template-columns: 1fr 1fr;
    }
}

/* Mobile */
@media (max-width: 600px) {
    .container {
        grid-template-columns: 1fr;
    }
}
```

Explanation:

- Desktop: Three boxes appear in one row.
- Tablet: Two columns are displayed.
- Mobile: One column is displayed.

## Mobile-First vs Desktop-First Design

### Mobile-First Design

We first design for smaller screens and then adjust the layout for larger screens using min-width.

```bash
.container {
    display: block;
}

@media (min-width: 768px) {
    .container {
        display: flex;
    }
}
```

### Desktop-First Design

We first design for larger screens and then adjust the layout for smaller screens using max-width.

```bash
.container {
    display: flex;
}

@media (max-width: 768px) {
    .container {
        display: block;
    }
}
```

### Refference

https://www.w3schools.com/htmlcss/
