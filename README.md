# Ad Learning Calculator

A lightweight web calculator for planning Meta and Google App Campaign budgets for loan-app user acquisition.

The calculator estimates:

- CPM, CTR, CPC, CPI, and application-success CPA
- Impressions, clicks, installs, and successful loan applications
- Blended CPI and blended application CPA
- Learning-budget requirements by platform
- Whether each campaign/ad-set pool is likely too thin, close to learning, or sufficiently funded

The default numbers are **illustrative Latin America cash-loan benchmark-style sample values**. They are not real account data and should be replaced with your own platform, MMP, and backend numbers before making media-buying decisions.

## How To Use

Open `index.html` in a browser.

1. Set the currency, test budget, monthly budget, and test days.
2. For each traffic pool, choose platform and operating system.
3. Enter budget, CPM, CTR, CPI, and application-success CPA.
4. Set the number of learning units:
   - Meta: number of Ad Sets.
   - Google: number of App Campaigns.
5. Read the outputs:
   - CPC = spend / clicks
   - Installs = spend / CPI
   - Successful applications = spend / application-success CPA
   - Install-to-application rate = successful applications / installs
   - Learning required budget = platform-specific learning requirement

The status badge is calculated from allocated budget divided by learning-required budget:

- `可达标`: allocated budget is at least 100% of estimated learning budget.
- `接近`: allocated budget is 65%-99% of estimated learning budget.
- `偏薄`: allocated budget is below 65% of estimated learning budget.

## Core Logic

### Media Funnel

The calculator uses simple planning math:

```text
impressions = spend / CPM x 1000
clicks = impressions x CTR
CPC = spend / clicks
installs = spend / CPI
successful applications = spend / application CPA
install-to-application rate = successful applications / installs
```

This is a planning model, not attribution truth. In production, final performance should be reconciled across ad platforms, MMP, SKAN where applicable, and backend loan-status data.

### Meta Learning Budget

Meta campaigns learn at the optimization-unit level. In practice, loan-app campaigns should avoid splitting budget across too many Ad Sets when optimizing for a low-frequency event such as a successful application.

This calculator estimates Meta learning budget as:

```text
Meta learning budget = application CPA x 50 x number of Ad Sets
```

The `50` event threshold reflects Meta's commonly cited learning-phase guidance for optimization events per ad set.

### Google App Campaign Learning Budget

Google's App Campaign best-practice guide says that for in-app action optimization, advertisers should pick an action completed by at least 10 different users per day in the campaign and set daily budget at least 10 times the target CPA.

This calculator estimates Google learning budget as:

```text
Google learning budget = application CPA x 10 x test days x number of Campaigns
```

For a 14-day test:

```text
Google learning budget = application CPA x 140 x number of Campaigns
```

## Android And iOS

Android and iOS should be treated as separate learning pools when they are split into separate campaigns or ad sets.

If the budget is limited, avoid splitting too early:

- Start with the dominant operating system if historical volume is clear.
- Keep the secondary operating system on a smaller validation budget.
- Move budget only after application CPA and downstream quality are both acceptable.

## Official References

- Google Ads Help: [Best practices guide: Setting up your App campaigns](https://support.google.com/google-ads/answer/6167162?hl=en)
- Google Ads Help: [About App campaigns](https://support.google.com/google-ads/answer/6247380?hl=en)
- Meta Business Help Center: [About the learning phase](https://www.facebook.com/business/help/112167992830700)

Note: Meta Help Center pages may require login or may be region/session restricted. If the page does not open, search the Meta Business Help Center for “learning phase”.

## Important Notes

- The calculator uses application-success CPA, not disbursement CPA.
- A low CPI does not guarantee good loan quality.
- For lending products, budget decisions should also check approval rate, contract rate, disbursement rate, repayment behavior, risk cost, and LTV.
- Do not send sensitive financial or personal data to ad platforms unless it is permitted by applicable law, platform policy, and your privacy framework.
- This tool is for planning only and does not replace legal, compliance, or financial review.

## Local Development

This is a static HTML app with no build step.

```bash
open index.html
```

For GitHub Pages, publish the repository root and set Pages to deploy from the `main` branch.
