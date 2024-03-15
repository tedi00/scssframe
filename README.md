# Small SCSS Pseudo-Framework

Designed to keep larger projects with multiple developers clean and consistent
despite them all writing styles instead of using ready-made classes.

Comes with simple separation of concerns, ease of use, and most importantly,
less thinking required for devs.

* Configure colors and variables
* Read through `util-mixins`
* Check `component-mixins` if your generic component is there, if not, create
* Add mixins, functions and variables you need and other custom styles to your 
semantic CSS classes

All you need is an understanding of CSS.
See [dev notes](#dev-notes) for a manifesto.

## Usage guidelines

* Repeating **values** of (S)CSS properties (colors, numerical values, etc.) are 
mostly defined through variables defined in either `colors` or `variables` unless 
single-use, odd values (property values specific to a single element).
* Repeating **property-value groups** are defined in mixins, reflected as `@include`-d
in semantic **class names** for components.
* Repeating **components** are defined with semantic class names, often including one or
more mixins.
* **Utility classes** are highly discouraged in favour of semantic class names, with
the utility added through functions, mixins and variables in the appropriate SCSS files.
* **Utility functions** and mixins are encouraged.
* **Separation of concerns** is highly encouraged, keeping styling and its related language
separate in the SCSS files, and not bleeding into HTML.

### Usage guideline examples and explanations

#### Good:

```scss
@use "preparatory/package" as p;

.card { /* semantic class name */
  @include p.card; /* card mixin */
  color: p.$c-black;
  background-color: p.$c-white-2; /* color through variable */
}
```
### Bad:
```scss
.d-flex { /* utility class - styling language and purpose bleeds into HTML */
  /* flex and gap should be a utility mixin, and gap and color values should 
  be derived by declared scss variables in other files */
  display: flex;
  gap: 1.25em;
  color: orangered;
}
```

## Dev notes

While using utility classes has been the standard for a long time, it is also
a bad way to get comfortable developing websites.

Bootstrap and tailwind abstract away CSS, leaving us with only a basic understanding,
lazy way to develop, and breaking separation of concerns, while component frameworks 
like Angular Material, as customizable as they are, still lead us to web apps that 
look and feel the same every time.

Some internal projects may pass this low bar, but every project from an outside 
brand/company - as well as internal projects of any highly reputable development 
team/company - will undeniably require highly customized components and complex 
styles based on usage concerns as well as web designers' preferences and ideas.

Creating projects where multiple people work together in harmony with only SCSS
can be challenging, as everyone has the urge to write their own styles. This is
why the usage guidelines for this internal framework were developed to help developers
reuse each other's variables, mixins, functions, etc. in order to work in sync
without the need to keep each other updated through meetings all the time.

