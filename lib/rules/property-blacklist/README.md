# property-blacklist

Specify a blacklist of disallowed properties.

```css
a { text-rendering: optimizeLegibility; }
/** ↑
 * These properties */
```

## 选项

`array|string`: `["array", "of", "unprefixed", /properties/ or "regex"]|"property"|"/regex/"`|/regex/

If a string is surrounded with `"/"` (e.g. `"/^background/"`), it is interpreted as a regular expression. This allows, for example, easy targeting of shorthands: `/^background/` will match `background`, `background-size`, `background-color`, etc.

给定：

```js
[ "text-rendering", "animation", "/^background/" ]
```

以下模式被视为违规：

```css
a { text-rendering: optimizeLegibility; }
```

```css
a {
  animation: my-animation 2s;
  color: pink;
}
```

```css
a { -webkit-animation: my-animation 2s; }
```

```css
a { background: pink; }
```

```css
a { background-size: cover; }
```

以下模式*不*被视为违规：

```css
a { color: pink; }
```

```css
a { no-background: sure; }
```
