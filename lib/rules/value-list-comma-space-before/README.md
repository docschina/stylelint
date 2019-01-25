# value-list-comma-space-before

要求在值列表的逗号之前必须有一个空格或不能有空白符。

```css
a { background-size: 0 ,0; }
/**                    ↑
 *           这个逗号之前的空白符 */
```

[命令行](../../../docs/user-guide/cli.md#自动修复错误)中的 `--fix` 选项可以自动修复此规则报告的大多数问题。

## 选项

`string`: `"always"|"never"|"always-single-line"|"never-single-line"`

### `"always"`

在逗号之前*必须*有一个空格。

以下模式被视为违规：

```css
a { background-size: 0,0; }
```

```css
a { background-size: 0
      , 0; }
```

以下模式*不*被视为违规：

```css
a { background-size: 0 ,0; }
```

```css
a { background-size: 0 ,
      0; }
```

### `"never"`

在逗号之前*不能*有空白符。

以下模式被视为违规：

```css
a { background-size: 0 ,0; }
```

```css
a { background-size: 0 ,
      0; }
```

以下模式*不*被视为违规：

```css
a { background-size: 0,0; }
```

```css
a { background-size: 0,
      0; }
```

### `"always-single-line"`

在单行值列表的逗号之前*必须*有一个空格。

以下模式被视为违规：

```css
a { background-size: 0,0; }
```

以下模式*不*被视为违规：

```css
a { background-size: 0 ,0; }
```

```css
a { background-size: 0 ,
      0; }
```

```css
a { background-size: 0
      , 0; }
```

### `"never-single-line"`

在单行值列表的逗号之前*不能*有空白符。

以下模式被视为违规：

```css
a { background-size: 0 ,0; }
```

以下模式*不*被视为违规：

```css
a { background-size: 0,0; }
```

```css
a { background-size: 0,
      0; }
```

```css
a { background-size: 0 ,
      0; }
```
