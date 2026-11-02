# 本 fork 云端部署

本 fork 使用 GitHub Actions 执行分析，无需个人电脑持续开机；它不提供常驻 Web 服务。

- 工作流：`.github/workflows/00-daily-analysis.yml`。
- 定时：周一至周五北京时间 16:00、18:00，对应 cron `0 8,10 * * 1-5`（UTC）。平台调度可能延迟，程序仍按交易日规则过滤。
- 示例目标：国芯科技（688262），在未配置自选股时作为工作流默认值；可通过 Repository variable `STOCK_LIST` 覆盖。
- 模型：计划使用 OpenAI，用户自行在 Repository secret `OPENAI_API_KEY` 填写密钥；不得提交到仓库或聊天。模型与可用 API 额度需要另行配置。
- 通知：渠道待选择，填写对应 Secrets 后再验证推送。
- 验收：启用工作流不代表分析通过；需在密钥、模型、自选股配置完成后手动运行，核对任务步骤、报告和通知结果。
- 回滚：恢复原 cron `0 10 * * 1-5`；在 Variables 修改或清除 `STOCK_LIST`。可在 Actions 的 Workflow options 中停用工作流。

此文档仅记录用户中文个人部署配置，不改变上游通用行为，因此未同步英文部署文档。
