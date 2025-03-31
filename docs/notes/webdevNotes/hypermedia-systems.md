Hypermedia Systems
========================

[online book](https://hypermedia.systems/)

Hypermedia is a media, for example a text, that includes non-linear branching from one location in the media to another, via, for example, hyperlinks embedded in the media. 

<a> and <form> are main examples of hypermedia control

One of the main precursors to modern ideas of hypermedia is [Vennevar Bush's article As We May Think](https://www.theatlantic.com/magazine/archive/1945/07/as-we-may-think/303881/). 

Seems to be related to the idea of [digital gardens](on-digital-gardens.md). I remember Bush's article being referenced when i was researching it.

## HTMX

Let’s look at an htmx-powered implementation of the simple JavaScript-powered button above:

```
<button hx-get="/contacts/1" hx-target="#contact-ui"> <1>
    Fetch Contact
</button>
```

An htmx implementation

issues a GET request to /contacts/1, replacing the contact-ui.

As with the JavaScript powered button, this button has been annotated with some attributes. However, in this case we do not have any (explicit) JavaScript scripting.

Instead, we have declarative attributes much like the href attribute on anchor tags and the action attribute on form tags. The hx-get attribute tells htmx: “When the user clicks this button, issue a GET request to /contacts/1.” The hx-target attribute tells htmx: “When the response returns, take the resulting HTML and place it into the element with the id contact-ui.”