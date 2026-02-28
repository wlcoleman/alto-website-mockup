# Alto Website Redesign — Prismic Implementation Handoff

**Prepared for:** Jonathan Campos / Dev Team
**Date:** February 28, 2026
**Mockup:** https://wlcoleman.github.io/alto-website-mockup/
**Source HTML:** https://github.com/wlcoleman/alto-website-mockup/blob/main/index.html

---

## 1. Design System

### Typography
- **Display / Headlines:** Cormorant Garamond (Google Fonts) — weights 300, 400, 500, 600, 700 + italic 300, 400
- **Body / UI:** DM Sans (Google Fonts) — weights 300, 400, 500, 600, 700

### Color Palette

| Name | Hex | Usage |
|------|-----|-------|
| Black | `#0C0A09` | Primary background |
| Black Warm | `#141110` | Section backgrounds |
| Black Card | `#1A1614` | Card backgrounds |
| White | `#F5F0EB` | Primary text (on dark), card bg (on light) |
| Cream | `#EDE6DD` | Light section backgrounds |
| **Copper** | `#AC826D` | **Primary accent — CTAs, highlights, numbers** |
| Copper Light | `#C49B84` | Hover states |
| Sand | `#BAA590` | Body text (on dark) |
| Sand Light | `#D4C4B0` | Secondary text |
| Sage | `#5B6C5C` | Subtle accent |
| Navy | `#525D73` | Subtle accent |
| Navy Deep | `#1C2130` | Gradient backgrounds |
| Brown | `#6B5C4F` | Body text (on light backgrounds) |
| Gold | `#DABB7C` | Occasional accent |
| Gray Warm | `#8A7E74` | Labels, captions |
| Gray Line | `rgba(186, 165, 144, 0.1)` | Borders, dividers |

### Spacing & Layout
- Max content width: `1200px`
- Section padding: `8rem 3rem` (desktop), `5rem 1.5rem` (tablet/mobile)
- Card padding: `2rem` to `2.5rem`
- Card border-radius: `8px`
- Card border: `1px solid rgba(186, 165, 144, 0.1)`
- Card hover: border shifts to `rgba(172, 130, 109, 0.2)`, subtle translateY(-3px)
- Gradient accent line on card top (on hover): `linear-gradient(90deg, #AC826D, transparent)`

### Effects
- Noise texture overlay (fixed, full-screen, opacity 0.022) — SVG feTurbulence
- Radial gradient glows behind sections (copper or sage, very subtle 0.03–0.08 opacity)
- Scroll-triggered fade-up animations (opacity 0→1, translateY 20px→0, 0.7s ease)
- Glassmorphism nav: `rgba(12, 10, 9, 0.88)` + `backdrop-filter: blur(24px)`

---

## 2. Page Structure — Slice Mapping

Each section below maps to a recommended Prismic Slice type.

---

### SLICE 1: Navigation
**Suggested Slice:** `navigation` (or site-level custom type)

| Element | Content |
|---------|---------|
| Logo | `Alto_Wordmark_Copper_XL.png` (28px height) |
| Links | Ride, Fleet, Infrastructure, Autonomous, Team |
| CTA Button | "Book a Ride" (copper bg, dark text) |

**Behavior:** Fixed top, blurred glass background, collapses to hamburger on mobile.

---

### SLICE 2: Hero
**Suggested Slice:** `hero_banner`

| Field | Type | Content |
|-------|------|---------|
| Eyebrow | Text | "Rideshare. Refined." |
| Headline | Rich Text | The *infrastructure* for electric & autonomous fleets |
| Subheadline | Rich Text | Alto operates the largest vertically integrated electric rideshare fleet in the US, with the depot, charging, and operational infrastructure to power the autonomous transition. |
| Stat 1 | Group (number + label) | 1,000+ / Electric Vehicles |
| Stat 2 | Group | 4,000+ / W-2 Drivers |
| Stat 3 | Group | 200M+ / Miles Driven |
| Stat 4 | Group | 4 / Markets |

