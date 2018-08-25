# Getting Started

Better/real docs coming

## Installation

Install the library via npm, the usual way:

    $ npm install 

```scss
@include "cupcake-foundations";
```

Otherwise, if you don't want to customise anything, just include the whole path:

```scss
@include "node_modules/cupcake-foundations/sass/cupcake";
```

You can then configure it by creating the [Cupcake configuration map](#Configuration).

Once that's done, you need to call the initialisation mixin that will generate the necessary configuration maps and base CSS output:

```scss
@include cupcake-init;
```

## Configuration

The configuration comes simply by setting the required sub-maps in the main `$cupcake` map, you can set one or more of the following keys in you project, `cupcake-init` will fill in the rest with the following default values.

```scss
$cupcake: (
  base-font-size: 16px,
  base-line-height: 1.4,
  breakpoints: (
    small: 600px,
    large: 1200px
  ),
  typefaces: (
    primary: (
      stack: ('Arial', sans-serif),
      weights: (
        regular: 'regular',
        bold: 'bold'
      )
    )
  )
);
```

More technical documentation in HTML format can be found in the `docs/` folder.

### Generated and reserved variables

`cupcake-init` will parse the `$cupcake` config map, and generate some additional non-scoped variables that are going to be used by either the dependencies or some of the mixins available by the tool.

- `$base-font-size`: handy variable for the size in pixels of the base font size.
- `$base-line-height`: unitless variable for the size of the line height.
- `$breakpoints`: will contain a list of named breakpoints. These will have to be used in the configuration map of `typi` that can be retrieved using the mixin `cupcake-breakpoint($name)`.
- `$typefaces`: will contain a list of named font faces, e.g. 'primary', 'headings', ...; you can later output the correct `font-family` and `font-weight` using the mixin `cupcake-font($name, $weight: 'regular')` each font face contains the following keys: 
  - `stack`: a map containing the list of font families to use.
  - `weights`: a list of weights for the selected font, like 'regular', 'bold', ... .

### Functions

- `cupcake-breakpoint($name)`: outputs the actual size given the name set in the `breakpoint` map (see [Generated and reserved variables](#Generated-and-reserved-variables) section).

### Mixins

- `cupcake-init`: does the initialisation of all the needed functions, needs to be called after all the needed maps have been configured and before calling any other function or mixin.
- `cupcake-font($name)`: generates the `font-family` and `font-weight` based on the `typefaces` map (see [Generated and reserved variables](#Generated-and-reserved-variables) section).


## Contribute & support

You can contribute to the development of this library in many ways:

- submitting [bug reports](link),
- opening [PRs](link),

**NOTE** Be sure to enable [stylelint](https://stylelint.io/) in your preferred IDE/Editor, or run `npm test` before pushing and opening a PR: any PR submitted that doesn't lint correctly will be rejected.
