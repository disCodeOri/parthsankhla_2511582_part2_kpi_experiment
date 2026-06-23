# Recommendation Memo

## Executive Summary
The business decision is whether to roll out the new onboarding campaign, limit it to some user groups, or keep testing. The decision affects new users, the growth team, product onboarding, and support. Paid conversion should improve, but not by creating more refunds, more tickets, slower conversion, or weak segments. The evidence needed is a clean Control vs Treatment read, a test on paid conversion, and a guardrail check.

Treatment converted 7.0% of users to paid. Control converted 3.2%. That is a 3.8% absolute lift. The p-value from the one-tailed z-test is 0.0006.

Recommendation: Launch only for selected segment.

## North Star Metric
Paid conversion rate is the North Star metric. The campaign is meant to move users from signup and onboarding into paid subscriptions.

Landing visits, trials, onboarding completion, revenue, and engagement are supporting metrics. They explain the path to conversion, but they do not replace the paid conversion read. Optimizing only for paid conversion could still create poor-fit users, refunds, more tickets, or gains that only work in one segment.

## KPI Tree Explanation
The KPI tree breaks paid conversion into acquisition quality, activation journey, and revenue quality. The guardrails are refund rate, support ticket rate, engagement score, and segment-level decline.

## Experiment Result Summary
| Metric | Control | Treatment | Delta |
| --- | ---: | ---: | ---: |
| Paid conversion rate | 3.2% | 7.0% | 3.8% |
| Trial start rate | 25.1% | 29.1% | 4.0% |
| Onboarding completion rate | 15.6% | 21.3% | 5.7% |
| ARPU | $51.75 | $53.88 | $2.13 |

## Hypothesis Test Interpretation
The p-value is below 0.05. Treatment has enough statistical support on paid conversion.

## Guardrail Analysis
| Guardrail | Control | Treatment | Delta | Readout |
| --- | ---: | ---: | ---: | --- |
| Refund rate | 0.0% | 0.4% | 0.4% | Acceptable |
| Support ticket rate | 14.7% | 24.8% | 10.0% | Risk |
| Engagement score | 57.0 | 62.9 | 5.9 | Acceptable |
| Days to convert | 8.9 | 6.4 | -2.5 | Acceptable |

## Segment-Level Insight
The strongest lift is in traffic_source = Referral, where Treatment is ahead by 8.5%. The weakest material segment is traffic_source = Social, where Treatment is at -1.7% versus Control. This is the main reason I would not treat the result as an automatic full rollout.

## Final Recommendation
Launch only for selected segment.

## Risks and Limitations
- This analysis uses 30-day outcomes only.
- Revenue outliers were flagged, not removed.
- Segment reads may be noisy where segment sample sizes are smaller.
- The test focuses on paid conversion, so long-term retention is not directly measured.

## Next Steps
- Validate the campaign experience for weaker segments.
- Monitor refunds, support tickets, and activation quality after rollout.
- Add retention and renewal metrics before making long-term budget decisions.