**Layout:** Full viewport height. Stats bar at bottom with top border. Dark background with subtle copper radial glow top-right.

---

### SLICE 3: Rider Experience (Consumer Section)
**Suggested Slice:** `rider_experience`
**Background:** Cream (`#EDE6DD`)

| Field | Type | Content |
|-------|------|---------|
| Eyebrow | Text | "The Alto Experience" |
| Headline | Text | Safety. Consistency. Hospitality. |
| Tagline | Text (italic) | Every ride is the same Alto experience. |
| Body | Rich Text | Your first ride and your thousandth should feel the same. Professional W-2 drivers, all-electric Kia EV9s, real-time safety monitoring. That's what we mean by consistency in Dallas and Houston. |

**Promise Cards** (repeatable group — 3 items):

| Icon | Title | Description |
|------|-------|-------------|
| 🛡️ | Safety First | AI-powered real-time video monitoring, background checks, drug testing, and ongoing performance reviews. 33% of our drivers are women, 3× the industry average. |
| ✨ | Consistent Quality | Every vehicle is a Kia EV9. Cleaned and inspected between rides, with curated music, bottled water, and phone chargers as standard. |
| 🤝 | Hospitality-Driven | Our W-2 drivers are trained professionals, not gig workers. Hourly pay, benefits, and career development mean they're here for the long run. |

**Vehicle Showcase** (right column):
- Dark card with "Kia EV9" heading
- Subtitle: "All-Electric · Premium Interior · Zero Emissions"
- Label: "The Alto Fleet Vehicle"
- (Replace with actual EV9 photo when available)

**Market Cards** (repeatable group — 2 items):

| City | Type | Description | Links |
|------|------|-------------|-------|
| Dallas | Alto App | Our hometown. Schedule rides, choose your vehicle, and rate your driver through the Alto app. | Book a Ride, Service Area, Hours |
| Houston | Alto App | Same premium experience. Same all-electric fleet. Powered by local W-2 drivers who know the city. | Book a Ride, Service Area, Hours |

**CTA Row:**
- Primary: "📱 Download the Alto App" (dark button)
- Text links: "View Service Areas →", "Hours of Operation →"

---

### SLICE 4: Uber-Powered Fleet
**Suggested Slice:** `partnership_highlight`
**Background:** `#141110` with subtle diagonal gradient

**Left Column:**

| Field | Content |
|-------|---------|
| Eyebrow | "Rides Powered by Alto" |
| Headline | Scaled on **Uber**, powered by Alto |
| Body | In Los Angeles and Miami, Alto vehicles and W-2 drivers operate on the Uber platform through Uber Black, Uber XL, and UberTeen. Uber is both our distribution partner and a $35M strategic investor. |
| Market Badge 1 | Los Angeles / Via Uber |
| Market Badge 2 | Miami / Via Uber |

**Right Column — Metrics Grid** (2×2):

| Number | Label |
|--------|-------|
| $35M | Uber Investment |
| 2M+ | Uber Rides (Year 1) |
| 250% | YoY Revenue Growth |
| $100M+ | Revenue Run Rate |

**"Uber" badge styling:** White text on `rgba(255,255,255,0.07)` background with subtle border.

---

### SLICE 5: Infrastructure Stats
**Suggested Slice:** `stats_grid`
**Background:** Dark with navy-deep gradient + sage/copper radial glows

| Field | Content |
|-------|---------|
| Eyebrow | "Infrastructure" |
| Headline | Built for scale. Ready for autonomy. |
| Body | Our depot and charging network is the physical layer that autonomous vehicles will need. The best depot locations in each city are limited, and we're already there. |

**Stats Grid** (4×2 = 8 items):

| Number | Label |
|--------|-------|
| 1,000+ | Kia EV9s |
| 7 | Depots Operational |
| ~2 MW | Charging Capacity |
| 4,000+ | W-2 Drivers |
| ~400 | Drivers Hired / Week |
| 4 | Major US Markets |
| 200M+ | Miles Driven |
| 100% | Zero Emission Fleet |

---

