# File: prompt-engine/01_Prompt_DSL.md

# AFNL Prompt DSL
## 小说提示词语言（Novel Prompt Language）

Version 1.0

---

# 为什么需要 Prompt DSL？

目前 99% 的 AI 小说 Prompt 都长这样：

```
你是一名优秀小说家。

帮我写一篇都市甜文。

要求没有AI味。

人物真实。

剧情合理。

节奏快。

文笔优美。

```

这类 Prompt 最大的问题：

**没有结构。**

LLM（大语言模型）真正擅长的是：

> **解析结构化信息。**

而不是：

一大段自然语言。

所以 AFNL Novel Engine 引入：

# Prompt DSL（Domain Specific Language）

即：

小说专用提示词语言。

以后。

所有 Prompt 都采用统一格式。

AI 会稳定很多。

---

# 第一章｜DSL 基础结构

一个 Prompt 由九个模块组成。

```
META

WORLD

CHARACTER

RELATION

PLOT

STYLE

SCENE

RULE

OUTPUT
```

顺序固定。

不要乱。

---

# 第二章｜META

描述小说基本信息。

例如：

```yaml
META:

title:
《XXXX》

genre:
都市甜文

length:
20000

platform:
番茄

reader:
18-35女性

view:
第三人称

tense:
过去式

ending:
HE
```

所有章节。

默认继承 META。

---

# 第三章｜WORLD

描述世界。

例如：

```yaml
WORLD:

time:
现代

city:
杭城

society:
正常现代社会

magic:
false

cultivation:
false

technology:
2025
```

如果是修仙：

```yaml
WORLD:

realm:
九州

cultivation:
true

sects:
九大仙门

immortal:
true
```

---

# 第四章｜CHARACTER

采用固定格式。

例如：

```yaml
CHARACTER:

FL:

name:
沈知夏

age:
25

job:
程序员

goal:
创业

fear:
失败

flaw:
嘴硬

habit:
喝热牛奶

love_language:
行动

growth:
学会依赖别人
```

男主：

```yaml
ML:

type:
男妈妈

career:
医生

habit:
做饭

weakness:
过度照顾别人

core:
稳定
```

---

# 第五章｜RELATION

不要让 AI 自己推关系。

全部写清楚。

例如：

```yaml
RELATION:

FL -> ML

first_impression:
温柔

current:
普通朋友

future:
恋人

conflict:
事业

trust:
20/100
```

AI 可以直接计算关系变化。

---

# 第六章｜PLOT

不要写：

```
剧情合理。
```

要写：

```yaml
PLOT:

opening:
女主失业

hook:
误进相亲局

midpoint:
发现男主身份

climax:
创业失败

ending:
共同创业成功
```

故事。

立即稳定。

---

# 第七章｜STYLE

最重要。

例如：

```yaml
STYLE:

pace:
快

emotion:
细腻

dialogue:
自然

description:
克制

humor:
轻松

romance:
慢热

prose:
生活化
```

不要写：

```
文笔优美。
```

AI 不知道什么叫优美。

---

# 第八章｜SCENE

当前章节。

只描述这一章。

例如：

```yaml
SCENE:

location:
咖啡店

time:
晚上

weather:
下雨

goal:
第一次约会

conflict:
误会

emotion:
暧昧
```

这样。

AI 不会乱写。

---

# 第九章｜RULE

整个系统最重要。

例如：

```yaml
RULE:

禁止：

直接表白

禁止：

解释人物心理

禁止：

连续内心戏

禁止：

连续环境描写

使用：

动作推动

对白推进

细节表达
```

RULE 永远最后。

优先级最高。

---

# 第十章｜OUTPUT

输出格式。

例如：

```yaml
OUTPUT:

chapter:
8

length:
1800

ending:
留悬念

markdown:
true
```

AI 输出会稳定很多。

---

# 第十一章｜完整 Prompt 示例

```yaml
META:
...

WORLD:
...

CHARACTER:
...

RELATION:
...

PLOT:
...

STYLE:
...

SCENE:
...

RULE:
...

OUTPUT:
...
```

整个 Prompt：

不到两页。

比自然语言稳定得多。

---

# 第十二章｜Prompt Compiler

以后。

用户不用写 Prompt。

只填写：

人物卡。

世界观。

剧情。

然后：

Compiler 自动生成：

完整 Prompt。

例如：

```
人物数据库

+

剧情数据库

+

风格数据库

+

规则数据库

↓

Prompt DSL

↓

LLM

↓

正文
```

整个过程。

完全自动。

---

# 第十三章｜Prompt 分层

推荐四层。

```
System Prompt

↓

Project Prompt

↓

Novel Prompt

↓

Chapter Prompt
```

System：

永远固定。

Project：

整个项目固定。

Novel：

一本书固定。

Chapter：

每章变化。

这样：

AI 一致性最高。

---

# 第十四章｜变量系统

支持变量。

例如：

```yaml
{{FL_NAME}}

{{ML_NAME}}

{{CURRENT_RELATION}}

{{TRUST}}

{{ROMANCE_LEVEL}}

{{CHAPTER_GOAL}}
```

Prompt 可重复使用。

---

# 第十五章｜Novel Engine 流程

```
数据库

↓

Prompt DSL

↓

Compiler

↓

LLM

↓

Consistency Checker

↓

Rewrite Engine

↓

最终章节
```

Prompt：

只是中间层。

真正价值。

来自数据库。

---

# AFNL 创作法则 No.022

> 不要写 Prompt。

> 要设计 Prompt。

> Prompt 不是一句话。

> Prompt 是一门语言。

End.
