# Cost-Benefit Analysis for Prediction-Based Interventions

This note explains how to do a cost-benefit analysis when a prediction model is used to assign a limited intervention.

The main idea:

> A prediction model ranks people by risk. A cost-benefit analysis asks whether intervening on the highest-risk people is worth the cost.

The model does not create the benefit by itself. The benefit comes from the intervention.

So we need to keep three things separate:

- who the model flags
- what would happen to those people without the intervention
- how much the intervention changes those outcomes

We will use a shooting-victimization example.

## 1. The Policy Setup

Suppose a city has an intervention for people at high risk of being shooting victims.

The intervention could be something like intensive outreach, services, or CBT plus summer jobs.

The city cannot serve everyone. It has enough resources for 500 people.

The prediction model is used to rank people by predicted shooting-victimization risk.

The policy rule is:

> Give the intervention to the 500 people with the highest predicted risk.

In this setup:

- the prediction model chooses the group to target
- the intervention is what may reduce the number of adverse outcomes
- the cost-benefit analysis compares the expected benefits to the program costs

## 2. Start With the Flagged Group

Suppose the model flags the top 500 people.

Among those 500 people, historical outcome data show that 65 become shooting victims.

| Quantity | Value |
|---|---:|
| Number flagged | 500 |
| Shooting victims among flagged group | 65 |
| Share of flagged group victimized | 65 / 500 = 13% |

The number 65 is important because it tells us how many adverse outcomes occurred in the group selected by the model.

If the model flagged 500 people but only 5 of them later became shooting victims, the intervention would have fewer victimizations it could possibly prevent.

## 3. Add the Treatment Effect

The model does not prevent shootings.

The intervention may prevent shootings.

Suppose we assume the intervention reduces shooting victimization by 50% among people who would otherwise become shooting victims.

Then:

$$
prevented\ victimizations = victimizations\ among\ flagged \times treatment\ effect
$$

In this example:

$$
prevented\ victimizations = 65 \times 0.50 = 32.5
$$

We can round this to about 33 prevented victimizations.

That means:

> If the intervention is assigned to the 500 highest-risk people, and if the intervention reduces victimization by 50%, then we expect about 33 fewer victimizations.

## 4. Convert Prevented Outcomes Into Dollars

To compare benefits and costs, we need to put the prevented outcomes into dollar terms.

Suppose we value one prevented victimization-year at $100,000.

Then:

$$
gross\ benefit = prevented\ victimizations \times value\ per\ prevented\ victimization
$$

For a one-year benefit:

$$
gross\ benefit = 33 \times \$100{,}000 = \$3.3\ million
$$

If the benefit lasts for three years:

$$
gross\ benefit = 33 \times \$100{,}000 \times 3 = \$9.9\ million
$$

The estimated benefit increases if the intervention effect lasts longer.

## 5. Compute Program Costs

Now compute the cost of providing the intervention.

Suppose the program costs $20,000 per person.

The city serves 500 people.

$$
program\ cost = number\ flagged \times cost\ per\ person
$$

So:

$$
program\ cost = 500 \times \$20{,}000 = \$10\ million
$$

This cost applies to everyone who receives the intervention, not just the people who would have become shooting victims.

That is why precision matters.

If many flagged people would not have experienced the outcome, the city still pays to serve them.

## 6. Compute Net Benefit

Net benefit is:

$$
net\ benefit = gross\ benefit - program\ cost
$$

For the one-year benefit:

$$
net\ benefit = \$3.3\ million - \$10\ million = -\$6.7\ million
$$

For the three-year benefit:

$$
net\ benefit = \$9.9\ million - \$10\ million = -\$0.1\ million
$$

Under these assumptions, the program does not quite pay for itself.

But it is close if the benefits last for three years.

## 7. Same Example in Python

```python
num_flagged = 500
victims_among_flagged = 65

treatment_effect = 0.50
value_per_prevented_victimization = 100000
cost_per_person = 20000

prevented_victimizations = victims_among_flagged * treatment_effect
program_cost = num_flagged * cost_per_person

one_year_benefit = prevented_victimizations * value_per_prevented_victimization
three_year_benefit = prevented_victimizations * value_per_prevented_victimization * 3

one_year_net_benefit = one_year_benefit - program_cost
three_year_net_benefit = three_year_benefit - program_cost

summary = pd.DataFrame({
    'quantity': [
        'Number flagged',
        'Victims among flagged',
        'Prevented victimizations',
        'Program cost',
        'One-year gross benefit',
        'One-year net benefit',
        'Three-year gross benefit',
        'Three-year net benefit'
    ],
    'value': [
        num_flagged,
        victims_among_flagged,
        prevented_victimizations,
        program_cost,
        one_year_benefit,
        one_year_net_benefit,
        three_year_benefit,
        three_year_net_benefit
    ]
})

summary
```

## 8. What This Has To Do With Prediction Metrics

AUC tells us whether the model ranks higher-risk people above lower-risk people.

Precision at the intervention threshold tells us how many people in the flagged group actually experience the outcome.

