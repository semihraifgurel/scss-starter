---
id: architecture
title: Architecture
---

Architecting a CSS project is probably one of the most difficult things you will have to do in a project’s lifetime and keeping its architecture consistent and meaningful is even harder.

One of the core things of SCSS Starter is its sustainable and scalable architecture inspired by [ITCSS](http://itcss.io). It pays a lot of attention to how specificity evolves so that you don’t have any undesired behavior.

## Folder Structure

After downloading, extract the files into the directory where your website is located. Your directory will look something like this.

```text
root
├─ src/
│  ├─ scss/
│      ├─ abstracts/
│         ├─ mixins/
│         ├─ _colors.scss
│         ├─ _functions.scss
│         ├─ _index.scss
│         ├─ _keyframes.scss
│         ├─ _placeholders.scss
│         └─ _variables.scss
│      ├─ base/
│         ├─ _base.scss
│         ├─ _fonts.scss
│         ├─ _grid.scss
│         ├─ _reset.scss
│         └─ _utilities.scss
│      ├─ components/
│         └─ _index.scss
│      ├─ libs/
│         ├─ _index_.scss
│         └─ _normalize.scss
│      ├─ objects/
│         └─ _index.scss
│      └─ main.scss
```

### Abstracts folder

The `abstracts/` folder gathers all Sass tools and helpers used across the project. Every global variable, function, mixin and placeholder should be put in here.

The rule of thumb for this folder is that it should not output a single line of CSS when compiled on its own. These are nothing but Sass helpers.

### Base folder

The `base/` folder holds what we might call the boilerplate code for the project. In there, you might find the reset file, some typography rules, and probably a stylesheet defining some standard styles for commonly used HTML elements (that I like to call `\_base.scss`).

### Objects folder

The `objects/` folder contains every file that takes part in laying out your site or application. This folder may have stylesheets for the main parts of your site or application (header, footer, navigation, sidebar…), the grid system or even CSS styles for all your forms.

### Components folder

The `components/` folder contains well-designed pieces of UI that can be reused at more than one spot. There are usually a lot of files in this folder since the whole site/application should be mostly composed of tiny modules. Buttons, form control elements, alerts, may be counted as examples.

### Libs Folder

And last but not least, most projects will have a `libs/` folder containing all the CSS files from external libraries and frameworks like – Normalize, Bootstrap, and so on. Putting those aside in a separate folder is a good way to say “Hey, this is not from me, not my code, not my responsibility”.

### Main file

The main file (usually labeled `main.scss`) should be the only Sass file of the whole codebase which should not begin with an underscore, and also should not contain anything but `@import` and comments.

In the main file the order of imports is important. Order should be as follows:

```scss
@import 'abstracts/index';

@import 'libs/index';

@import 'base/reset';

@import 'base/fonts';

@import 'base/grid';

@import 'base/base';

@import 'components/index';

@import 'objects/index';

@import 'base/utilities';
```
