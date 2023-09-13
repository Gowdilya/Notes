
#JavaScript #interview 


print 1 ... 100
"Fizz" if divisible by 3
"Buzz" if divisible by 5
"FizzBuzz" if divisible by 3 and 5

bonus:"Bazz" if divisible by 7

Print numbers 1...100, if the number is divisible by 3 print fizz, if it is divisible by 5 print buzz. If it's divisible by both print fizzbuzz
```js
for (let i = 1; i <= 100; i++) {
  if (Number.isInteger(i / 3)) {
    console.log("Fizz");
  }
  else if (Number.isInteger(i / 5)) {
    console.log("Buzz");
  }
  else if (Number.isInteger(i / 5) && Number.isInteger(i / 3)) {
    console.log("FizzBuzz");
  } else {
    console.log(i);
  }
}
```

Out put to a single line... O (1)

```js
for (let i = 1; i <= 100; i++) {
  let out = "";
  if (i % 3 === 0) out += "Fizz";
  if (i % 5 === 0) out += "Buzz";
  if (i % 7 === 0) out += "Bazz";
  console.log(out || i);
}
```