For cost-benefit analysis, precision at the intervention threshold is often more directly relevant than AUC.

In this example, the city is not intervening on everyone. It is intervening on the top 500.

So the key question is:

> Among the top 500 people, how many would experience the outcome without the intervention?

That number determines how many outcomes the intervention can potentially prevent.

## 9. Comparing Two Interventions

Cost-benefit analysis is especially useful when the interventions differ.

Suppose an agency has a fixed budget of $1,000,000 and is deciding between two interventions:

| Intervention | Outcome | Slots | Cost per person | Treatment effect |
|---|---|---:|---:|---:|
| Court support | Failure to appear | 1,000 | $1,000 | 40% |
| Intensive supervision | Violent arrest | 200 | $5,000 | 25% |

Both programs cost $1,000,000 in total:

$$
1{,}000 \times \$1{,}000 = \$1{,}000{,}000
$$

$$
200 \times \$5{,}000 = \$1{,}000{,}000
$$

The tradeoff is capacity versus intensity.

Court support can reach more people, but it targets a less severe outcome.

Intensive supervision reaches fewer people, but it targets a more severe outcome.

The more expensive intervention needs some combination of:

- a higher-risk flagged group
- a larger treatment effect
- a more costly outcome prevented

A lower-cost intervention can be worthwhile even if each prevented outcome is less costly, because the same budget can serve more people.

## 10. Template for the Final Project

For each intervention, compute:

1. `num_flagged`: how many people receive the intervention
2. `true_positives`: how many flagged people actually experience the outcome
3. `prevented_outcomes`: `true_positives * treatment_effect`
4. `gross_benefit`: `prevented_outcomes * benefit_per_prevented_outcome`
5. `program_cost`: `num_flagged * cost_per_case`
6. `net_benefit`: `gross_benefit - program_cost`

The final recommendation should not be based on prediction accuracy alone.

A strong recommendation should discuss:

- how many people the model flags
- how many flagged people experience the outcome
- how large the treatment effect is assumed to be
- how costly the intervention is
- how costly the prevented outcome is
- whether the fairness metrics raise concerns

## 11. Main Takeaway

The model answers:

> Who is most at risk?

The intervention answers:

> Can we reduce that risk?

The cost-benefit analysis answers:

> Is the expected reduction in the outcome large enough to justify the cost?

## 12. Quiz

Use the setup from the fixed-budget example:

- Court support has 1,000 slots and costs $1,000 per person.
- Intensive supervision has 200 slots and costs $5,000 per person.
- Court support reduces FTAs by 40% among people who would otherwise fail to appear.
- Intensive supervision reduces violent arrests by 25% among people who would otherwise have a violent arrest.

### Questions

1. What is the total program cost of court support?

2. What is the total program cost of intensive supervision?

3. Suppose 300 of the 1,000 people assigned to court support would otherwise fail to appear. How many FTAs do we expect court support to prevent?

4. Suppose 80 of the 200 people assigned to intensive supervision would otherwise have a violent arrest. How many violent arrests do we expect intensive supervision to prevent?

5. Suppose each prevented FTA is worth $5,000. Using the numbers from Question 3, what is the gross benefit of court support?

6. Using the court-support cost from Question 1 and the gross benefit from Question 5, what is the net benefit of court support?

7. Suppose each prevented violent arrest is worth $100,000. Using the numbers from Question 4, what is the gross benefit of intensive supervision?

8. Using the intensive-supervision cost from Question 2 and the gross benefit from Question 7, what is the net benefit of intensive supervision?

9. Why might the lower-cost court-support program still be worth considering, even if each prevented FTA is worth less than each prevented violent arrest?

10. Why is precision at the intervention threshold important for cost-benefit analysis?

## 13. Quiz Answers

1. Court support costs:

$$
1{,}000 \times \$1{,}000 = \$1{,}000{,}000
$$

2. Intensive supervision costs:

$$
200 \times \$5{,}000 = \$1{,}000{,}000
$$

3. Expected prevented FTAs:

$$
300 \times 0.40 = 120
$$

4. Expected prevented violent arrests:

$$
80 \times 0.25 = 20
$$

5. Gross benefit of court support:

$$
120 \times \$5{,}000 = \$600{,}000
$$

6. Net benefit of court support:

$$
\$600{,}000 - \$1{,}000{,}000 = -\$400{,}000
$$

7. Gross benefit of intensive supervision:

$$
20 \times \$100{,}000 = \$2{,}000{,}000
$$

8. Net benefit of intensive supervision:

$$
\$2{,}000{,}000 - \$1{,}000{,}000 = \$1{,}000{,}000
$$

9. Court support may still be worth considering because the same budget can serve many more people. A lower-cost intervention can be attractive if it reaches enough people or has a strong enough treatment effect.

10. Precision at the intervention threshold tells us how many people in the flagged group would actually experience the outcome without the intervention. That number determines how many outcomes the intervention can potentially prevent. A model with low precision at the threshold may spend resources on many people who would not have experienced the outcome.
