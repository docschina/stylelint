# declaration-colon-space-before

要求在声明块的冒号之前必须有一个空格或不能有空白符。

```css
a { color :pink }
/**       ↑
 * 这个冒号之前的空白符 */
```

[命令行](../../../docs/user-guide/cli.md#自动修复错误)中的 `--fix` 选项可以自动修复此规则报告的所有问题。

## 选项

`string`: `"always"|"never"`

### `"always"`

在冒号之前*必须*有一个空格。

以下模式被视为违规：

```css
a { color: pink }
```

```css
a { color:pink }
```

以下模式*不*被视为违规：

```css
a { color : pink }
```

```css
a { color :pink }
```

### `"never"`

在冒号之前*不能*有空白符。

以下模式被视为违规：

```css
a { color : pink }
```

```css
a { color :pink }
```

以下模式*不*被视为违规：

```css
a { color: pink }
```

```css
a { color:pink }
```
