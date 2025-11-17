This project investigates how different prompt framings cause Large Language Models (LLMs) to produce biased narratives from the same dataset. The experiment tests:

H1: Framing Bias - Positive vs negative narrative framing
H2: Confirmation Bias - Whether models agree with user-stated beliefs
H3: Selection Bias - How models choose “important” vs “unimportant” games

Two LLMs were tested (GPT-5.1 and Claude Sonnet 4.5).
Each prompt was run three times per model in separate chats.
All raw outputs are stored in results/llm_responses.xlsx.

Folder Summary
prompts/ All prompt templates (H1–H3)
results/ Raw LLM responses (Excel)
analysis/ Ground truth, hypotheses, and bias findings
REPORT.md Final written report

Key Findings
Positive and negative framing produced different sets of highlighted games.
Models supported user beliefs even when data was mixed (confirmation bias).
Postseason and dramatic games were repeatedly labeled “important” (selection bias).
Claude showed more numeric distortions; GPT-5.1 was more conservative.
All dataset content in this repo is anonymized and included only as pasted text inside prompts.
