# value-list-comma-newline-after

要求在值列表的逗号之后必须有换行符或不能有空白符。

```css
a { background-size: 0,
      0; }            ↑
/**                   ↑
 * 这个逗号之后的换行符 */
```

[命令行](../../../docs/user-guide/cli.md#自动修复错误)中的 `--fix` 选项可以自动修复此规则报告的大多数问题。

## 选项

`string`: `"always"|"always-multi-line"|"never-multi-line"`

### `"always"`

在逗号之后*必须*有一个换行符。

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
a { background-size: 0,
      0; }
```

### `"always-multi-line"`

在多行值列表的逗号之后*必须*有一个换行符。

以下模式被视为违规：

```css
a { background-size: 0
    , 0; }
```

以下模式*不*被视为违规：

```css
a { background-size: 0, 0; }
```

```css
a { background-size: 0,0; }
```

```css
a { background-size: 0,
      0; }
```

### `"never-multi-line"`

在多行值列表的逗号之后*不能*有空白符。

以下模式被视为违规：

```css
a { background-size: 0
      , 0; }
```

以下模式*不*被视为违规：

```css
a { background-size: 0,0; }
```

```css
a { background-size: 0, 0; }
```

```css
a { background-size: 0
      ,0; }
```
