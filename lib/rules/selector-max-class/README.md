# selector-max-class

限制一个选择器中类的数量

```css
div .foo.bar[data-val] > a.baz {}
/*  ↑   ↑                 ↑
    ↑   ↑                 ↑
    1   2                 3  -- this selector contains three classes */
```

此规则在计算一个选择器的类的数量之前先解析选择器嵌套。[选择器列表](https://www.w3.org/TR/selectors4/#selector-list)中的每个选择器都将单独计算。

`:not()` 伪类的内容也是单独计算的。此规则将其参数视为一个独立的选择器，结果不计入整个选择器的总数。

## 选项

`int`：允许的最大类数量。

例如，使用 `2`：

以下模式被视为违规：

```css
.foo.bar.baz {}
```

```css
.foo .bar {
  & > .baz {}
}
```

以下模式*不*被视为违规：

```css
div {}
```

```css
.foo .bar {}
```

```css
.foo.bar,
.lorem.ipsum {} /* 选择器列表中的每个选择器都将单独计算 */
```

```css
.foo .bar :not(.lorem.ipsum) {} /* `.lorem.ipsum` 在 `:not()` 里面，所以它是单独计算的 */
```