### SLICE 6: Operations Pillars
**Suggested Slice:** `feature_grid`

| Field | Content |
|-------|---------|
| Eyebrow | "Operations" |
| Headline | Vertically integrated fleet operations at scale |

**Cards** (3×2 grid, 6 items):

| Icon | Title | Description |
|------|-------|-------------|
| ⚡ | All-Electric Fleet | 1,000+ Kia EV9s across four markets. We completed the transition to an all-electric fleet in Q4 2025. |
| 🏗️ | Depot Infrastructure | 7 depots with charging, maintenance, and fleet staging. The same sites that run our human-driven fleet will run autonomous vehicles. |
| 🤖 | Proprietary Technology | AI-driven fleet optimization: supply positioning, demand forecasting, driver-trip matching, and ML-based scheduling. Unit costs come down quarter over quarter. |
| 🛡️ | Safety & Compliance | AI-powered real-time video monitoring across the fleet. W-2 employed drivers with background checks, drug testing, and continuous performance reviews. |
| 👥 | Driver Excellence | Multi-stage training with a high safety bar. 33% of our drivers are women, compared to 11% industry-wide. Hourly pay, benefits, and real career paths. |
| 📈 | Capital Efficiency | Central overhead under 10% of revenue. Unit costs declining 20%+ year over year. The model works at 1,000 vehicles and scales to 10,000+. |

---

### SLICE 7: AV Vision
**Suggested Slice:** `av_strategy`

| Field | Content |
|-------|---------|
| Eyebrow | "Autonomous Strategy" |
| Headline | The physical & digital *API for autonomy* |
| Body | AV technology will be commoditized. The physical infrastructure will not. Depots, charging, maintenance, fleet management, compliance: every autonomous fleet needs these, and they're hard to replicate. Alto is building the operations layer that any AV company can plug into. |

**Capability Tags** (repeatable text items):
- Depot & staging operations
- DC fast charging networks
- Vehicle maintenance & inspection
- Fleet management software
- Regulatory compliance
- Safety monitoring & remote assistance
- Driver workforce (hybrid model)
- Insurance & risk management

**Timeline Cards** (3 phases):

| Phase | Label | Title | Description |
|-------|-------|-------|-------------|
| 1 | Now | Solving Supply Today | Scaling human-driven electric fleets across four US markets. Proving unit economics and building the depot infrastructure that will serve both models. |
| 2 | 2027 | AV Integration Begins | Dual-use depots serving both human-driven and autonomous vehicles from partners like Lucid/Nuro, Wayve, Tesla, Waymo, or AVRide. Starting with 50 AV vehicles per market. |
| 3 | 2028+ | Fleet Operations Platform | 500+ AV vehicles per market. Multiple AV manufacturers competing for depot access, the same way car manufacturers compete for fleet contracts today. |

**Timeline visual:** Horizontal gradient line (copper → sand → fade) connecting three phase cards. Glowing copper dots at phase markers.

---

### SLICE 8: Leadership
**Suggested Slice:** `team_grid`

| Field | Content |
|-------|---------|
| Eyebrow | "Leadership" |
| Headline | Built by operators |

**Team Members** (5):

| Initials | Name | Title | Bio |
|----------|------|-------|-----|
| WC | Will Coleman | Founder & CEO | Former McKinsey Partner, 11 years in the air and travel practice. Left to build Alto after a decade advising the world's largest transportation companies. |
| DD | Dana Donato | Chief Operating Officer | Leads day-to-day operations across all four markets. Oversees depot operations, fleet management, and driver workforce. |
| PC | Patrice Crisinel | Chief Financial Officer | Manages financial strategy, investor relations, and capital allocation. Board member providing financial governance. |
| JC | Jonathan Campos | Chief Technology Officer | Leads development of Alto's proprietary fleet optimization platform, AI safety monitoring, and technology infrastructure. |
| FM | Fiona Maguire | Chief Experience Officer | Owns rider and driver experience across every touchpoint. Focused on building a brand riders trust and drivers want to work for. |

