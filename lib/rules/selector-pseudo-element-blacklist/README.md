# selector-pseudo-element-blacklist

Specify a blacklist of disallowed pseudo-element selectors.

```css
 a::before {}
/** ↑
 * These pseudo-element selectors */
```

This rule ignores:

-   CSS2 pseudo-elements i.e. those prefixed with a single colon
-   selectors that use variable interpolation e.g. `::#{$variable} {}`

## 选项

`array|string|regex`: `["array", "of", "unprefixed", "pseudo-elements" or "regex"]|"pseudo-element"|/regex/`

Given:

```js
["before", "/^my-/i"]
```

以下模式被视为违规：

```css
a::before {}
```

```css
a::my-pseudo-element {}
```

```css
a::MY-OTHER-pseudo-element {}
```


The following patterns are *not* considered violations:

```css
a::after {}
```

```css
a::not-my-pseudo-element {}
```
