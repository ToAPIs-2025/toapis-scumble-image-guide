# 本指南的 ToAPIs 图片模型历史价格

报价日期：**2026-10-13**，来自本次测试 Key。费用由 ToAPIs 指南维护，不是上游 Provider 文档的一部分。新调用前用自己的 Key 查询 `GET /v1/pricing?model=...`，历史报价不锁定当前价格。

| 展示模型 / API ID | 实测档位 | 历史报价 | 已确认单张消费 | 调用次数 |
|---|---|---:|---:|---:|
| gpt-image-2(VIP) / `gpt-image-2-vip` | low / 1K / n=1 | $0.0019/image | $0.0019 | 3 |
| gpt-image-2 / `gpt-image-2` | 1K / n=1，不传 quality | $0.015/image | $0.015 | 1 |

gpt-image-2(VIP) **$0.0019/image 起**，本例 low/1K 为 **$0.0019/image**。模型、通道和画质参数不同，不能由价格推断效果相同。报价已包含返回的账户折扣。

四次图片调用合计 **$0.0207**。API billing 为空，消费来源为账号持有人确认的后台截图；另一次早期受理/费用未知的提交未计入。Scumble 仅处理图片，本页不列视频价格或视频验收。

[逐项消费](COSTS_zh-CN.md) · [原始历史报价](evidence/pricing.json) · [图片验收清单](ACCEPTANCE_zh-CN.md) · [ToAPIs 当前价表](https://toapis.com/en/pricing) · [报价 API](https://docs.toapis.com/docs/en/api-reference/account/pricing) · [English](PRICING.md)
