# [XLN Code Style Guide](../README.md) - CSS / Sass

> Loosely based on the [Airbnb CSS / Sass guidelines](https://github.com/airbnb/css)*

## Table of Contents 
  1. [CSS](#css)
    - [Syntax](#syntax)
    - [Selectors](#selectors)
    - [Declaration order](#declaration-order)
    - [Naming convention](#naming-convention)
    - [Comments](#comments)   
    - [ID Selectors]()
    - [JavaScript hooks](#javascript-hooks)    
    - [Border](#border)
  1. [Sass](#sass)
    - [Naming variables](#naming-variables)
    - [Ordering of property declarations](#ordering-of-property-declarations)
    - [Nested selectors](#nested-selectors)
  1. [Architecture](#architecture)
    - [Base folder](#base-folder)
    - [Components folder](#components-folder)
    - [Layout folder](#layout-folder)
    - [Pages folder](#pages-folder)
    - [Themes folder](#themes-folder)
    - [Vendors folder](#vendors-folder)
    - [Abstracts folder](#abstracts-folder)
    - [Main file](#main-file)

## CSS

### Syntax
* Soft tabs (4 spaces) for indentation 
* Strictly no ID selectors
* When using multiple selectors in a rule declaration, give each selector its own line
* Put a space before the opening brace `{` in rule declarations
* Put closing braces `}` of rule declarations on a new line
* Put blank lines between rule declarations
* Properties should be listed alphabetically
* In properties, put a space after the `:` character
* End all declarations with a semi-colon
* Don't include spaces after commas within `rgb()`, `rgba()`, `hsl()`, `hsla()`, or `rect()` values. This helps differentiate multiple color values (comma, no space) from multiple property values (comma with space).
* Don't prefix property values or color parameters with a leading zero (e.g., `.5` instead of `0.5` and `-.5px` instead of `-0.5px`).
* Lowercase all hex values, e.g., `#fff`
* Use shorthand hex values where available, e.g., `#fff` instead of `#ffffff`
* Avoid specifying units for zero values, e.g., `margin: 0;` instead of `margin: 0px;`

**Bad**

```css
.selector, .selector-secondary, .selector[type=text] {
    background-color:rgba(0, 0, 0, 0.5);
    box-shadow:0px 1px 2px #CCC,inset 0 1px 0 #FFFFFF;
    margin:0px 0px 15px;
    padding:15px;
}
```

**Good**

```css
.selector,
.selector-secondary,
.selector[type="text"] {
    background-color: rgba(0,0,0,.5);
    box-shadow: 0 1px 2px #ccc, inset 0 1px 0 #fff;
    margin-bottom: 15px;
    padding: 15px;
}
```

**[⬆ back to top](#table-of-contents)**

### Selectors 
* Use classes over generic element tag for optimum rendering performance
* Keep selectors short and strive to limit the number of elements in each selector to three
* Scope classes to the closest parent **only** when necessary

**Bad**

```css
span { ... }
.page-container #stream .stream-item .tweet .tweet-header .username { ... }
.avatar { ... }
```

**Good**

```css
.avatar { ... }
.tweet-header .username { ... }
.tweet .avatar { ... }
```


**[⬆ back to top](#table-of-contents)**

### Declaration order
* Property declarations should be in alphabetical order
* *TODO: Consider [CSSComb](https://github.com/csscomb/csscomb.js) for automation*

```css
.selector {
    bottom: 0;
    display: block;
    float: right;
    height: 100px; 
    left: 0;
    position: absolute;
    right: 0;
    top: 0;
    width: 100px;
    z-index: 100;  
}
```


**[⬆ back to top](#table-of-contents)**

### Naming convention
* Under review. Consider a hybrid mix of [BEM and OOCSS](http://timhartmann.net/frontend-development/scss-styleguide-with-bem-oocss-smacss/)


**[⬆ back to top](#table-of-contents)**

### Comments
* Prefer single line comments `//` since these are removed when compiled by Sass
* Comments must be on their own line - no end of line comments
* Write detailed comments for code that isn't self-documenting, for example:
    - Uses of z-index
    - Compatibility or browser-specific hacks


**[⬆ back to top](#table-of-contents)**

### ID Selectors
* ID selectors introduce a high level of specificity and should be avoided
* [Read more](https://csswizardry.com/2014/07/hacks-for-dealing-with-specificity/) about CSS specificity


**[⬆ back to top](#table-of-contents)**

### JavaScript hooks
* Avoid binding the same class in both your CSS and JavaScript
* Recommend creating a JavaScript specific class to bind `.js-`

```html
<button class="btn btn-primary js-request-to-book">Request to Book</button>
```

**[⬆ back to top](#table-of-contents)**

### Border 
Use `0` instead of `none` to specify that a style has no border

**Bad**

```css
.foo {
  border: none;
}
```

**Good**

```css
.foo {
  border: 0;
}
```

**[⬆ back to top](#table-of-contents)**

## Sass

### Naming variables
* Use meaningful or generic terms to describe the variable. 
* Prefer dashed-case variable names (e.g. `$my-variable`). 
* Add a `prefix-` to allow for better readability

**Bad**

```scss
// Bad
$red: red;
$yellow: yellow;
```

**Good**

```scss
$color-brand: red;
$color-accent: yellow;
```

**[⬆ back to top](#table-of-contents)**

### Ordering of property declarations

The different items in a Sass rule set go in the following order:

1. Scoped variables
1. Mixin inclusions with `@include` with the exception of media queries
1. Pseudo-class/element nesting with `&`
1. Media queries
1. Regular selector nesting (if necessary)

    ```scss
    .element {
      $scoped-variable: whatever;
      @include mixin($argument);
      property: value;

      &:pseudo {
        // Styles here
      }

      @media (max-width: $screen-sm-max) {
        // Styles here
      }
      
      .nested {
        // Styles here
      }
      
    }
    ```

**[⬆ back to top](#table-of-contents)**

### Nested selectors
Do not nest selectors more than three levels deep

```css
.page-container {
  .content {
    .profile {
      // STOP!
    }
  }
}
```

**[⬆ back to top](#table-of-contents)**

## Architecture 
File architecture is based on the *7-1 Pattern:* All partials are categorized into 7 different folders, and a single file at root level (`main.scss`) which imports them all to be complied into a CSS stylesheet.

* `base/`
* `components/`
* `layout/`
* `pages/`
* `themes/`
* `abstracts/`
* `vendors/`
* `main.scss`


**Example file architecture**

```scss
sass/
|
|– abstracts/
|   |– _variables.scss    # Sass Variables
|   |– _functions.scss    # Sass Functions
|   |– _mixins.scss       # Sass Mixins
|   |– _placeholders.scss # Sass Placeholders
|
|– base/
|   |– _reset.scss        # Reset/normalize
|   |– _typography.scss   # Typography rules
|   …                     # Etc.
|
|– components/
|   |– _buttons.scss      # Buttons
|   |– _carousel.scss     # Carousel
|   |– _cover.scss        # Cover
|   |– _dropdown.scss     # Dropdown
|   …                     # Etc.
|
|– layout/
|   |– _navigation.scss   # Navigation
|   |– _grid.scss         # Grid system
|   |– _header.scss       # Header
|   |– _footer.scss       # Footer
|   |– _sidebar.scss      # Sidebar
|   |– _forms.scss        # Forms
|   …                     # Etc.
|
|– pages/
|   |– _home.scss         # Home specific styles
|   |– _contact.scss      # Contact specific styles
|   …                     # Etc.
|
|– themes/
|   |– _theme.scss        # Default theme
|   |– _admin.scss        # Admin theme
|   …                     # Etc.
|
|– vendors/
|   |– _bootstrap.scss    # Bootstrap
|   |– _jquery-ui.scss    # jQuery UI
|   …                     # Etc.
|
`– main.scss              # Main Sass file
```

### Base folder

The `base/` folder holds what we might call the boilerplate code for the project. 

### Components folder

For small components, there is the `components/` folder. While `layout/` is macro (defining the global wireframe), `components/` is more focused on widgets. It contains all kind of specific modules like a slider, a loader, a widget, and basically anything along those lines. 

### Layout folder

The `layout/` folder contains everything that takes part in laying out the site or application. This folder could have stylesheets for the main parts of the site (header, footer, navigation, sidebar…), the grid system or even CSS styles for all the forms.

### Pages folder

If you have page-specific styles, it is better to put them in a `pages/` folder, in a file named after the page. For instance, it’s not uncommon to have very specific styles for the home page hence the need for a `_home.scss` file in `pages/`.

### Themes folder

The themes folder holds files that create project specific themes ie `admin` and `default`.

### Vendors folder

CSS files from external libraries and frameworks live here.

If you have to override a section of any vendor, create an 8th folder called `vendors-extensions/` in which you may have files named exactly after the vendors they overwrite. For instance, `vendors-extensions/_bootstrap.scss` is a file containing all CSS rules intended to re-declare some of Bootstrap’s default CSS. This is to avoid editing the vendor files themselves, which is generally not a good idea.

### Abstracts folder

The `abstracts/` folder gathers all Sass tools and helpers used across the project. Every global variable, function, mixin and placeholder should be put in here.

The rule of thumb for this folder is that it should not output a single line of CSS when compiled on its own. These are nothing but Sass helpers.

### Main file

Files should be imported according to the folder they live in, one after the other in the following order:

1. `abstracts/`
1. `vendors/`
1. `base/`
1. `layout/`
1. `components/`
1. `pages/`
1. `themes/`

In order to preserve readability, the main file should respect these guidelines:

* one file per `@import`;
* one `@import` per line;
* no new line between two imports from the same folder;
* a new line after the last import from a folder;
* file extensions and leading underscores omitted.

```scss
@import 'abstracts/variables';
@import 'abstracts/functions';
@import 'abstracts/mixins';
@import 'abstracts/placeholders';

@import 'vendors/bootstrap';
@import 'vendors/jquery-ui';

@import 'base/reset';
@import 'base/typography';

@import 'layout/navigation';
@import 'layout/grid';
@import 'layout/header';
@import 'layout/footer';
@import 'layout/sidebar';
@import 'layout/forms';

@import 'components/buttons';
@import 'components/carousel';
@import 'components/cover';
@import 'components/dropdown';

@import 'pages/home';
@import 'pages/contact';

@import 'themes/theme';
@import 'themes/admin';
```

**[⬆ back to top](#table-of-contents)**
