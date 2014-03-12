#CSS Styleguide


## Table of contents

* [Summary](#summary)
* [Terminology](#terminology)
* [Style](#style)
    * [file organization](#file-organization)
    * [Comments](#comments)
    * [Whitespace](#whitespace)
* [Concepts](#concepts)
    * [OOCSS](#oocss)
    * [BEM](#bem)
    * [Source Order](#source-order)
    * [IDs vs classes](#IDs-vs-classes)
* [Writing CSS](#writing-css)
    * [Sass (SCSS)](#sass-scss)
    * [Selectors](#selectors)
    * [Naming conventions](#naming-conventions)
    * [Units](#units)
    * [Shorthand](#shorthand)
    * [Components](#components)
    * [JS Hooks](#js-hooks)
    * [Layout](#layout)
* [RTL](#rtl)

---

## Summary

1- Use the BEM (Block Element Modifier) methodology
2- Find common patterns in your code and abstract them so they can become reusable components.
3- Think about how you can write more clean, efficient and modular components
4- Be critical of your code and the code of others. Try and learn/recognize 'code smells' and refactor them.

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
* Hyphens or Underscores. _(check [BEM](#bem))_
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

**Block Comment**

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


**Section Comment**

Used to differentiate between different sections in one file, with only the title of the sub-section _always in uppercase_

    // SUB SECTION
    // ------------------------------------------------------------------------


**Documentation Comment**

Mainly used to document a component & it follows a specific format.

[check here](https://github.com/nopr/sassdown)
Component name:

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

or

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

### OOCSS
WIP

### BEM
WIP

### Source Order
WIP

### Classes vs IDs

*Avoid using IDs & use classes*

WIP

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
### Selectors
WIP

### Naming conventions
WIP

### Units
* `rem` for font-sizing
* `em` for margin & padding. _especially vertical spacing if you want to keep a vertical rhythm_
* `%` for widths

### Shorthand
WIP

### Components
WIP

### JS Hooks

**_Never use CSS classes as JavaScript hooks._** For JavaScript Hooks always prefix your classes with `.js-` prefix.

```html
<button class="js-modal"></button>
```

**Note**: I'm thinking about changing this & use `data-` attributes instead, for the time being stick to prefixed classes

### Layout
WIP

---

##RTL
WIP
