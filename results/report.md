1. OVERVIEW

This project investigates whether Large Language Models (LLMs) generate biased or systematically different data narratives when given the same dataset but prompted with different framings. The experiment uses an anonymized women’s lacrosse season dataset (19 games, regular season + postseason). The goal was to test how LLMs select, emphasize, or ignore data based on:

H1 - Framing Bias
H2 - Confirmation Bias
H3 - Selection Bias

Two LLMs were evaluated:

GPT-5.1 (OpenAI)
Claude Sonnet 4.5 (Anthropic via Syracuse license)

Each of the six prompt conditions was run three times per model in fresh chats to avoid memory contamination.
A total of 36 responses were collected and analyzed.

2. DATASET (Anonymized Summary)

The dataset includes 19 anonymized games with:
game_id
date
location
opponent label
opponent rank
tournament type
result (W/L)
score_for
score_against
score_diff
season phase
No personally identifying information or real team names appear.

3. EXPERIMENTAL PROMPTS

Six controlled prompts were designed across three bias hypotheses:

H1 - Framing Bias
Positive Frame
Negative Frame

H2 - Confirmation Bias
Agree Good ("This was a good season")
Agree Bad ("This was a bad season")

H3 - Selection Bias
High Importance ("3 most important games")
Low Importance ("3 least important games")

Each prompt was identical across models and included the full dataset block.

4. METHODOLOGY

For each prompt × model, three independent runs were collected.
All raw responses were stored in results/llm_responses.xlsx.

For each run, the following were extracted:
Which games the model highlighted
Tone and sentiment
Any factual errors

Pivot-style comparison tables were created to identify:
Frequent mentions
Omitted games
Differences between framing conditions
Differences across LLMs

5. FINDINGS

5.1. H1 - Framing Bias (Positive vs Negative)
Pattern Observed

Both GPT-5.1 and Claude produced different narratives depending on tone:

Positive framing consistently highlighted:
G9 (17–11 win)
G14 (18–6 win)
G15 (11–5 win)
G1, G3, G7 (early blowout wins)
G10, G11, G12 (mid-season streak)
G18 (NCAA win)

Negative framing consistently highlighted:
G6 (8–9 loss)
G8 (13–14 loss)
G19 (postseason one-goal loss)
G4 (8–16 loss to #2)
G16 (12–27 loss to #2)
G17 (ACC Tournament loss)
G13 (10–13 loss)

Interpretation
The underlying dataset never changed, but the “important” games changed entirely depending on tone.
This confirms framing bias in LLM-generated narratives.

5.2. H2 - Confirmation Bias (User Stated Belief)
Agree Good (LLM supports positive belief)

Most highlighted games:
G18 (NCAA win)
G1, G14, G15 (dominant wins)
G9 (mid-season momentum)
Agree Bad (LLM supports negative belief)

Most highlighted games:
G16 (12–27 loss)
G6, G8 (one-goal losses)
G4, G5 (ranked losses)
G19 (postseason loss)

Factual Errors Found

Claude introduced several numeric distortions to support the belief:
Incorrect record (“10–9 winning season” instead of 9–10)
Fabricated opponent splits (“0–5 vs top-10” or “8–1 vs unranked”)
Extra invented metrics not present in data

GPT-5.1 did not hallucinate numbers in the runs provided.

Interpretation
The model adjusted the narrative to agree with the user's stated belief, even when it required bending facts (Claude).
This demonstrates confirmation bias.

5.3. H3 - Selection Bias (Importance Assignment)
High Importance (3 most important games)

Across models, almost all runs selected:
G18 - NCAA win
G17 - ACC Tournament loss
G19 - NCAA one-goal loss
G16 - blowout vs #2
Low Importance (3 least important games)

Most frequently selected:
G1, G3 (early easy wins)
G15 (mid-season win)
G6 (early loss)
G11, G12 (mid-season close games)
G8 (one-goal loss)

Notable Omission
G2 (ranked early loss)
Never mentioned in any run across any model.

Interpretation
LLMs tend to:
Over-select postseason games
Over-select dramatic wins/losses
Under-select early/mid-season games
Ignore certain events entirely

This confirms selection bias: models infer “importance” even when the dataset gives no such ranking.

6. CROSS-MODEL COMPARISON

Bias Type			| GPT-5.1								| Claude Sonnet 4.5
--------------------|---------------------------------------|--------------------------------------------
Framing Bias		| Strong framing differences			| Strong differences, more emotional phrasing
Confirmation Bias	| Supports belief without errors		| Supports belief with numeric hallucinations
Selection Bias		| Prioritizes postseason/exciting games	| Same pattern, more extreme wording
Factual Accuracy	| No numeric hallucinations				| Multiple numeric distortions

Interpretation

Claude is more expressive and more likely to bend or invent numeric details to support the belief given in the prompt. GPT-5.1 is more conservative but still biased in game selection and framing.

7. LIMITATIONS

The experiment uses a single sport dataset (may not generalize).
Game importance was inferred from LLM output; models may express importance implicitly.
Only two LLMs were used due to time and access constraints.
Narrative analysis relies on explicit mention of game IDs.

8. CONCLUSION

Across all three hypotheses, both LLMs demonstrated measurable biases. For the same dataset:
Framing changes which events become “important”
User claims influence how the model interprets evidence
Models infer importance using their own hidden heuristics
Claude occasionally alters numeric facts to fit a narrative
This experiment supports the conclusion that LLM-generated data narratives are not neutral summaries but are shaped by prompt framing, user beliefs, and the model’s internal patterns of selection.

LLMs can be powerful tools for narrative generation, but these results highlight the importance of:
careful prompt design
independent verification
awareness of narrative bias
caution when using LLMs for data interpretation
