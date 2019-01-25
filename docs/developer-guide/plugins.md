# 编写插件

插件是社区构建的规则和规则集

我们建议您熟悉并遵守 stylelint 的[规则编写约定](rules.md)，包括命名、选项、消息、测试和文档。

<!-- TOC -->

## 插件详解

```js
// 简短的例子
var stylelint = require("stylelint")

var ruleName = "plugin/foo-bar"
var messages =  stylelint.utils.ruleMessages(ruleName, {
  expected: "Expected ...",
})

module.exports = stylelint.createPlugin(ruleName, function(primaryOption, secondaryOptionObject) {
  return function(postcssRoot, postcssResult) {
    var validOptions = stylelint.utils.validateOptions(postcssResult, ruleName, { .. })
    if (!validOptions) { return }
    // ... 一些逻辑 ...
    stylelint.utils.report({ .. })
  }
})

module.exports.ruleName = ruleName
module.exports.messages = messages
```

您的插件规则名必须有命名空间，例如 `your-namespace/your-rule-name`。如果您的插件只提供一个单独的规则或您想不出一个好的命名空间，您可以简单地使用 `plugin/my-rule`。此命名空间可确保插件规则永远不会与核心规则冲突。*请确保您的文档里面记录了插件的规则名（和命名空间），因为用户需要在配置中使用它。*

`stylelint.createPlugin(ruleName, ruleFunction)` 可确保您的插件能与其他规则一起正确设定。

