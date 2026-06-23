# Hypothesis Test Notes

## Metric Being Tested
The test uses paid conversion rate. It is calculated as paid users divided by all users in the group.

## Hypotheses
- Null hypothesis: Treatment paid conversion rate is less than or equal to Control paid conversion rate.
- Alternate hypothesis: Treatment paid conversion rate is greater than Control paid conversion rate.

## Test Design
- Test type: one-tailed two-proportion z-test.
- Significance level: 5%.
- Why one-tailed: the launch question is whether Treatment improves paid conversion, not just whether it is different.

## Test Inputs
| Input | Control | Treatment |
| --- | ---: | ---: |
| Users | 693 | 715 |
| Paid conversions | 22 | 50 |
| Paid conversion rate | 3.2% | 7.0% |

## Test Output
- Absolute lift: 3.8%
- Relative lift: 120.3%
- Z-score: 3.2519
- One-tailed p-value: 0.0006

## Decision Rule
Reject the null hypothesis if the p-value is below 0.05 and the treatment conversion rate is higher than control.

## Interpretation
The test rejects the null. Treatment has a higher paid conversion rate than Control, and the result is unlikely to be random noise at the 5% level.

## Business Link
Paid conversion is the main launch metric because it links onboarding to subscription growth. I still checked guardrails because a campaign can lift conversion and still be bad for the business if it brings low-quality users.
