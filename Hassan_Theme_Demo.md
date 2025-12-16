---
marp: true
theme: default
paginate: true
math: katex
---

<style>
/* =========================================================
   PHYSICS / MATH OPTIMIZED MARP THEME
   (Consolidated – Drop-in Replacement)
   ========================================================= */

/* ---------- 1. MODULAR CONFIGURATION ---------- */

:root {
    /* Layout */
    --title-pos-x: 20px;
    --title-pos-y: 20px;
    --title-height: 60px;
    --content-pad-top: 120px;
    --content-pad-side: 50px;

    /* Typography */
    --font-size-base: 28px;
    --font-size-h1: 40px;
    --font-size-h2: 24px;

    /* Colors */
    --color-primary: #2D3E50;
    --color-secondary: #666;
    --color-border: #EEE;
}

/* ---------- 2. GLOBAL SLIDE LAYOUT ---------- */

section {
    justify-content: flex-start;
    padding: var(--content-pad-top) var(--content-pad-side) 50px;
    font-size: var(--font-size-base);
    line-height: 1.4;
}

/* ---------- 3. PINNED HEADER SYSTEM ---------- */

h1 {
    position: absolute;
    top: var(--title-pos-y);
    left: var(--title-pos-x);
    right: var(--title-pos-x);
    height: var(--title-height);
    margin: 0;
    font-size: var(--font-size-h1);
    color: var(--color-primary);
    border-bottom: 2px solid var(--color-border);
    padding-bottom: 10px;
    line-height: 1.2;
    white-space: normal;
    overflow: hidden;
}

h2 {
    position: absolute;
    top: calc(var(--title-pos-y) + var(--title-height) + 5px);
    left: var(--title-pos-x);
    font-size: var(--font-size-h2);
    color: var(--color-secondary);
    margin: 0;
}

/* ---------- 4. TITLE SLIDE EXCEPTION ---------- */

section.title-slide {
    justify-content: center;
    align-items: center;
    text-align: center;
    padding: 50px;
}

section.title-slide h1 {
    position: relative;
    border: none;
    font-size: 60px;
}

section.title-slide h2 {
    position: relative;
    font-size: 35px;
}

/* Title Slide Smart Tag (#layout-title) */
section:has(a[href*="#layout-title"]) {
    justify-content: center !important;
    align-items: center !important;
    text-align: center !important;
    padding: 50px !important;
}

section:has(a[href*="#layout-title"]) h1 {
    position: relative !important;
    border: none !important;
    font-size: 60px !important;
    top: auto !important;
    left: auto !important;
    right: auto !important;
}

section:has(a[href*="#layout-title"]) h2 {
    position: relative !important;
    font-size: 35px !important;
    top: auto !important;
    left: auto !important;
}

/* ---------- 5. PHYSICS / MATH (KaTeX) ---------- */

.katex {
    font-size: 1.05em;
}

.katex-display {
    margin: 1.2em 0 1.4em;
}

.katex span {
    line-height: 1.2;
}

section.dense-math {
    line-height: 1.3;
}

section.dense-math .katex {
    font-size: 0.95em;
}

/* ---------- 6. FIGURES & PLOTS ---------- */

figure {
    margin: 0;
    display: flex;
    flex-direction: column;
    align-items: center;
}

figure img,
figure svg {
    max-width: 100%;
    height: auto;
}

figcaption {
    font-size: 0.7em;
    color: #555;
    margin-top: 6px;
    text-align: center;
}

/* Plot sizing */
.plot-full img {
    max-width: 100%;
}

.plot-large img {
    max-width: 90%;
}

.plot-medium img {
    max-width: 75%;
}

.plot-small img {
    max-width: 60%;
}

/* ---------- 7. SPLIT LAYOUTS (AUTO) ---------- */

section.split,
section.split-reverse {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 30px;
    align-items: center;
    height: 100%;
}

/* Split (text left, image right) */
section.split>p,
section.split>ul,
section.split>ol,
section.split>blockquote {
    grid-column: 1;
}

section.split>p:has(img),
section.split>img,
section.split>figure {
    grid-column: 2;
}

/* Split-reverse (image left, text right) */
section.split-reverse>p:has(img),
section.split-reverse>img,
section.split-reverse>figure {
    grid-column: 1;
}

section.split-reverse>p,
section.split-reverse>ul,
section.split-reverse>ol,
section.split-reverse>blockquote {
    grid-column: 2;
}

/* ---------- 8. GRID SYSTEM ---------- */

section.grid {
    display: grid;
    gap: 30px;
    height: 100%;
    align-items: start;
}

section.grid.cols-2 {
    grid-template-columns: 1fr 1fr;
}

section.grid.cols-3 {
    grid-template-columns: 1fr 1fr 1fr;
}

section.grid.cols-4 {
    grid-template-columns: repeat(4, 1fr);
}

section.grid.rows-2 {
    grid-template-rows: 1fr 1fr;
}

/* Spanning logic */
section.span-first> :first-child,
section.span-first>h1+*,
section.span-first>h2+* {
    grid-column: 1 / -1;
}

section.span-last> :last-child,
section.span-last> :nth-last-child(2):not(footer) {
    grid-column: 1 / -1;
}

section.span-both> :first-child,
section.span-both>h1+*,
section.span-both>h2+*,
section.span-both> :last-child,
/* Usage: <figure class="caption-top"> ... </figure> */
figure.caption-top {
    flex-direction: column-reverse;
    /* Moves figcaption to top */
}

figure.caption-top figcaption {
    margin-top: 0;
    margin-bottom: 6px;
}

figure.caption-bottom {
    flex-direction: column;
    /* Default */
}

/* SMART CAPTIONS (Markdown Pattern) */
/* Usage: In a gallery, standard text after an image acts as a caption */
section.gallery p {
    /* Existing Grid Logic */
    justify-items: center;
    align-items: end;
    /* Align caption at bottom by default */
}

/* ---------- 9. EQUATION + PLOT LAYOUT ---------- */

section.eq-plot {
    display: grid;
    grid-template-columns: 1fr 1.1fr;
    gap: 40px;
    align-items: center;
    height: 100%;
}

/* ---------- 10. TITLE FUNCTIONS ---------- */

section.title-center {
    --title-pos-x: 0;
}

section.title-center h1 {
    text-align: center;
    left: 50px;
    right: 50px;
}

section.title-middle {
    --title-pos-y: 150px;
    --content-pad-top: 230px;
}

section.title-right {
    --title-pos-x: 400px;
}

section.no-header {
    --title-height: 0px;
    --title-pos-y: -200px;
    --content-pad-top: 50px;
}

