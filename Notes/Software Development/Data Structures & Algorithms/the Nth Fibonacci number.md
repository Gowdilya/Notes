Compute the Nth Fibonacci Number

#DSA #Fibonacci #recursive  #brute-force
#dynamicProgramming
- A bruteforce approach.
- Recursive approach.
- Using dynamic programming.


## Fibonacci
Intially we assume there will be two numbers `0` and `1`.

```
0 1 1 2 3 5 8 13 21 34 55

0 + 1 = 1
1 + 1 = 2
2 + 1 = 3
3 + 2 = 5
5 + 3 = 8
...
...
```


Input: 
10
12

Output:
55
144

### Bruteforce Method.
- check if the given num is `0` then return first number 
- else if it is `1` then return the second number.
- If the num is greater than `2` then we will iterate till the given number and add it with its previous number and store the previous number.

```javascript
let fibonacci = (num) => {
 //initalize
 let a = 0;
 let b = 1;

 //to store the sum
 let c = 0;
 
 //iterate till the given num
 for(let i = 2; i <= num; i++){
    //sum of last two numbers
    c = a + b; 
   
    //assign the last value to first     
    a = b; 

    //assign the sum to the last
    b = c; 
 }
 
 //if the num is 0 then return a else return b;
 return num ? b : a;
}
```

```sh

Input:
console.log(fibonacci(10));
console.log(fibonacci(12));

Output:
55
144
```
Time complexity: O(n).  
Space complexity: O(1).


## Recursive
- We will create a function and check if given number is less than 2 then return the same number.
- Else we will call the same function twice with last two numbers and add them.

```js
let fibonacci = (num) => {
  if(num < 2){
    return num;
  }

  return fibonacci(num - 1) + fibonacci(num - 2);
}
```

OR

```js
let fibonacci = (num) => {
  return num < 2 ? num : fibonacci(num - 1) + fibonacci(num - 2);
}
```

```sh
Input:
console.log(fibonacci(9));
console.log(fibonacci(12));

Output:
34
144
```

\Time complexity: O(2 ^ n).  
Space complexity: O(n).

#### Time and Space complexity

- We are recursively calling the same function again and again with the lesser values like T(n)=T(n-1)+T(n-2)+O(1), so Time complexity is O(n ^ 2).
- Recursive functions are stored in call stack, so Space complexity is O(n).

This function works completely fine but it does a lot of unnecessary work by calling itself again and again with the same value.

```
                               fnc(9)
                               /    \
                           fnc(8)    fnc(7)
                          /   \       /   \
                    fnc(7)  fnc(6)  fnc(6) fnc(5)
                     /  \
                  fnc(6) func(5)

```

As you can see we are calling `fnc(7)` twice and `fnc(6)` thrice.  
We can optimize this algorithm by storing the already computed function using Dynamic Programming.


### Using Dynamic Programming.

We will use [memoization](https://en.wikipedia.org/wiki/Memoization) technique to find the fibonacci in javacscript.

#### Implementation

- We will create a function which will recursively call itself to compute the algorithm like implemented above.
- We will use an [array](https://learnersbucket.com/tutorials/array/javascript-array-complete-reference) to keep track of the already computed functions value.
- If the value for the given function already exits then we will return the value else we will call the same function recursively with lesser values and store it.

```js
//To store the function values
let memo = [0, 1];

//Function to calculate the fibonacci
let fibonacci = (num) => {
    //Get the value for current number
    let result = memo[num];
    
    //If there is no value for current number
    if(typeof result !== 'number'){ 
      //call the function recursively and store the result
      result = fibonacci(num - 1) + fibonacci(num - 2);
      memo[num] = result;
    }

    //Else if value then return it
    return result;
  }
```

```sh
Input:
console.log(fibonacci(10));
console.log(fibonacci(12));
console.log(fibonacci(15));

Output:
55
144
610
```


Time complexity: O(n).  
Space complexity: O(n).

#### Time and Space complexity

- We are using memoization to optimize the recursive algorithm by storing the value of the already computed functions with given number i.e we are just calling the functions with distinct numbers, so Time complexity is O(n).
- We are trading memory for speed, so Space complexity is O(n).