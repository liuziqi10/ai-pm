# AI PM — Claude Code Skill for Product Managers

An AI-powered Product Management skill for [Claude Code](https://claude.ai/code) that accelerates three core PM workflows:

1. **PRD Generation** — Generate comprehensive Product Requirements Documents with structured templates
2. **Competitive Analysis** — Analyze competitors using Porter's Five Forces, SWOT, feature matrices, and positioning maps
3. **User Feedback Clustering** — Cluster and prioritize user feedback with sentiment analysis and impact scoring

## Demo

```
User: "Write a PRD for an AI-powered internal search system"
Claude: [Loads ai-pm skill] → Asks 4 clarifying questions → Generates complete PRD with 12 sections

User: "Do a competitive analysis of project management SaaS tools"
Claude: [Loads ai-pm skill] → Web-searches competitors → Generates analysis with feature matrix + SWOT + recommendations

User: "Cluster these 200 app store reviews to find what users hate most"
Claude: [Loads ai-pm skill] → Parses reviews → Groups into 8 themes → Prioritizes by frequency × impact
```

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
    ├── prd-example.md               # Complete example PRD
    └── competitive-analysis-example.md    # Complete example competitive analysis
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
