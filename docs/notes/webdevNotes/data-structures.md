Data Structures
========================

## Getting paths in unweighted graph between two points

### what we need:
-  parameters - start vertex, end vertex, graph(adjacency list)
-  `checklist` array
-  `queue` array
-  `maxMoves`variable to stop loop (Object.keys(graph.length)

1. create a `startObj` `{current: neighbour.data, prev: null }`, push to `checklist` arr
2. add source neighbours to `queue`. node object forEach`{current: neighbour.data, prev: startObj }`
3. while `queue` is NOT empty && `checklist.length < maxMoves`
    4. let current vertex = `shift()` first item off `queue`
    5. if the current vertex is NOT in `checklist`, push current vertex to `checklist`
    6. for each neighbour of the vertex,
        7. if it is NOT the end vertex, push to `queue`
        8. if it is the end vertex, push to `checklist`

return `checklist`

## Getting shortest path from above 

### what we need:
-  parameters - start vertex, end vertex, pathArr(from above)
-  `shortestPath` array
- `current` variable (pointer)

1. set `current` to the end vertex in the `pathArr`, push `current` to `shortestPath`
2. while `current` is NOT the start vertex,
    3. set `current` to `current.prev`
    4. push `current`
5. reverse `shortestPath`

return `shortestPath`


