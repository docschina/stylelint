# custom-media-pattern

指定自定义媒体查询名的模式。

```css
@custom-media --foo (max-width: 30em);
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
@custom-media --bar (min-width: 30em);
```

以下模式*不*被视为违规：

```css
@custom-media --foo-bar (min-width: 30em);
```
