# snug – super neat utility generator
SCSS toolkit to create utility classes with ease.


> ❗ snug is still under development and functionality may change


## Requirements
For now you need to use [dart sass](https://sass-lang.com/dart-sass) to compile your styles.


## Available variants
Name                 | Type
:--                  | :--
responsive           | `@media`
dark                 | `@media`
light                | `@media`
`pseudo-class`       | [`pseudo-class`](https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-classes#alphabetical_index)
group-`pseudo-class` | [`pseudo-class`](https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-classes#alphabetical_index)


## Basic Usage
```scss
@use '@snug/core' as * with (
  $breakpoints: (
    's': 640px,
    'm': 768px,
    'l': 1024px,
  )
);

// Basic responsive variants
.banana {
  @include variants('responsive') {
    color: gold;
  }
}

// Adding additional variants
.banana {
  @include variants('responsive' 'hover' 'group-hover') {
    color: gold;
  }
}

```


## Advanced Usage
When using modifiers that change the same or a more specific css property these must be grouped by breakpoint.
A more specific property would be something like `padding-top` to `padding`.

```scss
// Wrap your code like this to have your modifiers grouped by breakpoint
@include variants('responsive') using ($props...) {
  .p-1 {
    @include variants($props...) {
      padding: 0.25rem;
    }
  }

  .pt-1 {
    @include variants($props...) {
      padding-top: 0.25rem;
    }
  }
}

```


## Performance
