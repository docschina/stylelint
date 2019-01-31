# selector-attribute-quotes

要求或禁止属性值的引号。

```css
[target="_blank"] {}
/**     ↑      ↑
 * 这些引号 */
```

## 选项

`string`: `"always"|"never"`

### `"always"`

属性值*必须*使用引号。

以下模式被视为违规：

```css
[title=flower] {}
```

```css
[class^=top] {}
```

以下模式*不*被视为违规：

```css
[title] {}
```

```css
[target="_blank"] {}
```

```css
[class|="top"] {}
```

```css
[title~='text'] {}
```

```css
[data-attribute='component'] {}
```

### `"never"`

属性值*不能*使用引号。

以下模式被视为违规：

```css
[target="_blank"] {}
```

```css
[class|="top"] {}
```

```css
[title~='text'] {}
```

```css
[data-attribute='component'] {}
```

以下模式*不*被视为违规：

```css
[title] {}
```

```css
[title=flower] {}
```

```css
[class^=top] {}
```
