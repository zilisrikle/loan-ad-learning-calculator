# Ad Learning Calculator

[![GitHub Pages](https://img.shields.io/badge/GitHub%20Pages-live-002fa7?style=for-the-badge&logo=github)](https://zilisrikle.github.io/loan-ad-learning-calculator/)
[![License: MIT](https://img.shields.io/badge/License-MIT-111111?style=for-the-badge)](./LICENSE)
[![Static HTML](https://img.shields.io/badge/Static-HTML%20%2B%20CSS%20%2B%20JS-002fa7?style=for-the-badge)](./index.html)
[![No Build](https://img.shields.io/badge/Build-none-111111?style=for-the-badge)](./index.html)

Language: [English](#english) | [简体中文](#简体中文) | [繁體中文](#繁體中文)

Live demo: [https://zilisrikle.github.io/loan-ad-learning-calculator/](https://zilisrikle.github.io/loan-ad-learning-calculator/)

## English

### What It Is

Ad Learning Calculator is a lightweight static web tool for planning Meta and Google App Campaign budgets for loan-app user acquisition.

It estimates:

- CPM, CTR, CPC, CPI, and application-success CPA
- Impressions, clicks, installs, and successful loan applications
- Blended CPI and blended application CPA
- Learning-budget requirements by platform
- Whether each campaign/ad-set pool is too thin, close to learning, or sufficiently funded

The default values are illustrative Latin America cash-loan benchmark-style samples. They are not real account data and should be replaced with your own ad platform, MMP, and backend numbers.

### How To Use

1. Open the [live calculator](https://zilisrikle.github.io/loan-ad-learning-calculator/) or open `index.html` locally.
2. Set currency, test budget, monthly budget, and test days.
3. For each traffic pool, choose platform and operating system.
4. Enter budget, CPM, CTR, CPI, and application-success CPA.
5. Set the number of learning units:
   - Meta: number of Ad Sets.
   - Google: number of App Campaigns.
6. Review estimated impressions, clicks, installs, successful applications, blended CPA, and learning status.

### Core Formulas

```text
impressions = spend / CPM x 1000
clicks = impressions x CTR
CPC = spend / clicks
installs = spend / CPI
successful applications = spend / application-success CPA
install-to-application rate = successful applications / installs
```

### Learning Logic

Meta learning budget:

```text
Meta learning budget = application-success CPA x 50 x number of Ad Sets
```

The `50` event threshold reflects Meta's commonly cited learning-phase guidance for optimization events per ad set.

Google App Campaign learning budget:

```text
Google learning budget = application-success CPA x 10 x test days x number of Campaigns
```

Google's App Campaign best-practice guide says that for in-app action optimization, advertisers should pick an action completed by at least 10 different users per day in the campaign and set daily budget at least 10 times the target CPA.

### Android And iOS

Android and iOS should be treated as separate learning pools when split into separate campaigns or ad sets. If budget is limited, avoid splitting too early: start with the dominant operating system, keep the secondary operating system on a validation budget, then move budget only after application CPA and downstream quality are both acceptable.

### Official References

- Google Ads Help: [Best practices guide: Setting up your App campaigns](https://support.google.com/google-ads/answer/6167162?hl=en)
- Google Ads Help: [About App campaigns](https://support.google.com/google-ads/answer/6247380?hl=en)
- Meta Business Help Center: [About the learning phase](https://www.facebook.com/business/help/112167992830700)

Meta Help Center pages may require login or may be region/session restricted. If the page does not open, search Meta Business Help Center for `learning phase`.

### Recommended GitHub Badges And License

Recommended setup for this project:

- MIT License: best for a small public calculator because it is permissive and easy to reuse.
- GitHub Pages badge: shows the tool is live.
- Static HTML badge: makes it clear there is no backend.
- No Build badge: useful because users can inspect and run the project directly.

### Important Notes

- The calculator uses application-success CPA, not disbursement CPA.
- A low CPI does not guarantee good loan quality.
- For lending products, budget decisions should also check approval rate, contract rate, disbursement rate, repayment behavior, risk cost, and LTV.
- Do not send sensitive financial or personal data to ad platforms unless it is permitted by applicable law, platform policy, and your privacy framework.
- This tool is for planning only and does not replace legal, compliance, or financial review.

### Local Development

This is a static HTML app with no build step.

```bash
open index.html
```

---

## 简体中文

### 这是什么

Ad Learning Calculator 是一个轻量级静态网页工具，用来估算贷款 App 在 Meta 和 Google App Campaign 获客投放中的预算厚度、学习门槛和转化产出。

它可以估算：

- CPM、CTR、CPC、CPI、申请成功 CPA
- 曝光、点击、安装、申请成功数
- 综合 CPI 和综合申请 CPA
- 不同平台的学习所需预算
- 每个 Campaign / Ad Set 投放池是“偏薄”“接近”还是“可达标”

默认值是拉美现金贷市场的示例量级，只用于演示计算逻辑，不代表任何真实账户数据。正式使用时，请替换为广告后台、MMP 和后端业务数据。

### 如何使用

1. 打开[在线计算器](https://zilisrikle.github.io/loan-ad-learning-calculator/)，或本地打开 `index.html`。
2. 设置币种、测试预算、月预算和测试天数。
3. 为每个投放池选择平台和系统。
4. 输入预算、CPM、CTR、CPI、申请成功 CPA。
5. 设置学习单元数量：
   - Meta：Ad Set 数。
   - Google：App Campaign 数。
6. 查看预计曝光、点击、安装、申请成功、综合 CPA 和学习状态。

### 核心公式

```text
曝光 = 花费 / CPM x 1000
点击 = 曝光 x CTR
CPC = 花费 / 点击
安装 = 花费 / CPI
申请成功 = 花费 / 申请成功 CPA
安装到申请成功率 = 申请成功 / 安装
```

### 学习逻辑

Meta 学习预算：

```text
Meta 学习预算 = 申请成功 CPA x 50 x Ad Set 数
```

其中 `50` 是 Meta 学习阶段常见引用的单个 Ad Set 优化事件量门槛。

Google App Campaign 学习预算：

```text
Google 学习预算 = 申请成功 CPA x 10 x 测试天数 x Campaign 数
```

Google App Campaign 官方最佳实践建议：如果优化 App 内事件，应选择每个 Campaign 每天至少有 10 个不同用户完成的事件；同时日预算至少为目标 CPA 的 10 倍。

### Android 和 iOS

如果 Android 和 iOS 拆成不同 Campaign 或 Ad Set，就应视为不同学习池。预算有限时不要过早拆太细：优先保证主力系统拿到足够事件，另一个系统先用小预算验证，再根据申请 CPA 和后续质量转移预算。

### 官方参考

- Google Ads Help: [Best practices guide: Setting up your App campaigns](https://support.google.com/google-ads/answer/6167162?hl=en)
- Google Ads Help: [About App campaigns](https://support.google.com/google-ads/answer/6247380?hl=en)
- Meta Business Help Center: [About the learning phase](https://www.facebook.com/business/help/112167992830700)

Meta 帮助中心页面可能需要登录，或受地区/会话限制。如果打不开，可在 Meta Business Help Center 搜索 `learning phase`。

### 推荐的 GitHub 徽章和许可证

这个项目我建议使用：

- MIT License：适合公开的小工具，允许他人自由使用、修改和再发布，同时保留署名和免责声明。
- GitHub Pages 徽章：说明工具已经在线可用。
- Static HTML 徽章：说明没有后端服务。
- No Build 徽章：说明不需要构建流程，直接打开即可使用。

### 重要说明

- 这个计算器使用的是申请成功 CPA，不是放款成功 CPA。
- CPI 低不等于贷款质量好。
- 贷款产品投放还需要看批核率、签约率、放款率、还款表现、风险成本和 LTV。
- 不要向广告平台传递敏感金融或个人数据，除非符合当地法律、平台政策和隐私框架。
- 本工具只用于投放规划，不替代法律、合规或财务审查。

### 本地运行

这是一个静态 HTML 应用，不需要构建。

```bash
open index.html
```

---

## 繁體中文

### 這是什麼

Ad Learning Calculator 是一個輕量級靜態網頁工具，用來估算貸款 App 在 Meta 和 Google App Campaign 獲客投放中的預算厚度、學習門檻和轉化產出。

它可以估算：

- CPM、CTR、CPC、CPI、申請成功 CPA
- 曝光、點擊、安裝、申請成功數
- 綜合 CPI 和綜合申請 CPA
- 不同平台的學習所需預算
- 每個 Campaign / Ad Set 投放池是「偏薄」「接近」還是「可達標」

預設值是拉美現金貸市場的示例量級，只用於演示計算邏輯，不代表任何真實帳戶數據。正式使用時，請替換為廣告後台、MMP 和後端業務數據。

### 如何使用

1. 打開[線上計算器](https://zilisrikle.github.io/loan-ad-learning-calculator/)，或本地打開 `index.html`。
2. 設定幣種、測試預算、月預算和測試天數。
3. 為每個投放池選擇平台和系統。
4. 輸入預算、CPM、CTR、CPI、申請成功 CPA。
5. 設定學習單元數量：
   - Meta：Ad Set 數。
   - Google：App Campaign 數。
6. 查看預計曝光、點擊、安裝、申請成功、綜合 CPA 和學習狀態。

### 核心公式

```text
曝光 = 花費 / CPM x 1000
點擊 = 曝光 x CTR
CPC = 花費 / 點擊
安裝 = 花費 / CPI
申請成功 = 花費 / 申請成功 CPA
安裝到申請成功率 = 申請成功 / 安裝
```

### 學習邏輯

Meta 學習預算：

```text
Meta 學習預算 = 申請成功 CPA x 50 x Ad Set 數
```

其中 `50` 是 Meta 學習階段常見引用的單個 Ad Set 優化事件量門檻。

Google App Campaign 學習預算：

```text
Google 學習預算 = 申請成功 CPA x 10 x 測試天數 x Campaign 數
```

Google App Campaign 官方最佳實踐建議：如果優化 App 內事件，應選擇每個 Campaign 每天至少有 10 個不同用戶完成的事件；同時日預算至少為目標 CPA 的 10 倍。

### Android 和 iOS

如果 Android 和 iOS 拆成不同 Campaign 或 Ad Set，就應視為不同學習池。預算有限時不要過早拆太細：優先保證主力系統拿到足夠事件，另一個系統先用小預算驗證，再根據申請 CPA 和後續質量轉移預算。

### 官方參考

- Google Ads Help: [Best practices guide: Setting up your App campaigns](https://support.google.com/google-ads/answer/6167162?hl=en)
- Google Ads Help: [About App campaigns](https://support.google.com/google-ads/answer/6247380?hl=en)
- Meta Business Help Center: [About the learning phase](https://www.facebook.com/business/help/112167992830700)

Meta 幫助中心頁面可能需要登入，或受地區/會話限制。如果打不開，可在 Meta Business Help Center 搜尋 `learning phase`。

### 推薦的 GitHub 徽章和授權

這個項目我建議使用：

- MIT License：適合公開的小工具，允許他人自由使用、修改和再發布，同時保留署名和免責聲明。
- GitHub Pages 徽章：說明工具已經線上可用。
- Static HTML 徽章：說明沒有後端服務。
- No Build 徽章：說明不需要構建流程，直接打開即可使用。

### 重要說明

- 這個計算器使用的是申請成功 CPA，不是放款成功 CPA。
- CPI 低不等於貸款質量好。
- 貸款產品投放還需要看批核率、簽約率、放款率、還款表現、風險成本和 LTV。
- 不要向廣告平台傳遞敏感金融或個人數據，除非符合當地法律、平台政策和私隱框架。
- 本工具只用於投放規劃，不替代法律、合規或財務審查。

### 本地運行

這是一個靜態 HTML 應用，不需要構建。

```bash
open index.html
```
