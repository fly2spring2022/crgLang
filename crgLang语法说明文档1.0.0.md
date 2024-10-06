### crgLang语法说明文档

## 目录
1. [概述](#概述)
2. [元数据声明](#元数据声明)
3. [模块结构](#模块结构)
   - [输入/输出类型定义](#输入输出类型定义)
4. [特殊模块](#特殊模块)
   - [初始化模块](#初始化模块)
   - [角色模块](#角色模块)
   - [主模块](#主模块)
   - [输出模块](#输出模块)
5. [执行序列与控制流](#执行序列与控制流)
6. [完整示例程序](#完整示例程序)
7. [联系方式](#联系方式)

---

## 概述
**crgLang** 是一种专为 AI Prompt 生成而设计的编程语言，面向自然语言处理中的大语言模型（如 GPT-4）的交互和应用。由于 crgLang 的解析器和编译器本身就是 AI 模型，所以它具备极大的灵活性，能够处理自然语言中的复杂表达，简化了代码执行的过程。

---

## 元数据声明

每个 crgLang 程序的开头必须包含元数据声明，用于定义程序的基本信息和运行所需的模型环境。

### 元数据语法

```plaintext
# METADATA
name: "程序名称"
version: "版本号"
author: "作者姓名"
date: "YYYY-MM-DD"
supported_models: ["模型A", "模型B"]
```

#### 说明：
- **name**: 程序名称，用于标识 crgLang 项目。
- **version**: 程序版本号，遵循语义化版本规范（如：1.0.0）。
- **author**: 作者信息，可以填写个人或团队名称。
- **date**: 程序创建或修改的日期。
- **supported_models**: 程序支持的 AI 大模型列表，指明该程序兼容的模型（如 GPT-4、ChatGPT）。

---

## 模块结构

crgLang 的每个模块都是程序的基本执行单元。每个模块接受输入，处理逻辑，返回输出结果。所有模块的首行都必须有描述该模块任务或功能的注释。

### 模块语法

```plaintext
def 模块名(input1, input2) {
    # 任务或功能描述
    // 实现代码
    return 输出结果;
}
```

#### 说明：
- **模块名**: 模块名称，用以标识模块的功能。
- **输入参数**: 每个模块可以接收一个或多个输入（可以是变量或自然语句描述）。
- **输出结果**: 每个模块处理后返回一个结果，该结果可传递给其他模块或作为最终输出。

---

### 输入/输出类型定义

crgLang 支持基本的数据类型，确保模块间数据的一致性。

#### 支持的类型：
- **string**: 字符串
- **int**: 整数
- **float**: 浮点数
- **boolean**: 布尔值（True/False）
- **list**: 列表
- **dict**: 字典（键值对）

#### 示例：

```plaintext
def exampleModule(input1: string, input2: int) {
    # 示例模块，返回组合后的字符串
    return "输入1是：" + input1 + "，输入2是：" + str(input2);
}
```

---

## 特殊模块

### 初始化模块

`init()` 模块是程序的起点，主要功能是展示程序的功能说明，提示用户输入，并提供初始界面。初始化模块为用户提供明确的交互内容和指引。

#### 初始化模块语法：

```plaintext
def init() {
    # 初始化任务，展示功能说明和用户提示
    return "欢迎使用此程序。该程序的功能是：生成AI Prompt。\n请输入您想要生成的内容：";
}
```

#### 示例：

```plaintext
def init() {
    # 初始化任务，提示用户输入
    return "欢迎使用AI Prompt生成器！请输入您希望生成的文章主题：";
}
```

---

### 角色模块

`roleModule()` 模块用于设定 prompt 中的角色，它的作用是帮助 AI 模型更好地理解执行任务的上下文。然而，该模块的返回内容不会直接显示给用户，它仅在后台起作用。需要注意的是，角色模块本身只是一个普通模块，因为它在AI prompt中充当了非常重要的元素，所以将它单独提取出来说明。

#### 角色模块语法：

```plaintext
def roleModule(role: string) {
    # 角色设定模块，用于设定 prompt 的角色
    return "角色设定为：" + role;  // 仅后台使用
}
```

#### 示例：

```plaintext
def roleModule(role: string) {
    # 设置为AI助手的角色
    return "角色设定为：AI助手";
}
```

---

### 主模块

`main()` 模块负责管理程序的主要逻辑，完成生成 AI Prompt 的主要任务。在此过程中，主模块会调用其他子模块来完成特定任务。主模块通常是整个程序的核心逻辑，负责串联并执行所有步骤。

#### 主模块语法：

```plaintext
def main() {
    # 主程序逻辑，负责生成最终的 prompt
}
```

#### 示例：

```plaintext
def main() {
    # 主程序，执行角色设定、用户输入解析并生成最终 prompt
    role = roleModule("AI助手");  # 后台设定角色
    userInput = "写一篇关于人工智能的文章";  # 假定用户输入
    parsedInput = parseUserInput(userInput);  # 解析用户输入
    intentPrompt = generateIntentPrompt(parsedInput);  # 根据解析生成 prompt

    # 输出最终结果
    output(intentPrompt);
}
```

---

### 输出模块

`output()` 模块用于处理程序的最终输出内容，通常将生成的 prompt 输出到控制台或其他指定目标。同样的，输出模块也仅是一个普通模块，鉴于它在AI prompt中的重要位置，所以单独提取出来说明。

#### 输出模块语法：

```plaintext
def output(data: string) {
    # 处理并输出最终结果
    print("最终生成的 prompt:\n" + data);
}
```

#### 示例：

```plaintext
def output(result: string) {
    # 输出生成的 prompt
    print("生成的 prompt 内容如下：\n" + result);
}
```

---

## 执行序列与控制流

crgLang 支持通过明确的执行序列来控制模块执行的顺序。执行序列部分决定了各模块的执行顺序，用户可以通过简单的 `execute` 语法来指定顺序。

### 执行序列语法：

```plaintext
# EXECUTION SEQUENCE
1. execute init();
2. execute main();
```

### 控制流语法：

crgLang 支持基本的控制流语句，如条件判断和循环控制。

```plaintext
if (条件) {
    # 条件为真时执行的逻辑
} else {
    # 条件为假时执行的逻辑
}
```

#### 示例：

```plaintext
def main() {
    # 主程序，执行角色设定、条件判断并生成 prompt
    role = "AI助手";
    if role == "AI助手":
        print("角色设定为 AI助手");
    else:
        print("角色设定未知");
}
```

---

## 完整示例程序

以下是一个完整的 crgLang 示例程序，展示了元数据声明、初始化模块、角色模块、主模块、输出模块以及执行序列的定义和使用：

```plaintext
# METADATA
name: "AI Prompt 生成器"
version: "1.1"
author: "开发者"
date: "2024-10-07"
supported_models: ["GPT-4", "Claude"]

def roleModule(role: string) {
    # 角色模块，用于后台设定角色
    return "角色设定为：" + role;
}

def parseUserInput(input: string) {
    # 用户输入解析模块，处理并返回解析后的信息
    return "解析后的信息：" + input;
}

def generateIntentPrompt(parsedInput: string) {
    # 意图生成模块，返回基于解析输入的 prompt
    return "根据用户意图生成的 prompt：" + parsedInput;
}

def init() {
    # 初始化模块，提示用户输入
    return "欢迎使用AI Prompt生成器！请输入您希望生成的文章主题：";
}

def output(result: string) {
    # 输出模块，输出最终生成的结果
    print("生成的 prompt 内容如下：\n" + result);
}

def main() {
    # 主模块，执行角色设定、用户输入解析并生成最终 prompt
    role = roleModule("AI助手");  # 后台设定角色
    userInput = "写一篇关于人工智能的文章";  # 假定用户输入
    parsedInput = parseUserInput(userInput);  # 解析用户输入
    intentPrompt = generateIntentPrompt(parsedInput);  # 根据解析生成 prompt
    output(intentPrompt);  # 输出最终结果
}

# EXECUTION SEQUENCE
1. execute init();
2. execute main();
```

---

## 未来扩展

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
