# Mental State OS v2.1

A free, static web app for repeated check-ins on sleepiness, cognitive fatigue, thinking clarity, stimulation craving, stress, physical sluggishness/restlessness, recovery and task readiness.

## What's new in v2.1

- **Answers persist between check-ins.** The latest form values are saved as you change them and pre-filled on the next check-in. This includes sleep figures, ratings, context, physical-need selections and optional work/break clock times. Update only what has changed. On a new local calendar day, sleep duration, sleep quality, wake time and work/break clock times reset for a fresh daily entry; other ratings remain pre-filled for review.
- **Automatic elapsed time.** Enter what time you got out of bed; the app computes time awake from the current local clock. Optional work-start and last-break times compute the active work stretch and time since break. Quick buttons set those times to now. Midnight crossing is handled.
- **Separate physical sluggishness and physical restlessness.** These can imply different actions, so they are no longer combined into one ambiguous question.
- **Action-first report.** The selected action appears before the full score grid, explains which signal caused the rule to win, and links to a supporting research source when available.
- **Evidence-linked interpretations.** Report hypotheses distinguish sleep pressure, cognitive fatigue, reward-cue pull, stress/arousal, physical needs and task-start friction.
- **Less intrusive caveats.** Method limitations are in a collapsed section instead of dominating the report. No claims are made about actual dopamine or other neurotransmitter levels.
- **Legacy history support.** Existing records remain available; saved reports are recalculated with the updated v2.1 rules when needed. Old records do not pretend to contain the new physical-restlessness rating.
- **Export improvements.** JSON backup and CSV export include wake/work/break times and the new rating.

## Files

- `index.html` — complete app with no build tools or external runtime dependencies.
- `LOGIC.md` — formulas, action routing, data flow and boundaries.
- `EVIDENCE.md` — evidence summary and interpretation of the research that informs the action rules.
- `CHANGELOG.md` — what changed in v2.1.

## Run locally

Open `index.html` in a modern browser. Local browser storage works best when served from a static server or a hosted site.

## Publish on GitHub Pages

1. Create a repository on GitHub. The free GitHub Pages configuration generally uses a public repository.
2. Upload the contents of this folder (`index.html`, `README.md`, `LOGIC.md`, `EVIDENCE.md`) to the repository root.
3. Open **Settings → Pages**.
4. Under build and deployment, select **Deploy from a branch**, choose `main` and `/(root)`, then save.
5. Open the URL shown in Pages settings after deployment completes. Bookmark it or add it to your phone's home screen.

Official instructions: https://docs.github.com/en/pages/getting-started-with-github-pages

## Privacy

- There is no server-side database, login, analytics script, advertising script or AI API.
- Check-ins are saved using browser `localStorage` for the exact site origin and browser profile used. Preferences auto-save as you edit the form; completed records are stored separately.
- Data does not sync across devices or browsers. Clearing site/browser data can delete it. Exported JSON/CSV files contain personal information and should be kept private.
- Anyone who can use the same browser profile may be able to inspect local history. GitHub Pages may log visitor information at the hosting layer.
- The code is visible when using a public repository. Never upload personal check-in exports to the source repository.

## Scope

This is a self-observation and decision-support tool, not a medical instrument. Its scores are self-report indices and transparent heuristics. The report can describe a pattern consistent with a mechanism; it cannot diagnose a disorder or estimate dopamine, adenosine, cortisol, norepinephrine or any other neurochemical concentration. Persistent, severe or unexplained fatigue or excessive daytime sleepiness warrants appropriate clinical assessment. Do not drive or perform safety-critical work while fighting sleep.
