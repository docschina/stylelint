# 规则测试工具

stylelint 规则需要*大量的*测试。所以我们构建了一个专门的 stylelint 规则测试格式，以加速大规模生成一致，有效的规则测试。

我们有一个用于描述测试的架构，以及用于创建“规则测试工具”的函数，其使用测试框架（例如，tape 或 Mocha）来解析该架构。

开发插件时，您可以使用以下规则测试工具或创建自己的工具。

-   stylelint-test-rule-tape
-   stylelint-test-rule-mocha
-   stylelint-test-rule-ava

## 使用规则测试工具

要使用您选择的规则测试程序，请执行以下操作：

```js
// `testRule` = 导入的规则测试工具
testRule(rule, testGroupDescription)
```

`rule` 正是是你正在测试的规则（一个函数）。

`testGroupDescription` 是一个适合以下架构的对象。

### 测试组架构

每个测试组对象都描述了具有特定配置的特定规则的一组测试用例。

所需属性：

-   `ruleName` {string}：规则的名称。用于生成的测试用例描述。
-   `config` {any}：此测试组的规则配置。应该与 `.stylelintrc` 中使用的规则配置格式相匹配。
-   `accept` {array}：*不应违反规则*的测试用例的对象数组。每个对象都具有以下属性：
    -   `code` {string}：要检查的 CSS 源码。
    -   `description` {string}：*可选。* 测试用例描述。
    -   `only` {boolean}：如果为 `true`，只运行这个测试用例。
-   `reject` {array}：*应该违反规则* 的测试用例的对象数组。每个对象都具有以下属性：
    -   `code` {string}：要检查的 CSS 源码。
    -   `message` {string}：预期违规的消息。
    -   `line` {number}：*可选但推荐使用。* 预期违规的行号。如果省略，则不会检查。
    -   `column` {number}：*可选但推荐使用。* 预期违规的列号。如果省略，则不会检查。
    -   `description` {string}：*可选。* 测试用例描述。
    -   `only` {boolean}：如果为 `true`，只运行这个测试用例。
    -   `fixed` {string}：*如果测试架构启用了 `fix`，则为必需。* 针对 `code` 属性自动修复的结果。

可选属性：

-   `syntax` {"css"|"css-in-js"|"html"|"less"|"markdown"|"sass"|"scss"|"sugarss"}：默认为 `"css"`。其他设置使用特殊解析器。
-   `skipBasicChecks` {boolean}：默认为 `false`。如果为 `true`，则不会执行一些基本检查（应该几乎总是包括在内）。你可以在 `lib/testUtils/basicChecks.js` 中查看它们。
-   `preceedingPlugins` {array}：应该在测试 CSS 之前运行的 PostCSS 插件数组。
-   `fix` {boolean}：默认为 `false`。如果为 `true`，则每个 `reject` 测试用例都将进行自动修复功能测试。*如果规则具有自动修复，则为必需项。*

## 创建规则测试工具

stylelint 本身公开了一种几乎可以用任何测试框架创建规则测试工具的方法。

```js
var testRule = stylelint.createRuleTester(equalityCheck)
```

传入 `equalityCheck` 函数。给定一些信息，此检查工具应使用您喜欢的任何测试运行器来执行相等性检查。

`equalityCheck` 函数应该接受两个参数：

-   `processCss` {Promise}：一个 Promise，释为您需要检查的对照组的数组（文档附后）。
-   `context` {object}：包含您可能需要的其他信息的对象：
    -   `caseDescription` {string}：整个测试用例的描述。最终打印会像这样：
    ```bash
    > rule: value-list-comma-space-before
    > config: "always-single-line"
    > code: "a { background-size: 0 ,0;\n}"
    ```
    -   `comparisonCount` {number}：需要执行的比较次数（例如对 tape 有用）。
    -   `completeAssertionDescription` {string}：虽然每个单独的对照组可能有自己的描述，但这个是对整个断言的描述（例如对 Mocha 有用）。
    -   `only` {boolean}：如果为 `true`，那么测试运行器应该只运行这个测试用例（例如 tape 中的 `test.only`，Mocha中的 `describe.only`）。

`processCss` 是一个 Promise，它释为对照组的数组。每个对照组都具有以下属性：

-   `actual` {any}：某些实际值。
-   `expected` {any}：某些预期值。
-   `description` {string}：一个（可能是空的）比较的描述。

在 `equalityCheck` 函数中，您需要确保执行以下操作：

-   设定测试用例。
-   当 `processCss` 解析后，遍历每个对照组。
-   对每个对照组进行断言 `actual === expected` 检查。

返回 `testRule` 函数（如上所述）。
