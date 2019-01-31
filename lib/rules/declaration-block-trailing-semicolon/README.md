# declaration-block-trailing-semicolon

要求或禁止声明块的一个尾随分号。

```css
a { background: orange; color: pink; }
/**                                ↑
 *                    这个分号 */
```

尾随分号是声明块中的*最后一个*分号，它是可选的。

此规则忽略：

-   Less 的 mixins
-   行尾 `//` 注释
-   包含嵌套规则（或@规则）的声明块

[命令行](../../../docs/user-guide/cli.md#自动修复错误)中的 `--fix` 选项可以自动修复此规则报告的所有问题。

## 选项

`string`: `"always"|"never"`

### `"always"`

这里*必须*有一个尾随分号。

以下模式被视为违规：

```css
a { color: pink }
```

```css
a { background: orange; color: pink }
```

```css
a { @include foo }
```

以下模式*不*被视为违规：

```css
a { color: pink; }
```

```css
a { background: orange; color: pink; }
```

```css
a { @include foo; }
```

### `"never"`

这里*不能*有尾随分号。

以下模式被视为违规：

```css
a { color: pink; }
```

```css
a { background: orange; color: pink; }
```

以下模式*不*被视为违规：

```css
a { color: pink }
```

```css
a { background: orange; color: pink }
```
