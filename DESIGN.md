# Design System Document: The Executive Monolith

## 1. Overview & Creative North Star: "The Architectural Horizon"
This design system is a digital translation of the Dubai skyline at twilight—imposing, precise, and unashamedly luxurious. We are moving away from the "friendly SaaS" aesthetic toward a **High-End Editorial** experience. Our Creative North Star is **The Architectural Horizon**. 

The system rejects the "web-as-a-grid" mentality in favor of a "web-as-an-environment" approach. We utilize intentional asymmetry, razor-sharp edges (0px border radius), and high-contrast tonal layering. The goal is to make the user feel as though they are navigating a premium physical space—a mahogany-clad boardroom or a glass-walled penthouse overlooking the Burj Khalifa.

---

## 2. Colors: Tonal Depth & Signature Textures
Our palette is anchored by the weight of Deep Navy and the ethereal quality of Silver accents. We define space not with lines, but with light.

### The "No-Line" Rule
**Explicit Instruction:** Traditional 1px solid borders are strictly prohibited for sectioning. Boundaries must be defined solely through background color shifts or subtle tonal transitions. Use `surface-container-low` (#f3f4f5) against a `background` (#f8f9fa) to create structural definition.

### Surface Hierarchy & Nesting
Treat the UI as a series of nested architectural planes. Use the `surface-container` tiers to create depth:
*   **Level 0 (Base):** `surface` (#f8f9fa)
*   **Level 1 (Sub-sections):** `surface-container-low` (#f3f4f5)
*   **Level 2 (Cards/Modules):** `surface-container-lowest` (#ffffff)
*   **Level 3 (Elevated Accents):** `surface-container-high` (#e7e8e9)

### The "Glass & Gradient" Rule
To evoke the reflective glass of corporate skyscrapers, use semi-transparent surface colors with `backdrop-blur`.
*   **Floating Elements:** Use `surface` at 80% opacity with a 20px blur.
*   **Signature Textures:** Apply a linear gradient (135°) from `primary` (#00113a) to `primary-container` (#002366) for hero sections and CTAs to provide the "visual soul" that flat blocks lack.

---

## 3. Typography: The Executive Voice
We use a high-contrast pairing of **Manrope** for impact and **Inter** for precision.

*   **Display & Headline (Manrope):** The "Architectural" font. Used for large, sweeping statements. It conveys authority and modern luxury.
*   **Body & Labels (Inter):** The "Precision" font. Used for data, executive summaries, and functional UI. It ensures maximum readability and a professional, hospitality-executive feel.

**Scale Philosophy:** We utilize extreme scale shifts. A `display-lg` headline should sit comfortably near `body-sm` metadata to create an editorial, "poster-like" layout.

---

## 4. Elevation & Depth: Tonal Layering
In this system, "Elevation" does not mean "Shadow." It means "Contrast."

*   **The Layering Principle:** Depth is achieved by stacking. Place a `surface-container-lowest` card on a `surface-container-low` section to create a natural "lift" without a single drop shadow.
*   **Ambient Shadows:** If a floating effect is mandatory (e.g., a modal), use an ultra-diffused shadow: `box-shadow: 0 20px 50px rgba(0, 17, 58, 0.06);`. The shadow color is a tinted version of `primary`, mimicking ambient light trapped between layers.
*   **The "Ghost Border" Fallback:** If accessibility requires a container edge, use a "Ghost Border": `outline-variant` (#c5c6d2) at **15% opacity**. Never use a 100% opaque border.
*   **Sharpness:** All `Roundedness` tokens are set to **0px**. This is a non-negotiable signature of the system; it reflects the sharp edges of modern architecture.

---

## 5. Components: Precision Tooling

### Buttons
*   **Primary:** Linear gradient (`primary` to `primary-container`), 0px radius, uppercase `label-md` with 1px letter spacing.
*   **Secondary:** Ghost style. No fill, `outline` (#757682) at 20% opacity, sharp edges.
*   **Tertiary:** Text only, using `on_primary_container` (#758dd5) with a 1px underline that appears only on hover.

### Cards & Lists
*   **Constraint:** Forbid divider lines.
*   **Alternative:** Use 48px or 64px of vertical whitespace (Spacing Scale) to separate list items. For cards, use a subtle background shift from `surface-container-lowest` to `surface-container-low` on hover.

### Input Fields
*   **Styling:** Underline-only style. A 2px bottom bar using `outline-variant`. On focus, the bar transitions to `primary` (#00113a).
*   **Labels:** Floating labels using `label-sm` in `on_surface_variant` (#444650).

### Additional Signature Component: The "Skyline Navigation"
A vertical side-navigation bar using `tertiary` (#131515) as the background. High-contrast white text (`on_tertiary`) with a silver (`tertiary_fixed_dim`) active state indicator—a simple 2px vertical line on the far left.

---

## 6. Do's and Don'ts

### Do:
*   **Embrace Whitespace:** Use twice as much margin as you think you need. Luxury is defined by the space you *don't* fill.
*   **Use Asymmetry:** Place a large `display-md` headline on the left, balanced by a small `body-md` block on the far right. 
*   **High Contrast:** Ensure text is either `on_surface` (near black) or `on_primary` (pure white) for maximum executive authority.

### Don't:
*   **No Rounded Corners:** Do not use `border-radius`. Not for buttons, not for cards, not for avatars.
*   **No Generic Grids:** Avoid 3-column "feature grids." Instead, try an overlapping layout where an image in a `surface-container` partially covers a text block.
*   **No Standard Shadows:** Avoid the "fuzzy grey" default shadow. If it doesn't look like light hitting a physical surface, remove it.
*   **No Dividers:** Never use a `<hr>` or a 1px border to separate content. Use a background color change or whitespace.