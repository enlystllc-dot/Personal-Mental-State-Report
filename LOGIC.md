# Mental State OS — scoring and decision logic

## 1. Ratings collected

Eight self-report sliders run from 0 to 4:

- Sleep quality: 0 = very poor; 4 = very good.
- Sleepiness: 0 = fully alert; 4 = fighting sleep.
- Cognitive fatigue: 0 = fresh; 4 = extreme.
- Thinking clarity: 0 = very foggy; 4 = very clear.
- Task readiness: 0 = not able; 4 = ready.
- Stimulation craving: 0 = none; 4 = overwhelming.
- Stress/arousal: 0 = calm; 4 = overwhelmed.
- Physical sluggishness/restlessness: 0 = good energy; 4 = extreme.

Context fields include last night's sleep, average sleep in the last three nights, hours awake, reported physical needs, work-stretch duration, time since the last meaningful break, recent activity and optional notes.

## 2. Display scores

Most 0–4 ratings are converted to 0–10 by multiplying by 2.5. Thinking fogginess is the reverse of clarity (4 − clarity) × 2.5. The displayed sleep recovery load is a small heuristic using sleep duration, sleep quality and sleepiness; it is explicitly not a validated sleep-debt calculation.

The 0–100 readiness index is an unvalidated arithmetic summary that subtracts weighted penalties for sleepiness, fatigue, fogginess, craving, stress, physical activation, reported physical needs and short sleep from 100. It is intended only as a convenient snapshot. The independent dimensions and action rules should take precedence over this composite number.

## 3. Action precedence

1. Severe reported sleepiness is the first safety override. The recommendation warns against driving and safety-critical tasks; rest/sleep is prioritized over stimulation or breathing exercises.
2. Reported illness symptoms prompt pausing and appropriate assessment.
3. Other reported physical needs are addressed before productivity interventions.
4. Short/restricted sleep plus sleepiness prioritizes recovery.
5. High reported stress/arousal prioritizes gentle paced breathing.
6. High stimulation craving with comparatively lower sleepiness and cognitive fatigue prioritizes phone friction, urge observation and a five-minute work start.
7. High cognitive fatigue or a long continuous work stretch prioritizes a screen-free recovery break.
8. High physical sluggishness/restlessness prioritizes brief movement.
9. Low task readiness prioritizes making the task smaller.
10. Otherwise, try a short work sprint and reassess.

These thresholds are chosen for simple, conservative routing; they have not been clinically validated. The first matched rule determines the priority action.

## 4. Neuroscience explanations

Possible underlying process labels are cautious descriptions of patterns compatible with reported symptoms. The app never computes numeric neurotransmitter estimates. In particular, dopamine level is unknown. Strong scrolling urges may be compatible with reward-cue pull, but multiple cognitive, environmental, motivational, sleep and stress processes can explain the same behavior.

## 5. Self-experiment feedback

The post-action check records the symptom to reassess, before rating, after rating, perceived helpfulness and an optional note. This can support personal reflection. It does not establish causation: time, expectation, context and regression to the mean may affect ratings.

## 6. Evidence anchors

- Adult sleep duration consensus: https://pmc.ncbi.nlm.nih.gov/articles/PMC4434546/
- NHLBI on body clock and sleep pressure: https://www.nhlbi.nih.gov/health/sleep-deprivation/body-clock
- Meta-analysis on microbreaks: https://pmc.ncbi.nlm.nih.gov/articles/PMC9432722/
- Meta-analysis on breathwork and stress: https://pubmed.ncbi.nlm.nih.gov/36624160/
- Review on dopamine, learning and motivation: https://www.nature.com/articles/nrn1406
- CDC/NIOSH on nap duration: https://www.cdc.gov/niosh/work-hour-training-for-nurses/longhours/mod7/05.html
- Meta-analysis on acute physical activity and cognition: https://pmc.ncbi.nlm.nih.gov/articles/PMC11358546/
