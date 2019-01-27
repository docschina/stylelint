# selector-max-combinators

限制一个选择器中组合选择器的数量

```css
  a > b + c ~ d e { color: pink; }
/** ↑   ↑   ↑  ↑
 * 这些是组合选择器 */
```

此规则在计算组合选择器的数量之前先解析选择器嵌套。[选择器列表](https://www.w3.org/TR/selectors4/#selector-list)中的每个选择器都将单独计算。

## 选项

`int`：允许的最大组合选择器数量。

例如，使用 `2`：

以下模式被视为违规：

```css
a b ~ c + d {}
```

```css
a b ~ c {
  & > d {}
}
```

```css
a b {
  & ~ c {
    & + d {}
  }
}
```

以下模式*不*被视为违规：

```css
a {}
```

```css
a b {}
```

```css
a b ~ c {}
```

```css
a b {
  & ~ c {}
}
```

```css
/* 选择器列表中的每个选择器都将单独计算 */
a b,
c > d {}
```
