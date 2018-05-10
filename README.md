Some helpful functions that enhance Sass

# map-get-next

Function to get next map item  
returns next map item or fallback value if map, key or next item does not exist

```sass
$map: (
    a: 100px,
    b: 200px
);

.foo {
    width: map-get-next($map, a);
}

.bar {
    width: map-get-next($map, b, auto);
}
```

Will generate the following CSS

```css
.foo {
    width: 200px;
}

.bar {
    width: auto;
}
```

### Parameters

* **$map** - Sass list map
* **$key** - List map key
* **$fallback** (false) - Fallback value if map, key or next item does not exist
* **$debug** (false) - Debug option

# map-get-prev

Function to get previous map item
returns previous map item or fallback value if map, key or previous item does not exist

```sass
$map: (
    a: 100px,
    b: 200px
);

.foo {
    width: map-get-prev($map, n);
}

.bar {
    width: map-get-prev($map, a, auto);
}
```

Will generate the following CSS

```css
.foo {
    width: 100px;
}

.bar {
    width: auto;
}
```

### Parameters

* **$map** - Sass list map
* **$key** - List map key
* **$fallback** (false) - Fallback value if map, key or previous item does not exist
