# TimedOnlineRewards - 定时在线奖励插件 / Timed Online Rewards Plugin

[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Minecraft](https://img.shields.io/badge/minecraft-1.16%2B-green.svg)](https://minecraft.net)
[![Java](https://img.shields.io/badge/java-17%2B-orange.svg)](https://openjdk.java.net)

一个功能强大的Minecraft Bukkit/Spigot插件，为服务器提供灵活的定时奖励系统。支持多种时间模式、丰富的奖励类型和完善的离线奖励处理机制。

A powerful Minecraft Bukkit/Spigot plugin that provides a flexible timed reward system for servers. Supports multiple time modes, rich reward types, and comprehensive offline reward handling mechanisms.

## ✨ 主要特性 / Main Features

- 🕒 **多种时间模式 / Multiple Time Modes** - 支持每日、每周、每月、特定时间和相对时间 / Supports daily, weekly, monthly, specific time and relative time
- 🎁 **丰富奖励类型 / Rich Reward Types** - 物品、金币、经验、自定义命令 / Items, coins, experience, custom commands
- 👥 **离线奖励处理 / Offline Reward Handling** - 保留、延迟发放或跳过离线玩家奖励 / Keep, delay or skip offline player rewards
- 🖥️ **图形化管理界面 / Graphical Management Interface** - 直观的GUI管理系统 / Intuitive GUI management system
- ⚙️ **灵活配置 / Flexible Configuration** - 完全可自定义的配置文件 / Fully customizable configuration files
- 🔧 **权限系统 / Permission System** - 细粒度的权限控制 / Fine-grained permission control
- 💾 **数据备份 / Data Backup** - 自动备份重要数据 / Automatic backup of important data

## 📸 界面预览 / Interface Preview

### 主管理界面 / Main Management Interface
![主界面](images/main-gui.png)
*主管理界面 - 查看和管理所有奖励计划 / Main management interface - View and manage all reward plans*

### 创建奖励计划 / Create Reward Plan
![创建计划](images/create-plan.png)
*创建新的奖励计划 / Create new reward plans*

### 时间设置界面 / Time Setting Interface
![时间设置](images/time-setting.png)
*灵活的时间配置选项 / Flexible time configuration options*

### 奖励内容设置 / Reward Content Setting
![奖励设置](images/reward-setting.png)
*丰富的奖励类型配置 / Rich reward type configuration*

## 🚀 快速开始 / Quick Start

### 系统要求 / System Requirements

- Minecraft 1.16+
- Java 17+
- Bukkit/Spigot/Paper 服务器 / server
- Vault插件（可选，用于经济系统支持）/ Vault plugin (optional, for economy system support)

### 安装步骤 / Installation Steps

1. 下载最新版本的插件jar文件 / Download the latest plugin jar file
2. 将jar文件放入服务器的 `plugins` 文件夹 / Place the jar file in the server's `plugins` folder
3. 重启服务器 / Restart the server
4. 使用 `/tr` 命令打开管理界面 / Use `/tr` command to open the management interface

### 基本配置 / Basic Configuration

插件首次运行时会自动生成配置文件：/ The plugin will automatically generate configuration files on first run:

```yaml
# config.yml - 主配置文件 / Main configuration file
prefix: "§6[定时奖励] "
debug-mode: false

rewards:
  offline-handling: "keep"  # keep/delay/skip

messages:
  offline-welcome: "§e欢迎回来！您有 §a%count% §e个离线奖励待领取"
  offline-hint: "§7使用 §f/tr offline §7查看和领取离线奖励"
```

## 📋 命令列表 / Command List

| 命令 / Command | 描述 / Description | 权限 / Permission |
|------|------|------|
| `/tr` | 打开主管理界面 / Open main management interface | `timedrewards.admin` |
| `/tr list` | 列出所有奖励计划 / List all reward plans | `timedrewards.list` |
| `/tr toggle <计划ID>` | 启用/禁用奖励计划 / Enable/disable reward plan | `timedrewards.edit` |
| `/tr reload` | 重新加载配置 / Reload configuration | `timedrewards.admin` |
| `/tr offline` | 查看离线奖励 / View offline rewards | `timedrewards.offline` |
| `/tr offline list` | 查看离线奖励详情 / View offline reward details | `timedrewards.offline` |
| `/tr offline claim` | 领取离线奖励 / Claim offline rewards | `timedrewards.offline` |
| `/tr help` | 显示帮助信息 / Show help information | - |

## 🔐 权限系统 / Permission System

| 权限节点 / Permission Node | 描述 / Description | 默认 / Default |
|----------|------|------|
| `timedrewards.admin` | 管理员权限 / Administrator permission | op |
| `timedrewards.create` | 创建奖励计划 / Create reward plans | op |
| `timedrewards.edit` | 编辑奖励计划 / Edit reward plans | op |
| `timedrewards.delete` | 删除奖励计划 / Delete reward plans | op |
| `timedrewards.list` | 查看奖励计划列表 / View reward plan list | true |
| `timedrewards.offline` | 管理离线奖励 / Manage offline rewards | true |

## ⚙️ 配置说明 / Configuration Guide

### 时间模式配置 / Time Mode Configuration

```yaml
timeSettings:
  type: "daily"        # daily/weekly/monthly/specific/relative
  hour: 12            # 小时 (0-23) / Hour (0-23)
  minute: 0           # 分钟 (0-59) / Minute (0-59)
  second: 0           # 秒 (0-59) / Second (0-59)
  dayOfWeek: 1        # 星期几 (1-7, 仅weekly模式) / Day of week (1-7, weekly mode only)
  dayOfMonth: 1       # 每月第几天 (1-31, 仅monthly模式) / Day of month (1-31, monthly mode only)
```

### 奖励内容配置 / Reward Content Configuration

```yaml
rewards:
  items:              # 物品奖励列表 / Item reward list
    - type: DIAMOND
      amount: 5
  economy: 100.0      # 金币奖励 / Economy reward
  experience: 50      # 经验奖励 / Experience reward
  commands:           # 命令奖励 / Command rewards
    - "give %player% minecraft:diamond 1"
```

### 离线奖励处理 / Offline Reward Handling

- **keep** - 保留离线奖励，玩家上线后可手动领取 / Keep offline rewards, players can manually claim after coming online
- **delay** - 延迟发放，玩家上线时自动发放所有离线奖励 / Delay distribution, automatically distribute all offline rewards when players come online
- **skip** - 跳过离线玩家，不发放奖励 / Skip offline players, do not distribute rewards

## 🛠️ 开发构建 / Development Build

### 环境要求 / Environment Requirements

- JDK 17+
- Maven 3.6+
- Git

### 构建步骤 / Build Steps

```bash
# 克隆仓库 / Clone repository
git clone https://github.com/your-username/TimedOnlineRewards.git
cd TimedOnlineRewards

# 编译项目 / Compile project
mvn clean compile

# 打包插件 / Package plugin
mvn package

# 生成的jar文件位于 / Generated jar file is located at
# target/TimedOnlineRewards-1.0.0.jar
```

### 项目结构 / Project Structure

```
src/
├── main/
│   ├── java/com/example/timedonlinerewards/
│   │   ├── commands/          # 命令处理器 / Command handlers
│   │   ├── config/            # 配置管理 / Configuration management
│   │   ├── gui/               # GUI界面 / GUI interfaces
│   │   ├── listeners/         # 事件监听器 / Event listeners
│   │   ├── managers/          # 核心管理器 / Core managers
│   │   ├── models/            # 数据模型 / Data models
│   │   └── utils/             # 工具类 / Utility classes
│   └── resources/
│       ├── config.yml         # 默认配置 / Default configuration
│       ├── rewards.yml        # 奖励配置 / Reward configuration
│       └── plugin.yml         # 插件描述 / Plugin description
```

## 🎯 命令奖励详解 / Command Rewards Guide

### 功能概述 / Function Overview
命令奖励允许您在发放奖励时执行自定义的服务器命令，这为奖励系统提供了极大的灵活性。所有命令以控制台权限执行，可以实现几乎任何类型的奖励效果。

Command rewards allow you to execute custom server commands when distributing rewards, providing great flexibility to the reward system. All commands are executed with console permissions and can achieve almost any type of reward effect.

### 设置方法 / Setup Method

#### 通过GUI设置（推荐）/ Setup via GUI (Recommended)
1. 使用命令 `/tr` 打开主界面 / Use command `/tr` to open main interface
2. 点击"创建奖励计划"或选择现有计划进行编辑 / Click "Create Reward Plan" or select existing plan to edit
3. 在奖励设置界面点击 **"命令奖励"** 按钮 / Click **"Command Rewards"** button in reward setting interface
4. 系统会提示您在聊天框中输入命令 / System will prompt you to enter command in chat
5. 输入要执行的命令（**不需要**添加 `/` 前缀）/ Enter command to execute (**no need** to add `/` prefix)
6. 点击"保存设置"按钮完成设置 / Click "Save Settings" button to complete setup

### 使用示例 / Usage Examples

#### 基础命令示例 / Basic Command Examples
```
# 给玩家物品 / Give player items
give %player% diamond_sword 1

# 传送玩家到spawn点 / Teleport player to spawn
spawn %player%

# 给玩家添加临时飞行权限（需要权限插件）/ Give player temporary fly permission (requires permission plugin)
lp user %player% permission settemp essentials.fly true 1h

# 发送全服公告 / Send server-wide announcement
broadcast §6[奖励] §e%player% §a获得了特殊奖励！

# 给予经济奖励（需要经济插件）/ Give economy reward (requires economy plugin)
eco give %player% 1000
```

## 📊 离线奖励详解 / Offline Rewards Guide

### 工作原理 / How It Works
当奖励计划执行时，插件会检查所有应该接收奖励的玩家：
- **在线玩家** - 立即发放奖励
- **离线玩家** - 根据配置处理

When reward plans execute, the plugin checks all players who should receive rewards:
- **Online players** - Distribute rewards immediately
- **Offline players** - Handle according to configuration

### 三种处理模式 / Three Handling Modes

#### 1. 保留模式 (keep) / Keep Mode
```yaml
offline-handling: "keep"
```
- 离线奖励保存到文件 / Offline rewards saved to files
- 玩家上线时收到提示消息 / Players receive notification when coming online
- 使用命令手动领取奖励 / Use commands to manually claim rewards
- 适合重要奖励，确保玩家不错过 / Suitable for important rewards, ensuring players don't miss them

**玩家体验 / Player Experience：**
```
[定时奖励] §e欢迎回来！您有 §a2 §e个离线奖励待领取
[定时奖励] §7使用 §f/tr offline §7查看和领取离线奖励
```

#### 2. 跳过模式 (skip) / Skip Mode
```yaml
offline-handling: "skip"
```
- 离线玩家直接跳过奖励 / Offline players are directly skipped for rewards
- 不保存任何记录 / No records are saved
- 适合鼓励在线活跃度的奖励 / Suitable for rewards that encourage online activity

#### 3. 延迟模式 (delay) / Delay Mode
```yaml
offline-handling: "delay"
```
- 离线奖励保存到文件 / Offline rewards saved to files
- 玩家上线时自动发放所有奖励 / Automatically distribute all rewards when players come online
- 适合日常小奖励，简化操作 / Suitable for daily small rewards, simplifying operations

## 🤝 贡献指南 / Contributing Guide

我们欢迎任何形式的贡献！/ We welcome contributions of any kind!

1. Fork 这个仓库 / Fork this repository
2. 创建您的特性分支 / Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. 提交您的更改 / Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. 推送到分支 / Push to the branch (`git push origin feature/AmazingFeature`)
5. 打开一个 Pull Request / Open a Pull Request

### 开发规范 / Development Standards

- 遵循Java代码规范 / Follow Java coding standards
- 添加适当的注释和文档 / Add appropriate comments and documentation
- 确保所有测试通过 / Ensure all tests pass
- 更新相关文档 / Update relevant documentation

## 📝 更新日志 / Changelog

### v1.0.0
- 🎉 首次发布 / Initial release
- ✨ 基础定时奖励功能 / Basic timed reward functionality
- 🖥️ GUI管理界面 / GUI management interface
- 🎁 多种奖励类型支持 / Multiple reward type support
- 👥 离线奖励处理机制 / Offline reward handling mechanism

### v1.0.1 (最新功能更新 / Latest Feature Updates)
- **新增自定义奖励消息功能 / Added custom reward message feature**：为每个奖励计划设置个性化消息 / Set personalized messages for each reward plan
- **优化奖励显示 / Optimized reward display**：奖励发放时显示详细内容和数量 / Show detailed content and quantities when distributing rewards
- **改进GUI反馈系统 / Improved GUI feedback system**：使用ActionBar提供即时操作反馈 / Use ActionBar for instant operation feedback
- **重构物品奖励设置 / Refactored item reward settings**：移除拖拽功能，改为按钮操作 / Removed drag functionality, changed to button operations
- **完善命令奖励系统 / Enhanced command reward system**：支持占位符、控制台权限执行、多命令组合 / Support placeholders, console permission execution, multiple command combinations

## 🐛 问题反馈 / Issue Reporting

如果您遇到任何问题或有功能建议，请：/ If you encounter any issues or have feature suggestions, please:

1. 查看 [Wiki](WIKI.md) 获取详细文档 / Check [Wiki](WIKI.md) for detailed documentation
2. 搜索现有的 [Issues](https://github.com/your-username/TimedOnlineRewards/issues) / Search existing [Issues](https://github.com/your-username/TimedOnlineRewards/issues)
3. 创建新的 Issue 并提供详细信息 / Create a new Issue with detailed information

## 📄 许可证 / License

本项目采用 MIT 许可证 - 查看 [LICENSE](LICENSE) 文件了解详情。

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 致谢 / Acknowledgments

- 感谢 Bukkit/Spigot 团队提供的优秀API / Thanks to the Bukkit/Spigot team for the excellent API
- 感谢 Vault 插件提供的经济系统支持 / Thanks to the Vault plugin for economy system support
- 感谢所有贡献者和用户的支持 / Thanks to all contributors and users for their support

## 📞 联系方式 / Contact

- 项目主页 / Project Homepage: [GitHub Repository](https://github.com/your-username/TimedOnlineRewards)
- 问题反馈 / Issue Reporting: [Issues](https://github.com/your-username/TimedOnlineRewards/issues)
- 讨论交流 / Discussions: [Discussions](https://github.com/your-username/TimedOnlineRewards/discussions)

---

⭐ 如果这个项目对您有帮助，请给我们一个星标！/ If this project helps you, please give us a star!