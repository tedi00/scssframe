# Small SCSS Pseudo-Framework

Designed to keep larger projects with multiple developers clean and consistent
despite them all writing styles instead of using ready-made classes.

Comes with simple separation of concerns, ease of use, and most importantly,
less thinking required for devs.

* Configure colors and variables
* Read through `util-mixins`
* Check `component-mixins` if your generic component is there, if not, create
* Add mixins you need and other custom styles to your semantic CSS classes

All you need is an understanding of CSS.

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
@use "package" as p;
.card { /* semantic class name */
    @include p.card; /* card mixin */
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