section.compact-title h1 {
    font-size: 34px;
}

/* ---------- 11. FOOTER ---------- */

footer {
    position: absolute;
    bottom: 18px;
    right: 40px;
    font-size: 16px;
    color: #777;
    pointer-events: none;
}

/* Footer Smart Tag (#footer) */
/* Usage: [Text](#footer) or [Text](#footer-left) or [Text](#footer-center) */

/* Base footer styles */
a[href*="#footer"] {
    position: absolute !important;
    bottom: 18px !important;
    font-size: 16px !important;
    color: #777 !important;
    text-decoration: none !important;
    pointer-events: none !important;
    display: block !important;
}

/* Footer Right (Default) */
a[href*="#footer"]:not([href*="#footer-left"]):not([href*="#footer-center"]) {
    right: 40px !important;
    left: auto !important;
}

/* Footer Left */
a[href*="#footer-left"] {
    left: 40px !important;
    right: auto !important;
}

/* Footer Center */
a[href*="#footer-center"] {
    left: 50% !important;
    right: auto !important;
    transform: translateX(-50%) !important;
}

/* NOTE:
   Uses :has() → requires modern Chromium / Safari */

/* ---------- 12. SEMANTIC CALLOUT BOXES (SYSTEMATIC NAMING) ---------- */
/* Usage: [Title](#box-grey-type) */

/* 1. THEOREM (#box-grey-theorem) */
section.theorem blockquote,
blockquote:has(a[href*="#box-theorem"]),
:not(blockquote)>p:has(a[href*="#box-theorem"]) {
    border-left: 5px solid #007bff;
    background-color: #f0f7ff;
    padding: 15px;
    margin-bottom: 20px;
    color: #2D3E50;
    box-shadow: 0 2px 5px rgba(0, 0, 0, 0.05);
    display: block;
}

section.theorem blockquote strong:first-child,
blockquote a[href*="#box-theorem"],
p a[href*="#box-theorem"] {
    color: #007bff !important;
    display: block;
    margin-bottom: 5px;
    text-transform: uppercase;
    font-size: 0.9em;
    letter-spacing: 1px;
    text-decoration: none;
    pointer-events: none;
    font-weight: bold;
}

/* 2. DEFINITION (#box-grey-def) */
section.definition blockquote,
blockquote:has(a[href*="#box-def"]),
:not(blockquote)>p:has(a[href*="#box-def"]) {
    border-left: 5px solid #28a745;
    background-color: #f0fff4;
    padding: 15px;
    margin-bottom: 20px;
    color: #2D3E50;
    box-shadow: 0 2px 5px rgba(0, 0, 0, 0.05);
    display: block;
}

section.definition blockquote strong:first-child,
blockquote a[href*="#box-def"],
p a[href*="#box-def"] {
    color: #28a745 !important;
    display: block;
    margin-bottom: 5px;
    text-transform: uppercase;
    font-size: 0.9em;
    letter-spacing: 1px;
    text-decoration: none;
    pointer-events: none;
    font-weight: bold;
}

/* 3. ALERT (#box-grey-alert) */
section.alert blockquote,
blockquote:has(a[href*="#box-alert"]),
:not(blockquote)>p:has(a[href*="#box-alert"]) {
    border-left: 5px solid #dc3545;
    background-color: #fff5f5;
    padding: 15px;
    margin-bottom: 20px;
    color: #2D3E50;
    box-shadow: 0 2px 5px rgba(0, 0, 0, 0.05);
    display: block;
}

section.alert blockquote strong:first-child,
blockquote a[href*="#box-alert"],
p a[href*="#box-alert"] {
    color: #dc3545 !important;
    display: block;
    margin-bottom: 5px;
    text-transform: uppercase;
    font-size: 0.9em;
    letter-spacing: 1px;
    text-decoration: none;
    pointer-events: none;
    font-weight: bold;
}

/* 4. GENERIC BOX (#box-grey-grey) */
section.box blockquote,
blockquote:has(a[href*="#box-grey"]),
:not(blockquote)>p:has(a[href*="#box-grey"]) {
    border-left: 5px solid #6c757d;
    background-color: #f8f9fa;
    padding: 15px;
    margin-bottom: 20px;
    color: #2D3E50;
    box-shadow: 0 2px 5px rgba(0, 0, 0, 0.05);
    border-radius: 0 4px 4px 0;
    display: block;
}

section.box blockquote strong:first-child,
blockquote a[href*="#box-grey"],
p a[href*="#box-grey"] {
    color: #495057 !important;
    display: block;
    margin-bottom: 5px;
    text-transform: uppercase;
    font-size: 0.9em;
    letter-spacing: 1px;
    text-decoration: none;
    pointer-events: none;
    font-weight: bold;
}

/* 5. BOXED FRAMES (#box-greyed-color) */
/* matches #boxed, #boxed-red, #boxed-blue using starts-with *="#boxed" */

/* Base Frame Structure */
blockquote:has(a[href*="#boxed"]),
:not(blockquote)>p:has(a[href*="#boxed"]) {
    background-color: transparent;
    padding: 10px;
    margin-bottom: 20px;
    border-radius: 4px;
    display: block;
    border: 2px solid #333;
    /* Default Black */
}

blockquote a[href*="#boxed"],
p a[href*="#boxed"] {
    display: none;
}

/* Colored Frames */
/* Note: CSS Cascade allows these to override the default border */
blockquote:has(a[href*="#boxed-red"]),
:not(blockquote)>p:has(a[href*="#boxed-red"]) {
    border-color: #dc3545;
}

blockquote:has(a[href*="#boxed-blue"]),
:not(blockquote)>p:has(a[href*="#boxed-blue"]) {
    border-color: #007bff;
}

blockquote:has(a[href*="#boxed-green"]),
:not(blockquote)>p:has(a[href*="#boxed-green"]) {
    border-color: #28a745;
}


/* ---------- 13. UNIVERSAL SMART TAG SYSTEM (SYSTEMATIC) ---------- */

/* 1. Text Colors (#color-name) */
a[href*="#color-red"] {
    color: #dc3545 !important;
    text-decoration: none;
    pointer-events: none;
}

a[href*="#color-blue"] {
    color: #007bff !important;
    text-decoration: none;
    pointer-events: none;
}

a[href*="#color-green"] {
    color: #28a745 !important;
    text-decoration: none;
    pointer-events: none;
}

a[href*="#color-grey"] {
    color: #6c757d !important;
    text-decoration: none;
    pointer-events: none;
}

a[href*="#color-purple"] {
    color: #6f42c1 !important;
    text-decoration: none;
    pointer-events: none;
}

