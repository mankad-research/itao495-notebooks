# Workflow Library (Project 1: Automate One Task)

Six datasets, 40 items each. Pick one, run an AI model on all 40 items, hand-label 20 of the outputs, then compute accuracy and cost.

**All data is synthetic.** Companies, people, products, and messages are invented. Any resemblance to real ones is coincidence, and no real personal data is used.

## Datasets

| Dataset | Model should | Suggested JSON keys | Counts as correct |
|---|---|---|---|
| support_email_triage | Classify each email by category (Billing, Shipping, Technical, Returns, Account, Other) and urgency (low, medium, high) | `category`, `urgency` | Both fields are right |
| product_reviews | Classify sentiment (positive, neutral, negative) and main topic (quality, price, shipping, support, usability) | `sentiment`, `main_topic` | Both fields are right |
| expense_categorization | Assign one category: Travel, Meals, Software, Office Supplies, Marketing, Training, Other | `category` | Category is right |
| meeting_notes | List action items as "Owner: task" and count them | `action_items` (list), `n_action_items` | Count is right and each item has the right owner and task (wording can differ) |
| lead_qualification | Label the inquiry hot, warm, or cold and give a one-sentence reason | `label`, `reason` | Label is right and the reason cites the rubric accurately |
| job_posting_skills | Extract only skills stated as required | `required_skills` (list) | All required skills found (paraphrase is fine) and no nice-to-have skills included |

Each dataset has one `id` column. Match model output to items by `id`.

## Definitions used when the data was written

- **Support category:** the customer's main request. **Urgency:** high means a deadline within days, a safety issue, or suspected fraud or account takeover; medium means action is needed but no hard deadline; low means a question or feedback.
- **Review main topic:** the aspect that drives the reviewer's opinion.
- **Action item:** a future task that a named person commits to or is assigned. Past work, hypothetical ideas, cancelled plans, and tasks with no named owner do not count.
- **Required skills:** skills the posting states as required, must-have, or needed. Preferred, bonus, plus, and nice-to-have skills do not count. Degrees, years of experience, and physical requirements are not skills.

## Lead rubric

- **Hot:** budget stated or clearly approved, AND decision timeline within 60 days, AND the writer is a decision-maker or has one involved.
- **Warm:** genuine interest but missing one of those three.
- **Cold:** vague, student or researcher, competitor fishing, or no buying signal.

## Labeling your 20 outputs

Hand-label 20 model outputs yourselves. Read the original item, decide whether the model's output is correct, and note your reasoning.

About 30% of items are deliberately tricky (sarcasm, two issues in one message, missing information, near-miss leads, "nice to have" mixed in with required skills). Reasonable people can disagree on a few, so write down your judgment calls.
