# env-change-guard

一个给 OpenClaw 新手使用的环境变量防呆技能。

## 这个技能做什么

`env-change-guard` 用来降低代理修改环境变量、系统变量时出错的概率，特别适合这些场景：

- 修改 `PATH`
- 修改系统变量
- 修改用户环境变量
- 设置 `JAVA_HOME`、`ANDROID_SDK_ROOT`、`ANDROID_HOME` 等变量
- 配置 Python、Node、Java、ADB、Android SDK、OpenClaw 等工具的环境

这个技能的核心不是“帮你随便改”，而是要求代理按更稳妥的方式执行：

- 修改前先解释要做什么
- 先读取当前值
- 明确风险等级
- 尽量只做最小改动
- 改完写日志
- 告诉用户怎么验证
- 告诉用户怎么回滚

## 为什么要做这个技能

环境变量修改看起来只是小操作，但它其实是新手最容易改乱系统配置的地方之一。

常见问题包括：

- 不知道自己改了什么
- 直接把 `PATH` 覆盖掉
- 分不清用户变量和系统变量
- 改完为什么命令还是不生效也不知道
- 出问题以后不会回滚

这个技能的目的，就是让这类操作变得：

- 更容易理解
- 更容易追踪
- 更容易回退

## 默认日志位置

默认把环境变量变更记录到：

`logs/env-change-log.md`

## 适合谁

- OpenClaw 新手
- 不熟悉系统配置的用户
- 需要配置 Python / Node / Java / Android SDK / ADB 的人
- 想清理混乱 `PATH` 的人
- 希望配置变更可追溯、可回滚的人

## 文件结构

- `SKILL.md` —— 技能主说明
- `references/log-entry-template.md` —— 日志模板
- `references/risk-guide.md` —— 风险等级说明
- `references/verification-and-rollback.md` —— 验证与回滚说明
- `references/windows-notes.md` —— Windows 使用说明

## 打包文件

技能打包文件位置：

`../../dist/env-change-guard.skill`

## 说明

这个 README 是给人看的。

技能实际执行逻辑以 `SKILL.md` 为准。
