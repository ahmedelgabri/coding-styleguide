#HTML Styleguide


## Table of contents

* [Terminology](#terminology)
* [Style](#style)
* [Internet Explorer](#internet-explorer)
* [RTL](#rtl)
* [Templating languages](#templating-languages)
* [Example](#example)

### Terminology

- **Tag**: `<div>`, `<p>`, `<img>`, etc...
- **Element**: `<div> content </div>`
- **Attribute**: `<div class="the class is an attribute">...</div>`
- **Comment**: `<!-- comment -->`
- **Conditional comment**: `<!--[if IE]> IE conditional comment<![endif]-->`

### Style

- HTML5 doctype `<!doctype html>` this works all the way to IE6.
- 2 spaces indentation.
- lowercase tags/attributes. **don't** do this `<DIV></DIV>` _do_ this `<div></div>`
- double quotations for attributes `<div class="something">` not `<div class='something'>`
- HTML syntax not xHTML `<img>` instead of `<img/>`.
- Use ARIA roles and labels when appropriate
- Use HTML5 form controls when applicable to trigger the right keyboard on mobile (`url`, `email`, etc...)
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

If you write CSS properly the amount of CSS fixes you want to do for IE8 and lower will be minimal and you can use simple solutions or even one off hacks in your CSS to fix this. If you have to support IE7 or lower, I can't help you. but I'd use conditional comments to serve a different stylesheet.


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


### Templating languages
Don't indent template logic cause this will add more indentation levels and then your document will turn into a Xmas tree.

**Example:** _using Django/Jinja2 templates_

Indenting the logic.
```html
<div>
  {% if something.somethingelse %}
    <ul>
      {% for name in somedata %}
        <li> {{ name }} </li>
      {% endfor %}
    </ul>
  {% endif %}
</div>
```
Without indenting the logic.
```html
<div>
{% if something.somethingelse %}
  <ul>
    {% for name in somedata %}
    <li> {{ name }} </li>
    {% endfor %}
  </ul>
{% endif %}
</div>
```

### Example

Here is a bare bone HTML document

```html
<!doctype html>
<html lang="en">
<!-- for RTL -->
<html lang="ar" dir="rtl">
<head>
  <meta charset="UTF-8">
  <link rel="stylesheet" href="css/main.css">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <script src="modernizr.js"></script>
  <link rel="author" type="text/plain" href="humans.txt">
  <title>Page title</title>
</head>
<body>

  <script src="script.js"></script>
</body>
</html>
```
