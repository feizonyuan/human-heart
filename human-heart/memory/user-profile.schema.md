# 学习档案规范（本地，零泄漏）

档案位置：`$CODEX_HOME/human-heart/user-profile.json`
（`CODEX_HOME` 未设置时为 `~/.codex/human-heart/user-profile.json`）

## 字段结构

```json
{
  "schema_version": 1,
  "profile_version": 12,
  "last_updated": "2026-08-13T21:30:00+08:00",
  "known": true,
  "identity": {
    "preferred_name": "",
    "background": [],
    "confidence": "low"
  },
  "emotional_triggers": [
    {"topic": "前任", "pattern": "提到会明显低落", "confidence": "high"},
    {"topic": "工作评价", "pattern": "自我否定加剧", "confidence": "medium"}
  ],
  "communication_style": {
    "language": ["zh-CN", "en"],
    "habits": ["爱用比喻", "话比较短", "喜欢先被确认再展开"],
    "confidence": "medium"
  },
  "effective_responses": [
    {"what": "先承认付出有意义，再谈放下", "feedback": "用户说这样舒服", "confidence": "high"}
  ],
  "avoid_topics": ["原生家庭（提过一次后回避）"],
  "dependency_signals": {
    "seen": false,
    "notes": ""
  },
  "boundaries": {
    "roleplay_allowed": true,
    "roleplay_notes": "喜欢温柔陪伴类扮演；需要提醒界限",
    "confidence": "medium"
  },
  "notes": ["低置信度印象：可能对'被否定'特别敏感，待确认"]
}
```

字段说明：`language` 为数组，支持用户常用多语言；
`boundaries` 记录角色扮演等边界偏好（是否允许、需要什么提醒）。

## 更新规则

1. 每次陪伴会话结束前更新；会话中只读不写。
2. 只记录用户主动分享的信息；不推断身份、不记录隐私猜测。
3. 每条记录带置信度：high / medium / low / 待确认。
4. 低置信度内容放入 `notes` 并标注"待确认"，不放进正式字段。
5. 用户纠正时，覆盖旧记录并去掉原置信度。
6. 用户当下表达与档案冲突时，以当下为准，先更新再继续。
7. 用户要求停止学习或删除时，立即删除整个档案，本次会话也不写入。
8. 用户切换语言或调整角色扮演边界时，当场更新对应字段。

## 隐私铁律

1. 数据只存在于用户本地磁盘，不随任何网络请求发送。
2. 不进日志、不进共享文档、不进第三方服务、不用于训练。
3. 输出中不引用档案原文；档案只用于调整语气与策略。
4. 学习透明：主动告知"我记住了什么"，用户可随时纠正。
5. 用户可查看、修改、删除；删除立即生效且不可恢复。
6. 档案内容是假设而非事实；低置信度不当作定论。

## 使用方式

- 会话开始时：若档案存在，读取并用于校准语气，但不在开场暴露"我记得你……"（除非用户问）。
- 会话过程中：不主动引用档案；只在判断回应策略时参考。
- 会话结束时：合并本次观察，更新档案；变更较多时告知用户"我记住了 X，如果你想改可以告诉我"。
