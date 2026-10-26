# Mental State OS v2.1 — scoring and decision logic

## User-experience behavior

- The latest form answers are saved continuously in browser `localStorage` under a separate preferences key, including answers changed before submission. A local calendar-day key keeps the carry-forward behavior convenient within a day without treating yesterday’s sleep and clock times as today’s measurements.
- On the next check-in, the app restores prior sleep figures, wake-up time, clock times for work/breaks, context, selected physical needs, the acknowledgement and all previously answered ratings. Change only what has changed.
- A new rating for physical restlessness was added in v2.0. Records from older versions do not contain it; old reports leave that metric out rather than pretending it was measured. Saved reports from earlier app logic are recalculated using report version 3 when opened or when history renders.
- Wake-up time is entered as a local clock time. The app calculates time awake from the current local clock, including crossing midnight. Work stretch and time since last break are calculated the same way from optional start/end clock times. Quick buttons set current time for a work start or completed break.
- The app refreshes displayed elapsed times every minute and calculates them again when a report is submitted. If a tab remains open across midnight, the app clears daily sleep/work/break times and sleep-quality rating on the next refresh; other symptom ratings stay filled for review.

## Ratings (0–4)

1. Sleep quality (0 very poor, 4 very good)
2. Sleepiness (0 fully alert, 4 fighting sleep)
3. Cognitive fatigue (0 fresh, 4 extreme)
4. Thinking clarity (0 very foggy, 4 very clear)
5. Task readiness (0 not able, 4 ready)
6. Stimulation craving (0 none, 4 overwhelming)
7. Stress/arousal (0 calm, 4 overwhelmed)
8. Physical sluggishness (0 energetic, 4 extremely sluggish)
9. Physical restlessness (0 settled, 4 extremely restless)

Context includes actual sleep last night, average sleep over three nights, wake-up time, elapsed time awake, optional work-start/last-break times, physical needs, recent activity/context and an optional note. The app does not require users to do elapsed-time arithmetic.

## Display scores

Self-report dimensions are mapped from 0–4 to 0–10 by multiplying by 2.5. Fogginess is the reverse of clarity: `(4 - clarity) × 2.5`. Task readiness is displayed in the forward direction; task-start difficulty is the reverse direction when used for reassessment.

Sleep recovery load is a bounded heuristic:

`clamp(max(0, 7 − sleepLast) × 8 + max(0, 7 − sleepRecent) × 5 + (4 − sleepQuality) × 2 + sleepiness × 2, 0, 100)`

The displayed value is shown on a 0–10 scale. It is not a validated sleep-debt score and does not estimate adenosine.

The 0–100 readiness index subtracts fixed weighted penalties for sleepiness, fatigue, fogginess, craving, stress, sluggishness, restlessness (when collected), physical needs and short sleep from 100. It is a heuristic snapshot, not the probability of productivity, a clinical score, or a calibrated forecast. The action-routing rules take precedence over the composite score.

## Action rules (first matched rule wins)

