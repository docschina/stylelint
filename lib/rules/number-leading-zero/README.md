# number-leading-zero

要求或禁止小于 1 的小数有一个前导零。

```css
a { line-height: 0.5; }
/**              ↑
 * 这个前导零 */
```

此规则忽略 Less mixins 的参数。

[命令行](../../../docs/user-guide/cli.md#自动修复错误)中的 `--fix` 选项可以自动修复此规则报告的所有问题。

## 选项

`string`: `"always"|"never"`

### `"always"`

这里*必须*有一个前导零。

以下模式被视为违规：

```css
a { line-height: .5; }
```

```css
a { transform: translate(2px, .4px); }
```

以下模式*不*被视为违规：

```css
a { line-height: 0.5; }
```

```css
a { transform: translate(2px, 0.4px); }
```

### `"never"`

这里*不能*有前导零。

以下模式被视为违规：

```css
a { line-height: 0.5; }
```

```css
a { transform: translate(2px, 0.4px); }
```

以下模式*不*被视为违规：

```css
a { line-height: .5; }
```

```css
a { transform: translate(2px, .4px); }
```
