### crgLang 语法说明文档

Author: fly2spring  
Name: crgLang  
Version: 1.0.0  
Ai_Model:  
Date: 10/03/2024  

---

## 1. 概述

**crgLang** 是一门专为 AI prompt 编写而设计的编程语言。它的目标是为用户提供一种简洁、结构化的方式来编写 prompt，以便大语言模型能够根据用户需求生成内容。crgLang 依赖于 AI 大模型进行解释和运行，而不需要传统的编译器或解析器。

---

## 2. crgLang 基本结构

crgLang 由 **模块（Module）** 和 **模板（Template）** 组成。模块用于收集用户输入，而模板用于根据这些输入生成最终的输出内容。程序通过 **Start** 块定义执行流程，并通过 **Output** 块控制展示给用户的内容。

### 2.1 模块（Module）

模块用于收集用户输入或外部数据，作为生成内容的基础。

```crgLang
Module CharacterSetup {
    name: UserInput name: "请输入角色的名字"
    age: UserInput age: "请输入角色的年龄"
}
```

### 2.2 模板（Template）

模板将用户输入的内容与预设的文本结合，生成具体的输出。

```crgLang
Template StoryTemplate {
    body: """
    主角名字: {name}
    年龄: {age}
    """
}
```

### 2.3 启动块（Start）

`Start` 块是程序的执行入口，定义了模块和模板的执行顺序。

```crgLang
Start {
    Module CharacterSetup
    Template StoryTemplate
}
```

### 2.4 输出块（Output）

`Output` 块控制哪些内容最终展示给用户。

```crgLang
Output {
    "故事生成成功，以下是您的故事："
    Template StoryTemplate
}
```

---

## 3. 条件逻辑和分支

crgLang 支持条件逻辑，使程序可以根据用户的输入动态调整生成的内容。

```crgLang
Template DynamicStory {
    If genre == "冒险" {
        body: "这是一个充满冒险的故事！"
    } else {
        body: "这是一个平静的故事。"
    }
}
```

---

## 4. 并行与分支执行

为了支持更复杂的生成流程，crgLang 提供了并行执行与多分支选择的功能。

```crgLang
Start {
    Parallel {
        Module CharacterSetup
        Module StorySettings
    }
    If genre == "科幻" {
        Template SciFiStory
    } else {
        Template FantasyStory
    }
}
```

---

## 5. 循环与动态内容

支持循环结构来生成动态内容，适合处理多次输入或生成多个项目。

```crgLang
Template ItemTemplate {
    For i in 1..{item_count} {
        body: "项目 {i}: 这是第 {i} 个生成项目"
    }
}
```

---

## 6. 预定义与复用

crgLang 允许定义可以在多个地方复用的模块和模板，减少重复代码。

```crgLang
Module PredefinedModule {
    data: UserInput data: "请输入一些数据"
}

Start {
    Include PredefinedModule
    Template OutputTemplate
}
```

---

## 7. 国际化与本地化

crgLang 支持国际化与本地化，根据用户的语言设置生成不同语言的文本。

```crgLang
Template LocalizedTemplate {
    language: "en" {
        body: "Hello, welcome!"
    }
    language: "zh" {
        body: "你好，欢迎！"
    }
}
```

---

## 8. 复杂数据结构的支持

crgLang 支持处理复杂的用户输入数据，如 JSON 对象或数组，便于处理更复杂的数据结构。

```crgLang
Module NestedData {
    person: UserInput person: "请输入人物数据" type: "json"
}

Template DisplayPerson {
    body: "名字: {person.name}, 年龄: {person.age}"
}
```

---

## 9. Markdown 格式支持

crgLang 支持将输出内容格式化为 Markdown 格式，以便生成更加结构化的文档。

```crgLang
Template StoryMarkdown {
    format: "markdown"
    body: """
    # {title}

    **主角名字**: {name}

    ### 故事简介
    {summary}

    *故事类型*: {genre}
    
    > 故事高潮: {climax}
    """
}
```

如果需要将 Markdown 渲染为 HTML，可以使用 `@render` 指令：

```crgLang
Output {
    @render "markdown"
    Template StoryMarkdown
}
```

---

## 10. 隐藏与注释

为了确保后台处理逻辑不会暴露给用户，crgLang 提供了 `@hidden` 和注释功能。

```crgLang
@hidden
Module HiddenModule {
    secret: UserInput secret: "请输入秘密信息"
}
```

---

## 11. 未来扩展

为进一步优化 crgLang 的灵活性和功能，未来可能添加以下功能：
1. **更复杂的条件逻辑**：允许基于更多条件的分支选择。
2. **内置模块库和模板库**：提供更多内置的模块和模板供用户直接调用。
3. **实时反馈机制**：让用户能够根据生成的内容实时提供反馈并调整生成结果。

---

## 许可证

**crgLang** 遵循 GNU通用公共许可证第3版（GNU General Public License v3.0，简称GPLv3）许可证。保护crgLang的自由和开放性，促进共享与合作。

---

## 联系方式

如需进一步咨询或建议，请通过 **61727091@qq.com** 联系我们，或访问我们的微信公众号 [Ai故事线](https://mp.weixin.qq.com/s/BoCCyXZrrbeKScsKvNxZsg)。