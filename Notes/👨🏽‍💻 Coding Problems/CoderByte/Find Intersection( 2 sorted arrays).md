#Hashmap
Have the function FindIntersection(**strArr**) read the array of strings stored in **strArr** which will contain 2 elements: the first element will represent a list of comma-separated numbers sorted in ascending order, the second element will represent a second list of comma-separated numbers (also sorted). Your goal is to return a comma-separated string containing the numbers that occur in elements of **strArr** in sorted order. If there is no intersection, return the string **false**.
![[Screenshot 2023-08-18 at 4.08.56 PM.png]]
#### Examples
Input: ["1, 3, 4, 7, 13", "1, 2, 4, 13, 15"]  
Output: 1,4,13

Input: ["1, 3, 9, 10, 17, 18", "1, 4, 9, 10"]  
Output: 1,9,10

# Brute Force - 2 nested loops O(n*m)?

# First Attempt:

```js
function FindIntersection(strArr) {
	var array1 = strArr[0].split(',');
	var array2 = strArr[1].split(',');
	strArr = array1.filter(value => array2.includes(value));
return strArr;
}
```


> [!NOTE] 2nd  Solution:
> tricky since after split some numbers in array have space in front.... ["1, 2, 4"].split ->["1"," 2", "4"]... as you can see 2 and 4 have space in front which need to be trimmed




```jsx
function FindIntersection(strArr) {
	var array1 = strArr[0].split(',').map(item=>item.trim());
	var array2 = strArr[1].split(',').map(item=>item.trim());
	strArr = array1.filter(value => array2.includes(value));
	return strArr.length > 0?strArr.toString():false;
}

// keep this function call here

console.log(FindIntersection(readline()));
```


> [!NOTE] Solution
> split(", " `)  includes space charecter

# Solution:
```jsx
function FindIntersection(strArr) {
	var array1 = strArr[0].split(', ');
	var array2 = strArr[1].split(', ');
	let MatchMap = {};
	let resultArr = [];
	array1.forEach(num => matchMap[num] = true);
	array2.forEach(num=>{
		if(matchMap[num]){
			resultArr.push(num);
		}
	})
	if(resultArr.length > 0){
		return resultArr.join(",");
	}
	return false;
}

// keep this function call here

console.log(FindIntersection(readline()));

```

O(n + m) is linear which is better that nested loop O(nm)