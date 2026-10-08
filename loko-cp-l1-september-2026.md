# LOKO — CP L1 investigation (September 2026)

**Data refreshed:** 8 October 2026  
**Period:** 1–30 September 2026  
**Scope:** Ukraine, `group_name = 'LOKO'`  
**Sources:** `main.ng_delivery.fact_provider_weekly`, `main.ng_delivery.dim_order_campaign_delivery`, `main.ng_delivery.dim_campaign_delivery_v2`.

## Executive conclusion

LOKO's **CP L1 was negative by €957.28 (−1.03% of GMV)** in September. Demand incentives are deducted only afterwards, in CP L2. A separate finance field shows **€43.39 of Bolt menu-campaign cost share inside CP L1**; this is only 1.1% of the €3,887.82 CP L1 variable-cost base and therefore does not explain the loss.

The direct CP L1 bridge is:

| Metric | EUR |
|---|---:|
| GMV | 92,796.71 |
| Delivered orders | 5,269 |
| Reporting revenue | 2,930.54 |
| Total variable costs (inside CP L1) | (3,887.82) |
| **CP L1** | **(957.28)** |
| Demand incentives (deducted after CP L1) | (292.16) |
| **CP L2** | **(1,249.44)** |

So the immediate reason for negative CP L1 is a **€957.28 gap between reporting revenue and variable costs**. The source exposes **€3,787.45** as the residual `other variable costs` bucket after demand refunds / supply refunds / fraud. Its known part is **€43.39 Bolt menu-campaign cost share**, leaving **€3,744.06** not itemised by the source. The complete bridge is: €3,744.06 unitemised variable costs + €43.39 Bolt menu-campaign cost share + €277.71 supply refunds − €177.34 demand-refund credit = €3,887.82. LOKO has no invoiced courier cost, supply incentives or fraud in this period; zero courier cost does not mean zero CP L1 costs.

## Important distinction: campaign funding vs CP L1

- **Demand incentives are not a CP L1 cost** and lower CP L2. However, €43.39 of **Bolt menu-campaign cost share** is recorded in CP L1 variable costs.
- `campaign_spend_provider_eur` is the part funded by the provider; `campaign_spend_bolt_eur` is the part funded by Bolt.
- A `provider_campaign_*` objective name identifies the campaign framework, **not** its funding. The two spend columns are the funding source of record.

## Campaign and spend-objective audit

September campaign attribution contains **€7,185.47** total spend:

| Spend objective | Campaigns | Attributed orders | Bolt spend, € | Provider spend, € | Total, € |
|---|---:|---:|---:|---:|---:|
| `bolt_market_supplier` | 2 | 3,320 | 0.00 | 6,749.25 | 6,749.25 |
| `marketing_3rd_party_partnership` | 4 | 166 | 344.64 | 0.00 | 344.64 |
| `provider_campaign_marketing` | 1 | 10 | 42.28 | 0.00 | 42.28 |
| `other` | 3 | 11 | 36.92 | 0.00 | 36.92 |
| `marketing` | 2 | 2 | 12.38 | 0.00 | 12.38 |
| **Total** | **12** | **3,509** | **436.22** | **6,749.25** | **7,185.47** |

The premise that there is no investment is therefore not fully supported by the campaign data: **€6,749.25 is provider-funded**, principally via the 3P Pricelist campaign. Provider-funded spend is not a Bolt CP L1 cost. Only €43.39 of Bolt menu-campaign cost share is recorded in CP L1; the remaining €3,744.06 unitemised variable costs are the main driver of the loss.

## Exact campaigns included

| Campaign | Spend objective | Attributed orders | Bolt, € | Provider, € | Total, € |
|---|---|---:|---:|---:|---:|
| UA, (CW), 2026W35, Provider Targeting, 3P Pricelist campaign | `bolt_market_supplier` | 3,295 | 0.00 | 6,699.31 | 6,699.31 |
| UA, (CW), 2026W36, Provider Targeting, FUIB-New Visa Bank | `marketing_3rd_party_partnership` | 82 | 244.04 | 0.00 | 244.04 |
| UA, (CW), 2026W29, Provider Targeting, Visa campaign (excl. providers with specific trait) - Abank | `marketing_3rd_party_partnership` | 55 | 64.37 | 0.00 | 64.37 |
| UA, (CW), 2025W44, Bolt Market, PL all_users price type, Flat, Kopikya price list | `bolt_market_supplier` | 25 | 0.00 | 49.95 | 49.95 |
| UA, NovaPost loyalty program, New Users, -40% Menu (max 300 UAH) x 15000 | `provider_campaign_marketing` | 10 | 42.28 | 0.00 | 42.28 |
| UA, (CW), 2026W29, Provider Targeting, Ukrsibbank | `marketing_3rd_party_partnership` | 29 | 36.23 | 0.00 | 36.23 |
| UA, SM TikTok, BOLTFOOD40, Menu 40%, (cap: 250 UAH) * 10k, 2026 | `other` | 6 | 24.71 | 0.00 | 24.71 |
| UA, Marketing Promocode 2026, Menu 100%, (cap: 500 UAH) * 200 | `marketing` | 1 | 9.49 | 0.00 | 9.49 |
| UA, BAP Yanovych Promocode, HAPPYB1RTHDAY, Menu 100%, (cap: 500 UAH) * 100, round 2 | `other` | 1 | 8.99 | 0.00 | 8.99 |
| `cs_small_comp_basket_with_cap_ua` | `other` | 4 | 3.22 | 0.00 | 3.22 |
| Partnership_WebPromoCodePage_30%_UA_Q2_Y26 | `marketing` | 1 | 2.90 | 0.00 | 2.90 |

## Next accounting action

To attribute the €3,787.45 CP L1 residual to a business owner, Finance / Delivery Economics needs to expose its components below `total_variable_costs_eur` for LOKO. The current provider-weekly financial fact supports a reconciled CP L1 bridge, but does not label that residual at campaign level. Campaign changes alone will not fix CP L1, because campaign spend is downstream of it.