#css

#### width of gutters between columns/rows
Specifies the size of the grid lines.

column-gap  
row-gap  
grid-column-gap  
grid-row-gap

The gutters are only created _between_ the columns/rows, not on the outer edges.

```css
.container { 
	grid-template-columns: 100px 50px 100px;
	grid-template-rows: 80px auto 80px;
	column-gap: 10px; 
	row-gap: 15px;
 }
```
![[Screenshot 2023-08-08 at 5.29.24 PM.png]]