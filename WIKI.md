# TimedOnlineRewards 插件百科 / Plugin Encyclopedia

## 概述 / Overview

**TimedOnlineRewards**（定时在线奖励插件）是一个专为Minecraft Bukkit/Spigot服务器设计的高级奖励管理系统。该插件提供了灵活的定时奖励机制，支持多种时间模式、丰富的奖励类型，以及完善的离线玩家奖励处理功能。

**TimedOnlineRewards** (Timed Online Rewards Plugin) is an advanced reward management system designed specifically for Minecraft Bukkit/Spigot servers. This plugin provides a flexible timed reward mechanism, supporting multiple time modes, rich reward types, and comprehensive offline player reward handling functionality.

## 历史与发展 / History and Development

### 项目起源 / Project Origin
TimedOnlineRewards插件诞生于对服务器管理员需求的深入理解。传统的奖励系统往往功能单一，缺乏灵活性，无法满足现代Minecraft服务器的复杂需求。本插件旨在提供一个全面、易用、功能强大的奖励管理解决方案。

The TimedOnlineRewards plugin was born from a deep understanding of server administrator needs. Traditional reward systems often have limited functionality and lack flexibility, unable to meet the complex needs of modern Minecraft servers. This plugin aims to provide a comprehensive, user-friendly, and powerful reward management solution.


## 技术架构 / Technical Architecture

### 系统要求 / System Requirements
- **Minecraft版本 / Minecraft Version**: 1.16及以上 / 1.16 and above
- **Java版本 / Java Version**: 17及以上 / 17 and above
- **服务器软件 / Server Software**: Bukkit、Spigot、Paper
- **依赖插件 / Dependencies**: Vault（可选，用于经济系统 / Optional, for economy system）

### 核心组件 / Core Components

#### 1. 配置管理系统 (ConfigManager) / Configuration Management System
负责管理插件的所有配置文件，包括主配置文件和奖励配置文件。支持热重载功能，允许管理员在不重启服务器的情况下更新配置。

Responsible for managing all plugin configuration files, including main configuration files and reward configuration files. Supports hot reload functionality, allowing administrators to update configurations without restarting the server.

#### 2. 奖励管理器 (RewardManager) / Reward Manager
核心组件之一，负责奖励计划的创建、编辑、删除和执行。支持多种奖励类型的统一管理。

One of the core components, responsible for creating, editing, deleting, and executing reward plans. Supports unified management of multiple reward types.

#### 3. 调度管理器 (ScheduleManager) / Schedule Manager
基于高精度时间计算的调度系统，支持多种时间模式的精确执行。采用异步处理机制，确保不影响服务器性能。

A scheduling system based on high-precision time calculations, supporting precise execution of multiple time modes. Uses asynchronous processing mechanisms to ensure server performance is not affected.

#### 4. 离线奖励管理器 (OfflineRewardManager) / Offline Reward Manager
专门处理离线玩家奖励的组件，支持三种处理模式：保留、延迟发放和跳过。

A component specifically for handling offline player rewards, supporting three processing modes: keep, delay, and skip.

#### 5. GUI管理系统 (GuiManager) / GUI Management System
提供直观的图形化用户界面，简化管理员的操作流程。采用事件驱动架构，确保界面响应的实时性。

Provides an intuitive graphical user interface, simplifying administrator operation workflows. Uses event-driven architecture to ensure real-time interface responsiveness.

### 数据存储 / Data Storage

#### 配置文件结构 / Configuration File Structure
```
plugins/TimedOnlineRewards/
├── config.yml          # 主配置文件 / Main configuration file
├── rewards.yml         # 奖励计划配置 / Reward plan configuration
├── playerdata/         # 玩家数据目录 / Player data directory
├── offline-rewards/    # 离线奖励存储 / Offline reward storage
└── backups/           # 自动备份目录 / Automatic backup directory
```

#### 数据持久化 / Data Persistence
插件采用YAML格式存储配置和数据，确保数据的可读性和可编辑性。支持自动备份机制，防止数据丢失。

The plugin uses YAML format to store configurations and data, ensuring data readability and editability. Supports automatic backup mechanisms to prevent data loss.

## 功能特性 / Features

### 时间管理系统 / Time Management System

