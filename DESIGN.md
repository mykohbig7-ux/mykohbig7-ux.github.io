/* ==========================================================================
   Portfolio — Style Implementation (DESIGN.md 기준)
   Canvas: Cloud (#f9f9fb) | Card: Paper (#ffffff) | Accent: Periwinkle (#576cdb)
   장식(그림자·그라데이션·애니메이션)은 사용하지 않고, 면의 대비와 1px 헤어라인으로 구분
   ========================================================================== */

:root {
  /* Colors */
  --color-periwinkle-signal: #576cdb;
  --color-deep-indigo: #1f1f47;
  --color-storm-violet: #3d3d5c;
  --color-slate: #575775;
  --color-fog: #6c7693;
  --color-ash: #84849a;
  --color-midnight-ink: #171a1c;
  --color-cloud: #f9f9fb;
  --color-paper: #ffffff;
  --color-mist: #eaedf6;
  --color-haze: #d1d6e1;
  --color-bone: #e3e6e8;
  --color-lilac-wash: #d6dbf5;
  --color-periwinkle-mist: #c1c9f6;
  --color-sky-tint: #abb6ed;
  --color-coral-ember: #f25a5a;
  --color-coral-blush: #f7d4d4;
  --color-mint-whisper: #a6f2d2;
  --color-mint-veil: #c1f6e0;

  /* Typography — 한글은 "Pretendard Variable"이 담당 */
  --font-object-sans: 'Object Sans', 'Inter', "Pretendard Variable", ui-sans-serif, system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
  --font-helvetica-neue: 'Helvetica Neue', "Pretendard Variable", ui-sans-serif, system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;

  /* Shapes */
  --radius-card: 16px;
  --radius-pill: 9999px;
  --radius-panel: 32px;

  /* Layout */
  --page-max-width: 1200px;
  --section-gap: 80px;
  --card-padding: 32px;
}

/* ==========================================================================
   Base
   ========================================================================== */

*, *::before, *::after {
  box-sizing: border-box;
}

html {
  scroll-padding-top: 80px;
  -webkit-text-size-adjust: 100%;
}

html, body {
  margin: 0;
  padding: 0;
  max-width: 100%;
  overflow-x: hidden;
  overflow-x: clip; /* sticky 헤더를 깨뜨리지 않으면서 가로 스크롤 차단 */
}

body {
  background-color: var(--color-cloud);
  color: var(--color-midnight-ink);
  font-family: var(--font-helvetica-neue);
  font-size: 16px;
  font-weight: 400;
  line-height: 1.5;
  word-break: keep-all;
  overflow-wrap: break-word;
  -webkit-font-smoothing: antialiased;
}

img, picture, video, canvas, svg {
  display: block;
  max-width: 100%;
  height: auto;
}

figure, p, dl, dd, ul {
  margin: 0;
}

ul {
  padding: 0;
}

a {
  color: inherit;
  text-decoration: none;
  overflow-wrap: anywhere;
}

h1, h2, h3 {
  margin: 0;
  font-family: var(--font-object-sans);
  color: var(--color-deep-indigo);
  text-wrap: balance;
}

:focus-visible {
  outline: 2px solid var(--color-periwinkle-signal);
  outline-offset: 2px;
}

/* Skip link */
.skip-link {
  position: absolute;
  top: -100px;
  left: 16px;
  z-index: 1000;
  padding: 12px 24px;
  border-radius: var(--radius-pill);
  background-color: var(--color-deep-indigo);
  color: var(--color-paper);
  font-family: var(--font-object-sans);
  font-weight: 500;
}

.skip-link:focus {
  top: 16px;
}

/* ==========================================================================
   Header — 흰 바, 하단 1px 헤어라인, 높이 64px (브랜드 좌 / 링크 중앙)
   ========================================================================== */

.site-header {
  position: sticky;
  top: 0;
  z-index: 100;
  display: grid;
  grid-template-columns: 1fr auto 1fr;
  align-items: center;
  height: 64px;
  padding-inline: max(24px, calc((100% - var(--page-max-width)) / 2 + 24px));
  background-color: var(--color-paper);
  border-bottom: 1px solid var(--color-mist);
}

.brand {
  justify-self: start;
  font-family: var(--font-object-sans);
  font-size: 18px;
  font-weight: 700;
  letter-spacing: -0.02em;
  color: var(--color-deep-indigo);
}

.site-header nav {
  display: flex;
  align-items: center;
  gap: 32px;
}

.site-header nav a {
  font-family: var(--font-object-sans);
  font-size: 16px;
  font-weight: 400;
  color: var(--color-deep-indigo);
}

.site-header nav a:hover {
  color: var(--color-periwinkle-signal);
}

