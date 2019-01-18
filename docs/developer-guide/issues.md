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
-   provide a link to the relevant section of the [Developer Guide](../developer-guide.md) when:
    -   adding the `help wanted` label to encourage the original poster to contribute, e.g. [adding an option to an existing rule](../developer-guide/rules.md#adding-an-option-to-an-existing-rule) or [fixing a bug in an existing rule](../developer-guide/rules.md#fixing-a-bug-in-an-existing-rule)
    -   closing an issue because the feature is best part of ecosystem e.g. [a plugin](../developer-guide/plugins.md) or [processor](../developer-guide/processors.md)
-   use milestones only on issues and not on pull requests and:
    -   use the `future-major` milestone for issues that introduce breaking changes
    -   optionally, create version milestones (e.g. `8.x`) to manage upcoming releases
-   use the following saved reply to close any issue that do not use the template:

```md
Thanks for creating this issue but we're closing it as issues need to follow one of our templates, so that we can clearly understand your particular circumstances.

Please help us to help you by [recreating the issue](https://github.com/stylelint/stylelint/issues/new/choose) using one of our templates.
```

There are three rules of thumb. You should use the:

-   `status: discussion`, `status: needs clarification` or `status: needs investigation` label when first triaging an issue
-   `help wanted`, a `type` (and `non-standard syntax: *` and `good first issue`) labels when a course of action is agreed
-   `status: wip` label when your are, or someone has said they are, about to start working on an issue
