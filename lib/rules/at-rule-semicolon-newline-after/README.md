# at-rule-semicolon-newline-after

要求在 @规则的分号之后必须有换行符。

```css
@import url("x.css");
@import url("y.css");
/**                 ↑
 *        这些分号之后的换行符 */
```

此规则允许在行尾注释之后跟换行符。例如：

```css
@import url("x.css"); /* 行尾注释 */

a {}
```

[命令行](../../../docs/user-guide/cli.md#自动修复错误)中的 `--fix` 选项可以自动修复此规则报告的所有问题。

## 选项

`string`: `"always"`

### `"always"`

在分号之后*必须*有一个换行符。

以下模式被视为违规：

```css
@import url("x.css"); @import url("y.css");
```

```css
@import url("x.css"); a {}
```

以下模式*不*被视为违规：

```css
@import url("x.css");
@import url("y.css");
```

```css
@import url("x.css"); /* 行尾注释 */
a {}
```

```css
@import url("x.css");

a {}
```
