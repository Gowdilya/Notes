#JavaScript #Coding

```js
const t2 = [1, 1, 2, 7, 4, 5, 5];

function RemoveDupe(arr: number[]) {
	var newArr = [];
	var numMap = new Map();
	for (let i = 0; i < arr.length; i++) {
	if (!numMap.get(arr[i])) {
		newArr.push(t2[i]);
	}

numMap.set(arr[i], true);

}
	return newArr;
}

  

console.log(RemoveDupe(t2));
```