# Javascript algorithm

#1、Quicksort
(1)、
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
from: http://antjanus.com/blog/web-development-tutorials/understanding-quicksort-js-native-implementation/



#2、 Javascript binary search
```javascript
/**
 * Performs a binary search on the host array. This method can either be
 * injected into Array.prototype or called with a specified scope like this:
 * binaryIndexOf.call(someArray, searchElement);
 *
 * @param {*} searchElement The item to search for within the array.
 * @return {Number} The index of the element which defaults to -1 when not found.
 */
function binaryIndexOf(searchElement) {
    'use strict';

    var minIndex = 0;
    var maxIndex = this.length - 1;
    var currentIndex;
    var currentElement;

    while (minIndex <= maxIndex) {
        currentIndex = (minIndex + maxIndex) / 2 | 0;
        currentElement = this[currentIndex];

        if (currentElement < searchElement) {
            minIndex = currentIndex + 1;
        }
        else if (currentElement > searchElement) {
            maxIndex = currentIndex - 1;
        }
        else {
            return currentIndex;
        }
    }

    return -1;
}
```
from: http://oli.me.uk/2013/06/08/searching-javascript-arrays-with-a-binary-search/

#3、Javascript bubblesort
```javascript
function swap(items, firstIndex, secondIndex){
    var temp = items[firstIndex];
    items[firstIndex] = items[secondIndex];
    items[secondIndex] = temp;
}

function bubbleSort(items){

    var len = items.length,
        i, j, stop;

    for (i=0; i < len; i++){
        for (j=0, stop=len-i; j < stop; j++){
            if (items[j] > items[j+1]){
                swap(items, j, j+1);
            }
        }
    }

    return items;
}
```

from: http://www.nczonline.net/blog/2009/05/26/computer-science-in-javascript-bubble-sort/

http://codingmiles.com/sorting-algorithms-bubble-sort-using-javascript/

#4、insertion sort
```javascript
function insertionSort(unsortedList) {
    var len = unsortedList.length;

    for (var i = 0; i < len; i++) {
        var tmp = unsortedList[i]; //Copy of the current element.
        /*Check through the sorted part and compare with the 
        number in tmp. If large, shift the number*/
        for (var j = i - 1; j >= 0 && (unsortedList[j] > tmp); j--) {
            //Shift the number
            unsortedList[j + 1] = unsortedList[j];
        }
        //Insert the copied number at the correct position
        //in sorted part.
        unsortedList[j + 1] = tmp;
    }
}

var ul = [5, 3, 1, 2, 4];
insertionSort(ul);
console.log(ul);
```
form: http://codingmiles.com/sorting-algorithms-insertion-sort-using-javascript/

http://bateru.com/news/2011/03/code-of-the-day-javascript-insertion-sort/

#5、Selection Sort 

```javascript
function selectionSort(items) {
    var length = items.length;

    for (var i = 0; i < length - 1; i++) { //Number of passes
        var min = i; //min holds the current minimum number position for each pass; i holds the Initial min number
        for (var j = i + 1; j < length; j++) { //Note that j = i + 1 as we only need to go through unsorted array
            if (items[j] < items[min]) { //Compare the numbers
                min = j; //Change the current min number position if a smaller num is found
            }
        }

        if (min != i) { //After each pass, if the current min num != initial min num, exchange the position.
            //Swap the numbers
            var tmp = items[i];
            items[i] = items[min];
            items[min] = tmp;
        }
    }
}
```
from: http://codingmiles.com/sorting-algorithms-selection-sort-using-javascript/


Resources:

http://h3manth.com/javascript-sorting/


#6、Computer science in JavaScript: Binary search

```javascript
function binarySearch(items, value){
    var startIndex = 0,
        stopIndex = items.length - 1,
        middle = Math.floor((stopIndex + startIndex) / 2);
    while(items[middle] != value && startIndex < stopIndex) {

        // 调整搜索区域
        if (value < items[middle]) {
            stopIndex = middle - 1;
        } else if (value > items[middle]){
            startIndex = middle + 1;
        }

        // 重新计算中间值
        middle = Math.floor((stopIndex + startIndex) / 2);
    }

    // 确保它是正确的值
    return (items[middle] != value) ? -1 : middle;
}
```

from:  https://www.nczonline.net/blog/2009/09/01/computer-science-in-javascript-binary-search/
