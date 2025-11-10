# Spec Presets - AI 辅助开发规范套件

完整的代码规范和模板系统，用于提升 AI 辅助开发的代码质量和一致性。

## 📦 目录结构

```
spec-presets/
├── core/                          # 核心规范（必需）
│   ├── requirements-spec.txt      # 开发需求规范（13条规则）
│   ├── requirements-spec.zh-CN.txt
│   ├── workflow-spec.txt          # 工作流规范（12条规则）
│   ├── workflow-spec.zh-CN.txt
│   ├── naming-conventions.txt     # 命名约定（12条约定）
│   ├── naming-conventions.zh-CN.txt
│   ├── spec-index.txt             # 中心索引和配置
│   └── spec-index.zh-CN.txt
│
├── quality/                       # 质量保证规范（推荐）
│   ├── testing-spec.zh-CN.txt    # 测试规范（12条规则）
│   ├── security-spec.zh-CN.txt   # 安全规范（12条规则）
│   └── error-handling-spec.zh-CN.txt  # 错误处理规范（12条规则）
│
├── architecture/                  # 架构设计规范（可选）
│   ├── api-design-spec.txt       # API 设计规范
│   └── database-spec.txt         # 数据库规范
│
├── templates/                     # 快速启动模板
│   ├── web-starter/              # Web 应用脚手架
│   ├── cli-starter/              # CLI 工具脚手架
│   └── library-starter/          # 库/SDK 脚手架
│
├── tools/                         # 规范验证工具
│   ├── spec-lint.py              # 规范检查工具
│   └── spec-report.js            # 合规报告生成器
│
└── ide-integration/               # IDE 集成配置
    ├── .vscode/settings.json     # VS Code 配置
    └── .editorconfig             # 编辑器通用配置
```

## 🚀 快速开始

### 1. 下载规范文件

```bash
# 克隆整个仓库
git clone <repository-url>

# 或使用 sparse checkout 只下载 spec-presets
git sparse-checkout set spec-presets
```

### 2. 选择项目模板

根据项目类型选择合适的模板：

```bash
# Web 应用
cd spec-presets/templates/web-starter
npm install
npm run dev

# CLI 工具
cd spec-presets/templates/cli-starter
python cli.py --items "test"

# 库/SDK
cd spec-presets/templates/library-starter
npm install
npm run build
```

### 3. 在 AI 对话中引用规范

```
@spec-presets/core/requirements-spec.zh-CN.txt
@spec-presets/quality/testing-spec.zh-CN.txt
@spec-presets/core/spec-index.zh-CN.txt

请生成一个用户登录功能，严格遵循这些规范。
```

## 📋 核心规范概览

### Requirements Spec (开发需求规范)

13 条关键规则，确保代码完整性、可运行性和质量：

- ✅ **RULE 1** - 生成完整可运行代码（无 TODO、无占位符）
- ✅ **RULE 2** - 复用现有代码和 API
- ✅ **RULE 3** - 最小化新增依赖
- ✅ **RULE 6** - 验证所有 API 是否存在（关键）
- ✅ **RULE 10** - 确保代码成功编译（关键）
- ✅ **RULE 13** - 只使用真实存在的库（关键）

### Testing Spec (测试规范)

12 条测试标准，确保代码质量：

- 测试完整性 - 新功能必须包含测试
- 覆盖率目标 - Web 70%+, CLI 80%+, Library 85%+
- 测试分层 - 单元测试 70%, 集成 20%, E2E 10%
- Mock 规范 - 外部依赖必须 Mock

### Security Spec (安全规范)

12 条安全标准，防护常见漏洞：

- 输入验证与清理 - 防止注入攻击
- 认证与授权 - 强认证细粒度授权
- 敏感数据保护 - 加密存储和传输
- OWASP Top 10 防护

### Error Handling Spec (错误处理规范)

12 条错误处理标准：

- 错误分类 - 业务/系统/第三方错误
- 自定义错误类 - 领域特定错误
- 用户友好提示 - 清晰可操作消息
- 全局错误处理器 - 统一错误中间件

## 🎯 项目类型配置

### Web 应用

```bash
# 推荐启用的规范
core/requirements-spec.txt       [启用 RULE 1,2,3,5,6,7,10,11,12,13]
core/workflow-spec.txt           [启用 RULE 1,2,6,9,10,12]
core/naming-conventions.txt      [启用 CONVENTION 1-6,9]
quality/testing-spec.txt         [启用 RULE 1-9, 目标覆盖率 70%]
quality/security-spec.txt        [启用 RULE 1-11]
quality/error-handling-spec.txt  [启用 RULE 1-11]
```

