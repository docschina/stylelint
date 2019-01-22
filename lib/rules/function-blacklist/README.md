# function-blacklist

Specify a blacklist of disallowed functions.

```css
a { transform: scale(1); }
/**            ↑
 * These functions */
```

## 选项

`array|string`: `["array", "of", "unprefixed", /functions/ or "regex"]|"function"|"/regex/"`

If a string is surrounded with `"/"` (e.g. `"/^rgb/"`), it is interpreted as a regular expression.

Given:

```js
["scale", "rgba", "linear-gradient"]
```

以下模式被视为违规：

```css
a { transform: scale(1); }
```

```css
a {
  color: rgba(0, 0, 0, 0.5);
}
```

```css
a {
  background:
    red,
    -moz-linear-gradient(45deg, blue, red);
}
```

The following patterns are *not* considered violations:

```css
a { background: red; }
```
