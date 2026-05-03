# Skilful Skill

中文 | [English](README.md)

Skilful Skill 是一个用于整理、维护和分发多种 AI skills 的项目。它面向 AI agent、开发者和自动化工作流，目标是让 skills 更容易被发现、理解、复用和扩展。

## 项目目标

- 收集不同用途的 skills，例如开发辅助、代码审查、调试、文档处理、数据分析和自动化任务。
- 用清晰、稳定的结构描述每个 skill 的用途、触发场景、输入输出和注意事项。
- 提供对 AI 友好的说明，让 agent 能快速判断何时使用某个 skill，以及如何安全地执行它。
- 保持内容简洁、可维护，方便后续逐步扩展。

## 对 AI 友好的约定

- 每个 skill 应说明适用场景、限制条件和预期结果。
- 示例应尽量具体，避免只写抽象描述。
- 文件命名和目录结构应保持稳定，方便 agent 检索。
- 重要行为应显式写出，减少隐含假设。

## Skills

- [`mvp-creator`](skills/mvp-creator/SKILL.md)：用于规划、初始化和扩展 TypeScript MVP 项目，覆盖 Web frontend、Backend、Fullstack、Electron 和 React Native 工作流。

## 当前状态

这是项目的初始版本。后续会逐步添加更多 skill 目录、模板、示例和贡献说明。
