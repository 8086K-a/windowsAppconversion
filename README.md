# Pake Windows & Mac 打包（8 平台 × 国内/国外 × 2 系统）

这个仓库用 **GitHub Actions** 调用 **Pake CLI**，把 8 个平台分别按「国内 / 国外」两个 URL 打包成 Windows 和 Mac 桌面套壳应用（共 32 个产物）。

## 你需要做的事（一次性）

### 1) URL 配置

工作流直接在代码中配置了 URL（已添加 `/admin` 路径）。

如果你想修改 URL，直接编辑 `.github/workflows/pake-windows.yml` 和 `.github/workflows/pake-mac.yml` 中的 `url` 字段。

### 2) 图标文件

本仓库默认使用 `new/` 文件夹下这 8 个 `.png`：

- `new/sitehub图标.png`
- `new/personlink图标.png`
- `new/mornspeaker图标.png`
- `new/mornclient图标.png`
- `new/morncoach图标.png`
- `new/morntool图标.png`
- `new/mornfront图标.png`
- `new/multigpt图标.png`
- `new/mornspeaker图标.png`
- `new/mornclient图标.png`
- `new/morncoach图标.png`
- `new/morntool图标.png`

如需替换，保持文件名不变即可，或去 workflow 里改映射。

## 如何触发构建

- 推送代码：会自动在 Actions 里构建并上传 32 个 artifacts（16 Windows + 16 Mac）
- 打 tag 发版：创建 `v1.0.0` 这类 tag 并 push，会自动生成 GitHub Release 并把 32 个产物作为附件上传

示例：

```bash
git tag v1.0.0
git push origin v1.0.0
```

## 产物在哪里

- Actions 页面 → 对应 workflow run → `Artifacts`
- Release（仅 tag 触发时）→ Release Assets

# windowsAppconversion
