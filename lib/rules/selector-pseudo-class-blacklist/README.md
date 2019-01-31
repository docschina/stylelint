# selector-pseudo-class-blacklist

指定禁用的伪类选择器的黑名单。

```css
  a:hover {}
/** ↑
 * 这个伪类选择器 */
```

此规则忽略使用变量插值的选择器，例如 `:#{$variable} {}`。

## 选项

`array|string|regex`: `["array", "of", "unprefixed", /pseudo-classes/ or "/regex/"]|"pseudo-class"|/regex/`

如果字符串用 `"/"` 包围（例如 `"/^nth-/"`），则将其解释为正则表达式。这允许方便的简写，例如：`/^nth-/` 将匹配 `nth-child`、`nth-last-child`、`nth-of-type` 等。

给定：

```js
["hover", "/^nth-/"]
```

以下模式被视为违规：

```css
a:hover {}
```

```css
a:nth-of-type(5) {}
```

```css
a:nth-child(2) {}
```

以下模式*不*被视为违规：

```css
a:focus {}
```

```css
a:first-of-type {}
```
