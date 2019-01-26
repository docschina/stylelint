# rule-empty-line-before

要求或禁止在规则之前的空行。

```css
a {}
      /* ← */
b {}  /* ↑ */
/**      ↑
 *      这行 */
```

此规则忽略作为源中第一个节点的规则。

[命令行](../../../docs/user-guide/cli.md#自动修复错误)中的 `--fix` 选项可以自动修复此规则报告的所有问题。我们建议启用 [`indentation`](../indentation/README.md) 规则，以便更好地使用此规则自动修复结果。

## 选项

`string`: `"always"|"never"|"always-multi-line"|"never-multi-line"`

### `"always"`

在规则之前*必须*有一个空行。

以下模式被视为违规：

```css
a {} b {}
```

```css
a {}
b {}
```

以下模式*不*被视为违规：

```css
a {}

b {}
```

### `"never"`

在规则之前*不能*有空行。

以下模式被视为违规：

```css
a {}

b {}
```

以下模式*不*被视为违规：

```css
a {} b {}
```

```css
a {}
b {}
```

### `"always-multi-line"`

在多行规则之前*必须*有一个空行。

以下模式被视为违规：

```css
a {
  color: red;
}
b {
  color: blue;
}
```

以下模式*不*被视为违规：

```css
a {
  color: red;
}

b {
  color: blue;
}
```

### `"never-multi-line"`

在多行规则之前*不能*有空行。

以下模式被视为违规：

```css
a {
  color: red;
}

b {
  color: blue;
}
```

以下模式*不*被视为违规：

```css
a {
  color: red;
}
b {
  color: blue;
}
```

## 可选的辅助选项

### `except: ["after-rule", "after-single-line-comment", "inside-block-and-after-rule", "inside-block", "first-nested"]`

#### `"after-rule"`

如果规则紧跟在另一个规则之后则反转主选项。

例如，使用 `"always"`：

以下模式被视为违规：

```css
a {}

b {}
```

以下模式*不*被视为违规：

```css
a {}
b {}
```

#### `"after-single-line-comment"`

如果规则紧跟在单行注释之后则反转主选项。

例如，使用 `"always"`：

以下模式被视为违规：

```css
/* 注释 */

a {}
```

以下模式*不*被视为违规：

```css
/* 注释 */
a {}
```

#### `"inside-block-and-after-rule"`

如果规则在块内且紧跟在另一个规则之后则反转主选项。

例如，使用 `"always"`：

以下模式被视为违规：

```css
@media {

  a {}

  b {}
}
```

以下模式*不*被视为违规：

```css
@media {
  a {}
  b {}
}
```

#### `"inside-block"`

如果规则在块内则反转主选项。

例如，使用 `"always"`：

以下模式被视为违规：

```scss
a {
  color: red;

  b {
    color: blue;
  }
}

```

以下模式*不*被视为违规：

```scss
a {
  color: red;
  b {
    color: blue;
  }
}
```

#### `"first-nested"`

如果规则被嵌套并且是其父节点的第一个子节点则反转主选项。

例如，使用 `"always"`：

以下模式被视为违规：

```css
@media {

  a {}

  b {}
}
```

以下模式*不*被视为违规：

```css
@media {
  a {}

  b {}
}
```

### `ignore: ["after-comment", "first-nested", "inside-block"]`

#### `"after-comment"`

如果规则紧跟在注释之后则忽略。

例如，使用 `"always"`：

以下模式*不*被视为违规：

```css
/* 注释 */
a {}
```

#### `"first-nested"`

如果规则被嵌套并且是其父节点的第一个子节点则忽略。

例如，使用 `"always"`：

以下模式*不*被视为违规：

```css
@media {
  a {}

  b {}
}
```

#### `"inside-block"`

忽略块内的规则。

例如，使用 `"always"`：

以下模式*不*被视为违规：

```css
@media {
  a {}
}
```

```css
@media {
  a {}
  b {}
}
```
