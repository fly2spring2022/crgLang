# crgLang

**crgLang** 是一门专为撰写 AI prompt 和生成结构化内容而设计的编程语言。它提供了一种简单而强大的语法，用于定义输入模块和模板，以便动态生成内容。与传统编程语言不同，**crgLang** 利用 AI 模型进行解释和执行，使用户能够专注于撰写有效的提示，而无需担心解析器或编译器。
**crg**：**C**reative **R**esearch **G**roup（创意研究小组）；**Lang**：**Lang**uage（语言）。

Author: fly2spring  
Name: crgLang  
Version: 1.0.0  
Ai_Model:  
Date: 10/03/2024  

---

## 特性

- **模块化输入收集**：使用 **模块（Modules）** 动态收集用户输入。
- **基于模板的内容生成**：定义输出的结构化模板。
- **条件逻辑**：支持基于用户输入的 `if-else` 条件。
- **并行和分支执行**：处理复杂提示流程，支持并行执行和分支逻辑。
- **国际化**：根据用户偏好生成多种语言的内容。
- **支持 Markdown**：输出可以使用 Markdown 格式，生成富文本。
- **复杂数据结构支持**：处理数组、JSON 和其他复杂输入。

## 快速入门

### 基本结构

一个 **crgLang** 程序由以下主要组件组成：

- **模块（Modules）**：用于收集用户输入。
- **模板（Templates）**：定义如何根据输入生成内容。
- **启动块（Start）**：定义执行流程的入口点。
- **输出块（Output）**：控制最终展示给用户的内容。

### 示例

以下是一个简单的 **crgLang** 程序，收集用户输入并生成一个短故事。

```crgLang
Module CharacterSetup {
    name: UserInput name: "请输入主角的名字"
    age: UserInput age: "请输入主角的年龄"
}

Template StoryTemplate {
    body: """
    主角 {name}，{age} 岁，开始了一段神秘的旅程......
    """
}

Start {
    Module CharacterSetup
    Template StoryTemplate
}

Output {
    "以下是您生成的故事："
    Template StoryTemplate
}
```

### 输出

当这个程序运行时，它会收集用户对角色名字和年龄的输入，然后根据模板生成一个短故事。

## 高级特性

### 条件逻辑

可以添加条件逻辑，根据用户输入自定义输出。

### 并行执行和分支

处理多个路径或并行执行模块。

### 循环生成输入

可以使用循环动态生成多个内容部分。

### 国际化

根据用户偏好支持多种语言。

### Markdown 支持

crgLang 支持将输出格式化为 Markdown，允许创建结构良好的文本。

## 运行 crgLang 程序

要运行 **crgLang** 程序，您只需以 AI 模型可以解释的方式提供语言结构。AI 模型本身充当解释器和执行器，根据定义的提示和模板生成最终输出。

**crgLang** 专为动态生成 AI 提示而设计。凭借模块化输入处理、基于模板的内容生成、条件逻辑、Markdown 支持和缓存等特性，它为编写生成丰富多样内容的提示提供了结构化的方法。

---

## 未来发展计划

- **增强条件逻辑**：支持更复杂的条件。
- **扩展模块库和模板库**：预置多样化模块和模板，供用户直接使用。
- **实时反馈机制**：允许用户交互性地调整生成的内容。
- **更多输出格式**：支持导出为 PDF 或 HTML 等格式。

---

## 许可证

**crgLang** 遵循 GNU通用公共许可证第3版（GNU General Public License v3.0，简称GPLv3）许可证。保护crgLang的自由和开放性，促进共享与合作。

---

## 联系方式

如需进一步咨询或建议，请通过 **61727091@qq.com** 联系我们，或访问我们的微信公众号 [Ai故事线](https://mp.weixin.qq.com/s/BoCCyXZrrbeKScsKvNxZsg)。
