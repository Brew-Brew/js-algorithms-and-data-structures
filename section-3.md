### Analyzing performance of arrays and objects

##### Big O of Objects

- insertion : O(1)
- Removal : O(1)
- Searching : O(N)
- Access : O(1)

```javascript
let instructor = {
  firstName: "kelly",
  isInstructor: true,
  favoriteNumbers: [1, 2, 3, 4]
};
```

##### Big O of method of Objects

- Object.keys : (O(N))
- Object.values : (O(N))
- Object.entries : (O(N))
- hasOwnProperty : (O(1))
