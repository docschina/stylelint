#管理 issues

你可以:

-   使用 [标签](https://github.com/stylelint/stylelint/labels) :
    -   添加 _一个_ `status: *` 的类似标签 (或者  `help wanted` 标签 当 ready-to-go)
    -   添加 _零个或者 一个_  `type: *` 的类似标签
    -   添加 _零个、一个 或者多个_  `non-standard syntax: *` 的类似标签
    -   可选择项, 添加  `good first issue` 标签
-   rename the title into a consistent format and:
-   把标题重名成统一格式：
    -   以 [CHANGELOG group names](pull-requests.md)为开头, 但是使用的是现在时:
        -   "Remove y" 例如： "Remove unit-blacklist"
        -   "Deprecate x in y" 例如： "Deprecate resolvedNested option in selector-class-pattern"
        -   "Add y" 例如： "Add unit-blacklist"
        -   "Add x to y" 例如： "Add ignoreProperties: [] to property-blacklist"
        -   "Fix false positives/negatives for x in y" 例如： "Fix false positives for Less mixins in color-no-hex"
    -   使用 `*` 如果这个issue适用于一组规则 ，例如： "Fix false negatives for SCSS variables in selector-*-pattern"
-   提供一个指向[Developer Guide](../developer-guide.md)的相关部分的链接 ，当:
    -   添加 `help wanted` 标签来鼓励楼主去修改 例如： [adding an option to an existing rule](../developer-guide/rules.md#adding-an-option-to-an-existing-rule) 或者 [fixing a bug in an existing rule](../developer-guide/rules.md#fixing-a-bug-in-an-existing-rule)
    -   关闭一个issue ，因为今后是更好的环境 例如： [a plugin](https://github.com/stylelint/stylelint/blob/master/docs/developer-guide/plugins.md) 或者 [processor](https://github.com/stylelint/stylelint/blob/master/docs/developer-guide/processors.md)
-   只有在issues的时候，不是在pull requests 的时候，使用里程碑:
    -   对 issues 使用 `future-major` 版本号 ,来描述突破性改变
    -   可供选项，创建版本号（例如:`8.x`),来控制升级发布
-   使用以下保存回复来关闭任何不需要模板issue

```md
感谢创建这个issue,但是我们将要关闭它，因为issues需要使用我们的模板，这样我们才能清楚的理解你的具体情况

这样有利于你我 [recreating the issue](https://github.com/stylelint/stylelint/issues/new/choose) 请使用一个我们的模板吧.
```

这里有三个经验法则，你可以使用它们：

-   `status: discussion`, `status: needs clarification` 或者 `status: needs investigation` 标签当第一次修复或者issue的时候
-   `help wanted`, 一个 `type` (和 `non-standard syntax: *` 和 `good first issue`) 标签当一连串行为被同意的时候
-   `status: wip` 标签当你或者其他人说他们，准备开始工作一个issue的时候
