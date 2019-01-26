# selector-pseudo-class-parentheses-space-inside

Require a single space or disallow whitespace on the inside of the parentheses within pseudo-class selectors.

```css
input:not( [type="submit"] ) {}
/**      ↑                 ↑
 * 这两个括号内侧的空白符 */
```

[命令行](../../../docs/user-guide/cli.md#自动修复错误)中的 `--fix` 选项可以自动修复此规则报告的所有问题。

## 选项

`string`: `"always"|"never"`

### `"always"`

在括号内侧*必须*有一个空格。

以下模式被视为违规：

```css
input:not([type="submit"]) {}
```

```css
input:not([type="submit"] ) {}
```

以下模式*不*被视为违规：

```css
input:not( [type="submit"] ) {}
```

### `"never"`

在括号内侧*不能*有空白符。

以下模式被视为违规：

```css
input:not( [type="submit"] ) {}
```

```css
input:not( [type="submit"]) {}
```

以下模式*不*被视为违规：

```css
input:not([type="submit"]) {}
```