#### 支持的时间模式 / Supported Time Modes
1. **每日模式 (Daily) / Daily Mode** - 每天在指定时间执行 / Execute at specified time every day
2. **每周模式 (Weekly) / Weekly Mode** - 每周在指定星期和时间执行 / Execute at specified day and time every week
3. **每月模式 (Monthly) / Monthly Mode** - 每月在指定日期和时间执行 / Execute at specified date and time every month
4. **特定时间模式 (Specific) / Specific Time Mode** - 在指定的具体时间点执行 / Execute at specified specific time point
5. **相对时间模式 (Relative) / Relative Time Mode** - 基于相对时间间隔执行 / Execute based on relative time intervals

#### 时间计算算法 / Time Calculation Algorithm
插件采用高精度的时间计算算法，支持跨时区处理，确保奖励发放的准确性。

The plugin uses high-precision time calculation algorithms, supports cross-timezone processing, ensuring accuracy of reward distribution.

### 奖励系统 / Reward System

#### 奖励类型 / Reward Types
1. **物品奖励 / Item Rewards** - 支持任意Minecraft物品，包括自定义NBT数据 / Supports any Minecraft items, including custom NBT data
2. **经济奖励 / Economy Rewards** - 通过Vault插件支持多种经济系统 / Supports multiple economy systems through Vault plugin
3. **经验奖励 / Experience Rewards** - 直接给予玩家经验值 / Directly gives players experience points
4. **命令奖励 / Command Rewards** - 执行自定义服务器命令 / Execute custom server commands

#### 奖励分发机制 / Reward Distribution Mechanism
- **即时分发 / Instant Distribution** - 对在线玩家立即发放奖励 / Immediately distribute rewards to online players
- **离线处理 / Offline Processing** - 根据配置处理离线玩家奖励 / Handle offline player rewards according to configuration
- **批量处理 / Batch Processing** - 支持同时向多个玩家发放奖励 / Supports distributing rewards to multiple players simultaneously

### 离线奖励处理 / Offline Reward Processing

#### 处理模式 / Processing Modes
1. **保留模式 (Keep) / Keep Mode**
   - 将离线奖励保存到文件 / Save offline rewards to files
   - 玩家上线时提示待领取奖励 / Notify players of pending rewards when they come online
   - 支持手动领取和批量领取 / Support manual claiming and batch claiming

2. **延迟模式 (Delay) / Delay Mode**
   - 玩家上线时自动发放所有离线奖励 / Automatically distribute all offline rewards when players come online
   - 提供发放进度反馈 / Provide distribution progress feedback
   - 支持发放失败重试 / Support retry on distribution failure

3. **跳过模式 (Skip) / Skip Mode**
   - 直接跳过离线玩家 / Directly skip offline players
   - 不保存任何离线奖励记录 / Do not save any offline reward records
   - 适用于实时性要求高的场景 / Suitable for scenarios with high real-time requirements

### 权限系统 / Permission System

#### 权限节点设计 / Permission Node Design
插件采用细粒度的权限控制，支持以下权限节点：

The plugin uses fine-grained permission control, supporting the following permission nodes:

- `timedrewards.admin` - 管理员权限 / Administrator permission
- `timedrewards.create` - 创建奖励计划 / Create reward plans
- `timedrewards.edit` - 编辑奖励计划 / Edit reward plans
- `timedrewards.delete` - 删除奖励计划 / Delete reward plans
- `timedrewards.list` - 查看奖励计划 / View reward plans
- `timedrewards.offline` - 管理离线奖励 / Manage offline rewards

#### 权限继承 / Permission Inheritance
权限系统支持继承机制，管理员权限自动包含所有子权限。

The permission system supports inheritance mechanisms, administrator permissions automatically include all sub-permissions.

## 用户界面 / User Interface

### GUI设计理念 / GUI Design Philosophy
插件的图形用户界面遵循直观、易用的设计原则，采用Minecraft原生的箱子界面，确保与游戏风格的一致性。

The plugin's graphical user interface follows intuitive and user-friendly design principles, using Minecraft's native chest interface to ensure consistency with the game style.

### 界面层次结构 / Interface Hierarchy
1. **主界面 / Main Interface** - 显示所有奖励计划的概览 / Display overview of all reward plans
2. **创建界面 / Creation Interface** - 引导用户创建新的奖励计划 / Guide users to create new reward plans
3. **编辑界面 / Edit Interface** - 修改现有奖励计划的详细设置 / Modify detailed settings of existing reward plans
4. **时间设置界面 / Time Setting Interface** - 配置奖励的执行时间 / Configure reward execution time
5. **奖励设置界面 / Reward Setting Interface** - 配置奖励的具体内容 / Configure specific reward content

