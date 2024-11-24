# 心灵手巧 🧠⛏️

使用LLMs和Mineflayer为《我的世界》打造智能模组！

[常见问题解答](https://github.com/kolbytn/mindcraft/blob/main/FAQ.md) | [Discord 支持](https://discord.gg/mp73p35dzC) | [博客文章](https://kolbynottingham.com/mindcraft/) | [贡献者待办事项](https://github.com/users/kolbytn/projects/1)

####‼️警告

请勿将此机器人连接到启用了编码功能的公共服务器。该项目允许LLM在您的计算机上编写/执行代码。尽管代码被沙盒化，但在公共服务器上仍然容易受到注入攻击。默认情况下，代码编写功能被禁用，您可以通过在`settings.js`中将`allow_insecure_coding`设置为`true`来启用它。我们强烈建议您使用docker容器等额外的安全层来运行。请注意。

##要求

- [Minecraft Java Edition](https://www.minecraft.net/en-us/store/minecraft-java-bedrock-edition-pc)（最高版本为v1.21.1，建议使用v1.20.4）
- [已安装Node.js](https://nodejs.org/)（版本至少为v14）
- 其中之一：[OpenAI API Key](https://openai.com/blog/openai-api) | [Gemini API Key](https://aistudio.google.com/app/apikey) | [Anthropic API Key](https://docs.anthropic.com/claude/docs/getting-access-to-claude) | [Replicate API Key](https://replicate.com/) | [Hugging Face API Key](https://huggingface.co/) | [Groq API Key](https://console.groq.com/keys) | [Ollama已安装](https://ollama.com/download). | [Qwen API Key [国际版]](https://www.alibabacloud.com/help/en/model-studio/developer-reference/get-api-key)/[[中文版]](https://help.aliyun.com/zh/model-studio/getting-started/first-api-call-to-qwen?) | [Novita AI API Key](https://novita.ai/settings?utm_source=github_mindcraft&utm_medium=github_readme&utm_campaign=link#key-management) |

## 安装与运行

1. 确保你满足上述要求。

2. 克隆或下载此仓库（绿色大按钮）

3. 将`keys.example.json`重命名为`keys.json`，并填写您的API密钥（您只需要一个）。所需的模型在`andy.json`或其他配置文件中设置。对于其他模型，请参考下表。

4. 在终端/命令提示符中，从已安装的目录运行`npm install`

5. 启动一个《我的世界》世界，并将其在本地主机端口“55916”上设置为局域网模式

6. 在安装目录下运行`node main.js`

如果你遇到问题，请查阅[常见问题解答](https://github.com/kolbytn/mindcraft/blob/main/FAQ.md)或在[Discord](https://discord.gg/jVxQWVTM)上寻求支持。目前，我们对GitHub上的问题回复可能不够及时。

##定制化

你可以在`settings.js`中配置项目细节。[查看文件。](settings.js)

你可以在他们的配置文件（如`andy.json`）中配置代理的名称、模型和提示。

| API | 配置变量 | 示例模型名称 | 文档 |
|------|------|------|------|
| OpenAI | `OPENAI_API_KEY` | `gpt-4o-mini` | [文档](https://platform.openai.com/docs/models) |
| Google | `GEMINI_API_KEY` | `gemini-pro` | [文档](https://ai.google.dev/gemini-api/docs/models/gemini) |
| Anthropic | `ANTHROPIC_API_KEY` | `claude-3-haiku-20240307` | [文档](https://docs.anthropic.com/claude/docs/models-overview) |
| 复制 | `REPLICATE_API_KEY` | `meta/meta-llama-3-70b-instruct` | [文档](https://replicate.com/collections/language-models) |
| Ollama（本地） | n/a | `llama3` | [文档](https://ollama.com/library) |
| Groq | `GROQCLOUD_API_KEY` | `groq/mixtral-8x7b-32768` | [文档](https://console.groq.com/docs/models) |
| Hugging Face | `HUGGINGFACE_API_KEY` | `huggingface/mistralai/Mistral-Nemo-Instruct-2407` | [文档](https://huggingface.co/models) |
| Novita AI | `NOVITA_API_KEY` | `gryphe/mythomax-l2-13b` | [文档](https://novita.ai/model-api/product/llm-api?utm_source=github_mindcraft&utm_medium=github_readme&utm_campaign=link) |
| Qwen | `QWEN_API_KEY` | `qwen-max` | [国际版](https://www.alibabacloud.com/help/en/model-studio/developer-reference/use-qwen-by-calling-api)/[中文版](https://help.aliyun.com/zh/model-studio/getting-started/models) |
| xAI | `XAI_API_KEY` | `grok-beta` | [文档](https://docs.x.ai/docs) |

如果你使用Ollama，要安装默认使用的模型（生成和嵌入），请执行以下终端命令：
`ollama pull llama3 && ollama pull nomic-embed-text`

## 在线服务器
要连接到在线服务器，你的机器人需要一个官方的Microsoft/Minecraft账户。你可以使用你自己的个人账户，但如果你想同时连接并与之游戏，则需要另一个账户。要进行连接，请在`settings.js`中更改以下行：
```javascript
“主机”：“111.222.333.444”，
“端口”：55920，
“auth”：“microsoft”，

// 其余部分相同。。。
```
‼️ profile.json中的机器人名称必须与Minecraft中的个人资料名称完全匹配！否则机器人会自言自语。

要使用不同的账户，Mindcraft将连接到Minecraft启动器当前正在使用的账户。你可以在启动器中切换账户，然后运行`node main.js`，待机器人连接成功后，再切换到你的主账户。

### Docker容器

如果你打算启用`allow_insecure_coding`，建议在docker容器中运行应用程序，以降低运行未知代码的风险。在连接到远程服务器之前，强烈建议这样做。

```bash
docker run -i -t --rm -v $(pwd):/app -w /app -p 3000-3003:3000-3003 node:latest node main.js
```
或者简单地说
```bash
docker组成
```

在docker中运行时，如果你想让机器人加入你的本地《我的世界》服务器，你需要使用一个特殊的主机地址`host.docker.internal`来从docker容器内部调用localhost。将此地址添加到你的[settings.js](settings.js)文件中：

```javascript
"host": "host.docker.internal", // 而不是 "localhost"，用于从docker容器内部加入本地《我的世界》游戏
```

若要连接到不受支持的Minecraft版本，您可以尝试使用[viaproxy](services/viaproxy/README.md)

## 机器人配置文件

机器人配置文件是JSON文件（例如“andy.json”），它们定义了：

1. 用于聊天和嵌入的机器人后端大型语言模型（LLMs）。
2. 用于影响机器人行为的提示。
3. 示例有助于机器人执行任务。

### 通过命令行指定配置文件

默认情况下，程序将使用`settings.js`中指定的配置文件。您可以使用`--profiles`参数指定一个或多个代理配置文件：

```bash
使用main.js节点，并加载./profiles/andy.json和./profiles/jill.json两个配置文件
```

### 模型规格

LLM后端可以简单指定为“model”: “gpt-3.5-turbo”。然而，对于聊天模型和嵌入模型，机器人配置文件可以指定以下属性：

```json
"model": {
  "api": "openai",
  "url": "https://api.openai.com/v1/",
  "model": "gpt-3.5-turbo"
},
"embedding": {
  "api": "openai",
  "url": "https://api.openai.com/v1/",
  "model": "text-embedding-ada-002"
}
```

模型参数可以接受字符串或对象。如果是字符串，则应指定要使用的模型。此时，api和url将被假定。如果是对象，则必须指定api字段。每个api都有默认的模型和url，因此这些字段是可选的。

如果未指定嵌入字段，则将使用聊天模型API的默认嵌入方法（请注意，anthropic没有嵌入模型）。嵌入参数也可以是字符串或对象。如果是字符串，则应指定嵌入API和默认模型，并将使用URL。如果未指定有效的嵌入且无法假设，则将使用单词重叠来检索示例。

因此，以下所有规格都与上述示例等效：

```json
"model": "gpt-3.5-turbo"
```
```json
"model": {
  "api": "openai"
}
```
```json
"model": "gpt-3.5-turbo",
"embedding": "openai"
```

## 补丁

我们依赖的一些节点模块中存在bug。要添加补丁，请修改您本地的节点模块文件，然后运行`npx patch-package [package-name]`

## 引文：

```
@misc{mindcraft2023,
    Author = {Kolby Nottingham and Max Robinson},
    Title = {MINDcraft: LLM Agents for cooperation, competition, and creativity in Minecraft},
    Year = {2023},
    url={https://github.com/kolbytn/mindcraft}
}
```
