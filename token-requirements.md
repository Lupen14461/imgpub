# GitHub Token 权限要求

## PicGo 上传图片到 GitHub 仓库需要的权限：

### Fine-grained token 需要的权限：
- ✅ **Contents** - Read and write（读写仓库内容）
- ✅ **Metadata** - Read（读取仓库元数据）

### Classic token 需要的权限：
- ✅ **repo** - 完整的仓库访问权限
  - repo:status
  - repo_deployment
  - public_repo
  - repo:invite
  - security_events

### 可选权限：
- **write:packages** - 如果你计划使用 GitHub Packages
- **read:user** - 读取用户信息

## 创建新 Token 的步骤：

### 推荐方式：Fine-grained personal access token (repo-scoped)

⚠️ **重要提醒**：Fine-grained token 的权限在创建时就固定了，创建后无法修改！如果权限不足，需要删除重新创建。

1. 访问：https://github.com/settings/tokens
2. 点击 "Generate new token" > "Generate new token (beta)"
3. 设置 Token 名称（如：PicGo-imgpub）
4. 选择过期时间（建议选择较长时间）
5. **Resource owner**: 选择你自己的账户
6. **Repository access**: 选择 "Selected repositories"，然后选择你的 imgpub 仓库
7. **Repository permissions** 中设置（⚠️ 必须在创建时就设置好）：
   - ✅ **Contents**: Read and write（用于上传文件）
   - ✅ **Metadata**: Read（读取仓库基本信息）
8. 点击 "Generate token"
9. 复制生成的 Token（只显示一次！）

**如果遗漏权限**：删除当前 token，重新创建并确保勾选所有必要权限。

### 备选方式：Classic personal access token

1. 访问：https://github.com/settings/tokens
2. 点击 "Generate new token" > "Generate new token (classic)"
3. 设置 Token 名称（如：PicGo-imgpub）
4. 选择过期时间（建议选择较长时间或不过期）
5. 勾选 **repo** 权限（这会自动包含所有子权限）
6. 点击 "Generate token"
7. 复制生成的 Token（只显示一次！）

## 测试 Token 是否有效：

在 PicGo 中配置完成后，可以通过以下方式测试：
1. 上传一张小图片
2. 检查是否成功上传到你的仓库
3. 验证生成的链接是否可以访问

## 常见问题：

### Token 相关问题：
1. **401 Unauthorized** - Token 无效或过期
2. **403 Forbidden** - Token 权限不足
3. **404 Not Found** - 仓库名称错误或不存在

### Fine-grained Token 特殊问题：
4. **权限不足但无法修改** - Fine-grained token 创建后无法编辑权限，需要删除重新创建
5. **仓库选择错误** - 创建时没有选择正确的仓库，需要重新创建
6. **过期时间太短** - 建议设置较长的过期时间，避免频繁更换

### 解决方案：
- 如果是 Fine-grained token 权限问题：删除当前 token → 重新创建 → 确保勾选所有必要权限
- 如果是 Classic token 问题：可以编辑现有 token 或创建新的