### 交互设计 / Interaction Design
- **左键点击 / Left Click** - 编辑或确认操作 / Edit or confirm operations
- **右键点击 / Right Click** - 切换状态或取消操作 / Toggle status or cancel operations
- **Shift+右键 / Shift+Right Click** - 删除操作 / Delete operations
- **聊天输入 / Chat Input** - 文本输入支持 / Text input support

## 命令系统 / Command System

### 命令设计原则 / Command Design Principles
插件的命令系统遵循简洁、一致的设计原则，所有命令都以 `/tr` 为主命令，通过子命令实现不同功能。

The plugin's command system follows concise and consistent design principles, with all commands using `/tr` as the main command and implementing different functions through subcommands.

### 命令分类 / Command Categories
1. **管理命令 / Management Commands** - 用于插件管理和配置 / For plugin management and configuration
2. **奖励命令 / Reward Commands** - 用于奖励计划的操作 / For reward plan operations
3. **离线命令 / Offline Commands** - 用于离线奖励的处理 / For offline reward processing
4. **信息命令 / Information Commands** - 用于查看插件信息 / For viewing plugin information

### Tab补全支持 / Tab Completion Support
所有命令都支持Tab键自动补全，提高用户体验。

All commands support Tab key auto-completion, improving user experience.

## 配置系统 / Configuration System

### 配置文件结构 / Configuration File Structure
插件采用分层配置结构，将不同类型的配置分离到不同文件中，提高可维护性。

The plugin uses a layered configuration structure, separating different types of configurations into different files to improve maintainability.

### 配置验证 / Configuration Validation
插件在启动时会验证配置文件的完整性和正确性，对于错误的配置会给出明确的错误提示。

The plugin validates the integrity and correctness of configuration files at startup, providing clear error messages for incorrect configurations.

### 热重载支持 / Hot Reload Support
支持在不重启服务器的情况下重新加载配置，方便管理员进行调试和优化。

Supports reloading configurations without restarting the server, making it convenient for administrators to debug and optimize.

## 性能优化 / Performance Optimization

### 异步处理 / Asynchronous Processing
所有耗时操作都采用异步处理机制，避免阻塞主线程，确保服务器性能。

All time-consuming operations use asynchronous processing mechanisms to avoid blocking the main thread and ensure server performance.

### 内存管理 / Memory Management
采用高效的数据结构和缓存机制，最小化内存占用。

Uses efficient data structures and caching mechanisms to minimize memory usage.

### 数据库优化 / Database Optimization
虽然使用文件存储，但采用了优化的读写策略，减少I/O操作的频率。

Although using file storage, optimized read/write strategies are employed to reduce the frequency of I/O operations.

## 扩展性 / Extensibility

### 插件API / Plugin API
插件提供了丰富的API接口，允许其他插件进行集成和扩展。

The plugin provides rich API interfaces, allowing other plugins to integrate and extend functionality.

### 事件系统 / Event System
支持自定义事件，允许其他插件监听和响应奖励相关的事件。

Supports custom events, allowing other plugins to listen and respond to reward-related events.

### 钩子支持 / Hook Support
支持与主流插件的钩子集成，如Vault、PlaceholderAPI等。

Supports hook integration with mainstream plugins such as Vault, PlaceholderAPI, etc.

## 安全性 / Security

### 权限验证 / Permission Verification
所有操作都经过严格的权限验证，防止未授权访问。

All operations undergo strict permission verification to prevent unauthorized access.

### 数据保护 / Data Protection
采用多重备份机制，确保数据安全。

Uses multiple backup mechanisms to ensure data security.

### 输入验证 / Input Validation
对所有用户输入进行严格验证，防止恶意输入。

Strictly validates all user inputs to prevent malicious input.

## 兼容性 / Compatibility

### 版本兼容 / Version Compatibility
插件支持Minecraft 1.16及以上版本，兼容主流的服务器软件。

The plugin supports Minecraft 1.16 and above, compatible with mainstream server software.

### 插件兼容 / Plugin Compatibility
与主流插件保持良好的兼容性，避免冲突。

Maintains good compatibility with mainstream plugins, avoiding conflicts.

### 跨平台支持 / Cross-Platform Support
支持Windows、Linux、macOS等主流操作系统。

Supports mainstream operating systems including Windows, Linux, macOS.

## 故障排除 / Troubleshooting

