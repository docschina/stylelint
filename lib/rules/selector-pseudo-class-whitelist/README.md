# selector-pseudo-class-whitelist

Specify a whitelist of allowed pseudo-class selectors.

```css
  a:hover {}
/** ↑
 * These pseudo-class selectors */
```

This rule ignores selectors that use variable interpolation e.g. `:#{$variable} {}`.

## 选项

`array|string|regex`: `["array", "of", "unprefixed", /pseudo-classes/ or "/regex/"]|"pseudo-class"|/regex/`

如果字符串用 `"/"` 包围（例如 `"/^nth-/"`），则将其解释为正则表达式。这允许方便的简写，例如：`/^nth-/` 将匹配 `nth-child`、`nth-last-child`、`nth-of-type` 等。

给定：

```js
["hover", "/^nth-/"]
```

以下模式被视为违规：

```css
a:focus {}
```

```css
a:first-of-type {}
```

以下模式*不*被视为违规：

```css
a:hover {}
```

```css
a:nth-of-type(5) {}
```

```css
a:nth-child(2) {}
```
