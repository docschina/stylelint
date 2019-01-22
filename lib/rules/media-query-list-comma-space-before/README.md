# media-query-list-comma-space-before

Require a single space or disallow whitespace before the commas of media query lists.

```css
@media screen and (color) ,projection and (color) {}
/**                       ↑
 *             These commas */
```

The `--fix` option on the [command line](../../../docs/user-guide/cli.md#autofixing-errors) can automatically fix all of the problems reported by this rule.

## 选项

`string`: `"always"|"never"|"always-single-line"|"never-single-line"`

### `"always"`

There *must always* be a single space before the commas.

以下模式被视为违规：

```css
@media screen and (color),projection and (color) {}
```

```css
@media screen and (color)
,projection and (color) {}
```

以下模式*不*被视为违规：

```css
@media screen and (color) ,projection and (color) {}
```

```css
@media screen and (color) ,
projection and (color) {}
```

### `"never"`

There *must never* be whitespace before the commas.

以下模式被视为违规：

```css
@media screen and (color) ,projection and (color) {}
```

```css
@media screen and (color)
, projection and (color) {}
```

以下模式*不*被视为违规：

```css
@media screen and (color),projection and (color) {}
```

```css
@media screen and (color),
projection and (color) {}
```

### `"always-single-line"`

There *must always* be a single space before the commas in single-line media query lists.

以下模式被视为违规：

```css
@media screen and (color),projection and (color) {}
```

以下模式*不*被视为违规：

```css
@media screen and (color) ,projection and (color) {}
```

```css
@media screen and (color)
, projection and (color) {}
```

```css
@media screen and (color)
,projection and (color) {}
```

### `"never-single-line"`

There *must never* be whitespace before the commas in single-line media query lists.

以下模式被视为违规：

```css
@media screen and (color) , projection and (color) {}
```

以下模式*不*被视为违规：

```css
@media screen and (color),projection and (color) {}
```

```css
@media screen and (color)
,projection and (color) {}
```

```css
@media screen and (color)
, projection and (color) {}
```
