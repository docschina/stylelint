# function-whitespace-after

要求或禁止函数之后的空白符。

```css
a { transform: translate(1, 1) scale(3); }
/**                           ↑
 *                   这个空白符 */
```

如果下一个字符是 `,`、`)`、`/` 或 `}`，则此规则不会在 `)` 之后立即检查空格，从而允许下面举例说明的一些模式。

[命令行](../../../docs/user-guide/cli.md#自动修复错误)中的 `--fix` 选项可以自动修复此规则报告的所有问题。

## 选项

`string`: `"always"|"never"`

### `"always"`

在函数之后*必须*有空白符。

以下模式被视为违规：

```css
a { transform: translate(1, 1)scale(3); }
```

以下模式*不*被视为违规：

```css
a { transform: translate(1, 1) scale(3); }
```

```css
a { transform: translate(1, 1)     scale(3); }
```

```css
a {
  transform:
    translate(1, 1)
    scale(3);
}
```

```css
/* 注意两个闭括号之间没有空格 */
a { top: calc(1 * (1 + 3)); }
```

```css
/* 注意 )，在闭括号后没有空格 */
a { padding: calc(1 * 2px), calc(2 * 5px); }
```

```scss
/* 注意 )}，在闭括号后没有空格 */
a {
  max-height: #{($line-height) * ($lines-to-show)}em;
}
```

```less
/* 注意 )}，在闭括号后没有空格 */
a {
  max-height: ((@line-height) * (@lines-to-show))em;
}
```

### `"never"`

在函数之后*不能*有空白符。

以下模式被视为违规：

```css
a { transform: translate(1, 1) scale(3); }
```

以下模式*不*被视为违规：

```css
a { transform: translate(1, 1)scale(3); }
```
