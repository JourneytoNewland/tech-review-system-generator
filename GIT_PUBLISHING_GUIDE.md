# Git 发布指南

## 📦 技能包发布清单

发布 `tech-review-system-generator` 技能到公开 Git 仓库时，请参考以下清单。

---

## ✅ 应该发布的文件

### 核心技能文件
```
tech-review-system-generator/
├── SKILL.md                    ✅ 必需（技能元数据和工作流程）
├── references/                 ✅ 推荐（参考文档）
│   ├── config.md              ✅ 配置选项说明
│   ├── module-mapping.md      ✅ 模块映射规则
│   └── checklist-templates.md ✅ 检查项模板
└── assets/                     ✅ 可选（资源文件）
    └── html-template.html     ✅ HTML 代码模板
```

### 项目文档
```
├── README.md                   ✅ 必需（使用说明）
├── LICENSE                     ✅ 推荐（开源许可证）
├── .gitignore                  ✅ 推荐（Git 忽略规则）
└── GIT_PUBLISHING_GUIDE.md     ✅ 可选（本发布指南）
```

---

## ❌ 不应该发布的文件

### 🔴 项目特定生成文件
这些文件是针对特定项目的生成结果，不应包含在技能包中：

```
❌ index.html              # 针对特定项目生成的评审系统
❌ REQ.md                  # 项目特定需求文档
❌ *.html                  # 其他生成的 HTML 文件
❌ exports/                # 导出的评审报告
❌ reports/                # 生成的报告文件
```

**原因**：这些文件是使用技能的结果，而非技能本身。

### 🔴 开发环境配置
可能包含敏感信息或本地配置：

```
❌ .claude/settings.json           # Claude Code 本地配置
❌ .claude/settings.local.json     # 本地覆盖配置
❌ .claude/hooks/                  # 项目钩子脚本
❌ .claude/skills/                 # 本地技能使用目录
❌ .env                            # 环境变量
❌ credentials.json                # 凭证文件
```

**原因**：这些是本地开发环境配置，不应共享。

### 🔴 操作系统文件
```
❌ .DS_Store               # macOS
❌ Thumbs.db              # Windows
❌ desktop.ini            # Windows
❌ *~                     # Linux 临时文件
```

**原因**：操作系统自动生成的文件，与技能无关。

### 🔴 编辑器和IDE配置
```
❌ .vscode/               # VS Code 配置
❌ .idea/                 # JetBrains IDE 配置
❌ *.swp, *.swo           # Vim 临时文件
❌ *~                     # Emacs 备份文件
```

**原因**：个人编辑器偏好设置，不应强加给其他用户。

### 🔴 依赖和缓存
```
❌ node_modules/          # Node.js 依赖
❌ __pycache__/           # Python 缓存
❌ venv/, env/            # Python 虚拟环境
❌ *.log                  # 日志文件
❌ *.tmp, *.cache         # 临时和缓存文件
```

**原因**：这些文件可以通过包管理器重新生成。

---

## 📋 推荐的技能仓库结构

```
tech-review-system-generator/
├── README.md                    # 技能使用说明
├── LICENSE                      # MIT/Apache 2.0 等
├── .gitignore                   # Git 忽略规则
├── GIT_PUBLISHING_GUIDE.md      # 发布指南（本文件）
│
├── tech-review-system-generator/  # 技能核心目录
│   ├── SKILL.md                  # 技能元数据和工作流程
│   ├── references/               # 参考文档
│   │   ├── config.md
│   │   ├── module-mapping.md
│   │   └── checklist-templates.md
│   └── assets/                   # 资源文件
│       └── html-template.html
│
└── examples/                     # 可选：示例项目
    ├── ai-native-bi/
    │   ├── REQ.md               # 示例需求文档
    │   └── index.html           # 示例生成结果
    └── README.md                # 示例说明
```

---

## 🚀 发布步骤

### 1. 准备发布目录

```bash
# 创建干净的发布目录
mkdir tech-review-system-generator-release
cd tech-review-system-generator-release

# 复制核心技能文件
cp -r ../tech-review-system-generator ./
cp ../README.md ./
cp ../GIT_PUBLISHING_GUIDE.md ./

# 可选：添加示例
mkdir examples
cp -r ../ai-native-bi-example examples/
```

