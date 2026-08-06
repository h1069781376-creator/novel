# File: architecture/NovelEngineArchitecture.md

# Novel Engine
## System Architecture（系统架构设计）

Version 4.0

Status: Core

---

# 0、为什么要重新设计？

目前市面上99%的 AI 小说工作流都是：

```
Prompt

↓

LLM

↓

小说
```

Claude

↓

小说

ChatGPT

↓

小说

Gemini

↓

小说

DeepSeek

↓

小说

这种模式有一个共同的问题：

AI负责了所有事情。

于是：

- 世界观忘了
- 人设崩了
- 伏笔没收
- 节奏乱了
- 后期AI味越来越重

所以

Novel Engine 的核心思想只有一句话：

> **LLM 只是文字生成器。**

真正的大脑。

应该属于 Engine。

---

# 1、总体架构

```
                        Novel Project
                              │
                              │
             ┌────────────────┴────────────────┐
             │                                 │
      Project Configuration              Global Memory
             │                                 │
             └──────────────┬──────────────────┘
                            │
                     Story Planner
                            │
                    Story Blueprint
                            │
          ┌─────────────────┼──────────────────┐
          │                 │                  │
     Character Engine   World Engine     Plot Engine
          │                 │                  │
          └─────────────────┼──────────────────┘
                            │
                     Chapter Planner
                            │
                     Scene Planner
                            │
                    Context Builder
                            │
                    Prompt Compiler
                            │
                            ▼
                     Large Language Model
                            │
                     Draft Chapter
                            │
        ┌───────────────────┼──────────────────┐
        │                   │                  │
Consistency Checker   AI Smell Checker   Rewrite Engine
        │                   │                  │
        └───────────────────┼──────────────────┘
                            │
                       Final Chapter
                            │
                    Story State Update
                            │
                     Memory Database
```

---

# 2、整个系统分层

整个 Engine 分为六层。

```
Layer 1

Specification
```

↓

```
Layer 2

Database
```

↓

```
Layer 3

Planner
```

↓

```
Layer 4

Compiler
```

↓

```
Layer 5

Generator
```

↓

```
Layer 6

Checker
```

---

# 第一层

Specification

定义：

世界是什么。

人物是什么。

剧情是什么。

例如：

```
character.spec

world.spec

scene.spec

dialogue.spec
```

这一层：

永远不写正文。

---

# 第二层

Database

真正的数据。

例如：

```
角色

剧情

对白

动作

微表情

场景

名场面

修仙体系

朝代制度
```

所有Prompt。

全部来自数据库。

不是自由发挥。

---

# 第三层

Planner

负责：

规划。

例如：

```
Story Planner

↓

Chapter Planner

↓

Scene Planner
```

Planner：

永远不生成正文。

只生成：

Blueprint。

---

# 第四层

Compiler

负责：

拼装Prompt。

例如：

```
Character

+

Scene

+

Rule

+

Style

+

Memory

↓

Prompt
```

Prompt：

自动生成。

用户。

不用写。

---

# 第五层

Generator

这里只有：

LLM。

例如：

```
GPT

Claude

Gemini

DeepSeek

Qwen
```

Engine：

不关心。

谁来写。

只关心：

输入。

输出。

---

# 第六层

Checker

AI写完以后。

进入：

```
Consistency

↓

AI Smell

↓

Rewrite

↓

Score
```

如果：

低于标准。

重新生成。

直到：

PASS。

---

# 3、Story State

这是整个系统。

真正核心。

任何时候。

只有一个：

Story State。

例如：

```yaml
StoryState:

CurrentChapter:12

CurrentScene:3

Relationship:

FL_ML:68

Emotion:

FL:

Nervous

ML:

Happy

World:

War

Timeline:

Day17

Foreshadow:

Ring

Hidden

StoryProgress:

61%
```

所有Engine。

共享。

StoryState。

---

# 4、Memory Database

Memory。

不是聊天记录。

Memory。

是小说状态。

例如：

```
Character Memory

↓

World Memory

↓

Story Memory

↓

Scene Memory

↓

Reader Memory
```

每写一章。

更新一次。

---

# 5、Character Engine

输入：

```
Character Spec
```

输出：

```
Character State
```

例如：

```
Confidence

↓

25

↓

31

↓

40
```

成长。

全部自动维护。

---

# 6、World Engine

维护：

```
国家

时间

战争

天气

修仙等级

货币

交通
```

所有Scene。

统一读取。

---

# 7、Plot Engine

维护：

```
剧情节点

↓

伏笔

↓

高潮

↓

回收
```

AI：

不能忘。

---

# 8、Scene Engine

每章。

拆成Scene。

例如：

```
Chapter8

↓

Scene1

办公室

↓

Scene2

咖啡厅

↓

Scene3

天桥
```

Prompt：

一次。

只写：

一个Scene。

质量最高。

---

# 9、Prompt Compiler

输入：

```
Scene

+

Character

+

Rule

+

Memory

↓

Prompt
```

Prompt。

自动生成。

用户。

永远不用写。

---

# 10、Rewrite Pipeline

第一次：

AI。

生成。

↓

Consistency。

↓

Rewrite。

↓

AI Smell。

↓

Rewrite。

↓

Score。

↓

PASS。

↓

Final。

不是：

一次完成。

而是：

循环。

---

# 11、Project Structure

```
NovelEngine

├── architecture
├── spec
├── schema
├── database
├── engine
├── workflow
├── compiler
├── checker
├── rewrite
├── style
├── template
├── docs
└── examples
```

---

# 12、Novel Project

每一本小说。

都是：

```
project/

config.yaml

story.yaml

characters/

world/

outline/

chapters/

memory/

cache/

export/
```

项目。

完全独立。

---

# 13、最大的设计思想

以前：

```
Prompt

↓

AI
```

以后：

```
Specification

↓

Database

↓

Planner

↓

State

↓

Compiler

↓

LLM

↓

Checker

↓

Rewrite

↓

Publish
```

LLM。

只是：

整个流水线。

其中一步。

---

# 14、未来可扩展接口

Engine 可以扩展：

```
Visual Novel

↓

漫画脚本

↓

有声小说

↓

短剧剧本

↓

动画脚本

↓

游戏剧情
```

因为：

Story Blueprint。

是统一的。

---

# 15、AFNL Engine Principle

> 小说不是Prompt。

> 小说不是AI。

> 小说是一套持续演化的数据流。

> Engine负责思考。

> LLM负责表达。

> 当二者分离。

> AI写作才真正进入工程时代。

End.
