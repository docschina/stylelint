# property-blacklist

指定禁用的属性的黑名单。

```css
a { text-rendering: optimizeLegibility; }
/** ↑
 * 这个属性 */
```

## 选项

`array|string`: `["array", "of", "unprefixed", /properties/ or "regex"]|"property"|"/regex/"`|/regex/

如果字符串用 `"/"` 包围（例如 `"/^background/"`），则将其解释为正则表达式。这允许方便的简写，例如：`/^background/` 将匹配 `background`、`background-size`、`background-color` 等。

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
