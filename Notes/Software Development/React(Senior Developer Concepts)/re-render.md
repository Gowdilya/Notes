#react

Happens when props or state of a component change.
We can prevent unnecessary re-rendering, useCallback, useMemo etc...
(Should Component Update for old react)

This means the parent would have to re-render, which will **trigger re-render of the child component regardless of its props**. Only when memoization techniques are used ( React.memo , useMemo ), then props change becomes important.