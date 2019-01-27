# selector-max-attribute

限制一个选择器中属性选择器的数量

```css
    [rel="external"] {}
/** ↑
 * 这种选择器 */
```

此规则在计算属性选择器的数量之前先解析选择器嵌套。[选择器列表](https://www.w3.org/TR/selectors4/#selector-list)中的每个选择器都将单独计算。

`:not()` 伪类的内容也是单独计算的。此规则将其参数视为一个独立的选择器，结果不计入整个选择器的总数。

## 选项

`int`：允许的最大属性选择器数量。

例如，使用 `2`：

以下模式被视为违规：

```css
[type="number"][name="quality"][data-attribute="value"] {}
```

```css
[type="number"][name="quality"][disabled] {}
```

```css
[type="number"][name="quality"] {
  & [data-attribute="value"] {}
}
```

```css
[type="number"][name="quality"] {
  & [disabled] {}
}
```

```css
[type="number"][name="quality"] {
  & > [data-attribute="value"] {}
}
```

```css
/* `[type="text"][data-attribute="value"][disabled]` 在 `:not()` 里面，所以它是单独计算的 */
input:not([type="text"][data-attribute="value"][disabled]) {}
```

以下模式*不*被视为违规：

```css
[type="text"] {}
```

```css
[type="text"][name="message"] {}
```

```css
[type="text"][disabled]
```

```css
/* 选择器列表中的每个选择器都将单独计算 */
[type="text"][name="message"],
[type="number"][name="quality"] {}
```

```css
/* `[disabled]` 在 `:not()` 里面，所以它是单独计算的 */
[type="text"][name="message"]:not([disabled]) {}
```

## 可选的辅助选项

### `ignoreAttributes: ["/regex/", /regex/, "string"]`

给定：

```js
["/^my-/", "dir"]
```

例如，使用 `0`。

以下模式*不*被视为违规：

```css
[dir] [my-attr] {}
```

```css
[dir] [my-other-attr] {}
```