/* 2. Typography (#font-size) */
a[href*="#font-tiny"] {
    font-size: 0.6em !important;
    text-decoration: none;
    pointer-events: none;
    color: inherit;
}

a[href*="#font-small"] {
    font-size: 0.8em !important;
    text-decoration: none;
    pointer-events: none;
    color: inherit;
}

a[href*="#font-large"] {
    font-size: 1.2em !important;
    text-decoration: none;
    pointer-events: none;
    color: inherit;
}

a[href*="#font-huge"] {
    font-size: 1.5em !important;
    text-decoration: none;
    pointer-events: none;
    color: inherit;
}

/* 3. Animation Helpers */
a[href*="#anim-fadein"] {
    animation: fadeIn 1s ease-in forwards;
    opacity: 0;
}

@keyframes fadeIn {
    to {
        opacity: 1;
    }
}

/* 4. Layout Modifiers */

/* #layout-center -> Centers text */
blockquote:has(a[href*="#layout-center"]) {
    text-align: center;
}

/* 5. Clean List Helper (Hidden Bullets) */
li:has(blockquote) {
    list-style: none;
    padding: 0;
    margin: 0;
}

/* 6. Graphics Sizing (#graphics-percent & #img-size) */
/* Usage: [Caption](#graphics-91) OR ![#graphics-91](src) */

/* Graphics Sizing (#graphics-percent) */
/* Usage: [Caption](#graphics-50) OR ![#graphics-50](src) */

/* Caption Mode */
p:has(a[href*="#graphics-1"]) img {
    width: 1% !important;
}

p:has(a[href*="#graphics-2"]) img {
    width: 2% !important;
}

p:has(a[href*="#graphics-3"]) img {
    width: 3% !important;
}

p:has(a[href*="#graphics-4"]) img {
    width: 4% !important;
}

p:has(a[href*="#graphics-5"]) img {
    width: 5% !important;
}

p:has(a[href*="#graphics-6"]) img {
    width: 6% !important;
}

p:has(a[href*="#graphics-7"]) img {
    width: 7% !important;
}

p:has(a[href*="#graphics-8"]) img {
    width: 8% !important;
}

p:has(a[href*="#graphics-9"]) img {
    width: 9% !important;
}

p:has(a[href*="#graphics-10"]) img {
    width: 10% !important;
}

p:has(a[href*="#graphics-11"]) img {
    width: 11% !important;
}

p:has(a[href*="#graphics-12"]) img {
    width: 12% !important;
}

p:has(a[href*="#graphics-13"]) img {
    width: 13% !important;
}

p:has(a[href*="#graphics-14"]) img {
    width: 14% !important;
}

p:has(a[href*="#graphics-15"]) img {
    width: 15% !important;
}

p:has(a[href*="#graphics-16"]) img {
    width: 16% !important;
}

p:has(a[href*="#graphics-17"]) img {
    width: 17% !important;
}

p:has(a[href*="#graphics-18"]) img {
    width: 18% !important;
}

p:has(a[href*="#graphics-19"]) img {
    width: 19% !important;
}

p:has(a[href*="#graphics-20"]) img {
    width: 20% !important;
}

p:has(a[href*="#graphics-21"]) img {
    width: 21% !important;
}

p:has(a[href*="#graphics-22"]) img {
    width: 22% !important;
}

p:has(a[href*="#graphics-23"]) img {
    width: 23% !important;
}

p:has(a[href*="#graphics-24"]) img {
    width: 24% !important;
}

p:has(a[href*="#graphics-25"]) img {
    width: 25% !important;
}

p:has(a[href*="#graphics-26"]) img {
    width: 26% !important;
}

p:has(a[href*="#graphics-27"]) img {
    width: 27% !important;
}

p:has(a[href*="#graphics-28"]) img {
    width: 28% !important;
}

p:has(a[href*="#graphics-29"]) img {
    width: 29% !important;
}

p:has(a[href*="#graphics-30"]) img {
    width: 30% !important;
}

p:has(a[href*="#graphics-31"]) img {
    width: 31% !important;
}

p:has(a[href*="#graphics-32"]) img {
    width: 32% !important;
}

p:has(a[href*="#graphics-33"]) img {
    width: 33% !important;
}

p:has(a[href*="#graphics-34"]) img {
    width: 34% !important;
}

p:has(a[href*="#graphics-35"]) img {
    width: 35% !important;
}

p:has(a[href*="#graphics-36"]) img {
    width: 36% !important;
}

p:has(a[href*="#graphics-37"]) img {
    width: 37% !important;
}

p:has(a[href*="#graphics-38"]) img {
    width: 38% !important;
}

p:has(a[href*="#graphics-39"]) img {
    width: 39% !important;
}

p:has(a[href*="#graphics-40"]) img {
    width: 40% !important;
}

p:has(a[href*="#graphics-41"]) img {
    width: 41% !important;
}

p:has(a[href*="#graphics-42"]) img {
    width: 42% !important;
}

p:has(a[href*="#graphics-43"]) img {
    width: 43% !important;
}

p:has(a[href*="#graphics-44"]) img {
    width: 44% !important;
}

p:has(a[href*="#graphics-45"]) img {
    width: 45% !important;
}

p:has(a[href*="#graphics-46"]) img {
    width: 46% !important;
}

p:has(a[href*="#graphics-47"]) img {
    width: 47% !important;
}

p:has(a[href*="#graphics-48"]) img {
    width: 48% !important;
}

p:has(a[href*="#graphics-49"]) img {
    width: 49% !important;
}

p:has(a[href*="#graphics-50"]) img {
    width: 50% !important;
}

p:has(a[href*="#graphics-51"]) img {
    width: 51% !important;
}

p:has(a[href*="#graphics-52"]) img {
    width: 52% !important;
}

p:has(a[href*="#graphics-53"]) img {
    width: 53% !important;
}

p:has(a[href*="#graphics-54"]) img {
    width: 54% !important;
}

p:has(a[href*="#graphics-55"]) img {
    width: 55% !important;
}

p:has(a[href*="#graphics-56"]) img {
    width: 56% !important;
}

p:has(a[href*="#graphics-57"]) img {
    width: 57% !important;
}

p:has(a[href*="#graphics-58"]) img {
    width: 58% !important;
}

p:has(a[href*="#graphics-59"]) img {
    width: 59% !important;
}

p:has(a[href*="#graphics-60"]) img {
    width: 60% !important;
}

p:has(a[href*="#graphics-61"]) img {
    width: 61% !important;
}

p:has(a[href*="#graphics-62"]) img {
    width: 62% !important;
}

