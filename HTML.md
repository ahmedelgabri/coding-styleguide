#HTML Styleguide


## Table of contents

* [Terminology](#terminology)
* [Style](#style)
* [Internet Explorer](#internet-explorer)
* [RTL](#rtl)
* [Example](#example)

### Terminology

- **Tag**: `<div>`, `<p>`, `<img>`, etc...
- **Element**: `<div> content </div>`
- **Attribute**: `<div class="the class is an attribute">...</div>`
- **Comment**: `<!-- comment -->`
- **Conditional comment**: `<!--[if IE]> IE conditional comment<![endif]-->`

### Style

- HTML5 doctype `<!doctype html>` this works all the way to IE6.
- 4 spaces indentation.
- lowercase tags/attributes. **don't** do this `<DIV></DIV>` _do_ this `<div></div>`
- double quotations for attributes `<div class="something">` not `<div class='something'>`
- HTML syntax not xHTML `<img>` instead of `<img/>`.
- Use ARIA roles and labels when appropriate
- Use HTML5 form controls when applicable to trigger the right keyboard on mobile (`url`, `email`, etc...)
- Organize your `<head>` section as follow:
    1. `<title>` tag
    2. `<meta>` elements
    3. Style sheets
    4. Scripts like `Modernizr` or `HTML5 shiv` _(All other scripts should be added before the closing `</body>` tag)_
- for `<script>` tags & style sheets don't use `type` attribute.

    ```html
    <!-- Wrong -->
    <script type="text/javascript" src="script.js"></script>
    <link type="text/css" rel="stylesheet" href="main.css">

    <!-- Right -->
    <link rel="stylesheet" href="main.css">
    <script src="script.js"></script>
    ```


### Internet Explorer

Use Conditional comments hack to serve IE a separate style sheet _(this will be achieved by Sass, you will only write your CSS once & Sass will create 2 separate files for you)_

```html
<!--[if gt IE 8]><!-->
    <link rel="stylesheet" href="css/main.css">
<!--<![endif]-->

<!--[if lte IE 8]>
    <link rel="stylesheet" href="css/ie.css">
<![endif]-->
```

Don't use this:

```html
<!--[if IE 8]><html class="ie8" dir="ltr" lang="en"><![endif]-->
<!--[if IE 9]><html class="ie9" dir="ltr" lang="en"><![endif]-->
<!--[if gt IE 9]><!--> <html dir="ltr" lang="en"> <!--<![endif]-->
```

Cause it'll add more specificity to your CSS selectors & if you wanted to remove IE support you will have to go through all your CSS & clean it up from `.ie-` classes.


### RTL

When dealing with RTL (Right to left) languages like Arabic **don't** use `text-align` & `direction` in CSS to achieve this.

Use `dir` & `lang` attributes on the `<html>` tag like this. `<html dir="rtl" lang="ar">`


### Example

Here is a bare bone HTML document

```html
<!doctype html>
<html lang="en">
<!-- for RTL -->
<html lang="ar" dir="rtl">
<head>
    <title>Page title</title>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <!--[if gt IE 8]><!-->
        <link rel="stylesheet" href="css/main.css">
    <!--<![endif]-->
    <!--[if lte IE 8]>
        <link rel="stylesheet" href="css/ie.css">
    <![endif]-->
    <script src="modernizr.js"></script>
    <link rel="author" type="text/plain" href="humans.txt">
</head>
<body>

    <script src="script.js"></script>
</body>
</html>
```
