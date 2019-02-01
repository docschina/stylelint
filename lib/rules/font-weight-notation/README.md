# font-weight-notation

要求 `font-weight` 使用数字或命名（如果可能）值。此外，当需要命名值时，要求名称有效。

```css
a { font-weight: bold }
/**              ↑
 *   这个表示法 */

a { font: italic small-caps 600 16px/3 cursive; }
/**                         ↑
*                还有这种表示法也是如此 */
```

有效的字体粗细命名是 `normal`、`bold`、`bolder` 和 `lighter`。

此规则忽略 `$sass`、`@less` 和 `var(--custom-property)` 变量语法

## 选项

`string`: `"numeric"|"named-where-possible"`

### `"numeric"`

`font-weight` 值*必须*是数量。

以下模式被视为违规：

```css
a { font-weight: bold; }
```

```css
a { font: italic normal 20px sans-serif; }
```

以下模式*不*被视为违规：

```css
a { font-weight: 700; }
```

```css
a { font: italic 400 20px; }
```

### `"named-where-possible"`

当适当的关键字可用时，`font-weight` 的值*必须*是关键字。

这意味着只有 `400` 和 `700` 将被拒绝，因为这些是唯一有等价关键字的数字（`normal` 和 `bold`）。

以下模式被视为违规：

```css
a { font-weight: 700; }
```

```css
a { font: italic 400 20px sans-serif; }
```

以下模式*不*被视为违规：

```css
a { font-weight: bold; }
```

```css
a { font: italic normal 20px sans-serif; }
```

## 可选的辅助选项

### `ignore: ["relative"]`

忽略[*相对*](https://drafts.csswg.org/css-fonts/#font-weight-prop)关键字名称 `bolder` 和 `lighter`。

以下模式*不*被视为违规：

```css
a { font-weight: 400; }
a b { font-weight: lighter; }
```
