# declaration-property-value-whitelist

指定声明内允许的属性和值对的白名单。

```css
a { text-transform: uppercase; }
/** ↑               ↑
 * 这些属性和值 */
```

## 选项

`object`: `{
  "unprefixed-property-name": ["array", "of", "values"],
  "unprefixed-property-name": ["/regex/", "non-regex"]
}`

如果在对象中找到属性名称，则仅允许其列入白名单的属性值。此规则会指正所有不匹配的值。（如果属性名称未包含在对象中，则什么都可以。）

如果属性名称用 `"/"` 包围（例如 `"/^animation/"`），则将其解释为正则表达式。这允许方便的简写，例如：`/^animation/` 将匹配 `animation`、`animation-duration`、`animation-timing-function` 等。

值也是如此。请记住，正则表达式值与声明的整个值匹配，而不是与声明的特定部分匹配。例如，像 `"10px solid rgba( 255 , 0 , 0 , 0.5 )"` 这样的值将*不*匹配 `"/^solid/"`（注意开头的行边界）但是*将*匹配 `"/\\s+solid\\s+/"` 或 `"/\\bsolid\\b/"`。

注意正则表达式意料之外的匹配带引号的字符串值和 `url()` 参数。例如 `"/red/"` 将匹配诸如 `"1px dotted red"` 正如 `"\"red\""` 以及 `"white url(/mysite.com/red.png)"`。

给定：

```js
{
  "transform": ["/scale/"],
  "whitespace": ["nowrap"],
  "/color/": ["/^green/"]
}
```

以下模式被视为违规：

```css
a { whitespace: pre; }
```

```css
a { transform: translate(1, 1); }
```

```css
a { -webkit-transform: translate(1, 1); }
```

```css
a { color: pink; }
```

```css
a { background-color: pink; }
```

以下模式*不*被视为违规：

```css
a { color: pink; }
```

```css
a { whitespace: nowrap; }
```

```css
a { transform: scale(1, 1); }
```

```css
a { -webkit-transform: scale(1, 1); }
```

```css
a { color: green; }
```

```css
a { background-color: green; }
```

```css
a { background: pink; }
```