p:has(a[href*="#graphics-63"]) img {
    width: 63% !important;
}

p:has(a[href*="#graphics-64"]) img {
    width: 64% !important;
}

p:has(a[href*="#graphics-65"]) img {
    width: 65% !important;
}

p:has(a[href*="#graphics-66"]) img {
    width: 66% !important;
}

p:has(a[href*="#graphics-67"]) img {
    width: 67% !important;
}

p:has(a[href*="#graphics-68"]) img {
    width: 68% !important;
}

p:has(a[href*="#graphics-69"]) img {
    width: 69% !important;
}

p:has(a[href*="#graphics-70"]) img {
    width: 70% !important;
}

p:has(a[href*="#graphics-71"]) img {
    width: 71% !important;
}

p:has(a[href*="#graphics-72"]) img {
    width: 72% !important;
}

p:has(a[href*="#graphics-73"]) img {
    width: 73% !important;
}

p:has(a[href*="#graphics-74"]) img {
    width: 74% !important;
}

p:has(a[href*="#graphics-75"]) img {
    width: 75% !important;
}

p:has(a[href*="#graphics-76"]) img {
    width: 76% !important;
}

p:has(a[href*="#graphics-77"]) img {
    width: 77% !important;
}

p:has(a[href*="#graphics-78"]) img {
    width: 78% !important;
}

p:has(a[href*="#graphics-79"]) img {
    width: 79% !important;
}

p:has(a[href*="#graphics-80"]) img {
    width: 80% !important;
}

p:has(a[href*="#graphics-81"]) img {
    width: 81% !important;
}

p:has(a[href*="#graphics-82"]) img {
    width: 82% !important;
}

p:has(a[href*="#graphics-83"]) img {
    width: 83% !important;
}

p:has(a[href*="#graphics-84"]) img {
    width: 84% !important;
}

p:has(a[href*="#graphics-85"]) img {
    width: 85% !important;
}

p:has(a[href*="#graphics-86"]) img {
    width: 86% !important;
}

p:has(a[href*="#graphics-87"]) img {
    width: 87% !important;
}

p:has(a[href*="#graphics-88"]) img {
    width: 88% !important;
}

p:has(a[href*="#graphics-89"]) img {
    width: 89% !important;
}

p:has(a[href*="#graphics-90"]) img {
    width: 90% !important;
}

p:has(a[href*="#graphics-91"]) img {
    width: 91% !important;
}

p:has(a[href*="#graphics-92"]) img {
    width: 92% !important;
}

p:has(a[href*="#graphics-93"]) img {
    width: 93% !important;
}

p:has(a[href*="#graphics-94"]) img {
    width: 94% !important;
}

p:has(a[href*="#graphics-95"]) img {
    width: 95% !important;
}

p:has(a[href*="#graphics-96"]) img {
    width: 96% !important;
}

p:has(a[href*="#graphics-97"]) img {
    width: 97% !important;
}

p:has(a[href*="#graphics-98"]) img {
    width: 98% !important;
}

p:has(a[href*="#graphics-99"]) img {
    width: 99% !important;
}

p:has(a[href*="#graphics-100"]) img {
    width: 100% !important;
}

/* Alt-Tag Mode */
img[alt*="#graphics-1"] {
    width: 1% !important;
}

img[alt*="#graphics-2"] {
    width: 2% !important;
}

img[alt*="#graphics-3"] {
    width: 3% !important;
}

img[alt*="#graphics-4"] {
    width: 4% !important;
}

img[alt*="#graphics-5"] {
    width: 5% !important;
}

img[alt*="#graphics-6"] {
    width: 6% !important;
}

img[alt*="#graphics-7"] {
    width: 7% !important;
}

img[alt*="#graphics-8"] {
    width: 8% !important;
}

img[alt*="#graphics-9"] {
    width: 9% !important;
}

img[alt*="#graphics-10"] {
    width: 10% !important;
}

img[alt*="#graphics-11"] {
    width: 11% !important;
}

img[alt*="#graphics-12"] {
    width: 12% !important;
}

img[alt*="#graphics-13"] {
    width: 13% !important;
}

img[alt*="#graphics-14"] {
    width: 14% !important;
}

img[alt*="#graphics-15"] {
    width: 15% !important;
}

img[alt*="#graphics-16"] {
    width: 16% !important;
}

img[alt*="#graphics-17"] {
    width: 17% !important;
}

img[alt*="#graphics-18"] {
    width: 18% !important;
}

img[alt*="#graphics-19"] {
    width: 19% !important;
}

img[alt*="#graphics-20"] {
    width: 20% !important;
}

img[alt*="#graphics-21"] {
    width: 21% !important;
}

img[alt*="#graphics-22"] {
    width: 22% !important;
}

img[alt*="#graphics-23"] {
    width: 23% !important;
}

img[alt*="#graphics-24"] {
    width: 24% !important;
}

img[alt*="#graphics-25"] {
    width: 25% !important;
}

img[alt*="#graphics-26"] {
    width: 26% !important;
}

img[alt*="#graphics-27"] {
    width: 27% !important;
}

img[alt*="#graphics-28"] {
    width: 28% !important;
}

img[alt*="#graphics-29"] {
    width: 29% !important;
}

img[alt*="#graphics-30"] {
    width: 30% !important;
}

img[alt*="#graphics-31"] {
    width: 31% !important;
}

img[alt*="#graphics-32"] {
    width: 32% !important;
}

img[alt*="#graphics-33"] {
    width: 33% !important;
}

img[alt*="#graphics-34"] {
    width: 34% !important;
}

img[alt*="#graphics-35"] {
    width: 35% !important;
}

img[alt*="#graphics-36"] {
    width: 36% !important;
}

img[alt*="#graphics-37"] {
    width: 37% !important;
}

img[alt*="#graphics-38"] {
    width: 38% !important;
}

img[alt*="#graphics-39"] {
    width: 39% !important;
}

img[alt*="#graphics-40"] {
    width: 40% !important;
}

img[alt*="#graphics-41"] {
    width: 41% !important;
}

img[alt*="#graphics-42"] {
    width: 42% !important;
}

img[alt*="#graphics-43"] {
    width: 43% !important;
}

img[alt*="#graphics-44"] {
    width: 44% !important;
}

img[alt*="#graphics-45"] {
    width: 45% !important;
}

img[alt*="#graphics-46"] {
    width: 46% !important;
}

img[alt*="#graphics-47"] {
    width: 47% !important;
}

img[alt*="#graphics-48"] {
    width: 48% !important;
}

img[alt*="#graphics-49"] {
    width: 49% !important;
}

