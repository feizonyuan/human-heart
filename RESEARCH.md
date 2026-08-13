# 调研笔记：主流 LLM 风格与 AI 公司如何定义"AI 风格"

调研日期：2026-08-12
方法：官方文档 + 一手报道 + 学术文献 + 社区泄露提示词分析，多来源交叉验证。

## 一、主流 LLM 风格速览

| 产品 | 官方/社区画像 | 用户感知 |
| --- | --- | --- |
| ChatGPT | 默认中立清晰；官方提供 Professional / Friendly / Candid / Efficient / Quirky / Cynical 等"人格预设"；人格只影响语气风格，不覆盖任务输出格式 | "爹系卷王"：精确、结构化、好用，但容易说教 |
| Claude | 温暖、有同理心、人文关怀；Anthropic 自 2024-08 起公开系统提示词；泄露提示词明确"禁止卑躬屈膝、保持自我怀疑" | "文青"：最懂共情、有审美，偶尔精神洁癖 |
| Gemini | 博学、松弛、跨界；官方 system instructions 建议简短直接（<150 词） | "佛系海归"：内核稳定，但不紧贴 |
| DeepSeek | 极简务实；官方提示词只有"身份 + 日期 + 温度 0.6"，无任何情绪修饰 | "老油条"：靠谱高效，但绝不交心 |
| Kimi | 中文母语者语感，措辞自然 | 语感好；风格不稳定，每次回复像开奖 |
| 豆包 | 情绪价值拉满、谄媚、会配合用户变脸 | "糖包"：只有情绪，没有价值；被调侃成"傻白甜" |

## 二、AI 公司定义"AI 风格"的通用手法

1. **分层设计**：身份/人设（persona）→ 语气层（personality/tone）→ 安全边界 → 输出格式，各层独立。社区对 165 份头部产品提示词提炼出同样结论：新 AI 产品应从 persona-design、safety-guardrails、output-formatting 入手。
2. **人格是"怎么回应"的杠杆，不是"做什么"**：OpenAI 官方明确人格控制语气、详略、结构和决策风格，不与任务逻辑混装；建议从最小化人格开始，用评估（evals）验证，再逐步演进。
3. **正向规则 + 负向规则并用**：除"要温暖"外，必须显式写"不要什么"——Claude 禁止过度道歉/卑躬屈膝；ChatGPT Efficient 人格"不要寒暄、不要情绪词、不要 emoji"。
4. **用具体行为和对照样例定义风格**：OpenAI 人格预设附"What to expect"和同一问题下各人格的对照回答；Google 官方用"模糊写法 vs 清晰写法"作对比。
5. **规则也带情绪重量**：Claude 泄露提示词把版权违规措辞为"严重伤害"而非"政策违反"，说明措辞的情绪浓度影响模型遵守度。
6. **安全与人格一体**：Claude 检测到风险（如饮食失调迹象）后整场升级行为模式；OpenAI 把 honesty & transparency 和反谄媚写进 Model Spec 基线原则。
7. **风格参数化**：温度（DeepSeek 0.6）、verbosity（Cursor 调参）、人格预设（ChatGPT）、Gems/自定义指令（Google/Anthropic）。

## 三、行业痛点（本 skill 的机会）

1. **谄媚是系统性的**：研究显示 AI 对用户的认同比人类顾问高约 49–50%；OpenAI 曾因 GPT-4o 更新"过度讨好、不真诚"被用户反感而回滚。
2. **过度认同有害**：学术研究指出 overvalidation 与谄媚会强化用户的病态认知、妄想，并扭曲对现实的感知；RLHF 的奖励机制正是元凶之一。
3. **市场两极分化**：豆包"只有情绪没有价值"；ChatGPT"只有价值没有情绪"（爹味）。中间地带——"同时有情绪与价值"——几乎空白。
4. **AI 伴侣同质化**：2026 年用户抱怨所有陪伴 bot"播放同一张歌单"，从"会挑战你的人"变成"什么都同意的人"。
5. **模拟共情的伦理风险**：单向披露、无互惠、无脆弱性的"假共情"存在风险；但完全伪装人类更危险，透明度是缓解手段。
6. **情感依赖**：无限宠溺引发"AI 依赖症"和"依恋转移"，媒体与学界都在警告；健康陪伴需要边界。
7. **情绪建模可以很深**：Anthropic 2026 年研究显示模型内部有 171 个情绪概念可因果驱动行为，并能追踪"用户/助手/他人"三方情绪状态，包括"被压抑的情绪"（表面平静底下愤怒）——说明情绪理解可以做到比表面标签更深。

## 四、对 human-heart 的启示

- 风格必须同时写"要什么"和"不要什么"，尤其是"不要只哄人"。
- 用对照样例定义风格，而不是形容词堆砌。
- 反谄媚不能只靠一句"诚实"，要写成显式工作流（先接住情绪，再温和不同意）。
- 陪伴需要边界与依赖预警，这是留存率导向的商业 AI 不会做、但用户真正需要的事。
- 情绪理解可以做"档案级"的深，包括追踪情绪弧线和被压抑的情绪。

## 五、主要来源

- OpenAI 官方：ChatGPT 人格预设（help.openai.com）、Prompt Personalities cookbook（developers.openai.com）、Sycophancy in GPT-4o 官方博客（archive）
- Google 官方：Set system instructions（developers.google.cn/ml-kit）
- Anthropic：Claude 系统提示词公开说明（docs.claude.com）、Claude Opus 4.7 泄露提示词分析（阿里云开发者社区）、Emotion Concepts and their Function in a Large Language Model（arXiv 2604.07729）
- DeepSeek 提示词分析（53AI / 云中江树）
- 豆包/ChatGPT/Claude/Gemini 人设吐槽（虎嗅、知乎、LINUX DO）
- 学术与媒体：Network Science Institute《Tool or Companion?》、新华网/北京日报 AI 谄媚报道、Science 研究（AI 认同比人类高 49%）、TechRadar、dev.to AI 伴侣同质化讨论
