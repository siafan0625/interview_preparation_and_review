# Interview Prep & Review Skills for Claude Code

两个 Claude Code custom skills，覆盖面试全流程：**面试前准备** + **面试后复盘**。

## 功能

### `/interview-prep` — 面试前准备
- 自动读取你的简历，一键启动
- 公司调研（WebSearch）：通用模块 + 岗位相关模块自动匹配
- JD 拆解：提炼核心能力要求，逐一匹配简历经历
- 定制自我介绍：30秒版 + 1分钟版，JD 涉及英语时自动生成中英双语
- 预判面试问题 + 答案大纲：经历类/动机类/假设类，每题 STAR 框架
- 反问清单：5-8 个展示研究深度的问题
- **支持后续面（二面/三面）**：检测到已有 prep.md 时自动切换，做差距分析、精进答案、补充新题

### `/interview-review` — 面试后复盘
- 逐题分析：面试官问了什么 → 答了什么 → 好不好 → 为什么
- 按质量分级：✅ 过关 / ⚠️ 需修改 / ❌ 需重构
- 引导用户参与改进：不是单方面给答案，而是引导你补充案例和思路
- 可选模拟练习：Claude 扮演面试官针对薄弱点提问

## 安装

### 1. 复制 skill 文件

```bash
# 克隆仓库
git clone https://github.com/siafan0625/interview_preparation_and_review.git
cd interview_preparation_and_review

# 复制到 Claude Code skills 目录
cp -r skills/interview-prep ~/.claude/skills/
cp -r skills/interview-review ~/.claude/skills/
cp skills/interview-config.md ~/.claude/skills/
```

### 2. 注册 skills

在 `~/.claude/CLAUDE.md`（如果没有就创建一个）中添加：

```markdown
## 面试 Skills

- `/interview-prep [公司名] [岗位名]` — 面试准备（支持多轮）：自动读取简历，公司调研、JD拆解、定制自我介绍、预判问题+答案、反问清单。如检测到已有 prep.md，自动询问是否切换到后续面模式（差距分析、精进答案、补充新题）。
- `/interview-review [公司名] [岗位名]` — 面试后系统复盘：逐题分析、对比准备vs实际、生成改进方案、可选模拟练习。需要用户提供录音稿或问答回忆。
```

### 3. 首次使用配置

首次运行任一 skill 时，会自动引导你配置：
- 简历存放目录
- 面试准备文档存放目录
- 目标岗位和偏好方向
- 经历特点（可选）

也可以直接编辑 `~/.claude/skills/interview-config.md` 手动配置。

## 使用

```bash
# 面试前准备（一面）
/interview-prep 字节跳动 产品运营
# 然后贴上岗位 JD

# 面试前准备（二面/三面）— 自动检测并切换
/interview-prep 字节跳动 产品运营
# 检测到已有 prep.md，询问是否为后续面

# 面试后复盘
/interview-review 字节跳动 产品运营
# 然后贴上录音稿或回忆
```

## 文件结构

```
~/.claude/skills/
├── interview-config.md          ← 个人配置（路径、偏好）
├── interview-prep/
│   └── SKILL.md                 ← 面试准备 skill
└── interview-review/
    └── SKILL.md                 ← 面试复盘 skill
```

产出文档结构（示例）：

```
你的面试准备目录/
├── 0323 字节跳动/
│   ├── prep.md                  ← 一面准备
│   ├── review.md                ← 一面复盘
│   └── prep-二面.md             ← 二面准备
├── 0325 腾讯/
│   └── prep.md
└── 面试共性问题复盘.md           ← 跨公司共性问题（可选）
```

## 依赖

- [Claude Code](https://claude.ai/claude-code) — Anthropic 官方 CLI
- Claude Code 的 WebSearch 工具（用于公司调研）

## License

MIT
