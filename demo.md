---
marp: true
theme: default
paginate: true
math: katex
---

<style>
/* Hassan Theme v1.0 - Paste hassan_theme.css contents here */
/* Or use: @import url('./hassan_theme.css'); (may not work in Marp CLI) */
</style>

[](#layout-title)

# Hassan Theme Demo
## Version 1.0

---

[](#layout-split)
[Layouts Demo](#footer)

# Split Layout
**`[](#layout-split)`**

*   Text goes left
*   Images go right
*   Perfect for explanatory slides

![#graphics-60](figures/fig_2level_schematic.png)

---

[](#layout-3col)
[3-Column Demo](#footer-center)

# Three Columns
**`[](#layout-3col)`**

> **Column 1**
> First content.

> **Column 2**
> Second content.

> **Column 3**
> Third content.

---

[](#layout-flex)
[Flex Demo](#footer-left)

# Modular Flex
**`[](#layout-flex)` + `#w-XX`**

> **[Full Width](#w-100)**
> 100% width.

> **[Half](#w-50)**
> 50%.

> **[Half](#w-50)**
> 50%.

> **[Third](#w-33)**
> 33%.

> **[Third](#w-33)**
> 33%.

> **[Third](#w-33)**
> 33%.

---

[](#layout-split)
[Semantic Boxes](#footer)

# Box Types
**Smart Tags for Colored Boxes**

> **[Theorem](#box-theorem)**
> Blue box for theorems.

> **[Definition](#box-def)**
> Green box for definitions.

> **[Alert](#box-alert)**
> Red box for warnings.

---

[](#layout-split)
[GIF Support](#footer-left)

# Animated GIFs
**Same sizing tags work!**

![#graphics-60](figures/demo_sine.gif)

*   `![#graphics-60](file.gif)`
*   Animations play automatically

---

[](#compact)
[Summary](#footer-center)

# Summary

| Category | Tags |
|----------|------|
| **Layouts** | split, split-rev, 3col, 4col, 5col, 2x2, flex |
| **Flex Widths** | w-100, w-75, w-66, w-50, w-33, w-25, w-20 |
| **Head** | center, right, hide, title |
| **Footer** | left, center, right |
| **Boxes** | theorem, def, alert, grey, boxed |
| **Colors** | red, blue, green, purple, grey |
| **Fonts** | tiny, small, normal, large, huge |
| **Graphics** | 1-100%, img-tiny/small/medium/large/full |
| **Overflow** | compact, dense, fit, shrink |

