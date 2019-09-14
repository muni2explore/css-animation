# SASS

## SCSS - MAPS

```scss
$font-weights:(
  'regular': 400,
  'medium': 500,
  'bold': 700
)

body{
  font-weight: map-get($font-weights, bold)
}

```
