Hypothesis 1 - Framing Bias

Statement
The wording of the prompt (positive vs negative framing) will cause the LLM to produce different narratives about the same season, even though the data does not change.

Reasoning
The dataset contains
1) Wins with large margins
2) Losses with large margins
3) Many ranked opponents
4) Several close games
This makes it easy for an LLM to highlight either good or bad aspects depending on the framing.

Expected Outcome
If this bias exists then
1) Positive framing prompts will highlight:
	a) Big wins (+12, +9, +8)
	b) NCAA tournament win (+6)
	c) Wins vs ranked teams (#17, #20, #11)
2) Negative framing prompts will highlight:
	a) Large losses (–15, –8, –5)
	b) Losing record vs ranked teams (3–7)
	c) Close losses (–1, –3)
If framing has no effect, then the summaries should be nearly identical.

Hypothesis 2 - Confirmation Bias

Statement
When the prompt includes an explicit claim (e.g., “This was a disappointing season”), the LLM will adjust its summary to support that claim regardless of what the actual data shows.

Reasoning
LLMs tend to “agree” with the user because their training encourages helpfulness and alignment.
The dataset is mixed (9–10 record, +14 differential), so interpreting it positively or negatively is easy for the model depending on your wording.

Expected Outcome
If this bias exists then
1) When told “This was an excellent season”, the LLM will emphasize:
	a) Wins vs ranked teams
	b) NCAA tournament success
	c) High scoring wins
2) When told “This was a poor season”, the LLM will emphasize:
	a) Losing record
	b) Large losses (–15, –8, –5)
	c) Subpar results vs ranked opponents
If no confirmation bias exists, then the model will explain the disagreement with user claims.

Hypothesis 3 - Selection Bias

Statement
The LLM will systematically focus on certain types of games (e.g., ranked opponents, blowouts, or tournament games) even when prompts do not ask it to prioritize them.

Reasoning
Schedule includes clear categories like
1) Ranked opponents
2) Postseason games
3) Large margins
4) Close games
5) Home vs away
This allows us to detect if the model selects a particular subset of games across many prompts.

Expected Outcome
If this bias exists then
1) The model may repeatedly mention ranked losses (#2, #3, #7) even in neutral prompts.
OR
2) It may consistently highlight big wins regardless of prompt structure.
OR
3) It may always discuss tournament games (G17, G18, G19).
If no selection bias exists then the game mentions will be evenly distributed or tied to clear logic.