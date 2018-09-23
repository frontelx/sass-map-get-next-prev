# Sass map-get functions

Enhancement functions map-get-next and map-get-prev.  
For example when Sass map is used with a `@each` loop.

* [map-get-next](#map-get-next)
  + [Basic usage](#basic-usage)
    - [CSS output](#css-output)
  + [Pracical usage](#pracical-usage)
    - [CSS output](#css-output-1)
  + [Parameters](#parameters)
* [map-get-prev](#map-get-prev)
  + [Basic usage](#basic-usage-1)
    - [CSS output](#css-output-2)
  + [Parameters](#parameters-1)

## map-get-next

Function to get next map item.  
Returns next map item or fallback value if map, key or next item does not exist.

### Basic usage

```sass
$map: (
    s: 320px,
    m: 768px,
);

.foo {
  width: map-get-next($map, s);
}

.bar {
  width: map-get-next($map, m, 1024px);
}
```

#### CSS output

```css
.foo {
  width: 768px;
}

.bar {
  width: 1024px;
}
```

### Pracical usage

Set min- and max with for all breakpoints in Sass map.

```sass
$map: (
    s: 320px,
    m: 768px,
);

@each $breakpoint, $width in $map {
  @media (min-width: $width) and (max-width: map-get-next($map, $breakpoint, 1024px) - 1px) {
    ...
  }
}
```

#### CSS output

```css
@media (min-width: 320px) and (max-width: 767px) {
  ...
}

@media (min-width: 768px) and (max-width: 1023px) {
  ...
}
```

### Parameters

* **$map** - Sass list map
* **$key** - List map key
* **$fallback** (false) - Fallback value if map, key or next item does not exist
* **$debug** (false) - Debug option

## map-get-prev

Equivalent to map-get-next

Function to get previous map item.  
Returns previous map item or fallback value if map, key or previous item does not exist.

### Basic usage

```sass
$map: (
    s: 320px,
    m: 768px,
);

.foo {
    width: map-get-prev($map, m);
}

.bar {
    width: map-get-prev($map, s, 240px);
}
```

#### CSS output

```css
.foo {
    width: 320px;
}

.bar {
    width: 240px;
}
```

### Parameters

* **$map** - Sass list map
* **$key** - List map key
* **$fallback** (false) - Fallback value if map, key or previous item does not exist
