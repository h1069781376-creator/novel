# File: spec/character.spec.md

# AFNL Novel Specification
## Character Specification（人物数据规范）

Version 1.0

Status: Stable

---

# 1. 为什么需要 Character Spec？

传统小说写作：

```
姓名：

沈知夏

年龄：

24

职业：

医生
```

结束。

但是 AI 无法真正理解一个人物。

因为：

人物不是资料。

人物是：

```
过去

↓

现在

↓

未来
```

所以。

Novel Engine 使用：

Character Specification。

简称：

Character Spec。

---

# 2. Character ID

所有人物。

必须拥有唯一ID。

例如：

```yaml
id: CH000001
```

全文。

永远引用：

ID。

不要引用：

姓名。

因为：

姓名可能修改。

ID 不会。

---

# 3. Basic Info

```yaml
basic:

name:

gender:

age:

birthday:

height:

weight:

occupation:

race:

faction:

status:
```

status：

例如：

```
Alive

Dead

Missing

Retired

Unknown
```

---

# 4. Appearance

不要写：

```
很好看。
```

必须拆开。

```yaml
appearance:

hair:

eye:

skin:

voice:

posture:

walking_style:

clothing_style:

recognition:
```

recognition：

最容易认出来的特点。

例如：

```
右眼泪痣

银发

耳钉

总穿白衬衫
```

---

# 5. Personality

禁止：

```
温柔。

善良。

独立。
```

必须结构化。

```yaml
personality:

core:

strength:

weakness:

fear:

desire:

boundary:

temper:

confidence:
```

例如：

confidence：

```
20/100
```

---

# 6. Habit

```yaml
habit:

drink:

food:

sleep:

sport:

reading:

music:

pet:

collect:

daily_action:
```

daily_action：

每天都会做的事情。

例如：

```
睡前看书

晨跑

写日记

喝热牛奶
```

---

# 7. Speech Pattern

这是 AI 最容易忽略。

也是最重要。

```yaml
speech:

speed:

tone:

favorite_words:

taboo_words:

emoji_style:

humor:

curse:
```

例如：

favorite_words：

```
好的。

嗯。

知道了。
```

不要：

每个人。

说一样的话。

---

# 8. Value

人物真正核心。

```yaml
value:

life:

love:

family:

career:

money:

justice:

freedom:

power:
```

例如：

money：

```
40/100
```

代表：

赚钱重要。

但不是人生全部。

---

# 9. Ability

```yaml
ability:

combat:

academic:

social:

leadership:

creativity:

medical:

business:

craft:
```

全部：

100分制。

AI 更容易保持一致。

---

# 10. Relationship

```yaml
relation:

father:

mother:

teacher:

friend:

enemy:

lover:

subordinate:
```

全部：

引用：

Character ID。

不要写名字。

---

# 11. Story Role

```yaml
story:

importance:

arc:

entry:

exit:

mission:

ending:
```

arc：

例如：

```
成长

救赎

黑化

治愈

复仇
```

---

# 12. Growth

成长必须数字化。

例如：

```yaml
growth:

confidence:

20

↓

85

trust:

5

↓

95

independence:

40

↓

100
```

AI：

终于知道：

人物成长。

---

# 13. Emotion Trigger

记录：

什么事情。

最容易影响人物。

```yaml
trigger:

cry:

anger:

fear:

joy:

love:
```

例如：

cry：

```
被误解
```

anger：

```
欺负弱者
```

---

# 14. Secret

```yaml
secret:

known_by:

hidden:

exposed:

chapter:
```

例如：

第18章。

秘密曝光。

AI。

不会提前剧透。

---

# 15. Forbidden

非常重要。

```yaml
forbidden:

never_do:

never_say:

never_choose:
```

例如：

never_do：

```
主动背叛朋友
```

即使剧情变化。

AI 也不能违反。

除非：

人物成长。

修改：

Spec。

---

# 16. Character State

每章结束。

更新一次。

```yaml
state:

chapter:

location:

emotion:

injury:

relationship:

goal:
```

例如：

```
Chapter:

18

Emotion:

失落

Goal:

找到姐姐
```

下一章。

直接读取。

---

# 17. Validation Rule

Character Spec。

必须满足：

```
唯一ID

√
```

```
至少一个缺点

√
```

```
至少三个习惯

√
```

```
成长目标

√
```

```
不能只有优点

√
```

否则：

Validation：

Fail。

---

# 18. Character Example

```yaml
id: CH000021

basic:
  name: 林照雪
  age: 26
  occupation: 药师

personality:
  core: 冷静
  weakness: 不会求助
  fear: 成为负担

habit:
  drink: 热茶
  reading: 医书
  daily_action:
    - 睡前整理药箱

speech:
  favorite_words:
    - 好
    - 稍等

value:
  freedom: 95

growth:
  trust:
    from: 20
    to: 90

forbidden:
  never_do:
    - 滥用医术
```

---

# 19. Novel Engine 调用方式

```
Character Spec

↓

Prompt Compiler

↓

Scene Generator

↓

Dialogue Generator

↓

Consistency Checker

↓

Rewrite
```

整个流程。

统一读取：

Character Spec。

---

# AFNL Character Design Principle

> 人物不是名字。

> 人物不是设定。

> 人物是一组持续变化的数据。

> 当 AI 能理解数据。

> 它才能保持人物的一致性。

End.
