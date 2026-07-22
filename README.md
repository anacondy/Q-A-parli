# Q-A-parli 🇮🇳

> [**Live Site: https://anacondy.github.io/Q-A-parli/**](https://anacondy.github.io/Q-A-parli/)

A highly optimized, hardware-accelerated web application to browse, search, and explore Indian Parliament Questions and Answers.

---

## 🏛️ Design & Aesthetics
- **Color Palette**: Stone grays, deep blacks, muted sage greens, and warm off-whites designed to mimic a clean, architectural, and moody aesthetic.
- **Typography**: Uses **Playfair Display** for bold serif headings, **Inter** for clean sans-serif body text, and **JetBrains Mono** for structural badges and code components.
- **Atmospheric UI**: Includes a lightweight film grain overlay for a textured feel alongside bold, condensed typography elements.

## 🔍 Search System
- **Command Palette**: Quickly access search anywhere using the \Ctrl+K / ⌘K\ keyboard shortcut.
- **Multi-parameter Search**: Seamlessly filter searches by question text, MP name, topic, ministry, or parliamentary session.
- **Inline Filter Chips**: Quick toggles integrated directly within the search overlay (All, Lok Sabha, Rajya Sabha, Starred, Unstarred).
- **Real-time Engine**: Implements debounced keystroke tracking and matches highlight rendering dynamically.

## 🤖 AI Integration (Production-Ready)
- Includes a robust \AIIntegration\ data structure module capable of fetching real-time data using endpoints for **Gemini, OpenAI, Claude, or Grok**.
- Utilizes structured JSON prompting mechanics specifically tuned to avoid hallucination and enforce factual accuracy based on official Lok Sabha and Rajya Sabha sources.
- Integrates a deduplication engine relying on question numbers and **Jaccard similarity** checks to prevent UI clashing or duplicated entries on load.

## 📊 Embedded Data
- Currently bootstrapped with real-format Q&A entries spanning recent Budget, Winter, and Monsoon sessions.
- Attributes all data appropriately to official URLs (\loksabha.nic.in\, \ajyasabha.nic.in\).

---

## ⚡ Performance Features
Designed specifically to hit **60 FPS on low-end devices** and up to **144 FPS / 144 Hz on high-end displays** with zero frame drops.

- **Hardware Acceleration**: Heavy use of \	ransform: translateZ(0)\ and \will-change: transform, opacity\ triggers GPU offloading for smooth paints.
- **Micro-Optimized DOM Updates**: Throttled window events and decoupled UI updates using \equestAnimationFrame\.
- **Content Visibility**: Employs \content-visibility: auto; contain-intrinsic-size: auto 600px;\ to drastically reduce layout shifts and render blocking times for large lists.
- **Scroll Throttling**: Scroll listeners run passively and utilize \IntersectionObserver\ for lazy sequence animations.
- **Accessibility**: Repects \prefers-reduced-motion\ for users requesting minimal animations.

---

## 🚀 GitHub Actions Deployment

This site is continuously deployed using **GitHub Actions**.
- Tracks the \main\ branch securely.
- Validates basic structural integrity locally and ships statically to GitHub Pages.

---

## 📚 Documentation & Wiki

### Setup / Local Hosting
To run the project locally, there are no dependencies. Simply run a local web server to prevent CORS issues with local fonts/scripts:

`ash
# Python 3
python -m http.server 8000
`
Then visit \http://localhost:8000\.

### Code Walkthrough
The logic is functionally split to run completely within the static HTML acting as an SPA:

1. **State Management**: Lightweight memory model tracking active states, filter queues, and \Set\ structures for deduplicating parsed API payload chunks.
2. **IntersectionObserver**: Native observer pattern loading and clearing classes as elements cross the viewport boundary.
3. **Event Delegation**: Native decoupled \onclick\ directives mapping functions cleanly inside module scope to prevent \O(N)\ listener memory leaks.

For detailed architecture logic, consider checking out the repository [WiKi](https://github.com/anacondy/Q-A-parli/wiki).

## ⚖️ License
Licensed under [MIT](LICENSE) - See LICENSE file for details.
