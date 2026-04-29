#Prompt:

Goal:
Build a cinematic, scroll-driven travel website where 161 image frames act as a video controlled by scroll, with layered UI animations.

🎬 FRAME SYSTEM (CRITICAL)
Frame URL pattern:
https://mnjjesosykmgfmnfbwaz.supabase.co/storage/v1/object/public/beach/ezgif-frame-###.png
Format:
001 → 161 (zero-padded)
Total frames: 161
⚙️ RENDERING ENGINE
Use HTML canvas (NOT img tags)
Draw frames using requestAnimationFrame
Preload:
First 20 frames → priority
Remaining → lazy load in background
🎯 SCROLL → FRAME MAPPING
frameIndex = Math.floor(scrollProgress * 160)
Scroll range:
start: 0
end: 4000px (long scroll for smoothness)
🎬 SCROLL TIMELINE (LOCKED)
🔹 Phase 1 (0%–20%)
Only background animation
Slight scale: 1 → 1.05
No UI
🔹 Phase 2 (20%–30%)

Text (centered):

Mexico

Animation:

opacity: 0 → 1
scale: 0.9 → 1
blur: 10px → 0
🔹 Phase 3 (30%–45%)

Mexico:

moves → top-left
scale: 1 → 0.6

New text appears:
Mexico Island

fade + slide from right
perfectly aligned baseline
🔹 Phase 4 (45%–65%)

Split layout:

LEFT:

Explore (bold, 64–80px)
Our Islands (lighter)

CTA:

“Book Now →”
hover: subtle glow + translateY(-2px)

RIGHT:

Glass card
backdrop-blur: 20px
border-radius: 16px
opacity: 0 → 1
translateY: 50px → 0
🔹 Phase 5 (65%–90%)
Background continues frame animation
Right card:
translateX: 0 → -80px (parallax depth)
Text:
opacity: 1 → 0.85
🔹 Phase 6 (90%–100%)
Final frame locks
Optional:
fade overlay (dark 10–20%)
🎨 DESIGN SYSTEM
Font: Inter (preferred)
Heading weight: 700–800
Letter spacing: -1%
Line height: 0.9–1.1

Colors:

White: #FFFFFF
Accent: #00C2B8 (teal tone)
Glass:
background: rgba(255,255,255,0.1);
backdrop-filter: blur(20px);
⚡ PERFORMANCE RULES (NON-NEGOTIABLE)
Use:
will-change: transform
translate3d() (GPU acceleration)
DO NOT:
use 161 <img> elements
trigger layout reflows on scroll
Add:
mobile fallback → static hero (no frame animation)
🧠 ANIMATION ENGINE

Use:

GSAP ScrollTrigger (recommended)
OR
Framer Motion + scroll hooks
⚠️ HARD CONSTRAINTS
No jitter
No frame skipping
No layout shift
No text flicker
No reflow during scroll
