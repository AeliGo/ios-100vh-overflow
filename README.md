## 100vh overflow issue on IOS (safari & chrome)

The problem we have been receiving after adding the `height: 100vh` is content overflow on ios. It happens due to the calculation method which Safari and Chrome are using. Mobile devices calc browser viewport as (**top bar + document + bottom bar**) = `100vh`. 

### Solution 1:
Using height:100%; for html and body
```css
html,
body {
	height: 100%;
}
```
### Solution 2:
![enter image description here](https://i0.wp.com/css-tricks.com/wp-content/uploads/2020/05/problem.png?resize=1536,1536&ssl=1)
On the left, the browser navigation bar (considered browser chrome) is covering up the footer making it appear that the footer is beyond 100vh when it is not. On the right, the `-webkit-fill-available` property is being used rather than viewport units to fix the problem.
```css
html,
body {
	height: 100vh;
	/* mobile viewport bug fix */
	height: -webkit-fill-available;
}
```
