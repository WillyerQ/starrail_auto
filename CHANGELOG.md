# Changelog

## v1.0.0 (2026-05-09)

### ✨ 功能

- **体力计算**：输入当前体力值，自动计算到达阈值（默认160）的精确时间
- **WOL 网络唤醒**：到点自动发送魔术包唤醒 Windows PC
- **SSH + 计划任务执行**：通过 `schtasks` 在用户桌面会话中执行三月七助手，**支持保留锁屏**
- **任务可配置**：WebUI 选择要执行的任务（日常/周常/模拟宇宙等）
- **自动关机**：任务完成后自动关闭电脑，支持 WebUI 开关
- **体力帮助图片**：`/体力帮助` 生成指令列表图片，支持 `backgrounds/` 自定义背景
- **自动更新检查**：运行三月七助手前自动检查并运行更新器
- **报错日志报告**：任务失败时自动抓取日志，以 Markdown 格式发送报告
- **文件日志**：运行日志写入 `logs/` 目录，方便排查问题
- **计划任务执行**：通过 `schtasks /ru /rp` 以指定用户身份运行，无需设置自动登录

### 🔧 修复

- [#1] `metadata.yaml` name 含横杠导致加载失败 → 改为合法 Python 标识符
- [#2] Heredoc 写文件导致 `\n` 被展开为真换行，字符串语法错误 → 改用 Python 脚本写入
- [#3] 日志函数递归调用 `info_log()` 调自己 → 改为直接调 `logger.info()`
- [#4] `on_message` 方式注册命令不响应 → 改用 `@filter.command()` 装饰器注册
- [#5] 异步生成器用 `for` 而非 `async for` 遍历 → 改为 `async for`
- [#6] 日志句柄重复添加 → 改用模块级单例

### 🏗 项目

- 仓库从 `astrbot-plugin-starrail-auto` 重命名为 `starrail_auto`
- 完整的 `README.md` 文档
- `requirements.txt` 依赖声明
- `_conf_schema.json` WebUI 配置页面
- `backgrounds/` 自定义帮助背景文件夹
- `logs/` 日志文件夹
