# Insight Rx demo script · Team CodePaws

HackGT 13 · Aasrith Mandava

**[InsightRx_CodePaws_demo.mp4](InsightRx_CodePaws_demo.mp4)**: 3:40 (220.9 s), 1920×1080, 30 fps, captions burned in, plus [InsightRx_CodePaws_demo.srt](InsightRx_CodePaws_demo.srt). Poster: [InsightRx_CodePaws_poster.jpg](InsightRx_CodePaws_poster.jpg).

The video names no hackathon challenge or track, so it can go with any submission.

- **Story:** the problem → what Insight Rx is → why it matters to healthcare providers (HCPs) → how it is built → a live walkthrough (**01 Screen → 02 Discover → 03 Engage HCPs → 04 Under the hood**) → impact → the stack.
- **Live, in real time:** Chrome, driven by Playwright, on the deployed app (https://insightrx-hcp.vercel.app), with the live GPU vision model. Nothing is fast-forwarded. Only loading waits and still, silent frames are trimmed, with a short cross-fade.
- **Voice:** xAI Grok text-to-speech, voice `rex`, 1.18× speed, 183 s of narration. Every line was checked with Whisper speech recognition.

## The HCP angle

| Who | What Insight Rx gives them | Where in the video |
|---|---|---|
| Family doctor (referring HCP) | A screening, a verdict and a treatment plan during the visit | 0:50 to 1:27 |
| Specialist (receiving HCP) | A complete, signed consult, accepted in one click, relayed to the coordinator | 1:55, 2:09 |
| Out-of-network HCPs | Real clinicians from the national NPI registry, with a referral letter | 2:16 |
| Life-science teams | Eye-detected demand per target, and HCP questions through a de-identified firewall at the moment therapy is decided | 1:50, 2:22 |

## The approach, as the video explains it

| Technical piece | Plain-words line in the video |
|---|---|
| DINOv2 foundation model, fine-tuned (LoRA ensemble) on real mBRSET retinas | "a vision AI trained on millions of images, fine-tuned to read retinas" |
| Image quality gate; AUROC 0.98 on held-out patients | "after a quality check… shown a sick and a healthy eye, it's right 98 times in 100" |
| Attention maps | "here's where it looked" |
| Second (systemic) model with release gates and evidence tiers | "a second model flags heart, kidney and nerve risks, each with a trust label" |
| Target ranking by evidence, guidelines and binding-site confidence | "ranks the proteins behind this disease by evidence, guidelines and drug-site certainty" |
| PDB drug-contact residues at 4.5 Å; AlphaFold pLDDT at that site | "the drug touches 21 spots, and AlphaFold is 95 out of 100 confident about them" |
| SHA-256 signature of the case, images, model run and reading | "sealed with a SHA-256 fingerprint" |
| Retrieval-grounded answers (RAG) + per-clinician memory | "looks up guidelines first, then Gemini writes a cited answer, and Backboard's memory keeps it true to my habits" |
| Guarded plain-language rewrite + multilingual text-to-speech | "in the patient's own language, never adding numbers or names… multilingual voice reads it aloud" |
| TimescaleDB hypertable + continuous aggregate | "a time-series database that rolls findings up daily, automatically" |
| Audit trail + Solana Memo anchoring | "a tamper-evident audit trail, ready to stamp its fingerprint on the Solana blockchain" |

## Shot list and narration

| # | Time | Chapter | On screen | Narration |
|---|------|---------|-----------|-----------|
| 1 | 0:00 | · | **The problem:** #1 cause of blindness in working-age adults; 26% of people with diabetes affected; 35% skip the yearly eye exam | Diabetic eye disease is the top cause of blindness in working-age adults. One in four people with diabetes has it, yet a third skip their yearly exam, and most photos of the eye end up as a line in a chart. |
| 2 | 0:11 | · | **What Insight Rx is:** one eye photo → what to treat, which drug target, who to call · Team CodePaws | I'm Aasrith Mandava from team CodePaws. At HackGT 13 we built Insight Rx: one photo of the eye becomes what to treat, which drug to target, and who to call. |
| 3 | 0:22 | · | **Built for HCPs:** the family doctor decides in the visit · the specialist gets a signed consult · life-science teams reach the right HCP, with no cold outreach | It's built for healthcare providers, or HCPs: the family doctor decides in the visit; the specialist gets a complete, signed consult. Drug makers reach the right HCP when therapy is decided, with no cold outreach. |
| 4 | 0:36 | · | **How it is built:** a web app on Vercel + Neon; AI on a GPU through a Cloudflare tunnel; portable ONNX models; five smart services | Under the hood: a web app on Vercel and Neon, our AI on a live GPU through a Cloudflare tunnel, and five smart services. |
| 5 | 0:44 | 01 Screen | **Sign-in:** the role picker; sign in as *Dr. Alex Morgan* (family doctor) | Every role has its own login and sees only what it should. I'm Dr. Alex Morgan, a family doctor. |
| 6 | 0:50 | 01 Screen | **Screen:** upload both eyes, age 64, tick semaglutide and pioglitazone, *Vision model live*, press *Screen* | I add a phone photo of each eye, the age and current medicines, and send them to our GPU model. |
| 7 | 0:57 | 01 Screen | **Result:** attention heatmaps on both eyes → verdict: referable DR in both eyes, grades, macular-edema signal | It builds on DINOv2, a vision AI trained on millions of images, fine-tuned to read retinas. Here's where it looked. After a quality check: disease needing a specialist, in both eyes. Shown a sick and a healthy eye, it's right 98 times in 100. |
| 8 | 1:13 | 02 Discover | **Whole-body view** with trust labels → every systemic condition and what moved it | Eye vessels mirror the body, so a second model flags heart, kidney and nerve risks, each with a trust label. |
| 9 | 1:19 | 02 Discover | **Treatment considerations:** two eye-specific *Major* interaction alerts | Guideline treatments are checked against current medicines, catching two eye-specific risks: semaglutide and pioglitazone. |
| 10 | 1:27 | 02 Discover | **Target ranking → VEGF-A:** PDB drug complex in 3D → *AlphaFold* view (colours = confidence) → 21 drug-contact residues, confidence 95 | Next, it ranks the proteins behind this disease by evidence, guidelines and drug-site certainty. Top pick: VEGF-A, which makes vessels leak. Flip to DeepMind's AlphaFold: the drug touches 21 spots, and AlphaFold is 95 out of 100 confident about them. |
| 11 | 1:50 | 02 Discover | **Therapeutics explorer** by organ → portfolio report | Across patients, the explorer shows drug makers where eye-detected demand meets few existing drugs. |
| 12 | 1:55 | 03 Engage HCPs | **HCP-to-HCP consult:** save the patient → your reading → *Dr. Priya Nair* → attest → *Sign & send* | Now the HCP-to-HCP handoff: one click saves the patient and opens a consult. Confirm, pick a specialist, sign, sealed with a SHA-256 fingerprint. |
| 13 | 2:09 | 03 Engage HCPs | **Switch to Dr. Priya Nair:** open the referral → *Accept consultation*; the relay passes to the coordinator | The retina specialist accepts it, and the next step passes to the care coordinator. |
| 14 | 2:16 | 03 Engage HCPs | **Refer out:** national NPI registry search → *Referral letter* | Outside the network? Real doctors from the national NPI registry, with a referral letter. |
| 15 | 2:22 | 03 Engage HCPs | **HCP → drug-maker question:** asked from a therapy option; the request carries only a de-identified context behind the firewall | When an HCP asks a drug maker a question, a firewall shows them an age range and findings, never the patient. |
| 16 | 2:31 | 04 Under the hood | **Copilot:** memory panel → a typed question → a cited answer tailored to the remembered habit | The Copilot looks up guidelines first, then Gemini writes a cited answer, and Backboard's memory keeps it true to my habits. |
| 17 | 2:40 | 04 Under the hood | **Explain to patient:** plain-language note → another language tab → play (the real ElevenLabs voice) | Gemini rewrites the result in plain words in the patient's own language, never adding numbers or names, and ElevenLabs' multilingual voice reads it aloud. |
| 18 | 2:52 | 04 Under the hood | **Finding trends:** 30-day series from the Tiger Data continuous aggregate | Every screening feeds a Tiger Data time-series database that rolls findings up daily, automatically. |
| 19 | 2:58 | 04 Under the hood | **Medicare quality and billing:** CMS131 / HEDIS EED, code 92228 | And it pays for itself: each screen read by a doctor closes a Medicare quality gap and bills code 92228. |
| 20 | 3:05 | 04 Under the hood | **Audit trail:** model run, signed review, consultation package, each with its fingerprint | Every action lands in a tamper-evident audit trail, ready to stamp its fingerprint on the Solana blockchain. |
| 21 | 3:11 | · | **Impact card:** per 10,000 patients: 3,520 gaps, $304K in reads, 2,600 found | Per ten thousand patients: about 3,500 missed exams closed, $300,000 in billable reads, and 2,600 people with eye disease found. |
| 22 | 3:22 | · | **Technology card:** each service and how it is used | Gemini explains, ElevenLabs speaks, Backboard remembers, Tiger Data tracks, Solana keeps records honest, and Grok voiced this video. |
| 23 | 3:31 | · | **Closing card:** HCP engagement, triggered by a clinical signal | Insight Rx: HCP engagement, triggered by a clinical signal. One eye photo, the right treatment, the right doctor. |

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
