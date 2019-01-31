# selector-combinator-whitelist

指定允许的组合选择器的白名单。

```css
  a + b {}
/** ↑
 * 这个组合选择器 */
```

此规则将空白后代选择器规范化为单个空格。

此规则忽略[参考选择器](https://www.w3.org/TR/selectors4/#idref-combinators)，例如 `/for/`。

## 选项

`array|string`: `["array", "of", "combinators"]|"combinator"`

给定：

```js
[">", " "]
```

以下模式被视为违规：

```css
a + b {}
```

```css
a ~ b {}
```

以下模式*不*被视为违规：

```css
a > b {}
```

```css
a b {}
```

```css
a
b {}
```
