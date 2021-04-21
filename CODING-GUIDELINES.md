<h1 align="center">Coding Guidelines</h1>

# General Principles

> ✅ Use Classes in SCSS for styling elements.

### Stylelint Rule
```json
"selector-max-id": 0
```

### Example

```scss
.component {
  ...
}
```

> ❌ Don't use ID's for styling.

```scss
#component {
  ...
}
```

> ✅ Style the base elements (such as typography elements)


```scss
h1 {
  ...
}
```

> ❌ Reference or style descendent elements in your class selectors

```scss
.component h1 {
  ...
}
```

# Performance

Overly specific selectors can cause performance issues, it requires a lot of DOM walking and for large documents can cause a significant increase in the layout time.

> ❌ Don't

```scss
ul.user-list li span a:hover {
  ...
}
```

> ✅ Do

```scss
.user-list-link:hover {
  ...
}
```

# Formating & Indentation

Remove all trailing white-space for your files
```json
"no-eol-whitespace": true
```

Don't mix spaces with tabs for indentation
```json
"indentation": 2
```


# Commenting

- Separate your code into logical section using standard comment blocks.
- Leave one clear line under your section comments.

> ✅ Do

```scss
// =============================================================================
// FILE TITLE / SECTION TITLE
// =============================================================================


// Comment Block / Sub-section
// -----------------------------------------------------------------------------
//
// Purpose: This will describe when this component should be used. This comment
// block is 80 chars long
//
// 1. Mark lines of code with numbers which are explained here.
// This keeps your code clean, while also allowing detailed comments.
//
// -----------------------------------------------------------------------------

.component {
    ... // 1
}
```

# Spacing

CSS rules should be comma separated but live on new lines
```json
"selector-list-comma-newline-after": "always"
```
Include a single space before the opening brace of a rule-set
```json
"block-closing-brace-space-before": "always"
```
- Include a single space after the colon of a declaration.
- include a semi-colon at the end of every declaration in a declaration block
- include a space after each comma in comma-separated property or function values.
- CSS Blocks should be spearated by a single clear line

# Quotes

> ✅ Always use double quotes, quote attribute values in selectors

```scss
input[type="checkbox"] {
  background-image: url("/img/you.jpg");
  font-family: "Helvetica Neue Light", "Helvetica Neue", Helvetica, Arial;
}
```

> ❌ Don't

```scss
input[type="checkbox"] {
  background-image: url(/img/you.jpg);
  font-family: Helvetica Neue Light, Helvetica Neue, Helvetica, Arial;
}
```

# When Declaring Values

- Use lower-case and shorthand hex values
- use unit-less line-height values
- Where allowed, avoid specifying units of zero values
- Never use `!important`
- Set properties explicitly

  - `background-color: #333` over `background: #333`
  - `margin-top: 10px` over `margin: 10px 0 0`

> ✅ Do

```scss
.component {
  background-color: #ccc;
  color: #aaa;
  left: 0;
  line-height: 1.25;
  min-height: 400px;
  padding: 0 20px;
  top: 0;
}
```

> ❌ Don't

```scss
.component {
  background: #ccc;
  color: #aaaaaa;
  left: 0px;
  line-height: 24px;
  height: 400px !important; //jerk #yolo FUUUUUU
  padding: 0px 20px 0px 20px;
  top: 0px;
}
```

# Declaration order

> The goal is to understand the essence of the styles by reading few declarations. Most of the time, the essence is how the element is laid out and its size is determined. A proper ordering of rules allows to scan the declaration block for properties quickly, and this is the order that should be followed:

```scss
.declarationOrder {
  /* Declarations */
  $varName: #ccc;

  /* Sass Inheritance */
  @extend %a-placeholder;
  @include silly-links;

  // Content
  content: "";

  // Positioning
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  z-index: 10;

  // Box Model
  display: block;
  float: right;
  width: 100rem;
  height: 100rem;
  padding: 10rem;
  margin: 10rem;

  // Typography
  color: $varName;
  font: normal 1rem "Helvetica", sans-serif;
  line-height: 1.3;
  text-align: center;

  // Visual
  background-color: $varName;
  border-radius: 4px;
  opacity: 1;

  // Animation
  transition: all 1s;

  // Misc
  user-select: none;
}
```

