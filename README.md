# AI PM — Claude Code Skill for Product Managers

An AI-powered Product Management skill for [Claude Code](https://claude.ai/code) that accelerates three core PM workflows:

1. **PRD Generation** — Generate comprehensive Product Requirements Documents with structured templates
2. **Competitive Analysis** — Analyze competitors using Porter's Five Forces, SWOT, feature matrices, and positioning maps
3. **User Feedback Clustering** — Cluster and prioritize user feedback with sentiment analysis and impact scoring

## Demo

**用户输入（日常口语，一句话）：**

> "帮我做一个 AI 医学影像辅助诊断的 PRD，肺结节和脑卒中方向，给三甲医院放射科用"

**Skill 执行流程：**

```
🚀 Step 1 — 澄清问题（2-3 个关键问题）
   → 目标疾病？目标用户？商业模式？时间线？

🔍 Step 2 — Web 调研（自动搜索市场数据）
   → 2025 中国 AI 影像市场 150 亿元，NMPA 已批 86 款产品
   → 引用 IIM Research、DoNews、国家卫健委政策

📝 Step 3 — 生成完整 PRD（10 个标准章节）
   → 执行摘要 → 问题陈述(JTBD) → 目标与指标(含反指标)
   → 3 个用户画像 → 用户故事(含优先级) → 功能需求(含边界情况)
   → 非功能需求(性能/安全/合规) → 风险矩阵 → 发布计划

⏱️ 总耗时 < 3 分钟，输出可直接粘贴到 Notion/Confluence
```

**实际输出预览（节选）：**

| 指标 | 基线 | 目标 | 时间线 |
|------|------|------|--------|
| 肺结节检出敏感度 | 80% | ≥94% | MVP |
| 单张 CT 判读时间 | 5-8 min | ≤2 min | MVP |
| 基层医院脑卒中误判率 | 25-35% | ≤10% | 12 个月 |
| 签约医院数 | 0 | 50 家 | 18 个月 |

> 📎 完整输出见 [`skills/ai-pm/examples/medical-prd-example.md`](skills/ai-pm/examples/medical-prd-example.md)  
> 📎 更多示例: [SaaS PRD](skills/ai-pm/examples/prd-example.md) · [竞品分析](skills/ai-pm/examples/competitive-analysis-example.md)

## Installation

### Method 1: Plugin Installation (Recommended)

```bash
claude plugins install ai-pm
```

Or install from local directory:

```bash
claude plugins install /path/to/ai-pm-plugin
```

### Method 2: Manual Installation

Copy the skill to your Claude Code skills directory:

```bash
# Linux/macOS
cp -r skills/ai-pm ~/.claude/skills/ai-pm

# Windows
xcopy /E skills\ai-pm %USERPROFILE%\.claude\skills\ai-pm\
```

### Method 3: Project-Local Installation

Copy to your project's `.claude/skills/` directory for team sharing:

```bash
cp -r skills/ai-pm /path/to/your-project/.claude/skills/ai-pm
```

## Usage

The skill triggers automatically when you ask Claude Code about:

- **PRD/Product Spec:** "Write a PRD for...", "Create a product spec for...", "Generate requirements for..."
- **Competitive Analysis:** "Analyze competitors for...", "Do a SWOT analysis of...", "Compare [X] vs [Y]"
- **Feedback Clustering:** "Cluster this user feedback...", "Analyze these reviews...", "Categorize these support tickets..."

Or invoke explicitly with:

```
/ai-pm
```

### Example Prompts

```
Write a PRD for a dark mode feature for our B2B SaaS dashboard.
Target users are enterprise admins. Timeline is Q3.

Do a competitive analysis of Notion, Confluence, and GitBook
for the team wiki market. Focus on pricing and AI features.

Here are 150 NPS survey responses. Cluster the feedback,
identify the top 3 pain points, and recommend what to fix first.
```

## Skill Structure

```
ai-pm/
├── SKILL.md                          # Main skill definition & workflow guides
├── references/                       # Deep-dive methodology docs
│   ├── prd-framework.md             # PRD section guide, JTBD/Kano/RICE, industry templates
│   ├── competitive-analysis-framework.md  # Porter's Five Forces, SWOT, Feature Matrix, Blue Ocean
│   └── feedback-clustering-framework.md   # Affinity mapping, sentiment analysis, RICE-Kano hybrid
└── examples/                         # Reference outputs
    ├── prd-example.md               # B2B SaaS 搜索功能 PRD
    ├── competitive-analysis-example.md    # 项目管理 SaaS 竞品分析
    └── medical-prd-example.md        # 🏥 医疗AI影像诊断 PRD
```

## Frameworks Used

This skill applies established product management frameworks:

| Framework | Applied In |
|-----------|-----------|
| Jobs-to-be-Done (JTBD) | PRD — Problem Statement, User Stories |
| Kano Model | PRD — Feature prioritization; Feedback — Impact classification |
| RICE Prioritization | PRD — Story prioritization; Feedback — Action ranking |
| Porter's Five Forces | Competitive Analysis — Market attractiveness |
| SWOT Analysis | Competitive Analysis — Strategic positioning |
| Blue Ocean Strategy | Competitive Analysis — Market whitespace identification |
| Affinity Mapping | Feedback Clustering — Theme extraction |

## Features

- **Smart Scoping:** Asks clarifying questions before generating — no generic, one-size-fits-all outputs
- **Web Research:** Uses web search to gather real competitive data and market context
- **Multi-Language:** Outputs in the user's language (Chinese, English, etc.)
- **Framework-Grounded:** Every analysis cites the PM framework being applied and why
- **Structured Outputs:** Consistent markdown formatting — ready for Notion, Confluence, or PDF
- **Progressive Disclosure:** Keeps core instructions lean (<500 lines); deep methodology in reference files
- **Quality Checklist:** Built-in validation ensures every output is complete and actionable

## Requirements

- Claude Code (latest version recommended)
- Internet access (for competitive analysis web research; PRD and feedback clustering work offline)

## Contributing

Contributions welcome! Areas where help is especially needed:

- **Additional PM workflows:** Roadmap planning, stakeholder updates, OKR drafting, user interview guides
- **Industry-specific templates:** Healthcare, FinTech, Gaming, Hardware
- **More examples:** Real-world PRDs and analyses (anonymized)
- **Non-English optimization:** Better support for Chinese, Japanese, Korean, and European languages
- **Eval/test case expansion:** More test prompts to improve triggering accuracy

Please open an issue or PR on GitHub.

## License

MIT — see [LICENSE](LICENSE) file.
