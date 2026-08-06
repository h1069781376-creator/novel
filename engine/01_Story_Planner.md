# File: engine/01_Story_Planner.md

# AFNL Novel Engine
## Story Planner（故事规划引擎）

Version 1.0

Status: Core Engine

---

# 0. Story Planner 的职责

Story Planner 不是写正文。

Story Planner 负责回答一个问题：

> **这本小说，为什么值得读完？**

它的输出不是章节。

不是对白。

不是文笔。

而是一份：

```
Story Blueprint（故事蓝图）
```

后续：

Chapter Planner

↓

Scene Planner

↓

Prompt Compiler

全部依赖：

Story Blueprint。

---

# 1. 输入（Input）

Story Planner 接收：

```
Character Spec

+

World Spec

+

Plot Requirement

+

Platform Requirement

+

Length Requirement

+

Theme
```

例如：

```yaml
theme:
女性成长

genre:
都市甜文

platform:
番茄

length:
20000

ending:
HE
```

---

# 2. 输出（Output）

输出：

Story Blueprint。

包含：

```yaml
Story Blueprint

Logline

Core Conflict

Story Question

Selling Point

Theme

Acts

Ending

Foreshadow Plan
```

Story Planner。

不会生成正文。

---

# 3. 第一步：Logline

一句话。

必须满足：

```
人物

+

目标

+

阻碍

+

代价
```

模板：

```
当【人物】

因为【事件】

必须完成【目标】

否则【代价】

最终面对【主题】。
```

例如：

```
一位社恐程序员穿进女尊王朝，

必须在三个月内成为摄政王，

否则系统将永久抹除她，

最终她必须决定：

建立一个属于所有人的世界，

还是继续统治。
```

---

# 4. 第二步：Story Question

整本小说。

只有一个核心问题。

例如：

```
她能不能改变这个王朝？
```

不要：

三个。

五个。

十个。

一个。

贯穿全文。

---

# 5. 第三步：Theme

主题。

不是题材。

例如：

错误：

```
穿越
```

正确：

```
成长

自由

责任

信任

选择
```

一本短篇。

建议：

一个主题。

最多两个。

---

# 6. 第四步：Core Conflict

冲突。

统一管理。

```yaml
external:

internal:

relationship:

world:
```

例如：

External：

皇权斗争。

Internal：

不敢相信别人。

Relationship：

男主身份。

World：

制度压迫。

---

# 7. 第五步：Selling Point

Story Planner。

必须提炼：

一句卖点。

例如：

```
全天下都认为男子不能读书。

她偏偏建了一座男子书院。
```

卖点：

一句话。

即可传播。

---

# 8. 第六步：Story Beats

采用统一节点。

推荐：

12 Beat。

```text
Opening

↓

Inciting Incident

↓

First Choice

↓

Midpoint

↓

Lowest Point

↓

Climax

↓

Resolution
```

所有章节。

映射。

到：

Beat。

---

# 9. 第七步：Emotion Curve

Story Planner。

生成：

整本书情绪曲线。

例如：

```
陌生

↓

好奇

↓

依赖

↓

误会

↓

成长

↓

告白

↓

高潮

↓

治愈
```

不是：

章节情绪。

而是：

整本书。

---

# 10. 第八步：Relationship Curve

关系。

统一变化。

例如：

```yaml
Chapter

1

Relation

0

----------------

5

25

----------------

10

48

----------------

15

72

----------------

20

100
```

避免：

一见钟情。

第二章：

生死相许。

---

# 11. 第九步：Growth Curve

每位主要角色。

都有成长曲线。

例如：

```yaml
FL

Confidence

20

↓

95

Trust

5

↓

80

Leadership

15

↓

90
```

成长：

必须可追踪。

---

# 12. 第十步：Foreshadow Planner

统一规划。

例如：

```yaml
Plant

Chapter3

↓

Mention

Chapter8

↓

Reminder

Chapter15

↓

Payoff

Chapter19
```

伏笔。

不是灵感。

是计划。

---

# 13. 第十一步：Ending Planner

Story Planner。

一开始。

就决定：

结局。

例如：

```yaml
Ending:

HE

Theme Completed:

Freedom

Relationship:

100

World Changed:

Yes
```

否则：

容易烂尾。

---

# 14. Story Blueprint 示例

```yaml
title:
《凤归》

theme:
自由

story_question:
她能否改变女尊制度？

selling_point:
建立男子书院

acts:

Act1:
进入王朝

Act2:
建立书院

Act3:
推翻旧制度

ending:
HE
```

---

# 15. Story Planner 与其它模块

```
Character Spec

↓

Story Planner

↓

Story Blueprint

↓

Chapter Planner

↓

Scene Planner

↓

Prompt Compiler

↓

LLM

↓

Rewrite Engine
```

Story Planner。

是整个系统。

真正的入口。

---

# 16. Validation

Story Blueprint。

必须满足：

```
Logline

√
```

```
Theme

√
```

```
Conflict

√
```

```
Emotion Curve

√
```

```
Ending

√
```

否则。

不能进入：

Chapter Planner。

---

# 17. Story State

Story Planner。

生成：

全局状态。

例如：

```yaml
story_state:

progress:

0%

relationship:

0

world_state:

Peace

theme_progress:

0%
```

Chapter Planner。

持续更新。

---

# 18. Engine Rule

Story Planner。

永远不能：

生成正文。

职责：

只有：

规划。

生成正文。

属于：

Chapter Generator。

---

# 19. AFNL Story Principle

> 好故事。

> 从来不是：

> 写出来的。

> 而是：

> **设计出来的。**

> 当故事结构成立。

> 文笔只是放大器。

End.
