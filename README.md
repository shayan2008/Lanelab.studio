# LaneLab

Swimming software for coaches and athletes: practice planning, race analysis, and AI coaching in one workspace.

Live at **[lanelab.studio](https://lanelab.studio)**.

I built LaneLab as a competitive swimmer and coach: the planning, split analysis and set-writing work that normally happens across a whiteboard, a stopwatch and three spreadsheets, in one place.

## What it does

| Area | Detail |
| --- | --- |
| Race intelligence | Event and race reference data, split analysis, scoring, LCM / SCM / SCY course conversions |
| Strategy planner | Pacing and split plans from athlete inputs, with separate coach and athlete views and PDF export |
| Practice builder | Session building, lane plans and deck sheets |
| AI coaching | Coach chat, swim-set analysis and image-based set input, powered by Gemini |
| Season calendar | Planning across a training cycle |

## Stack

| Layer | Technology |
| --- | --- |
| Framework | Next.js 16, React 19, React Server Components |
| Build | Vite 8, TypeScript 5.9 |
| Runtime | Cloudflare Workers |
| Database | Cloudflare D1 with Drizzle ORM |
| AI | Google Gemini (`@google/genai`) |
| UI | Tailwind CSS 4, Motion, Lucide |
| Documents | pdf-lib for report and deck-sheet export |

## Development

```bash
npm run install:ci   # install
npm run dev          # local dev server
npm run build        # verified production build
npm test             # build + race intelligence + AI policy + render tests
```

Deploy and database:

```bash
npm run deploy:cloudflare
npm run db:generate           # generate migrations from schema
npm run db:migrate:local      # apply locally
npm run db:migrate:remote     # apply to the deployed D1 database
```

Copy `.env.example` and `.dev.vars.example` before running locally.

## Testing

The suite covers more than smoke tests: `test:race` checks the race-intelligence maths (conversions, split arithmetic, scoring), and `test:ai-policy` enforces guardrails on what the coaching model is allowed to assert, because a coaching tool that invents training advice is worse than no tool.

## Project

Entered in CAYIA 2026. Engineering and coaching workflow by [Shayan Doroudiani](https://github.com/shayan2008); product, design and commercialisation by Yichen Liu.
