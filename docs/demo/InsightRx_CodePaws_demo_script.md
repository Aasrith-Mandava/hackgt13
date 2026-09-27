# Insight Rx demo script · Team CodePaws

HackGT 13 · Aasrith Mandava

**[InsightRx_CodePaws_demo.mp4](InsightRx_CodePaws_demo.mp4)**: 3:09 (189.5 s), 1920×1080, 30 fps, captions burned in, plus [InsightRx_CodePaws_demo.srt](InsightRx_CodePaws_demo.srt). Poster: [InsightRx_CodePaws_poster.jpg](InsightRx_CodePaws_poster.jpg).

The video names no hackathon challenge or track, so it can go with any submission.

- **Live, not mocked:** Chrome, driven by Playwright, on the deployed app (https://insightrx-hcp.vercel.app), with the live GPU vision model. The clicks, typing and account switches are real. Waits for the model, Gemini and page loads are cut, and silent on-screen action plays at 2.3×.
- **Voice:** xAI Grok text-to-speech, voice `rex`, 1.18× speed, 161 s of narration. Every line was checked with Whisper speech recognition.
- **Shape:** a cold open on the live heatmap, then **01 Screen → 02 Discover → 03 Engage → 04 Under the hood**, then impact and credits. A "● LIVE · chapter" tag marks every live-app shot.

## The approach, as the video explains it

| Technical piece | Plain-words line in the video |
|---|---|
| DINOv2 foundation model, fine-tuned (LoRA ensemble) on real mBRSET retinas | "builds on DINOv2, a vision AI that learned from millions of images, then taught to read retinas" |
| Image quality gate; AUROC 0.98 on held-out patients | "after a quality check… shown a sick and a healthy eye, it picks right 98 times in 100" |
| Attention maps | "marking exactly where it saw disease" |
| Second (systemic) model with release gates and evidence tiers | "a second model flags heart, kidney and nerve risks, each with a trust label" |
| Target ranking by evidence, guidelines and binding-site confidence | "ranks the proteins behind this disease by evidence, guidelines and drug-site certainty" |
| PDB drug-contact residues at 4.5 Å; AlphaFold pLDDT at that site | "the drug touches 21 spots, and AlphaFold is 95 out of 100 confident about them" |
| SHA-256 signature of the case, images, model run and reading | "a SHA-256 fingerprint exposes any later change" |
| Retrieval-grounded answers (RAG) + per-clinician memory | "looks up guideline passages first, then Gemini writes a cited answer, and Backboard's memory keeps it true to my habits" |
| Guarded plain-language rewrite + multilingual text-to-speech | "in the patient's own language, never adding numbers or names… multilingual voice reads it aloud" |
| TimescaleDB hypertable + continuous aggregate | "a time-series database that rolls findings up daily, so trends update themselves" |
| Audit trail + Solana Memo anchoring | "a tamper-evident audit trail, ready to stamp its fingerprint on the Solana blockchain" |

## Shot list and narration

| # | Time | Chapter | On screen | Narration |
|---|------|---------|-----------|-----------|
| 1 | 0:00 | Live | **Cold open (live footage):** AI heatmaps appear on both eyes of a real patient | Our AI drew this heatmap live from a phone photo of a real eye, marking exactly where it saw disease. |
| 2 | 0:06 | · | **Title card:** Team CodePaws · Aasrith Mandava | I'm Aasrith Mandava from team CodePaws. At HackGT 13 we built Insight Rx: one photo of the eye becomes a treatment plan, a drug target and a referral. |
| 3 | 0:16 | · | **Architecture card:** web app on Vercel + Neon; AI on a GPU through a Cloudflare tunnel; portable ONNX models on Hugging Face; five smart services | Under the hood: a web app on Vercel and Neon, our AI on a real GPU through a secure Cloudflare tunnel, plus five smart services. |
| 4 | 0:25 | 01 Screen | **Sign-in:** the role picker; sign in as *Dr. Alex Morgan* (family doctor) | Every role gets its own login and sees only what it should. I'm Dr. Alex Morgan, a family doctor. |
| 5 | 0:31 | 01 Screen | **Screen:** upload both eyes, age 64, tick semaglutide and pioglitazone, *Vision model live*, press *Screen* (the GPU wait is trimmed) | One phone photo per eye, the patient's age and medicines, and it's off to our model on the GPU. |
| 6 | 0:36 | 01 Screen | **Result:** switch on the attention heatmaps → verdict summary: referable DR in both eyes, grade probabilities, macular-edema signal | Our model builds on DINOv2, a vision AI that learned from millions of images, then taught to read retinas. After a quality check: disease needing a specialist, in both eyes. Shown a sick and a healthy eye, it picks right 98 times in 100. |
| 7 | 0:51 | 02 Discover | **Whole-body view** with trust labels → every systemic condition and what moved its score | Eye vessels mirror the body, so a second model flags heart, kidney and nerve risks, each with a trust label. |
| 8 | 0:57 | 02 Discover | **Treatment considerations:** the two eye-specific *Major* interaction alerts | Guideline treatments are checked against current medicines, catching two eye-specific risks: semaglutide and pioglitazone. |
| 9 | 1:04 | 02 Discover | **Target ranking → VEGF-A:** PDB drug complex in 3D → *AlphaFold* view (colours = confidence) → structure insights: 21 contact residues, confidence 95 | Then it ranks the proteins behind this disease by evidence, guidelines and drug-site certainty. Top pick: VEGF-A, which makes vessels leak, shown in 3D. Flip to DeepMind's AlphaFold: the drug touches 21 spots, and AlphaFold is 95 out of 100 confident about them. |
| 10 | 1:28 | 02 Discover | **Therapeutics explorer** by organ → portfolio report | Across patients, the explorer shows drug makers where eye-detected demand meets few existing drugs. |
| 11 | 1:34 | 03 Engage | **Save patient & consult:** your reading → *Dr. Priya Nair* → attest → *Sign & send* (SHA-256 fingerprint) | One click saves the patient and starts a consult: confirm, pick a specialist, sign. A SHA-256 fingerprint exposes any later change. |
| 12 | 1:45 | 03 Engage | **Switch to Dr. Priya Nair:** open the referral → *Accept consultation*; the relay passes to the coordinator | The retina specialist accepts, and the next step passes to the care coordinator. |
| 13 | 1:51 | 03 Engage | **Refer out:** national NPI registry search → *Referral letter* | Outside the network? Real doctors from the national NPI registry, plus a ready referral letter. |
| 14 | 1:56 | 03 Engage | **Ask the drug maker** from a therapy option → **switch to the manufacturer desk:** question plus de-identified context only | Drug-maker questions pass a firewall: they see an age range and findings, never the patient. |
| 15 | 2:03 | 04 Under the hood | **Copilot:** memory panel → a typed question → a cited answer tailored to the remembered habit | The Copilot looks up guideline passages first, then Gemini writes a cited answer, and Backboard's memory keeps it true to my habits. |
| 16 | 2:11 | 04 Under the hood | **Explain to patient:** plain-language note → another language tab → play (the real ElevenLabs voice) | Gemini rewrites it in plain words in the patient's own language, never adding numbers or names, and ElevenLabs' multilingual voice reads it aloud. |
| 17 | 2:23 | 04 Under the hood | **Finding trends:** 30-day series from the Tiger Data continuous aggregate | Every screening feeds a Tiger Data time-series database that rolls findings up daily, so trends update themselves. |
| 18 | 2:29 | 04 Under the hood | **Medicare quality and billing:** CMS131 / HEDIS EED, code 92228 | And it pays for itself: each screen read by a doctor closes a Medicare quality gap and bills code 92228. |
| 19 | 2:37 | 04 Under the hood | **Audit trail:** model run, signed review, consultation package, each with its fingerprint | Every action lands in a tamper-evident audit trail, ready to stamp its fingerprint on the Solana blockchain. |
| 20 | 2:43 | · | **Impact card:** per 10,000 patients: 3,520 gaps, $304K in reads, 2,600 found | Per ten thousand patients: about 3,500 missed exams closed, $300,000 in billable reads, 2,600 people with eye disease found. |
| 21 | 2:53 | · | **Technology card:** each service and how it is used | Gemini explains, ElevenLabs speaks, Backboard remembers, Tiger Data tracks, Solana keeps records honest, and Grok voiced this video. |
| 22 | 3:02 | · | **Closing card** | Insight Rx, by team CodePaws: one eye photo, the right treatment, the right doctor. |

## Every feature, and where it appears

| Feature | Time |
|---|---|
| Role-based sign-in | 0:25 |
| Two-eye screening with patient details and medicines, live GPU model | 0:31 |
| Quality gate, referable DR, grades, macular edema, attention maps, accuracy | 0:00, 0:36 |
| Whole-body risk signals with trust labels and score drivers | 0:51 |
| Guideline therapy and eye-specific drug-safety alerts | 0:57 |
| Protein-target ranking; VEGF-A in PDB and AlphaFold; drug-contact residues | 1:04 |
| Therapeutics explorer and portfolio report | 1:28 |
| Save, three-step consult, SHA-256-signed package | 1:34 |
| Specialist inbox, accept, relay to the coordinator | 1:45 |
| National NPI registry referral letter | 1:51 |
| Drug-maker question firewall (manufacturer desk) | 1:56 |
| Copilot: retrieval + Gemini answers, Backboard memory | 2:03 |
| Patient explainer in the patient's own language, read aloud by ElevenLabs | 2:11 |
| Finding trends on Tiger Data | 2:23 |
| Medicare quality measures and billing | 2:29 |
| Tamper-evident audit trail (Solana-ready) | 2:37 |
| Impact per 10,000 patients; technology recap | 2:43 |

## Technology

| Service | What it does in Insight Rx | In this take |
|---|---|---|
| **Google Gemini** | Cited Copilot answers; guarded plain-language patient explainer in the patient's language | Live |
| **ElevenLabs** | Multilingual read-aloud of the explainer (the real audio is in the video) | Live |
| **Backboard.io** | Per-clinician Copilot memory, visible and deletable | Live |
| **Tiger Data** | TimescaleDB hypertable and continuous aggregate of de-identified findings | Live |
| **Solana** | SHA-256 digests of signed reviews and consultations on the Memo program | Anchoring is off in this deployment, so the narration says "ready to stamp" |
| **Vercel + Neon**, **Cloudflare Tunnel**, **Hugging Face** | Hosting and database, the GPU path, the portable ONNX bundle | Live / described |
| **xAI Grok** | Narration voice | Live |