/* ==========================================================================
   Containers
   ========================================================================== */

main {
  display: block;
  width: 100%;
}

.hero,
.metrics,
.section,
footer {
  width: 100%;
  max-width: var(--page-max-width);
  margin-left: auto;
  margin-right: auto;
  padding-left: 24px;
  padding-right: 24px;
}

/* ==========================================================================
   Eyebrow
   ========================================================================== */

.eyebrow {
  margin-bottom: 12px;
  font-family: var(--font-object-sans);
  font-size: 13px;
  font-weight: 500;
  line-height: 18px;
  letter-spacing: 0.04em;
  text-transform: uppercase;
  color: var(--color-fog);
}

/* ==========================================================================
   Hero — 2단 분할 (텍스트 좌 / 요약 카드 우)
   ========================================================================== */

.hero {
  display: grid;
  grid-template-columns: minmax(0, 1.2fr) minmax(0, 0.8fr);
  gap: 48px;
  align-items: center;
  padding-top: var(--section-gap);
  padding-bottom: 64px;
}

.hero-copy {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  min-width: 0;
}

h1#hero-title {
  margin-bottom: 24px;
  font-size: 64px;
  font-weight: 300;
  line-height: 1;
  letter-spacing: -0.04em;
}

.hero-line,
.hero-line.plain {
  font-weight: 300;
}

.hero-summary {
  max-width: 520px;
  margin-bottom: 32px;
  font-size: 18px;
  line-height: 1.5;
  color: var(--color-storm-violet);
}

.hero-actions {
  display: flex;
  align-items: center;
  flex-wrap: wrap;
  gap: 16px;
}

/* Primary pill button — 테두리 없음, 채움만으로 정의 */
.button {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  padding: 12px 24px;
  border: 0;
  border-radius: var(--radius-pill);
  font-family: var(--font-object-sans);
  font-size: 16px;
  font-weight: 500;
  line-height: 24px;
  cursor: pointer;
}

.button.primary {
  background-color: var(--color-periwinkle-signal);
  color: var(--color-paper);
}

.button.primary:hover {
  opacity: 0.92;
}

/* Ghost text link — 배경·테두리 없음, 뒤에 화살표, hover에서만 밑줄 */
.button.secondary {
  padding: 12px 8px;
  background-color: transparent;
  color: var(--color-periwinkle-signal);
}

.button.secondary::after,
.contact-links a::after {
  content: "\203A";
  margin-left: 6px;
}

.button.secondary:hover,
.contact-links a:hover {
  text-decoration: underline;
}

/* Hero snapshot card */
.snapshot {
  min-width: 0;
  padding: var(--card-padding);
  background-color: var(--color-paper);
  border: 1px solid var(--color-mist);
  border-radius: var(--radius-card);
}

.snapshot-label {
  margin-bottom: 20px;
  font-size: 14px;
  font-weight: 500;
  line-height: 20px;
  color: var(--color-fog);
}

.snapshot dl > div {
  display: flex;
  align-items: baseline;
  justify-content: space-between;
  gap: 16px;
  padding: 12px 0;
  border-bottom: 1px solid var(--color-mist);
}

.snapshot dl > div:first-child {
  padding-top: 0;
}

.snapshot dt {
  font-size: 14px;
  color: var(--color-fog);
}

.snapshot dd {
  font-size: 14px;
  font-weight: 500;
  text-align: right;
  color: var(--color-deep-indigo);
}

.availability {
  display: flex;
  align-items: center;
  gap: 8px;
  margin-top: 20px;
  font-size: 14px;
  color: var(--color-storm-violet);
}

.availability span {
  flex: none;
  width: 8px;
  height: 8px;
  border-radius: 50%;
  background-color: var(--color-mint-whisper);
}

/* ==========================================================================
   Metrics — Stat block (카드·구분선 없음, 넓은 열 간격)
   ========================================================================== */

.metrics {
  display: grid;
  grid-template-columns: repeat(4, minmax(0, 1fr));
  column-gap: 64px;
  row-gap: 32px;
}

.metrics strong {
  display: block;
  margin-bottom: 4px;
  font-family: var(--font-object-sans);
  font-size: 40px;
  font-weight: 500;
  line-height: 1.1;
  letter-spacing: -0.025em;
  color: var(--color-deep-indigo);
}

.metrics span {
  display: block;
  font-size: 14px;
  line-height: 20px;
  color: var(--color-fog);
}

/* ==========================================================================
   Section heading — 가운데 정렬, 얇은(300) 제목
   ========================================================================== */

.section {
  padding-top: var(--section-gap);
}

.section-heading {
  margin-bottom: 56px;
  text-align: center;
}

