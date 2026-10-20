<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset=".github/assets/hero-dark.png">
    <img src=".github/assets/hero.png" alt="record.me.at landing page" width="880">
  </picture>
</p>

<h1 align="center">record.me.at</h1>

<p align="center"><strong>Record your screen in a tab and share it behind one link.</strong></p>

<p align="center">
  <img src="https://img.shields.io/badge/status-in%20development-171717?style=flat-square" alt="Status: in development">
  <img src="https://img.shields.io/badge/license-source--available-404040?style=flat-square" alt="License: source-available">
  <img src="https://img.shields.io/badge/part%20of-me.at-737373?style=flat-square" alt="Part of me.at">
</p>

<p align="center">
  <a href="#features">Features</a> ·
  <a href="#how-it-works">How it works</a> ·
  <a href="#built-with">Built with</a>
</p>

Explaining something on a call costs everyone a meeting, and most screen recorders want a desktop app first. I built record.me.at for async screen recording: record in the browser, get a share link, see who watched. Recording runs in your browser tab, and nothing is thrown away until the server confirms the whole upload. A share link has to pass a set of checks before anyone can watch, and anything unexpected is refused.

> **Status:** in development, at an early internal stage. The record and watch pages exist, and uploads and playback need storage configured before they work.

<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset=".github/assets/overview-dark.svg">
    <img src=".github/assets/overview.svg" alt="record.me.at at a glance: records in your tab, uploads that resume, links that fail closed, see who watched" width="880">
  </picture>
</p>

## Why record.me.at

| The usual screen recorder | record.me.at |
| --- | --- |
| A desktop app to install | Records in the browser tab |
| A dropped connection loses the take | Uploads resume from the first missing part |
| A permanent file URL | Link checks on every view, then short-lived signed playback |
| View time that counts idle tabs | View time capped at the recording's own length |

## Features

- **Browser capture**: screen recording with the browser's own screen-sharing and `MediaRecorder` APIs, no desktop app.
- **Resumable uploads**: chunked uploads that resume from the first missing part, with the local buffer released only after the server confirms.
- **Gated share links**: every view passes a fail-closed set of link controls, including a readiness check, before playback.
- **Short-lived playback**: recordings play through short-TTL signed URLs.
- **View analytics**: owners see who watched, with view time capped by the recording's own length.
- **Embeds**: a chrome-free player for iframes, discoverable through oEmbed.
- **Abuse reports and retention**: viewers can report a recording, and a daily sweep applies retention and cleans up abandoned uploads.
- **Optional transcripts**: sent to an OpenAI-compatible speech-to-text endpoint when one is configured.

## How it works

<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset=".github/assets/flow-dark.svg">
    <img src=".github/assets/flow.svg" alt="How record.me.at works: record, upload, share, watch, measure" width="880">
  </picture>
</p>

The browser captures the screen and uploads it in chunks, resuming from the first missing part, and the local copy is released only once the server confirms the whole file. Each view of a share link passes a fail-closed set of checks, then plays through a short-lived signed URL, and view time is capped at the recording's length.

## Built with

<p>
  <img src="https://img.shields.io/badge/Next.js-16-000000?style=flat-square&logo=nextdotjs&logoColor=white" alt="Next.js 16">
  <img src="https://img.shields.io/badge/React-19-171717?style=flat-square&logo=react&logoColor=white" alt="React 19">
  <img src="https://img.shields.io/badge/TypeScript-5-262626?style=flat-square&logo=typescript&logoColor=white" alt="TypeScript">
  <img src="https://img.shields.io/badge/Tailwind%20CSS-4-404040?style=flat-square&logo=tailwindcss&logoColor=white" alt="Tailwind CSS 4">
  <img src="https://img.shields.io/badge/Drizzle-Postgres-525252?style=flat-square&logo=drizzle&logoColor=white" alt="Drizzle ORM and Postgres">
  <img src="https://img.shields.io/badge/Cloudflare-R2-737373?style=flat-square&logo=cloudflare&logoColor=white" alt="Cloudflare R2">
</p>

- Next.js 16 (App Router) and React 19
- TypeScript
- Tailwind CSS 4
- Drizzle ORM and Postgres
- S3-compatible object storage (Cloudflare R2)
- Better Auth (shared me.at account)

## Part of the me.at family

record.me.at is one of my [`*.me.at`](https://me.at) apps. They share one design system, one account, and one app shell. Development happens in a private monorepo; this repository is the project's public-facing home.

## License

Source-available. See [LICENSE](LICENSE).