1. **Pronounced sleepiness (rating ≥ 3):** stop demanding work; do not drive or perform safety-critical tasks while fighting sleep. For a daytime nap, consider around 15–20 minutes and allow sleep inertia to clear; protect sufficient night sleep.
2. **Reported illness/unusual symptoms:** pause, assess immediate needs and seek care if symptoms are severe, persistent or concerning.
3. **Reported immediate physical need:** address thirst, hunger, bathroom/basic comfort or pain/discomfort before productivity advice. The action map keys directly off the original need value to avoid mismatched labels.
4. **Sleep limitation combined with symptoms:** if last-night sleep is under 6 hours with sleepiness, fatigue or poor clarity; or 3-night average under 6.5 hours with sleepiness or marked fatigue; or very poor sleep quality with sleepiness/fatigue, reduce cognitive demand, consider a short nap if genuinely sleepy and timing allows, and protect sleep opportunity.
5. **Severe cognitive fatigue / poor clarity / long work stretch:** if fatigue ≥ 3, or fatigue ≥ 2 with clarity ≤ 1, or ≥ 90 minutes since work-start/last break with fatigue ≥ 2, take a screen-free 10-minute break.
6. **High stress or physical restlessness:** if stress ≥ 3 or restlessness ≥ 3, try comfortable slow breathing (around 3 seconds in, 5–6 out) for up to 5 minutes. Stop if dizzy or uncomfortable.
7. **High stimulation craving with lower sleepiness/fatigue:** if craving ≥ 3 and sleepiness ≤ 2 and fatigue ≤ 2, put the phone out of reach, observe the urge briefly and do a 5-minute task start.
8. **Moderate mental noise:** if stress ≥ 2 and none of the earlier priorities matched, do a 5-minute natural-breath attention reset. Evidence for mindfulness is stronger for structured repeated programs than for any one short session, so this is a low-friction experiment rather than a guaranteed cognitive booster.
9. **High physical sluggishness:** try a 5–10 minute easy-to-brisk walk and daylight if practical and safe.
10. **Very low task readiness:** use a two-minute concrete start.
11. **Otherwise:** use a protected 10-minute work sprint and reassess.

The conditions and thresholds are transparent routing choices, not validated clinical cutoffs. Several symptoms can coexist; order indicates product priority, not proven causal importance.

## Mechanistic report

- **Sleep pressure / circadian timing:** informed by reported sleep, sleepiness and sleep quality. The app describes a sleep-related pattern; it does not estimate adenosine concentration or measure circadian phase.
- **Cognitive fatigue / sustained attention:** informed by self-reported fatigue, clarity and elapsed work time. It is not a direct measure of cognitive capacity.
- **Reward-cue pull / “wanting”:** informed by stimulation craving. Dopamine research distinguishes incentive salience (“wanting”) from pleasure (“liking”), but an urge does not establish high/low dopamine or a dopamine deficit.
- **Stress/arousal and physical restlessness:** separately informed by stress and restlessness ratings. No cortisol, norepinephrine or autonomic value is inferred.
- **Physical needs:** the app acts on the need reported, then uses reassessment to see if the target symptom changes.
- **Task-start friction:** suggested where task readiness is very low and no higher-priority pattern dominates.

Pattern labels indicate how clearly reported answers fit the observable pattern. They are not probabilities of a neurochemical explanation.

## Personal feedback

Post-action reassessment stores the targeted symptom before and after, perceived helpfulness, note and action code. This supports within-person observation, but the app does not automatically retrain thresholds or infer causation. Time, expectation, context, natural fluctuation and regression to the mean can affect the change.

## Main evidence anchors

- Adult sleep recommendation consensus (≥7 hours regularly for most adults): https://pmc.ncbi.nlm.nih.gov/articles/PMC4434546/
- Sleep restriction meta-analysis (44 studies; sleepiness and sustained attention): https://pubmed.ncbi.nlm.nih.gov/38759474/
- Nap duration / sleep inertia (CDC/NIOSH): https://www.cdc.gov/niosh/work-hour-training-for-nurses/longhours/mod7/05.html
- Microbreak meta-analysis (19 records, 22 samples, N=2,335; fatigue/vigor improved modestly, overall performance not significantly): https://pmc.ncbi.nlm.nih.gov/articles/PMC9432722/
- Breathwork RCT meta-analysis (12 stress trials, N=785; small-to-medium average self-reported stress effect, with study limitations): https://pubmed.ncbi.nlm.nih.gov/36624160/
- Brief mindfulness induction meta-analysis (34 studies, N=3,524; small overall cognitive effect and methodological limitations): https://pubmed.ncbi.nlm.nih.gov/32739799/
- Acute exercise meta-review (30 systematic reviews/meta-analyses, 383 unique studies, N=18,347; small-to-medium average cognitive effect): https://pubmed.ncbi.nlm.nih.gov/39883421/
- Dopamine, incentive salience and wanting vs liking: https://pubmed.ncbi.nlm.nih.gov/9858756/

These studies support general mechanisms and broad intervention choices; they do not validate this app's formula or guarantee that a given action will work for a particular user.
