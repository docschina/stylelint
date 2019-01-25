# selector-combinator-space-before

要求在组合选择器之前必须有一个空格或不能有空白符。

```css
  a > b + c ~ d e >>> f { color: pink; }
/** ↑   ↑   ↑  ↑  ↑
 * 这些是组合选择器 */
```

组合选择器用于将几个不同的选择器组合成新的和更具体的选择器。有几种类型的组合选择器，包括：子（`>`），紧邻兄弟（`+`），一般兄弟（`~`）和后代（由两个选择器之间的空格表示）。

根据此规则*不*检查后代选择器。

此外，不检查 `:nth-*()` 参数内的 `+` 和 `-` 符号（例如 `a:nth-child(2n+1)`）。

[命令行](../../../docs/user-guide/cli.md#自动修复错误)中的 `--fix` 选项可以自动修复此规则报告的所有问题。

## 选项

`string`: `"always"|"never"`

### `"always"`

在组合选择器之前*必须*有一个空格。

以下模式被视为违规：

```css
a+ b { color: pink; }
```

```css
a>b { color: pink; }
```

以下模式*不*被视为违规：

```css
a + b { color: pink; }
```

```css
a >b { color: pink; }
```

### `"never"`

在组合选择器之前*不能*有空白符。

以下模式被视为违规：

```css
a + b { color: pink; }
```

```css
a >b { color: pink; }
```

以下模式*不*被视为违规：

```css
a+ b { color: pink; }
```

```css
a>b { color: pink; }
```