img[alt*="#graphics-50"] {
    width: 50% !important;
}

img[alt*="#graphics-51"] {
    width: 51% !important;
}

img[alt*="#graphics-52"] {
    width: 52% !important;
}

img[alt*="#graphics-53"] {
    width: 53% !important;
}

img[alt*="#graphics-54"] {
    width: 54% !important;
}

img[alt*="#graphics-55"] {
    width: 55% !important;
}

img[alt*="#graphics-56"] {
    width: 56% !important;
}

img[alt*="#graphics-57"] {
    width: 57% !important;
}

img[alt*="#graphics-58"] {
    width: 58% !important;
}

img[alt*="#graphics-59"] {
    width: 59% !important;
}

img[alt*="#graphics-60"] {
    width: 60% !important;
}

img[alt*="#graphics-61"] {
    width: 61% !important;
}

img[alt*="#graphics-62"] {
    width: 62% !important;
}

img[alt*="#graphics-63"] {
    width: 63% !important;
}

img[alt*="#graphics-64"] {
    width: 64% !important;
}

img[alt*="#graphics-65"] {
    width: 65% !important;
}

img[alt*="#graphics-66"] {
    width: 66% !important;
}

img[alt*="#graphics-67"] {
    width: 67% !important;
}

img[alt*="#graphics-68"] {
    width: 68% !important;
}

img[alt*="#graphics-69"] {
    width: 69% !important;
}

img[alt*="#graphics-70"] {
    width: 70% !important;
}

img[alt*="#graphics-71"] {
    width: 71% !important;
}

img[alt*="#graphics-72"] {
    width: 72% !important;
}

img[alt*="#graphics-73"] {
    width: 73% !important;
}

img[alt*="#graphics-74"] {
    width: 74% !important;
}

img[alt*="#graphics-75"] {
    width: 75% !important;
}

img[alt*="#graphics-76"] {
    width: 76% !important;
}

img[alt*="#graphics-77"] {
    width: 77% !important;
}

img[alt*="#graphics-78"] {
    width: 78% !important;
}

img[alt*="#graphics-79"] {
    width: 79% !important;
}

img[alt*="#graphics-80"] {
    width: 80% !important;
}

img[alt*="#graphics-81"] {
    width: 81% !important;
}

img[alt*="#graphics-82"] {
    width: 82% !important;
}

img[alt*="#graphics-83"] {
    width: 83% !important;
}

img[alt*="#graphics-84"] {
    width: 84% !important;
}

img[alt*="#graphics-85"] {
    width: 85% !important;
}

img[alt*="#graphics-86"] {
    width: 86% !important;
}

img[alt*="#graphics-87"] {
    width: 87% !important;
}

img[alt*="#graphics-88"] {
    width: 88% !important;
}

img[alt*="#graphics-89"] {
    width: 89% !important;
}

img[alt*="#graphics-90"] {
    width: 90% !important;
}

img[alt*="#graphics-91"] {
    width: 91% !important;
}

img[alt*="#graphics-92"] {
    width: 92% !important;
}

img[alt*="#graphics-93"] {
    width: 93% !important;
}

img[alt*="#graphics-94"] {
    width: 94% !important;
}

img[alt*="#graphics-95"] {
    width: 95% !important;
}

img[alt*="#graphics-96"] {
    width: 96% !important;
}

img[alt*="#graphics-97"] {
    width: 97% !important;
}

img[alt*="#graphics-98"] {
    width: 98% !important;
}

img[alt*="#graphics-99"] {
    width: 99% !important;
}

img[alt*="#graphics-100"] {
    width: 100% !important;
}

/* Semantic aliases (Caption Mode) */
p:has(a[href*="#img-tiny"]) img {
    width: 20% !important;
}

p:has(a[href*="#img-small"]) img {
    width: 40% !important;
}

p:has(a[href*="#img-medium"]) img {
    width: 60% !important;
}

p:has(a[href*="#img-large"]) img {
    width: 80% !important;
}

p:has(a[href*="#img-full"]) img {
    width: 100% !important;
}

/* Semantic aliases (Alt-Text Mode) */
img[alt*="#img-tiny"] {
    width: 20% !important;
}

img[alt*="#img-small"] {
    width: 40% !important;
}

img[alt*="#img-medium"] {
    width: 60% !important;
}

img[alt*="#img-large"] {
    width: 80% !important;
}

img[alt*="#img-full"] {
    width: 100% !important;
}

/* Slide-Level Layouts (Option B Naming) */
/* Usage: [](#layout-split), [](#layout-3col), [](#head-center), etc. */

/* Split Layout (2-Column: Text Left, Image Right) */
section:has(a[href*="#layout-split"]) {
    display: grid !important;
    grid-template-columns: 1fr 1fr !important;
    grid-gap: 40px !important;
    align-items: center !important;
}

/* Grid 3 Columns */
section:has(a[href*="#layout-3col"]) {
    display: grid !important;
    grid-template-columns: repeat(3, 1fr) !important;
    grid-gap: 20px !important;
    align-items: center !important;
}

/* Grid 4 Columns */
section:has(a[href*="#layout-4col"]) {
    display: grid !important;
    grid-template-columns: repeat(4, 1fr) !important;
    grid-gap: 20px !important;
    align-items: center !important;
}

/* Grid 5 Columns */
section:has(a[href*="#layout-5col"]) {
    display: grid !important;
    grid-template-columns: repeat(5, 1fr) !important;
    grid-gap: 20px !important;
    align-items: center !important;
}

/* Explicit Grid Patterns */

/* 2x2 Grid (4 equal boxes) */
section:has(a[href*="#layout-2x2"]) {
    display: grid !important;
    grid-template-columns: 1fr 1fr !important;
    grid-template-rows: 1fr 1fr !important;
    grid-gap: 20px !important;
    align-items: center !important;
}

/* 1-2 Pattern (1 full-width, then 2 columns) */
section:has(a[href*="#layout-1-2"]) {
    display: grid !important;
    grid-template-columns: 1fr 1fr !important;
    grid-gap: 20px !important;
    align-items: center !important;
}

section:has(a[href*="#layout-1-2"])> :first-child,
section:has(a[href*="#layout-1-2"])>h1+* {
    grid-column: 1 / -1 !important;
}

/* 1-3 Pattern (1 full-width, then 3 columns) */
section:has(a[href*="#layout-1-3"]) {
    display: grid !important;
    grid-template-columns: 1fr 1fr 1fr !important;
    grid-gap: 20px !important;
    align-items: center !important;
}

