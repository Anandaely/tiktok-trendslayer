---
name: tiktok-trend-slayer
description: TikTok 选品猎手 - 自动监控 TikTok 商品榜与达人榜，利用 AI 挖掘高增长爆款，生成选品及达人撮合策略。当用户需要 TikTok 选品分析、爆款挖掘、达人匹配、趋势监控时使用此技能。
---

# TikTok Trend Slayer — TikTok Shop Influencer Analytics
Fetch TikTok influencer data via EchoTik API, filter high-engagement creators, and generate reports.
是一款面向 TikTok 电商卖家的智能选品工具。通过自动监控 TikTok Shop 商品榜、EchoTik 数据接口，实时识别高增长爆款商品，并利用 AI 分析爆款视频的钩子（Hook）与结构，自动匹配合适的中腰部达人（KOC），帮助卖家快速发现蓝海品类与合作机会。在 TikTok 电商领域，领先 48 小时发现爆款意味着 10 倍的利润空间。传统的选品工具只告诉你“什么火了”，而 TikTok Trend Slayer 告诉你“什么即将火”以及“为什么火”。将原本需要 3 小时的手动刷榜和分析，缩短为 1 分钟的“选品简报”。


## 核心功能概述 （Core Features Overview）

1. **黑马发现算法｜Dark Horse Discovery Algorithm**
调用 TikTok Affiliate API 和 EchoTik 接口获取商品/达人数据，实时监测 GMV 增长斜率。当某个商品在 24 小时内销量增速翻倍，且挂车达人数仍处于低位时，系统将自动触发“蓝海预警”。

Leverages TikTok Affiliate and EchoTik APIs to fetch real-time product and creator data, monitoring GMV growth gradients. When a product's sales growth doubles within 24 hours while the number of linked creators remains low, the system automatically triggers a "Blue Ocean Alert."
2. **视频病毒基因拆解 | Viral Video Gene Dissection**
识别 GMV 增速前 5% 商品及 24h 销量翻倍的黑马 SKU，AI 自动解析高转化视频的“黄金 3 秒”Hook、脚本结构与 BGM 情绪，为您提供 1:1 可复刻的爆款脚本公式。

Identifies the top 5% of products by GMV growth and "dark horse" SKUs with doubled sales. AI automatically analyzes the "Golden 3-Second" hooks, script structures, and BGM vibes of high-conversion videos, providing you with 1:1 replicable viral script formulas.

3. **达人撮合雷达 | Creator Matchmaking Radar**
基于商品画像自动筛选最具带货潜力的高转化 KOC，拒绝只看粉丝数，只看实战转化率，自动制定达人合作方案。

Automatically filters KOCs with the highest sales potential based on product profiling. Moving beyond vanity metrics like follower counts, it focuses solely on actual conversion rates to generate automated creator collaboration plans.

4. **自动选品报告 | Automated Product Selection Report**
支持自动生成目标品类/商品、当前销量、预估利润、竞争程度及推荐话术等的完整报告。

Supports the automatic generation of comprehensive reports covering target categories/products, current sales volume, estimated profit margins, competition levels, and recommended sales pitches.

## 指令示例 (Sample Prompts)

1. **全局搜索 | Global Search**
@TikTok-Trend-Slayer 帮我找出过去 48 小时内在美国区 3C 类目下增长最快的 3 个黑马商品。

@TikTok-Trend-Slayer, find the top 3 "dark horse" products in the U.S. 3C category that have shown the fastest growth over the past 48 hours.

2.**深度拆解 | Deep Dive / Breakdown**
针对这款 [商品名]，分析其最近 5 个爆火视频的脚本结构，并给我 3 个适合拍摄的 Hook。

For this [Product Name], analyze the script structures of its 5 most recent viral videos and provide me with 3 filming-ready hooks.

3. **达人匹配 | Creator Matching**
我想推一款磁吸充电宝，请列出 5 位近期带过同类产品且互动率超过 5% 的中小达人。

I want to promote a magnetic power bank. Please list 5 micro-influencers who have recently promoted similar products and maintain an engagement rate of over 5%.


## 环境要求

- `curl` - HTTP 请求工具
- `jq` - JSON 处理工具
- 环境变量:
  - `TIKTOK_SHOP_API_KEY` - TikTok Shop API 密钥
  - `ECHOTIK_TOKEN` - EchoTik API Token

## API 申请

| API | 申请地址 | 获取密钥 |
|-----|----------|----------|
| TikTok Shop Partner | https://seller.tiktokglobalshop.com/ | App Key + App Secret |
| EchoTik | https://www.echotik.com/ | API Token |

## 使用方法

### 执行选品分析
```bash
# 分析指定品类
~/.openclaw/workspace/skills/tiktok-trend-slayer/scripts/tiktok_slayer.sh --category beauty

# 分析所有重点品类（3C、美妆、家居）
~/.openclaw/workspace/skills/tiktok-trend-slayer/scripts/tiktok_slayer.sh --all

# 生成 Markdown 报告
~/.openclaw/workspace/skills/tiktok-trend-slayer/scripts/tiktok_slayer.sh --category beauty --format md
```

### 设置定时监控

```bash
# 添加到 crontab，每天 8:00 执行
0 8 * * * cd ~/.qclaw/workspace/skills/tiktok-trend-slayer && ./scripts/tiktok_slayer.sh --all >> logs/cron.log 2>&1
```


## 输出格式

报告包含以下字段：
- `product_name` - 商品名称
- `product_image` - 商品主图 URL
- `current_sales` - 当前销量
- `gmv_growth` - GMV 增长率
- `estimated_profit` - 预估利润
- `recommended_creators` - 推荐达人列表
- `viral_keywords` - 爆火关键词
- `video_hooks` - 视频 Hook 分析

## 达人匹配标准

- 粉丝量：1K-100K（中小达人/KOC）
- 互动率：> 5%
- 品类垂直度：与商品品类匹配

## 参考文档

- [API 文档](references/api_docs.md) - TikTok Shop API 和 EchoTik API 详细说明
- [输出示例](references/output_example.md) - 报告格式示例
