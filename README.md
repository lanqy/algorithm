# algorithm
Collect all kinds of algorithms implemented in JavaScript

#1、Quicksort
```javascript
function quicksort(arr) {
    //if array is empty
    if (arr.length === 0) {
        return [];
    }
    var left = [];
    var right = [];
    var pivot = arr[0];
    //go through each element in array
    for (var i = 1; i < arr.length; i++) {
        if (arr[i] < pivot) {
            left.push(arr[i]);
        } else {
            right.push(arr[i]);
        }
    }
    return quicksort(left).concat(pivot, quicksort(right));
}
```
from http://antjanus.com/blog/web-development-tutorials/understanding-quicksort-js-native-implementation/
