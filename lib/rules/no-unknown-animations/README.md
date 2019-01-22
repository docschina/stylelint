# no-unknown-animations

禁止未知的动画。

```css
a { animation-name: fancy-slide; }
/**                    ↑
 *                这个动画名称 */

a { animation: fancy-slide 2s linear; }
/**                    ↑
 *                 还有这个 */
```

此规则认为在同一源码中定义的 `@keyframes` 规则的标识符是已知的。

## 选项

### `true`

以下模式被视为违规：

```css
a { animation-name: fancy-slide; }
```

```css
a { animation: fancy-slide 2s linear; }
```

```css
a { animation-name: fancccy-slide; }
@keyframes fancy-slide {}
```

```css
a { animation: linear 100ms fancccy-slide; }
@keyframes fancy-slide {}
```

```css
a { animation-name: jump; }
@keyframes fancy-slide {}
```

以下模式*不*被视为违规：

```css
a { animation-name: fancy-slide; }
@keyframes fancy-slide {}
```

```css
@keyframes fancy-slide {}
a { animation-name: fancy-slide; }
```

```css
@keyframes fancy-slide {}
a { animation: fancy-slide 2s linear; }
```

```css
a { animation: 100ms steps(12, end) fancy-slide; }
@keyframes fancy-slide {}
```
