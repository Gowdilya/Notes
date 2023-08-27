#DSA
> [!NOTE]
> Important to have a plan when coding BS algorithm. Don’t confuse +1/-1 indexes.` [lo,hi) → lo is inclusive, and hi is exclusive in this algorithm.`

Assume array is in Order...

```js
export default function bs_list(haystack: number[], needle: number): boolean {
    let lo = 0;
    let hi = haystack.length;
    do {
        const m = Math.floor(lo + (hi - lo)/2);
        const v = haystack[m];

        if(v === needle){
            return true;
        } else if ( v > needle){
            hi = m;
        }else{
            lo = m + 1;
        }
    }while(lo < hi );
    return false;
}

```