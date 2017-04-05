# CSS

## Table of Contents
- [Directory Structure](#directory-structure)
- [BEM](http://getbem.com/) Block Element Modifier
- [BEM in the wild](http://csswizardry.com/2013/01/mindbemding-getting-your-head-round-bem-syntax/)
- [SASS/SCSS](http://sass-lang.com/guide) We are using SCSS
- [CSS Reference](http://tympanus.net/codrops/css_reference/) extensive reference for CSS properties

## BEM

**Blocks**
```SCSS
.billboard {
  // your code
}
.site-header {
  // your code
}
```    
**Block Modifiers**
```SCSS
.billboard--modifier {
  // your code
}
.site-header--modifier {
  // your code
}
```

**Block Elements**
```SCSS
.billboard__element {
  // your code
}
.site-header__element {
  // your code
}
.site-header__my-element {
  // your code
}
```
**Block Element Modifier**
```SCSS
.billboard__element--modifier {
  // your code
}
.site-header__element--modifier {
  // your code
}
.site-header__my-element--modifier {
  // your code
}
```

## Directory Structure

We are using a folder structure similar to [SMACSS](https://smacss.com/):

- `main.scss`: Center of the styling universe. Includes all internal and external styles (like node_modules or bower_components).
- `base`: All [base rules](https://smacss.com/book/type-base) & [layout rules](https://smacss.com/book/type-layout).
- `components`: Each component deserves an own file where its [module rules](https://smacss.com/book/type-module) and [state rules](https://smacss.com/book/type-state) go. Mind the underscore in the filename, which marks it as an include, so SASS won't generate an own .css file for every component.
- `util`: Variable definitions (also overrides for included styles from node_modules), SASS Mixins and Patterns.

```
+-- base
|   +-- _base.scss
+-- components
|   +-- _teaser.scss
|   +-- _billboard.scss
|   +-- _slideshow-slide.scss
+-- util
|   +-- _mixins.scss
|   +-- _patterns.scss
|   +-- _variables.scss
+-- main.scss
```