.section-heading h2,
#contact-title {
  font-size: 48px;
  font-weight: 300;
  line-height: 1.125;
  letter-spacing: -0.03em;
}

.section-heading h2 {
  margin-bottom: 16px;
}

.section-heading > p {
  max-width: 640px;
  margin: 0 auto;
  font-size: 18px;
  line-height: 1.5;
  color: var(--color-fog);
}

/* ==========================================================================
   Project cards (Feature card: 흰 면, 16px 반경, 32px 패딩, 1px 헤어라인, 그림자 없음)
   ========================================================================== */

.project-card {
  min-width: 0;
  padding: var(--card-padding);
  background-color: var(--color-paper);
  border: 1px solid var(--color-mist);
  border-radius: var(--radius-card);
}

.project-card.featured {
  display: grid;
  grid-template-columns: minmax(0, 1fr) minmax(0, 1fr);
  gap: 48px;
  align-items: center;
  margin-bottom: 24px;
}

.project-visual {
  margin: 0;
  min-width: 0;
}

.project-visual img {
  width: 100%;
  height: auto;
  object-fit: cover;
  background-color: var(--color-cloud);
  border: 1px solid var(--color-mist);
  border-radius: var(--radius-card);
}

.project-visual.wide img {
  aspect-ratio: 16 / 10;
}

.project-visual.std img {
  aspect-ratio: 16 / 9;
}

.project-copy {
  min-width: 0;
}

.project-number {
  margin-bottom: 8px;
  font-family: var(--font-object-sans);
  font-size: 13px;
  font-weight: 500;
  line-height: 18px;
  color: var(--color-fog);
}

.project-copy h3 {
  margin-bottom: 12px;
  font-size: 24px;
  font-weight: 500;
  line-height: 1.25;
  letter-spacing: -0.02em;
}

.project-copy > p {
  color: var(--color-storm-violet);
}

.project-lead {
  margin-bottom: 24px;
}

.impact-list {
  list-style: none;
  margin: 0 0 24px;
}

.impact-list li {
  display: grid;
  grid-template-columns: 2.75em minmax(0, 1fr);
  gap: 12px;
  margin-bottom: 8px;
  font-size: 14px;
  line-height: 20px;
  color: var(--color-storm-violet);
}

.impact-list li:last-child {
  margin-bottom: 0;
}

.impact-list strong {
  font-weight: 500;
  color: var(--color-deep-indigo);
}

/* Tags — 작은 pill 칩 */
.tags {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
}

.tags span {
  display: inline-block;
  padding: 4px 12px;
  border-radius: var(--radius-pill);
  background-color: var(--color-periwinkle-mist);
  font-size: 13px;
  line-height: 18px;
  color: var(--color-deep-indigo);
}

details {
  margin-top: 24px;
  padding-top: 16px;
  border-top: 1px solid var(--color-mist);
}

summary {
  font-family: var(--font-object-sans);
  font-size: 14px;
  font-weight: 500;
  color: var(--color-periwinkle-signal);
  cursor: pointer;
}

summary::marker {
  color: var(--color-periwinkle-signal);
}

summary:hover {
  text-decoration: underline;
}

details[open] summary {
  margin-bottom: 12px;
}

details p {
  color: var(--color-storm-violet);
}

/* Compact cards */
.project-grid {
  display: grid;
  grid-template-columns: repeat(2, minmax(0, 1fr));
  gap: 24px;
}

.project-card.compact .project-visual {
  margin-bottom: 24px;
}

.project-card.compact .tags {
  margin-top: 16px;
}

.one-line-impact {
  margin-top: 12px;
  font-size: 14px;
  line-height: 20px;
  color: var(--color-slate);
}

.one-line-impact strong {
  margin-right: 8px;
  font-weight: 500;
  color: var(--color-deep-indigo);
}

/* ==========================================================================
   Capability cards (Feature card + Category icon badge)
   ========================================================================== */

.capability-grid {
  display: grid;
  grid-template-columns: repeat(3, minmax(0, 1fr));
  gap: 24px;
}

.capability-grid article {
  display: flex;
  flex-direction: column;
  min-width: 0;
  padding: var(--card-padding);
  background-color: var(--color-paper);
  border: 1px solid var(--color-mist);
  border-radius: var(--radius-card);
}

.capability-grid article > span {
  display: flex;
  align-items: center;
  justify-content: center;
  flex: none;
  width: 40px;
  height: 40px;
  margin-bottom: 24px;
  border-radius: 50%;
  background-color: var(--color-periwinkle-mist);
  font-family: var(--font-object-sans);
  font-size: 14px;
  font-weight: 500;
  color: var(--color-deep-indigo);
}

