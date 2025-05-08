:material-repeat: recursion
========================
## operate on deeply nested array

```
function func(arr) {

    //info to carry over
    let total = 0;
    
    //base case (easiest condition to fulfill)
    if (arr.length === 0) {
        return 0;
    };
    
    //--recursive version of a for loop--
    
    let first = arr.shift();
    
    //checking if the first item is a nested array, otherwise operate
    if (Array.isArray(first)) {
        total += func(first)
    } else if (~a value you can operate on~) {
        //operate here, for example:
        total += 1
    }
    
    /*in order for the info to carry over, the final top level return call
    /*needs to call the function and add it to the
    /* initial carry over info
    return total + func(arr)
    
}
```

## Fibonacci numbers array

```
function fibsRec(n) {
   if (n === 1) {
      return [0];
    } else if (n === 2) {
      return [0, 1];
    } else if (n === 0) {
      return;
    }
    
    //to get a persistent array, call function on array
    //this is the "addding part"
    //adding at the final return statement is for single item outputs
    let arr = fibsRec(n-1)
    
    //you can "push" directly without explicitly stating that it is an array
    //no need for a default array
    arr.push(arr[arr.length - 1] + arr[arr.length - 2]);

    return arr
}
```
## Recursive forEach

useful for nested arrays

```
  function forEachRecur(callback, arr) {
    if (arr.length === 0) {
      return;
    }

    const first = arr.shift();

    if (Array.isArray(first)) {
      forEachRecur(callback, first);
    } else {
      callback(first);
    }

    return forEachRecur(callback, arr);
  }
```
``````
## Enqueue (level order traversal)

```
  function enqueue(root, level, queue) {
    if (root === null) {
      return;
    }

    if (queue.length <= level) {
      queue.push([]);
    }

    queue[level].push(root);

    enqueue(root.left, level + 1, queue);
    enqueue(root.right, level + 1, queue);
  }
```

Set up a queue array first, then pass is in as an argument.
`let queue = []`
Queue will be a nested array. Each outer index is a level.

``````

## Tips

- base case return value should be the same as the final return value


