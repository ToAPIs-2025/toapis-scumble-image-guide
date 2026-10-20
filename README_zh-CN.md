# Scumble 的 ToAPIs 图片接入指南


<!-- TOAPIS-MODELS-20261020 -->
## 模型与价格更新 · 2026-10-20

新增可独立运行的31套图片请求模板、8套视频模板。当前26套图片与8套视频可匹配同Key精确价格；另5套图片缺价，默认阻止新付费调用。它们属于额外API脚本；项目原生Provider、UI、导入及完整出片的验收范围仍以下方原教程为准。

| 图片模型／实测档位 | 当前档位报价／张 | 历史案例金额／张 | 费用证据 |
|---|---:|---:|---|
| gpt-image-2(VIP)<br><sub>low</sub> | $0.0019/image | **$0.0019/image** | 计费日志，阶段未知 |
| gpt-image-2.5-flare-vip<br><sub>low</sub> | 当前Key暂未返回报价 | **$0.005272/image**<br><sub>Token计费；当前$/M未返回，本例金额不是固定单张价。</sub> | 任务回执已结算 |
| nano_banana<br><sub>1K</sub> | $0.012/image | **$0.012/image** | 计费日志，阶段未知 |
| gemini-nano-banana-2.1<br><sub>1K</sub> | $0.015/image | **$0.015/image** | 计费日志，阶段未知 |
| gpt-image-2<br><sub>1K</sub> | $0.015/image | **$0.015/image** | 计费日志，阶段未知 |
| gemini-nano-banana-2.1-vip<br><sub>1K</sub> | $0.02/image | **$0.02/image** | 计费日志，阶段未知 |
| qwen-image-3.0<br><sub>1K</sub> | 当前Key暂未返回报价 | **$0.021/image** | 计费日志，阶段未知 |
| gpt-image-2.5-flare<br><sub>high</sub> | $0.0225/image | **$0.0225/image** | 计费日志，阶段未知 |
| gpt-image-2.5-sunburst<br><sub>high</sub> | $0.0225/image | **$0.0225/image** | 计费日志，阶段未知 |
| flux-2-pro<br><sub>1K</sub> | $0.025/image | **$0.025/image** | 计费日志，阶段未知 |
| doubao-seedream-5-0-pro<br><sub>1K</sub> | $0.042857/image | **$0.042856/image** | 计费日志，阶段未知 |

| 视频模型 | 档位／输入 | 本例消费 | 文件时长 | 本例每秒金额（升序） |
|---|---|---:|---:|---|
| MiniMax-H3-Max-Turbo | 5s / 480P / 文生视频 | $0.125/clip | 5.18s | **$0.024131/s**<br><sub>pricing底层费率：$0.025/s</sub> |
| seedance-2-mini | 4s / 480p / 首帧 | $0.13338/clip | 4.04s | **$0.033015/s**<br><sub>pricing底层费率：$3.285714/M total tokens</sub> |
| seedance-2-fast | 4s / 480p / 文生视频 | $0.214568/clip | 4.04s | **$0.053111/s**<br><sub>pricing底层费率：$5.285714/M total tokens</sub> |
| kling-v3 | 5s / 720p / std / 文生视频 | $0.3/clip | 5.04s | **$0.059524/s**<br><sub>pricing底层费率：$0.06/s</sub> |
| MiniMax-H3 | 5s / 768p / 文生视频 | $0.32/clip | 5.17s | **$0.061896/s**<br><sub>pricing底层费率：$0.064/s</sub> |
| seedance-2 | 4s / 480p / 首帧 | $0.26676/clip | 4.04s | **$0.06603/s**<br><sub>pricing底层费率：$6.571429/M total tokens</sub> |
| kling-3.0-turbo | 4s / 720p / 文生视频 | $0.32/clip | 4.04s | **$0.079208/s**<br><sub>pricing底层费率：$0.08/s</sub> |
| seedance-2-5 | 4s / 480p / 文生视频 | $0.3883/clip | 4.04s | **$0.096114/s**<br><sub>pricing底层费率：$10/M total tokens</sub> |

报价核对：2026-10-20。图片案例日期2026-10-17；视频案例日期2026-10-20。表格按本例金额／秒金额排序，质量、分辨率和输入不同，不是同配置质量排名。图片日志的阶段未知，不能当作单任务最终净结算；当前报价与历史金额分别显示。视频金额均由billing=settled确认，$/s按实际文件时长折算，任务处理耗时不参与计算。Token模型不是固定每秒价，底层$/M只作小字补充。

gpt-image-2(VIP)通用价格为$0.0019/image起；本例low/1K为$0.0019/image。新脚本有31套历史成功图片请求模板、8套视频模板；当前26套图片与8套视频可匹配价格，另5套图片因当前Key缺价而默认阻止新付费调用。

