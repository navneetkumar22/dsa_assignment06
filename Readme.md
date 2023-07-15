# PPT - DSA Assignment 06

## Answer 1:
```js
const diStringMatch = str => {
    let count1 = -1;
    let count2 = str.length + 1;
    const result = [];

    for (let i = 0; i <= str.length; i++) {

        if (str[i] === "I") {
            count1++;
            result.push(count1);
        } else {
            count2--;
            result.push(count2);
        }
    }
    return result;
};
```

<br/>

## Answer 2:
```js
var searchMatrix = function (matrix, target) {

    // log (m*n) = log(m) + log(n) 
    // finding the row in log(n) time and then finding target in log(m) time

    const m = matrix[0].length, n = matrix.length;
    if (target < matrix[0][0] || target > matrix[n - 1][m - 1]) return false;

    let low = 0, high = matrix.length - 1;
    let mid;
    while (low <= high) {
        mid = Math.floor((low + high) / 2)

        if (target <= matrix[mid][m - 1] && target >= matrix[mid][0]) break;
        if (target < matrix[mid][0]) high = mid - 1;
        else if (target > matrix[mid][m - 1]) low = mid + 1;
    }


    return binarySearch(target, matrix[mid])
};

function binarySearch(target, nums) {
    let low = 0, high = nums.length - 1;

    while (low <= high) {
        let mid = Math.floor((low + high) / 2);
        if (target == nums[mid]) return true;

        if (target < nums[mid]) high = mid - 1;
        else low = mid + 1;
    }

    return false
}
```

<br/>

## Answer 3:
```js
const validMountainArray = arr => {
    if (arr.length < 3 || arr[0] >= arr[1])
        return false;
   
        let peak = true;
   
    for (let i = 0; i < arr.length - 1; i++) {
        if (peak && arr[i] > arr[i + 1]) {
            peak = false;
        } else if ((!peak && arr[i] <= arr[i + 1]) || (arr[i] === arr[i + 1])) {
            return false;
        }
    }
    return peak ? false : true;
};
```

<br/>

## Answer 4:
```js
const findMaxLength = nums => {
    let hash = { 0: -1 };
    let count = 0;
    let max = 0;

    for (let i = 0; i < nums.length; i++) {
        if (nums[i] == 0)
            count--;
        else
            count++;

        if (hash[count] != null)
            max = Math.max(max, i - hash[count]);
        else
            hash[count] = i
    }
    return max;
};
```

<br/>

## Answer 5:
```js
const minValue = (A, B) => {
    let n = A.length;

    // Sort A and B so that minimum and maximum value can easily be fetched.
    A.sort(function (a, b) {
        return a - b;
    });
    B.sort(function (a, b) {
        return a - b;
    });

    // Multiplying minimum value of A and maximum value of B
    let result = 0;
    for (let i = 0; i < n; i++)
        result += (A[i] * B[n - i - 1]);

    return result;
}
```

<br/>

## Answer 6:
```js
const findOriginalArray = changed => {
    if (changed.length % 2 === 1)
        return []; // get rid of odd-length inputs
    let double = true;
    changed.sort((a, b) => a - b) // sort array in ascending order
    let i = 0;

    while (i < changed.length) {
        let pos = changed.indexOf(changed[i] * 2, i + 1); // check for presence of doubled number
        if (pos === -1) {
            double = false; // if not found, break out of the loop w/ false check
            break;
        } else {
            changed.splice(pos, 1); // if found, get rid of doubled number and move on.
            i++;
        }
    }
    return (double ? changed : []);
};
```

<br/>

## Answer 7:
```js
const generateMatrix = n => {
    // MATRIX[Y][X]
    //    ---------
    //Y0 | 1  2  3 |
    //Y1 | 4  5  6 |
    //Y2 | 7  8  9 |
    //    ---------
    //     X0 X1 X2

    let matrix = [], count = 0, x = 0, y = 0;
    const maxElements = n * n;

    for (let i = 0; i < n; i++) {
        matrix[i] = new Array()
    }

    while (maxElements > count) {
        for (let i = x; maxElements > count && i < n - x; i++) {
            count++;
            matrix[y][i] = count;
            // console.log(1, matrix[y][i])
        }
        y++;

        for (let i = y; maxElements > count && i < n - (y - 1); i++) {
            count++;
            matrix[i][(n - 1) - x] = count;
            // console.log(2, matrix[i][(n-1) - x])
        }
        x++;

        for (let i = (n - 1) - x; maxElements > count && i >= x - 1; i--) {
            count++;
            matrix[(n - 1) - (y - 1)][i] = count;
            // console.log(3, matrix[(n-1)-(y-1)][i])
        }

        for (let i = (n - 1) - y; maxElements > count && i >= y; i--) {
            count++;
            matrix[i][x - 1] = count
            // console.log(4, matrix[i][x-1])
        }
    }
    return matrix;
};
```

<br/>

## Answer 8:
