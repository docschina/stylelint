# selector-max-type

限制一个选择器中类型选择器的数量

```css
    a {}
/** ↑
 * 这种选择器 */
```

此规则在计算类型选择器的数量之前先解析选择器嵌套。[选择器列表](https://www.w3.org/TR/selectors4/#selector-list)中的每个选择器都将单独计算。

`:not()` 伪类的内容也是单独计算的。此规则将其参数视为一个独立的选择器，结果不计入整个选择器的总数。

## 选项

`int`：允许的最大类型选择器数量。

例如，使用 `2`：

以下模式被视为违规：

```css
div a span {}
```

```css
div a {
  & span {}
}
```

```css
div a {
  & > a {}
}
```

以下模式*不*被视为违规：

```css
div {}
```

```css
div a {}
```

```css
.foo div a {}
```

```css
div.foo a {}
```

```css
/* 选择器列表中的每个选择器都将单独计算 */
div,
a span {}
```

```css
/* `span` 在 `:not()` 里面，所以它是单独计算的 */
div a .foo:not(span) {}
```

以下模式*不*被视为违规：

## 可选的辅助选项

### `ignore: ["child", "compounded", "descendant", "next-sibling"]`

#### `"child"`

不计算子类型选择器。

例如，使用 `2`：

以下模式*不*被视为违规：

```css
div span > a {}
```

```css
#bar div span > a {}
```

#### `"compounded"`

不计算复合类型选择器————即与其他选择器链接的类型选择器。

例如，使用 `2`：

以下模式*不*被视为违规：

```css
div span a.foo {}
```

```css
div span a#bar {}
```

#### `"descendant"`

不计算后代类型选择器。

例如，使用 `2`：

以下模式*不*被视为违规：

```css
.foo div span a {}
```

```css
#bar div span a {}
```

#### `"next-sibling"`

不计算紧邻兄弟类型选择器。

例如，使用 `2`：

以下模式*不*被视为违规：

```css
div a + span {}
```

```css
#bar + div + span + a + span {}
```

### `ignoreTypes: ["/regex/", /regex/, "string"]`

给定：

```js
["/^my-/", "custom"]
```

例如，使用 `2`。

以下模式*不*被视为违规：

```css
div a custom {}
```

```css
div a my-type {}
```

```css
div a my-other-type {}
```
