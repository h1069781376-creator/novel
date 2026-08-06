# File: spec/world.spec.md

# AFNL Novel Specification
## World Specification（世界观数据规范）

Version 1.0

Status: Stable

---

# 1. 为什么需要 World Spec？

AI 最容易犯的错误之一：

**世界观漂移（World Drift）**

例如：

第一章：

```
这是一个普通现代都市。
```

第二十章：

```
有人开始御剑飞行。
```

或者：

第一章：

```
修仙界没有手机。
```

第十五章：

```
大家在微信群聊天。
```

问题不是创意。

而是：

**规则改变了。**

所以，Novel Engine 规定：

> **世界观不是背景。**
>
> **世界观是一套不可随意违反的规则系统。**

---

# 2. World ID

每个世界必须拥有唯一 ID。

```yaml
id: WORLD000001
```

一本小说只能绑定一个主世界。

如果涉及平行世界、穿越、多重宇宙，则建立多个 World Spec。

---

# 3. Basic Information

```yaml
basic:

name:

genre:

era:

technology:

magic:

cultivation:

civilization_level:

status:
```

示例：

```yaml
basic:

name: 九霄大陆

genre: 修仙

era: 架空

technology: 农耕文明

magic: true

cultivation: true

civilization_level: 中世纪

status: Active
```

---

# 4. Geography

地图不是图片。

而是数据。

```yaml
geography:

continents:

countries:

cities:

sects:

danger_zone:

forbidden_land:
```

例如：

```yaml
cities:

- 天启城
- 云梦州
- 长安

sects:

- 青云宗
- 天剑宗
- 药王谷
```

---

# 5. Political System

```yaml
politics:

system:

leader:

succession:

law:

tax:

army:

religion:
```

例如：

```yaml
system: 女尊帝国

leader: 女帝

succession: 世袭

law:

- 男子可入仕
- 禁止买卖人口
```

---

# 6. Economy

AI 经常忘记：

人物的钱哪来的。

建立统一经济系统。

```yaml
economy:

currency:

income:

consumption:

luxury:

poverty:

trade:
```

例如：

```yaml
currency:

银两

金币

灵石
```

现代：

```yaml
currency:

人民币
```

---

# 7. Technology

统一技术树。

```yaml
technology:

transport:

communication:

medical:

weapon:

industry:

education:
```

例如：

现代：

```
高铁

手机

互联网
```

修仙：

```
飞舟

传音符

丹药
```

不能混。

除非设定允许。

---

# 8. Power System

这是修仙小说核心。

统一规范。

```yaml
power:

energy:

realm:

limit:

breakthrough:

price:
```

例如：

```yaml
realm:

炼气

筑基

金丹

元婴

化神
```

price：

突破代价。

例如：

寿命。

雷劫。

资源。

---

# 9. Social Rules

世界运行规则。

```yaml
society:

marriage:

family:

education:

gender:

occupation:

taboo:
```

例如：

女尊：

```yaml
gender:

女性主导

marriage:

一妻多夫（合法）
```

都市：

```
现代婚姻法
```

---

# 10. Religion & Belief

```yaml
belief:

god:

temple:

festival:

ritual:

afterlife:
```

即使没有宗教。

也要写：

```
None
```

避免 AI 后续自动补设定。

---

# 11. Time System

统一时间。

```yaml
timeline:

calendar:

month:

day:

festival:

season:
```

例如：

修仙：

```
青元历

一年360天
```

现代：

```
公历
```

---

# 12. Creature

```yaml
creature:

human:

monster:

spirit:

beast:

immortal:
```

例如：

都市：

```
monster: false
```

AI：

以后不会突然冒出来妖怪。

---

# 13. Resources

统一资源。

```yaml
resource:

food:

water:

medicine:

energy:

rare_items:
```

修仙：

```
灵石

灵药

灵脉
```

现代：

```
电力

石油

天然气
```

---

# 14. Forbidden Rules

整个世界。

最重要。

```yaml
forbidden:

never:

always:

exception:
```

例如：

```yaml
never:

死人复活

always:

修炼需要资源

exception:

凤凰血
```

AI：

不能违反。

---

# 15. Story Constraint

世界。

服务剧情。

```yaml
constraint:

travel_speed:

communication_speed:

war_scale:

life_expectancy:
```

例如：

如果：

最快交通：

马车。

AI：

不能：

一天跨越全国。

---

# 16. Dynamic Events

世界。

不是静止。

```yaml
events:

chapter:

event:

effect:
```

例如：

```yaml
chapter: 20

event:

魔族入侵

effect:

所有宗门停战
```

以后。

所有章节。

读取：

新状态。

---

# 17. World Validation

必须检查：

```
世界唯一

√
```

```
规则完整

√
```

```
科技一致

√
```

```
经济一致

√
```

```
时间一致

√
```

否则：

Validation Failed。

---

# 18. Example

```yaml
id: WORLD000003

basic:
  name: 云澜界
  genre: 修仙
  magic: true

power:
  energy: 灵气

  realm:
    - 炼气
    - 筑基
    - 金丹
    - 元婴

society:
  gender: 平等

forbidden:
  never:
    - 死者复生

technology:
  communication:
    - 传音符

resource:
  energy:
    - 灵石
```

---

# 19. Novel Engine Workflow

```
World Spec

↓

Prompt Compiler

↓

Scene Generator

↓

Consistency Checker

↓

Timeline

↓

Story Engine
```

世界观。

永远优先于剧情。

---

# 20. AFNL World Principle

> 世界观不是设定。

> 世界观是规则。

> 规则一旦建立。

> 作者也必须遵守。

> 当 AI 与作者遵守同一套规则时。

> 世界才会真正活起来。

End.
