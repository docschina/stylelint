# selector-max-compound-selectors

限制一个选择器中复合选择器的数量

```css
   div .bar[data-val] > a.baz + .boom > #lorem {}
/* ↑   ↑                ↑       ↑       ↑
   ↑   ↑                ↑       ↑       ↑
  Lv1 Lv2              Lv3     Lv4     Lv5  -- these are compound selectors */
```

A [compound selector](https://www.w3.org/TR/selectors4/#compound) is a chain of one or more simple (tag, class, ID, universal, attribute) selectors. If there is more than one compound selector in a complete selector, they will be separated by combinators (e.g. ` `, `+`, `>`). One reason why you might want to limit the number of compound selectors is described in the [SMACSS book](https://smacss.com/book/applicability).

此规则在计算一个选择器的深度之前先解析选择器嵌套。[选择器列表](https://www.w3.org/TR/selectors4/#selector-list)中的每个选择器都将单独计算。

`:not()` is considered one compound selector irrespective to the complexity of the selector inside it. The rule *does* process that inner selector, but does so separately, independent of the main selector.

## 选项

`int`：允许的最大复合选择器数量。

例如，使用 `3`：

以下模式被视为违规：

```css
.foo .bar .baz .lorem {}
```

```css
.foo .baz {
  & > .bar .lorem {}
}
```

以下模式*不*被视为违规：

```css
div {}
```

```css
.foo div {}
```

```css
#foo #bar > #baz {}
```

```css
.foo + div :not (a b ~ c) {} /* `a b ~ c`:not()` 里面，所以它是单独计算的 */
```
