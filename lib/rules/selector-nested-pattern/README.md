# selector-nested-pattern

指定嵌套规则的选择器的模式。

```css
    a {
      color: orange;
      &:hover { color: pink; }
    } ↑
/**   ↑
 * 这个嵌套选择器 */
```

非标准选择器（例如具有 Sass 或 Less 插值的选择器）和嵌套在@规则内的规则选择器将被忽略。

## 选项

`regex|string`

字符串将被翻译成一个正则表达式，就像 `new RegExp(yourString)` ———— 所以一定要正确转义。

选择器值将完整检查。如果您想允许使用组合选择器和逗号，则必须将它们合并到您的模式中。

给定字符串：

```js
"^&:(?:hover|focus)$"
```

以下模式被视为违规：

```css
a {
  .bar {}
}
```

```css
a {
  .bar:hover {}
}
```

```css
a {
  &:hover,
  &:focus {}
}
```

以下模式*不*被视为违规：

```css
a {
  &:hover {}
}
```

```css
a {
  &:focus {}
}
```

```css
a {
  &:hover {}
  &:focus {}
}
```
