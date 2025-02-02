# JCSS: CSS-in-JS and Javascript CSS Architecture
This architecture is meant to provide a platform where the developer can use CSS in Javascript and vice versa (Using Javascript in CSS). This will work completely different from the popular architecture [JSS](https://cssinjs.org/?v=v10.10.1) since our project will add a new rule to the CSS, making it a CSS superset.

### Ruleset:
1. It must support [Proposal Version 1](./PROPOSAL-VERSION_1.md)
2. JCSS's CSS must have a rule called `@javascript`
3. The rule mentioned above will contain a valid Javascript code
4. To use Javascript inline, you must use `?()` syntax or `.()` syntax

### How it will work:
Here's some small examples:
```css
/* Define javascript variables */
@javascript {
    const myColor = ( ( Math.random() * 10 ) > 5 ) ? '#31AF82' : '#FF6550';
}
@export Anchor {
    this {
        color: ?( myColor );
    }
    this:hover {
        transform: scale( 1.1 );
    }
}
```
```css
/* Inline Javascript */
@export Anchor {
    this {
        color: ?( ( ( Math.random() * 10 ) > 5 ) ? '#31AF82' : '#FF6550' );
    }
    this:hover {
        transform: scale( 1.1 );
    }
}
```
```css
/* Run code with interval */
@export Anchor {
    this {
        color: .(
            ( ( Math.random() * 10 ) > 5 ) ? '#31AF82' : '#FF6550',
            100
        );
    }
    this:hover {
        transform: scale( 1.1 );
    }
}
```
