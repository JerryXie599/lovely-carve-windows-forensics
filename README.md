# LovelyCarve Windows 基础信息、痕迹与事件日志取证插件

插件 ID：`org.lovelycarve.winevtx`（LPP v2，`v2.3.0`）

> 本仓库仅提供面向 **LovelyCarve** 的 Release `.lcpkg` 二进制插件包发布与使用说明，不包含源码。

## 下载与安装（双版本对照）

请根据你使用的 LovelyCarve 主程序版本，前往 **[Releases](../../releases)** 下载对应的 `.lcpkg` 包：

| 适用主程序 | Release 版本 | 下载文件名 | 说明 |
| --- | --- | --- | --- |
| **官方主项目** ([LovelyTeams/LovelyCarve](https://github.com/LovelyTeams/LovelyCarve)) | [`v2.3.0`](../../releases/tag/v2.3.0) | `org.lovelycarve.winevtx-2.3.0-windows-x64.lcpkg` | 标准 LPP v2 协议，无魔改扩展（`schema_hash: fnv1a64:c462cc9c93a9a543`） |
| **二开增强版** ([JerryXie599/LovelyCarve-Mod](https://github.com/JerryXie599/LovelyCarve-Mod)) | [`v2.3.0-mod`](../../releases/tag/v2.3.0-mod) | `org.lovelycarve.winevtx-2.3.0-mod-windows-x64.lcpkg` | 完整适配二开版快速分析内联子项勾选与按列筛选体验 |

### 安装方式
- **图形界面**：打开 LovelyCarve → **「设置 → 插件 → 安装 .lcpkg」**，选择下载的 `.lcpkg` 文件。
- **命令行**：
  ```bash
  lovelycarve-cli plugin install org.lovelycarve.winevtx-2.3.0-windows-x64.lcpkg
  ```

## 核心能力（共 41 类结构化取证记录）

### 1. Windows 系统基础信息与注册表/SAM 痕迹（`win_baseinfo` / `win_baseinfo_evidence` / `win_registry_files`）
覆盖 16 大分析子项：
- **系统与用户**：OS 版本/安装时间/主机名/时区、SAM 本地用户与密码提示/密保、账户与密码策略、用户配置与默认浏览器
- **网络与无线**：网卡配置、Wi-Fi 与已知网络、防火墙规则、**蓝牙设备与配对连接记录**
- **服务与执行痕迹**：系统服务与计划任务、安装软件/自启动/文件打开方式、**ShimCache / Prefetch / Amcache**、硬件信息与 USB 插拔记录
- **用户活动与凭据**：用户痕迹/桌面/快捷方式/时间轴、回收站记录、Win11 记事本与系统通知、凭据文件与 Windows Defender 检测记录
- **远程访问与凭据解析**：远程桌面（RDP）、SSH、远控工具及 SecureCRT / MobaXterm 凭据解密

### 2. Windows 事件日志（EVTX）分析与威胁狩猎（`winevtx_system` / `winevtx_evidence` / `winevtx_files`）
支持系统卷自动识别、全盘 EVTX 快速排查与右键单文件解析，涵盖登录审计、进程创建、服务/计划任务持久化、RDP/SSH 远程访问事件、蓝牙事件日志及威胁狩猎规则提取。
