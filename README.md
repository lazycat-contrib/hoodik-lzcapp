# Hoodik - LazyCat App

[Hoodik](https://github.com/hudikhq/hoodik)（轻量级、端到端加密的自建云存储）的懒猫微服（LazyCat）打包。

## 模式

- **镜像模式（mirror）**：`hoodik` 镜像经 `docker.1ms.run` 加速器拉取，`require_digest_match: true` 校验镜像内容与上游一致。
- **自动跟随上游**：每日检查上游 `hudik/hoodik` 的 semver tag（`channel: stable`），发现新版本自动更新版本号与镜像、构建 LPK、发布商店。
- **喵喵商店发布**：仅私有商店（MiaoMiao private store），不发布官方商店。

## 结构

| 文件 | 说明 |
| --- | --- |
| `package.yml` | 包元数据（`cloud.lazycat.app.hoodik`） |
| `lzc-manifest.yml` | 服务与路由配置（mirror 镜像 + upstream 注释） |
| `lzc-build.yml` | 构建配置 |
| `dist/env.yml` | 邮件等运行时配置模板（setup_script 首次复制到 /data） |
| `icon.png` | 图标 |
| `.github/lazycat-action.yml` | [lazycat-github-action](https://github.com/ca-x/lazycat-github-action) 配置 |
| `.github/workflows/lazycat.yml` | 构建 + 发布工作流 |

## 所需 Secrets

| Secret | 说明 |
| --- | --- |
| `APPSTORE_URL` / `APPSTORE_TOKEN` | 喵喵商店 API 地址与发布令牌 |
| `APP_ID` | 可选 |
| `PRIVATE_STORE_GROUP_CODES` | 可选，私有分组码 |
