# WeChat Pay JSAPI Skill

开箱即用的微信小程序 JSAPI 标准支付技能包，适用于任何需要接入微信支付的小程序项目。

支持 **Spring Boot / Node.js / PHP** 三种后端语言的完整支付代码，包含平台配置指引、统一下单、二次签名、前端调起支付、异步回调验签的全流程实现。

## 安装

在 WorkBuddy 中导入以下 .zip 文件即可安装：

```
技能包 → 导入 → 选择 wechat-payment.zip
```

或直接放入 `~/.workbuddy/skills/wechat-payment/` 目录。

## 适用场景

- 小程序会员/订阅付费（月卡、年卡）
- 课程/内容付费
- 虚拟道具购买
- 任何需要拉起微信支付密码框的场景

## 内容概览

| 模块 | 内容 |
|------|------|
| 平台配置 | AppID、商户号、API 密钥获取指南 |
| 支付流程 | code → openid → 统一下单 → 二次签名 → 调起支付 完整链路 |
| Java 代码 | `WechatPayUtil` 工具类 + Controller 接口（sign / unifiedOrder / buildPaymentParams / verifyCallback） |
| Node.js 代码 | `WechatPay` class + Express 路由 |
| PHP 代码 | `WechatPay` class + 接口示例 |
| 前端代码 | 微信小程序 `wx.requestPayment` 完整调用示例 |
| SQL | payment 表建表语句 |
| 参数对照 | `wx.requestPayment` 五参数与后端字段映射 |
| 错误排查 | 签名错误、金额无效、商户号未关联等常见问题 |
| 上线清单 | 域名白名单、HTTPS、密钥配置等发布前检查项 |

## 技术要点

- **支付 API**：`wx.requestPayment`（JSAPI 标准支付，非虚拟支付）
- **签名方式**：微信支付 APIv2 MD5 签名
- **签名字段名**：后端用 `packageStr`，前端映射为 `package`（避免 JS 保留字冲突）
- **code 有效期**：`wx.login()` 的 code 每次支付前重新获取，不可缓存

## 文件结构

```
wechat-payment/
└── SKILL.md    # 完整技能内容（配置、Java/Node.js/PHP 代码、前端代码、SQL、排查）
```

## License

MIT