### 2. 创建 .gitignore

```bash
# 使用提供的模板
cp ../.gitignore.skill ./.gitignore
```

### 3. 初始化 Git 仓库

```bash
git init
git add .
git commit -m "Initial release of tech-review-system-generator skill"
```

### 4. 推送到 GitHub

```bash
# 创建 GitHub 仓库后
git remote add origin https://github.com/your-username/tech-review-system-generator.git
git branch -M main
git push -u origin main
```

---

## 🔒 安全检查清单

在推送前，请确保：

- [ ] 删除了所有 `index.html` 生成文件
- [ ] 删除了项目特定的 `REQ.md` 文件
- [ ] 检查 `settings.json` 中没有敏感信息（API密钥、密码等）
- [ ] 删除了 `.env` 和 `credentials.json`
- [ ] 删除了所有 `.DS_Store` 和其他操作系统文件
- [ ] 删除了 `node_modules/` 和其他依赖目录
- [ ] 确认没有包含个人配置文件（`.vscode/`, `.idea/` 等）

---

## 📝 LICENSE 推荐

推荐使用开源许可证以明确使用条款：

- **MIT License**：最宽松，允许任何用途
- **Apache 2.0**：宽松，包含专利授权
- **GPL v3**：copyleft，衍生作品需开源

创建 `LICENSE` 文件：

```bash
# 使用 MIT License 示例
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
```

---

## 📌 发布后的 README 模板

```markdown
# Tech Review System Generator

根据技术方案文档自动生成完整的单文件 HTML 技术评审系统。

## 🚀 快速开始

### 安装技能

\`\`\`bash
# 方式一：项目级安装
mkdir -p .claude/skills
git clone https://github.com/your-username/tech-review-system-generator.git .claude/skills/tech-review-system-generator

# 方式二：全局安装
git clone https://github.com/your-username/tech-review-system-generator.git ~/.claude/skills/tech-review-system-generator
\`\`\`

### 使用技能

\`\`\`markdown
# 在 Claude Code 中
请使用 tech-review-system-generator 技能，为 ./REQ.md 生成评审系统
\`\`\`

## 📖 详细文档

查看 [README.md](README.md) 获取完整使用指南。

## 📄 许可证

本项目采用 MIT 许可证 - 详见 [LICENSE](LICENSE) 文件。

## 🤝 贡献

欢迎提交 Issue 和 Pull Request！
```

---

## ⚠️ 常见错误

### 错误 1：包含了生成的 HTML 文件

**问题**：将 `index.html` 包含在仓库中

**解决**：
```bash
# 从 Git 中移除但保留本地文件
git rm --cached index.html
echo "*.html" >> .gitignore
git add .gitignore
git commit -m "Remove generated HTML files"
```

### 错误 2：包含了敏感配置

**问题**：`settings.json` 中包含 API 密钥

**解决**：
```bash
# 从 Git 中移除敏感文件
git rm settings.json
echo "settings.json" >> .gitignore
git add .gitignore
git commit -m "Remove sensitive config"

# 重置历史（如果已推送）
# 警告：这会改写 Git 历史
git filter-branch --force --index-filter \
  "git rm --cached --ignore-unmatch settings.json" \
  --prune-empty --tag-name-filter cat -- --all
```

### 错误 3：包含了大文件

**问题**：仓库体积过大（>50MB）

**解决**：
```bash
# 查找大文件
git rev-list --objects --all |
  git cat-file --batch-check='%(objecttype) %(objectname) %(objectsize) %(rest)' |
  awk '/^blob/ {print substr($0,6)}' |
  sort -nk2 |
  tail -10

# 移除大文件后，清理历史
git filter-repo --path large-file.zip --invert-paths
git gc --aggressive --prune=now
```

---

## 📚 参考资料

- [GitHub Ignoring Files](https://docs.github.com/en/get-started/getting-started-with-git/ignoring-files)
- [Git SCM - gitignore](https://git-scm.com/docs/gitignore)
- [Choose an Open Source License](https://choosealicense.com/)

---

**最后更新**：2025-03-04