为了使插件规则能够使用[标准配置格式](../user-guide/configuration.md#rules)，`ruleFunction` 应该接受两个参数：主选项和可选辅助选项对象。

如果您的插件规则支持[自动修复](rules.md#添加自动修复)，则 `ruleFunction` 还应接受第三个参数：context。此外，强烈建议您在辅助选项对象中支持 `disableFix` 选项。如果用户为规则传递 `disableFix` 选项，则不在规则内执行自动修复。

`ruleFunction` 可以返回一个函数，这个函数本质上是一个小的 [PostCSS 插件](https://github.com/postcss/postcss/blob/master/docs/writing-a-plugin.md)：它接受两个参数：PostCSS Root（解析的 AST）和 PostCSS LazyResult。您必须[了解 PostCSS 应用程序接口](https://api.postcss.org/)。

### 异步规则

规则使用异步 PostCSS 插件也是可行的！您需要做的就是从插件函数返回一个 Promise 实例。

```js
// 简短的异步例子
var stylelint = require("stylelint")

var ruleName = "plugin/foo-bar-async"
var messages =  stylelint.utils.ruleMessages(ruleName, {
  expected: "Expected ...",
})

module.exports = stylelint.createPlugin(ruleName, function(primaryOption, secondaryOptionObject) {
  return function(postcssRoot, postcssResult) {
    var validOptions = stylelint.utils.validateOptions(postcssResult, ruleName, { .. })
    if (!validOptions) { return }

    return new Promise(function(resolve) {
      // 一些异步操作
      setTimeout(function() {
        // ... 一些逻辑 ...
        stylelint.utils.report({ .. })
        resolve()
      }, 1)
    })
  }
})

module.exports.ruleName = ruleName
module.exports.messages = messages
```

## `stylelint.utils`

stylelint 公开了一些有用的实用程序。*关于这些应用程序的接口，请查看源码的注释和标准规则中的示例。*

### `stylelint.utils.report`

将插件中的违规添加到 stylelint 向用户报告的违规列表中。

*不要直接使用 PostCSS 的 `node.warn()` 方法。*当您使用 `stylelint.utils.report` 时，您的插件会遵守禁用范围和其他 stylelint 未来的特性。这会提供更好的用户体验，更符合标准规则。

### `stylelint.utils.ruleMessages`

将您的消息定制为标准 stylelint 规则的格式。

### `stylelint.utils.validateOptions`

验证您的规则选项。

### `stylelint.utils.checkAgainstRule`

*在您自己的规则中*使用标准 stylelint 规则检查 CSS。此功能为希望修改、约束或扩展现有 stylelint 规则功能的插件作者提供了强大功能和灵活性。

接受选项对象和用于接收来自被调用规则的警告的回调。选项是：

-   `ruleName`: 要调用的规则的名称。
-   `ruleSettings`: 您正在调用的规则的设置，格式与 `.stylelintrc` 配置对象中的格式相同。
-   `root`: 针对此规则运行的根节点。

使用警告来创建一个*来自您插件规则*的*新*警告，并用 `stylelint.utils.report` 汇报

比如，假设您要创建一个插件，使用您的预处理器内置的 @规则的例外列表来运行 `at-rule-no-unknown`：

```js
const allowableAtRules = [..]

function myPluginRule(primaryOption, secondaryOptions) {
  return (root, result) => {
    const defaultedOptions = Object.assign({}, secondaryOptions, {
      ignoreAtRules: allowableAtRules.concat(options.ignoreAtRules || []),
    })

    stylelint.utils.checkAgainstRule({
      ruleName: 'at-rule-no-unknown',
      ruleSettings: [primaryOption, defaultedOptions],
      root: root
    }, (warning) => {
      stylelint.utils.report({
        message: myMessage,
        ruleName: myRuleName,
        result: result,
        node: warning.node,
        line: warning.line,
        column: warning.column,
      })
    })
  }
}
```

## `stylelint.rules`

所有规则函数都可以在 `stylelint.rules` 中找到。这使您可以根据您的特定需求构建现有规则。

一个典型的用例是，在复杂条件下构建规则选项。例如，您的代码库可能使用特殊注释指令来自定义特定样式表的规则选项。您可以构建一个插件来检查这些指令，然后使用正确的选项运行适当的规则（或者根本不运行它们）。

所有规则都有共同的签名。它们是一个接受两个参数的函数：主选项和辅助选项对象。并且该函数返回一个具有 PostCSS 插件签名的函数，期望PostCSS 根节点和结果作为其参数。

这里有个简短的例子，只有当样式表某处有个特殊的指令 `@@check-color-hex-case` 时才运行 `color-hex-case`。

```js
export default stylelint.createPlugin(ruleName, function (expectation) {
  const runColorHexCase = stylelint.rules["color-hex-case"](expectation)
  return (root, result) => {
    if (root.toString().indexOf("@@check-color-hex-case") === -1) return
    runColorHexCase(root, result)
  }
})
```

## 允许主选项数组

如果您的插件可以接受数组作为其主选项，则必须通过在规则函数上设置属性 `primaryOptionArray = true` 来指定它。有关更多信息，请查看[“处理规则”](rules.md#主选项)文档。

## 外部辅助模块

除了[“处理规则”](rules.md)文档中提到的标准解析器, 我们还推荐使用在 stylelint 里用到的其他的外部模块。它们包括:

-   [normalize-selector](https://github.com/getify/normalize-selector)：规范化CSS选择器。
-   [postcss-resolve-nested-selector](https://github.com/davidtheclark/postcss-resolve-nested-selector)：给予 PostCSS AST 中的（嵌套）选择器，返回解析后的选择器的数组。
-   [style-search](https://github.com/davidtheclark/style-search)：搜索CSS（和类 CSS）中的字符串，对字符串、注释和函数内是否发生匹配敏感。

请看一下 [stylelint 的内部工具](https://github.com/stylelint/stylelint/tree/master/lib/utils)，如果您遇到一个您的插件需要的函数，请考虑帮助我们把它提取为外部模块。

## 对等依赖

您应该在插件的 `package.json` 的 `peerDependencies`（**不是** `dependencies`）键中表明，您的插件可以使用什么版本的 stylelint。这是为了确保不会安装非预期的 stylelint 版本。

例如，要表示您的插件可以与 stylelint 版本 7 和 8 一起使用：

```json
{
  "peerDependencies": {
    "stylelint": "^7.0.0 || ^8.0.0"
  }
}
```

## 测试插件

为了测试您的插件，您可以考虑使用和 stylelint 内部使用的一样的规则测试函数，: [`stylelint-test-rule-tape`](https://github.com/stylelint/stylelint-test-rule-tape)。

## 插件包

要使单个模块提供多个规则，只需导出一个插件对象数组（而不是单个对象）。

## 共享插件和插件包

-   在您的 `package.json` 文件中使用 `stylelint-plugin` 关键字。
-   一旦您的插件发布，请发送一个拉取请求将您的插件添加到[列表](../user-guide/plugins.md)。
