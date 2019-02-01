# selector-max-specificity

限制选择器的优先级。

```css
    .foo, #bar.baz span, #hoo { color: pink; }
/** ↑     ↑              ↑
 *   这些选择器中的每一个 */
```

访问[优先级计算器](https://specificity.keegan.st)，了解选择器优先级的可视化表示。

这条规则忽略了带有变量插值的选择器（``#{$var}`、`@{var}`、`$(var)`）。

此规则在计算一个选择器的优先级之前先解析选择器嵌套。[选择器列表](https://www.w3.org/TR/selectors4/#selector-list)中的每个选择器都将单独计算。

## 选项

`string`: 允许的最大优先级。

格式为 `"id,class,type"`，如 [W3C 选择器规范](https://drafts.csswg.org/selectors/#specificity-rules)中所述。

例如，使用 `"0,2,0"`：

以下模式被视为违规：

```css
#foo {}
```

```css
.foo .baz .bar {}
```

```css
.foo .baz {
  & .bar {}
}
```

```css
.foo {
  color: red;
  @nest .baz .bar & {
    color: blue;
  }
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
.foo div {
  & div a {}
}
```

```css
.foo {
  & .baz {}
}
```

```css
.foo {
  color: red;
  @nest .baz & {
    color: blue;
  }
}
```

## 可选的辅助选项

### `ignoreSelectors: ["/regex/", /regex/, "string"]`

给定：

```js
["0,2,0", {
  ignoreSelectors: [":global", ":local", "/my-/"]
}];
```

以下模式*不*被视为违规：

```css
:global(.foo) .bar {}
```

```css
:local(.foo.bar)
```

```css
:local(.foo, :global(.bar).baz)
```

以下模式被视为违规：

```css
:global(.foo) .bar.baz {}
```

```css
:local(.foo.bar.baz)
```

```css
:local(.foo, :global(.bar), .foo.bar.baz)
```
