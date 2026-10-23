# Mental State OS

A free, static, privacy-conscious web app for structured self-observation of sleepiness, cognitive fatigue, thinking clarity, stimulation craving, stress/arousal, physical needs and perceived task readiness.

## Files

- `index.html` — complete app; no build tools or dependencies.
- `LOGIC.md` — scoring and decision-rule explanation.

## Run locally

Open `index.html` in a modern browser. Some browser security settings may affect file downloads; the app's `localStorage` works best when served from a local static server or hosted site.

## Publish on GitHub Pages

1. Create a GitHub repository. GitHub Pages on the Free plan generally requires a public repository.
2. Upload `index.html`, `README.md`, and `LOGIC.md` to the repository root.
3. Open **Settings → Pages**.
4. Under **Build and deployment**, select **Deploy from a branch**; choose the `main` branch and `/ (root)`, then save.
5. Wait for the Pages deployment to finish. GitHub shows the published URL in the Pages settings.
6. Open the published URL and run a test check-in. Bookmark the URL or add it to your phone's home screen.

GitHub's interface can change. Refer to the official instructions: https://docs.github.com/en/pages/getting-started-with-github-pages

## Privacy

- There is no server-side database, login, analytics script, external font, advertising, or AI API.
- Answers and reports are stored in `localStorage` for the exact origin (domain) and browser profile used to access the app.
- Local data does not sync automatically between devices or browsers. Clearing site/browser data can delete it.
- Anyone with access to the same browser profile may be able to inspect the history. Export files contain personal information and should be handled accordingly.
- GitHub Pages may log visitor data at the hosting layer; browser-local storage does not mean there are no platform logs.
- The repository code is visible when the repository is public. Do not put personal check-in answers, private keys, or secrets in the repository.

## Scope and limitations

This app produces **self-report indices** and **rule-based suggestions**. It does not measure brain activity, diagnose a medical or mental health condition, calculate sleep debt precisely, or estimate dopamine, adenosine, cortisol, norepinephrine or any other neurochemical level. Its confidence labels describe how directly reported answers support a behavioral interpretation—not the probability of a biochemical explanation. The scoring cutoffs and action rules are pragmatic starting heuristics, not validated clinical thresholds.

For persistent, severe or unexplained fatigue or excessive daytime sleepiness, seek appropriate clinical advice. Do not drive or perform safety-critical work while struggling to stay awake.
