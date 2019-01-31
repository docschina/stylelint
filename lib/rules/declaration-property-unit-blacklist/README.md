# declaration-property-unit-blacklist

指定声明内禁用的属性和单位对的黑名单。

```css
a { width: 100px; }
/** ↑         ↑
 * 这些属性和单位 */
```

## 选项

`object`: `{
  "unprefixed-property-name": ["array", "of", "units"]
}`

如果属性名称用 `"/"` 包围（例如 `"/^animation/"`），则将其解释为正则表达式。这允许方便的简写，例如：`/^animation/` 将匹配 `animation`、`animation-duration`、`animation-timing-function` 等。

给定：

```js
{
  "font-size": ["em", "px"],
  "/^animation/": ["s"]
}
```

以下模式被视为违规：

```css
a { font-size: 1em; }
```

```css
a { animation: animation-name 5s ease; }
```

```css
a { -webkit-animation: animation-name 5s ease; }
```

```css
a { animation-duration: 5s; }
```

以下模式*不*被视为违规：

```css
a { font-size: 1.2rem; }
```

```css
a { height: 100px; }
```

```css
a { animation: animation-name 500ms ease; }
```

```css
a { -webkit-animation: animation-name 500ms ease; }
```

```css
a { animation-duration: 500ms; }
```
