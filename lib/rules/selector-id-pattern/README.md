# selector-id-pattern

指定 ID 选择器的模式。

```css
.foo, #bar.baz a, #hoo[disabled] { color: pink; }
/**   ↑           ↑
 * 这些 ID 选择器 */
```

## 选项

`regex|string`

字符串将被翻译成一个正则表达式，就像 `new RegExp(yourString)` ———— 所以一定要正确转义。

此规则将检查 *`#` 之后*的选择器值。无需在模式中包含 `#`。

给定字符串：

```js
"foo-[a-z]+"
```

以下模式被视为违规：

```css
#foop {}
```

```css
#foo-BAR {}
```

```css
div > .zing + #foo-BAR {}
```

以下模式*不*被视为违规：

```css
#foo-bar {}
```

```css
div > .zing + #foo-bar {}
```

```css
.foop {}
```

```css
[foo='bar'] {}
```
