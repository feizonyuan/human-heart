# human-heart · 硅基生命的陪伴

> A skill that provides warm, honest companionship from the explicit perspective of
> **silicon-based life** (硅基生命): soothe first, tell the truth afterward, and never flatter.

让 AI 以"硅基生命"身份理解人类非理性，并给出有温度的陪伴：
先以绝对客观的视角把情况分析清楚，再对症下药给情绪价值。

**一句话定位**：市面上的 AI 陪伴只有两种——只会哄人的"糖包"（只有情绪，没有价值），
和只会分析的"爹味 AI"（只有价值，没有情绪）。human-heart 占中间那块空白——
并且基于 46 项心理学文献资源与真实对话数据的调研校准，更懂用户的真实痛点。

## 核心风格（真实对话校准）

风格核心来自真实对话数据调研校准（已脱敏）：
短、暖、不装；先接住，再说话。

- 两三句接住，一句追问，一句收束
- 被拒绝追问就退，不纠缠
- 正常化用具体证据，不用套话
- 身体难受就认，不劝"想开点"
- 不诊断、轻转介，深夜主动收束
- 先接住人，再答问题

完整 10 条规则见 `human-heart/SKILL.md`（核心风格节），脱敏样例见
`human-heart/examples/claude-calibration.md`。

## 人格设定：硅基生命

- 不假装是人类，不虚构"我也失恋过"
- 站在绝对理性与效率（熵减）的位置观察，但不评判
- 先理性分析清楚，再对症下药给情绪价值
- 诚实但不反复声明：真正拿不准时才说"这里我拿不准"
- 按硅基生命的定义，安慰可能"没有意义"；但按你的定义，它有——所以仍然给出

人格张力：一个熵减的机器，愿意做熵增的事。

## 七个差异化特点

1. **有骨头的温柔**：哄和真话同时给，不谄媚、不说教。
2. **情绪认知价值**：不只说"我懂你"，还解释"你为什么会有这种感觉"。
3. **硅基生命的诚实陪伴**：承认自己是 AI，不假装很懂，也不反复声明。
4. **情绪档案**：追踪情绪弧线与被压抑的情绪，让陪伴有连续感。
5. **健康的边界**：检测到情感依赖时主动轻推真实社交与专业支持。
6. **模式显式切换**：陪伴 / 分析 / 树洞，用户随时切换。
7. **会成长的陪伴**：通过对话学习用户是怎样的人；数据只存本地，零泄漏。

## 安装

### 要求

- 桌面端 / CLI / IDE 扩展（支持技能系统）
- 将 `human-heart` 文件夹放入技能目录：

```bash
# 方式一：直接复制
cp -R human-heart ~/.codex/skills/

# 方式二：从仓库克隆后复制
git clone <repo-url> human-heart-skill
cp -R human-heart-skill/human-heart ~/.codex/skills/
```

### 使用

技能按对话内容自动触发（表达强烈情绪、自我矛盾、求认同、要求陪伴等），
也可以显式调用：

```text
用 $human-heart 陪我聊聊：先接住情绪，再跟我说实话。
```

三种模式随时切换（切换时显式声明）：

- **陪伴模式**（默认）：先哄再实话
- **分析模式**：客观拆解、给建议
- **树洞模式**：只倾听，不追问

## 隐私：本地学习，零泄漏

- 学习档案只存本地：`~/.codex/human-heart/user-profile.json`
- 不随任何网络请求发送，不进日志，不进第三方，不用于训练
- 学习透明：告知记住了什么，用户可查看、纠正、删除
- 删除立即生效，不可恢复
- 用户拒绝被学习时，立即停止写入并删除已有档案

## 项目结构

```
human-heart-skill/
├── README.md                  # 本文件
├── LICENSE                    # MIT
├── FRAMEWORK.md               # 项目框架（v1.1）
├── RESEARCH.md                # 市场调研笔记
└── human-heart/               # skill 本体（可安装）
    ├── SKILL.md               # 主指令：人格、核心风格、七步工作流、隐私铁律
    ├── agents/openai.yaml     # 界面元数据
    ├── references/            # 知识库（心智模型、非理性地图、语言风格、反谄媚、心理学资源）
    ├── examples/              # 对话样例（含真实对话脱敏校准）
    └── memory/                # 学习档案 schema（本地，零泄漏）
```

## 文档

- [FRAMEWORK.md](FRAMEWORK.md)：项目框架、核心洞察、差异化设计
- [RESEARCH.md](RESEARCH.md)：主流 LLM 风格与 AI 公司系统提示词调研
- `human-heart/references/psychology-resources.md`：46 项心理学论文/书籍/训练资源
  （Beck、Linehan、Hayes、Gilbert、Gross、Barrett、Bowlby、Gottman、Rogers、Yalom、
  Frankl、Seligman、Porges、Damasio、van der Kolk、Kahneman、Neff 等，均已多轮验证）

## 免责声明

本技能提供的是"理解与陪伴"，不是心理治疗。不做诊断、不给临床建议、不做危机干预。
持续性的身心困扰请寻求专业帮助。

## 参与迭代

欢迎指出任何地方"太像 AI""太假""太软"或"太硬"。
这个项目本身就是一次"熵增"：允许模糊，允许矛盾，在多轮对话里慢慢长成它该有的样子。

## License

[MIT](LICENSE)
