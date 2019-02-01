# selector-class-pattern

指定类选择器的模式。

```css
    .foo, #bar.baz span, #hoo[disabled] { color: pink; }
/** ↑         ↑
 * 这些类选择器 */
```

此规则忽略非输出 Less mixin 定义和调用 Less mixins。

转义选择器（例如 `.u-size-11\/12\@sm`）被解析为两次转义（例如 `.u-size-11\\/12\\@sm`）。您的正则表达式应该考虑到这一点。

## 选项

`regex|string`

字符串将被翻译成一个正则表达式，就像 `new RegExp(yourString)` ———— 所以一定要正确转义。

此规则将检查 *`.` 之后*的选择器值。无需在模式中包含 `.`。

给定字符串：

```js
"foo-[a-z]+"
```

以下模式被视为违规：

```css
.foop {}
```

```css
.foo-BAR {}
```

```css
div > #zing + .foo-BAR {}
```

以下模式*不*被视为违规：

```css
.foo-bar {}
```

```css
div > #zing + .foo-bar {}
```

```css
#foop {}
```

```css
[foo='bar'] {}
```

```less
.foop() {}
```

```less
.foo-bar {
  .foop;
}
```

## 可选的辅助选项

### `resolveNestedSelectors: true | false` (default: `false`)

此选项将解析使用 `&` 插值的嵌套选择器。

例如，使用 `true`。

给定字符串：

```js
"^[A-Z]+$"
```

以下模式被视为违规：

```css
.A {
  &__B {} /* 解析为 ".A__B" */
}
```

以下模式*不*被视为违规：

```css
.A {
  &B {} /* 解析为 ".AB" */
}
```
