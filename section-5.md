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
function same(arr1, arr2){
    if(arr1.length !== arr2.length){
        return false;
    }
    for(let i = 0; i < arr1.length; i++){
        let correctIndex = arr2.indexOf(arr1[i] ** 2)
        if(correctIndex === -1) {
            return false;
        }
        console.log(arr2);
        arr2.splice(correctIndex,1)
    }
    return true;
}

same([1,2,3,2], [9,1,4,4])

```

`Refactored solution`
- time complexity가 O(N)
```javascript
function same(arr1, arr2){
    if(arr1.length !== arr2.length){
        return false;
    }
    let frequencyCounter1 = {}
    let frequencyCounter2 = {}
    for(let val of arr1){
        frequencyCounter1[val] = (frequencyCounter1[val] || 0) + 1
    }
    for(let val of arr2){
        frequencyCounter2[val] = (frequencyCounter2[val] || 0) + 1        
    }
    console.log(frequencyCounter1);
    console.log(frequencyCounter2);
    for(let key in frequencyCounter1){
      // 아예 제곱에 해당하는 값이 없는 경우
        if(!(key ** 2 in frequencyCounter2)){
            return false
        }
        // frequency가 다른 경우
        if(frequencyCounter2[key ** 2] !== frequencyCounter1[key]){
            return false
        }
    }
    return true
}

same([1,2,3,2,5], [9,1,4,4,11])

```