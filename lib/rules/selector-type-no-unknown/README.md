# selector-type-no-unknown

禁止未知的类型选择器。

```css
    unknown {}
/** ↑
 * 这个类型选择器 */
```

此规则考虑了 HTML、SVG 和 MathML 规范中定义的标记。

## 选项

### `true`

以下模式被视为违规：

```css
unknown {}
```

```css
tag {}
```

以下模式*不*被视为违规：

```css
input {}
```

```css
ul li {}
```

```css
li > a {}
```

## 可选的辅助选项

### `ignore: ["custom-elements", "default-namespace"]`

#### `"custom-elements"`

允许自定义元素。

以下模式被视为违规：

```css
unknown {}
```

```css
x-Foo {}
```

以下模式*不*被视为违规：

```css
x-foo {}
```

#### `"default-namespace"`

允许属于默认命名空间的未知类型选择器。

以下模式被视为违规：

```css
namespace|unknown {}
```

以下模式*不*被视为违规：

```css
unknown {}
```

### `ignoreNamespaces: ["/regex/", /regex/, "string"]`

给定：

```js
["/^my-/", "custom-namespace"]
```

以下模式*不*被视为违规：

```css
custom-namespace|unknown {}
```

```css
my-namespace|unknown {}
```

```css
my-other-namespace|unknown {}
```

### `ignoreTypes: ["/regex/", /regex/, "string"]`

给定：

```js
["/^my-/", "custom-type"]
```

以下模式*不*被视为违规：

```css
custom-type {}
```

```css
my-type {}
```

```css
my-other-type {}
```
