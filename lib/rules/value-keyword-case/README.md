# value-keyword-case

指定关键字值的大小写。

```css
    a { display: block; }
/**              ↑
 *    这个值 */
```

此规则忽略 [`<custom-idents>`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/custom-ident) 的已知属性。使用 `ignoreValues：[]` 辅助选项可以忽略与非属性（例如 `$vars` 和自定义属性）配对且不符合主选项的值。

[命令行](../../../docs/user-guide/cli.md#自动修复错误)中的 `--fix` 选项可以自动修复此规则报告的所有问题。

## 选项

`string`: `"lower"|"upper"`


### `"lower"`

以下模式被视为违规：

```css
a {
  display: Block;
}
```

```css
a {
  display: bLoCk;
}
```

```css
a {
  display: BLOCK;
}
```

```css
a {
  transition: -WEBKIT-TRANSFORM 2s;
}
```

以下模式*不*被视为违规：

```css
a {
  display: block;
}
```

```css
a {
  transition: -webkit-transform 2s;
}
```

### `"upper"`

以下模式被视为违规：

```css
a {
  display: Block;
}
```

```css
a {
  display: bLoCk;
}
```

```css
a {
  display: block;
}
```

```css
a {
  transition: -webkit-transform 2s;
}
```

以下模式*不*被视为违规：

```css
a {
  display: BLOCK;
}
```

```css
a {
  transition: -WEBKIT-TRANSFORM 2s;
}
```

## 可选的辅助选项

### `ignoreKeywords: ["/regex/", /regex/, "non-regex"]`

Ignore case of keywords values.

例如，使用 `"lower"`。

给定：

```js
["Block", "/^(f|F)lex$/"]
```

以下模式被视为违规：

```css
a {
  display: bLoCk;
}
```

```css
a {
  display: BLOCK;
}
```

```css
a {
  display: fLeX;
}
```

```css
a {
  display: FLEX;
}
```

以下模式*不*被视为违规：

```css
a {
  display: block;
}
```

```css
a {
  display: Block;
}
```

```css
a {
  display: flex;
}
```

```css
a {
  display: Flex;
}
```

### `ignoreProperties: ["/regex/", /regex/, "non-regex"]`

忽略列出的属性的值的大小写。

例如，使用 `"lower"`。

```js
["/^(b|B)ackground$/", "display"]
```

以下模式被视为违规：

```css
a {
  text-align: LEFT;
}
```

```css
a {
  text-align: Left;
}
```

以下模式*不*被视为违规：

```css
a {
  display: bloCk;
}
```

```css
a {
  display: BloCk;
}
```

```css
a {
  display: BLOCK;
}
```

```css
a {
  display: block;
}
```

```css
a {
  background: Red;
}
```

```css
a {
  Background: deepPink;
}
```
