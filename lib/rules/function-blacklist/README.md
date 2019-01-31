# function-blacklist

指定禁用的函数的黑名单。

```css
a { transform: scale(1); }
/**            ↑
 * 这个函数 */
```

## 选项

`array|string`: `["array", "of", "unprefixed", /functions/ or "regex"]|"function"|"/regex/"`

如果字符串用 `"/"` 包围（例如 `"/^rgb/"`），则将其解释为正则表达式。

给定：

```js
["scale", "rgba", "linear-gradient"]
```

以下模式被视为违规：

```css
a { transform: scale(1); }
```

```css
a {
  color: rgba(0, 0, 0, 0.5);
}
```

```css
a {
  background:
    red,
    -moz-linear-gradient(45deg, blue, red);
}
```

以下模式*不*被视为违规：

```css
a { background: red; }
```
