# selector-no-qualifying-type

禁止用类型选择器来限定一个选择器。

```css
    a.foo {}
/** ↑
 * 这个类型选择器限定了类选择器 */
```

当类型选择器与另一个选择器复合（链接）时（例如 `a.foo`、`a#foo`），即所谓“限定”。该规则不干涉类型选择器通过组合选择器与其他选择器组合（例如 `a > .foo`、`a #foo`）。

## 选项

### `true`

以下模式被视为违规：

```css
a.foo {
  margin: 0
}
```

```css
a#foo {
  margin: 0
}
```

```css
input[type='button'] {
  margin: 0
}
```

以下模式*不*被视为违规：

```css
.foo {
  margin: 0
}
```

```css
#foo {
  margin: 0
}
```

```css
input {
  margin: 0
}
```

## 可选的辅助选项

### `ignore: ["attribute", "class", "id"]`

#### `"attribute"`

允许被类型限定的属性选择器。

以下模式*不*被视为违规：

```css
input[type='button'] {
  margin: 0
}
```

#### `"class"`

允许被类型限定的类选择器。

以下模式*不*被视为违规：

```css
a.foo {
  margin: 0
}
```

#### `"id"`

允许被类型限定的 ID 选择器。

以下模式*不*被视为违规：

```css
a#foo {
  margin: 0
}
```
