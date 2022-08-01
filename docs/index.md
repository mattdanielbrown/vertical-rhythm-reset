# vertical-rhythm-reset

[![NPM](https://img.shields.io/npm/v/vertical-rhythm-reset.svg?style=flat-square)](https://www.npmjs.com/package/vertical-rhythm-reset)
[![GitHub Workflow Status (master)](https://img.shields.io/github/workflow/status/jhildenbiddle/vertical-rhythm-reset/Build/master?label=checks&style=flat-square)](https://github.com/jhildenbiddle/vertical-rhythm-reset/actions?query=branch%3Amaster+)
[![Codacy grade](https://img.shields.io/codacy/grade/01917626fcc14886ac621c1928a2961f?style=flat-square)](https://app.codacy.com/gh/jhildenbiddle/vertical-rhythm-reset/dashboard)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=flat-square)](https://github.com/jhildenbiddle/vertical-rhythm-reset/blob/master/LICENSE)
[![Tweet](https://img.shields.io/twitter/url/http/shields.io.svg?style=social)](https://twitter.com/intent/tweet?url=https%3A%2F%2Fgithub.com%2Fjhildenbiddle%2Fvertical-rhythm-reset&hashtags=css,sass,scss,frontend)
<a class="github-button" href="https://github.com/jhildenbiddle/vertical-rhythm-reset" data-icon="octicon-star" data-show-count="true" aria-label="Star jhildenbiddle/vertical-rhythm-reset on GitHub">Star</a>

A Sass/SCSS library for responsive vertical rhythm grids, modular scale typography, and CSS normalization.

?> **New!** Version 2.x now supports Dart Sass. Those migrating from version 1.x should review the [Migration](#migration) section for details.

## Demo

<!-- Codepen Demo -->
<!-- cspell:disable-next-line -->
<iframe height="450" style="width: 100%;" scrolling="no" title="Demo: Vertical Rhythm Reset (CSS/SCSS)" src="https://codepen.io/jhildenbiddle/embed/preview/wGjZLj?default-tab=result&editable=true&theme-id=light" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href="https://codepen.io/jhildenbiddle/pen/wGjZLj">
  Demo: Vertical Rhythm Reset (CSS/SCSS)</a> by John Hildenbiddle (<a href="https://codepen.io/jhildenbiddle">@jhildenbiddle</a>)
  on <a href="https://codepen.io">CodePen</a>.
</iframe>

## Features

- **Simplified vertical rhythm grids**<br>
  Maintain visual symmetry by aligning elements to an invisible-yet-recognizable layout pattern.

- **Modular scale typography**<br>
  Bring harmony to your typography using a calculated range of proportional font sizes.

- **CSS reset & normalization**<br>
  Standardize the default presentation of HTML5 elements across desktop and mobile browsers.

- **Responsive layout support**<br>
  Define custom breakpoints, each with their own vertical rhythm and typography settings.

- **Customizable utility classes**<br>
  Create pixel-perfect layouts in less time and without the need for custom classes.

- **Fast-and-easy implementation**<br>
  As little as two lines of code generates the CSS foundation for you project.

**Browser Support**

- Chrome 19+
- Edge
- Firefox 4+
- Internet Explorer 9+
- Safari 6+

**Sass Support**

- Dart Sass

## Installation

[**NPM**](https://www.npmjs.com/package/vertical-rhythm-reset)

```shell
npm install vertical-rhythm-reset
```

**CDN**

Available on [jsdelivr](https://www.jsdelivr.com/package/npm/vertical-rhythm-reset) (below), [unpkg](https://unpkg.com/browse/vertical-rhythm-reset/), and other CDN services that auto-publish npm packages.

```text
https://cdn.jsdelivr.net/npm/vertical-rhythm-reset@2
```

!> Note the `@` version lock in the URL above. This prevents breaking changes in future releases from affecting your project and is therefore the safest method of loading dependencies from a CDN. When a new major version is released, you will need to manually update your CDN URLs by changing the version after the `@` symbol.

**Git**

```shell
git clone https://github.com/jhildenbiddle/vertical-rhythm-reset.git
```

[Download](https://github.com/jhildenbiddle/vertical-rhythm-reset/archive/master.zip) the latest source code in zip format.

## Usage

1. Import Vertical Rhythm Reset:

   ```scss
   @use "vertical-rhythm-reset" as vr;
   ```

1. Call the [`reset()`](#reset) mixin at the top of your main SCSS file to generate the default CSS rules:

   ```scss
   @include vr.reset();
   ```

1. Use the [`set()`](#set) mixin to declare vertical rhythm and modular type scale styles:

   ```scss
   .myclass {
     @include vr.set(
       $font-size: 2,
       $height   : 3,
       $margin   : 1,
       $padding  : 1
     );
   }
   ```

1. Use [utility classes](#utility-classes) to apply vertical rhythm and modular type scale styles without requiring custom CSS:

   ```html
   <!-- Set the font-size to a modular type scale of 2 -->
   <p class="vr-font-size-2">Hello, World!</p>

   <!-- Set height and width to three vertical rhythm rows -->
   <div class="vr-height-3 vr-width-3" style="background: red;"></div>
   ```

1. Call the [`grid()`](#grid) mixin under any element to view the vertical rhythm grid overlay.

   ```scss
   body {
     @include vr.grid();
   }
   ```

## Customization

The default settings provide a sensible starting point for new projects:

- CSS reset and normalization of all HTML5 elements
- A base font-size of `14px`
- A base line-height of `1.5`
- Two breakpoints configured for responsive typography and vertical rhythm grids:
  1. At 60em (960px):
     - Font size is increased to `16px`
  2. At 90em (1440px):
     - Font size increases to `18px`

There are many configuration options available that allow you to customize the Vertical Rhythm Reset as you see fit. The sections below provide an overview of how to configure settings. For complete details on variable and mixin settings, please review the [SassDoc documentation](http://jhildenbiddle.github.io/vertical-rhythm-reset/sassdoc/).

### Vertical Rhythm Grid

A vertical rhythm grid provides symmetry to your project by aligning elements to an invisible-yet-recognizable visual layout pattern.

The height of a grid row is calculated by multiplying the font-size by the line-height. The result is then converted to a `rem`-based value and applied to all elements using a `*` selector rule.

To configure the base vertical rhythm grid, set the `$font-size` and `$line-height` global variables before calling the [`reset()`](#reset) mixin.

```scss
// Configure using global variables
vr.$font-size  : 14px; // Default
vr.$line-height: 1.5;  // Default

@include vr.grid();
```

```scss
// Configure using mixin arguments
@include vr.grid(
  $font-size  : 14px, // Default
  $line-height: 1.5   // Default
);
```

Once the vertical rhythm grid has been established you may use the [`set()`](#set) mixin and [utility classes](#utility-classes) to align items to the grid by setting dimension values to grid row multiples.

```scss
.myclass {
  @include vr.set(
    $height   : 2,
    $margin   : 1,
    $padding  : 1
  );
}
```

```html
<!-- Height set to one vertical rhythm row (default) -->
<p>Hello, World!</p>

<!-- Height set to two vertical rhythm rows using set() mixin -->
<p class="myclass">Hello, World!</p>

<!-- Height set to two vertical rhythm rows using a utility class -->
<p class="vr-height-2">Hello, World!</p>
```

### Modular Scale Typography

Modular scale typography provides a harmonious range of proportional font sizes. This calculated range of font sizes also helps answer the question, "What font-sizes should I use for this project?" and allows changing these sizes project-wide by modifying a single global variable.

The `$modular-scale-map` global variable contains a list of modular type scale names and their ratios. As the ratio increases, so does the size difference between each font size.

```scss
// List of modular scale names and values
vr.$modular-scale-map: (
    minor-second    : 1.067, // Ratio = 15:16
    major-second    : 1.125, // Ratio = 8:9
    minor-third     : 1.2,   // Ratio = 5:6
    major-third     : 1.25,  // Ratio = 4:5
    perfect-fourth  : 1.333, // Ratio = 3:4
    augmented-fourth: 1.414, // Ratio = 1:√2
    perfect-fifth   : 1.5,   // Ratio = 2:3
    minor-sixth     : 1.6,   // Ratio = 5:8
    golden          : 1.618, // Ratio = 1:1.618
    major-sixth     : 1.667, // Ratio = 3:5
    minor-seventh   : 1.778, // Ratio = 9:16
    major-seventh   : 1.875, // Ratio = 8:15
    octave          : 2      // Ratio = 1:2
);
```

Set the `$modular-scale` global variable to one of these named ratios to generate module scale typography styles and helper classes:

```scss
// Set the desired modular scale by name or numeric value
vr.$modular-scale: minor-third; // Default
```

Use the [`set()`](#set) mixin and [utility classes](#utility-classes) to set the font-size of elements to a modular type scale. The mixin will calculate the number of vertical rhythm rows a given font size should occupy.

```scss
.myclass {
  @include vr.set($font-size: 2);
}
```

```html
<!-- Set font size using the set() mixin -->
<p class="myclass">Hello, World!</p>

<!-- Set the font size using a utility class -->
<p class="vr-font-size-2">Hello, World!</p>
```

### Responsive Layouts

The `$breakpoints` global variable is a map that contains breakpoint settings used to generate media queries and recalculate values for responsive layouts.

**Configuration:**

- Copy one of the example maps below as your starting point
- Modify the map keys and values as needed (see the [SassDoc documentation](http://jhildenbiddle.github.io/vertical-rhythm-reset/sassdoc/) for details)
  - The top-level key is the `min-width` media query value
  - The nested properties and values specify the settings to use for a given breakpoint
  - Only settings that change between breakpoints need to be specified
  - Any settings not for a breakpoint will inherit the value from the previous breakpoint
- Set the value to `false` to disable responsive typography and vertical rhythm grids

**Tips**

1. Font-size and line-height values can have a significant impact on the generated CSS output. To keep the CSS output as lightweight as possible, maintain a consistent line-height across breakpoints and use font-size values that equal whole numbers when multiplied by the line-height. This will allow the `rem`-based values generated for the root breakpoint to work across all breakpoints which removes the need to generate recalculated values for every media query.
2. Use the [`grid()`](#grid) mixin to visualize the vertical rhythm grid settings. For a stronger breakpoint change indicator, consider specifying unique `grid-color` for each breakpoint.

```scss
// Default settings
vr.$breakpoints: (
    60em: ( // 960px
        font-size: 16px
    ),
    90em: ( // 1440px
        font-size: 18px
    )
);
```

```scss
// Custom settings
vr.$breakpoints: (
    60em: ( // 960px
        font-size    : 16px,
        line-height  : 1.4,
        modular-scale: major-third,
        grid-color   : purple
    ),
    90em: ( // 1440px
        font-size    : 18px,
        line-height  : 1.3,
        modular-scale: perfect-fourth,
        grid-color   : blue
    )
);
```

## Mixins

### reset()

Generates all necessary CSS styles for vertical rhythm grid, modular scale typography, responsive breakpoints, and CSS reset/normalization.

This mixin can be called with arguments or without. When called without arguments, global variable values will be used. When called with arguments, global variable values will be used for omitted arguments.

💡 See [SassDoc documentation](http://jhildenbiddle.github.io/vertical-rhythm-reset/sassdoc/) for additional details.

```scss
// Global variables
vr.$box-sizing   : border-box;
vr.$font-size    : 14px;
vr.$line-height  : 1.5;
vr.$modular-scale: minor-third;
vr.$grid-color   : rgb(233, 30, 99);
vr.$breakpoints  : (...);
vr.$helpers      : (...);

// Call the mixin at root
@include vr.reset();
```

```scss
 // Call the mixin at root with arguments
 // Global variables will be updated with values provided
 // Omitted values will use defaults
 @include vr.reset(
   $box-sizing   : border-box,
   $font-size    : 14px,
   $line-height  : 1.5,
   $modular-scale: minor-third,
   $grid-color   : rgb(233, 30, 99),
   $breakpoints  : (...),
   $helpers      : (...)
 );
```

### grid()

Renders the vertical rhythm grid as a background image and applies a highlight color as a semi-transparent background to all child elements. This is useful for debugging and visualizing the vertical rhythm grid.

💡 See [SassDoc documentation](http://jhildenbiddle.github.io/vertical-rhythm-reset/sassdoc/) for additional details.

```scss
// Global variables
vr.$grid-color: rgb(233, 30, 99);

// Call the grid() mixin with defaults
body {
  @include vr.grid();
}
```

```scss
// Call the grid() mixin with arguments
body {
  @include vr.grid(
    $color: rgb(233, 30, 99),
    $lines: true,
    $highlight: true,
    $detail: true
  );
}
```

### set()

Generates CSS declarations for vertical rhythm grid alignment and modular scale typography. Use this mixin to specify CSS properties and values to ensure elements align to the vertical rhythm grid.

💡 See [SassDoc documentation](http://jhildenbiddle.github.io/vertical-rhythm-reset/sassdoc/) for additional details.

| Argument Name     | Description                              | Type                       | Default |
| ----------------- | ---------------------------------------- | -------------------------- | ------- |
| `$font‑size`      | Modular scale font size (number) or custom font size (px\|rem\|%) | Length(px\|rem\|%), Number | `null`  |
| `$line-height`    | Line height                              | Number                     | `null`  |
| `$height`         | Vertical rhythm row height (number) or fixed height (px) | Length(px), Number | `null`  |
| `$width`          | Width                                    | Number                     | `null`  |
| `$margin`         | Margin ([shorthand](https://developer.mozilla.org/en-US/docs/Web/CSS/margin)) | Length\|List\|Number | `null`  |
| `$margin‑top`     | Margin top                               | Length\|Number             | `null`  |
| `$margin‑bottom`  | Margin bottom                            | Length\|Number             | `null`  |
| `$margin‑right`   | Margin right                             | Length\|Number             | `null`  |
| `$margin‑left`    | Margin left                              | Length\|Number             | `null`  |
| `$padding`        | Padding ([shorthand](https://developer.mozilla.org/en-US/docs/Web/CSS/padding)) | Length\|List\|Number | `null`  |
| `$padding‑top`    | Padding top                              | Length\|Number             | `null`  |
| `$padding‑bottom` | Padding bottom                           | Length\|Number             | `null`  |
| `$padding‑right`  | Padding right                            | Length\|Number             | `null`  |
| `$padding‑left`   | Padding left                             | Length\|Number             | `null`  |
| `$offset`         | Border offset (top\|top  bottom)         | Length(px)\|List\|Number   | `null`  |
| `$offset‑top`     | Border offset top                        | Length(px)\|Number         | `null`  |
| `$offset‑bottom`  | Border offset bottom                     | Length(px)\|Number         | `null`  |

- **font-size**: Setting the font-size with this mixin provides calculated modular type scale sizes and the necessary line height for vertical rhythm alignment. *Unit-less* values represent `rem`-based modular type scale multiples (0, 1, 2, etc). *Unit* values (18px, 80%, etc.) will be converted to `rem` units.
- **height**: Setting the height with this mixin allows specifying values as a multiple of vertical rhythm grid rows and for calculating the top/bottom margins required for fixed-height (px) elements. *Unit-less* values will be converted to a `rem`-based height equivalent of vertical rhythm rows. *Unit* values (px) will be applied unchanged with margin values calculated to ensure the fixed-height element aligns to the vertical rhythm grid.
- **margin and padding**: Setting margins and padding with this mixin allows specifying values as a multiple of vertical rhythm grid rows. *Unit-less* values will be converted to a `rem`-based height equivalent of vertical rhythm rows. *Unit* values (px) will be applied unchanged. The `$margin` and `$padding` arguments both accept [CSS shorthand](https://developer.mozilla.org/en-US/docs/Web/CSS/margin) notation for convenience.
- **offset**: Setting the border offset with this mixin allows elements with borders to align to the vertical rhythm grid. *Unit-less* values will be converted to `px`-based values. *Unit* values (px) will be applied unchanged. The `$offset` argument accepts a single value as the top/bottom values or two values as separate top and bottom values.

```scss
.myclass {
  @include vr.set(
    // Set font size to a modular type scale of 3
    $font-size: 3,
    // Set height to 3 vertical rhythm grid rows
    $height: 3,
    // Set the top/bottom margin to 1 vertical rhythm grid row and left/right to 0
    $margin: 1 0,
    // Set the border offset values to match the top/bottom border
    $offset-top: 3px,
    $offset-bottom: 2px
  );

  border-top: 3px solid red;
  border-bottom: 2px solid blue;
}
```

## Utility Classes

The `$helpers` global variable is a map that contains settings used to generate vertical rhythm utility classes. These CSS classes provide a convenient way to set vertical rhythm and typography values directly on HTML elements without using the [`set()`](#set) mixin.

```html
<!-- Font size (showing range 1 through 5) -->
<div class="vr-font-size-1">...</div>
<div class="vr-font-size-2">...</div>
<div class="vr-font-size-3">...</div>
<div class="vr-font-size-4">...</div>
<div class="vr-font-size-5">...</div>

<!-- Other utility classes (showing range 1 of n) -->
<div class="vr-line-height-1">...</div>
<div class="vr-height-1">...</div>
<div class="vr-width-1">...</div>
<div class="vr-margin-1">...</div>
<div class="vr-margin-top-1">...</div>
<div class="vr-margin-bottom-1">...</div>
<div class="vr-padding-1">...</div>
<div class="vr-padding-top-1">...</div>
<div class="vr-padding-bottom-1">...</div>
<div class="vr-offset-1">...</div>
<div class="vr-offset-top-1">...</div>
<div class="vr-offset-bottom-1">...</div>
```

**Configuration**

The utility classes generated by the [`reset()`](#reset) can be customized using the `$helpers` global variable.

- Copy the map object below to use as your starting point.
- Modify the map keys and values as needed (see the [SassDoc documentation](http://jhildenbiddle.github.io/vertical-rhythm-reset/sassdoc/) for details).
  - The top-level key is the property which CSS classes will be generated for
  - `count` is the number of variations to generate
  - `prefix` is the portion of the generated class name that will precede the numeric value
  - `suffix` is the portion of the generated class name that will proceed the numeric value

💡 See [SassDoc documentation](http://jhildenbiddle.github.io/vertical-rhythm-reset/sassdoc/) for additional details.

**Tips**

1. If you don't intent to use these helper classes and rules, set the `$helpers` value to `false`. This will prevent helper classes and rules from being generated which will reduce the size of [`reset()`](#reset) mixin output.
2. Offset classes work by adjusting the top position and the bottom margin. This means that applying both a bottom offset and margin class to the same element can result in a conflict. To avoid this conflict, consider using one of the following approaches for applying a bottom offset and bottom margin to the same element:
   - Use the [`set()`](#set) mixin instead of helper classes when both a `margin` and `offset` is needed. The [`set()`](#set) mixin accounts for this scenario and adjust the generated CSS output accordingly.
   - Wrap the element in a parent tag, then apply the offset class to the main element and the margin class(es) to the parent element.

```scss
// Defaults
vr.$helpers: (
  font-size: (
    count : 5,
    prefix: "vr-font-size-"
  ),
  line-height: (
    count : 10,
    prefix: "vr-line-height-"
  ),
  height: (
    count : 10,
    prefix: "vr-height-"
  ),
  width: (
    count : 10,
    prefix: "vr-width-"
  ),
  margin: (
    count : 5,
    prefix: "vr-margin-"
  ),
  margin-top: (
    count : 5,
    prefix: "vr-margin-top-"
  ),
  margin-bottom: (
    count : 5,
    prefix: "vr-margin-bottom-"
  ),
  padding: (
    count : 5,
    prefix: "vr-padding-"
  ),
  padding-top: (
    count : 5,
    prefix: "vr-padding-top-"
  ),
  padding-bottom: (
    count : 5,
    prefix: "vr-padding-bottom-"
  ),
  offset: (
    count : 5,
    prefix: "vr-offset-"
  ),
  offset-top: (
    count : 5,
    prefix: "vr-offset-top-"
  ),
  offset-bottom: (
    count : 5,
    prefix: "vr-offset-bottom-"
  )
);
```

## Migration

**From version 1.x**

When version 1.x of Vertical Rhythm Reset was released, it offered compatibility with the two most popular Sass implementations at that time: [Ruby Sass](https://sass-lang.com/ruby-sass) and [LibSass](https://sass-lang.com/libsass). These Sass libraries have since been deprecated as of [2019](https://sass-lang.com/blog/ruby-sass-is-deprecated) and [2020](https://sass-lang.com/blog/libsass-is-deprecated) respectively.

Version 2.x of Vertical Rhythm Reset makes the recommended switch to [Dart Sass](https://sass-lang.com/dart-sass). The features and CSS output remain identical in to the previous version, however the switch to Dart Sass requires a few implementation changes.

1. Replace the `@import` rule with the new `@use` rule and note the `vr` namespace. The namespace specified will be used to access all variables and mixins. If you are unfamiliar with the differences between `@import` and `@use`, review the [official documentation](https://sass-lang.com/documentation/at-rules/use) for details.

   ```scss
   // Version 1.x
   @import "path/to/vertical-rhythm-reset";
   ```

   ```scss
   // Version 2.x
   @use "vertical-rhythm-reset" as vr;
   ```

1. Global variables names have changed from a `$vr-[name]` pattern to a namespaced `vr.$[name]` pattern. The new `vr.` prefix is based on the namespace delcared in the `@use` statement above.

   ```scss
   // Version 1.x
   $vr-font-size: 14px;
   ```

   ```scss
   // Version 2.x
   vr.$font-size: 14px;
   ```

1. Mixin names have changed from a `vr-[mixin]` pattern to a namespaced `vr.[mixin]` pattern.

   ```scss
   // Version 1.x
   @include vr-reset();
   @include vr-grid();
   ```

   ```scss
   // Version 2.x
   @include vr.reset();
   @include vr.grid();
   ```

1. The `vr()` mixing has been renamed to [`set()`](#set).

   ```scss
   // Version 1.x
   @include vr(/* ... */);
   ```

   ```scss
   // Version 2.x
   @include vr.set(/* ... */);
   ```

## Contact & Support

- Create a [Github issue](https://github.com/jhildenbiddle/vertical-rhythm-reset/issues) for bug reports, feature requests, or questions
- Follow [@jhildenbiddle](https://twitter.com/jhildenbiddle) for announcements
- Add a ⭐️ [star on GitHub](https://github.com/jhildenbiddle/vertical-rhythm-reset) or 🐦 [tweet](https://twitter.com/intent/tweet?url=https%3A%2F%2Fgithub.com%2Fjhildenbiddle%2Fvertical-rhythm-reset&hashtags=css,sass,scss,frontend) to spread the word and support the project!

## License

This project is licensed under the [MIT license](https://github.com/jhildenbiddle/vertical-rhythm-reset/blob/main/LICENSE).

Copyright (c) John Hildenbiddle ([@jhildenbiddle](https://twitter.com/jhildenbiddle))

<!-- GitHub Buttons -->
<script async defer src="https://buttons.github.io/buttons.js"></script>
