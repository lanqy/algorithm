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
http://h3manth.com/javascript-sorting/

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
