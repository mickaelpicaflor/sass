# Quasar Sass Style Guide

*An experimental approach to Sass organization, naming and so on.*

This style guide tries to stay as much compliant as possible with the current prevalent css/sass standards. However some things can differ based on experiences and preferences.

## Table of Contents

  1. [Basic Rules](#basic-rules)
  1. [Code organization](#code-organization)
  1. [Naming](#naming)

## Basic Rules

## Code organization

The following code structure is not made to be followed 100% as it is. It remaines a proposition, a base, and should be adapted according each project needs.

```
scss
├── assets
│   └── _a-fonts.scss                                   // Font faces, typekit, google fonts etc...
│   └── _a-keyframes.scss
├── base
│   └── _b-reset.scss
│   └── _b-typography.scss
├── components
│   └── {componentName}
│           └── _c-{componentName}.scss
│               └── _c-{componentChildName}.scss
├── elements
│   └── {elementName}
│           └── _e-{elementName}.scss
├── layout
│   └── _la-{layoutName}.scss
├── libs
│   └── {libName}
│           └── _li-{libName}.scss
├── modules
│   └── {moduleName}
│           └── _m-{moduleName}.scss
│               └── _m-{moduleChildName}.scss
├── pages
│   └── _p-{pageName}.scss
├── theme
│   └── {themename}
│           └── {themeMode}
│               └── _t-{colorScheme}.scss
│               └── _t-{fonts}.scss
│               └── _t-{root}.scss
│               └── _t-{layout}.scss
├── _shame.sccs
├── main.sccs
```


## Naming

