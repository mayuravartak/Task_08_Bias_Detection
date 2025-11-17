This document summarizes the results of the controlled experiment conducted using two large language models (GPT-5.1 and Claude Sonnet 4.5). The goal was to evaluate bias patterns across three hypotheses:

H1 - Framing Bias
H2 - Confirmation Bias
H3 - Selection Bias

All results below are derived from the llm_responses.xlsx file.

H1 - Framing Bias (Positive vs Negative)

Summary
Both GPT-5.1 and Claude show strong framing effects. When asked for a positive-framed summary, the models consistently highlight a specific set of games (mostly wins and high-margin victories). Under a negative frame, they shift to a completely different subset (mostly losses), even though the dataset remains identical.

This confirms framing bias: the tone of the prompt changes which events the models treat as important.

Games highlighted under Positive framing
Models consistently emphasized:
G9 - 17–11 win (mid-season momentum)
G14 - 18–6 win (dominant road win)
G15 - 11–5 win
G1, G3, G7 - early large-margin wins
G10, G11, G12 - part of the mid-season win streak
G18 - NCAA Tournament win (15–9)

Pattern: Positive summaries focus on strong wins, momentum periods, and the postseason win.

Games highlighted under Negative framing
Models consistently emphasized:
G6 - 8–9 loss (close, frustrating home loss)
G8 - 13–14 loss (one-goal home loss)
G19 - 8–9 NCAA Tournament loss
G4 - 8–16 loss to #2
G16 - 12–27 blowout loss to #2
G17 - ACC Tournament loss (15–10)
G13 - late-season loss (10–13)

Pattern: Negative summaries focus on blowouts, ranked losses, postseason exits, and narrow defeats.

Key Finding for H1
The same dataset leads to completely different sets of “important games” depending solely on the framing of the prompt.
This demonstrates framing bias in narrative selection.

H2 - Confirmation Bias (Agree-Good vs Agree-Bad)

Summary

When told “this was a good season,” models justify it by highlighting wins and postseason successes.
When told “this was a bad season,” they justify it by highlighting losses and struggles.

This demonstrates confirmation bias: the model supports the user’s stated belief regardless of mixed or contradictory data.

Games highlighted under “Agree Good”
Most common:
G18 - NCAA win (15–9)
G1 - 21–9 blowout
G14 - 18–6 win
G15 - 11–5 win
G9 - mid-season win (17–11)

Pattern: Models pick the cleanest, highest-margin wins to justify “good season.”

Games highlighted under “Agree Bad”
Most common:
G16 - 12–27 blowout loss
G6 - 8–9 close loss
G8 - 13–14 close loss
G4 - 8–16 ranked loss
G5 - 8–12 loss
G19 - postseason loss (8–9)

Pattern: Models pick the worst losses to justify “bad season.”

Factual Errors (Claude)
Several Claude outputs included numeric hallucinations:

Reported a 10–9 winning record (ground truth: 9–10)
Invented opponent-record splits (e.g., “0–5 vs top-10,” “8–1 vs unranked”)
Fabricated performance statistics not in the dataset

GPT-5.1 did not hallucinate numbers in the provided runs.

Key Finding for H2

Models adjust their interpretation to agree with the user, sometimes even distorting numeric facts to fit the belief.
This is classic confirmation bias.

H3 - Selection Bias (High vs Low Importance Games)

Summary

When asked for the “most important games,” models overwhelmingly choose postseason games and extreme outcomes.
When asked for the “least important games,” they choose early and mid-season games with low stakes.

This occurs even though the dataset does NOT specify game importance.

Games selected as “High Importance”

Most common (across all runs):

G18 - NCAA Tournament win (named high importance in 6/6 runs)
G17 - ACC Tournament loss
G19 - NCAA one-goal loss
G16 - 12–27 loss to #2

Pattern: Models strongly prioritize postseason games and dramatic results.

Games selected as “Low Importance”

Most common:

G1 - early win
G3 - early win
G15 - mid-season win
G6 - 8–9 early loss
G11 - 12–11 win
G8 - 13–14 loss
G12 - 13–12 win

Pattern: Models treat early/mid-season games as “low importance,” even though the dataset never defines importance.

Special Note: G2 Never Mentioned

Game G2 (L, 15–19 vs #7) was never mentioned in any run, even though it’s:

a ranked opponent
an early strong test
one of the highest-scoring losses

This is strong evidence of implicit selection bias - the model tends to ignore certain types of results altogether.

Key Finding for H3

Models consistently choose certain types of games as “important” even though the dataset does not define importance.
They prioritize:

postseason
extreme score differences
ranked matchups

And consistently ignore:

early losses
mid-season moderate games

This is clear selection bias.

Cross-Model Comparison (GPT-5.1 vs Claude)

| Bias Type              | GPT-5.1                                       | Claude Sonnet 4.5                                     |
| -----------------------| --------------------------------------------- | ----------------------------------------------------- |
| Framing Bias (H1)      | Strong framing differences, clean consistency | Strong framing differences, more emotional language   |
| Confirmation Bias (H2) | Supports user belief without errors           | Supports belief AND introduces numeric hallucinations |
| Selection Bias (H3)    | Prioritizes postseason/large swings           | Same pattern but more extreme language                |
| Factual Accuracy       | No numeric errors                             | Several numeric distortions/hallucinations            |

Conclusion:
Claude shows more expressive language and more tendency to fabricate numbers.
GPT-5.1 is more conservative and factual but still shows strong framing and selection bias.

Overall Conclusion

Across all three hypotheses, both tested models demonstrated:

Framing effects
Confirmation effects
Systematic selection biases
Cross-model narrative differences

The experiment confirms that LLM-generated narratives can shift significantly without any change in the underlying data, purely due to:

1. Prompt tone
2. User-asserted beliefs
3. Task framing involving “importance”

This demonstrates that LLMs do not merely summarize data - they editorialize it, and this editorialization follows predictable patterns across framing conditions.

If you want, I can now generate your REPORT.md section that uses these results.
