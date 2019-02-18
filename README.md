mixin-responsive
======================

A sass mixin to make responsive all property easy

## Example

a simple demo here : https://codepen.io/antho-fsy/pen/xMmjRb

## Mixin

```
@mixin responsive($property, $r-map, $r-breakpoints: $r-breakpoints) {
    @each $r-breakpoint, $r-space in $r-map {
        @if $r-breakpoint == null {
            #{$property}: $r-space;
        }
        @else {
            @if map-has-key($r-breakpoints, $r-breakpoint) {
                $r-breakpoint: map-get($r-breakpoints, $r-breakpoint);
            }
            @media screen and (min-width: $r-breakpoint) {
                 #{$property}: $r-space;
            }
        }
    }
}
```

## Variables 

```
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