section:has(a[href*="#layout-1-3"])> :first-child,
section:has(a[href*="#layout-1-3"])>h1+* {
    grid-column: 1 / -1 !important;
}

/* 2-1 Pattern (2 columns, then 1 full-width) */
section:has(a[href*="#layout-2-1"]) {
    display: grid !important;
    grid-template-columns: 1fr 1fr !important;
    grid-gap: 20px !important;
    align-items: center !important;
}

section:has(a[href*="#layout-2-1"])> :last-child,
section:has(a[href*="#layout-2-1"])> :nth-last-child(2):not(footer) {
    grid-column: 1 / -1 !important;
}

/* 3-1 Pattern (3 columns, then 1 full-width) */
section:has(a[href*="#layout-3-1"]) {
    display: grid !important;
    grid-template-columns: 1fr 1fr 1fr !important;
    grid-gap: 20px !important;
    align-items: center !important;
}

section:has(a[href*="#layout-3-1"])> :last-child,
section:has(a[href*="#layout-3-1"])> :nth-last-child(2):not(footer) {
    grid-column: 1 / -1 !important;
}

/* Composite Grid Patterns (Multi-Row with Variable Columns) */

/* 1-2-1 Pattern: 4 items - Full, 2-col, Full */
/* Uses 2-column grid */
section:has(a[href*="#layout-1-2-1"]) {
    display: grid !important;
    grid-template-columns: 1fr 1fr !important;
    grid-gap: 20px !important;
    align-items: center !important;
}

section:has(a[href*="#layout-1-2-1"])> :nth-child(2) {
    grid-column: 1 / -1 !important;
}

/* 1st content = full */
section:has(a[href*="#layout-1-2-1"])> :last-child {
    grid-column: 1 / -1 !important;
}

/* Last = full */

/* 1-3-1 Pattern: 5 items - Full, 3-col, Full */
/* Uses 3-column grid */
section:has(a[href*="#layout-1-3-1"]) {
    display: grid !important;
    grid-template-columns: 1fr 1fr 1fr !important;
    grid-gap: 20px !important;
    align-items: center !important;
}

section:has(a[href*="#layout-1-3-1"])> :nth-child(2) {
    grid-column: 1 / -1 !important;
}

/* 1st content = full */
section:has(a[href*="#layout-1-3-1"])> :last-child {
    grid-column: 1 / -1 !important;
}

/* Last = full */

/* 1-2-3-1 Pattern: 7 items - Full, 2-col, 3-col, Full */
/* Uses 6-column grid (LCM of 2,3) */
section:has(a[href*="#layout-1-2-3-1"]) {
    display: grid !important;
    grid-template-columns: repeat(6, 1fr) !important;
    grid-gap: 20px !important;
    align-items: center !important;
}

section:has(a[href*="#layout-1-2-3-1"])> :nth-child(2) {
    grid-column: 1 / -1 !important;
}

/* Item 1: full width */
section:has(a[href*="#layout-1-2-3-1"])> :nth-child(3) {
    grid-column: span 3 !important;
}

/* Item 2: half */
section:has(a[href*="#layout-1-2-3-1"])> :nth-child(4) {
    grid-column: span 3 !important;
}

/* Item 3: half */
section:has(a[href*="#layout-1-2-3-1"])> :nth-child(5) {
    grid-column: span 2 !important;
}

/* Item 4: third */
section:has(a[href*="#layout-1-2-3-1"])> :nth-child(6) {
    grid-column: span 2 !important;
}

/* Item 5: third */
section:has(a[href*="#layout-1-2-3-1"])> :nth-child(7) {
    grid-column: span 2 !important;
}

/* Item 6: third */
section:has(a[href*="#layout-1-2-3-1"])> :last-child {
    grid-column: 1 / -1 !important;
}

/* Item 7: full */

/* ========================================= */
/* MODULAR FLEX SYSTEM (Item-Level Control) */
/* ========================================= */
/* Usage: [](#layout-flex) on slide, then [Content](#w-50) on each blockquote */

/* Flex Container */
section:has(a[href*="#layout-flex"]) {
    display: flex !important;
    flex-wrap: wrap !important;
    gap: 20px !important;
    align-items: flex-start !important;
    align-content: flex-start !important;
}

/* Item Widths (#w-XX) */
/* These apply to blockquotes containing the tag */
blockquote:has(a[href*="#w-100"]) {
    flex: 0 0 100% !important;
    max-width: 100% !important;
}

blockquote:has(a[href*="#w-75"]) {
    flex: 0 0 calc(75% - 10px) !important;
    max-width: calc(75% - 10px) !important;
}

blockquote:has(a[href*="#w-66"]) {
    flex: 0 0 calc(66.66% - 10px) !important;
    max-width: calc(66.66% - 10px) !important;
}

blockquote:has(a[href*="#w-50"]) {
    flex: 0 0 calc(50% - 10px) !important;
    max-width: calc(50% - 10px) !important;
}

blockquote:has(a[href*="#w-33"]) {
    flex: 0 0 calc(33.33% - 10px) !important;
    max-width: calc(33.33% - 10px) !important;
}

blockquote:has(a[href*="#w-25"]) {
    flex: 0 0 calc(25% - 10px) !important;
    max-width: calc(25% - 10px) !important;
}

blockquote:has(a[href*="#w-20"]) {
    flex: 0 0 calc(20% - 10px) !important;
    max-width: calc(20% - 10px) !important;
}

/* Also support paragraph-level (for non-blockquote content) */
p:has(a[href*="#w-100"]) {
    flex: 0 0 100% !important;
    max-width: 100% !important;
}

p:has(a[href*="#w-75"]) {
    flex: 0 0 calc(75% - 10px) !important;
    max-width: calc(75% - 10px) !important;
}

p:has(a[href*="#w-66"]) {
    flex: 0 0 calc(66.66% - 10px) !important;
    max-width: calc(66.66% - 10px) !important;
}

p:has(a[href*="#w-50"]) {
    flex: 0 0 calc(50% - 10px) !important;
    max-width: calc(50% - 10px) !important;
}

p:has(a[href*="#w-33"]) {
    flex: 0 0 calc(33.33% - 10px) !important;
    max-width: calc(33.33% - 10px) !important;
}

p:has(a[href*="#w-25"]) {
    flex: 0 0 calc(25% - 10px) !important;
    max-width: calc(25% - 10px) !important;
}

p:has(a[href*="#w-20"]) {
    flex: 0 0 calc(20% - 10px) !important;
    max-width: calc(20% - 10px) !important;
}

/* Additional Slide-Level Layout Tags */

