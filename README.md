# Hassan Theme v1.0

A pure Markdown-based Marp presentation theme using Smart Tags to control layouts, styling, and content without HTML or Marp directives.

## Files
| File | Purpose |
|------|---------|
| `hassan_theme.css` | The complete CSS theme |
| `demo.md` | Demo presentation showing all features |
| `figures/` | Sample images and GIFs |


## Quick Start

```markdown
---
marp: true
theme: default
paginate: true
math: katex
---

<style>
/* Paste contents of hassan_theme.css here */
</style>

[](#layout-split)
[Footer Text](#footer)

# My Slide Title

> **[Theorem](#box-theorem)**
> Content goes here.

![#graphics-50](image.png)
```

---

## Slide-Level Layout Tags

Place these at the top of any slide to control the overall layout.

### Basic Layouts

| Tag | Effect |
|-----|--------|
| `[](#layout-split)` | 2-column: text left, image right |
| `[](#layout-split-rev)` | 2-column: image left, text right |
| `[](#layout-3col)` | 3-column grid |
| `[](#layout-4col)` | 4-column grid |
| `[](#layout-5col)` | 5-column grid |
| `[](#layout-gallery)` | Auto-fit image gallery |

### Pattern Layouts

| Tag | Items | Pattern |
|-----|-------|---------|
| `[](#layout-2x2)` | 4 | 2×2 equal grid |
| `[](#layout-1-2)` | 3 | Full row → 2-col row |
| `[](#layout-1-3)` | 4 | Full row → 3-col row |
| `[](#layout-2-1)` | 3 | 2-col row → Full row |
| `[](#layout-3-1)` | 4 | 3-col row → Full row |
| `[](#layout-1-2-1)` | 4 | Full → 2-col → Full |
| `[](#layout-1-3-1)` | 5 | Full → 3-col → Full |
| `[](#layout-1-2-3-1)` | 7 | Full → 2-col → 3-col → Full |

### Modular Flex System

For custom layouts, use `#layout-flex` with item-level width tags.

```markdown
[](#layout-flex)

> **[Header](#w-100)**
> Full width.

> **[Left](#w-50)**
> Half width.

> **[Right](#w-50)**
> Half width.
```

| Item Tag | Width |
|----------|-------|
| `#w-100` | 100% |
| `#w-75` | 75% |
| `#w-66` | 66% (two-thirds) |
| `#w-50` | 50% (half) |
| `#w-33` | 33% (third) |
| `#w-25` | 25% (quarter) |
| `#w-20` | 20% (fifth) |

---

## Title/Header Tags

| Tag | Effect |
|-----|--------|
| `[](#head-center)` | Center-aligned title |
| `[](#head-right)` | Right-aligned title |
| `[](#head-hide)` | Hide the H1 title completely |

---

## Footer Tags

| Tag | Position |
|-----|----------|
| `[Text](#footer)` | Right (default) |
| `[Text](#footer-left)` | Left |
| `[Text](#footer-center)` | Center |

---

## Semantic Box Tags

Apply to blockquote titles for colored callout boxes.

| Tag | Color | Use Case |
|-----|-------|----------|
| `[Title](#box-theorem)` | Blue | Theorems, propositions |
| `[Title](#box-def)` | Green | Definitions |
| `[Title](#box-alert)` | Red | Warnings, important notes |
| `[Title](#box-grey)` | Grey | Neutral boxes |
| `[Title](#boxed)` | Border only | Framed content |

**Example:**
```markdown
> **[Theorem 1](#box-theorem)**
> Let $V$ be a vector space...
```

---

## Text Color Tags

| Tag | Color |
|-----|-------|
| `[Text](#color-red)` | Red |
| `[Text](#color-blue)` | Blue |
| `[Text](#color-green)` | Green |
| `[Text](#color-purple)` | Purple |
| `[Text](#color-grey)` | Grey |

---

## Font Size Tags

| Tag | Size |
|-----|------|
| `[Text](#font-tiny)` | 60% |
| `[Text](#font-small)` | 80% |
| `[Text](#font-normal)` | 100% |
| `[Text](#font-large)` | 120% |
| `[Text](#font-huge)` | 150% |

---

## Graphics Sizing Tags

### Percentage-Based (1-100%)

```markdown
![#graphics-50](image.png)     <!-- 50% width -->
![#graphics-75](image.png)     <!-- 75% width -->
```

### Semantic Aliases

| Tag | Width |
|-----|-------|
| `#img-tiny` | 20% |
| `#img-small` | 40% |
| `#img-medium` | 60% |
| `#img-large` | 80% |
| `#img-full` | 100% |

### With Caption

```markdown
![Caption Text](image.png)
[Caption](#graphics-50)
```

---

## Composing Multiple Tags

Tags can be combined using `#tag1#tag2` syntax.

```markdown
> **[Big Red Warning](#box-alert#font-large)**
> Important content.

[](#layout-split#layout-box)  <!-- 2-col with grey boxes -->
```

---

## Files

| File | Purpose |
|------|---------|
| `hassan_theme.css` | The complete CSS theme (paste into `<style>` block) |
| `Layout_Test_Deck.md` | Demo deck showcasing all features |
| `SMART_TAG_REFERENCE.md` | This documentation |

---

## Usage in New Presentations

1. Create a new `.md` file
2. Add Marp frontmatter
3. Paste the contents of `hassan_theme.css` in a `<style>` block
4. Use Smart Tags as documented above

**Minimal Template:**
```markdown
---
marp: true
theme: default
paginate: true
math: katex
---

<style>
/* PASTE hassan_theme.css CONTENTS HERE */
</style>

[](#layout-split)
[Slide 1](#footer)

# My Presentation

Content here.

---

# Slide 2

More content.
```
