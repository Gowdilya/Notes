### Equivalent Keypresses

Have the function EquivalentKeypresses(**strArr**) read the array of strings stored in **strArr** which will contain 2 strings representing two comma separated lists of keypresses. Your goal is to return the string **true** if the keypresses produce the same printable string and the string **false** if they do not. A keypress can be either a printable character or a backspace represented by **-B**. You can produce a printable string from such a string of keypresses by having backspaces erase one preceding character.

#### Examples

Input: ["a,b,c,d", "a,b,c,d,-B,d"]  
Output: true

```jsx
function EquivalentKeypresses(strArr) {
var a = strArr[0].split(',');
var b = strArr[1].split(',');
	var keyPA= [];
	var keyPB =[];
for( let i = 0; i < a.length && i< b.length; i ++){
	if(a[i]){
		if(a[i] =='-B' && keyPA.length > 0){
			keyPA.pop();
		}else{
			keyPA.push(a[i]);
		}
	}
	if(b[i]){
		if(b[i] ==='-B' && keyPB.length > 0){
			keyPB.pop();
		}else{
			keyPB.push(b[i]);
		}
	}
	}
	strArr = (keyPA.join() === keyPB.join());
// code goes here
return strArr;

}
```

