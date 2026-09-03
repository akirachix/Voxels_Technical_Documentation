# Brand Guideline

> The visual and verbal identity of Mara Guard — built around deep African earth tones, edge-AI precision, and conservation-first messaging. This guide is the single source of truth for designers, engineers, and partners building assets for the project.

---

## 1. Logo Usage

- **Official mark** — Always use the official Mara Guard logo (`images/logo1.png`) with proper clear space and sizing.
- **Don'ts** — Do not distort, recolor, or overlay the logo on busy backgrounds. Avoid low-contrast surfaces.
- **Clear space** — Maintain a margin around the logo equal to at least the height of the "M" glyph in the wordmark.
- **Backgrounds** — The primary lockup reads well on white, deep brown, or the hero gradient.

![Mara Guard primary logo](../images/logo.png)

## 2. Official Colors

The Mara Guard palette is inspired by the Maasai Mara landscape — earth, sunset, and stone. **Use only these five colors** across all surfaces.

**Brand Color Codes (Quick Reference):**

- `#8A5228` — Primary (deep wood brown) · used for primary panels, surfaces, and the main brand color
- `#FFFFFF` — Primary (white) · used for backgrounds and text on dark panels
- `#CD8151` — Accent (bronze) · used for links, badges, highlights, and call-to-action
- `#DDBB8C` — Warm tan · used for soft surfaces, callouts, and body text on dark
- `#000000` — Black · used for borders, footer, code blocks, and high-contrast text

## 3. Typography

- **Headings** — _Poppins Bold_. Used for page titles, section titles, and card headers. Always weight 700+ for hierarchy.
- **Body** — _Poppins Regular_. Paragraphs, captions, and nav items. Line-height ~1.6 for readability on dark panels.
- **Code** — _Fira Mono_. Code blocks, command snippets, and inline `code` tags. Background `#000000`.

## 4. Imagery & Icons

- **Wildlife & field imagery** — Maasai Mara landscapes, lions in their natural habitat, field hardware in deployment.
- **Dashboard screenshots** — Use the official dashboard (`images/dashboard.png`) on the brown palette with Poppins labels.
- **Mobile screenshots** — Use the Flutter app captures (`images/mobile-home.png`, `images/mobile-landing.png`, `images/mobile-signup.png`) in feature showcases.
- **AI & detection imagery** — Bounding-box overlays on real detection frames (`images/test-lion.png`, `images/test1-lion.png`) when illustrating the YOLOv8 model.
- **Hardware imagery** — The solar field node and gateway hardware in real environmental context.
- **Avoid** stock photography unrelated to conservation, lions, or East African ecosystems.

## 5. Voice & Messaging

- **Values** — Conservation, Coexistence, Protection, Innovation. Every message should respect the people, the wildlife, and the land.
- **Tone** — Trustworthy, calm, technical, and inclusive. Speak as an engineering team that takes responsibility for the ecosystem it touches.
- **Tagline** — _"Coexistence. Protection. Innovation."_ — used on splash, app store listings, and the documentation homepage.
- **Mission** — Mitigate human-wildlife conflict in the Maasai Mara by replacing dangerous blindspots with secure, trackable edge-intelligence arrays.

## 6. Example Application

- Android / iOS app and dashboard use deep brown banners, rounded cards, and Poppins throughout.
- All interfaces show the Mara Guard logo on splash and primary navigation.
- Endpoint rows, alert cards, and telemetry tiles all use the bronze accent (`#CD8151`) for emphasis.

<div style="border: 2px solid #CD8151; border-radius: 16px; padding: 24px; background: #FFFFFF; margin: 24px 0; box-shadow: 0 8px 24px rgba(0,0,0,0.15);">
<table style="width:100%; border:none; background:transparent; margin:0; padding:0; border-collapse:separate; border-spacing:12px;">
  <tr>
    <td style="text-align:center; border:none; background:transparent; padding:0;"><img src="../images/home.png" alt="Mara Guard home screen" style="max-width:100%; height:auto; border-radius:12px; border:1px solid #DDBB8C; display:block;"><br><strong style="color:#000000;">Home</strong></td>
    <td style="text-align:center; border:none; background:transparent; padding:0;"><img src="../images/lion.png" alt="Mara Guard lion detection screen" style="max-width:100%; height:auto; border-radius:12px; border:1px solid #DDBB8C; display:block;"><br><strong style="color:#000000;">Lion Detection</strong></td>
    <td style="text-align:center; border:none; background:transparent; padding:0;"><img src="../images/battery1.png" alt="Mara Guard battery monitoring screen" style="max-width:100%; height:auto; border-radius:12px; border:1px solid #DDBB8C; display:block;"><br><strong style="color:#000000;">Battery</strong></td>
    <td style="text-align:center; border:none; background:transparent; padding:0;"><img src="../images/settings.png" alt="Mara Guard settings screen" style="max-width:100%; height:auto; border-radius:12px; border:1px solid #DDBB8C; display:block;"><br><strong style="color:#000000;">Settings</strong></td>
  </tr>
</table>
<p style="text-align:center; color:#000000; margin: 16px 0 0 0; font-size:0.95em;"><em>All four mobile app screens — Home, Lion Detection, Battery, Settings — sharing the same deep brown palette and bronze accent.</em></p>
</div>

_The ranger dashboard applying the brand — deep brown panels, bronze accents, Poppins typography._