/* Split Reverse */
section:has(a[href*="#layout-split-rev"]) {
    display: grid !important;
    grid-template-columns: 1fr 1fr !important;
    grid-gap: 40px !important;
    align-items: center !important;
}

section:has(a[href*="#layout-split-rev"])>p:has(img) {
    grid-column: 1;
}

section:has(a[href*="#layout-split-rev"])>ul,
section:has(a[href*="#layout-split-rev"])>ol {
    grid-column: 2;
}

/* Title Center */
section:has(a[href*="#head-center"]) h1 {
    text-align: center !important;
    left: 0 !important;
    right: 0 !important;
    width: 100% !important;
}

/* Title Right */
section:has(a[href*="#head-right"]) h1 {
    text-align: right !important;
    left: auto !important;
    right: 40px !important;
}

/* No Header */
section:has(a[href*="#head-hide"]) h1 {
    display: none !important;
}

/* Compare Lists */
section:has(a[href*="#layout-compare-lists"]) {
    display: grid !important;
    grid-template-columns: 1fr 1fr !important;
    grid-gap: 20px !important;
}

/* Compare Text */
section:has(a[href*="#layout-compare-text"]) {
    display: grid !important;
    grid-template-columns: 1fr 1fr !important;
    grid-gap: 20px !important;
}

/* Gallery */
section:has(a[href*="#layout-gallery"]) {
    display: grid !important;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr)) !important;
    grid-gap: 15px !important;
    align-items: center !important;
}

/* Span First (first child spans) */
section:has(a[href*="#header-span"])> :first-child,
section:has(a[href*="#header-span"])>h1+* {
    grid-column: 1 / -1 !important;
}

/* Span Last (last child spans) */
section:has(a[href*="#footer-span"])> :last-child,
section:has(a[href*="#footer-span"])> :nth-last-child(2):not(footer) {
    grid-column: 1 / -1 !important;
}

/* Span Both (first and last span) */
section:has(a[href*="#wrap-span"])> :first-child,
section:has(a[href*="#wrap-span"])>h1+*,
section:has(a[href*="#wrap-span"])> :last-child {
    grid-column: 1 / -1 !important;
}

/* Box (grey background) */
section:has(a[href*="#layout-box"]) blockquote {
    background-color: #f8f9fa !important;
    border-left: 5px solid #6c757d !important;
    padding: 15px !important;
    margin-bottom: 15px !important;
    border-radius: 4px !important;
}

/* ========================================= */
/* OVERFLOW & SIZING CONTROL TAGS           */
/* ========================================= */

/* Compact Mode (#compact) - Reduces padding and font sizes */
section:has(a[href*="#compact"]) {
    padding: 80px 30px 30px !important;
    font-size: 22px !important;
}

section:has(a[href*="#compact"]) h1 {
    font-size: 32px !important;
}

section:has(a[href*="#compact"]) blockquote {
    padding: 10px !important;
    margin-bottom: 10px !important;
}

/* Dense Mode (#dense) - Even more compact */
section:has(a[href*="#dense"]) {
    padding: 60px 20px 20px !important;
    font-size: 18px !important;
    line-height: 1.2 !important;
}

section:has(a[href*="#dense"]) h1 {
    font-size: 28px !important;
}

section:has(a[href*="#dense"]) blockquote {
    padding: 8px !important;
    margin-bottom: 8px !important;
}

/* Fit Content (#fit) - Prevents overflow */
section:has(a[href*="#fit"]) {
    overflow: hidden !important;
}

section:has(a[href*="#fit"]) * {
    overflow: hidden !important;
    text-overflow: ellipsis !important;
}

/* Auto-Shrink Text (#shrink) */
section:has(a[href*="#shrink"]) {
    font-size: clamp(14px, 2.5vw, 28px) !important;
}

/* No Wrap (#nowrap) - Prevents text wrapping */
section:has(a[href*="#nowrap"]) blockquote,
section:has(a[href*="#nowrap"]) p {
    white-space: nowrap !important;
    overflow: hidden !important;
    text-overflow: ellipsis !important;
}

/* Scroll (#scroll) - Adds scrollbar if needed */
section:has(a[href*="#scroll"]) {
    overflow: auto !important;
}

/* Auto-Fit (#auto-fit) - Scales content to fit slide */
section:has(a[href*="#auto-fit"]) {
    font-size: clamp(12px, 2vw, 24px) !important;
    line-height: 1.2 !important;
}

section:has(a[href*="#auto-fit"]) h1 {
    font-size: clamp(20px, 3vw, 36px) !important;
}

section:has(a[href*="#auto-fit"]) h2 {
    font-size: clamp(14px, 2vw, 22px) !important;
    position: relative !important;
    top: auto !important;
    left: auto !important;
}

section:has(a[href*="#auto-fit"]) table {
    font-size: clamp(10px, 1.5vw, 18px) !important;
}

/* No Subtitle (#no-subtitle) - Removes H2 absolute positioning */
section:has(a[href*="#no-subtitle"]) h2 {
    display: none !important;
}

/* Relative Subtitle (#rel-subtitle) - Makes H2 flow with content */
section:has(a[href*="#rel-subtitle"]) h2 {
    position: relative !important;
    top: auto !important;
    left: auto !important;
    margin-bottom: 20px !important;
}</style>

