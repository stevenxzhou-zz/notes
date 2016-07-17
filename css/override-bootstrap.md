How to overide css lib such as Bootstrap?

#### 1. CSS Priority Score
The default priority score of css defined as following:

- 1000 !important
- 100 points for IDs 
- 10 points for classes and pseudo-classes
- 1 point for tag selectors and pseudo-elements
 
#### 2. How's the load sequence work with priority Priority Score?
```javascript
// PriorityScore Will always be mort important
if (stylesheet1.style.priorityScore > stylesheet2.style.priorityScore) {
	return stylesheet1.style;
} else if (stylesheet1.style.priorityScore < stylesheet2.style.priorityScore) {
	return stylesheet2.style;
} else { //If priorityScore even then check their File Load sequence
	if (stylesheet1.order > stylesheet2.order) {
		return stylesheet1.style;
	} else if (stylesheet1.order < stylesheet2.order) {
		return stylesheet2.style;
	} else { // If they are in the same file, then check Style load sequence
		if (stylesheet1.style.order > stylesheet2.style.order) {
			return stylesheet1.style.order;
		} else {
			return stylesheet2.style.order;
		}
	}
}
```

#### 3. Solution:
`<body id=“bootstrap-overrides”></body>`
```css
.jumbotron h1 {  /* 10+1 = 101 */
	line-height: 1;
	color: inherit;
}

h1 {  /* 1 = 101 */
	line-height: 1;
	color: inherit;
}

bootstrap-overrides h1 { /* 100+1 = 101 */
	line-height: 1;
	color: inherit;
}
```
#### 4. Reference
[1] Stackoverflow: [best way to override bootstrap css](http://stackoverflow.com/questions/20721248/best-way-to-override-bootstrap-css)