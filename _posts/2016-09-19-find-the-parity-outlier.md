---
layout: post
title: Find the parity outlier
---

To practice and sharpen my Javascript skill, I've been trying to do challenges at [Codewars](https://www.codewars.com){:target="_blank" rel="noopener"} whenever I have time. Here is a challenge I've done recently, and how I solved it.

#### Challenge

You are given an array (which will have a length of at least 3, but could be very large) containing integers. The array is either entirely comprised of odd integers or entirely comprised of even integers except for a single integer N. Write a method that takes the array as an argument and returns N.

For example:

[2, 4, 0, 100, 4, 11, 2602, 36]

Should return: 11

[160, 3, 1719, 19, 11, 13, -21]

Should return: 160

#### Solution

```javascript
function findOutlier(integers){
    var odds = [];
    var evens = [];

    for (var i = 0; i < integers.length; i++) {
      if (integers[i] % 2 === 0) {
        evens.push(integers[i]);
      } else {
        odds.push(integers[i]);
      }
    }

    if (odds.length > evens.length) {
      return evens[0];
    } else {
      return odds[0];
    }   
}
```

To get to the correct solution, first I need to split the array of integers into two arrays, an odds and evens array. Then I just compare the arrays' length and return the first item of the shorter array. (You can also return the first item of the array with length equal to one since there is only one odd or one even integer).  
