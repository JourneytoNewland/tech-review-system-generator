# tech-review-system-generator

根据技术方案文档自动生成完整的单文件 HTML 技术评审系统的 Claude Code 技能。

## 📖 技能简介

**tech-review-system-generator** 是一个 Claude Code 技能，能够快速将技术方案文档（Markdown格式）转换为功能完整的交互式评审系统。

### 核心能力

- 📊 **可视化Dashboard**：实时展示评审进度、问题分布、模块统计
- 📝 **智能评审项生成**：自动提取技术点，生成结构化评审清单
- 🔍 **疑问澄清机制**：识别方案中的逻辑疑问点，标记需要澄清的内容
- 🎯 **多维度分类**：按模块、优先级、类别组织评审项
- 💬 **协作功能**：支持评论、状态管理、角色切换
- 📤 **报告导出**：JSON格式导出评审结果

### 适用场景

- ✅ 架构设计文档评审
- ✅ 系统设计文档评审
- ✅ API设计文档评审
- ✅ 数据库设计文档评审
- ✅ 性能优化方案评审
- ✅ 运维监控方案评审

## 🚀 快速开始

### 方式一：在当前项目中使用（推荐）

如果您正在评审当前项目的技术方案：

1. **准备技术方案文档**
   - 将技术方案文档放在项目根目录
   - 支持 Markdown 格式（.md 文件）
   - 例如：`ARCHITECTURE.md`、`DESIGN_DOC.md`

2. **直接调用技能**
   ```
   为 ./ARCHITECTURE.md 生成评审系统
   ```

3. **打开生成的评审系统**
   - 在浏览器中打开生成的 `index.html`
   - 开始评审

### 方式二：在其他项目中使用本技能

如果您想在**其他项目**中使用这个技能，按以下步骤操作：

#### Step 1: 复制技能到目标项目

将技能复制到项目的 `.claude/skills/` 目录：

```bash
# 复制技能到项目的 .claude/skills/ 目录
mkdir -p /path/to/your-project/.claude/skills
cp -r /path/to/tech-review-system-generator /path/to/your-project/.claude/skills/
```

**重要说明**：
- ❌ **不要**复制到项目根目录
- ✅ **必须**放在 `.claude/skills/` 目录下
- 这样技能才能被 Claude Code 正确识别

#### Step 2: 验证技能文件结构

确保目标项目包含以下结构：

```
your-project/
├── .claude/
│   └── skills/                       # 项目技能目录
│       └── tech-review-system-generator/    # ✅ 技能必须放在这里
│           ├── SKILL.md                # 必需
│           ├── references/
│           │   ├── config.md
│           │   ├── module-mapping.md
│           │   └── checklist-templates.md
│           └── assets/
│               └── html-template.html
├── YOUR_TECH_DOC.md                # 您的技术方案文档
└── ...                              # 其他项目文件
```

#### Step 3: 在 Claude Code 中打开项目

```bash
cd /path/to/your-project
code .  # 或使用 Claude Code CLI 打开
```

#### Step 4: 调用技能生成评审系统

在 Claude Code 对话中使用：

```
使用 tech-review-system-generator 为 ./YOUR_TECH_DOC.md 生成评审系统
```

**简化版本**（如果技能已正确识别）：

```
为 ./YOUR_TECH_DOC.md 生成评审系统
```

#### Step 5: 查看生成的结果

技能会在项目根目录生成 `index.html`，在浏览器中打开即可使用。

### 方式三：安装为全局技能（所有项目可用）

#### Step 1: 复制到全局技能目录

```bash
cp -r /path/to/tech-review-system-generator ~/.claude/skills/
```

#### Step 2: 验证安装

```bash
ls ~/.claude/skills/tech-review-system-generator/SKILL.md
# 应该显示文件存在
```

#### Step 3: 在任何项目中使用

现在您可以在**任何项目**中直接使用：

```
为 ./my-tech-doc.md 生成评审系统
```

### 方式四：使用配置文件自定义（可选）

在项目根目录创建 `.claude/settings.json`：

```json
{
  "skills": {
    "tech-review-system-generator": {
      "enabled": true,
      "config": {
        "grade": "detailed",      // concise/standard/detailed
        "style": "modern",        // modern/clean/technical
        "visualization": true,
        "systemName": "我的技术评审系统"
      }
    }
  }
}
```

### 基本用法示例

### 配置选项

您可以通过参数自定义生成的评审系统：

