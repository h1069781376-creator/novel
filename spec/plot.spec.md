# File: spec/plot.spec.md

# AFNL Novel Specification
## Plot Specification（剧情数据规范）

Version 1.0

Status: Stable

---

# 1. 为什么需要 Plot Spec？

AI 最大的问题不是不会写剧情。

而是：

**不会管理剧情。**

典型情况：

```
第一章

埋伏笔

↓

第五章

忘记

↓

第十章

重新埋一个新的

↓

最后

全部烂尾
```

原因很简单。

AI 没有：

> 剧情状态（Story State）

所以 Novel Engine 规定：

**剧情必须数据化。**

不是写：

```
这里发生了什么。
```

而是记录：

```
为什么发生

发生以后改变了什么

下一步会影响什么
```

---

# 2. Plot ID

所有剧情节点。

都有唯一ID。

```yaml
id: PLOT000001
```

整个故事。

由多个 Plot Node 组成。

---

# 3. Plot Node

每个剧情。

必须拥有：

```yaml
plot:

id:

title:

chapter:

status:
```

status：

```
Planning

Running

Finished

Dropped
```

---

# 4. Purpose（剧情目的）

最重要。

每一个剧情。

至少完成一件事情。

```yaml
purpose:

world

character

relationship

conflict

foreshadow

emotion
```

例如：

第一次约会。

目的：

```
relationship
```

不是：

吃饭。

---

# 5. Trigger（触发）

为什么发生？

```yaml
trigger:

who

when

where

why
```

例如：

```
女主加班。

↓

男主送饭。

```

不是随机。

而是：

有原因。

---

# 6. Conflict（冲突）

没有冲突。

不是剧情。

```yaml
conflict:

external:

internal:

hidden:
```

例如：

```
external

竞争公司。

internal

女主害怕失败。

hidden

男主身份。
```

---

# 7. Stakes（代价）

如果失败。

会失去什么？

```yaml
stakes:

money

life

career

relationship

identity
```

没有代价。

读者不会紧张。

---

# 8. Turning Point（转折）

所有剧情。

必须发生变化。

```yaml
turning:

before:

event:

after:
```

例如：

```
陌生人

↓

一起加班

↓

朋友
```

关系变化。

就是剧情。

---

# 9. Relationship Impact

剧情。

改变关系。

```yaml
relationship:

FL_ML:

before:

20

after:

35

reason:
```

例如：

```
共同解决项目。
```

以后。

所有章节。

读取：

最新关系值。

---

# 10. Character Impact

谁成长？

```yaml
growth:

character:

change:

score:
```

例如：

```
自信

20

↓

28
```

如果：

没有成长。

建议：

删除剧情。

---

# 11. Emotion Curve

记录：

这一段情绪。

```yaml
emotion:

start:

middle:

end:
```

例如：

```
尴尬

↓

轻松

↓

心动
```

情绪必须变化。

---

# 12. Foreshadow

伏笔。

不能忘。

```yaml
foreshadow:

plant:

chapter:

payoff:

chapter:

status:
```

例如：

```
Plant

3

↓

Payoff

18
```

Checker：

自动提醒。

---

# 13. Information Flow

读者。

什么时候知道？

人物。

什么时候知道？

```yaml
information:

reader:

FL:

ML:

villain:
```

例如：

```
读者知道。

女主不知道。

```

形成：

戏剧张力。

---

# 14. Scene Dependency

当前剧情。

依赖哪些剧情？

```yaml
dependency:

need:

unlock:
```

例如：

```
Need:

PLOT003

Unlock:

PLOT008
```

没有前置。

不能触发。

---

# 15. Output State

剧情结束以后。

世界发生变化。

```yaml
output:

world:

character:

relation:

timeline:
```

例如：

```
关系：

35

↓

52
```

下一章：

直接读取。

---

# 16. Plot Validation

必须满足：

```
有目的

√
```

```
有冲突

√
```

```
有变化

√
```

```
有结果

√
```

否则。

不是剧情。

只是：

流水账。

---

# 17. Plot Graph

剧情之间。

形成图。

例如：

```
P1

↓

P2

↓

P5

↓

Ending
```

而不是：

线性文本。

以后。

AI。

可以自动寻找：

断链剧情。

---

# 18. Example

```yaml
id: PLOT0012

title:
第一次约会

purpose:
relationship

trigger:
男主邀请

conflict:
双方紧张

turning:
陌生
→
熟悉

emotion:
尴尬
→
轻松
→
心动

relationship:
20
→
35

foreshadow:
Plant:
围巾

Payoff:
第17章
```

---

# 19. Novel Engine Workflow

```
Plot Spec

↓

Story Planner

↓

Chapter Planner

↓

Scene Planner

↓

Prompt Compiler

↓

正文
```

剧情。

先规划。

再生成。

---

# 20. AFNL Plot Principle

> 剧情不是发生了什么。

> 剧情是：

> **发生之后。**

> **什么改变了。**

> 如果没有改变。

> 就没有剧情。

End.
