# function-parentheses-newline-inside

要求在函数的括号内侧必须有换行符或不能有空白符。

```css
  a {
    transform: translate(
      1,             /* ↑ */
      1              /* ↑ */
    );               /* ↑ */
  }                  /* ↑ */
/** ↑                   ↑
 *  这两个括号内侧的换行符 */
```

[命令行](../../../docs/user-guide/cli.md#自动修复错误)中的 `--fix` 选项可以自动修复此规则报告的所有问题。

## 选项

`string`: `"always"|"always-multi-line"|"never-multi-line"`

### `"always"`

在括号内侧*必须*有一个换行符。

以下模式被视为违规：

```css
a { transform: translate(1, 1); }
```

```css
a { transform: translate(1,
  1
  ); }
```

以下模式*不*被视为违规：

```css
a {
  transform: translate(
    1, 1
  );
}
```

```css
a {
  transform: translate(
    1,
    1
  );
}
```

### `"always-multi-line"`

在多行函数的括号内侧*必须*有一个换行符。

以下模式被视为违规：

```css
a { transform: translate(1,
  1) }
```

以下模式*不*被视为违规：

```css
a { transform: translate(1, 1) }
```

```css
a { transform: translate( 1, 1 ) }
```

```css
a {
  transform: translate(
    1, 1
  );
}
```

```css
a {
  transform: translate(
    1,
    1
  );
}
```

### `"never-multi-line"`

以下模式被视为违规：

```css
a {
  transform: translate(
    1, 1
  );
}
```

```css
a {
  transform: translate(
    1,
    1
  );
}
```

以下模式*不*被视为违规：

```css
a { transform: translate(1, 1) }
```

```css
a { transform: translate( 1, 1 ) }
```

```css
a { transform: translate(1,
  1) }
```