[本仓库多模型脚本](toapis-models/README_zh-CN.md) · [完整价表](PRICING_zh-CN.md) · [原图／视频及费用证据](https://github.com/ToAPIs-2025/toapis-quickstart/tree/main/tutorials/model-support-2026-10-20)

下方保留原项目历史案例、消费及集成说明；历史金额不改成今天的新报价。

<!-- /TOAPIS-MODELS-20261020 -->

[English](README.md) · [Scumble 原项目](https://github.com/DenRakEiw/scumble) · [图片验收清单](ACCEPTANCE_zh-CN.md) · [模型价格](PRICING_zh-CN.md) · [实际消费](COSTS_zh-CN.md)

这是由 **ToAPIs 独立维护的图片 Provider 接入指南**，提供四张真实生成/参考改图、原创输入和可复用 wrapper。Scumble 应用请从上游项目安装；本仓库提供教程与示例。

Scumble 作者已在 [原 Issue #5](https://github.com/DenRakEiw/scumble/issues/5#issuecomment-6217158456) 认可四次真实调用，并在 [recipe](https://github.com/DenRakEiw/scumble/blob/4e6c17e5fc6f2ddbc35d201edaee3a04ac40356d/recipes/gpt_image_2.json) 与 [Provider 文档](https://github.com/DenRakEiw/scumble/blob/4e6c17e5fc6f2ddbc35d201edaee3a04ac40356d/docs/RECIPES.md) 中记录标准/VIP 通道的实测范围并注明来源。该记录仅确认调用证据，不代表官方背书、赞助或已建立商务合作。

**Scumble 是图片编辑器，没有视频功能。** 后续支持按作者的图片验收清单推进。官方通道遮罩编辑由作者自行验收，现有四次调用未覆盖该项。

## 四张真实图片与消费

2026-10-13，基于上游固定 SHA `0d0be6b3e41f00e8621af14fe11597eaf258501f`，通过未修改的 `electron/main/providers/toapis.js` 完成上传 → 生成/参考改图 → 查询原任务 → 下载。四张输出均为 1024×1024 PNG。

![Scumble 的 ToAPIs 图片接入指南](screenshots/cn/01-cover.png)

| 案例 | 精确 API ID / 档位 | 后台确认消费 | 原图 |
|---|---|---:|---|
| 浅色棚拍 | `gpt-image-2-vip` / low / 1K | $0.0019 | [PNG](assets/vip-low-coral-bowl.png) |
| 深色棚拍，参考改图 | `gpt-image-2-vip` / low / 1K | $0.0019 | [PNG](assets/vip-low-dark-bowl.png) |
| 日照室内，参考改图 | `gpt-image-2-vip` / low / 1K | $0.0019 | [PNG](assets/vip-low-interior-bowl.png) |
| 标准棚拍 | `gpt-image-2` / 1K | $0.015 | [PNG](assets/standard-coral-bowl.png) |

合计 **4.14 积分=$0.0207**，来源为账号持有人确认的后台消费截图；原始 API 回执的 billing 为空。另有一次早期错误上下文配置的提交未返回任务 ID，受理与费用未知，未计入合计。[消费依据](COSTS_zh-CN.md) · [原创输入](cases/briefs.json) · [原图画廊](GALLERY.md)。

本历史实测中 **gpt-image-2(VIP) low/1K 为 $0.0019/image**；一般宣传口径为 $0.0019/image 起。不同模型和档位的效果不同。带日期的 ToAPIs 报价和消费由本指南维护，上游 Provider 文档保持中立。

## 运行 Provider 示例

Node 20+（实测 24.19.0）、Git。Electron 产品按上游说明安装；以下命令直接运行 Provider，不启动画布。默认不调用 API，只有 `--live` 显式发起付费请求。

```bash
git clone https://github.com/ToAPIs-2025/toapis-scumble-image-guide.git

git clone https://github.com/DenRakEiw/scumble.git scumble-upstream

git -C scumble-upstream checkout 0d0be6b3e41f00e8621af14fe11597eaf258501f

cd toapis-scumble-image-guide

cp .env.example .env

# Fill TOAPIS_API_KEY privately. Windows PowerShell: Copy-Item .env.example .env

node run_cases.cjs --upstream ../scumble-upstream

node ../scumble-upstream/tools/toapis_test.js

node run_cases.cjs --upstream ../scumble-upstream --key-file .env --live --case vip-low-coral-bowl

node run_cases.cjs --upstream ../scumble-upstream --key-file .env --live
```

深色/室内参考改图依赖 `vip-low-coral-bowl`。已有完成记录直接复用；已有提交记录却没有完成结果时停止，先查询原任务。代理按系统 CA/代理配置，保持 TLS 验证开启。

## 接口映射与验收边界

1. 使用 `ctx.key` 和 **`ctx.base`**（如 `https://toapis.cn`），不是 `ctx.settings`。
2. Standard 使用 `gpt-image-2`、不传 quality；VIP 使用 `gpt-image-2-vip`、`quality=low`、`resolution=1k`、`n=1`、`size=1:1`。
3. 参考图片通过 `POST /v1/uploads/images` 上传，把返回的 URL 放入 `reference_images`。
4. `POST /v1/images/generations` 提交，`GET /v1/images/generations/{id}` 查询同一任务，下载结果时不转发 API Key。
5. Wrapper 保存持久提交记录，每案例提交一次生成 POST，轮询间隔至少 8 秒，保存原始图片字节及 SHA-256。

两次参考改图属于整图指令编辑，不能视为 alpha mask 局部重绘验收。画布交互、选区回填、图层导出和遮罩编辑仍待验证。作者已记录标准/VIP 通道的上传、查询和输出尺寸证据；边界限制与完整画布往返需另行验收，详见[五项清单](ACCEPTANCE_zh-CN.md)。

## 作者归因与技术支持

尊重作者保持上游文档中立、不维护厂商价格比较的要求。ToAPIs 专属配置、带日期的费用和排障材料保留在本指南。图片 Provider 排障需要：Scumble 版本/SHA、recipe/通道、选区及 mask 尺寸、预期与实际输出尺寸、脱敏错误。凭证和账号信息通过私有支持渠道交换。

保留原作者推荐入口 `https://toapis.com/login?aff=vfR1`，归属及分成尚未核实；本指南不替换或宣称拥有该推荐码。

[原项目及固定版本](https://github.com/DenRakEiw/scumble/tree/0d0be6b3e41f00e8621af14fe11597eaf258501f) · [GPL-3.0](LICENSE) · [ToAPIs 模型页](https://go2v.toapis.com/1013_scumble_cheaper_gh_cn) · [可复用教程图](SCREENSHOT_GUIDE_zh-CN.md)
