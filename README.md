# TipJar P2P — Support Creators On-Chain

> A peer-to-peer creator tipping board built on [Intercom](https://github.com/Trac-Systems/intercom) by Trac Systems.

## What is TipJar P2P?
<img width="1291" height="826" alt="image" src="https://github.com/user-attachments/assets/0a2e407f-6282-48b3-bfb3-2bc3e730a283" />

TipJar P2P is a decentralized creator support board where anyone can **post their work** (art, music, code, writing, research, design) and **receive TNK tips from supporters** via Intercom P2P sidechannels.

No middlemen. No custodians. Pure peer-to-peer tipping.

## Features

- 📌 **Post your work** — Share any creative or technical work with a title, description, and category
- 💸 **Tip via P2P** — Send TNK tips directly to creators using Intercom sidechannels
- 🗂 **Category filter** — Browse by Art, Music, Code, Writing, Video, Research, Design
- 📊 **Live stats** — Total posts, tips, TNK tipped, and unique creators
- 🔒 **Non-custodial** — Trac wallet address per post, you always control your keys

## How it Works

1. Creator posts their work with a Trac wallet address
2. Supporters browse the feed and hit **Tip ↗**
3. TNK is routed P2P via Intercom sidechannels to the creator's Trac address
4. Stats update in real-time

## Screenshots

> App running at `/index.html`:

![TipJar P2P Screenshot](./screenshot.png)

## Getting Started

```bash
git clone https://github.com/YOUR_HANDLE/intercom
cd intercom
# open index.html in browser
# or serve with any static server:
npx serve .
```

## Trac Address (for payout)

```
trac1axm42chw8tctvf34dscw2ve30r0ztyvj7tq7r3ux0u2j4e8xdslq98t79t
```

> Replace `trac1axm42chw8tctvf34dscw2ve30r0ztyvj7tq7r3ux0u2j4e8xdslq98t79t` with your actual Trac address to receive the 500 TNK payout.

## Fork Info

- **Fork of:** [Trac-Systems/intercom](https://github.com/Trac-Systems/intercom)
- **Added:** `index.html` — TipJar P2P creator board
- **Added:** `SKILL.md` — Agent skill instructions
- **Listed in:** [awesome-intercom](https://github.com/Trac-Systems/awesome-intercom)

## License

MIT — fork freely, tip generously.
