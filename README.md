# Code

团队开发代码库，支持从提交到验证的完整开发流程。

## 快速开始

### 环境要求

- Node.js 18.x 或 20.x
- npm 9.x 或更高版本
- Git 2.x

### 初始化项目

```bash
# 克隆仓库
git clone https://github.com/coder-Mr-song/Code.git
cd Code

# 安装依赖
npm install

# 运行测试
npm test

# 构建项目
npm run build
```

## 项目结构

```
Code/
├── .github/
│   └── workflows/        # GitHub Actions CI 配置
├── src/                  # 源代码目录
│   ├── __tests__/       # 测试文件
│   └── index.ts         # 入口文件
├── dist/                 # 构建输出（自动生成）
├── package.json          # 项目配置
├── tsconfig.json         # TypeScript 配置
├── jest.config.js        # 测试配置
└── README.md            # 项目文档
```

## 开发流程

### 分支策略

我们采用 **功能分支工作流**：

1. **主分支（master）**
   - 始终保持稳定可发布状态
   - 受保护，禁止直接推送
   - 所有更改必须通过 Pull Request 合并

2. **功能分支**
   - 从 `master` 分支创建
   - 命名规范：`feature/<功能名>` 或 `fix/<问题描述>`
   - 完成后通过 PR 合并回 `master`

### 提交工作流

```bash
# 1. 创建新分支
git checkout -b feature/your-feature-name

# 2. 进行开发并提交
git add .
git commit -m "feat: 添加新功能描述"

# 3. 推送到远程
git push origin feature/your-feature-name

# 4. 在 GitHub 上创建 Pull Request
```

### 提交信息规范

遵循 [Conventional Commits](https://www.conventionalcommits.org/) 规范：

- `feat:` 新功能
- `fix:` 修复问题
- `docs:` 文档更新
- `style:` 代码格式调整（不影响功能）
- `refactor:` 重构代码
- `test:` 测试相关
- `chore:` 构建或辅助工具变动

示例：
```
feat: 添加用户认证功能
fix: 修复登录页面崩溃问题
docs: 更新 API 文档
```

## 持续集成（CI）

每次 push 或 Pull Request 时，GitHub Actions 会自动运行：

1. **代码检查**（ESLint）
2. **格式检查**（Prettier）
3. **构建**（TypeScript 编译）
4. **测试**（Jest 单元测试）
5. **覆盖率报告**

CI 必须通过才能合并 PR。查看 `.github/workflows/ci.yml` 了解详细配置。

## 可用命令

```bash
npm run build        # 编译 TypeScript
npm test            # 运行测试
npm run lint        # 代码检查
npm run format      # 格式化代码
npm run format:check # 检查代码格式
```

## Pull Request 流程

1. **创建 PR**
   - 填写清晰的标题和描述
   - 关联相关的 issue（如有）
   - 确保 CI 全部通过

2. **代码审查**
   - 至少一位团队成员审查
   - 解决所有审查意见

3. **合并**
   - CI 通过 ✅
   - 审查通过 ✅
   - 使用 "Squash and merge" 保持历史清晰

## 分支保护规则

`master` 分支已启用以下保护：

- ✅ 要求 Pull Request 才能合并
- ✅ 要求状态检查通过（CI）
- ✅ 禁止强制推送
- ✅ 禁止删除分支

## 贡献指南

1. Fork 本仓库
2. 创建功能分支
3. 提交更改（遵循提交规范）
4. 推送到你的 Fork
5. 创建 Pull Request

## 问题反馈

如遇到问题，请在 [Issues](https://github.com/coder-Mr-song/Code/issues) 中提交。

## 许可证

ISC