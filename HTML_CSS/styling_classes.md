# CSS Styling Classe

Styling classes are reusable CSS classes used to apply visual properties to HTML elements.

They control colors, fonts, backgrounds, spacing, borders, and alignment.

## Text Styling

```bash
.text-center {
    text-align: center;
}

.text-left {
    text-align: left;
}

.text-right {
    text-align: right;
}

.text-bold {
    font-weight: bold;
}

.text-uppercase {
    text-transform: uppercase;
}

.text-italic {
    font-style: italic;
}
```

## Background Styling

```bash
.bg-primary {
    background-color: blue;
}

.bg-secondary {
    background-color: gray;
}

.bg-success {
    background-color: green;
}

.bg-danger {
    background-color: red;
}
```

## Spacing Classes

CSS provides margin and padding properties.

**Margin:** Space outside an element's border.

**Padding:** Space between content and border.

```bash
.mt-10 {
    margin-top: 10px;
}

.mb-10 {
    margin-bottom: 10px;
}

.p-20 {
    padding: 20px;
}

.mx-auto {
    margin-left: auto;
    margin-right: auto;
}
```

## Border Classes

```bash
.border {
    border: 1px solid black;
}

.border-radius {
    border-radius: 10px;
}

.rounded-circle {
    border-radius: 50%;
}
```

## Width and Height Classes

```bash
.w-100 {
    width: 100%;
}

.h-100 {
    height: 100%;
}

.full-screen {
    min-height: 100vh;
}
```

## Display Classes

```bash
.d-block {
    display: block;
}

.d-inline {
    display: inline;
}

.d-inline-block {
    display: inline-block;
}

.d-flex {
    display: flex;
}

.d-grid {
    display: grid;
}

.d-none {
    display: none;
}
```

## Combining Styling Classes

HTML

```bash
<div class="container bg-primary p-20 text-center">
    <h1 class="text-bold">Welcome</h1>
    <p class="text-uppercase">Learn CSS</p>
</div>
```

### Refference

https://www.w3schools.com/htmlcss/