**Avatar styling:** 56px circle, gradient copper background, initials in Cormorant Garamond.
(Replace with actual headshots when available.)

---

### SLICE 9: Dual CTA
**Suggested Slice:** `dual_cta`

**Left Card** (cream background):

| Field | Content |
|-------|---------|
| Title | Ride with Alto |
| Body | Safe, all-electric rides in Dallas and Houston. Download the app and see for yourself. |
| CTA | "📱 Download the App" (dark button) |
| Links | Service Areas →, Hours → |

**Right Card** (dark with copper border):

| Field | Content |
|-------|---------|
| Title | Partner with *Alto* |
| Body | We're building the infrastructure layer for the autonomous transition. If you're an investor, AV company, or fleet operator, let's talk. |
| CTA Primary | "Investor Inquiries" → mailto:invest@ridealto.com |
| CTA Secondary | "Join Our Team" (outline button) |

---

### SLICE 10: Footer
**Suggested Slice:** `footer` (or site-level custom type)

**4-column layout:**

| Column 1 (Brand) | Column 2 (Company) | Column 3 (Riders) | Column 4 (Partners) |
|-------------------|--------------------|--------------------|---------------------|
| Logo + tagline | About | Book a Ride | Investor Inquiries |
| "The infrastructure for electric and autonomous mobility. Operating in Dallas, Houston, Los Angeles, and Miami." | Leadership | Service Areas | AV Partnerships |
| | Careers | Hours of Operation | Drive for Alto |
| | Press | Safety | Fleet Operations |

**Footer bottom:** © 2026 Alto. All rights reserved. | Privacy · Terms · Contact

---

## 3. Assets

All assets are in the GitHub repo under `/assets/`:
- `Alto_Wordmark_Copper_XL.png` — Copper wordmark (nav, footer)
- `Alto_Wordmark_White.png` — White wordmark
- `Alto_Logo_White.png` — Logo mark only (white)
- `Alto_Logo_Copper.png` — Logo mark only (copper)
- `Alto_Logo_Black.png` — Logo mark only (black)
- `Alto_Lockup_White.png` — Full lockup with tagline
- `Alto_Brand_Book_2025.pdf` — Full brand guidelines

**Needed from the team:**
- High-res Kia EV9 photo (black vehicle, studio or lifestyle shot)
- Executive headshots (replace avatar initials)
- Any additional lifestyle/fleet photography

---

## 4. Responsive Breakpoints

| Breakpoint | Key Changes |
|------------|-------------|
| > 1024px | Full desktop layout |
| 900–1024px | 2-col grids → 2-col, team → 1-col |
| 600–900px | Single column throughout, nav collapses, reduce padding |
| < 600px | Stack everything, smaller stat numbers, vertical CTA buttons |

---

## 5. Interactive Behaviors

- **Scroll animations:** Elements fade up (20px) on intersection (threshold 0.12). Staggered 80ms between siblings.
- **Card hovers:** translateY(-3px), border color shifts to copper, subtle shadow
- **Nav CTA hover:** background lightens, translateY(-1px)
- **Link arrows:** gap increases on hover (0.4rem → 0.6rem)
- **No JavaScript dependencies** — uses IntersectionObserver for animations

---

## 6. Notes for Prismic Implementation

1. **Slice Zone approach:** Each section above maps to one Slice. The homepage would be a "Page" custom type with a Slice Zone containing all 8 content slices in order.

2. **Repeatable groups:** Promise cards, market cards, stats, team members, timeline phases, and capability tags should all be repeatable groups within their respective slices so content editors can add/remove items.

3. **Rich Text fields:** Headlines that contain italic styling (like "*infrastructure*" and "*API for autonomy*") need Rich Text fields, not plain Key Text.

4. **The CSS is self-contained:** The full stylesheet is in the HTML `<style>` block. It can be extracted directly into your component styles or a global CSS file.

5. **Fonts:** Add Cormorant Garamond and DM Sans from Google Fonts to your Prismic/Next.js setup.

6. **Image optimization:** The noise texture is an inline SVG data URL. Keep it as-is for performance.
