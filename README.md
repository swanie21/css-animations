# CSS Animations using Transitions &amp; Transforms

## CSS transitions can enrich user experiences by adding animations to elements by smoothly changing CSS values over a specified duration

## CSS transforms change the shape and position of the content by rotation, skewing, scaling and translation in 2D and 3D space

[Live animations demo](http://kirstenswanson.io/css-animations/)

## Transition Examples:

```
button {
  transition-duration: 0.3s;
  transition-property: background;
  transition-timing-function: ease;
}
```
Shorthand:
```
button {
  transition: background 0.3s ease;
}
```

The `transition-timing-function` value allows the speed of the transition to change over time. There are 6 values for this property: `ease`, `linear`, `ease-in`, `ease-out`, `ease-in-out` and `cubic-bezier`. The `ease` value is the default value.

Add a `transition-delay` property to delay the transition the moment the change of state is triggered

```
button {
  transition-delay: 0.5
  transition-duration: 0.3s;
  transition-property: background;
  transition-timing-function: ease;
}
```

Shorthand:
```
button {
  transition: background 0.3s ease 0.5;
}
```

You might think that the transition property goes on the pseudo-class like the `:hover` state, but you might want the transition triggered on other states like `:focus`, so you should only declare the transition on the normal state.

```
button {
  background: #2b5ea2;
  transition-delay: 0.5
  transition-duration: 0.3s;
  transition-property: background;
  transition-timing-function: ease;
  &:hover, &:focus {
    background: darken(#2b5ea2, 15%);
  }
}
```

You can chain multiple transition properties

```
button {
  transition: background 0.5s ease, color 0.5s linear;
}
```

Shorthand:
```
button {
  transition: all 0.5s ease;`
}
```
Both the background and the color would be transitioned

By stating the `all` value you can target all the available properties so they all have the same duration and timing function on all the pseudo-class states (:hover, :focus, :active).

Some other CSS properties that can be transitioned include `width`, `opacity`, `position` and `font-size`. Click [here](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_animated_properties) for the complete list of properties that can be animated.

## Transform Examples:

`scale()` increases or decreases the size of an element    

```
button:hover {
  transform: scale(2);
}
```
The button will be twice the original size when you hover over it

You can pass in two values into `scale(x, y)`  
```
button:hover {
  transform: scale(2, 3);
}
```
The button will be twice its original width and triple its original height

## Animation Example:

CSS3 animations use `keyframes` to specify what styles the element will have at certain times. To specify when the styling changes should occur you can use percentages or the keywords "from" (0%) and "to" (100%). Additionally, the animation needs an identifier or name in order to reference the animation when you want to call it. The animation identifier in the example below is `hover-pulse`.

```
button:hover {
  animation-name: hover-pulse;
  animation-duration: 1s;
  animation-timing-function: linear;
  animation-iteration-count: infinite;
}

@keyframes hover-pulse {
  25% {
    transform: scale(1.1);
  }
  75% {
    transform: scale(0.9);
  }
}
```

Shorthand:
```
button:hover {
  animation: hover-pulse 1s linear infinite;
}
```
This button will infinitely pulse increasing and decreasing in size when hovered on
