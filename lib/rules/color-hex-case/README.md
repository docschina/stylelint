# color-hex-case

指定 16 进制颜色的大小写。

```css
a { color: #fff }
/**        ↑
 * 这个 16 进制颜色 */
```

[命令行](../../../docs/user-guide/cli.md#自动修复错误)中的 `--fix` 选项可以自动修复此规则报告的所有问题。

## 选项

`string`: `"lower"|"upper"`

### `"lower"`

以下模式被视为违规：

```css
a { color: #FFF; }
```

以下模式*不*被视为违规：

```css
a { color: #000; }
```

```css
a { color: #fff; }
```

### `"upper"`

以下模式被视为违规：

```css
a { color: #fff; }
```

以下模式*不*被视为违规：

```css
a { color: #000; }
```

```css
a { color: #FFF; }
```
