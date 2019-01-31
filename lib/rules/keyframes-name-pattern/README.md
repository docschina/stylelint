# keyframes-name-pattern

指定关键帧名的模式。

```css
@keyframes slide-right {}
/**             ↑
 * 这种模式 */
```

## 选项

`regex|string`

字符串将被翻译成一个正则表达式，就像 `new RegExp(yourString)` ———— 所以一定要正确转义。

给定字符串：

```js
"foo-.+"
```

以下模式被视为违规：

```css
@keyframes foo {}
```

```css
@keyframes bar {}
```

```css
@keyframes FOO-bar {}
```

以下模式*不*被视为违规：

```css
@keyframes foo-bar {}
```
