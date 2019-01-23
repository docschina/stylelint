# declaration-property-value-blacklist

Specify a blacklist of disallowed property and value pairs within declarations.

```css
a { text-transform: uppercase; }
/** ↑               ↑
 * These properties and these values */
```

## 选项

`object`: `{
  "unprefixed-property-name": ["array", "of", "values"],
  "unprefixed-property-name": ["/regex/", "non-regex", /regex/]
}`

如果属性名称用 `"/"` 包围（例如 `"/^animation/"`），则将其解释为正则表达式。这允许方便的简写，例如：`/^animation/` 将匹配 `animation`、`animation-duration`、`animation-timing-function` 等。

The same goes for values. Keep in mind that a regular expression value is matched against the entire value of the declaration, not specific parts of it. For example, a value like `"10px solid rgba( 255 , 0 , 0 , 0.5 )"` will *not* match `"/^solid/"` (notice beginning of the line boundary) but *will* match `"/\\s+solid\\s+/"` or `"/\\bsolid\\b/"`.

Be careful with regex matching not to accidentally consider quoted string values and `url()` arguments. For example, `"/red/"` will match value such as `"1px dotted red"` as well as `"\"foo\""` and `"white url(/mysite.com/red.png)"`.

给定：

```js
{
  "transform": ["/scale3d/", "/rotate3d/", "/translate3d/"],
  "position": ["fixed"],
  "color": ["/^green/"],
  "/^animation/": ["/ease/"]
}
```

以下模式被视为违规：

```css
a { position: fixed; }
```

```css
a { transform: scale3d(1, 2, 3); }
```

```css
a { -webkit-transform: scale3d(1, 2, 3); }
```

```css
a { color: green; }
```

```css
a { animation: foo 2s ease-in-out; }
```

```css
a { animation-timing-function: ease-in-out; }
```

```css
a { -webkit-animation-timing-function: ease-in-out; }
```

以下模式*不*被视为违规：

```css
a { position: relative; }
```

```css
a { transform: scale(2); }
```

```css
a { -webkit-transform: scale(2); }
```

```css
a { color: lightgreen; }
```

```css
a { animation: foo 2s linear; }
```

```css
a { animation-timing-function: linear; }
```

```css
a { -webkit-animation-timing-function: linear; }
```
