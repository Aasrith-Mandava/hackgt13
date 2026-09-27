# Insight Rx demo script · Team CodePaws (3-minute cut)

HackGT 13 · Impiricus challenge · Aasrith Mandava

**[InsightRx_CodePaws_demo.mp4](InsightRx_CodePaws_demo.mp4)**: 3:09 (189.3 s), 1920×1080, 30 fps, captions burned in, plus [InsightRx_CodePaws_demo.srt](InsightRx_CodePaws_demo.srt). Poster: [InsightRx_CodePaws_poster.jpg](InsightRx_CodePaws_poster.jpg).

- **Live, not mocked:** Chrome, driven by Playwright, on the deployed app (https://insightrx-hcp.vercel.app), with the live GPU vision model. The clicks, typing and account switches are real. Waits for the model, Gemini and page loads are cut, and silent on-screen action plays at 1.9×.
- **Voice:** xAI Grok text-to-speech, voice `rex`, 1.12× speed, 158 s of narration. Every line was checked with Whisper speech recognition.
- **Shape:** a cold open on the live heatmap, then **01 Screen → 02 Discover → 03 Engage → 04 Sponsors, live**, then impact and credits. A "● LIVE · chapter" tag marks every live-app shot.

## Shot list and narration

| # | Time | Chapter | On screen | Narration |
|---|------|---------|-----------|-----------|
| 1 | 0:00 | Live | **Cold open (live footage):** attention heatmaps appear on both eyes of a real patient | This heatmap came from a phone photo of a real patient's eye, read live by our model moments ago. |
| 2 | 0:06 | · | **Title card:** Team CodePaws · Aasrith Mandava | I'm Aasrith Mandava from team CodePaws. Insight Rx turns one eye photo into what to treat, which drug to target, and who to engage. |
| 3 | 0:15 | · | **Architecture card:** Vercel/FastAPI → Neon; Cloudflare Tunnel → GPU; Hugging Face ONNX; five sponsor integrations | Built at HackGT 13: FastAPI on Vercel and Neon, retinal models on a live GPU through a Cloudflare tunnel, and five sponsor integrations. |
| 4 | 0:26 | 01 Screen | **Sign-in:** hover specialist, coordinator and manufacturer-desk roles, then sign in as *Dr. Alex Morgan* | Every role sees only what it should, from screeners to specialists to a manufacturer desk. I'm Dr. Alex Morgan, primary care. |
| 5 | 0:34 | 01 Screen | **Screen:** upload both eyes, age 64, tick semaglutide and pioglitazone, *Vision model live*, press *Screen* (the GPU wait is trimmed) | Two phone photos of the retina, the patient's age and medicines, and our fine-tuned DINOv2 ensemble reads them on a live GPU. |
| 6 | 0:43 | 01 Screen | **Result:** quality gate, referable DR in both eyes, grade probabilities, macular-edema signal; switch on the attention maps | After a quality gate: referable diabetic retinopathy in both eyes, with grades, an edema signal, and an AUROC of 0.98 on unseen patients. |
| 7 | 0:53 | 02 Discover | **Whole-body view** (evidence tiers) → **every systemic condition** with what moved it | The same photos score heart, kidneys, nerves and metabolism, each with its evidence tier and what moved it. |
| 8 | 1:00 | 02 Discover | **Treatment considerations:** the two *Major* interaction alerts | Guideline therapy follows, with eye-specific alerts: semaglutide with retinopathy, pioglitazone with edema. |
| 9 | 1:08 | 02 Discover | **Targets → VEGF-A:** ranked targets, PDB 1CZ8 drug complex in 3D → *AlphaFold* view (pLDDT colours), structure insights: 21 contact residues, confidence 95 | Then personalised protein targets. The top one, VEGF-A, opens in its real PDB structure. Flip to AlphaFold, and the 21 drug-contact residues score 95 out of 100. |
| 10 | 1:27 | 02 Discover | **Therapeutics explorer** by organ → *Portfolio report (PDF)* | The explorer and portfolio report show pharma where eye-detected demand meets open drug space. |
| 11 | 1:33 | 03 Engage | **Save patient & consult:** your reading → *Dr. Priya Nair* → attest → *Sign & send consultation* | One click saves the patient: confirm the reading, pick the specialist, then sign and send a package sealed with a SHA-256 signature. |
| 12 | 1:43 | 03 Engage | **Switch to Dr. Priya Nair:** open the referral → *Accept consultation*; relay now with Taylor Brooks (coordinator) | The retina specialist accepts, and the relay hands the case to the coordinator. |
| 13 | 1:49 | 03 Engage | **Refer out:** CMS NPI Registry search → *Referral letter* | Outside the network? Real clinicians from the CMS NPI Registry, with a referral letter. |
| 14 | 1:55 | 03 Engage | **Ask the manufacturer** from a therapy option → **switch to Morgan Lee, PharmD:** the desk sees only the question and a de-identified context | Manufacturer questions cross a firewall: the desk sees an age band and findings, never the patient. |
| 15 | 2:02 | 04 Sponsors, live | **Copilot:** Backboard memory panel → ask about semaglutide follow-up → Gemini's cited answer, tailored to the remembered habit (*Remembered* and *Sources* chips) | Now the sponsors, live. The Copilot's memory runs on Backboard, and Gemini writes a cited answer that uses my own follow-up habit. |
| 16 | 2:11 | 04 Sponsors, live | **Explain to patient:** English → *Português (Brasil)* → play (the real ElevenLabs voice) | Gemini rewrites the result for the patient in English or Portuguese, and ElevenLabs reads it aloud. |
| 17 | 2:21 | 04 Sponsors, live | **Finding trends:** 30-day series, *Source: Tiger Data continuous aggregate* | Every screening streams de-identified findings into a Tiger Data hypertable with a continuous aggregate. |
| 18 | 2:28 | 04 Sponsors, live | **CMS quality and billing:** CMS131 / HEDIS EED, CPT 92228 | Each physician-read screen closes a CMS eye-exam gap and bills CPT 92228. |
| 19 | 2:35 | 04 Sponsors, live | **Audit trail:** model run, signed review, consultation package | And every signature lands in an append-only audit trail, ready to anchor on Solana's Memo program. |
| 20 | 2:42 | · | **Impact card:** per 10,000 patients: 3,520 gaps, $304K in reads, 2,600 found | Per ten thousand patients: about 3,500 exam gaps closed, $300,000 in billable reads, and 2,600 people with retinopathy found. |
| 21 | 2:52 | · | **Sponsor card:** each technology and how it is used | Gemini explains, ElevenLabs speaks, Backboard remembers, Tiger Data tracks, Solana proves, and Grok voiced this video. |
| 22 | 3:01 | · | **Closing card** | Insight Rx, by team CodePaws: one eye photo, the right therapy, the right physician. |

## Every feature, and where it appears

| Feature | Time |
|---|---|
| Role-based sign-in (screeners, clinicians, specialists, coordinator, manufacturer desk) | 0:26 |
| Two-eye screening with patient details and medicines, live GPU model | 0:34 |
| Quality gate, referable DR, grades, macular edema, attention maps, AUROC 0.98 | 0:00, 0:43 |
| Whole-body oculomics with evidence tiers and score drivers | 0:53 |
| Guideline therapy and eye-specific drug-safety alerts | 1:00 |
| Personalised protein-target ranking; VEGF-A in PDB and AlphaFold; drug-contact residues | 1:08 |
| Therapeutics explorer and portfolio report | 1:27 |
| Save, three-step consult, SHA-256-signed package | 1:33 |
| Specialist inbox, accept, referral relay to the coordinator | 1:43 |
| CMS NPI Registry referral letter | 1:49 |
| Medical-information firewall (manufacturer desk) | 1:55 |
| Copilot: Backboard memory + Gemini cited answers | 2:02 |
| Patient explainer: Gemini (EN/PT) + ElevenLabs voice | 2:11 |
| Finding trends on Tiger Data | 2:21 |
| CMS quality measures and CPT 92228 billing | 2:28 |
| Append-only audit trail and signatures (Solana anchoring) | 2:35 |
| Impact per 10,000 patients; sponsor recap | 2:42 |


## Sponsor technologies

| Technology | What it does in Insight Rx | Shown |
|---|---|---|
| **Backboard.io** (MLH) | Per-clinician Copilot memory, visible and deletable, used in answers | Live |
| **Google Gemini** (MLH) | Cited Copilot answers; plain-language patient explainer (EN / PT-BR) with a no-new-numbers guard | Live |
| **ElevenLabs** (MLH) | Multilingual read-aloud of the explainer (the real audio is in the video) | Live |
| **Tiger Data** (MLH) | TimescaleDB hypertable and continuous aggregate of de-identified findings | Live |
| **Solana** (MLH) | SHA-256 digest of signed reviews and consultations on the Memo program | Anchoring is off in this deployment, so the narration says "ready to anchor" |
| **Vercel + Neon**, **Cloudflare Tunnel**, **Hugging Face** | Hosting and database, the GPU path, the portable ONNX bundle | Live / described |
| **xAI Grok** | Narration voice | Live |
