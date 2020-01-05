### Problem Solving Patterns

#### Frequency Counter 패턴

이 패턴은 object나 set 으로 값들의 values/frequencies를 모은다. (value를 key로, frequency를 value로)
이 패턴을 통해 array들과 string들의 nested loop나, O(N^2) 연산을 피할수 있게 된다.

ex)
두개의 array를 받아, 첫번째 array의 값들의 제곱에 해당하는 값들이 순서에 상관없이 두번째 배열에 갯수에 맞게 들어가 있으면 true를 결과값으로 내는 **same**이라는 함수를 만들어라.

```
same([1,2,3], [4,1,9]) // true
same([1,2,3], [1,9]) // false
same([1,2,1], [4,4,1]) // false (1,1,4의 값들로 이루어져야 함)
```

`NAIVE한 solution`

- time complexity가 O(N^2)

```javascript
function same(arr1, arr2) {
  if (arr1.length !== arr2.length) {
    return false;
  }
  for (let i = 0; i < arr1.length; i++) {
    let correctIndex = arr2.indexOf(arr1[i] ** 2);
    if (correctIndex === -1) {
      return false;
    }
    console.log(arr2);
    arr2.splice(correctIndex, 1);
  }
  return true;
}

same([1, 2, 3, 2], [9, 1, 4, 4]);
```

`Refactored solution`

- time complexity가 O(N)

```javascript
function same(arr1, arr2) {
  if (arr1.length !== arr2.length) {
    return false;
  }
  let frequencyCounter1 = {};
  let frequencyCounter2 = {};
  for (let val of arr1) {
    frequencyCounter1[val] = (frequencyCounter1[val] || 0) + 1;
  }
  for (let val of arr2) {
    frequencyCounter2[val] = (frequencyCounter2[val] || 0) + 1;
  }
  console.log(frequencyCounter1);
  console.log(frequencyCounter2);
  for (let key in frequencyCounter1) {
    // 아예 제곱에 해당하는 값이 없는 경우
    if (!(key ** 2 in frequencyCounter2)) {
      return false;
    }
    // frequency가 다른 경우
    if (frequencyCounter2[key ** 2] !== frequencyCounter1[key]) {
      return false;
    }
  }
  return true;
}

same([1, 2, 3, 2, 5], [9, 1, 4, 4, 11]);
```

#### Multiple Pointer 패턴

- 이 패턴은 index나 포지션 값들을 가지는 포인터들이나 값들을 만들어 처음부터 혹은 끝부터, 혹은 중간으로 이동시키는 패턴
- 매우 작은 공간 복잡도를 가지는 패턴

ex)

- sumZero라는 정렬된 integer 타입의 array들에서 합이 0 인 첫번째 쌍을 찾는 문제, 없다면 undefined return

```
sumZero([-3,-2,-1,0,1,2,3]) // [-3,3]
sumZero([-2,0,1,3]) // undefined
```

`Naive한 버전`

- time complexity : O(N^2)
- space complexity : O(1)

```javascript
function sumZero(arr) {
  for (let i = 0; i < arr.length; i++) {
    for (let j = i + 1; j < arr.length; j++) {
      if (arr[i] + arr[j] === 0) {
        return [arr[i], arr[j]];
      }
    }
  }
}

sumZero([-4, -3, -2, -1, 0, 1, 2, 5]);
```

`REFACTOR 버전`

- time complexity O(N)
- space complexity O(1)

```javascript
function sumZero(arr) {
  let left = 0;
  let right = arr.length - 1;
  while (left < right) {
    let sum = arr[left] + arr[right];
    if (sum === 0) {
      return [arr[left], arr[right]];
    } else if (sum > 0) {
      right--;
    } else {
      left++;
    }
  }
}
```
