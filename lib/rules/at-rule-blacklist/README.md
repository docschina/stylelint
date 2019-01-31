# at-rule-blacklist

指定禁用的@规则的黑名单。

```css
    @keyframes name {}
/** ↑
 * 像这样的@规则 */
```

## 选项

`array|string`: `["array", "of", "unprefixed", "at-rules"]|"at-rule"`

给定：

```js
["extend", "keyframes"]
```

以下模式被视为违规：

```css
a { @extend placeholder; }
```

```css
@keyframes name {
  from { top: 10px; }
  to { top: 20px; }
}
```

```css
@-moz-keyframes name {
  from { top: 10px; }
  to { top: 20px; }
}
```

以下模式*不*被视为违规：

```css
@import "path/to/file.css";
```
