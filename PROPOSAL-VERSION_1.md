# JCSS: CSS-in-JS and Javascript CSS Architecture
This architecture is meant to provide a platform where the developer can use CSS in Javascript and vice versa (Using Javascript in CSS). This will work completely different from the popular architecture [JSS](https://cssinjs.org/?v=v10.10.1) since our project will add a new rule to the CSS, making it a CSS superset.

### Ruleset:
1. JCSS's CSS must have a rule called `@export`
2. The rule mentioned above (`@export`) must act like a media rule.
3. The rule mentioned above will have a special keyword called `this`

### How it will work:
Here's a small example:
```css
/* style.css */
@export Anchor {
    this {
        color: #ababab;
    }
    this:hover {
        transform: scale( 1.1 );
    }
}
```
And let's assume you have another file called `main.js`
```js
/* main.js */
import { Anchor, default as Style } from 'style.css';

// Anchor object MUST AT LEAST CONTAIN the property "className"
// Class name can be randomized and if any change is going to happen
// it must change the underlying style as well.
console.log( Anchor.className );
// Example output: anchor-7zhfgr

// Style is a CSSOM object. You can modify it and you can
// change some of the properties, then you can get the raw
// CSS using `Style.cssText` property
console.log( Style.cssText );
```
