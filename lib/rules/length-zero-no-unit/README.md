# length-zero-no-unit

禁止零长度的单位。

```css
a { top: 0px; }
/**      ↑↑
 * 这个零和这种类型的长度单位 */
```

*长度*指距离测量。长度是*尺寸*，即*数字*后面紧跟*单位标识符*。但是对于零长度，单元标识符是可选的。长度单位是：`em`、`ex`、`ch`、`vw`、`vh`、`cm`、`mm`、`in`、`pt`、`pc`、`px`、`rem`、`vmin` 和 `vmax`。

[命令行](../../../docs/user-guide/cli.md#自动修复错误)中的 `--fix` 选项可以自动修复此规则报告的所有问题。

## 选项

### `true`

以下模式被视为违规：

```css
a { top: 0px }
```

```css
a { top: 0.000em }
```

以下模式*不*被视为违规：

```css
a { top: 0 } /* 没有单位 */
```

```css
a { transition-delay: 0s; } /* 尺寸 */
```

```css
a { top: 2in; }
```

```css
a { top: 1.001vh }
```

## 可选的辅助选项

### `ignore: ["custom-properties"]`

#### `"custom-properties"`

忽略自定义属性中零长度的单位。

以下模式*不*被视为违规：

```css
a { --x: 0px; }
```
