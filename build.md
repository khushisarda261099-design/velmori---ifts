# Velmori Gifts - Project Specification & Status

This document provides a comprehensive overview of the **Velmori Gifts** codebase. It is designed to help AI agents and developers understand the architecture, design patterns, and structure of the project efficiently without reading the entire codebase, saving token usage.

---

## 🚀 Project Overview
* **Project Name:** Velmori Gifts
* **Description:** A premium, elegant, and highly interactive single-page landing website for a boutique gift shop specializing in curated hampers, handmade bouquets, jewellery, and custom gifts.
* **Founder:** Ruchita Tawade
* **Contact Info:** +91 93566 64679 / WhatsApp link integrated.

---

## 🛠️ Technology Stack
1. **HTML5:** Semantic markup structure.
2. **CSS3 (Vanilla):** Custom styles, layout structures (Flexbox & Grid), glassmorphism, and modern transitions/animations. No external frameworks are used.
3. **Vanilla JavaScript:** 
   - **Lenis Smooth Scrolling:** Implemented for premium scroll physics.
   - **Video Scrubbing Animation:** Binds a background MP4 video's `currentTime` to the user's scroll progress via Lenis.
   - **Ripple Mouse Trail:** An elegant gold-rose expanding ring trail using a high-performance 40-element DOM object pool to avoid garbage collection jank.
   - **Canvas Particle Rendering:** Soft falling petals in the background.
4. **Typography (Google Fonts):**
   - *Cormorant Garamond*: Serif font (600 semi-bold) for headings, logos, and italic emphasizes.
   - *Lato*: Sans-serif font (400 regular) for readability in body copy, labels, and stats.

---

## 🎨 Design System & Customizations

### 1. Color Palette (CSS Variables)
* `--blush`: `#F5D5C8` (Accent backgrounds)
* `--cream`: `#FDF6F0` (Main page background)
* `--gold`: `#C9A84C` (Primary highlights & borders)
* `--rose`: `#B56070` (Secondary icons/labels)
* `--taupe`: `#8B7B6B` (Muted description/body text)
* `--dark`: `#3D2B2B` (Primary text & dark backgrounds)

### 2. Branding & Assets
* **Logo:** The brand crest is stored at `images/logo.png`. It is displayed inside custom gold-rimmed circular containers (`border-radius: 50%; overflow: hidden;`) to mask the rectangular background in the Navbar, Hero Badge (text-free floating seal), and Footer.
* **Products:** Product images are stored as standard image files (`.jpeg`/`.png`) inside the `images/` directory (e.g., `birthday_hamper.jpeg`, `apology_hamper.jpeg`, `bouque_pipe_cleaner.jpeg`). Base64 inline strings have been removed for performance.
* **Videos:** Scroll animation videos are stored in the `media/` directory.

---

## 📂 Codebase Directory Structure
```
velmori-gifts/
├── index.html        # Core file: Contains all markup, styles, and script logic.
├── images/           # Contains product images and brand logo (logo.png).
├── media/            # Contains video assets for scroll animations.
├── README.md         # Public README for repository overview and deployment info.
└── build.md          # This file (AI developer guidelines & project status).
```

---

## 🏗️ Detailed Architecture of `index.html`

### 1. Styles Block (`<style>` in `<head>`)
* Implements a responsive layout with modern glassmorphism (`backdrop-filter`).
* **Ripple Trail:** Defines `.ripple` elements for the custom 40-element DOM pool trail.
* **Scroll Lock:** `html { scroll-behavior: auto !important }` ensures no conflict with the Lenis smooth scrolling.

### 2. Markup Structure (`<body>`)
* **Ripple Container (`#ripple-container`):** Holds the DOM elements for the elegant mouse trail.
* **Canvas Element (`#petals-canvas`):** Falling petal background.
* **Navigation Bar (`.nav`):** Fixed-top container with frosted glass effect and circular logo mask.
* **Hero Section (`.hero`):** Interactive central brand badge functioning as a floating text-free circular seal containing the VG logo.
* **Video Scrubbing Section (`#scroll-container`):** A sticky container mapping the scroll position to the playback time of the background video, overlaying animated text slides.
* **Products Grid (`.products`):** Multi-column CSS grid rendering product cards linked to local `/images`.

### 3. JavaScript Logic (`<script>` at footer)
* **Lenis Integration:** Overrides native scroll and drives the custom scroll loop via `requestAnimationFrame`.
* **Video Scrubbing:** Uses `lenis.on('scroll')` to calculate the percentage of the `#scroll-container` crossed and updates the video's `currentTime`.
* **Ripple Trail:** High-performance loop updating the transform, opacity, and scale of 40 pre-created DOM rings based on cursor movement distance threshold (40px).
* **Petal Fall Animation:** `Petal` class managing variables for position, size, wind drift, and color.
* **Scroll-driven Entry Animations:** `IntersectionObserver` observing elements for slide-up/fade-in effects.

---

## ⚡ Current Status & Recent Changes (June 2026)
* **Completed:** 
  * Replaced base64 images with local files inside `images/`.
  * Added sticky video scroll-scrubbing section.
  * Replaced liquid warp cursor with an elegant DOM-pool based gold-rose ripple.
  * Masked the brand logo in perfect circles across the site and simplified the hero badge into a pure logo seal.
  * Upgraded typography weights for higher contrast and readability.
