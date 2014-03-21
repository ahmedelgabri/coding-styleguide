#CSS Styleguide


## Table of contents

* [Summary](#summary)
* [Terminology](#terminology)
* [Style](#style)
    * [file organization](#file-organization)
    * [Comments](#comments)
    * [Whitespace](#whitespace)
* [Concepts](#concepts)
    * [BEM](#bem-oocss)_(OOCSS)_
    * [Source Order](#source-order)
    * [IDs vs classes](#IDs-vs-classes)
* [Writing CSS](#writing-css)
    * [Sass (SCSS)](#sass-scss)
    * [Units](#units)
    * [Shorthand](#shorthand)
    * [JS Hooks](#js-hooks)
    * [Layout](#layout)

---

## Summary

1. Use the BEM (Block Element Modifier) methodology
2. Find common patterns in your code and abstract them so they can become reusable components.
3. Think about how you can write more clean, efficient and modular components
4. Be critical of your code and the code of others. Try and learn/recognize 'code smells' and refactor them.

## Terminology

A CSS rule

```css
.selector { // Declaration block
    |- Declaration -|
    property: value;
}
```


## Style

* Use 4 spaces for indentation.
* Avoid using IDs always use Classes, cause they are reusable & have lower specificity.
* Multi-line.
* Hyphens or Underscores. _(check [BEM](#bem-oocss))_
* Always include the final semi-colon in a ruleset.
* Always try to abstract patterns as much as possible to write less code & make your code easier to maintain & more reusable.
* Avoid over qualified selectors like this `div.something {}` it should be `.something {}`.
* Avoid chaining classes `.box.red` & use multiple classes extension on the element instead _More in OOCSS & BEM_
* If you are not supporting IE7 always use `box-sizing: border-box`.
* Don't use `!important`, use the cascade as much as you can.

### File organization

Utilize the power of preprocessors & always break down your code into separate files & import them in your main file.

`main.scss`

```scss
@import '_component1';
@import '_component2';
```

### Comments

Always write useful comments for anything you write or you think it might confuse you _believe me it happens_ or your team members.

When using Sass, always use the Sass comment format `//` instead of the CSS one `/* */` unless specified otherwise.

Comments are for you & your team, make sure in your build process all the comments are stripped out.

There are 4 comment format used.

**Block/Section Comment**

Mainly used at the top of the file with the name _Always in uppercase_ & a description of the file. Also can be used within a single file between variations.

    /*=========================================================================
     NAME OF THE COMPONENT

     Description:
     Lorem ipsum dolor sit amet

     MARKUP:
        <ul class="component component--modifier">
            <li class="component__child"> Something </li>
            <li class="component__child"> Something </li>
        </ul>

     Classes:
        .component - brief description
        .component--modifier - brief description
        .component__child - brief description

    =========================================================================*?


**Sub-section Comment**

Used to differentiate between different sections in one file, with only the title of the sub-section _always in uppercase_

    // SUB SECTION
    // ------------------------------------------------------------------------

**Inline Comment**

Which the simple form of comments used for describing hacks, techniques in the code itself.

```scss
.class {
    overflow: hidden; // Clearing floats
}
```

### Whitespace

1 space between the selector & the opening curly bracket and between the property & value.

```scss
.selector {
    property: value;
}
```

1 Carriage return between a comment & a rule.

```scss
// SECTION COMMENT
------------------------------

.selector {

}
```

or

```scss
/*=============================
 BLOCK COMMENT
=============================*/

.selector {

}
```

3 Carriage return between each rule

```scss
.selector {
    // code
}



.selector {
    // code
}
```

5 Carriage returns between each section (i.e. buttons main styles & primary buttons styling).

```scss
/*=================
 BUTTONS
=================*/

.selector {
    // code
}





// PRIMARY BUTTONS
--------------------

.selector {
    // code
}
```

---

## Concepts

### BEM _OOCSS_

BEM _Block, Element, Modifier_ is an OOCSS Methodology that helps to keep your component as modular, fixable & maintainable as possible.

Some posts that will help understand BEM:
- [About HTML semantics and front-end architecture](http://nicolasgallagher.com/about-html-semantics-front-end-architecture/)
- [Getting your head around BEM syntax](http://csswizardry.com/2013/01/mindbemding-getting-your-head-round-bem-syntax/)
- [Code smells in CSS](http://csswizardry.com/2012/11/code-smells-in-css/)
- [Using more classes in your HTML](http://csswizardry.com/2012/10/a-classless-class-on-using-more-classes-in-your-html/)
- [CSS selector intent](http://csswizardry.com/2012/07/shoot-to-kill-css-selector-intent/)

#### Some points to keep in mind when using BEM

- Components shouldn't be tightly coupled to their placement in the layout.
- Avoid setting dimensions `width`, `height` on the component, a component should fit inside the space which it's placed.
- Don't leave anything for the chance, make sure your selectors are specific as they need to be. so instead of doing `ul li` use class `.nav-item` on the `<li>` & target it with just `.nav-item`

#### The BEM naming convention I'm using:
 | Name                     | Class                           |
 | -------------------------| --------------------------------|
 | Block _Componenet_ class | `.<prefix>-component`           |
 | Element _Child_ class    | `.<prefix>-component__child`    |
 | Modifier class           | `.<prefix>-component--modifier` |





To learn more about the `<prefix>` read [Global scope, Namespacing & CSS](https://medium.com/p/681bda44c43e).

Example:

```html
<ul class="p-nav p-nav--large">
    <li class="p-nav__item">Menu item</li>
    <li class="p-nav__item">Menu item</li>
    <li class="p-nav__item">Menu item</li>
    <li class="p-nav__item">Menu item</li>
    <li class="p-nav__item">Menu item</li>
    <li class="p-nav__item">Menu item</li>
</ul>
```

You can also have block inside block
```html
<div class="p-article">
    <p class="p-article__body">Lorem ipsum dolor sit amet, consectetur adipisicing elit. Similique, officia, dolores, modi dolorem rem hic vero quis animi fugiat consectetur facilis doloremque velit eum provident at enim ex quibusdam ut.</p>

    <div class="p-badge">
        <a href="#" class="p-badge__link">Some link</a>
    </div>
</div>
```

### Source Order
Since we are using multiple files & using an OOCSS methodology to write CSS we should use the source order in our advantage & only extend what we are inheriting without overriding much of the CSS.

### Classes vs IDs

There is no difference between IDs & Classes in general other than 2 things:

- IDs are unique so you can only have one ID per page which makes them not modular.
- IDs has more specificity than Classes which can cause maintainability issues with large code bases.

So there is no point actually to prefer IDs over Classes when writing CSS.

---

## Writing CSS

### Sass (SCSS)

I always try to keep my CSS flat _less specificity_ & relay more on the cascade. But if you need to nest CSS, maximum nest 2 levels _exceptions for Pseudo elements/classes_

```scss
.component {
    display: inline;

    .component__child {
        color: red;

        &:hover {
            color: green;
        }
    }
}
```

`@includes` should always be on top & followed by 1 Carriage return.

```scss
.selector {
    @include mixin1();
    @include mixin2();

    display: block;
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

**Wrong** Now this modifier class is actually overriding the main component class & not extending it. _We are overriding the pattern image & padding too_ A better way would be like this.

```scss
.component {
    background-color: #ccc;
    background-image: url(../images/pattern.png);
    background-repeat: no-repeat;
    padding-right: .5em;
    padding-left: .5em;
}


.component--green {
    background: green;
    padding-top: .5em;
    padding-bottom: .5em;
}
```

Yes, more lines but more explicit, understandable & maintainable.

### JS Hooks

**_Never use CSS classes as JavaScript hooks._** For JavaScript Hooks always prefix your classes with `.js-` prefix.

```html
<button class="js-modal"></button>
```

**Note**: I'm thinking about changing this & use `data-` attributes instead, for the time being stick to prefixed classes

### Layout
**General rule:** Layouts would be handled by the grid a component shouldn't have a `width` set on it.