### CLI 工具

```bash
# 推荐启用的规范
core/requirements-spec.txt       [启用 RULE 1,2,3,5,6,7,10,12,13]
quality/testing-spec.txt         [启用 RULE 1-9, 目标覆盖率 80%]
quality/security-spec.txt        [启用 RULE 1,3,4,6,8,11]
quality/error-handling-spec.txt  [启用 RULE 1-7,10,11]
```

### 库/SDK

```bash
# 推荐启用的规范
core/requirements-spec.txt       [启用 RULE 1,2,3,6,7,10,12,13]
quality/testing-spec.txt         [启用 RULE 1-10, 目标覆盖率 85%]
quality/error-handling-spec.txt  [启用 RULE 1,2,5,6,10,12]
```

## 🛠️ 工具使用

### Spec Lint - 规范检查

```bash
# 检查当前目录
python spec-presets/tools/spec-lint.py

# 指定目录
python spec-presets/tools/spec-lint.py --target-dir ./src --spec-dir ./spec-presets/core

# 输出示例:
# 🔍 检查目录: ./src
# 发现 3 个问题:
#   ❌ 错误: 1
#   ⚠️  警告: 2
```

### Spec Report - 合规报告

```bash
# 生成报告
node spec-presets/tools/spec-report.js

# 保存为 JSON
node spec-presets/tools/spec-report.js --output compliance-report.json

# 输出示例:
# 📋 规范遵守情况报告
# 总体合规率: 85%
# 已启用规则: 34/40
```

## 🎨 IDE 集成

### VS Code

复制配置文件到项目根目录：

```bash
cp spec-presets/ide-integration/.vscode/settings.json .vscode/
cp spec-presets/ide-integration/.editorconfig .
```

推荐安装的扩展：

- ESLint - 代码检查
- Prettier - 代码格式化
- EditorConfig - 编辑器配置
- Todo Tree - TODO 高亮

### 其他编辑器

所有支持 EditorConfig 的编辑器都可以使用 `.editorconfig` 文件。

## 📚 使用示例

### 示例 1: 生成符合规范的登录页面

```
@spec-presets/core/requirements-spec.zh-CN.txt
@spec-presets/quality/security-spec.zh-CN.txt
@spec-presets/quality/error-handling-spec.zh-CN.txt

生成一个登录页面，包含：
1. 邮箱和密码输入
2. 表单验证
3. 错误处理
4. 安全的密码处理
```

### 示例 2: 生成 CLI 工具

```
@spec-presets/core/requirements-spec.zh-CN.txt
@spec-presets/templates/cli-starter/cli.py

参考 cli.py 的模式，生成一个文件批处理工具。
```

### 示例 3: 添加单元测试

```
@spec-presets/quality/testing-spec.zh-CN.txt
@spec-presets/core/naming-conventions.zh-CN.txt

为 UserService 类生成单元测试，确保：
- 覆盖率 > 85%
- 包含边界条件测试
- 使用 Mock 隔离外部依赖
```

## 🔄 工作流集成

### Git Hooks

在 `.git/hooks/pre-commit` 中添加：

```bash
#!/bin/bash
# 提交前检查规范
python spec-presets/tools/spec-lint.py
if [ $? -ne 0 ]; then
  echo "规范检查失败，请修复后再提交"
  exit 1
fi
```

### CI/CD

在 GitHub Actions / GitLab CI 中添加：

```yaml
# .github/workflows/spec-check.yml
name: Spec Compliance Check

on: [push, pull_request]

jobs:
  spec-check:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: Run spec lint
        run: python spec-presets/tools/spec-lint.py
      - name: Generate compliance report
        run: node spec-presets/tools/spec-report.js --output report.json
      - name: Upload report
        uses: actions/upload-artifact@v3
        with:
          name: compliance-report
          path: report.json
```

## 📊 规范统计

| 规范文件 | 规则数 | 关键规则 | 适用项目 |
|---------|-------|---------|---------|
| requirements-spec | 13 | 4 | All |
| workflow-spec | 12 | 6 | All |
| naming-conventions | 12 | 5 | All |
| testing-spec | 12 | 9 | All |
| security-spec | 12 | 11 | Web, API |
| error-handling-spec | 12 | 11 | All |

**总计**: 73 条规则，覆盖代码质量、安全、测试、工作流等各个方面。

## 🤝 贡献

欢迎提交 Issue 和 Pull Request 改进规范！

## 📄 许可证

MIT License

---

**最后更新**: 2025-11-10  
**版本**: v1.0.0
