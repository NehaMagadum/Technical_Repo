# CSS Specificity

CSS Specificity determines which CSS rule is applied when multiple CSS rules target the same HTML element and set the same property.

In simple words, specificity decides which CSS selector has higher priority.

## Types of CSS Selectors and Their Specificity

Specificity is commonly represented using three numbers: (ID, Class, Element)

| Selector     | Example           | Specificity                       |
| ------------ | ----------------- | --------------------------------- |
| Universal    | *                 | 0-0-0                             |
| Element      | p                 | 0-0-1                             |
| Class        | .box              | 0-1-0                             |
| Attribute    | [type="text"]     | 0-1-0                             |
| Pseudo-class | :hover            | 0-1-0                             |
| ID           | #header           | 1-0-0                             |
| Inline style | style="color:red" | Higher than normal selector rules |

## Specificity Calculation

Consider the following CSS:

```bash
p {
    color: red;
}

.text {
    color: blue;
}

#heading {
    color: green;
}
```

HTML

```bash
<p id="heading" class="text">
    Hello World
</p>
```

Which color will be applied?

Answer: Green.

Because:

- p = 0-0-1
- .text = 0-1-0
- #heading = 1-0-0  
  The ID selector has higher specificity than the class and element selectors.

## Combining Selectors

```bash
div p {
    color: red;
}

.container p {
    color: blue;
}

#main p {
    color: green;
}
```

**Specificity:**

| Selector     | Specificity |
| ------------ | ----------- |
| div p        | 0-0-2       |
| .container p | 0-1-1       |
| #main p      | 1-0-1       |

The #main p selector wins if all rules compete in the same cascade origin and layer with the same importance.

## !important

!important gives a declaration priority over normal declarations in the cascade.
CSS

```bash
p {
    color: red !important;
}

p {
    color: blue;
}
```

```
Output: Red.
```

However, !important should be avoided unless necessary because it makes CSS difficult to maintain and override.

## When Specificity is Equal

When two competing rules have equal specificity and the same cascade priority, the rule written later is applied.

```bash
p {
    color: red;
}

p {
    color: blue;
}
```

```
Output : Blue
```

### Refference

https://www.w3schools.com/htmlcss/
