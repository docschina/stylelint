# declaration-empty-line-before

要求或禁止在声明之前的空行。

```css
a {
  --foo: pink;
             /* ← */
  top: 15px; /* ↑ */
}            /* ↑ */
/**             ↑
 *             这行 */
```

此规则仅适用于标准属性声明。对于自定义属性声明，请使用 [`custom-property-empty-line-before`](../custom-property-empty-line-before/README.md) 规则。

[命令行](../../../docs/user-guide/cli.md#自动修复错误)中的 `--fix` 选项可以自动修复此规则报告的所有问题。我们建议启用 [`indentation`](../indentation/README.md) 规则，以便更好地使用此规则自动修复结果。

## 选项

`string`: `"always"|"never"`

### `"always"`

以下模式被视为违规：

```css
a {
  --foo: pink;
  top: 5px;
}
```

```css
a {
  bottom: 15px;
  top: 5px;
}
```

以下模式*不*被视为违规：

```css
a {
  --foo: pink;

  top: 5px;
}
```

```css
a {

  bottom: 15px;

  top: 5px;
}
```

### `"never"`

以下模式被视为违规：

```css
a {
  --foo: pink;

  bottom: 15px;
}
```

```css
a {

  bottom: 15px;

  top: 5px;
}
```

以下模式*不*被视为违规：

```css
a {
  --foo: pink;
  bottom: 15px;
}
```

```css
a {
  bottom: 15px;
  top: 5px;
}
```

## 可选的辅助选项

### `except: ["after-comment", "after-declaration", "first-nested"]`

#### `"after-comment"`

如果声明紧跟在注释之后则反转主选项。

共享行注释不会触发此选项。

例如，使用 `"always"`：

以下模式被视为违规：

```css
a {
  /* 注释 */

  top: 5px;
}
```

```css
a {
  bottom: 5px; /* 注释 */
  top: 5px;
}
```

以下模式*不*被视为违规：

```css
a {
  /* 注释 */
  top: 5px;
}

```

```css
a {
  bottom: 5px; /* 注释 */

  top: 5px;
}

```

#### `"after-declaration"`

如果声明紧跟在另一个声明之后则反转主选项。

共享行注释不会影响此选项。

例如，使用 `"always"`：

以下模式被视为违规：

```css
a {

  bottom: 15px;

  top: 5px;
}
```

```css
a {

  bottom: 15px; /* 注释 */

  top: 5px;
}
```

以下模式*不*被视为违规：

```css
a {

  bottom: 15px;
  top: 5px;
}
```

```css
a {

  bottom: 15px; /* 注释 */
  top: 5px;
}
```

#### `"first-nested"`

如果声明被嵌套并且是其父节点的第一个子节点则反转主选项。

例如，使用 `"always"`：

以下模式被视为违规：

```css
a {

  bottom: 15px;

  top: 5px;
}
```

以下模式*不*被视为违规：

```css
a {
  bottom: 15px;

  top: 5px;
}
```

### `ignore: ["after-comment", "after-declaration", "first-nested", "inside-single-line-block"]`

#### `"after-comment"`

如果声明紧跟在注释之后则忽略。

例如，使用 `"always"`：

以下模式*不*被视为违规：

```css
a {
  /* 注释 */
  bottom: 15px;
}
```

#### `"after-declaration"`

如果声明紧跟在另一个声明之后则忽略。

例如，使用 `"always"`：

以下模式*不*被视为违规：

```css
a {

  bottom: 15px;
  top: 15px;
}
```

```css
a {

  bottom: 15px;

  top: 15px;
}
```

```css
a {

  color: orange;
  text-decoration: none;

  bottom: 15px;
  top: 15px;
}
```

#### `"first-nested"`

如果声明被嵌套并且是其父节点的第一个子节点则忽略。

例如，使用 `"always"`：

以下模式*不*被视为违规：

```css
a {
  bottom: 15px;

  top: 5px;
}
```

#### `"inside-single-line-block"`

忽略单行块内的声明。

例如，使用 `"always"`：

以下模式*不*被视为违规：

```css
a { bottom: 15px; top: 5px; }
```
