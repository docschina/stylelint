# selector-list-comma-space-after

要求在选择器列表的逗号之后必须有一个空格或不能有空白符。

```css
   a, b { color: pink; }
/** ↑
 * 这个逗号之后的空白符 */
```

[命令行](../../../docs/user-guide/cli.md#自动修复错误)中的 `--fix` 选项可以自动修复此规则报告的所有问题。

## 选项

`string`: `"always"|"never"|"always-single-line"|"never-single-line"`

### `"always"`

在逗号之后*必须*有一个空格。

以下模式被视为违规：

```css
a,b { color: pink; }
```

```css
a ,b { color: pink; }
```

以下模式*不*被视为违规：

```css
a, b { color: pink; }
```

```css
a , b { color: pink; }
```

### `"never"`

在逗号之后*不能*有空白符。

以下模式被视为违规：

```css
a, b { color: pink; }
```

```css
a , b { color: pink; }
```

以下模式*不*被视为违规：

```css
a,b { color: pink; }
```

```css
a ,b { color: pink; }
```

### `"always-single-line"`

在单行选择器列表的逗号之后*必须*有一个空格。

以下模式被视为违规：

```css
a,b { color: pink; }
```

以下模式*不*被视为违规：

```css
a
,b { color: pink; }
```

### `"never-single-line"`

在单行选择器列表的逗号之后*不能*有空格。

以下模式被视为违规：

```css
a, b { color: pink; }
```

以下模式*不*被视为违规：

```css
a
, b { color: pink; }
```
