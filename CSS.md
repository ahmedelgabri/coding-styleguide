#CSS Styleguide


## Table of contents

* General
* Style
    * file organization
    * Comments
    * Whitespace
    * Sass (SCSS)
* Writing CSS
    * OOCSS
    * BEM
    * Naming conventions
    * Components
    * JS Hooks
    * IDs vs Classes
    * Selectors
    * Layout
    * Units

## General

## Style

* Use 4 spaces for indentation.
* Always try to abstract patterns as much as possible to write less code & make your code easier to maintain & more reusable.
* Avoid using IDs & use classes, cause classes are reusable.
* Avoid over qualified selectors `div.something {}` it should be `.something {}`.
* Avoid chaining classes `.box.red` & use multiple classes extension on the element instead _More in OOCSS & BEM_
* If you are not supporting IE7 always use `box-sizing: border-box`.
* Don't use `!important`, use the cascade as much as you can.
* `rem` for font-sizing
* `em` for margin & padding. _especially vertical spacing if you want to keep a vertical rhythm_
* `%` for widths

### File organization

Utilize preprocessors power & always break down your code into separate files. But each of your component in a separate file & import them in your main file.

`main.scss`

    ```scss
    @import '_component';
    ```

### Comments

Always write useful comments for anything you write or you think it might confuse you _believe me it happens_ or your team members.

When using Sass, always use the Sass comment format `//` instead of the CSS one `/* */` unless specified otherwise.

Comments are for you & your team, make sure in your build process all the comments are stripped out.

There are 4 comment format used.

**Block Comment**
Mainly used at the top of the file with the name _Always in uppercase_ & a description of the file. Also can be used within a single file between variations.

    //=========================================================================
    // NAME OF THE COMPONENT
    //
    // Description:
    // Lorem ipsum dolor sit amet
    //=========================================================================


**Section Comment**
Used to differentiate between different sections in one file, with only the title of the sub-section _always in uppercase_

    // SUB SECTION
    // ------------------------------------------------------------------------


** Documentation Comment**
Mainly used to document a component & it follows a specific format.

[check here](https://github.com/nopr/sassdown)
Component name:

** Inline Comment **

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
//=============================
// BLOCK COMMENT
//=============================

.selector {

}
```

3 Carriage returns between each rule & between documentation comment & a rule.

```scss
/*
    DOCUMENTATION COMMENT
*/



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
//=================
// BUTTONS
//=================

.selector {
    // code
}





// PRIMARY BUTTONS
--------------------

.selector {
    // code
}
```

## Sass (SCSS)