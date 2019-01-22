# selector-type-no-unknown

Disallow unknown type selectors.

```css
    unknown {}
/** ↑
 * This type selector */
```

This rule considers tags defined in the HTML, SVG, and MathML specifications to be known.

## 选项

### `true`

以下模式被视为违规：

```css
unknown {}
```

```css
tag {}
```

The following patterns are *not* considered violations:

```css
input {}
```

```css
ul li {}
```

```css
li > a {}
```

## Optional secondary options

### `ignore: ["custom-elements", "default-namespace"]`

#### `"custom-elements"`

Allow custom elements.

以下模式被视为违规：

```css
unknown {}
```

```css
x-Foo {}
```

The following patterns are *not* considered violations:

```css
x-foo {}
```

#### `"default-namespace"`

Allow unknown type selectors if they belong to the default namespace.

以下模式被视为违规：

```css
namespace|unknown {}
```

The following patterns are *not* considered violations:

```css
unknown {}
```

### `ignoreNamespaces: ["/regex/", /regex/, "string"]`

Given:

```js
["/^my-/", "custom-namespace"]
```

The following patterns are *not* considered violations:

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

Given:

```js
["/^my-/", "custom-type"]
```

The following patterns are *not* considered violations:

```css
custom-type {}
```

```css
my-type {}
```

```css
my-other-type {}
```