> ✅ Do

```scss
.component {
  // Sass Inheritance
  @extend %a-placeholder;
  @include silly-links;

  // Position and Layout
  top: 0;
  left: 0;

  // Box Model
  width: 150px;
  min-height: 400px;
  padding: 0 20px;

  // Typography
  line-height: 1.25;
  color: #aaa;
}
```

> ❌ Don't

```scss
.component {
  top: 0;
  padding: 0 20px;
  @include silly-links;
  left: 0;
  @extend %a-placeholder;
  min-height: 400px;
  line-height: 1.25;
  width: 150px;
  color: #aaa;
}
```

# Pseudo Elements and Classes

Pseudo Elements and classes are very different things, as is the syntax used to declare them:

> ✅ Declare pseudo **classes** with a single colon

```scss
.component:focus {
    ...
}

.component:hover {
    ...
}
```

> ✅ Declare pseudo **elements** with a a double colon

```scss
.component::before {
    ...
}

.component::after {
    ...
}
```

> ❌ Don't

```scss
.component:after {
    ...
}
```

# Units

> ✅ Do

- Use `rem` units as primary unit type, This includes:
  - Positioning: `top`, `right`, `bottom`, `left`
  - Dimensions: `width`, `height`, `margin`, `padding`
  - Font Size
- Use `px` units as primary unit type for the following properties
  - Border widths: `border: 1px solid #bada55;`
- Line-height should be kept unti-less. If you find you are using a line-height with a set unit type, try to thing of alternative ways to achieve the same outcome. If it's a unique case which requires a specific `px` or `rem` unit, outline the reasoning with comments so that others are aware of its purpose.

> ❌ Don't

- Avoid all use of magic numbers. Rethink the problem (`margin-top: 37px`)

# Nesting

Nesting is handy, sometimes, but will conflict with our **Specifity** and **Performance** guidelines.

As we follow conventions and thoughts from widely accepted methodologie such as BEM, the use of the suffix can help immensely though.

- Just because you can, doesn't mean you should.
- Watch you output, be mindful of Specifity and Performance described in this document.

> ✅ Aim for maximum depth of just 1 nested rule

```scss
.panel-body {
  position: relative;
}

.panel-sideBar {
  z-index: 10;
}

.panel-sideBar-item {
  cursor: pointer;
}

.panel-sideBar-item-label {
  color: #aeaeae;

  &.has-smallFont {
    font-size: 1rem;
  }
}
```

At its worst, this produces:

```scss
.panel-sideBar-item-label.has-smallFont {
  font-size: 1rem;
}
```

> ❌ Don't

```scss
.bc-tab-panel {
  .panel-body {
    position: relative;

    .panel-side-bar {
      z-index: 10;

      .panel-side-item {
        cursor: pointer;

        .panel-side-item-label {
          color: #aeaeae;

          &.small-font {
            font-size: 1rem;
          }
        }
      }
    }
  }
}
```

At its worst, this produces:

```scss
.bc-tab-panel
  .panel-body
  .panel-side-bar
  .panel-side-item
  .panel-side-item-label.small-font {
  font-size: 13px;
}
```

# @extends or @include

- Excessive use of `@include` can cause unecessary bloat to your stylesheet, but gzip should help with that
- Excessive use of `@extend` can create a large selector blocks (not helpful in web inspector) and hoisting of your selector can cause override and inheritance issues.

> ✅ We advise to `@include` over `@extend` generally, but use common sense. In situations where it's better to `@extend` it's safer to do so on a placeholder selector

> ✅ Make use of placeholder selectors to separate repeated local styles

```scss
%placeholderSelector {
  background-color: #eee;
}

.component1 {
  @extend %placeholderSelector;
  color: red;
}

.component2 {
  @extend %placeholderSelector;
  color: blue;
}
```

# Components

