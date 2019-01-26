# selector-attribute-operator-space-after

要求在属性选择器中的运算符之后必须有一个空格或不能有空白符。

```css
[target= _blank]
/**    ↑
 * 运算符之后的空白符 */
```

[命令行](../../../docs/user-guide/cli.md#自动修复错误)中的 `--fix` 选项可以自动修复此规则报告的所有问题。

## 选项

`string`: `"always"|"never"`

### `"always"`

在运算符之后*必须*有一个空格。

以下模式被视为违规：

```css
[target=_blank] {}
```

```css
[target =_blank] {}
```

```css
[target='_blank'] {}
```

```css
[target="_blank"] {}
```

```css
[target ='_blank'] {}
```

```css
[target ="_blank"] {}
```

以下模式*不*被视为违规：

```css
[target] {}
```

```css
[target= _blank] {}
```

```css
[target= '_blank'] {}
```

```css
[target= "_blank"] {}
```

```css
[target = _blank] {}
```

```css
[target = '_blank'] {}
```

```css
[target = "_blank"] {}
```

### `"never"`

在运算符之后*不能*有空格。

以下模式被视为违规：

```css
[target= _blank] {}
```

```css
[target = _blank] {}
```

```css
[target= '_blank'] {}
```

```css
[target= "_blank"] {}
```

```css
[target = '_blank'] {}
```

```css
[target = "_blank"] {}
```

以下模式*不*被视为违规：

```css
[target] {}
```

```css
[target=_blank] {}
```

```css
[target='_blank'] {}
```

```css
[target="_blank"] {}
```

```css
[target =_blank] {}
```

```css
[target ='_blank'] {}
```

```css
[target ="_blank"] {}
```
