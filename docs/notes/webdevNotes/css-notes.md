:material-language-css3: CSS notes
========================

## 3d Transform

[intro to css 3d transforms](https://3dtransforms.desandro.com/)

for cubes and boxes, translateZ value is how much the face moves away from the center axis

---

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

## modal

```
/* modal */
::backdrop{
  background-color: var(--darkest);
  opacity: 0.75;
}

dialog{

  background-image: url(../images/backgrounds/whiteline.jpg);
  /* centers */
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);

  padding: 40px 25px;

}

dialog img {
  max-height: 100%;
}
```

## bobbing animation

```
animation: float 3s ease-in-out infinite

@keyframes float {
	0% {
		transform: translatey(0px);
	}
	50% {
		transform: translatey(-20px);
	}
	100% {
		transform: translatey(0px);
	}
}
```

