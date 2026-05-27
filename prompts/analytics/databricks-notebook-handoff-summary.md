# Databricks Notebook Handoff Summary

Use this prompt pack when you have a large Databricks notebook and need to explain what it does clearly without reading every cell.

The goal is not to audit every line of code. The goal is to create a practical handoff summary for a manager, product stakeholder, or another analyst.

---

## When to Use This

Use this when you need to understand or explain:

- What business question the notebook answers
- What data sources it uses
- What major joins and filters shape the result
- What metrics, flags, or outputs are created
- What the final result means
- What assumptions or caveats matter before presenting the work

---

## 1. Default All-in-One Prompt

Use this first in most cases.

```text
I need a clear, practical handoff summary of this Databricks notebook.

Audience:
- A manager who wants the business purpose and takeaway
- Another analyst who may need to review or continue the work

This is not a code audit and not a cell-by-cell summary. Focus on explaining the analysis clearly without forcing someone to read the full notebook.

Do not modify the notebook.
Do not run expensive cells unless you ask first.
Focus on what the code actually does, not only what markdown says.

Please produce:

1. Executive summary
Give 5-7 bullets:
- Main question
- Data used
- Population analyzed
- Main comparison or metric
- Final output
- Likely takeaway
- Key caveat

2. Manager-friendly explanation
Explain the analysis as a simple data story:
- What we started with
- What we filtered to
- What we joined in
- What we calculated
- What the final output shows
- Why it matters

3. Analyst handoff
Create practical tables for:

Important inputs:
| Input | Purpose | Key fields | Why it matters |
|---|---|---|---|

Important joins:
| Join | Key | Type | Why it matters | Watchout |
|---|---|---|---|---|

Important filters:
| Filter | Meaning | Impact on analysis |
|---|---|---|

Important metrics:
| Metric / flag | Definition | Numerator | Denominator | Grain | Notes |
|---|---|---|---|---|---|

Final outputs:
| Output | What it shows | How to interpret it |
|---|---|---|

4. Assumptions and caveats
List only the major items that affect interpretation.

5. Suggested next steps
List the most useful follow-up checks or analysis improvements.

Keep it concise but specific.
Use plain English.
Mention cell numbers or section names only where helpful.
Flag unclear logic instead of guessing.
```

---

## 2. Manager-Friendly Rewrite Prompt

Use this after the first summary when the audience is a manager, PM, or leadership stakeholder.

```text
Rewrite the notebook summary for a manager or product stakeholder.

Audience:
- Product manager
- Analytics manager
- Business stakeholder
- Someone who does not need to read the code

Style:
- Plain English
- Clear and concise
- No unnecessary technical detail
- Mention joins, filters, and grain only when they affect interpretation
- Avoid code language unless needed

Please produce:

1. Executive summary
Give 6-8 bullets covering:
- What question the notebook answers
- What data was used
- What population was included
- What major comparisons were made
- What the output shows
- What the likely takeaway is
- What caveats matter

2. Analysis story
Explain the analysis in simple terms:
- We started with...
- We narrowed it to...
- We joined in...
- We compared...
- The output helps us understand...

3. Key interpretation notes
List the assumptions that matter for interpreting the result.

4. Recommended next step
Suggest the most logical follow-up based on the notebook.

Do not include cell-by-cell detail.
Do not overstate conclusions that are not directly supported by the notebook.
Flag unclear items instead of guessing.
```

---

## 3. Analyst Continuation Prompt

Use this when another analyst may need to review, validate, or continue the notebook.

```text
Now create an analyst continuation summary.

Goal:
Help another analyst understand enough of this notebook to continue the work without reading every cell.

Do not create a full audit. Focus only on the parts that matter for continuing, validating, or modifying the analysis.

Please provide:

1. Analysis purpose
- Main business question
- Main population being analyzed
- Final output or decision this supports

2. Data flow
Create a simple flow:
Source data → cleaning/filtering → joins → aggregations → final output

3. Important inputs
Create a table:
| Input table / dataframe / view | Plain-English purpose | Key fields used | Why it matters |
|---|---|---|---|

4. Important joins
Create a table:
| Left input | Right input | Join key | Join type | Why this join matters | Possible issue to watch |
|---|---|---|---|---|---|

5. Important filters
Create a table:
| Filter | Plain-English meaning | Where applied | Why it matters |
|---|---|---|---|

6. Metric definitions
Create a table:
| Metric / flag | Plain-English definition | Numerator | Denominator | Grain | Notes |
|---|---|---|---|---|---|

7. Grain and population
Explain:
- What one row represents in the major intermediate/final datasets
- What population is included
- What population is excluded
- Where the grain changes in the notebook

8. Final outputs
Explain:
- What final outputs are produced
- Which output is most important
- How to interpret the output

9. What to check before presenting
List the 5-8 most important validation checks, such as:
- Row counts before/after major joins
- Duplicate checks
- Date range checks
- Denominator checks
- Filters that could exclude meaningful records
- Metrics that depend on assumptions

Keep this practical and concise.
```

---

## 4. Slack / Confluence Summary Prompt

Use this when you need a paste-ready update.

```text
Turn the notebook handoff summary into a polished update I can paste into Slack or Confluence.

Audience:
- Product and analytics stakeholders

Style:
- Clear
- Direct
- Not too technical
- No AI-sounding filler
- Keep the original meaning
- Do not overstate the result

Structure:

1. Purpose
Briefly explain what the notebook is analyzing.

2. Approach
Explain the data flow in plain English:
- Starting data
- Major filters
- Major joins
- Metrics/output created

3. Key takeaway
Summarize what the analysis appears to show.

4. Interpretation notes
List caveats or assumptions that matter.

5. Next steps
List 2-4 practical follow-ups.

Keep it concise and paste-ready.
```

---

## 5. Join and Filter Drilldown Prompt

Use this when the first summary is too high-level or when joins/filters are likely to affect the conclusion.

```text
Explain the important joins and filters in this notebook in plain English.

Do not list every minor condition. Focus only on joins and filters that affect the final result.

For joins, include:
- What is being joined
- Join key
- Join type, if clear
- Why the join exists
- What could happen if the join is wrong

For filters, include:
- The filter logic
- Plain-English meaning
- Whether it limits the population, time window, product group, order status, or event type
- Why it matters for the final conclusion

Then summarize:
- The final analysis population
- The main exclusions
- The biggest interpretation risk from the joins or filters
```

---

## 6. Metric Definition Drilldown Prompt

Use this when the notebook has rates, flags, CASE statements, or denominators.

```text
Extract and explain the key metric definitions from this notebook.

Focus on metrics, rates, flags, and derived fields that affect the final output.

For each important metric or flag, create a table:

| Metric / flag | Plain-English meaning | How it is calculated | Numerator | Denominator | Grain | Important filters | Where it appears |
|---|---|---|---|---|---|---|---|

Also explain:
- Which metrics are final outputs versus intermediate helper fields
- Whether any metric uses a hidden assumption
- Whether any denominator could be misunderstood
- Whether the metric is calculated before or after joins/filters
- What someone should validate before using this metric in a presentation

Do not summarize unrelated cells.
```

---

## Recommended Workflow

1. Start with **Default All-in-One Prompt**.
2. Use **Manager-Friendly Rewrite Prompt** if the output is going to leadership or PMs.
3. Use **Analyst Continuation Prompt** if someone else needs to pick up the notebook.
4. Use **Slack / Confluence Summary Prompt** when you need a paste-ready update.
5. Use the drilldown prompts only when joins, filters, or metrics need more clarity.
