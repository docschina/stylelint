# keyframe-declaration-no-important

禁止关键帧声明的 `!important`。

```css
@keyframes important2 {
  from { margin: 10px }
  to { margin: 20px !important }
}                /* ↑ */
/**                 ↑
*     这个 !important */
```

在某些浏览器中完全忽略在关键帧声明中使用 `！important`：
[MDN - 关键帧中的 !important 关键词](https://developer.mozilla.org/zh-CN/docs/Web/CSS/@keyframes#关键帧中的 _!important_ 关键词)

## 选项

### `true`

以下模式被视为违规：

```css
@keyframes important1 {
  from {
    margin-top: 50px;
  }
  to {
    margin-top: 100px !important;
  }
}
```

```css
@keyframes important1 {
  from {
    margin-top: 50px;
  }
  to {
    margin-top: 100px!important;
  }
}
```

```css
@keyframes important1 {
  from {
    margin-top: 50px;
  }
  to {
    margin-top: 100px ! important;
  }
}
```

以下模式*不*被视为违规：

```css
a { color: pink !important; }
```

```css
@keyframes important1 {
  from {
    margin-top: 50px;
  }
  to {
    margin-top: 100px;
  }
}
```
