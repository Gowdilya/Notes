
A _binary gap_ within a positive integer N is any maximal sequence of consecutive zeros that is surrounded by ones at both ends in the binary representation of N.

For example, number 9 has binary representation 1001 and contains a binary gap of length 2. The number 529 has binary representation 1000010001 and contains two binary gaps: one of length 4 and one of length 3. The number 20 has binary representation 10100 and contains one binary gap of length 1. The number 15 has binary representation 1111 and has no binary gaps. The number 32 has binary representation 100000 and has no binary gaps.

Write a function:

> class Solution { public int solution(int N); }

that, given a positive integer N, returns the length of its longest binary gap. The function should return 0 if N doesn't contain a binary gap.

For example, given N = 1041 the function should return 5, because N has binary representation 10000010001 and so its longest binary gap is of length 5. Given N = 32 the function should return 0, because N has binary representation '100000' and thus no binary gaps.

Write an ****efficient**** algorithm for the following assumptions:

> - N is an integer within the range [1..2,147,483,647].
```js
// cd to JavaScript Folder, in Terminal Type "node binaryGap.js" 
// n % x, gives the remainder after division 

var binaryGap = function (N) {
    // write your code in JavaScript (Node.js 4.0.0)     
    // Tests if our value is an integer
    const bin = N.toString(2);

    let currentGap = 0;
    let gaps = []; // collect list of gaps

    for (i=0; i<bin.length; i++){

      if (bin[i]==="0"){
        currentGap++;

        if (bin[i+1]==="1"){
          gaps.push(currentGap);
          currentGap = 0;
        }
      }
    }

    if (gaps.length===1){
      return gaps[0];
    } else if (gaps.length>1){
      return Math.max(...gaps) //Max Gap, or have newGap > OldGap use it
    } else {
      return 0
    }

  };
  
  console.log(binaryGap(21));
  //console.log((32).toString(2));A _binary gap_ within a positive integer N is any maximal sequence of consecutive zeros that is surrounded by ones at both ends in the binary representation of N.

For example, number 9 has binary representation 1001 and contains a binary gap of length 2. The number 529 has binary representation 1000010001 and contains two binary gaps: one of length 4 and one of length 3. The number 20 has binary representation 10100 and contains one binary gap of length 1. The number 15 has binary representation 1111 and has no binary gaps. The number 32 has binary representation 100000 and has no binary gaps.

Write a function:

> class Solution { public int solution(int N); }

that, given a positive integer N, returns the length of its longest binary gap. The function should return 0 if N doesn't contain a binary gap.

For example, given N = 1041 the function should return 5, because N has binary representation 10000010001 and so its longest binary gap is of length 5. Given N = 32 the function should return 0, because N has binary representation '100000' and thus no binary gaps.

Write an ****efficient**** algorithm for the following assumptions:

> - N is an integer within the range [1..2,147,483,647].
```