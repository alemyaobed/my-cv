# Projects and terms

Reference map of the work at Amazethu, written so any future session
understands what each project and internal name means, and what is safe
to say on public surfaces (README, portfolio site, CV) versus what stays
internal.

Rule of thumb: platforms and generic roles are public-safe (Render, AWS,
GitHub Actions, "the API service", "the ML conversation service").
Codenames and internal service names are not (be-app, botai, fe-web,
PCR-infra, GPS isolation).

## The platform

- Amazethu / Amaspeak (INTERNAL names): the company and its
  language-learning product. Public surfaces say "a language-learning
  platform" or nothing at all.
- be-app (INTERNAL): Node.js API service, port 4000. Public: "the main
  API service".
- botai (INTERNAL): Python ML/conversation service, port 5000, the
  heaviest compute consumer. Public: "the ML conversation service".
- fe-web (INTERNAL): React web frontend. Public: "the web frontend".
- frontend-expo (INTERNAL): Expo mobile app, out of migration scope.
- Language programs: French, Kiswahili (content review workflows cycle
  through these).

## Language tutor research

Research program into a conversational-AI language tutor (repo:
language-tutor-research, Python). This is the AI/LLM body of work.

- Testbed: local experimentation platform with a simulated backend
  (fastapi_sim mirrors the production API) for content and interaction
  engineering; two axes: content validation and interaction engineering.
- Student simulation: simulated students for evaluating tutor behavior
  before real users.
- Architectures: tutor architecture experimentation (architecture
  personalities, interaction modes, audio mode).
- CCGP (INTERNAL): content generation pipeline (hcgp generation, hqcp
  quality control) with AI contracts: AI-Lesson-Designer,
  AI-Curriculum-Designer, AI-Coding-Agent.
- kb / langs_kb: language knowledge base with an LLM reviewer
  (kb-reviewer notebook) and expert knowledge review system.
- PCR-infra (INTERNAL): content review integration workflow
  (pcri-text, PCR-infra updates); protects reviewed content.
- GPS isolation (INTERNAL): feature isolation methodology; the GPS
  isolation plan was owned and handed off to Mugisha.
- Speech: faster-whisper STT, edge-tts and ElevenLabs TTS, pregenerated
  lesson audio.
- Models: Gemini via google-genai.
- Research method: validation-first, human-AI collaboration over
  autonomy, multi-turn dialogue over batch, real user feedback loops
  (validation-discovery-framework).

## Growth and operations

- Traction / retention: retention metrics design, event cleanup
  (signup_successful vs sign-in, isNewUser gating), production traction
  sheet in Google Sheets (gspread).
- Hiring: questionnaire to 90 candidates, two-stage filtering to a pool
  of 34, technical interview process; strategy owned, execution
  delegated.
- Weekly reports: Monday cadence, chat export in
  documents/work/weekly-reports/.

## Low-cost infrastructure project

Jan 2026 onward. Full arc: AWS estate documentation (ECS Fargate, ECR,
S3, CloudWatch, API Gateway, Amplify, Secrets Manager), cost
optimization (PROD $353.26/month by Nov 2025), provider comparison
matrix (Render, Railway, Cloudflare, Fly.io, Vercel), phased migration
to Render (botai first, then be-app, then fe-web), dual Hobby
workspaces (STAG + PROD), tag-based RENDER-* GitHub Actions deploys,
keep-warm ping workflow (56 min), email alerting over webhooks,
Squarespace DNS and SSL cutover, end-to-end validation (Stripe, auth,
audio flows). Current run cost roughly $50-60/month combined.
