# [XLN Code Style Guide](../README.md) - HTML

> Style guide for HTML at XLN Audio. Inspired by the [Google HTML/CSS Style Guide](https://google.github.io/styleguide/htmlcssguide.xml#HTML_Formatting_Rules)

## Table of Contents 
  1. [General style rules](#general-style-rules)
    - [Protocol](#protocol)
    - [Indentation](#indentation)
    - [Comments](#comments)
  1. [HTML style rules](#html-style-rules)
    - [Multimedia fallback](#multimedia-fallback)
    - [Separation of concerns](#separation-of-concerns)
    - [Type attributes](#type-attributes)
    - [HTML quotation marks](#html-quotation-marks)

## General style rules

### Protocol
Omit the protocol from embedded resources - prevents mixed content issues and results in minor file size savings.

```html
<!-- Not recommended -->
<script src="https://www.google.com/js/gweb/analytics/autotrack.js"></script>

<!-- Recommended -->
<script src="//www.google.com/js/gweb/analytics/autotrack.js"></script>
```

**[⬆ back to top](#table-of-contents)**

### Indentation
Soft tabs (4 spaces) for indentation 

**[⬆ back to top](#table-of-contents)**

### Capitilization 
All code must be lowercase - elements, attributes, attribute values (except `text/CDATA`) etc

```html
<!-- Not recommended -->
<A HREF="/">Home</A>

<!-- Recommended -->
<img src="google.png" alt="Google">
```

**[⬆ back to top](#table-of-contents)**

### Comments
Comment external snippets and files

```html
<!-- Google Analytics -->
<script>
(function(i,s,o,g,r,a,m){i['GoogleAnalyticsObject']=r;i[r]=i[r]||function(){
(i[r].q=i[r].q||[]).push(arguments)},i[r].l=1*new Date();a=s.createElement(o),
m=s.getElementsByTagName(o)[0];a.async=1;a.src=g;m.parentNode.insertBefore(a,m)
})(window,document,'script','https://www.google-analytics.com/analytics.js','ga');

ga('create', 'UA-XXXXX-Y', 'auto');
ga('send', 'pageview');
</script>
<!-- End Google Analytics -->
```

**[⬆ back to top](#table-of-contents)**

## HTML style rules

### Multimedia fallback
For multimedia, such as images, videos, animated objects via canvas, make sure to offer alternative access. For images that means use of meaningful alternative text (alt) and for video and audio transcripts and captions, if available.

```html
<!-- Not recommended -->
<img src="spreadsheet.png">

<!-- Recommended -->
<img src="spreadsheet.png" alt="Spreadsheet screenshot.">
```

**[⬆ back to top](#table-of-contents)**

### Type attributes
It is not necessary to specify type attributes 

```html
<!-- Not recommended -->
<link rel="stylesheet" href="//www.google.com/css/maia.css"
  type="text/css">

<!-- Recommended -->
<link rel="stylesheet" href="//www.google.com/css/maia.css">

<!-- Not recommended -->
<script src="//www.google.com/js/gweb/analytics/autotrack.js"
  type="text/javascript"></script>

<!-- Recommended -->
<script src="//www.google.com/js/gweb/analytics/autotrack.js"></script>
```

**[⬆ back to top](#table-of-contents)**

### HTML quotation marks
Use double `"` quotation marks rather than single quotation marks `'` around attribute values
```html 
<!-- Not recommended -->
<a class='maia-button maia-button-secondary'>Sign in</a>

<!-- Recommended -->
<a class="maia-button maia-button-secondary">Sign in</a>
```

**[⬆ back to top](#table-of-contents)**