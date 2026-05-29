# deepstock.cn

`deepstock.cn` 是一个面向 A 股场景的交易终端 demo。它基于原生 C++20、Qt6 与嵌入式 Python 构建，目标是验证桌面端专业交易终端与手机端智能体助手两种产品形态。

## 核心方向

- 桌面端：A 股行情、自选、盘口、委托、持仓、资金、组合、研究与风控。
- 手机端：智能体先完成扫描、解释、仓位和风险计算，用户再确认委托草稿。
- 投顾端：AI 风格投顾与真人认证老师共同构成内容型交易社区，支持短评、聊天和直播课程。
- 数据侧：保留 AkShare、Yahoo Finance、研究和量化脚本基础，后续可继续接入 A 股数据源与券商接口。

## 当前 Demo

| 模块 | 说明 |
| --- | --- |
| A 股交易工作台 | 默认标的、自选股、交易所、人民币显示和交易页文案已面向 A 股 demo 调整 |
| 中文化界面 | 导航、账户、批量下单、订单面板、持仓/资产/资金等主要交易界面已中文化 |
| deepstock 品牌 | 构建目标、应用标题、打包元信息与安装器组件已改为 deepstock |
| 手机端原型 | `mobile-demo/index.html` 展示 A 股智能交易助理与智能投顾广场页面 |
| 智能投顾广场 | 包含投资大师风格 AI 智能体、真人老师频道示例、付费短评、粉丝聊天、消息版面和视频直播间 |

## 手机端预览

```bash
cd mobile-demo
python3 -m http.server 4177
```

访问：

```text
http://127.0.0.1:4177/
```

## 桌面端构建示例

```bash
cmake -S fincept-qt -B fincept-qt/build-deepstock \
  -DCMAKE_PREFIX_PATH="$HOME/Qt/6.8.3/macos" \
  -DFINCEPT_ALLOW_QT_DRIFT=ON \
  -DFINCEPT_BUILD_TESTS=OFF

cmake --build fincept-qt/build-deepstock --target deepstock --parallel 4
```

运行：

```bash
open fincept-qt/build-deepstock/deepstock.app
```

## 重要说明

本项目目前用于 demo 和产品验证，不构成投资建议。真实交易产品化前，需要补齐券商授权、风控、审计、合规和用户二次确认链路。

智能投顾广场中的“巴菲特风格”“段永平风格”“索罗斯风格”等 AI 智能体仅代表策略框架和教育型解释，不代表真人本人。真人老师频道正式上线前，需要完成身份认证、姓名/肖像授权、投顾资质审核、内容审核、风险揭示和付费留痕。
