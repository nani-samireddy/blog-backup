---
title: "Scss cheat sheet"
seoTitle: "SCSS cheat sheet"
datePublished: Thu Feb 08 2024 06:58:43 GMT+0000 (Coordinated Universal Time)
cuid: clscvax6400080akzdefz49j2
slug: scss-cheat-sheet
tags: css, sass, scss, cheatsheet, css-che, sass-cheat-sheet, scss-cheat-sheet

---

### variables

```scss
$primary-color: #3498db;
$secondary-color: #2ecc71;
$base-font-size: 16px;
$font-scale-factor: 1.2;
$container-width: 960px;
$content-width: $container-width - 40px;
```

### Nesting

```scss
.navigation {
  ul {
    list-style: none;
    li {
      display: inline-block;
      margin-right: 10px;
      a {
        text-decoration: none;
        color: $primary-color;
        &:hover {
          color: $secondary-color;
        }
      }
    }
  }
}
```

### Mixins

```scss
@mixin border-radius($radius) {
  -webkit-border-radius: $radius;
  -moz-border-radius: $radius;
  border-radius: $radius;
}

.button {
  @include border-radius(5px);
  background-color: $primary-color;
  color: #fff;
  padding: 10px 20px;
}
```

### Extend (Inheritance)

```scss
.error {
  color: red;
}
.error-message {
  @extend .error;
  border: 1px solid red;
}
```

### Functions

```scss
@function adjust-font-size-to($base-size, $scale-factor) {
  @return $base-size * $scale-factor;
}
```

### Partials and Importing

```scss
@import 'variables';
@import 'mixins';
@import 'components/navigation';
```

### Operators

```scss
.container {
  width: $container-width;
}
.content {
  width: $content-width;
}
```

### Control Directives (if, for, each)

```scss
@for $i from 1 through 3 {
  .column-#{$i} {
    width: 100px * $i;
  }
}
```

### Placeholder Selectors

```scss
%box-style {
  border: 1px solid black;
  padding: 10px;
}

.box1 {
  @extend %box-style;
  background-color: #fff;
}

.box2 {
  @extend %box-style;
  background-color: #f2f2f2;
}
```

### Comments

```scss
// This is a single-line comment
/*
 * This is a multi-line comment
 * You can write multiple lines here
 */
```