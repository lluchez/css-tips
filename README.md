# CSS Tips
Collection of CSS tips


## Selectors

- `:has()` to check for matching siblings. [Documentation](https://developer.mozilla.org/en-US/docs/Web/CSS/:has)
- `~`: [Subsequent-sibling combinator](https://developer.mozilla.org/en-US/docs/Web/CSS/Subsequent-sibling_combinator)
- `:focus-within`. Matches an element if the element or any of its descendants are focused. [Documentation](https://developer.mozilla.org/en-US/docs/Web/CSS/:focus-within)
- `:empty` to style component without any content. [Video](https://www.youtube.com/shorts/CE8hQIvTzGk)

## Positioning

### inset

`inset` allows to specify `top`, `right`, `bottom` and `left` with a single CSS line.
[Documentation](https://developer.mozilla.org/en-US/docs/Web/CSS/inset)

### anchor()

![image](https://github.com/user-attachments/assets/677b666e-4d09-4ae3-99ef-92658a4c696f)


```html
<body>
  <div id="box1"></div>
  <div id="box2" anchor="box1"></div>
</body>
```

```css
. {
  position: absolute;
  bottom: anchor(top);
  left: anchor(center);
}
```

[Reference video](https://www.youtube.com/shorts/fO0XD75u2TI)


## Scrolling

Ability to provide scrolling features (carousel, table of content links) without the need for JavaScript:
- [::scroll-marker](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Selectors/::scroll-marker). See [related video](https://www.youtube.com/watch?v=HXIHpDnsizk)


## Sizing

- `min`
- `max`
- `clamp`, combine `width`, `min-width` and `max-width` into a single command
- `minmax`
- `stretch` (*better alternative to `100%`*). [Ref](https://css-tricks.com/we-completely-missed-width-height-stretch/)


## Text

### Avoid wrapping text

You can use `min-width: fit-content;` instead of `white-space: nowrap;`
[Reference Video](https://www.youtube.com/shorts/4GR_lE1W09o)

### Text Gradients

![image](https://github.com/user-attachments/assets/22910d2e-9849-4717-a303-5aa7b6b87afd)

Can't directly use `color: linear-gradient`.
Instead we can use this tip:

```css
h1 {
  background: linear-gradient(to right, red, blue); /* apply gradient to background */
  background-clip: text; /* limit background painting area */
  color: transparent; /* make text transparent */
}
```

### Counters
```css
:root {
  counter-reset: headings; /* headings is a name */
}
h2 {
  counter-increment: headings; /* increment counter via `counter-increment` */
}
h2:before {
  content: counter(headings); /* show the value of the counter prior to the element
}
```
Allows styled counters:
![image](https://github.com/user-attachments/assets/55700097-a7da-4fb0-bf33-aea6df18dc20)

### Auto increasing inputs (textarea)

```css
textarea {
  field-sizing: content;
}
```

[Official Doc](https://developer.mozilla.org/en-US/docs/Web/CSS/field-sizing). [Youtube Video](https://youtu.be/ElELqkwzcYM?si=8Q2p-yNNJyEup3s1)

## Transitions

### Transition to and from `display: none`

[Youtube video](https://youtu.be/vmDEHAzj2XE?si=kXEVH8Xy8jIgY5Od)


## Scrolling/Snapping

Snap scrolling:

```css
.wrapper {
  display: flex;
  gap: 20px;
  width: 300px;
  overflow-x: scroll;
  scroll-snap-type: x mandatory; /* children need to define `scroll-snap-align`. Could also use `proximity` */
  .card {
    scroll-snap-align: center;
    box-sizing: border-box;
    flex-shrink: 0;
    width: 300px; /* needs to be the same size as the wrapper */
  }
}
```

![image](https://github.com/user-attachments/assets/0aa0eb26-a2f7-4efc-bc2b-1bfa1f452a6d)


## Images

- `backdrop-filter` to control how elements behind will display. Values include `blur`, `invert`, `opacity`, etc. [Documentation](https://developer.mozilla.org/en-US/docs/Web/CSS/backdrop-filter)
- [simple hack for blurry image placeholders](https://leanrada.com/notes/css-only-lqip/). Example: `<img src="…" style="--lqip:350819">`

## CSS Reset

### Minimal Reset

[Reference](https://www.youtube.com/shorts/2lyDv0wOQuQ)

```css
*, *::before, *::after {
  box-sizing: border-box;
}

* {
  margin: 0;
  padding: 0;
  font-inherit;
}

html {
  color-scheme: dark light;
}

body {
  min-height: 100vh;
}

img, picture, svg, video {
  display: block;
  max-width: 100%
}
```
