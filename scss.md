# SASS

## SCSS - MAPS

```scss
$font-weights:(
  'regular': 400,
  'medium': 500,
  'bold': 700
)

body{
  font-weight: map-get($font-weights, bold);
}

```
## & , #{&}

```scss

.main {
  &__paragraph{
     font-weight: map-get($font-weights, regular);
  }
}

```
into

```css
.main__paragraph {
  font-weight: 400;
}
```


```scss

.main {
  #{&}__paragraph{
     font-weight: map-get($font-weights, regular);
  }
}

```
into

```css
.main .main__paragraph {
  font-weight: 400;
}
```

## function

```scss

$font-weights:(
  'regular': 400,
  'medium': 500,
  'bold': 700
)

@function weight($weight-name) {
  return map-get($font-weights, $weight-name);
}


body{
  font-weight: weight(bold);
}
```

## mixin
don's repeat styles

```scss
@mixin flexCenter {
  display: flex;
  justify-content: center;
  align-items: center;
}

.main {
  @include flexCenter;
}

```

```scss
@mixin flexCenter1($direction) {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: $direction;
}

.main {
  @include flexCenter(row);
}

```

```scss
@mixin theme($light-theme: true) {
  @if $light-theme {
    background: lighten($primary-color, 100%);
    color: darken($text-color, 100%);
  } 
}

.light {
  @include theme($light-theme: true);
}
```


```scss
@mixin mobile {
  @media (max-width: $mobile) {
     @content;
  }
}


@include mobile{
  flex-direction: column;
}

```

## extend

```scss
.para{
  font-weight: weight(bold);
}

.para1{
  @extend .para;
  font-weight: weight(bold);
}
```

## for loop

```scss
@for $i from 1 through 4 {
  .menu-nav__item:nth-child(#{$i}){
     transistion-delay: ($i * 0.1s) + 0.15s;
  }
}
```