| 参数 | 选项 | 默认值 | 说明 |
|------|------|--------|------|
| 内容粒度 | concise/standard/detailed | standard | 每个模块的评审项数量 |
| 界面风格 | modern/clean/technical | modern | UI设计风格 |
| 可视化 | yes/no | yes | 是否包含图表 |
| 系统名称 | 自定义字符串 | 自动提取 | 评审系统标题 |

**示例：**

```
为 ./YOUR_DOC.md 生成评审系统，使用详细版粒度、modern风格、包含可视化图表
```

## 💡 使用示例

### 示例 1：生成架构评审系统

```
为 ./docs/microservice-architecture.md 生成评审系统
```

技能会自动：
1. 分析文档，识别微服务架构相关章节
2. 生成 4-8 个评审模块（服务拆分、API网关、服务发现等）
3. 为每个模块创建 10-20 个评审项
4. 生成包含 Dashboard 的 HTML 系统

### 示例 2：生成数据建模评审系统

```
为 ./database-schema-design.md 生成评审系统，使用详细版配置
```

生成特点：
- 每个模块 20+ 个评审项
- 覆盖表结构、索引、关系、查询优化等细节
- 包含性能指标、扩展性等深度评审点

### 示例 3：生成性能优化方案评审

```

## 📖 完整使用教程

### 教程 1：为新项目设置技能和生成评审系统

#### 场景
您有一个新项目 `my-new-project`，里面有技术方案文档 `docs/design.md`，想生成评审系统。

#### 完整步骤

```bash
# 1. 进入项目目录
cd ~/projects/my-new-project

# 2. 创建项目技能目录并复制技能
mkdir -p .claude/skills
cp -r ~/projects/yuyiruku/tech-review-system-generator .claude/skills/

# 3. 验证技能文件
ls .claude/skills/tech-review-system-generator/SKILL.md
# 输出: .claude/skills/tech-review-system-generator/SKILL.md ✅

# 4. 用 Claude Code 打开项目
code .

# 5. 在 Claude Code 对话中输入
为 ./docs/design.md 生成评审系统

# 6. 等待生成完成，查看生成的文件
ls index.html
# 输出: index.html ✅

# 7. 在浏览器中打开
open index.html  # macOS
# 或
start index.html  # Windows
```

#### 目录结构

```
my-new-project/
├── docs/
│   └── design.md                    # 您的技术方案
├── .claude/
│   └── skills/
│       └── tech-review-system-generator/  # ✅ 技能（正确位置）
│           ├── SKILL.md
│           ├── references/
│           └── assets/
└── index.html                        # 生成的评审系统 ✨
```

### 教程 2：为多个文档批量生成评审系统

#### 场景
您有多个技术文档需要评审：

```
docs/
├── 01-architecture.md
├── 02-database.md
├── 03-api-design.md
└── 04-deployment.md
```

#### 完整步骤

```bash
# 1. 进入项目并复制技能
cd ~/projects/my-project
mkdir -p .claude/skills
cp -r ~/projects/yuyiruku/tech-review-system-generator .claude/skills/
mkdir -p reviews  # 创建评审输出目录

# 2. 在 Claude Code 中依次生成

# 第一个文档
为 ./docs/01-architecture.md 生成评审系统，系统名称：架构设计评审
mv index.html reviews/01-architecture.html

# 第二个文档
为 ./docs/02-database.md 生成评审系统，系统名称：数据库设计评审
mv index.html reviews/02-database.html

# 第三个文档
为 ./docs/03-api-design.md 生成评审系统
mv index.html reviews/03-api-design.html

