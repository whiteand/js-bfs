# js-bfs

Package for breadth-first search on js value.

# Install

```bash
npm i --save js-bfs
```

# Usage

```javascript
import { bfs } from 'js-bfs'

const value = {
  a: {
    arr: [1,2,3,4],
    b: {
      c: '1'
    }
  }
}

let i = 0;
bfs(value, (item, path) => {
  console.log(++i, { item, path })
})
```

Output:
```javascript
1. { item: { a: { arr: [ 1, 2, 3, 4 ], b: { c: '1' } } }, path: [] }
2. { item: { arr: [ 1, 2, 3, 4 ], b: { c: '1' } },        path: [ 'a' ] }
3. { item: [ 1, 2, 3, 4 ],                                path: [ 'a', 'arr' ] }
4. { item: { c: '1' },                                    path: [ 'a', 'b' ] }
5. { item: 1,   path: [ 'a', 'arr', 0 ] }
6. { item: 2,   path: [ 'a', 'arr', 1 ] }
7. { item: 3,   path: [ 'a', 'arr', 2 ] }
8. { item: 4,   path: [ 'a', 'arr', 3 ] }
9. { item: '1', path: [ 'a', 'b', 'c' ] }
```

# End of search

If you want to stop search you should return `false` from callback.

```typescript
bfs([1,2,3,4,5,6], (number) => {
  console.log(number)
  if (number === 4) return false
})
```
Output:
```bash
1
2
3
4
```

# Type

```typescript
bfs: (
  value: any,
  action: (
    value: any,
    path: string|number[]
  ) => any|false
) => void
```