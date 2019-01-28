# selector-descendant-combinator-no-non-space

禁止后代选择器使用非空格字符。

```css
.foo .bar .baz {}
/** ↑    ↑
* 这些后代选择器 */
```

此规则确保后代选择器仅使用单个空格，不使用制表符，换行符或多个空格。

[命令行](../../../docs/user-guide/cli.md#自动修复错误)中的 `--fix` 选项可以自动修复此规则报告的大多数问题。

## 选项

### `true`

以下模式被视为违规：

```css
.foo  .bar {}
```

```css
.foo
.bar {}
```

以下模式*不*被视为违规：

```css
.foo .bar {}
```
