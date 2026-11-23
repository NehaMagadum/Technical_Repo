# Common Header Meta Tags

Meta tags provide metadata about an HTML document.

They are written inside the `<head>` element and are not directly displayed on the webpage.

They provide information to browsers, search engines, and other services.

## Basic HTML Structure

```bash
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport"
          content="width=device-width, initial-scale=1.0">

    <title>My Website</title>
</head>

<body>
    <h1>Hello World</h1>
</body>

</html>
```

## Important Meta Tags

### 1. Charset

Defines the character encoding of the webpage.

```bash
<meta charset="UTF-8">
```

UTF-8 supports a wide range of characters and symbols.

### 2. Viewport

Controls the viewport dimensions and initial scaling on mobile devices.

```bash
<meta name="viewport"
      content="width=device-width, initial-scale=1.0">
```

Explanation:

- width=device-width: Sets the viewport width to the device width.
- initial-scale=1.0: Sets the initial zoom level to 100%.
  This is important for responsive web design.

### 3. Description

Provides a short description of the webpage.

```bash
<meta name="description"
      content="Learn HTML, CSS and JavaScript.">
```

Search engines may use this description in search result snippets.

### 4. Keywords

Defines keywords associated with the webpage.

```bash
<meta name="keywords"
      content="HTML, CSS, JavaScript">
```

Note: Google does not use the keywords meta tag for ranking.

### 5. Author

Specifies the author of the webpage.

```bash
<meta name="author" content="Developer Name">
```

### 6. Robots

Provides instructions to search engine crawlers.

```bash
<meta name="robots" content="index, follow">
```

- index: Allows indexing.
- follow: Allows following links.

### 7. Theme Color

Specifies a preferred browser interface theme color on supported devices.

```bash
<meta name="theme-color" content="#ffffff">
```

### 8. Refresh

Automatically refreshes or redirects a page after a specified time.

```bash
<meta http-equiv="refresh" content="30">
```

This refreshes the page every 30 seconds. Automatic refresh should be used carefully.

## Other Important Head Elements

These are not meta tags, but are commonly written inside `<head>`.

### Title

```bash
<title>My Portfolio</title>
```

Defines the webpage title shown in the browser tab.

### Favicon

```bash
<link rel="icon" href="favicon.ico">
```

Defines the small icon shown in the browser tab.

### External CSS

```bash
<link rel="stylesheet" href="style.css">
```

Connects an external CSS file.

### Preconnect

```bash
<link rel="preconnect" href="https://fonts.googleapis.com">
```

Hints that the browser should establish an early connection to a required external origin.

### Refference

https://www.w3schools.com/htmlcss/
