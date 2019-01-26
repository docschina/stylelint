# media-query-list-comma-newline-before

要求在媒体查询列表的逗号之前必须有换行符或不能有空白符。

```css
    @media screen and (color)
    , projection and (color) {}
/** ↑
 * 这些逗号 */
```

## 选项

`string`: `"always"|"always-multi-line"|"never-multi-line"`

### `"always"`

在逗号之前*必须*有一个换行符。

以下模式被视为违规：

```css
@media screen and (color), projection and (color) {}
```

```css
@media screen and (color),
projection and (color) {}
```

以下模式*不*被视为违规：

```css
@media screen and (color)
,projection and (color) {}
```

```css
@media screen and (color)
,
projection and (color) {}
```

### `"always-multi-line"`

在多行媒体查询列表的逗号之前*必须*有一个换行符。

以下模式被视为违规：

```css
@media screen and (color),
projection and (color) {}
```

以下模式*不*被视为违规：

```css
@media screen and (color), projection and (color) {}
```

```css
@media screen and (color)
,projection and (color) {}
```

```css
@media screen and (color)
,
projection and (color) {}
```

### `"never-multi-line"`

在多行媒体查询列表的逗号之前*不能*有空白符。

以下模式被视为违规：

```css
@media screen and (color)
,projection and (color) {}
```

```css
@media screen and (color)
,
projection and (color) {}
```

以下模式*不*被视为违规：

```css
@media screen and (color), projection and (color) {}
```

```css
@media screen and (color),
projection and (color) {}
```
