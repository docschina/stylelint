# color-hex-length

指定 16 进制颜色的简写或扩写。

```css
a { color: #fff }
/**        ↑
 * 这个 16 进制颜色 */
```

[命令行](../../../docs/user-guide/cli.md#自动修复错误)中的 `--fix` 选项可以自动修复此规则报告的所有问题。

## 选项

`string`: `"short"|"long"`

### `"short"`

以下模式被视为违规：

```css
a { color: #ffffff; }
```

```css
a { color: #ffffffaa; }
```

以下模式*不*被视为违规：

```css
a { color: #fff; }
```

```css
a { color: #fffa; }
```

```css
a { color: #a4a4a4; }
```

### `"long"`

以下模式被视为违规：

```css
a { color: #fff; }
```

```css
a { color: #fffa; }
```

以下模式*不*被视为违规：

```css
a { color: #ffffff; }
```

```css
a { color: #ffffffaa; }
```
