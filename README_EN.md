# WeChat Pay JSAPI Skill

A plug-and-play WeChat Mini Program payment skill package supporting standard JSAPI payment. Works with any Mini Program that needs WeChat Pay integration.

Provides complete payment code for **Spring Boot / Node.js / PHP** backends, covering the full flow: platform configuration, unified ordering, secondary signing, frontend payment invocation, and async callback verification.

## Installation

Import the .zip file in WorkBuddy:

```
Skills → Import → Select wechat-payment.zip
```

Or place it directly under `~/.workbuddy/skills/wechat-payment/`.

## Use Cases

- Mini Program membership/subscription payments (monthly, yearly)
- Course/content purchases
- Virtual item purchases
- Any scenario requiring the WeChat Pay password dialog

## Contents

| Section | Description |
|---------|-------------|
| Platform Config | Where to get AppID, Merchant ID, API key |
| Payment Flow | code → openid → unifiedOrder → secondary signing → payment invocation |
| Java Code | `WechatPayUtil` class + Controller (sign / unifiedOrder / buildPaymentParams / verifyCallback) |
| Node.js Code | `WechatPay` class + Express route |
| PHP Code | `WechatPay` class + integration example |
| Frontend Code | Complete `wx.requestPayment` invocation example for Mini Programs |
| SQL | `payment` table schema |
| Parameter Mapping | `wx.requestPayment` five-parameter to backend field mapping |
| Troubleshooting | Sign errors, invalid amounts, unlinked merchant accounts, etc. |
| Go-Live Checklist | Domain whitelist, HTTPS, API key setup, and other pre-launch checks |

## Technical Notes

- **Payment API**: `wx.requestPayment` (standard JSAPI payment, NOT virtual payment)
- **Signing Method**: WeChat Pay APIv2 MD5 signature
- **Field Naming**: Backend uses `packageStr`; frontend maps to `package` (avoiding JS reserved word conflict)
- **Code Validity**: `wx.login()` code must be freshly obtained before each payment; do not cache

## File Structure

```
wechat-payment/
└── SKILL.md    # Full skill content (config, Java/Node.js/PHP code, frontend code, SQL, troubleshooting)
```

## License

MIT
