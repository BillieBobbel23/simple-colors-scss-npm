# simple-colors-scss

Simple-colors-scss is a map based color manager for SCSS.  
It aims towards simple setup, utilization and extendibility.

![version](https://img.shields.io/npm/v/simple-colors-scss.svg)
![size](https://img.shields.io/bundlephobia/minzip/simple-colors-scss)
![stats](https://david-dm.org/BillieBobbel23/simple-colors-scss/status.svg)

## Installation:

Install the package using [NPM](https://www.npmjs.com/get-npm):  
`` npm install simple-colors-scss --save``  

## Setup:

Create a empty theme file from the project directory:  
``npm run create --prefix ./node_modules/simple-colors-scss``  

Import the package and newly createds ``_colors.scss`` into your stylesheet (before other logic):  

```
1. @import 'your_project/node_modules/simple-colors-scss/core';
2. @import 'your_project/colors';
```

## Setting colors:

A color scheme is a map of color codes and bindings to them, all inside ``_colors.scss``.  

Add unique colors to the ``$colors`` variable:  
*These use [name-that-color](http://chir.ag/projects/name-that-color/#6195ED):*

```
  $colors: {
    // Named colors (HEX):
    'white': #FFF,
    'deep-orange': #BDBDBD,
    'alizarin-crimson': #E32636
    
    // but we can use other color systems:
    'purple-rgb': rgb(255,0,128),
    'white-rgba-33' rgba(255,255,255, .33),
    'blue-hsl': hsl(240, 100%, 50%),

    // or metavalues
    'transparent': transparent 
  }
``` 
  
Next add custom bindings, shorthands and variations to ``$bindings`` using the [color()](#using-color()) function:

  ```
  $binding: {
    // use shorthands
    'orange': color('deep-orange'), 
    'pink': color('alizarin-crimson'),

    // or variations
    'orange-light': lighten(color('deep-orange'), 30%),
    'orange-dark': darken(color('deep-orange'), 30%),

    // or theming
    'primary': color('alizarin-crimson'),
    'primary-text': color('white'),
    
    // or complex colors
    'border-y': color('orange-dark') color('none'),
    'gradient': linear-gradient(to left, color('deep-orange'), color('alizarin-crimson'))
  }
  ```

## Using color():

Next to ``$bindings`` the ``color()`` function is used in your regular SCSS to fetch colors:

```
background-image: color("blue-hsl");
``` 

Add some functionality and logic to these to easily create custom mixins.  
*Use [simple-colors-scss-helpers](https://github.com/billiebobbel23/simple-color-scss-helpers) to get some examples of some simple mixins using this package.*

```
@import "your/project/node_modules/simple-colors-scss";

@include bg('blue-hsl'); // will produce the same
```



If the value is either indefined or unknow it will fail gracefully.

// @debug "Unknown color: `#{$key}` found, value could not be set";
```

## Use it:

Now you can do things like:
```
color: color('white');
background-color(color('orange-dark'));
border: 1px solid color('border-y');
```
