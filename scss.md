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
