# comment-empty-line-before

要求或禁止在注释之前的空行。

```css
a {}
           /* ← */
/* 注释 */ /* ↑ */
/**           ↑
*           这行 */
```

此规则忽略：

-   作为源码中第一个节点的注释
-   共享行的注释
-   使用 `//` 的单行注释（当您使用支持它们的自定义语法时）
-   选择器和值列表中的注释

[命令行](../../../docs/user-guide/cli.md#自动修复错误)中的 `--fix` 选项可以自动修复此规则报告的所有问题。我们建议启用 [`indentation`](../indentation/README.md) 规则，以便更好地使用此规则自动修复结果。

## 选项

`string`: `"always"|"never"`

### `"always"`

在注释之前*必须*有一个空行。

以下模式被视为违规：

```css
a {}
/* 注释 */
```

以下模式*不*被视为违规：

```css
a {}

/* 注释 */
```

```css
a {} /* 注释 */
```

### `"never"`

在注释之前*不能*有空行。

以下模式被视为违规：

```css
a {}

/* 注释 */
```

以下模式*不*被视为违规：

```css
a {}
/* 注释 */
```

```css
a {} /* 注释 */
```

## 可选的辅助选项

### `except: ["first-nested"]`

如果注释被嵌套并且是其父节点的第一个子节点则反转主选项。

例如，使用 `"always"`：

以下模式被视为违规：

```css
a {

  /* 注释 */
  color: pink;
}
```

以下模式*不*被视为违规：

```css
a {
  /* 注释 */
  color: pink;
}
```

### `ignore: ["after-comment", "stylelint-commands"]`

#### `"after-comment"`

如果注释紧跟在另一个注释之后则忽略。

例如，使用 `"always"`：

以下模式*不*被视为违规：

```css
a {
  background: pink;

  /* 注释 */
  /* 注释 */
  color: #eee;
}
```

```css
a {
  background: pink;

  /* 注释 */

  /* 注释 */
  color: #eee;
}
```

#### `"stylelint-commands"`

忽略将命令传递给 stylelint 的注释，例如 `/* stylelint-disable color-no-hex */`。

例如，使用 `"always"`：

以下模式被视为违规：

```css
a {
  background: pink;
  /* 并非 stylelint 命令 */
  color: #eee;
}
```

以下模式*不*被视为违规：

```css
a {
  background: pink;
  /* stylelint-disable color-no-hex */
  color: pink;
}
```
