# selector-list-comma-newline-before

要求在选择器列表的逗号之前必须有换行符或不能有空白符。

```css
    a
    , b { color: pink; }
/** ↑
 * 这个逗号之前的换行符 */
```

[命令行](../../../docs/user-guide/cli.md#自动修复错误)中的 `--fix` 选项可以自动修复此规则报告的所有问题。

## 选项

`string`: `"always"|"always-multi-line"|"never-multi-line"`

### `"always"`

在逗号之前*必须*有一个换行符。

以下模式被视为违规：

```css
a, b { color: pink; }
```

```css
a,
b { color: pink; }
```

以下模式*不*被视为违规：

```css
a
, b { color: pink; }
```

```css
a
,b { color: pink; }
```

### `"always-multi-line"`

在多行选择器列表的逗号之前*必须*有一个换行符。

以下模式被视为违规：

```css
a,
b { color: pink; }
```

以下模式*不*被视为违规：

```css
a, b { color: pink; }
```

```css
a
,b { color: pink; }
```

```css
a
,
b { color: pink; }
```

### `"never-multi-line"`

在多行选择器列表的逗号之前*不能*有空白符。

以下模式被视为违规：

```css
a
, b { color: pink; }
```

```css
a
,
b { color: pink; }
```

以下模式*不*被视为违规：

```css
a,b { color: pink; }
```

```css
a,
b { color: pink; }
```