### 常见问题 / Common Issues
1. **插件无法加载 / Plugin Cannot Load** - 检查Java版本和服务器兼容性 / Check Java version and server compatibility
2. **GUI无响应 / GUI Not Responding** - 检查权限配置和事件监听器 / Check permission configuration and event listeners
3. **奖励未发放 / Rewards Not Distributed** - 检查时间配置和调度器状态 / Check time configuration and scheduler status
4. **配置文件错误 / Configuration File Error** - 检查YAML语法和配置项 / Check YAML syntax and configuration items

### 调试模式 / Debug Mode
插件提供调试模式，可以输出详细的运行日志，帮助定位问题。

The plugin provides debug mode, which can output detailed runtime logs to help locate issues.

### 日志系统 / Logging System
完善的日志系统记录所有重要操作，便于问题追踪。

A comprehensive logging system records all important operations for easy issue tracking.

## 最佳实践 / Best Practices

### 配置建议 / Configuration Recommendations
1. 合理设置奖励频率，避免过于频繁 / Set reasonable reward frequency, avoid being too frequent
2. 根据服务器规模调整离线奖励处理模式 / Adjust offline reward processing mode according to server scale
3. 定期备份配置文件和数据 / Regularly backup configuration files and data

### 性能建议 / Performance Recommendations
1. 避免在高峰时段执行大量奖励 / Avoid executing large amounts of rewards during peak hours
2. 合理配置奖励内容，避免过于复杂 / Configure reward content reasonably, avoid being too complex
3. 定期清理过期的离线奖励记录 / Regularly clean up expired offline reward records

### 安全建议 / Security Recommendations
1. 严格控制管理权限的分配 / Strictly control the allocation of administrative permissions
2. 定期检查配置文件的安全性 / Regularly check the security of configuration files
3. 监控插件的运行状态 / Monitor the plugin's running status

## 社区与支持 / Community and Support

### 开源社区 / Open Source Community
插件采用开源模式，欢迎社区贡献代码和建议。

The plugin adopts an open source model, welcoming community contributions of code and suggestions.

### 技术支持 / Technical Support
提供多种技术支持渠道，包括GitHub Issues、讨论区等。

Provides multiple technical support channels, including GitHub Issues, discussion forums, etc.

### 文档维护 / Documentation Maintenance
持续更新和完善文档，确保用户能够获得最新的使用指南。

Continuously updates and improves documentation to ensure users can get the latest usage guides.

## 未来发展 / Future Development

### 计划功能 / Planned Features
1. 数据库存储支持 / Database storage support
2. Web管理界面 / Web management interface
3. 更多奖励类型 / More reward types
4. 高级统计功能 / Advanced statistics functionality

### 技术升级 / Technical Upgrades
1. 支持更新的Minecraft版本 / Support newer Minecraft versions
2. 性能优化和改进 / Performance optimization and improvements
3. 用户体验提升 / User experience improvements

## API文档 / API Documentation

### 核心API / Core API

#### 获取插件实例 / Get Plugin Instance
```java
TimedOnlineRewards plugin = (TimedOnlineRewards) Bukkit.getPluginManager().getPlugin("TimedOnlineRewards");
```

#### 奖励管理 / Reward Management
```java
// 创建奖励计划 / Create reward plan
RewardPlan plan = new RewardPlan("plan_id", "Plan Name");
plugin.getRewardManager().addRewardPlan(plan);

// 发放奖励 / Distribute reward
plugin.getRewardManager().giveReward(player, plan);

// 获取奖励计划 / Get reward plan
RewardPlan plan = plugin.getRewardManager().getRewardPlan("plan_id");
```

#### 离线奖励管理 / Offline Reward Management
```java
// 存储离线奖励 / Store offline reward
plugin.getOfflineRewardManager().storeOfflineReward(playerUUID, playerName, plan);

// 检查离线奖励 / Check offline rewards
boolean hasRewards = plugin.getOfflineRewardManager().hasOfflineRewards(playerUUID);

// 处理离线奖励 / Process offline rewards
plugin.getOfflineRewardManager().processOfflineRewards(player);
```

### 事件API / Event API

#### 自定义事件 / Custom Events
```java
// 奖励发放事件 / Reward distribution event
public class RewardGiveEvent extends Event {
    private final Player player;
    private final RewardPlan plan;
    
    // 构造函数和方法 / Constructor and methods
}

// 监听事件 / Listen to events
@EventHandler
public void onRewardGive(RewardGiveEvent event) {
    // 处理事件 / Handle event
}
```

---

*本百科文档持续更新中，如有疑问或建议，欢迎通过GitHub Issues反馈。*


*This encyclopedia document is continuously updated. If you have any questions or suggestions, please feel free to provide feedback through GitHub Issues.*
