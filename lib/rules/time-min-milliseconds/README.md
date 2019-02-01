# time-min-milliseconds

指定时间值的最小毫秒数。

```css
a { animation: slip-n-slide 150ms linear; }
/**                         ↑
 *                       这个时间 */
```

这条规则检查 `transition-duration`、`transition-delay`、`animation-duration`、`animation-delay` 中的正数，以及它们在 `transition` 和 `animation` 简写中声明的那些时间。

## 选项

`int`: 时间值的最小毫秒数。

例如，使用 `100`：

以下模式被视为违规：

```css
a { animation: 80ms; }
```

```css
a { transition-duration: 0.08s; }
```

```css
a { transition: background-color 6ms linear; }
```

```css
a { animation-delay: 0.01s; }
```

以下模式*不*被视为违规：

```css
a { animation: 8s; }
```

```css
a { transition-duration: 0.8s; }
```

```css
a { transition: background-color 600ms linear; }
```

```css
a { animation-delay: 1s; }
```
