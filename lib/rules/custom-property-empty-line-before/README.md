# custom-property-empty-line-before

要求或禁止在自定义属性之前的空行。

```css
a {
  top: 10px;
                          /* ← */
  --foo: pink;            /* ↑ */
}                         /* ↑ */
/**                          ↑
 *                          这行 */
```

[命令行](../../../docs/user-guide/cli.md#自动修复错误)中的 `--fix` 选项可以自动修复此规则报告的所有问题。我们建议启用 [`indentation`](../indentation/README.md) 规则，以便更好地使用此规则自动修复结果。

## 选项

`string`: `"always"|"never"`

### `"always"`

以下模式被视为违规：

```css
a {
  top: 10px;
  --foo: pink;
  --bar: red;
}
```

以下模式*不*被视为违规：

```css
a {
  top: 10px;

  --foo: pink;

  --bar: red;
}
```

### `"never"`

以下模式被视为违规：

```css
a {
  top: 10px;

  --foo: pink;

  --bar: red;
}
```

```css
a {

  --foo: pink;
  --bar: red;
}
```

以下模式*不*被视为违规：

```css
a {
  top: 10px;
  --foo: pink;
  --bar: red;
}
```

```css
a {
  --foo: pink;
  --bar: red;
}
```

## 可选的辅助选项

### `except: ["after-comment", "after-custom-property", "first-nested"]`

#### `"after-comment"`

如果自定义属性紧跟在注释之后则反转主选项。

共享行注释不会触发此选项。

例如，使用 `"always"`：

以下模式被视为违规：

```css
a {

  --foo: pink;
  /* 注释 */

  --bar: red;
}
```

```css
a {

  --foo: pink; /* 注释 */
  --bar: red;
}
```

以下模式*不*被视为违规：

```css
a {

  --foo: pink;
  /* 注释 */
  --bar: red;
}
```

```css
a {

  --foo: pink; /* 注释 */

  --bar: red;
}
```

#### `"after-custom-property"`

如果自定义属性紧跟在另一个自定义属性之后则反转主选项。

共享行注释不会影响此选项。

例如，使用 `"always"`：

以下模式被视为违规：

```css
a {

  --foo: pink;

  --bar: red;
}
```

```css
a {

  --foo: pink; /* 注释 */

  --bar: red;
}
```

以下模式*不*被视为违规：

```css
a {

  --foo: pink;
  --bar: red;
}
```

```css
a {

  --foo: pink; /* 注释 */
  --bar: red;
}
```

#### `"first-nested"`

如果自定义属性被嵌套并且是其父节点的第一个子节点则反转主选项。

例如，使用 `"always"`：

以下模式被视为违规：

```css
a {

  --foo: pink;

  --bar: red;
}
```

以下模式*不*被视为违规：

```css
a {
  --foo: pink;

  --bar: red;
}
```

### `ignore: ["after-comment", "first-nested", "inside-single-line-block"]`

#### `"after-comment"`

如果自定义属性紧跟在注释之后则忽略。

例如，使用 `"always"`：

以下模式*不*被视为违规：

```css
a {
  /* 注释 */
  --foo: pink;
}
```

#### `"first-nested"`

如果自定义属性被嵌套并且是其父节点的第一个子节点则忽略。

例如，使用 `"always"`：

以下模式*不*被视为违规：

```css
a {
  --foo: pink;

  --bar: red;
}
```

#### `"inside-single-line-block"`

忽略单行块内的自定义属性。

例如，使用 `"always"`：

以下模式*不*被视为违规：

```css
a { --foo: pink; --bar: red; }
```
