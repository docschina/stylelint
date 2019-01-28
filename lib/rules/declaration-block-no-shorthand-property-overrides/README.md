# declaration-block-no-shorthand-property-overrides

禁止简写属性覆盖相关的扩写属性。

```css
a { background-repeat: repeat; background: green; }
/**                            ↑
 *               这个简写属性会覆盖之前的属性 */
```

绝大多数情况下，这只是作者的疏忽。有关此行为的更多信息，请参阅 [MDN 的简写属性文档](https://developer.mozilla.org/zh-CN/docs/Web/CSS/Shorthand_properties)。

## 选项

### `true`

以下模式被视为违规：

```css
a {
  padding-left: 10px;
  padding: 20px;
}
```

```css
a {
  transition-property: opacity;
  transition: opacity 1s linear;
}
```

```css
a {
  -webkit-transition-property: opacity;
  -webkit-transition: opacity 1s linear;
}
```

```css
a {
  border-top-width: 1px;
  top: 0;
  bottom: 3px;
  border: 2px solid blue;
}
```

以下模式*不*被视为违规：

```css
a { padding: 10px; padding-left: 20px; }
```

```css
a { transition-property: opacity; } a { transition: opacity 1s linear; }
```

```css
a { transition-property: opacity; -webkit-transition: opacity 1s linear; }
```