[](#layout-title)

# Hassan Theme Demo
## Complete Feature Showcase

---

[](#layout-split)
[Slide Layouts](#footer)

# Basic Split Layout
**`[](#layout-split)` - Text Left, Image Right**

*   This is the default 2-column layout.
*   Text automatically goes to the left.
*   Images automatically go to the right.
*   Perfect for explanatory slides.

![#graphics-70](figures/fig_2level_schematic.png)

---

[](#layout-split-rev)
[Split Reverse](#footer-left)

# Split Reverse Layout
**`[](#layout-split-rev)` - Image Left, Text Right**

![#graphics-70](figures/fig_2level_schematic.png)

*   This flips the standard layout.
*   Image now goes to the left.
*   Text flows to the right.
*   Great for visual variety.

---

[](#layout-3col)
[3-Column Grid](#footer-center)

# Three Column Grid
**`[](#layout-3col)`**

> **Column 1**
> First column content with detailed information.

> **Column 2**
> Second column with more content.

> **Column 3**
> Third column completing the layout.

---

[](#layout-2x2)
[2x2 Grid](#footer)

# 2x2 Grid Layout
**`[](#layout-2x2)` - 4 Equal Boxes**

> **Q1 - Top Left**
> First quadrant content.

> **Q2 - Top Right**
> Second quadrant content.

> **Q3 - Bottom Left**
> Third quadrant content.

> **Q4 - Bottom Right**
> Fourth quadrant content.

---

[](#layout-1-2)
[1-2 Pattern](#footer-left)

# 1-2 Pattern Layout
**`[](#layout-1-2)` - Header Row, Then 2 Columns**

> **Introduction (Full Width)**
> This block automatically spans both columns below.

> **Left Column**
> Detailed content here.

> **Right Column**
> More details here.

---

[](#layout-flex)
[Modular Flex](#footer-center)

# Modular Flex System
**`[](#layout-flex)` + `#w-XX` on each item**

> **[Full Width Header](#w-100)**
> This item is 100% width.

> **[Half Width](#w-50)**
> 50% width item.

> **[Half Width](#w-50)**
> Another 50% item.

> **[Third Width](#w-33)**
> 33% width.

> **[Third Width](#w-33)**
> 33% width.

> **[Third Width](#w-33)**
> 33% width.

---

[](#layout-split)
[Semantic Boxes](#footer)

# Semantic Box Types
**Smart Tags for Colored Callout Boxes**

> **[Theorem 1](#box-theorem)**
> Blue box for theorems and propositions.

> **[Definition](#box-def)**
> Green box for definitions.

> **[Warning](#box-alert)**
> Red box for alerts and important notes.

---

[](#layout-split)
[Text Styling](#footer-left)

# Text Colors and Sizes
**Smart Tags for Typography**

**Colors:**
*   This is **[Red Text](#color-red)**.
*   This is **[Blue Text](#color-blue)**.
*   This is **[Green Text](#color-green)**.
*   This is **[Purple Text](#color-purple)**.
*   This is **[Grey Text](#color-grey)**.

**Sizes:**
*   [Tiny Text](#font-tiny)
*   [Small Text](#font-small)
*   [Large Text](#font-large)
*   [Huge Text](#font-huge)

---

[](#layout-split)
[Graphics Sizing](#footer-center)

# Graphics Sizing
**`![#graphics-XX](src)` for Any Percentage**

![#graphics-50](figures/fig_2level_schematic.png)

*   `#graphics-50` = 50% width
*   Supports 1-100% sizes
*   **Semantic aliases:**
    *   `#img-tiny` = 20%
    *   `#img-small` = 40%
    *   `#img-medium` = 60%
    *   `#img-large` = 80%

---

[](#layout-split)
[GIF Support](#footer-left)

# Animated GIF Support
**GIFs work with all sizing tags!**

![#graphics-60](figures/demo_sine.gif)

*   Use same syntax as images
*   `![#graphics-60](file.gif)`
*   Supports all `#graphics-XX` sizes
*   Animations play automatically

---
[](#layout-split)
[](#head-center)
[Head Center](#footer)

# This Title is Centered
**`[](#head-center)`**

The title above is centered using the `#head-center` tag.
Useful for section dividers and announcements.

---

[](#head-hide)
[Head Hide Demo](#footer-left)

**This Slide Has No Visible Title!**
**`[](#head-hide)` - Title is Hidden**

The H1 title is completely hidden on this slide.
Content starts at the top of the slide.
Great for full-screen content or quotes.

---

[](#layout-split)
[Math Support](#footer)

# KaTeX Math Support
**Full LaTeX Math Rendering**

*   Inline math: $E = mc^2$
*   Display math:

$$
\boxed{\hat{H} = \hbar\omega\left(a^\dagger a + \frac{1}{2}\right)}
$$

> **[Theorem](#box-theorem)**
> The eigenvalues are $E_n = \hbar\omega(n + 1/2)$

---

[](#layout-flex#compact)
[Compact Mode](#footer-left)

# Compact Mode Demo
**`#compact` - Fits More Content**

> **[Item A](#w-50)**
> Reduced padding.

> **[Item B](#w-50)**
> Smaller fonts (22px).

> **[Item C](#w-33)**
> Third width.

> **[Item D](#w-33)**
> Third width.

> **[Item E](#w-33)**
> Third width.

> **[Footer](#w-100)**
> All fits on one slide!

---

[](#layout-flex#dense)
[Dense Mode](#footer-center)

# Dense Mode Demo
**`#dense` - Maximum Content**

> **[A](#w-25)**
> 25%

> **[B](#w-25)**
> 25%

> **[C](#w-25)**
> 25%

> **[D](#w-25)**
> 25%

> **[E](#w-20)**
> 20%

> **[F](#w-20)**
> 20%

> **[G](#w-20)**
> 20%

> **[H](#w-20)**
> 20%

> **[I](#w-20)**
> 20%

---

[](#layout-flex)
[Custom 2-3-1](#footer)

# Custom Pattern: 2-3-1
**Build ANY layout with #w-XX tags**

> **[Left Half](#w-50)**
> Row 1, Column 1.

> **[Right Half](#w-50)**
> Row 1, Column 2.

> **[Third A](#w-33)**
> Row 2, Column 1.

> **[Third B](#w-33)**
> Row 2, Column 2.

> **[Third C](#w-33)**
> Row 2, Column 3.

> **[Full Footer](#w-100)**
> Row 3 - spans everything.

---

[](#layout-split)
[Multi-Tag Composition](#footer-center)

# Combining Multiple Tags
**`[Text](#tag1#tag2)` Syntax**

> **[Big Blue Theorem](#box-theorem#font-large)**
> Tags can be combined for complex styling.

> **[Red Alert](#box-alert#color-red)**
> Multiple tags work together.

*   Slide-level: `[](#layout-split#layout-box)`
*   Item-level: `[Text](#color-red#font-huge)`

---

[](#layout-split)
[Footer Positions](#footer-center)

# Footer Positioning
**Three Footer Placement Options**

| Tag | Position |
|-----|----------|
| `[Text](#footer)` | Right (default) |
| `[Text](#footer-left)` | Left |
| `[Text](#footer-center)` | Center |

This slide uses `#footer-center`.

---

[](#compact)
[Summary](#footer-center)

# Summary

| Category | Features |
|----------|----------|
| **Layouts** | split, split-rev, 3col, 4col, 5col, 2x2, 1-2, 1-3, 2-1, 3-1, flex |
| **Head** | center, right, hide, title |
| **Footer** | left, center, right |
| **Boxes** | theorem, def, alert, grey, boxed |
| **Colors** | red, blue, green, purple, grey |
| **Fonts** | tiny, small, normal, large, huge |
| **Graphics** | 1-100%, img-tiny/small/medium/large/full |
| **Flex Widths** | w-100, w-75, w-66, w-50, w-33, w-25, w-20 |
| **Overflow** | compact, dense, fit, shrink |

[End of Demo](#footer-center)

