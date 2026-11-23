# CSS Structural Classes

- Structural classes are CSS classes used to organize and arrange the layout of a webpage.
- They help developers create reusable and maintainable layouts.
- These classes are commonly used in frontend development.

## Container

A container holds and organizes the main content of a webpage.

HTML

```bash
<div class="container">
    <h1>Welcome</h1>
    <p>Welcome to my website.</p>
</div>
```

CSS

```bash
.container {
    max-width: 1200px;
    margin: 0 auto;
    padding: 20px;
}
```

**Purpose:**

- Controls content width.
- Aligns content.
- Provides consistent spacing.
- Keeps content organized.

## Header

The header contains introductory content or navigation.

HTML

```bash
<header class="header">
    <h1>My Website</h1>
</header>
```

CSS

```bash
.header {
    background-color: #333;
    color: white;
    padding: 20px;
}
```

## Navbar

A navigation bar contains links to different pages or sections.

HTML

```bash
<nav class="navbar">
    <a href="#">Home</a>
    <a href="#">About</a>
    <a href="#">Contact</a>
</nav>
```

CSS

```bash
.navbar {
    display: flex;
    gap: 20px;
}
```

## Main

The `<main>` element contains the primary content of the webpage.

HTML

```bash
<main class="main">
    <h2>Main Content</h2>
</main>
```

A webpage should generally have one visible main element.

## Section

A section groups related content.

HTML

```bash
<section class="about">
    <h2>About Us</h2>
    <p>Information about our company.</p>
</section>
```

## Article

An article represents independent, self-contained content.

Examples:

- Blog posts
- News articles
- Forum posts
- Product reviews

HTML

```bash
<article class="article">
    <h2>CSS Basics</h2>
    <p>Learn CSS from the beginning.</p>
</article>
```

## Aside

The aside element contains content indirectly related to the main content.

Examples:

- Sidebars
- Related articles
- Advertisements
- Additional information

HTML

```bash
<aside class="sidebar">
    <h3>Related Topics</h3>
</aside>
```

## Footer

The footer contains information about the webpage or website.

Examples:

- Copyright information
- Contact details
- Social media links
- Privacy policy

HTML

```bash
<footer class="footer">
    <p>Copyright 2026 My Website</p>
</footer>
```

### Refference

https://www.w3schools.com/htmlcss/
