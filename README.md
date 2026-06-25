# Part 2: KPI Framework, Business Experiment Analysis & Decision Recommendation

## Business Context
The business decision is whether to roll out the new onboarding campaign, limit it to some user groups, or keep testing. The decision affects new users, the growth team, product onboarding, and support. Paid conversion should improve, but not by creating more refunds, more tickets, slower conversion, or weak segments. The evidence needed is a clean Control vs Treatment read, a test on paid conversion, and a guardrail check.

## Dataset Description
- Source file: `data/campaign_experiment_data.xlsx`
- Rows analyzed: 1408
- Experiment groups: Control (693 users) and Treatment (715 users)
- Key fields: experiment group, region, device type, traffic source, plan type, funnel flags, revenue, support tickets, refunds, days to convert, and engagement score.

## North Star Metric Selected
Paid conversion rate is the North Star metric. The campaign is supposed to turn more new users into paying subscribers. The other metrics explain the funnel or check for damage.

## KPI Tree Summary
The KPI tree in `outputs/kpi_tree.png` connects paid conversion rate to acquisition quality, activation journey, and revenue quality. It also shows guardrails for refunds, support burden, engagement, and segment-level decline.

## Experiment Analysis Approach
- Checked missing values.
- Checked Control and Treatment group counts.
- Checked duplicate user IDs.
- Validated binary fields.
- Flagged revenue outliers using the IQR rule.
- Compared segment distribution across region, device type, traffic source, and plan type.
- Compared Control vs Treatment for the required summary metrics.

Data quality handling: 56 rows had missing required values, 16 duplicate user ID rows were found, and 4 revenue outliers were flagged. I kept the outliers in the main business read because they are real revenue observations, but treated them as a review item. Missing `days_to_convert` is expected for users who did not convert.

## Hypothesis Test Summary
- Test: one-tailed two-proportion z-test.
- Metric: paid conversion rate.
- Control paid conversion rate: 3.2%
- Treatment paid conversion rate: 7.0%
- Absolute lift: 3.8%
- P-value: 0.0006
- Statistical readout: Reject the null hypothesis.

The test is one-tailed because the launch decision is directional: Treatment should be rolled out only if it improves paid conversion.

## Guardrail Metrics Considered
- Refund rate: 0.0% Control vs 0.4% Treatment
- Support ticket rate: 14.7% Control vs 24.8% Treatment
- Engagement score: 57.0 Control vs 62.9 Treatment
- Average days to convert: 8.9 Control vs 6.4 Treatment
- ARPU: $51.75 Control vs $53.88 Treatment
- Revenue per converted user: about $1,630 Control vs about $770 Treatment

## Final Recommendation
Run a phased launch, not a blanket rollout. Prioritize segments with clear positive lift, including Referral, Free plan, North, Tablet/Mobile, Paid Search, Email, and Organic. Hold out or re-test Social traffic because it shows negative lift. Treat Basic plan as inconclusive because the lift is nearly flat.

The tradeoff is important: Treatment improves conversion, but converted users bring in less revenue on average and support tickets rise from 14.7% to 24.8%. Do not scale without support capacity, onboarding FAQ fixes, and weekly ticket monitoring.

## Assumptions and Limitations
- Revenue outliers were flagged for review but retained in the main business summary.
- Missing `days_to_convert` is expected for users who did not convert.
- The significance level is 5%.
- The analysis uses 30-day revenue and early engagement, not long-term retention.

## Screenshots Included
- `screenshots/summary_metrics.png`
- `screenshots/hypothesis_test_output.png`
- `screenshots/kpi_tree_preview.png`
