# Design System Document: The Rhythmic Studio

## 1. Overview & Creative North Star
**Creative North Star: "The Neon Pulse"**

This design system moves away from the static, flat nature of traditional educational apps and embraces the kinetic energy of a live performance. We are not building a textbook; we are building a stage. The design breaks the standard "template" look by using **Kinetic Asymmetry**—where progress bars might tilt, and drum pads feel like they are floating in a smoke-filled studio. 

By overlapping high-contrast typography with semi-transparent surfaces and "glowing" interactive elements, we create a sense of rhythmic depth. This system is designed to feel as responsive as a snare hit: immediate, tactile, and vibrating with energy.

---

## 2. Colors
Our palette mimics a darkened studio illuminated by neon equipment lights. The contrast between the deep `#0e0e0e` background and the "electric" accents drives the user's focus toward action.

*   **Primary (`#89acff`) & Secondary (`#fd9000`):** These represent the "electric blue" and "punchy orange." Use Primary for rhythmic guidance and Secondary for peak energy moments (like hitting a high score).
*   **Tertiary (`#f3ffcd`):** This is our "vibrant lime." Use this sparingly for "Perfect" hit indicators or critical success states to ensure it retains its visual punch.

**The "No-Line" Rule**
Traditional borders are forbidden. They create a "grid" feel that kills the flow. Instead, define sections using background shifts. A `surface-container-low` section sitting on a `surface` background is enough to signify a new area. If you need a break, use a 32px vertical gap instead of a line.

**Surface Hierarchy & Nesting**
Treat the UI as a series of physical layers.
*   **Base:** `surface` (#0e0e0e)
*   **The Stage:** `surface-container` (#1a1919) for main content areas.
*   **The Equipment:** `surface-container-highest` (#262626) for interactive drum pads or cards. 

**The "Glass & Gradient" Rule**
To achieve a "professional studio" polish, floating controls must use Glassmorphism. Use `surface-container-high` at 60% opacity with a 20px backdrop blur. For primary CTAs, apply a subtle linear gradient from `primary` (#89acff) to `primary-container` (#739eff) to give the button "weight" and a metallic, hardware-like sheen.

---

## 3. Typography
Typography in this system is a percussion instrument. We use two distinct voices to create rhythm.

*   **The Lead (Display & Headline):** `spaceGrotesk`. This font is architectural and bold. Use `display-lg` for massive, immersive numbers (like a countdown) and `headline-md` for screen titles. Its wide stance mimics the "wide" sound of a crash cymbal.
*   **The Rhythm Section (Body & Title):** `beVietnamPro`. This is our workhorse. It is clean and legible at high speeds. Use `body-lg` for instructional text to ensure readability while the user is actively drumming.

**Visual Identity through Hierarchy**
By pairing a massive `display-lg` stat next to a tiny, uppercase `label-md` descriptor, we create "Syncopation"—a visual rhythm that feels modern and editorial rather than a standard list of data.

---

## 4. Elevation & Depth
Depth is achieved through **Tonal Layering**, mimicking how light falls on a drum kit in a dark room.

*   **The Layering Principle:** Instead of shadows, place a `surface-container-lowest` card on a `surface-container-low` section. The subtle shift in hex value creates a natural lift.
*   **Ambient Shadows:** For floating drum pads that need to "pop," use extra-diffused shadows.
    *   *Shadow Color:* `on-surface` (#ffffff) at 4% opacity. 
    *   *Blur:* 40px to 60px.
    *   This creates a "glow" effect rather than a "drop" effect, making the component look like it’s backlit by studio LEDs.
*   **The "Ghost Border" Fallback:** If a component (like a search bar) risks disappearing, use a "Ghost Border": `outline-variant` (#494847) at **15% opacity**. Never use a 100% opaque border.

---

## 5. Components

### **Drum Pad Buttons (Primary & Secondary)**
These are the heart of the app. They must feel tactile.
*   **Shape:** `md` (0.75rem) roundedness.
*   **Styling:** Use the `primary` to `primary-container` gradient. 
*   **Interaction:** On press, the component should scale down to 0.95 and increase its inner "glow" (ambient shadow) to mimic being struck.

### **Rhythm Cards**
For lesson cards, forbid divider lines.
*   **Structure:** Use `surface-container-high`. 
*   **Imagery:** Use overlapping elements (e.g., a drumstick image breaking the "top" boundary of the card) to create an editorial, high-end feel.
*   **Spacing:** Use 24px internal padding to give the content "room to breathe."

### **Dynamic Input Fields**
*   **Style:** No background fill. Only a bottom "Ghost Border" (15% opacity `outline-variant`).
*   **Active State:** The border transitions to 100% `primary` (#89acff) with a soft glow.

### **Interactive Chips**
*   **Selection Chips:** Use `full` roundedness.
*   **Unselected:** `surface-container-highest` background with `on-surface-variant` text.
*   **Selected:** `secondary` (#fd9000) background with `on-secondary` (#462400) text.

### **The "Metronome" Progress Bar**
A custom component unique to this system. Instead of a flat bar, use a series of vertical blocks. As the rhythm progresses, blocks transition from `surface-variant` to `tertiary` (#f3ffcd) with a "strobe" animation.

---

## 6. Do’s and Don’ts

**Do:**
*   **Do** use intentional asymmetry. A title can be slightly offset to the left of a card to create a "pushed" rhythmic feel.
*   **Do** use `tertiary` for success moments. It’s our brightest "neon" and should feel like a reward.
*   **Do** lean into Glassmorphism for overlays. It maintains the "Studio" depth.

**Don’t:**
*   **Don’t** use pure black (#000000) for surfaces unless it’s the `surface-container-lowest` background. Use the `surface` (#0e0e0e) to maintain tonal richness.
*   **Don’t** use standard Material shadows. They look "office-like" and "corporate." Only use high-blur, low-opacity ambient glows.
*   **Don’t** use dividers or 1px borders. Use white space or tonal shifts to separate content. If it looks like a spreadsheet, it’s wrong.

---
*Director's Final Note: Ensure every transition has a "bounce" or "snap" to it. This app should feel like it's keeping time with the user.*