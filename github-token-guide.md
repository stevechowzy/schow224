# GitHub Token 使用指南

## 创建Token步骤
1. 访问GitHub个人设置中的Developer Settings
2. 选择Personal Access Tokens (Classic)
3. 点击"Generate new token"
4. 设置Token权限：
   - repo（完整仓库访问权限）
   - workflow（工作流权限）
5. 设置合理的过期时间（建议30-90天）
6. 生成后立即保存token字符串（注意：token只显示一次）

## 使用注意事项
1. Token安全
   - 永远不要在代码中直接硬编码token
   - 不要在公开场合分享token
   - token泄露后要立即在GitHub中撤销

2. 权限管理
   - 仅授予必要的最小权限
   - 定期检查并更新token
   - 过期前及时更新新token

3. 环境配置
   - 在本地开发环境中使用环境变量存储token
   - 在CI/CD中使用GitHub Secrets存储token

## Token使用场景
1. 命令行Git操作认证
2. API访问认证
3. 自动化工作流认证

## 最佳实践
1. 使用环境变量：
   ```bash
   export GITHUB_TOKEN=your_token_here
   ```

2. 在.gitignore中添加token相关文件
3. 定期轮换token以提高安全性
4. 为不同项目使用不同的token

注意：本文档仅供内部参考，请勿外传。

## Git命令示例
1. 配置环境变量后的Git操作：
   ```bash
   # 设置环境变量
   export GITHUB_TOKEN=your_token_here
   
   # 使用环境变量进行Git操作
   git remote set-url origin https://oauth2:${GITHUB_TOKEN}@github.com/username/repository.git
   git push origin main
   ```

2. 或直接在克隆时使用token：
   ```bash
   git clone https://oauth2:your_token_here@github.com/username/repository.git
   ```

注意：请将your_token_here替换为实际的GitHub Token，username和repository替换为实际的用户名和仓库名。