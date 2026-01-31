# Pake Windows & Mac 打包（6 平台 × 国内/国外 × 2 系统）

这个仓库用 **GitHub Actions** 调用 **Pake CLI**，把 6 个平台分别按「国内 / 国外」两个 URL 打包成 Windows 和 Mac 桌面套壳应用（共 24 个产物）。

## 你需要做的事（一次性）

### 1) 在 GitHub 仓库里配置 URL（推荐用 Secrets，可选）

进入：`Settings` → `Secrets and variables` → `Actions` → `New repository secret`

这个 workflow 支持两种方式提供 URL：

- 推荐：用 GitHub Actions Secrets（便于后续改 URL，不改代码）
- 备选：直接在 workflow 的 `matrix.url` 里写死（Morngpt 已经写好）

如果你用 Secrets，按下面名称创建 12 个 secret（值就是对应的 URL）：

- `SITEHUB_URL_CN`
- `SITEHUB_URL_GLOBAL`
- `PERSONALINK_URL_CN`
- `PERSONALINK_URL_GLOBAL`
- `MORNSPEAKER_URL_CN`
- `MORNSPEAKER_URL_GLOBAL`
- `MORNCLIENT_URL_CN`
- `MORNCLIENT_URL_GLOBAL`
- `MORNCOACH_URL_CN`
- `MORNCOACH_URL_GLOBAL`
- `MORNTool_URL_CN`
- `MORNTool_URL_GLOBAL`

Morngpt 默认 URL 已预置：

- CN: https://morngpt.mornscience.top/
- Global: https://mornhub.net/

如果你也想把另外两个平台写死到代码里：打开 `.github/workflows/pake-windows.yml` 和 `.github/workflows/pake-mac.yml`，把对应条目的 `url: ""` 填上即可。

> 说明：workflow 里不会把 URL 打印到日志里，但 URL 仍会被用于打包。

### 2) 图标文件

本仓库默认使用 `new/` 文件夹下这 6 个 `.png`：

- `new/sitehub图标.png`
- `new/personlink图标.png`
- `new/mornspeaker图标.png`
- `new/mornclient图标.png`
- `new/morncoach图标.png`
- `new/morntool图标.png`

如需替换，保持文件名不变即可，或去 workflow 里改映射。

## 如何触发构建

- 推送代码：会自动在 Actions 里构建并上传 24 个 artifacts（12 Windows + 12 Mac）
- 打 tag 发版：创建 `v1.0.0` 这类 tag 并 push，会自动生成 GitHub Release 并把 24 个产物作为附件上传

示例：

```bash
git tag v1.0.0
git push origin v1.0.0
```

## 产物在哪里

- Actions 页面 → 对应 workflow run → `Artifacts`
- Release（仅 tag 触发时）→ Release Assets

# windowsAppconversion
