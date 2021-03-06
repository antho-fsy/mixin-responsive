mixin-responsive
======================

A sass mixin to make responsive all property easy

## Example

a simple demo here : https://codepen.io/antho-fsy/pen/xMmjRb

## Mixin

```sass
@mixin responsive($property, $r-map, $r-breakpoints: $r-breakpoints) {
    @each $r-breakpoint, $r-size in $r-map {
        @if $r-breakpoint == null {
            #{$property}: $r-size;
        }
        @else {
            @if map-has-key($r-breakpoints, $r-breakpoint) {
                $r-breakpoint: map-get($r-breakpoints, $r-breakpoint);
            }
            @media screen and (min-width: $r-breakpoint) {
                 #{$property}: $r-size;
            }
        }
    }
}
```

## Variables 

```sass
$screen-tablet: 768px;
$screen-desktop-large: 1300px;

$space-s: 10px;
$space-m: 30px;
$space-l: 40px;

$r-breakpoints: (
    medium: $screen-tablet,
    large: $screen-desktop-large
);

$mp-default: (
    null  : $space-s,
    medium: $space-m,
    large : $space-l
);

$fs-default: (
    null  : 24px,
    medium: 14px
);

$width-default: (
    null  : 100%,
    medium: auto
);
```

## Example

```sass
.bloc {
  display: inline-block;
  background-color: #243145;
  @include responsive(width, $width-default);
  .bloc02 {
    background-color: #ff4848;
    @include responsive(margin, $mp-default);
    @include responsive(padding, $mp-default);
    @include responsive(font-size, $fs-default);
    transition: .3s;
  }
}

```

## Output example

```css
.bloc {
  display: inline-block;
  background-color: #243145;
  width: 100%;
}

@media screen and (min-width: 768px) {
  .bloc {
    width: auto;
  }
}

.bloc .bloc02 {
  background-color: #ff4848;
  margin: 10px;
  padding: 10px;
  font-size: 24px;
  transition: .3s;
}

@media screen and (min-width: 768px) {
  .bloc .bloc02 {
    padding: 30px;
    font-size: 14px;
    margin: 30px;
  }
}

@media screen and (min-width: 1300px) {
  .bloc .bloc02 {
    margin: 40px;
    padding: 40px;
  }
}


```
