:material-robot-happy-outline: Useful code snippets
========================

## Remove all child divs

```
while (parentContainer.firstChild) {
    parentContainer.removeChild(parentContainer.lastChild);
};
```

---

## Sorting numbers in array properly

[Array methods cheatsheet from javascript.info](https://javascript.info/array-methods)

```
const arr = [14, -3, 1, 21]

arr.sort( (a, b) => a - b );

console.log(arr) //[-3, 1, 14, 21]

```

--