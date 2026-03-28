# Design System Specification: High-Performance Voxel Minimalism

## 1. Overview & Creative North Star
### Creative North Star: "The Refracted Block"
This design system moves beyond the "pixel art" cliché into a sophisticated, high-fidelity interpretation of a voxel-based universe. We are not building a game; we are building a premium digital environment that feels like Minecraft with "RTX-On"—where light, depth, and glass-like refraction replace flat textures. 

The system achieves an editorial, high-end feel through **Rigid Brutalism** (perfect 90-degree corners) juxtaposed with **Ethereal Lighting** (neon glows and glassmorphism). We break the "template" look by using extreme typographic scales and intentional asymmetry, treating the 12-column grid as a canvas for "stacked" physical layers rather than a flat container.

---

## 2. Colors & Tonal Depth
Our palette is divided into two distinct environmental modes: **Lush Overworld (Day)** and **The Void (Night)**. Both rely on high-chroma accents set against deep, atmospheric surfaces.

### Surface Hierarchy & Nesting
To maintain a premium feel, we strictly enforce the **"No-Line" Rule**. Boundaries are defined by shifting between `surface` tiers. 
- **Surface (Base):** `#0e0e0e` – The fundamental bedrock.
- **Surface-Container-Low:** `#131313` – Used for large sectioning.
- **Surface-Container-High:** `#201f1f` – Used for interactive modules.
- **Surface-Container-Highest:** `#262626` – The "top-most" layer for modals or tooltips.

### The Glass & Gradient Rule
All primary containers must utilize **Glassmorphism**. 
- **Token Application:** `surface_variant` at 60% opacity with a `backdrop-filter: blur(10px)`.
- **Signature Glows:** Use `primary` (#69f6b8) for active states and `secondary` (#c97cff) for "End-tier" luxury items. These aren't just colors; they are light sources. Apply a `0px 0px 20px` spread to mimic ray-traced emissive lighting.

---

## 3. Typography
We balance the "Blocky" heritage with modern editorial legibility.

- **Display & Headline (Space Grotesk):** Our "Modern Brutalist" face. Use `display-lg` (3.5rem) for high-impact hero titles. It feels engineered and precise.
- **The "Artifact" Font (Pixel/Blocky):** Reserved exclusively for short, uppercase utility titles (e.g., "HACK-CRAFT", "INVENTORY"). It acts as a brand signature, not a reading font.
- **Body & Label (Manrope):** Our workhorse. Manrope provides a clean, humanist contrast to the rigid geometry of the UI.

**Hierarchy Tip:** Use `headline-lg` in `primary` color for section headers to create a "Level Start" feel, while keeping body text in `on_surface_variant` for a soft, readable contrast.

---

## 4. Elevation & Depth
Depth is not simulated with drop shadows; it is simulated with **Tonal Layering** and **Refraction**.

- **The Layering Principle:** A "floating" card should be `surface_container_lowest` sitting on a `surface_container_low` background. This creates a subtle "inset" or "lifted" look without visual clutter.
- **Ambient Glows:** Instead of grey shadows, use a `4%-8%` opacity shadow tinted with `surface_tint` (#69f6b8). This mimics the way green grass reflects light onto a white surface in an RTX environment.
- **The Ghost Border:** For accessibility on glass elements, use `outline_variant` at **15% opacity**. This creates a "specular highlight" on the edge of the glass block rather than a heavy border.

---

## 5. Components

### Buttons: The "Extruded Block"
- **Primary:** `primary` background with `on_primary` text. Use a hard, 2px bottom offset in `primary_container` to simulate a 3D block face. 
- **Interactive State:** On hover, the "block" should depress (transform: translateY(2px)) and trigger a `primary_dim` outer glow.
- **Rounding:** Strictly `0px`. Everything is a voxel.

### Inventory-Grid Cards
- **Structure:** Use a 1:1 aspect ratio for image containers. 
- **Styling:** `surface_container_low` background with a `Ghost Border`. No dividers.
- **Prizes:** Featured prizes use a `secondary` (purple) glow to signify "Epic/End-tier" loot.

### The Villager Toggle
- **Visuals:** A custom toggle where the thumb is a simplified, 3D-style brown block (the "Villager Nose") and the track is `surface_container_high`.
- **Active State:** The track shifts to `primary_container` when toggled "On."

### Input Fields
- **Style:** Underlined only, or fully enclosed in a `surface_container_lowest` box.
- **Focus State:** The bottom border transforms into a 2px `primary` line with a subtle emissive glow.

---

## 6. Do's and Don'ts

### Do:
- **Use Vertical White Space:** Utilize the `spacing.12` (4rem) and `spacing.16` (5.5rem) tokens to let elements breathe. High-end design requires "negative space" to feel intentional.
- **Embrace Asymmetry:** Offset your 12-column grid. A card that spans columns 2-7 creates more visual interest than one perfectly centered.
- **Layer Glass:** Stack a glass container on top of a gradient background for maximum "RTX" depth.

### Don't:
- **No 1px Solid Borders:** Never use a high-contrast border to separate content. Use a background color shift or a `1.5` (0.5rem) gap.
- **No Rounding:** Do not use `border-radius`. Even the "Villager" toggle must be composed of rectangles.
- **No Generic Shadows:** Avoid the `rgba(0,0,0,0.5)` drop shadow. If it doesn't look like light is hitting a surface, don't use it.
- **Limit the Pixel Font:** Never use the blocky font for more than three words. It is a graphic element, not a medium for information.

---

## 7. Layout & Grid
- **Desktop:** 12-column grid with `spacing.6` (2rem) gutters. 
- **The "Overhang" Effect:** Allow hero imagery or 3D block icons to "break" the grid containers, spilling over into the margins to create a sense of physical space.
- **Mobile:** 1-column stack with `spacing.4` (1.4rem) side margins. Glass elements should maintain 100% width to maximize the "frosted" area.