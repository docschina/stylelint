# property-whitelist

Specify a whitelist of allowed properties.

```css
a { display: block; }
/** ↑
 * These properties */
```

This rule ignores variables (`$sass`, `@less`, `--custom-property`).

## 选项

`array|string`: `["array", "of", "unprefixed", /properties/ or "regex"]|"property"|"/regex/"`|/regex/

如果字符串用 `"/"` 包围（例如 `"/^background/"`），则将其解释为正则表达式。这允许方便的简写，例如：`/^background/` 将匹配 `background`、`background-size`、`background-color` 等。

给定：

```js
["display", "animation", "/^background/"]
```

以下模式被视为违规：

```css
a { color: pink; }
```

```css
a {
  animation: my-animation 2s;
  color: pink;
}
```

```css
a { borkgrund: orange; }
```

以下模式*不*被视为违规：

```css
a { display: block; }
```

```css
a { -webkit-animation: my-animation 2s; }
```

```css
a {
  animation: my-animation 2s;
  -webkit-animation: my-animation 2s;
  display: block;
}
```

```css
a { background: pink; }
```

```css
a { background-color: pink; }
```
