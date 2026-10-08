# route-rule

适用于 Clash / Mihomo 的分流规则片段。规则来自 [blackmatrix7/ios_rule_script](https://github.com/blackmatrix7/ios_rule_script/tree/master/rule/Clash)，通过 HTTP 规则源每 24 小时更新，并使用本地缓存。

## 使用

1. 获取 [routing.yaml](./routing.yaml)，把其中的 `rule-providers` 和 `rules` 合并到你的现有配置；同名顶层字段各保留一份。
2. 将规则中的 `PROXY` 替换为你现有代理策略组的名称。该策略组和节点由你在本地配置。
3. 使用规则模式，保持下列规则顺序，让末尾的 `MATCH` 负责兜底。

`routing.yaml` 包含 27 个规则源和 28 条分流入口。它需要与现有代理配置合并后使用，单独导入无法提供代理连接。

| 分流 | 服务 |
| --- | --- |
| 拒绝 | 广告 |
| 直连 | 微信、微信输入法、抖音、局域网、Apple、中国大陆域名与 IPv4 |
| PROXY | Claude、Anthropic、Binance、PayPal、GitHub、YouTube、Twitter、Telegram、Google、OneDrive、TikTok、OpenAI、Gemini、Copilot、Speedtest、Netflix，以及未命中其他规则的连接 |

Apple、广告与中国大陆规则分别使用域名文件及补充规则文件，覆盖各来源的规则类型。

## 发布内容

本仓库只发布规则片段和使用说明。节点、节点订阅、认证凭据、证书及个人专用例外规则均未包含。文件中的远程链接仅用于下载公开的 blackmatrix7 分流规则。

上游规则内容和使用条款以 [blackmatrix7 原仓库](https://github.com/blackmatrix7/ios_rule_script)为准。