.capability-grid article:nth-child(1) > span {
  background-color: var(--color-coral-blush);
}

.capability-grid article:nth-child(2) > span {
  background-color: var(--color-mint-veil);
}

.capability-grid article:nth-child(3) > span {
  background-color: var(--color-periwinkle-mist);
}

.capability-grid h3 {
  margin-bottom: 12px;
  font-size: 24px;
  font-weight: 500;
  line-height: 1.25;
  letter-spacing: -0.02em;
}

.capability-grid p {
  margin-bottom: 24px;
  color: var(--color-storm-violet);
}

.capability-grid small {
  display: block;
  margin-top: auto;
  padding-top: 16px;
  border-top: 1px solid var(--color-mist);
  font-size: 13px;
  line-height: 18px;
  color: var(--color-slate);
}

/* ==========================================================================
   Contact — 큰 패널(32px 반경), 가운데 정렬
   ========================================================================== */

.contact {
  width: calc(100% - 48px);
  max-width: calc(var(--page-max-width) - 48px);
  margin: var(--section-gap) auto;
  padding: 80px 32px;
  background-color: var(--color-paper);
  border: 1px solid var(--color-mist);
  border-radius: var(--radius-panel);
  text-align: center;
}

#contact-title {
  margin-bottom: 20px;
}

.contact > p:not(.eyebrow) {
  max-width: 560px;
  margin: 0 auto 32px;
  font-size: 18px;
  line-height: 1.5;
  color: var(--color-storm-violet);
}

.contact-links {
  display: flex;
  align-items: center;
  justify-content: center;
  flex-wrap: wrap;
  gap: 16px 32px;
}

.contact-links a {
  font-family: var(--font-object-sans);
  font-size: 16px;
  font-weight: 500;
  color: var(--color-periwinkle-signal);
}

/* ==========================================================================
   Footer
   ========================================================================== */

footer {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 16px;
  padding-top: 32px;
  padding-bottom: 48px;
  border-top: 1px solid var(--color-mist);
  font-size: 14px;
  color: var(--color-fog);
}

footer a {
  color: var(--color-slate);
}

footer a:hover {
  color: var(--color-deep-indigo);
}

/* ==========================================================================
   Responsive
   ========================================================================== */

@media (max-width: 1100px) {
  h1#hero-title {
    font-size: 48px;
    line-height: 1.1;
    letter-spacing: -0.03em;
  }

  .metrics {
    column-gap: 32px;
  }
}

@media (max-width: 960px) {
  .hero {
    grid-template-columns: minmax(0, 1fr);
    gap: 40px;
    padding-top: 56px;
    padding-bottom: 48px;
  }

  h1#hero-title {
    font-size: 56px;
    line-height: 1.05;
    letter-spacing: -0.04em;
  }

  .metrics {
    grid-template-columns: repeat(2, minmax(0, 1fr));
  }

  .project-card.featured,
  .project-grid,
  .capability-grid {
    grid-template-columns: minmax(0, 1fr);
  }

  .project-card.featured {
    gap: 32px;
  }

  .section-heading h2,
  #contact-title {
    font-size: 40px;
    line-height: 1.125;
    letter-spacing: -0.025em;
  }
}

@media (max-width: 600px) {
  :root {
    --section-gap: 64px;
    --card-padding: 24px;
  }

  .site-header {
    display: flex;
    justify-content: space-between;
    padding-inline: 16px;
  }

  .site-header nav {
    gap: 16px;
  }

  .site-header nav a {
    font-size: 14px;
  }

  .hero,
  .metrics,
  .section,
  footer {
    padding-left: 16px;
    padding-right: 16px;
  }

  .hero {
    padding-top: 40px;
  }

  h1#hero-title {
    font-size: 40px;
    letter-spacing: -0.025em;
  }

  .hero-summary {
    font-size: 16px;
  }

  .hero-actions {
    width: 100%;
    flex-direction: column;
    align-items: stretch;
    gap: 8px;
  }

  .button {
    width: 100%;
  }

  .metrics {
    column-gap: 24px;
  }

  .metrics strong {
    font-size: 32px;
    letter-spacing: -0.02em;
  }

  .section-heading {
    margin-bottom: 40px;
  }

  .section-heading h2,
  #contact-title {
    font-size: 32px;
    line-height: 1.25;
    letter-spacing: -0.02em;
  }

  .section-heading > p,
  .contact > p:not(.eyebrow) {
    font-size: 16px;
  }

  .project-card.featured {
    gap: 24px;
  }

  .contact {
    width: calc(100% - 32px);
    padding: 56px 24px;
  }

  .contact-links {
    flex-direction: column;
    gap: 12px;
  }

  footer {
    padding-bottom: 32px;
  }
}
