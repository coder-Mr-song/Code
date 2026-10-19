# 贡献指南

感谢你考虑为本项目做出贡献！本文档提供了参与项目开发的详细指南。

## 行为准则

- 保持尊重和专业的交流
- 欢迎建设性的反馈和讨论
- 尊重不同的观点和经验

## 如何贡献

### 报告问题

发现 bug 或有功能建议时：

1. 检查 [Issues](https://github.com/coder-Mr-song/Code/issues) 中是否已存在类似问题
2. 如果没有，创建新的 issue，包含：
   - 清晰的标题
   - 详细的问题描述
   - 复现步骤（对于 bug）
   - 期望行为
   - 实际行为
   - 环境信息（Node.js 版本等）

### 提交代码

#### 1. 准备开发环境

```bash
# Fork 并克隆仓库
git clone https://github.com/YOUR_USERNAME/Code.git
cd Code

# 添加上游仓库
git remote add upstream https://github.com/coder-Mr-song/Code.git

# 安装依赖
npm install
```

#### 2. 创建分支

```bash
# 更新 master 分支
git checkout master
git pull upstream master

# 创建功能分支
git checkout -b feature/your-feature-name
```

分支命名规范：
- `feature/功能名` - 新功能
- `fix/问题描述` - bug 修复
- `docs/文档主题` - 文档更新
- `refactor/重构范围` - 代码重构

#### 3. 进行开发

- 编写清晰、可维护的代码
- 遵循项目的代码风格（使用 ESLint 和 Prettier）
- 为新功能添加测试
- 更新相关文档

#### 4. 提交更改

```bash
# 运行检查
npm run lint
npm run format:check
npm test
npm run build

# 提交代码
git add .
git commit -m "feat: 添加新功能的简短描述"
```

提交信息格式：

```
<类型>: <简短描述>

[可选的详细说明]

[可选的关联 issue]
```

类型包括：
- `feat` - 新功能
- `fix` - bug 修复
- `docs` - 文档更新
- `style` - 代码格式（不影响功能）
- `refactor` - 重构
- `test` - 测试相关
- `chore` - 构建或工具变动

示例：
```
feat: 添加用户认证中间件

实现基于 JWT 的认证中间件，支持：
- Token 验证
- 权限检查
- 错误处理

关联 #123
```

#### 5. 推送并创建 Pull Request

```bash
# 推送到你的 Fork
git push origin feature/your-feature-name
```

在 GitHub 上创建 Pull Request：

1. 访问你的 Fork 页面
2. 点击 "Compare & pull request"
3. 填写 PR 信息：
   - **标题**：清晰描述更改内容
   - **描述**：详细说明更改的动机和实现方式
   - **关联 issue**：使用 `Closes #123` 或 `Fixes #456`
   - **测试说明**：如何验证更改
4. 提交 PR

## 代码规范

### TypeScript 风格

- 使用 TypeScript 严格模式
- 明确声明类型，避免使用 `any`
- 使用接口和类型别名提高可读性
- 使用枚举管理常量集合

示例：
```typescript
// 好的做法
interface User {
  id: string;
  name: string;
  email: string;
}

function getUser(id: string): User | null {
  // ...
}

// 避免
function getUser(id: any): any {
  // ...
}
```

### 测试规范

- 每个功能模块都应有对应的测试
- 测试文件放在 `__tests__` 目录
- 使用描述性的测试名称
- 覆盖正常情况和边界情况

示例：
```typescript
describe('UserService', () => {
  describe('getUser', () => {
    it('should return user when id exists', () => {
      // ...
    });

    it('should return null when id does not exist', () => {
      // ...
    });

    it('should throw error when id is invalid', () => {
      // ...
    });
  });
});
```

### 文档规范

- 为公共 API 添加 JSDoc 注释
- 复杂逻辑添加行内注释
- 更新 README 和相关文档

示例：
```typescript
/**
 * 根据 ID 获取用户信息
 * @param id - 用户 ID
 * @returns 用户对象，如果不存在则返回 null
 * @throws {ValidationError} 当 ID 格式无效时
 */
function getUser(id: string): User | null {
  // ...
}
```

## Pull Request 审查流程

### 提交者责任

- 确保 CI 全部通过
- 及时回复审查意见
- 保持 PR 专注于单一目标
- 保持 PR 大小适中（建议 < 500 行）

### 审查者关注点

- 代码质量和可维护性
- 测试覆盖率
- 文档完整性
- 性能影响
- 安全问题

### 合并条件

- ✅ CI 全部通过
- ✅ 至少一位审查者批准
- ✅ 所有讨论已解决
- ✅ 代码符合项目规范

## 开发技巧

### 本地测试

```bash
# 运行所有测试
npm test

# 监听模式
npm test -- --watch

# 生成覆盖率报告
npm test -- --coverage

# 运行特定测试文件
npm test -- path/to/test.spec.ts
```

### 调试

```bash
# 使用 Node.js 调试器
node --inspect-brk node_modules/.bin/jest --runInBand

# VS Code 用户可以使用内置调试器
# 配置见 .vscode/launch.json
```

### 保持同步

```bash
# 定期同步上游更改
git fetch upstream
git checkout master
git merge upstream/master
git push origin master

# 将 master 合并到功能分支
git checkout feature/your-feature
git merge master
```

## 发布流程

（维护者专用）

1. 更新版本号（遵循语义化版本）
2. 更新 CHANGELOG
3. 创建发布标签
4. 推送到 GitHub
5. 发布到 npm（如适用）

## 获取帮助

- 📖 查看 [README](README.md)
- 💬 在 issue 中提问
- 📧 联系维护者

## 致谢

感谢所有贡献者对本项目的支持！
