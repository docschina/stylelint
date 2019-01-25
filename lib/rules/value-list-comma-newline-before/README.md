# value-list-comma-newline-before

要求在值列表的逗号之前必须有换行符或不能有空白符。

```css
  a { background-size: 0
    , 0; }
/** ↑
 * 这个逗号之前的换行符 */
```

## 选项

`string`: `"always"|"always-multi-line"|"never-multi-line"`

### `"always"`

在逗号之前*必须*有一个换行符。

以下模式被视为违规：

```css
a { background-size: 0,0; }
```

```css
a { background-size: 0,
      0; }
```

以下模式*不*被视为违规：

```css
a { background-size: 0
      , 0; }
```

### `"always-multi-line"`

在多行值列表的逗号之前*必须*有一个换行符。

以下模式被视为违规：

```css
a { background-size: 0,
      0; }
```

以下模式*不*被视为违规：

```css
a { background-size: 0, 0; }
```

```css
a { background-size: 0,0; }
```

```css
a { background-size: 0
      , 0; }
```

### `"never-multi-line"`

在多行值列表的逗号之前*不能*有空白符。

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
a { background-size: 0,
      0; }
```
