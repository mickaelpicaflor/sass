![App Header](./app_readme-1024x-light.png)

# Quasar Sass Style Guide

*An experimental approach to Sass organization, naming and so on.*

This style guide tries to stay as much compliant as possible with the current prevalent css/sass standards. However some things can differ based on experiences and preferences.

## Table of Contents

  1. [Basic Rules](#basic-rules)
  1. [Code organization](#code-organization)
  1. [Naming](#naming)

## Basic Rules

Reminder, this guide is supposed to be used as a reference but does not pretend at any time to be a pure source of truth. It is made to make scss code a bit more consistent and a bit more logic. The goal is to make your life easier, if ever you arrive at a point when you are overthinking, or think it wastes more time than it is supposed to save, just code your own way.

It is recommended to use a plugin such as beautify or prettier with your code editor to keep code nice and clean. A csscomb config file may be granted in this repo soon.

## Code organization

The following code structure is not made to be followed 100% as it is. It remaines a proposition, a base, and should be adapted according each project needs.

```
scss
├── assets
│   └── _a-Fonts.scss
│   └── _a-Keyframes.scss
│   └── _a-Mixins.scss
├── base
│   └── _b-Reset.scss
│   └── _b-Typography.scss
├── components
│   └── {ComponentName}
│       └── _c-{ComponentName}.scss
│           └── _c-{ComponentChildName}.scss
├── elements
│   └── {ElementName}
│       └── _e-{ElementName}.scss
├── layout
│   └── _la-{LayoutName}.scss
├── libs
│   └── {LibName}
│       └── _li-{LibName}.scss
├── modules
│   └── {ModuleName}
│       └── _m-{ModuleName}.scss
│           └── _m-{ModuleChildName}.scss
├── pages
│   └── _p-{PageName}.scss
├── theme
│   └── {Themename}
│       └── {ThemeMode}
│           └── _t-{ColorScheme}.scss
│           └── _t-{Fonts}.scss
│           └── _t-{Root}.scss
│           └── _t-{Layout}.scss
├── _shame.sccs
├── main.sccs
```

As you can see, first level folder are written in lowercase, whereas component folder name, and component folder name are wrriten in PascalCase (except prefixes).

Let's have a bit of explanations concerning some of the files above :

- **Assets**

`/assets/_a-fonts.scss`

Gathers fonts importations, font faces, typekit, google fonts and so on.

`/assets/_a-keyframes.scss`

Gathers every keyframes animation so it can be used as a source of truth for every animation in the app.

`/assets/_a-mixins.scss`

Same as keyframes but for mixins.


- **Base**

`/base/_b-reset.scss`

Resets major browser native styles (this file could also be called `_b-normalize.scss`).


`/base/_b-typography.scss`

Creates default/fallback font styles for tags such as `<hN>`, `<p>`, and so on.


- **Elements, Components, and Modules**

Let's talk about `elements`, `components`, `modules` and how to differentiate them.

An `element` is either a micro component or a file made to style html tags (or equivalent). For example, we could have a style called `_e-checkboxes.scss` containing the styles related to every checkbox (micro-component), or a file called `_e-form.scss` containing the default/fallback styles related to every html tag inside a form `input`, `select`, and so on.

A `module` is a group of code that can be derived sementically in `components`. To better understand let's see an example. Let's say that in our project we have a list of resources (kind of a table). We will have a `module` file called `/ResourceList/_m-ResourceList.scss` which will define the shared styles of every type of resource list in our app. Some module can have children, in our example we could have a module child file called `/ResourceList/_m-ResourceListItem.scss` defining shared styles for our resource list items.

Then let's say that our app will be containing an order list, and a customer list. We would then have two components `/OrderList/_c-OrderList.scss` and `/CustomerList/_c-CustomerList.scss` (and their respective list item), that would define styles overwriting our module styles to fit their needs.


- **Layout**

`/layout/_la-{LayoutName}.scss`

This file is kinda specific to some frameworks (e.g. React.js / Vue.js) and will be used to add some layout components style specifications.

`/libs/{LibName}/_li-{LibName}.scss`

If needed, when using a library that adds styles to your app which need to be customized, you can create a folder and a file with the same name of the library to overwrite its default styles.


- **Page/Template**

`/page/_p-{PageName}.scss`

This file may be also called `/template/_te-{TemplateName}` in some cases. As its name says, it is used to define some style specifications according to page/template.


- **Theme**

`/theme/...`

It is possible to pre-define some styles or variables sets to prepare theme for your app. To do so, create a folder with the name of your theme. You can choose to add a sub-folder with a mode for your theme (e.g. light and dark). And finally you can create some files to define theme specific styles.


- **Misc**

`_shame.scss`

Optional file. It would be used to store ugly styles tweak. A well coded app should have this file empty.

`main.scss`

This file is used to handle which and how partials files are loaded into the app. There could be several files of this type with different names if app is becoming so big that you need to only exports some specific partials at a time.


## Naming

The naming convetions are greatly inspired from [BEM Suit CSS practices](https://github.com/suitcss/suit/blob/master/doc/naming-conventions)

In this section we will talk about Bundle, Component, descendant, part, modifier, and states, so we better do some explanations before so we all understand what it is about.


- **Bundle**

In most of the project this will be absent, but if you want/need to, you can add bundle name in front of class name. Imho it reduces a lot class visibility buit is totally up to you.


- **Component**

In class name, component corresponds to what your class defines. It could be everything, an alert, a panel, everything. The only requirement is that is is semantic.

```css
// Good
._e-ToolTip {}

// Bad
.e-RedBlock {}

```


- **Descendant**

A descendant is a child of your component. 

It should be written precede by two underscores. 

```css
// Good
._e-ToolTip__Content {}

// Bad
.e-ToolTipContent {}

```


- **Part**

The main difference between a part and a descendant is that if you remove a part from its parent, parent does not lose its integrity (e.g. `Filter-TypeOfFilter` you can have several type of filters acting independantly ; `Button__Content` if you remove content from Button it loses its integrity)

A part should be written precede by a hyphen.

```css
// Good
._e-ToolTip-Icon {}

// Bad
.e-ToolTipIcon {}

// Bad
.e-ToolTip__Icon {} // A tooltip can be define without an icon

```


- **Modifier**

Modifiers should be written in camelCase, precede by two hyphens.

```css
// Good
._e-ToolTip--fromTop {}

// Bad
.e-ToolTipFromTop {}

```


- **States**

States are made to reflect changes to a component's sate. It should be written camelCase with a hyphen between verb and state. 

```css
// Good
._e-ToolTip.has-error {}
._e-ToolTip.has-multipleErrors {} 

// Bad
.e-ToolTipHasError {}

```

These classes should never directly be styled they should always be used as an adjoining class. This means that several components could have the same state of component class, but every class should be define in its own context.

```html
// Good
<div class="_e-ToolTip has-Error"></div>

<style>
    ._e-ToolTip.has-error {
        color : red;
    }
</style>

<div class="_e-Alert has-Error"></div>

<style>
    ._e-Alert.has-error {
        color : orange;
    }
</style>


// Bad
<div class="_e-ToolTip has-Error"></div>

<style>
    .has-error {
        color : palevioletred;
    }

    ._e-ToolTip.has-error {
        color : red !important;     // !important is only an example
    }
</style>

```
Each class name should have a prefix corresponding to the sass file it takes its source in.


Let's resume :

```css
._x-ComponentName {}
._x-ComponentName__DescendantName {}

._x-ComponentName-ComponentPartName {}
._x-ComponentName-ComponentPartName__DescendantName {}

._x-ComponentName--someModifier {}
._x-ComponentName.is-stateOfComponent {}

```