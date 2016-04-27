#CSS Styleguide


## Table of contents

* [Summary](#summary)
* [Terminology](#terminology)
* [Style](#style)
    * [file organization](#file-organization)
* [Concepts](#concepts)
    * [Atomic CSS](#atomic-css)
    * [IDs vs classes](#IDs-vs-classes)
* [Writing CSS](#writing-css)
    * [Preprocessors](#preprocessors)
    * [Units](#units)
    * [Shorthand](#shorthand)
    * [JS Hooks](#js-hooks)
    * [Layout](#layout)
    * [Linters](#linters)

---

## Summary

1. Use atomic classes and move the repetition to HTML, easier to debug and maintain.
2. Every class should only do one thing only.
3. Don't nest, keep your CSS flat.
4. Don't use IDs.
5. Be critical of your code and the code of others. Try and learn/recognize 'code smells' and refactor them.

## Terminology

A CSS rule

```css
.selector { // Declaration block
    |- Declaration -|
    property: value;
}
```


## Style

* Use 2 spaces for indentation.
* Avoid using IDs always use Classes, because they are reusable & have lower specificity.
* Multi-line.
* Always include the final semi-colon in a ruleset.
* Avoid nesting.
* Don't use `!important`, use the cascade as much as you can.

### File organization

Utilize the power of preprocessors & always break down your code into separate files & import them in your main file.

`main.scss`

```scss
@import '_component1';
@import '_component2';
```

### Whitespace

1 space between the selector & the opening curly bracket and between the property & value.

```scss
.selector {
    property: value;
}
```

1 Carriage return between a comment & a rule.

---

## Concepts

### Atomic CSS
Some posts that will help understand:
- [About HTML semantics and front-end architecture](http://nicolasgallagher.com/about-html-semantics-front-end-architecture/)
- [Functional Programming, CSS, and your sanity](http://www.jon.gold/2015/07/functional-css/)
- [Building and shipping functional CSS](https://blog.colepeters.com/building-and-shipping-functional-css/)
- [Code smells in CSS](http://csswizardry.com/2012/11/code-smells-in-css/)
- [Using more classes in your HTML](http://csswizardry.com/2012/10/a-classless-class-on-using-more-classes-in-your-html/)
- [CSS selector intent](http://csswizardry.com/2012/07/shoot-to-kill-css-selector-intent/)
- [Global scope, Namespacing & CSS](http://gabri.me/2013/08/global-scope-namespacing-css/).

### Classes vs IDs

There is no difference between IDs & Classes in general other than 2 things:

- IDs are unique so you can only have one ID per page which makes them not modular.
- IDs has more specificity than Classes which can cause maintainability issues with large code bases.

So there is no point actually to prefer IDs over Classes when writing CSS.

---

## Writing CSS

### Preprocessors

I've used all of them, but I prefer PostCSS. It gives me control over the features that I can use and it works well with the npm/node workflow.

I always try to keep my CSS flat _less specificity_. Exceptions for nesting are Pseudo elements/classes and **I Don't use `mixins`**. They can lead to convoluted code that's hard to debug or maintain.

```scss
.button {
    color: red;

    &:hover {
        color: green;
    }
}
```

### Units
I prefer to use relative units as much as possible cause it' more flexible

* `rem` for font-sizing
* `em` for margin & padding. _especially vertical spacing if you want to keep a vertical rhythm_
* `%` for widths

### Shorthand

Shorthands are bad for extending components, in general I don't use them & here is an example why.

Let's imagine that we have a component that we want to extend it to maybe have a different background & padding.

```scss
.component {
    background: #ccc url(../images/pattern.png) no-repeat 0 0;
    padding: 0 .5em;
}


.component--green {
    background: green;
    padding: .5em .5em;
}
```

**This is not right** now this modifier class is actually overriding the main component class & not extending it. _We are overriding the pattern image & padding too_ A better way would be like this.

```scss
.component {
    background-color: #ccc;
    background-image: url(../images/pattern.png);
    background-repeat: no-repeat;
    padding-right: .5em;
    padding-left: .5em;
}


.component--green {
    background-color: green;
    padding-top: .5em;
    padding-bottom: .5em;
}
```

Yes, more lines but more explicit, understandable & maintainable. BTW, atomic CSS fixes this issue by removing the duplication from your code and encouraging composition over overriding.

### JS Hooks

**_Never use CSS classes as JavaScript hooks._** For JavaScript Hooks always prefix your classes with `.js-` prefix.

```html
<button class="js-modal"></button>
```

**Note**: I'm thinking about changing this & use `data-` attributes instead, for the time being stick to prefixed classes

### Layout
**General rule:** Layouts would be handled by the grid a component shouldn't have a `width` set on it.


### Linters

I use [stylelint](https://github.com/stylelint/stylelint)
