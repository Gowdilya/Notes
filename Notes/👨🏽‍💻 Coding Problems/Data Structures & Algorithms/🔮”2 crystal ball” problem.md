

First crystal ball will iterate the whole array(worst case). in O(sqrt(N)), The second one iterates the subsection that is sqrt(N) size so that also takes O(sqrt(N)).

`O(sqrt(N) + sqrt(N)) = O (2 * sqrt(N)) = O(sqrt(N))`

```js
export default function two_crystal_balls(breaks: boolean[]): number {
    const jmpAmount = Math.floor(Math.sqrt(breaks.length));
    let i = jmpAmount;
    for (; i<breaks.length; i +=jmpAmount){
        if(breaks[i]){
            break;
        }
    }
    i -=jmpAmount;
    for (let j = 0; j < jmpAmount && i < breaks.length; ++ j, ++i){
        if (breaks[i]){
            return i;
        }
    }
    return -1;


}
```