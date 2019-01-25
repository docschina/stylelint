# media-feature-colon-space-after

要求在媒体功能的冒号之后必须有一个空格或不能有空白符。

```css
@media (max-width: 600px) {}
/**              ↑
 * 这个冒号之后的空白符 */
```

[命令行](../../../docs/user-guide/cli.md#自动修复错误)中的 `--fix` 选项可以自动修复此规则报告的所有问题。

## 选项

`string`: `"always"|"never"`

### `"always"`

在冒号之后*必须*有一个空格。

以下模式被视为违规：

```css
@media (max-width:600px) {}
```

```css
@media (max-width :600px) {}
```

以下模式*不*被视为违规：

```css
@media (max-width: 600px) {}
```

```css
@media (max-width : 600px) {}
```

### `"never"`

在冒号之后*不能*有空白符。

以下模式被视为违规：

```css
@media (max-width: 600px) {}
```

```css
@media (max-width : 600px) {}
```

以下模式*不*被视为违规：

```css
@media (max-width:600px) {}
```

```css
@media (max-width :600px) {}
```
