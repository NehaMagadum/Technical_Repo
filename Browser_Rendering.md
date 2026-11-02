# Browser Rendering
Browser rendering is the process by which a web browser transforms raw code (HTML, CSS, JavaScript) into an interactive visual page on your screen.
## The main Stages of the rendering pipeline
1. Parsing and Tree Building
2. Render Tree Construction
3. Layout(Reflow)
4. Painting
5. Compositing.
   
The process can be broken down into these main steps:

### Step 1: Parse HTML and Build DOM
HTML → DOM
- Browser reads the HTML code.
- It converts HTML tags into a tree structure called the DOM (Document Object Model).
- DOM represents the structure of the webpage.
Example: HTML elements like html, body, h1 and p become nodes in the DOM tree.

### Step 2: Parse CSS and Build CSSOM
CSS → CSSOM
- Browser reads and processes CSS files.
- It converts CSS rules into a tree called CSSOM (CSS Object Model).
- CSSOM contains styling information such as colors, fonts, sizes and spacing.
- Browser waits for CSS processing before rendering.
Example: h1 { color: blue; } tells the browser to display the heading in blue.

### Step 3: Execute JavaScript
JavaScript → Execution
- Browser loads, parses and executes JavaScript.
- JavaScript can change HTML content and CSS styles.
- It can also handle user actions like clicks and form submissions.
Example: Clicking a button changes the text on the webpage.

### Step 4: Build the Render Tree
DOM + CSSOM → Render Tree
- Browser combines DOM and CSSOM.
- It creates a Render Tree.
- The render tree contains the elements and styles needed to display the webpage.
- Elements with display: none are excluded.
  
### Step 5: Calculate Layout
Layout
- Browser calculates the position and size of every visible element.
- It determines where each element should appear on the screen.
- It calculates height, width, margins and spacing.
  
### Step 6: Paint the Page
Paint → Screen
- Browser uses the layout information to draw the webpage.
- It paints text, colors, borders, images and backgrounds.
- Finally, the webpage appears on your screen.

<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/d7a70e1e-52f1-42ad-b3bc-750a84d9c145" />

## Mechanism Behind It 
The core mechanism behind browser rendering relies on an asynchronous, multi-threaded pipeline designed to turn a stream of network bytes into a interactive 60Hz (or higher) visual interface.  

Here is the deep technical breakdown of the sub-systems and mechanisms that execute this process.
```
[Network Bytes] ──> [Tokens] ──> [DOM Tree]   ─┐
                                               ├──> [Render Tree] ──> [Layout Engine] ──> [Paint] ──> [Compositing (GPU)]
[CSS Files]     ──> [Tokens] ──> [CSSOM Tree] ─┘
```



