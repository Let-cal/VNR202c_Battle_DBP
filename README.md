# VNR202c — Battle of Dien Bien Phu

A one-page, scroll-based site about the 1954 Battle of Dien Bien Phu, made for the FPT University course VNR202c (History of the Communist Party of Vietnam). The content is in Vietnamese.

**Status:** Course project, FPT University, December 2024 — archived. The demo deployment is offline.

## My role

Team Lead and front-end developer. In this repository I built:

- Project setup (Next.js, TypeScript, Tailwind CSS).
- The historical context section: the slide sequence on the background of the battle and the phases of the attack.
- Reusable horizontal-scroll and swipe-grid components.
- The Lenis smooth-scroll hook.

## Team

Commits in this repository: [@Let-cal](https://github.com/Let-cal), [@tthienduc13](https://github.com/tthienduc13) (layout, sidebar, leaders, summary, victory and Q&A sections) and [@Kiamng](https://github.com/Kiamng) (strategy section).

## Stack

Next.js 14, React 18, TypeScript, Tailwind CSS, GSAP, Framer Motion, Lenis, tsParticles, Zustand, Google Generative AI SDK (Gemini).

## Features

- Sections: victory hero, historical context, phases of the attack, strategy, leaders, summary.
- Horizontal scrolling and animated transitions between sections.
- **Q&A section:** the visitor picks one of four preset history questions; the page sends it to Gemini (`gemini-1.5-flash`) and shows the answer.

## How to run

Requires Node.js 18 or newer.

```sh
npm ci
npm run dev        # http://localhost:3000
```

The Q&A section needs your own Gemini API key. Create `.env.local`:

```sh
NEXT_PUBLIC_API_KEY=your-gemini-api-key
```

## Known limitations

- **The API key is exposed to the browser.** Any variable starting with `NEXT_PUBLIC_` is bundled into the client code, and `components/ai-chat/index.tsx` calls Gemini from the browser. Anyone who opens the site can read the key. Before deploying, move the call into a server route (for example `app/api/ask/route.ts`) that reads a server-only variable.
- The model name `gemini-1.5-flash` is hard-coded. If Google has retired it, change it to a current model.
- The demo deployment is offline.
- No automated tests.
