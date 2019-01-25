# at-rule-empty-line-before

要求或禁止在 @规则之前的空行。

```css
a {}
          /* ← */
@media {} /* ↑ */
/**          ↑
 *          这行 */
```

此规则忽略：

-   作为源中第一个节点的 @规则
-   Less 中的 `@import`。

[命令行](../../../docs/user-guide/cli.md#自动修复错误)中的 `--fix` 选项可以自动修复此规则报告的所有问题。我们建议启用 [`indentation`](../indentation/README.md) 规则，以便更好地使用此规则自动修复结果。

## 选项

`string`: `"always"|"never"`

### `"always"`

在 @规则之前*必须*有一个空行。

以下模式被视为违规：

```css
a {} @media {}
```

```css
a {}
@media {}
```

以下模式*不*被视为违规：

```css
a {}

@media {}
```

### `"never"`

在 @规则之前*不能*有空行。

以下模式被视为违规：

```css
a {}

@media {}
```

以下模式*不*被视为违规：

```css
a {} @media {}
```

```css
a {}
@media {}
```

## 可选的辅助选项

### `except: ["after-same-name", "inside-block", "blockless-after-same-name-blockless", "blockless-after-blockless", "first-nested"]`

#### `"after-same-name"`

如果 @规则紧跟在另一个同名的 @规则之后则反转主选项。

这意味着您可以按名称对 @规则进行分组。

例如，使用 `"always"`：

以下模式*不*被视为违规：

```css
@charset "UTF-8";

@import url(x.css);
@import url(y.css);

@media (min-width: 100px) {}
@media (min-width: 200px) {}
```

```css
a {

  @extends .foo;
  @extends .bar;

  @include x;
  @include y {}
}
```

#### `"inside-block"`

如果 @规则在块内则反转主选项。

例如，使用 `"always"`：

以下模式被视为违规：

```css
a {

  @extend foo;
  color: pink;
}

b {
  color: pink;

  @extend foo;
}
```

以下模式*不*被视为违规：

```css
a {
  @extend foo;
  color: pink;
}

b {
  color: pink;
  @extend foo;
}
```

#### `"blockless-after-same-name-blockless"`

如果无块 @规则紧跟在另一个同名的无块 @规则之后则反转主选项。

这意味着您可以按名称对无块 @规则进行分组。

共享行注释不会影响此选项。

例如，使用 `"always"`：

以下模式*不*被视为违规：

```css
@charset "UTF-8";

@import url(x.css);
@import url(y.css);
```

```css
@charset "UTF-8";

@import url(x.css); /* 注释 */
@import url(y.css);
```

```css
a {

  @extends .foo;
  @extends .bar;

  @include loop;
  @include doo;
}
```

#### `"blockless-after-blockless"`

如果无块 @规则紧跟在另一个无块 @规则之后则反转主选项。

共享行注释不会影响此选项。

例如，使用 `"always"`：

以下模式被视为违规：

```css
@import url(x.css);

@import url(y.css);

@media print {}
```

以下模式*不*被视为违规：

```css
@import url(x.css);
@import url(y.css);

@media print {}
```

```css
@import url(x.css); /* 注释 */
@import url(y.css);

@media print {}
```

#### `"first-nested"`

如果 @规则被嵌套并且是其父节点的第一个子节点则反转主选项。

例如，使用 `"always"`：

以下模式被视为违规：

```css
a {

  @extend foo;
  color: pink;
}

b {
  color: pink;
  @extend foo;
}
```

以下模式*不*被视为违规：

```css
a {
  @extend foo;
  color: pink;
}

b {
  color: pink;

  @extend foo;
}
```

### `ignore: ["after-comment", "first-nested", "inside-block", "blockless-after-same-name-blockless", "blockless-after-blockless"]`

#### `"after-comment"`

如果 @规则紧跟在注释之后则忽略。

共享行注释不会触发此选项。

以下模式*不*被视为违规：

```css
/* 注释 */
@media {}
```

```css
/* 注释 */

@media {}
```

```css
@media {} /* 注释 */

@media {}
```

#### `"first-nested"`

如果 @规则被嵌套并且是其父节点的第一个子节点则忽略。

例如，使用 `"always"`：

以下模式*不*被视为违规：

```css
@supports {
  @media {}

  @media {}
}
```

#### `"inside-block"`

忽略块内的 @规则。

例如，使用 `"always"`：

以下模式*不*被视为违规：

```css
a {
  @extend foo;
  color: pink;
}

a {

  @extend foo;
  color: pink;
}

b {
  color: pink;
  @extend foo;
}

b {
  color: pink;

  @extend foo;
}
```

#### `"blockless-after-same-name-blockless"`

如果无块 @规则紧跟在另一个同名的无块 @规则之后则忽略。

这意味着您可以按名称对无块 @规则进行分组。

例如，使用 `"always"`：

以下模式*不*被视为违规：

```css

@charset "UTF-8";

@import url(x.css);
@import url(y.css);
```

```css
a {

  @extends .foo;
  @extends .bar;

  @include loop;
  @include doo;
}
```

#### `"blockless-after-blockless"`

如果无块 @规则紧跟在另一个无块 @规则之后则忽略。

例如，使用 `"always"`：

以下模式*不*被视为违规：

```css
@import url(x.css);

@import url(y.css);

@media print {}
```

```css
@import url(x.css);
@import url(y.css);

@media print {}
```

### `ignoreAtRules: ["array", "of", "at-rules"]`

忽略指定的 @规则。

例如，使用 `"always"`。

给定：

```js
["import"]
```

以下模式*不*被视为违规：

```css
@charset "UTF-8";
@import {}
```