# 第四个文档
为 ./docs/04-deployment.md 生成评审系统
mv index.html reviews/04-deployment.html
```

#### 创建评审汇总页面

创建 `reviews/index.html` 作为导航页：

```html
<!DOCTYPE html>
<html>
<head>
    <title>技术评审汇总</title>
    <meta charset="UTF-8">
    <style>
        body { font-family: Arial, sans-serif; padding: 20px; background: #f5f5f5; }
        .review-list { display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 20px; }
        .review-card { border: 1px solid #ddd; padding: 15px; border-radius: 8px; background: white; }
        .review-card h3 { margin-top: 0; color: #1976D2; }
        .review-card a { display: inline-block; margin-top: 10px; color: white; background: #1976D2; padding: 8px 16px; border-radius: 4px; text-decoration: none; }
        .review-card a:hover { background: #115293; }
    </style>
</head>
<body>
    <h1>📊 技术评审汇总</h1>
    <div class="review-list">
        <div class="review-card">
            <h3>🏗️ 架构设计评审</h3>
            <p>系统架构、技术选型、模块划分</p>
            <a href="01-architecture.html" target="_blank">查看评审 →</a>
        </div>
        <div class="review-card">
            <h3>💾 数据库设计评审</h3>
            <p>数据模型、表结构、索引设计</p>
            <a href="02-database.html" target="_blank">查看评审 →</a>
        </div>
        <div class="review-card">
            <h3>🔌 API设计评审</h3>
            <p>接口定义、数据格式、错误处理</p>
            <a href="03-api-design.html" target="_blank">查看评审 →</a>
        </div>
        <div class="review-card">
            <h3>🚀 部署方案评审</h3>
            <p>部署架构、监控告警、容灾备份</p>
            <a href="04-deployment.html" target="_blank">查看评审 →</a>
        </div>
    </div>
</body>
</html>
```

### 教程 3：团队协作使用

#### 步骤 1：生成评审系统

```
为 ./TEAM_DESIGN.md 生成评审系统，系统名称：团队协作评审
```

#### 步骤 2：部署到内网服务器

```bash
# 方式A：部署到 Web 服务器
cp index.html /var/www/html/reviews/team-design.html

# 方式B：推送到 Git 仓库
git init
git add index.html
git commit -m "Add review system"
git push origin main
```

#### 步骤 3：分工评审

| 角色 | 重点关注 |
|------|----------|
| 架构师 | 架构设计、性能优化 |
| 产品经理 | 交互流程、需求覆盖 |
| 开发负责人 | 数据建模、运维监控 |

#### 步骤 4：汇总评审意见

1. 点击"导出"保存 JSON
2. 团队讨论评审结果
3. 更新技术方案文档
4. 重新生成评审系统（如需要）


为 ./performance-optimization-plan.md 生成评审系统，系统名称：性能优化评审
```

## 📂 项目结构

本项目作为技能的分发示例，展示了技能的正确使用方式：

```
yuyiruku/                              # 示例项目
├── REQ.md                             # 输入：技术方案文档
├── index.html                         # 输出：生成的评审系统
├── tech-review-system-generator/      # 技能分发副本（用于分享）
│   ├── SKILL.md
│   ├── references/
│   └── assets/
├── .claude/                           # 项目配置目录
│   ├── settings.json                  # 项目设置
│   └── skills/                        # ✅ 项目技能目录（正确用法示例）
│       └── tech-review-system-generator/
│           ├── SKILL.md
│           ├── references/
│           └── assets/
└── README.md                         # 本文件
```

### 技能的三种位置

| 位置 | 用途 | 推荐场景 |
|------|------|----------|
| `./tech-review-system-generator/` | **分发副本** | 技能的源码版本，用于版本控制和分享给其他团队 |
| `./.claude/skills/tech-review-system-generator/` | **项目级技能** | 当前项目使用，团队定制化修改 |
| `~/.claude/skills/tech-review-system-generator/` | **全局技能** | 所有项目可用，由用户统一管理 |

**使用建议**：
- ✅ 学习和参考：查看 `./tech-review-system-generator/`
- ✅ 实际使用：复制到 `.claude/skills/` 目录
- ✅ 团队共享：发布到内部 Git 仓库，其他团队复制到各自项目

**重要**：在其他项目中使用时，应该复制到 `.claude/skills/` 目录，而不是根目录。

### 生成的评审系统包含

- **6个核心模块**，共 126 个评审项
- **10个疑问澄清类评审项**（标记为 🔍）
- **可视化Dashboard**（3种图表）
- **完整的交互功能**（勾选、评论、状态管理）

## 🔧 技能工作原理

### 1. 文档分析

```
技术方案文档
    ↓
提取章节结构
    ↓
识别技术决策点
    ↓
确定评审模块数量（4-8个）
```

### 2. 模块映射

根据文档内容自动映射到标准模块类型：

| 文档内容 | 模块类型 | 图标 |
|----------|----------|------|
| architecture, design, schema | 架构设计 | fa-sitemap |
| data, model, entity, database | 数据建模 | fa-database |
| process, workflow, pipeline | 流程设计 | fa-cogs |
| performance, optimization | 性能优化 | fa-bolt |
| monitoring, ops, deployment | 运维监控 | fa-chart-line |
| interaction, ui, user | 交互流程 | fa-comments |

### 3. 评审项生成

为每个模块生成评审项：

```javascript
{
  id: 'module1-item1',
  title: '双轨存储架构一致性',
  desc: '评估图数据库(Neo4j)与向量数据库(Milvus)的数据同步机制...',
  priority: 'P0',                    // P0/P1/P2
  status: 'pending',                 // pending/reviewing/approved/revision
  category: '架构设计',
  checklist: [
    { id: 'c1', text: '检查点1', checked: false },
    { id: 'c2', text: '检查点2', checked: false }
  ]
}
```

### 4. 疑问点识别

自动识别以下情况并生成澄清类评审项（🔍）：

| 问题类型 | 触发条件 | 示例 |
|----------|----------|------|
| missing_detail | 关键技术细节未说明 | 错误处理流程缺失 |
| logic_conflict | 前后描述不一致 | 性能指标与架构矛盾 |
| tech_uncertainty | 技术选型无依据 | 为何选择 BGE-Large |
| unclear_requirement | 需求不明确 | "合理的响应时间" |
| dependency_missing | 依赖未列出 | 外部系统依赖 |
| edge_case | 边界情况未考虑 | 超大数据量处理 |

疑问澄清类评审项示例：

```javascript
{
  id: 'qc1',
  title: '🔍 双库事务一致性机制',
  desc: 'Milvus不支持ACID事务，如何保证双库一致性？',
  priority: 'P0',
  status: 'questioning',            // 特殊状态：待澄清
  category: '疑问澄清',
  question_type: 'missing_detail',
  impact_area: ['数据入库', '系统稳定性'],
  suggestions: [
    '考虑使用Saga模式',
    '增加定时一致性校验',
    '设计数据对比工具'
  ]
}
```

### 5. HTML系统生成

生成单文件 HTML，包含：
- React 18 + Babel（JSX编译）
- Tailwind CSS（样式）
- Chart.js 4.4（可视化）
- FontAwesome（图标）

## 🎨 生成结果

### Dashboard 界面

- 📈 **总体进度环形图**：整体完成度
- 🥧 **问题分布饼图**：P0/P1/P2 占比
- 📊 **模块进度柱状图**：各模块完成情况
- 📅 **评审活动时间线**：近期评审记录

### 评审项类型

| 状态 | 说明 | 徽章 |
|------|------|------|
| pending | 待评审 | ⏰ 灰色 |
| reviewing | 评审中 | 🔄 蓝色 |
| approved | 已通过 | ✅ 绿色 |
| revision | 需修改 | ⚠️ 红色 |
| **questioning** | **待澄清** | **🔍 琥珀色** |

## 📊 本项目生成实例

以 [REQ.md](REQ.md) 为例，技能生成了以下评审系统：

### 模块分布

| # | 模块 | 评审项 | 疑问项 |
|---|------|--------|--------|
| 1 | 语义架构设计 | 22 | 3 |
| 2 | 数据入库流程 | 20 | 2 |
| 3 | 专项数据管理 | 20 | 2 |
| 4 | 交互流程设计 | 20 | 1 |
| 5 | 性能优化 | 18 | 1 |
| 6 | 运维监控 | 18 | 1 |
| **总计** | **-** | **118** | **10** |

### 疑问澄清类示例

1. 🔍 **双库事务一致性机制** (P0)
   - 问题：Milvus不支持ACID事务，如何保证双库一致性？
   - 影响：数据入库、系统稳定性

2. 🔍 **Embedding模型选型依据** (P1)
   - 问题：为何选择BGE-Large？768维向量影响？
   - 影响：语义检索、系统性能

3. 🔍 **性能指标合理性验证** (P1)
   - 问题：30ms/50ms指标的压测数据？
   - 影响：系统性能、用户体验

## 🛠️ 自定义技能

### 修改模块映射

编辑 `tech-review-system-generator/references/module-mapping.md`：

```markdown
### 自定义模块类型

**关键词**：`microservice, service, api`

```javascript
{
  name: '微服务架构',
  icon: 'fa-cubes',
  color: '#9C27B0',
  checklist: [
    '服务拆分合理性',
    '接口定义完整性',
    '服务治理机制'
  ]
}
```
```

### 修改检查项模板

编辑 `tech-review-system-generator/references/checklist-templates.md`，添加新的评审类型。

### 调整配置参数

编辑 `tech-review-system-generator/references/config.md`：

```javascript
// 内容粒度
const CONTENT_GRADE = {
  concise: { minItems: 5, maxItems: 8 },
  standard: { minItems: 10, maxItems: 15 },
  detailed: { minItems: 20, maxItems: 30 }
};

// 界面风格
const UI_STYLES = ['modern', 'clean', 'technical'];
```

## 📚 进阶使用

### 为不同类型文档生成

#### 架构设计文档

```
为 ./docs/system-architecture.md 生成评审系统
```

特点：生成架构设计、数据建模、接口设计等模块

#### API设计文档

```
为 ./api-specification.md 生成评审系统，使用精简版配置
```

特点：生成接口定义、数据模型、错误处理等模块

#### 性能优化方案

```
为 ./performance-tuning.md 生成评审系统
```

特点：生成性能指标、优化策略、监控告警等模块

### 批量生成

为多个文档生成评审系统：

```bash
# Claude Code 中依次执行
为 ./doc1.md 生成评审系统
为 ./doc2.md 生成评审系统
为 ./doc3.md 生成评审系统
```

## 🚀 发布技能到 Git

如果你想将此技能发布到公开的 Git 仓库（如 GitHub）供其他人使用，请参考以下指南。

### 📦 应该发布的文件

```
✅ tech-review-system-generator/    # 技能核心目录
✅ README.md                         # 使用说明
✅ LICENSE                           # 开源许可证（推荐）
✅ .gitignore                        # Git 忽略规则
```

### ❌ 不应该发布的文件

```
❌ index.html                        # 项目特定生成文件
❌ REQ.md                            # 项目特定需求文档
❌ .claude/settings.json             # 本地配置（可能含敏感信息）
❌ .claude/hooks/                    # 项目钩子
❌ .claude/skills/                   # 本地使用目录
❌ .DS_Store, Thumbs.db              # 操作系统文件
❌ node_modules/, __pycache__/       # 依赖和缓存
```

### 🚀 快速发布步骤

```bash
# 1. 创建干净的发布目录
mkdir tech-review-system-generator-release
cd tech-review-system-generator-release

# 2. 复制核心技能文件
cp -r ../tech-review-system-generator ./
cp ../README.md ./
cp ../.gitignore.skill ./.gitignore

# 3. 创建 LICENSE（推荐使用 MIT）
cat > LICENSE << 'EOF'
MIT License

Copyright (c) 2025 [Your Name]

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
EOF

# 4. 初始化 Git 仓库
git init
git add .
git commit -m "Initial release of tech-review-system-generator skill"

# 5. 推送到 GitHub
git remote add origin https://github.com/your-username/tech-review-system-generator.git
git branch -M main
git push -u origin main
```

### 📋 发布前检查清单

在推送前，请确保：

- [ ] 删除了所有 `index.html` 生成文件
- [ ] 删除了项目特定的 `REQ.md` 文件
- [ ] 检查 `settings.json` 中没有敏感信息（API密钥、密码等）
- [ ] 删除了 `.env` 和 `credentials.json`
- [ ] 删除了所有 `.DS_Store` 和其他操作系统文件
- [ ] 删除了 `node_modules/` 和其他依赖目录
- [ ] 确认没有包含个人配置文件（`.vscode/`, `.idea/` 等）

### 📚 详细指南

完整的发布指南请参考：[GIT_PUBLISHING_GUIDE.md](GIT_PUBLISHING_GUIDE.md)

该指南包含：
- 详细的文件分类说明
- 推荐的仓库结构
- 安全检查清单
- 常见错误及解决方案
- LICENSE 模板
- 发布后的 README 模板

---

## 🤝 贡献与反馈

### 改进技能

如需改进技能功能：

1. 修改 `tech-review-system-generator/` 下的文件
2. 使用新文档测试生成效果
3. 同步到全局：`cp -r tech-review-system-generator/* ~/.claude/skills/tech-review-system-generator/`

### 问题反馈

如遇到问题，检查：
- 文档格式是否为 Markdown
- 文档是否包含清晰的章节结构
- Claude Code 技能是否正确加载

## 📄 许可

本技能生成的评审系统仅供内部技术评审使用。

---

**技能版本**：v1.1
**技能作者**：crazygenius
**更新时间**：2026-03-04
**示例项目**：AI原生智能BI语义数据入库方案
