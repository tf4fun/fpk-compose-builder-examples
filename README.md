# FnPack Auto Builder

基于 GitHub Actions 的 FnPack 应用自动打包工具。

## GitHub Action

### 输入

| 参数 | 说明 |
|------|------|
| `input-dir` | 应用源目录，包含 `compose.yaml` |
| `output-dir` | 输出目录 |

### 输出

- 构建产物：`.fpk` 安装包
- Push 到 `main` / `dev_*`：上传为 Artifact
- 推送 Tag `v*.*.*`：创建 Release 并发布

### 使用的 Action

```yaml
- uses: tf4fun/fpk-compose-builder@main
  with:
    input-dir: ./examples/your-app
    output-dir: ./dist/your-app
```

## 打包文件结构

```
examples/your-app/
├── compose.yaml    # 必需：应用配置
├── icon.png        # 可选：应用图标
└── LICENSE.txt     # 可选：许可证
```

## 示例说明

### nginx - 最小化示例

最简单的打包配置，仅包含基础的 Docker Compose 服务定义，适合快速了解打包流程。

📁 [examples/nginx/compose.yaml](examples/nginx/compose.yaml)

---

### bilibili - 自定义 UI 入口

展示如何配置应用清单（`manifest`）和桌面应用入口（`app/ui/config`）。

📁 [examples/bilibili/compose.yaml](examples/bilibili/compose.yaml)

---

### lobe-chat - 安装向导

展示如何添加安装向导（`wizard/install`），让用户在安装时配置参数，并在 services 中通过 `${wizard_xxx}` 引用。

📁 [examples/lobe-chat/compose.yaml](examples/lobe-chat/compose.yaml)

---

### nocodb / chromium - 完整示例

包含所有配置项的完整示例：

- `manifest` - 应用元信息（名称、版本、维护者等）
- `wizard/install` - 安装向导（带输入验证）
- `app/ui/config` - 桌面入口配置
- `config/resource` - 数据持久化和权限配置

**NocoDB** 展示了邮箱格式验证和密码强度验证规则。

📁 [examples/nocodb/compose.yaml](examples/nocodb/compose.yaml)

**Chromium** 展示了多端口、共享内存、子路径访问等高级配置。

📁 [examples/chromium/compose.yaml](examples/chromium/compose.yaml)

## 官方文档

完整的 FnPack 开发文档请参考：https://developer.fnnas.com/docs/guide
