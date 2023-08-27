
#dynamicProgramming  #DSA 

Given a string `s`, return _the longest_  ***palindromic substring***

**Example 1:**
**Input:** s = "babad"
**Output:** "bab"
**Explanation:** "aba" is also a valid answer.

**Example 2:**
**Input:** s = "cbbd"
**Output:** "bb"

**Constraints:**

- `1 <= s.length <= 1000`
- `s` consist of only digits and English letters.



# First attempt
Get every possible substring and check if they were palindromes. If the string is a palindrome, check the length. If the length is greater than the length of the current longest, set the current longest equal to the current string.

### issues
This solution is straightforward and definitely works, however there is a glaring issue. It's very slow for large strings. You have a nested loop to get every possible substring which has a O(n^2) runtime, and you have to check each substring to see if it is a palindrome which is O(n) giving you a total runtime of O(n^3).


> [!NOTE] Reverse String in JavaScript
> let reverse = s.split('').reverse().join('');



```js
/**
 * @param {string} s
 * @return {string}
 */
var longestPalindrome = function (s) {
    // check base case
    // examine every possible substring
    // if substring and length is longer than current longest, set to longest
    // return longest
    if (isPalindrome(s)) {
        return s;
    }

    let current = '';

    for (let i = 0; i < s.length; i++) {
        for (let j = i + 1; j <= s.length; j++) {
            let ss = s.substring(i, j);
            if (isPalindrome(ss)) {
                if (ss.length > current.length) {
                    current = ss;
                }
            }
        }
    }
    return current;
};

function isPalindrome(s) {
    let reverse = s.split('').reverse().join('');
    if (s === reverse) {
        return true;
    } else {
        return false;
    }
}
```

## Solution 2(expand out)

Manacher's algorithm is **used to find the longest palindromic substring in any given string**. This algorithm is faster than the brute force approach, as it exploits the idea of a palindrome happening inside another palindrome. Manacher's algorithm is designed to find the palindromic substrings with odd lengths only.

we can iterate through the string once. At each index, we check to see if the positions to the left and right of the current index are equal. If they are equal, then the substring is a palindrome.
We continue incrementing and decrementing the left and right pointers until the substring is no longer a palindrome. If the substring is not a palindrome, we exit the inner loop and continue to the next index in the string (outer loop).

```js
function longestPalindrome(str) {
  let longest = "";

  // loop through string once
  for (let i = 0; i < str.length; i++) {
    // use two different starting positions to
    // account for even or odd strings
    checkLeftAndRight(i, i);
    checkLeftAndRight(i, i + 1);
  }

  function checkLeftAndRight(left, right) {
    while (left >= 0 && right < str.length && str[left] === str[right]) {
      // subtract left from right and add one to get current
      // length of substring
      if (right - left + 1 > longest.length) {
        // set longest to current substring
        longest = str.slice(left, right + 1);
      }
      left--;
      right++;
    }
  }

  return longest;
}

var a = "a";
var ab = "ab";
var aa = "aa";
var aba = "aba";
var caba = "caba";

console.log(longestPalindrome(a));//a
console.log(longestPalindrome(ab));//a
console.log(longestPalindrome(aa));//aa
console.log(longestPalindrome(aba));//aba
console.log(longestPalindrome(caba));//aba
```

## Solution 3 (dynamic Programming)

```js
function longestPalindrome(str) {
  const length = str.length;
  const dp = Array(length)
    .fill(false)
    .map(() => Array(length).fill(false));
  let maxLength = 1;
  let start = 0;

  // Single characters are palindromes
  for (let i = 0; i < length; i++) {
    dp[i][i] = true;
  }

  // Check for palindromic substrings of length 2
  for (let i = 0; i < length - 1; i++) {
    if (str[i] === str[i + 1]) {
      dp[i][i + 1] = true;
      maxLength = 2;
      start = i;
    }
  }

  // Check for palindromic substrings of length greater than 2
  for (let len = 3; len <= length; len++) {
    for (let i = 0; i < length - len + 1; i++) {
      const j = i + len - 1;
      if (str[i] === str[j] && dp[i + 1][j - 1]) {
        dp[i][j] = true;
        if (len > maxLength) {
          maxLength = len;
          start = i;
        }
      }
    }
  }
  return str.slice(start, start + maxLength);
}

var a = "a";
var ab = "ab";
var aa = "aa";
var aba = "aba";
var caba = "caba";

console.log(longestPalindrome(a));
console.log(longestPalindrome(ab));
console.log(longestPalindrome(aa));
console.log(longestPalindrome(aba));
console.log(longestPalindrome(caba));

```