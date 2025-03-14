CSS notes
========================

## Grid cheatsheet

[from CSS Tricks](https://css-tricks.com/snippets/css/complete-guide-grid/)

![css-grid-poster](../../media/css-grid-poster.png)

---

## CSS Reset

I like Josh Comeau's [Modern CSS Reset](https://www.joshwcomeau.com/css/custom-css-reset/).

I use a slightly modified version at the start of my css. I remove anything I don't need.

```
* {
    box-sizing: border-box;
    margin: 0;
}

body {
    line-height: 1.5;
    -webkit-font-smoothing: antialiased;
}

img, picture, video, canvas, svg {
    max-width: 100%;
}

input, button, textarea, select {
    font: inherit;
}

p, h1, h2, h3, h4, h5, h6 {
    overflow-wrap: break-word;
}

p {
    text-wrap: pretty;
}

h1, h2, h3, h4, h5, h6 {
    text-wrap: balance;
}

.bold{
    font-weight: bold;
}

.italic{
    font-style: italic;
}
```

---