Syntax: `<componentName>[--modifierName|-descendantName]`

This component syntax is mainly taken from [Suit CSS](http://suitcss.github.io/) with minor modifications.

Component Driven development offers several benefits when reading and writing HTML and CSS:

- It helps to distinguish between the classes for the root of the component, descendant elements, and modifications.
- It keeps the specificity of selectors low.
- It helps to decouple presentation semantics from document semantics.

You can thing of components as custom elements that enclose specific semantics, styling, and behaviour.

> ❌ Do not choose a class name base on its visual presentation or its content

> ✅ The Primary achitectural division is between components and utilities:

- componentName (eg. `.dropdown` or `.buttonGroup`)
- componentName--modifierName (eg. `.dropdwon--dropUp` or `.button--primary`)
- componentName-descendantName (eg. `.dropdown-item`)
- componentName.is-stateOfComponent (eg. `dropdown.is-active`)
- u-utilityName (eg. `u-textTruncate`)

## ComponentName

The component's name must be written in camel case. Use class names as short as possible but as long as necessary.

- Example `.nav` not `.navigation`
- Example `.button` not `.btn`

```scss
.myComponent {
  /*...*/
}
```

```html
<article class="myComponent">...</article>
```

## componentName--modifierName

A component modifier is a class that modifies the presentation of the base component in some form. Modifier names must be written in camel case and be separated from the component name by two hyphens. The class should be included in the HTML in addition to the base component class.

```scss
.button {
  ...
}

.button--primary {
  ...
}
```

```html
<button class="button button--primary">...</button>
```

## componentName-descendantName

A component descendant is a class this is attached to a descendant node of a component. It's reponsible for applying presentation directly to the descendant on behalf of a particular component. Descendant names must be written in camel case.

```html
<article class="tweet">
  <header class="tweet-header">
    <img class="tweet-avatar" src="{$src}" alt="{$alt}" />
    ...
  </header>

  <div class="tweet-body">...</div>
</article>
```

You might notice that `tweet-avatar`, despite being a descendant of `tweet-header` does not have the class of `tweet-header-avatar`. WHY? because it doesn't necessarily **have** to live there. It could be adjacent to `tweet-header` and function the same way. Therefore, you should only prepend a descendant with its parent if must live there. Strive to keep class names as short as possible, but as long as necessary.

When building a component, you'll often run into the situation where you have a list, group or sipmly require a container for some descendants. In this case, it's much better to follow a pattern of pluralising the container and having each descendant be singular. This keeps the relationship clear between descendant levels.

> ✅ Do

```html
<nav class="pagination">
  <ul class="pagination-list">
    <li class="pagination-listItem">...</li>
  </ul>
</nav>
```

```html
<ul class="breadcrumbs">
  <li class="breadcrumb">
    <a class="breadcrumb-label" href="#"></a>
  </li>
</ul>
```

> ❌ Avoid verbose descendant names

```html
<nav class="pagination">
  <ul class="pagination-pages">
    <li class="pagination-pages-page">...</li>
  </ul>
</nav>
```

```html
<ul class="breadcrumbs">
  <li class="breadcrumbs-breadcrumb">
    <a class="breadcrumbs-breadcrumb-label" href="#"></a>
  </li>
</ul>
```

## componentName.is-stateOfComponent

Use `is-stateName` for state-based modifications of components. The state name must be Camel case. Never style these classes directly; they should always be used as an adjoining class.

`JS` or any backend language can add/remove these classes. This means that the same state names can be used in multiple contexts, but every component must define its own styles for the state (as they are scoped to the component).

```html
<article class="tweet is-expanded">...</article>
```

```scss
.tweet {
    ...
}

.tweet.is-expanded {
    ...
}
```

# Utilities

Utility classes are low-level structural and positional traits. Utilities can be applied directly to any element; multiple utilities can be used together; and utilities can be used alngside component classes.

Utility classes should be useful sparingly, lean towards component level styling to make for as reusable HTML patterns as possible.

## u-utilityName

Syntax: `u-<utilityName>`
Utilties must use a camel case name, prefixed with a `u` namespace.

# Variables and Mixins

Variables and Mixins should follow similar naming conventions.

## Variables

Syntax: `[<componentName>[--modifierName][-descendantName]-]<propertyName>-<variableName>[--<modifierName>]`

Variables should be named as such, things that can change over time.

Variables should also follow our component naming convention to show context and be in camelCase. If the variable is a global, generic variable, the property name should be prefixed first, followed by the variant and or modifier name for clearer understanding of use.

> ✅ Abstract your variable names

```scss
$color-brandPrimary: #aaa;
$fontSize: 1rem;
$fontSize--large: 2rem;
$lineHeight-small: 1.2;
```

❌ Name you variables after the color value

```scss
$zirotoheroBlue: #00abc9;
$color-blue: #00ffee;
$color-lightBlue: #eeff00;
```

## Component / Micro App level variables

Micro apps must base their local variables on the global variables primarily. You may add your own specific variables as required if no global variable is available.

For portability, your component should declare it's own set of variables inside it's own settings partial, inside the settings folder.

If your variable is scoped to your component, it should be namespaced as such following component naming conventions.

> ✅ Do

```css
$componentName-fontSize:                                fontSize("small");
$componentName-decendantName-backgroundColor:           #ccc;
$componentName-decendantName-marginBottom:              fontSize("large");
$componentName-decendantName--active-backgroundColor:   #000;
```

```css
.componentName {
    font-size: $componentName-fontSize;
}

.componentName-decendantName {
    background-color: $componentName-decendantName-backgroundColor;
    margin-bottom: $componentName-decendantName-marginBottom;
}

.componentName-decendantName--active {
    background-color: $componentName-decendantName--active-backgroundColor;
}
```

## Maps

Variable maps with a simple getter mixin, can help simplify your variable names when calling them, and help better group variables together using their relationship.

> ✅ Do

```scss
// Setting variables and mixin
// -----------------------------------------------------------------------------

$colors: (
    primary: (
        base: #00abc9,
        light: #daf1f6,
        dark: #12799a
    ),
    secondary: (
        base: #424d55,
        light: #ccc,
        lightest: #efefef,
        dark: #404247
    ),
    success: (
        base: #bbd33e,
        light: #eaf0c6
    )
);

@function color($color, $tone: "base") {
    @return map-get(map-get($colors, $color), $tone);
}
```


```scss
// Usage
// -----------------------------------------------------------------------------

body {
    color: color("secondary");
}

h1,
h2,
h3 {
    color: color("secondary", "dark");
}

.alert {
    background-color: color("primary", "light");
}

.alert-close {
    color: color("primary");
}

.alert--success {
    background-color: color("success", "light");

    > .alert-close {
        color: color("success");
    }
}
```

**Every variable used in the core architecture must be based off the global
variables.**

## Colors

Use the globally available colors.
A component shouldn't really have a need for a *new* color.
This creates consistency and sanity.

Avoid using the `darken(color, %)` and `lighten(color, %)` mixins for similar reasons.

Use the color maps available to you:
```css
.component {
    background-color: color("brand", "primary");
}
```

## z-index scale

Use the z-index scale under global settings.

`zIndex("lowest")` or `zIndex("high")` for example.


## Font Weight

Never declare a new font weight,
only use the available font settings. e.g.

```css
fontWeight("light");
fontWeight("semibold");
```

## Line Height

We provides a line height scale. This should be used for blocks of text. e.g.

```css
lineHeight("smallest");
lineHeight("large");
```

Alternatively, when using line height to vertically center a single line of text, be sure to set the line height to the height of the container - 1.

```CSS
.button {
  height: remCalc(50px);
  line-height: remCalc(49px);
}
```

## Animations

Animation delays, durations and easing should be taken from the global framework

## Mixins

Mixins follow regular camel case naming conventions and do not require namespacing. If you are creating a mixin for a utility, it will need to match the utility name (including `u` namespacing).

* `@mixin buttonVariant;`
* `@mixin u-textTruncate;`
