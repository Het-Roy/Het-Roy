<div align="center">

<div class="min-h-screen bg-[#0a0a0a] text-white overflow-x-hidden" id="portfolio-root">

<!-- ============================================================ -->
<!--  INJECT CDNs                                                  -->
<!-- ============================================================ -->
<script src="https://cdn.tailwindcss.com"></script>
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/css/all.min.css"/>
<link rel="preconnect" href="https://fonts.googleapis.com"/>
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin/>
<link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@400;700;900&family=Rajdhani:wght@300;400;600;700&family=JetBrains+Mono:wght@300;400;700&display=swap" rel="stylesheet"/>

<style>
/* ═══════════════════════════════════════════════
   ROOT & RESET
═══════════════════════════════════════════════ */
*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

:root {
  --cyan:    #00f5ff;
  --purple:  #a855f7;
  --green:   #39ff14;
  --pink:    #ff006e;
  --bg:      #0a0a0a;
  --bg2:     #0d0d1a;
  --glass:   rgba(255,255,255,0.04);
  --glass-b: rgba(0,245,255,0.07);
}

html { scroll-behavior: smooth; }

body {
  background: var(--bg);
  color: #fff;
  font-family: 'Rajdhani', system-ui, sans-serif;
  cursor: none !important;
  overflow-x: hidden;
}

/* ═══════════════════════════════════════════════
   CUSTOM NEON CURSOR
═══════════════════════════════════════════════ */
#cursor-dot {
  position: fixed; top: 0; left: 0; width: 8px; height: 8px;
  background: var(--cyan); border-radius: 50%;
  pointer-events: none; z-index: 99999;
  transform: translate(-50%,-50%);
  box-shadow: 0 0 10px var(--cyan), 0 0 30px var(--cyan);
  transition: transform .1s ease;
}
#cursor-ring {
  position: fixed; top: 0; left: 0; width: 36px; height: 36px;
  border: 1.5px solid rgba(0,245,255,0.6); border-radius: 50%;
  pointer-events: none; z-index: 99998;
  transform: translate(-50%,-50%);
  transition: left .12s ease, top .12s ease, transform .2s ease, border-color .2s;
}
.cursor-trail {
  position: fixed; border-radius: 50%;
  pointer-events: none; z-index: 99997;
  transform: translate(-50%,-50%);
  animation: trail-fade .6s ease forwards;
}
@keyframes trail-fade {
  from { opacity: .6; transform: translate(-50%,-50%) scale(1); }
  to   { opacity: 0; transform: translate(-50%,-50%) scale(.2); }
}

/* ═══════════════════════════════════════════════
   HERO SECTION
═══════════════════════════════════════════════ */
#hero {
  position: relative; min-height: 100vh;
  display: flex; flex-direction: column;
  align-items: center; justify-content: center;
  overflow: hidden;
  padding: 4rem 1rem 2rem;
}

/* Scanline overlay */
#hero::before {
  content: '';
  position: absolute; inset: 0;
  background: repeating-linear-gradient(
    0deg,
    transparent,
    transparent 2px,
    rgba(0,245,255,0.013) 2px,
    rgba(0,245,255,0.013) 4px
  );
  pointer-events: none; z-index: 1;
  animation: scanlines 8s linear infinite;
}
@keyframes scanlines { from { background-position: 0 0; } to { background-position: 0 100px; } }

/* Particle canvas */
#particle-canvas {
  position: absolute; inset: 0; z-index: 0;
}

.hero-content { position: relative; z-index: 2; text-align: center; }

.hero-name {
  font-family: 'Orbitron', monospace;
  font-size: clamp(2.8rem, 9vw, 7rem);
  font-weight: 900;
  line-height: 1;
  background: linear-gradient(135deg, var(--cyan) 0%, var(--purple) 50%, var(--pink) 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  filter: drop-shadow(0 0 40px rgba(0,245,255,0.5));
  animation: name-pulse 3s ease-in-out infinite;
  letter-spacing: 0.06em;
}
@keyframes name-pulse {
  0%,100% { filter: drop-shadow(0 0 30px rgba(0,245,255,0.5)) drop-shadow(0 0 80px rgba(168,85,247,0.3)); }
  50%      { filter: drop-shadow(0 0 60px rgba(0,245,255,0.9)) drop-shadow(0 0 120px rgba(168,85,247,0.6)); }
}

.hero-sub {
  font-family: 'Rajdhani', sans-serif;
  font-size: clamp(1rem, 2.5vw, 1.4rem);
  color: rgba(255,255,255,0.5);
  letter-spacing: 0.3em;
  text-transform: uppercase;
  margin: .6rem 0 1.4rem;
}

/* Typing effect */
#typewriter-container {
  display: inline-flex; align-items: center; gap: 4px;
  font-family: 'JetBrains Mono', monospace;
  font-size: clamp(1rem, 2.8vw, 1.6rem);
  color: var(--cyan);
  text-shadow: 0 0 20px var(--cyan);
  min-height: 2.2rem;
}
#typed-text { color: var(--cyan); }
#cursor-blink {
  display: inline-block; width: 2px; height: 1.2em;
  background: var(--cyan);
  box-shadow: 0 0 8px var(--cyan);
  animation: blink .75s step-end infinite;
  margin-left: 2px;
}
@keyframes blink { 0%,100% { opacity: 1; } 50% { opacity: 0; } }

/* ═══════════════════════════════════════════════
   SECTION STYLES SHARED
═══════════════════════════════════════════════ */
.section-wrap {
  max-width: 1200px; margin: 0 auto;
  padding: 5rem 1.5rem;
}
.section-title {
  font-family: 'Orbitron', monospace;
  font-size: clamp(1.6rem, 4vw, 3rem);
  font-weight: 900;
  text-align: center;
  margin-bottom: 3.5rem;
  position: relative;
}
.section-title span {
  background: linear-gradient(90deg, var(--cyan), var(--purple));
  -webkit-background-clip: text; -webkit-text-fill-color: transparent; background-clip: text;
}
.section-title::after {
  content: '';
  display: block; margin: .7rem auto 0;
  width: 80px; height: 3px;
  background: linear-gradient(90deg, var(--cyan), var(--purple));
  border-radius: 2px;
  box-shadow: 0 0 12px var(--cyan);
}

/* Glass card base */
.glass-card {
  background: var(--glass);
  border: 1px solid rgba(0,245,255,0.12);
  border-radius: 16px;
  backdrop-filter: blur(14px);
  -webkit-backdrop-filter: blur(14px);
  transition: border-color .3s, box-shadow .3s;
}
.glass-card:hover {
  border-color: rgba(0,245,255,0.45);
  box-shadow: 0 0 30px rgba(0,245,255,0.15), 0 0 60px rgba(168,85,247,0.1), inset 0 0 30px rgba(0,245,255,0.03);
}

/* ═══════════════════════════════════════════════
   SECTION 1 — SOCIALS
═══════════════════════════════════════════════ */
#socials {
  background: linear-gradient(180deg, transparent 0%, rgba(0,245,255,0.03) 50%, transparent 100%);
  padding: 2rem 0 3rem;
}
.socials-grid {
  display: flex; flex-wrap: wrap;
  justify-content: center; gap: 1.4rem;
  padding: 0 1.5rem;
}
.social-card {
  width: 160px;
  padding: 1.8rem 1rem;
  border-radius: 20px;
  display: flex; flex-direction: column;
  align-items: center; gap: .8rem;
  cursor: none;
  position: relative; overflow: hidden;
  transform-style: preserve-3d;
  transition: box-shadow .3s;
  will-change: transform;
}
.social-card .s-icon {
  font-size: 2.2rem;
  transition: transform .4s cubic-bezier(.34,1.56,.64,1), color .3s;
}
.social-card .s-label {
  font-family: 'Rajdhani', sans-serif;
  font-size: .95rem; font-weight: 600;
  letter-spacing: .1em; text-transform: uppercase;
  color: rgba(255,255,255,0.7);
  transition: color .3s;
}
/* Ripple */
.ripple-el {
  position: absolute; border-radius: 50%;
  transform: scale(0); animation: ripple-anim .6s linear;
  background: rgba(0,245,255,0.25); pointer-events: none;
}
@keyframes ripple-anim { to { transform: scale(4); opacity: 0; } }

/* LinkedIn */
.sc-li { border-color: rgba(0,119,181,0.3); }
.sc-li .s-icon { color: #0077b5; text-shadow: 0 0 20px #0077b5; }
.sc-li:hover { box-shadow: 0 0 30px rgba(0,119,181,0.4), 0 20px 40px rgba(0,0,0,0.5); border-color: #0077b5; }

/* YouTube */
.sc-yt { border-color: rgba(255,0,0,0.3); }
.sc-yt .s-icon { color: #ff0000; text-shadow: 0 0 20px #ff0000; }
.sc-yt:hover { box-shadow: 0 0 30px rgba(255,0,0,0.4), 0 20px 40px rgba(0,0,0,0.5); border-color: #ff0000; }

/* Twitter/X */
.sc-tw { border-color: rgba(255,255,255,0.15); }
.sc-tw .s-icon { color: #e7e9ea; text-shadow: 0 0 20px rgba(255,255,255,0.5); }
.sc-tw:hover { box-shadow: 0 0 30px rgba(255,255,255,0.2), 0 20px 40px rgba(0,0,0,0.5); border-color: rgba(255,255,255,0.5); }

/* GitHub */
.sc-gh { border-color: rgba(240,246,252,0.15); }
.sc-gh .s-icon { color: #f0f6fc; text-shadow: 0 0 20px rgba(240,246,252,0.4); }
.sc-gh:hover { box-shadow: 0 0 30px rgba(240,246,252,0.2), 0 20px 40px rgba(0,0,0,0.5); border-color: rgba(240,246,252,0.5); }

/* Discord */
.sc-dc { border-color: rgba(88,101,242,0.3); }
.sc-dc .s-icon { color: #5865f2; text-shadow: 0 0 20px #5865f2; }
.sc-dc:hover { box-shadow: 0 0 30px rgba(88,101,242,0.4), 0 20px 40px rgba(0,0,0,0.5); border-color: #5865f2; }

/* ═══════════════════════════════════════════════
   SECTION 2 — CAREER STORY
═══════════════════════════════════════════════ */
#career {
  background: linear-gradient(135deg, rgba(168,85,247,0.04) 0%, transparent 50%, rgba(0,245,255,0.04) 100%);
}
.career-story {
  position: relative;
  padding: 2.5rem 2.5rem 2.5rem 3.5rem;
  border-radius: 20px;
  line-height: 1.85;
  font-size: clamp(.95rem,1.8vw,1.1rem);
  color: rgba(255,255,255,0.82);
  overflow: hidden;
}
/* Animated left border */
.career-story::before {
  content: '';
  position: absolute; left: 0; top: 0;
  width: 3px; height: 0; border-radius: 3px;
  background: linear-gradient(180deg, var(--cyan), var(--purple), var(--pink));
  box-shadow: 0 0 12px var(--cyan);
  transition: height 1.4s cubic-bezier(.16,1,.3,1);
}
.career-story.line-drawn::before { height: 100%; }

.career-story p { margin-bottom: 1.2rem; opacity: 0; transform: translateY(18px); transition: opacity .6s ease, transform .6s ease; }
.career-story p.revealed { opacity: 1; transform: translateY(0); }

.career-highlight {
  color: var(--cyan); font-weight: 700;
  text-shadow: 0 0 12px rgba(0,245,255,0.4);
}
.career-stat {
  display: inline-block;
  background: linear-gradient(135deg, rgba(0,245,255,0.12), rgba(168,85,247,0.12));
  border: 1px solid rgba(0,245,255,0.25);
  border-radius: 8px; padding: .15rem .6rem;
  color: var(--green); font-family: 'JetBrains Mono', monospace;
  font-size: .85em; font-weight: 700;
  text-shadow: 0 0 10px var(--green);
  margin: 0 2px;
}

/* ═══════════════════════════════════════════════
   SECTION 3 — SKILLS
═══════════════════════════════════════════════ */
#skills {
  background: var(--bg2);
}
.skills-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(150px, 1fr));
  gap: 1.4rem;
}
.skill-card {
  padding: 1.6rem 1rem 1.4rem;
  border-radius: 18px;
  display: flex; flex-direction: column;
  align-items: center; gap: .7rem;
  cursor: none; position: relative; overflow: hidden;
  transform-style: preserve-3d;
  transition: box-shadow .3s;
  will-change: transform;
}
.skill-card::before {
  content: '';
  position: absolute; inset: 0; border-radius: 18px;
  background: linear-gradient(135deg, rgba(0,245,255,0.06), rgba(168,85,247,0.06));
  opacity: 0; transition: opacity .3s;
}
.skill-card:hover::before { opacity: 1; }

/* SVG Progress Ring */
.ring-wrap { position: relative; width: 70px; height: 70px; }
.ring-svg { width: 70px; height: 70px; transform: rotate(-90deg); }
.ring-bg { fill: none; stroke: rgba(255,255,255,0.06); stroke-width: 4; }
.ring-fill { fill: none; stroke-width: 4; stroke-linecap: round; transition: stroke-dashoffset 1.5s cubic-bezier(.16,1,.3,1); }
.ring-icon {
  position: absolute; top: 50%; left: 50%;
  transform: translate(-50%,-50%);
  font-size: 1.5rem;
  transition: transform .4s cubic-bezier(.34,1.56,.64,1);
}
.skill-card:hover .ring-icon { transform: translate(-50%,-50%) rotate(360deg) scale(1.2); }

.skill-name {
  font-family: 'JetBrains Mono', monospace;
  font-size: .78rem; font-weight: 700;
  text-transform: uppercase; letter-spacing: .08em;
  color: rgba(255,255,255,0.85);
}
.skill-pct {
  font-family: 'Orbitron', monospace;
  font-size: .72rem; font-weight: 700;
  color: var(--cyan); text-shadow: 0 0 8px var(--cyan);
}

/* ═══════════════════════════════════════════════
   SECTION 4 — CONTRIBUTION HEATMAP
═══════════════════════════════════════════════ */
#contrib {
  background: linear-gradient(135deg, rgba(0,245,255,0.03) 0%, transparent 40%, rgba(168,85,247,0.04) 100%);
}
.contrib-stats {
  display: flex; flex-wrap: wrap; justify-content: center; gap: 1.5rem;
  margin-bottom: 2.5rem;
}
.c-stat {
  padding: 1rem 2rem; border-radius: 14px;
  text-align: center; min-width: 170px;
}
.c-stat-num {
  font-family: 'Orbitron', monospace;
  font-size: 2rem; font-weight: 900;
  color: var(--cyan); text-shadow: 0 0 20px var(--cyan);
}
.c-stat-label {
  font-family: 'Rajdhani', sans-serif;
  font-size: .85rem; letter-spacing: .15em;
  text-transform: uppercase; color: rgba(255,255,255,0.5);
  margin-top: .25rem;
}

/* Heatmap */
.heatmap-container {
  overflow-x: auto; padding: 1.5rem;
  border-radius: 16px; position: relative;
  cursor: none;
}
.heatmap-months {
  display: flex; margin-left: 28px; margin-bottom: 5px;
  gap: 0;
}
.heatmap-month-label {
  font-family: 'JetBrains Mono', monospace;
  font-size: .65rem; color: rgba(255,255,255,0.35);
  min-width: 0; flex: 1;
}
.heatmap-body { display: flex; gap: 4px; align-items: flex-start; }
.heatmap-days {
  display: flex; flex-direction: column; gap: 4px;
  margin-right: 4px; padding-top: 2px;
}
.heatmap-day-label {
  font-family: 'JetBrains Mono', monospace;
  font-size: .6rem; color: rgba(255,255,255,0.3);
  height: 11px; line-height: 11px;
}
.heatmap-grid {
  display: flex; gap: 4px;
}
.heatmap-col { display: flex; flex-direction: column; gap: 4px; }
.heatmap-cell {
  width: 11px; height: 11px; border-radius: 2px;
  transition: transform .15s cubic-bezier(.34,1.56,.64,1), box-shadow .15s;
  cursor: none; position: relative;
}
.heatmap-cell:hover {
  transform: scale(2.2);
  z-index: 10;
}

/* Intensity levels */
.hm-0 { background: rgba(255,255,255,0.05); }
.hm-1 { background: #0e4429; box-shadow: 0 0 4px rgba(0,245,255,0.1); }
.hm-2 { background: #006d32; box-shadow: 0 0 6px rgba(0,245,255,0.2); }
.hm-3 { background: #26a641; box-shadow: 0 0 8px rgba(0,245,255,0.3); }
.hm-4 { background: #39d353; box-shadow: 0 0 14px rgba(57,211,83,0.6), 0 0 30px rgba(0,245,255,0.2); }
/* Extra neon intense */
.hm-5 { background: var(--cyan); box-shadow: 0 0 18px var(--cyan), 0 0 40px rgba(168,85,247,0.4); }

/* Tooltip */
.hm-tooltip {
  position: fixed; pointer-events: none; z-index: 9999;
  background: rgba(10,10,20,0.92);
  border: 1px solid rgba(0,245,255,0.4);
  border-radius: 8px; padding: .5rem .85rem;
  font-family: 'JetBrains Mono', monospace;
  font-size: .7rem; color: #fff;
  box-shadow: 0 0 20px rgba(0,245,255,0.2);
  backdrop-filter: blur(8px);
  white-space: nowrap;
  opacity: 0; transform: translateY(6px);
  transition: opacity .15s, transform .15s;
}
.hm-tooltip.visible { opacity: 1; transform: translateY(0); }

/* Scroll-reveal base */
.reveal-el { opacity: 0; transform: translateY(30px); transition: opacity .7s ease, transform .7s ease; }
.reveal-el.revealed { opacity: 1; transform: translateY(0); }

/* Fire pulse */
@keyframes fire-pulse {
  0%,100% { text-shadow: 0 0 8px #ff6600, 0 0 20px #ff3300; transform: scale(1); }
  50%      { text-shadow: 0 0 20px #ff6600, 0 0 50px #ff9900; transform: scale(1.15); }
}
.fire-emoji { display: inline-block; animation: fire-pulse 1.2s ease-in-out infinite; }

/* Divider line */
.neon-divider {
  width: 100%; height: 1px;
  background: linear-gradient(90deg, transparent, var(--cyan), var(--purple), transparent);
  box-shadow: 0 0 10px rgba(0,245,255,0.3);
  margin: 0 auto;
}

/* Glow trail on heatmap */
.glow-trail {
  position: absolute; pointer-events: none; border-radius: 50%;
  background: radial-gradient(circle, rgba(0,245,255,0.15) 0%, transparent 70%);
  width: 120px; height: 120px;
  transform: translate(-50%,-50%);
  transition: left .08s ease, top .08s ease;
  z-index: 0;
}

/* Month labels helper */
.month-row { display: grid; grid-template-columns: repeat(12, 1fr); }

@media (max-width: 640px) {
  .heatmap-cell { width: 9px; height: 9px; }
  .skills-grid { grid-template-columns: repeat(auto-fill, minmax(130px,1fr)); }
  .social-card { width: 130px; }
  .career-story { padding: 1.5rem 1.2rem 1.5rem 2rem; }
}
</style>

<!-- ═══════════════════════════════════════════════════════════
     CURSOR ELEMENTS
═══════════════════════════════════════════════════════════════ -->
<div id="cursor-dot"></div>
<div id="cursor-ring"></div>
<div class="hm-tooltip" id="hm-tooltip"></div>

<!-- ═══════════════════════════════════════════════════════════
     SECTION 1 — HERO
═══════════════════════════════════════════════════════════════ -->
<section id="hero">
  <canvas id="particle-canvas"></canvas>

  <div class="hero-content">
    <div class="hero-sub">⚡ Full Stack Developer & Open Source Architect ⚡</div>
    <h1 class="hero-name">YOUR NAME</h1>
    <div style="margin: 1.2rem 0 2rem;">
      <div id="typewriter-container">
        <span id="typed-text"></span><span id="cursor-blink"></span>
      </div>
    </div>

    <!-- scroll cue -->
    <div style="margin-top:2rem; animation: bounce 2s ease infinite;">
      <i class="fa-solid fa-angles-down" style="color: var(--cyan); font-size: 1.4rem; opacity:.6; text-shadow: 0 0 12px var(--cyan);"></i>
    </div>
  </div>
</section>

<!-- ═══════════════════════════════════════════════════════════
     SOCIALS
═══════════════════════════════════════════════════════════════ -->
<div class="neon-divider"></div>
<section id="socials">
  <div class="section-wrap" style="padding-top:3rem; padding-bottom:3rem;">
    <h2 class="section-title"><span>Connect With Me</span></h2>
    <div class="socials-grid">

      <a href="https://linkedin.com/in/YOUR_USERNAME" class="glass-card social-card sc-li" target="_blank" rel="noopener">
        <i class="fa-brands fa-linkedin s-icon"></i>
        <span class="s-label">LinkedIn</span>
      </a>

      <a href="https://github.com/YOUR_USERNAME" class="glass-card social-card sc-gh" target="_blank" rel="noopener">
        <i class="fa-brands fa-github s-icon"></i>
        <span class="s-label">GitHub</span>
      </a>

      <a href="https://youtube.com/@YOUR_CHANNEL" class="glass-card social-card sc-yt" target="_blank" rel="noopener">
        <i class="fa-brands fa-youtube s-icon"></i>
        <span class="s-label">YouTube</span>
      </a>

      <a href="https://twitter.com/YOUR_HANDLE" class="glass-card social-card sc-tw" target="_blank" rel="noopener">
        <i class="fa-brands fa-x-twitter s-icon"></i>
        <span class="s-label">Twitter / X</span>
      </a>

      <a href="https://discord.gg/YOUR_SERVER" class="glass-card social-card sc-dc" target="_blank" rel="noopener">
        <i class="fa-brands fa-discord s-icon"></i>
        <span class="s-label">Discord</span>
      </a>

    </div>
  </div>
</section>

<!-- ═══════════════════════════════════════════════════════════
     SECTION 2 — CAREER STORY
═══════════════════════════════════════════════════════════════ -->
<div class="neon-divider"></div>
<section id="career">
  <div class="section-wrap">
    <h2 class="section-title reveal-el"><span>My Journey</span></h2>

    <div class="glass-card career-story reveal-el" id="career-story">
      <p>
        I didn't start with a roadmap — I started with <span class="career-highlight">curiosity and a compiler</span>.
        At 16, I wrote my first C program that sorted a list of numbers and felt the kind of rush most people reserve for skydiving.
        That single moment rewired my brain. I knew: this was the language I'd use to speak to machines.
      </p>
      <p>
        Fast-forward through <span class="career-stat">3+ years</span> of obsessive engineering — I evolved from writing raw
        <span class="career-highlight">C & C++ systems</span> to architecting production-grade full-stack platforms used by thousands.
        I navigated the entire MERN constellation — <span class="career-highlight">MongoDB, Express, React, Node.js</span> —
        not just as a user, but as someone who bends them to do things the docs don't mention.
      </p>
      <p>
        I've shipped <span class="career-stat">15+ projects</span> from concept to deployment, slashed API latency by
        <span class="career-stat">68%</span> through surgical Node.js optimisation, and built React component libraries
        used across <span class="career-stat">5 teams</span>. My MongoDB schemas have survived schema migrations that
        would have broken lesser architectures. My Express APIs handle <span class="career-stat">50k+ req/day</span> without a heartbeat missed.
      </p>
      <p>
        Beyond code, I believe in <span class="career-highlight">open-source as infrastructure for humanity</span>.
        I contribute to repositories that make the web safer, faster, and more accessible. I write technical content that has reached
        <span class="career-stat">100k+ developers</span> across platforms — because the best code is code that teaches.
      </p>
      <p>
        Right now, I'm pushing boundaries at the intersection of <span class="career-highlight">AI-augmented development & distributed systems</span>.
        Building things that don't exist yet. Solving problems that haven't been named yet.
        The terminal is always open. The compiler never sleeps. <span class="career-highlight">Neither do I.</span>
      </p>
    </div>
  </div>
</section>

<!-- ═══════════════════════════════════════════════════════════
     SECTION 3 — SKILLS
═══════════════════════════════════════════════════════════════ -->
<div class="neon-divider"></div>
<section id="skills">
  <div class="section-wrap">
    <h2 class="section-title reveal-el"><span>Weapons of Mass Development</span></h2>

    <div class="skills-grid" id="skills-grid">
      <!-- JS fills these dynamically -->
    </div>
  </div>
</section>

<!-- ═══════════════════════════════════════════════════════════
     SECTION 4 — CONTRIBUTION HEATMAP
═══════════════════════════════════════════════════════════════ -->
<div class="neon-divider"></div>
<section id="contrib">
  <div class="section-wrap">
    <h2 class="section-title reveal-el"><span>My Digital Footprint</span></h2>

    <!-- Stats Row -->
    <div class="contrib-stats reveal-el">
      <div class="glass-card c-stat">
        <div class="c-stat-num" id="total-contrib">0</div>
        <div class="c-stat-label">Total Contributions</div>
      </div>
      <div class="glass-card c-stat">
        <div class="c-stat-num"><span id="streak-count">0</span> <span class="fire-emoji">🔥</span></div>
        <div class="c-stat-label">Day Current Streak</div>
      </div>
      <div class="glass-card c-stat">
        <div class="c-stat-num" id="repos-count">0</div>
        <div class="c-stat-label">Public Repositories</div>
      </div>
    </div>

    <!-- Heatmap -->
    <div class="glass-card heatmap-container reveal-el" id="heatmap-wrap">
      <div class="glow-trail" id="glow-trail"></div>
      <div id="heatmap-root"></div>
    </div>

    <!-- Legend -->
    <div style="display:flex; align-items:center; justify-content:flex-end; gap:.5rem; margin-top:.75rem; padding-right:.5rem;">
      <span style="font-family:'JetBrains Mono',monospace; font-size:.65rem; color:rgba(255,255,255,0.35);">Less</span>
      <div style="width:11px;height:11px;border-radius:2px;" class="hm-0"></div>
      <div style="width:11px;height:11px;border-radius:2px;" class="hm-1"></div>
      <div style="width:11px;height:11px;border-radius:2px;" class="hm-2"></div>
      <div style="width:11px;height:11px;border-radius:2px;" class="hm-3"></div>
      <div style="width:11px;height:11px;border-radius:2px;" class="hm-4"></div>
      <div style="width:11px;height:11px;border-radius:2px;" class="hm-5"></div>
      <span style="font-family:'JetBrains Mono',monospace; font-size:.65rem; color:rgba(255,255,255,0.35);">More</span>
    </div>

  </div>
</section>

</div><!-- /#portfolio-root -->

<!-- ═══════════════════════════════════════════════════════════
     ALL JAVASCRIPT
═══════════════════════════════════════════════════════════════ -->
<script>
(function() {
'use strict';

/* ────────────────────────────────────────────
   CURSOR
──────────────────────────────────────────── */
const dot   = document.getElementById('cursor-dot');
const ring  = document.getElementById('cursor-ring');
let mx = 0, my = 0, rx = 0, ry = 0;

document.addEventListener('mousemove', e => {
  mx = e.clientX; my = e.clientY;
  dot.style.left  = mx + 'px';
  dot.style.top   = my + 'px';

  // trail
  const t = document.createElement('div');
  t.className = 'cursor-trail';
  const sz = 4 + Math.random() * 6;
  t.style.cssText = `width:${sz}px;height:${sz}px;left:${mx}px;top:${my}px;
    background:rgba(0,245,255,${0.2 + Math.random()*.3});`;
  document.body.appendChild(t);
  setTimeout(() => t.remove(), 600);
});

(function animRing() {
  rx += (mx - rx) * .12;
  ry += (my - ry) * .12;
  ring.style.left = rx + 'px';
  ring.style.top  = ry + 'px';
  requestAnimationFrame(animRing);
})();

/* ────────────────────────────────────────────
   PARTICLE CANVAS (HERO BACKGROUND)
──────────────────────────────────────────── */
const canvas = document.getElementById('particle-canvas');
const ctx    = canvas.getContext('2d');
let W, H, particles = [];

function resizeCanvas() {
  const hero = document.getElementById('hero');
  W = canvas.width  = hero.offsetWidth;
  H = canvas.height = hero.offsetHeight;
}
resizeCanvas();
window.addEventListener('resize', resizeCanvas);

function Particle() {
  this.x = Math.random() * W;
  this.y = Math.random() * H;
  this.vx = (Math.random() - .5) * .4;
  this.vy = (Math.random() - .5) * .4;
  this.r  = Math.random() * 1.5 + .3;
  this.alpha = Math.random() * .5 + .1;
  this.color = Math.random() > .5 ? '0,245,255' : '168,85,247';
}
for (let i = 0; i < 90; i++) particles.push(new Particle());

function drawParticles() {
  ctx.clearRect(0, 0, W, H);
  particles.forEach(p => {
    p.x += p.vx; p.y += p.vy;
    if (p.x < 0) p.x = W; if (p.x > W) p.x = 0;
    if (p.y < 0) p.y = H; if (p.y > H) p.y = 0;

    ctx.beginPath();
    ctx.arc(p.x, p.y, p.r, 0, Math.PI * 2);
    ctx.fillStyle = `rgba(${p.color},${p.alpha})`;
    ctx.fill();
  });
  // connect nearby particles
  for (let i = 0; i < particles.length; i++) {
    for (let j = i + 1; j < particles.length; j++) {
      const dx = particles[i].x - particles[j].x;
      const dy = particles[i].y - particles[j].y;
      const dist = Math.sqrt(dx*dx + dy*dy);
      if (dist < 100) {
        ctx.beginPath();
        ctx.moveTo(particles[i].x, particles[i].y);
        ctx.lineTo(particles[j].x, particles[j].y);
        ctx.strokeStyle = `rgba(0,245,255,${(1 - dist/100) * .08})`;
        ctx.lineWidth = .5;
        ctx.stroke();
      }
    }
  }
  requestAnimationFrame(drawParticles);
}
drawParticles();

/* ────────────────────────────────────────────
   TYPING EFFECT
──────────────────────────────────────────── */
const phrases = [
  'Building the future, one commit at a time.',
  'MERN Stack Architect & Systems Engineer.',
  'Open Source Believer. Performance Obsessed.',
  'Turning caffeine into production-grade code.',
  'Full Stack Developer. Problem Destroyer.',
];
let pIdx = 0, cIdx = 0, deleting = false;
const typedEl = document.getElementById('typed-text');

function type() {
  const phrase = phrases[pIdx];
  if (!deleting) {
    typedEl.textContent = phrase.slice(0, ++cIdx);
    if (cIdx === phrase.length) { deleting = true; setTimeout(type, 1800); return; }
    setTimeout(type, 55 + Math.random() * 30);
  } else {
    typedEl.textContent = phrase.slice(0, --cIdx);
    if (cIdx === 0) { deleting = false; pIdx = (pIdx + 1) % phrases.length; setTimeout(type, 300); return; }
    setTimeout(type, 28);
  }
}
type();

/* ────────────────────────────────────────────
   3D TILT — SOCIAL & SKILL CARDS
──────────────────────────────────────────── */
function addTilt(el, strength = 15) {
  el.addEventListener('mousemove', e => {
    const r  = el.getBoundingClientRect();
    const x  = e.clientX - r.left - r.width  / 2;
    const y  = e.clientY - r.top  - r.height / 2;
    const rx = -(y / (r.height / 2)) * strength;
    const ry =  (x / (r.width  / 2)) * strength;
    el.style.transform = `perspective(600px) rotateX(${rx}deg) rotateY(${ry}deg) scale(1.06)`;
  });
  el.addEventListener('mouseleave', () => {
    el.style.transform = 'perspective(600px) rotateX(0) rotateY(0) scale(1)';
  });
}

function addRipple(el) {
  el.addEventListener('click', e => {
    const r  = el.getBoundingClientRect();
    const rp = document.createElement('span');
    rp.className = 'ripple-el';
    const sz = Math.max(r.width, r.height);
    rp.style.cssText = `width:${sz}px;height:${sz}px;left:${e.clientX - r.left - sz/2}px;top:${e.clientY - r.top - sz/2}px;`;
    el.appendChild(rp);
    setTimeout(() => rp.remove(), 700);
  });
}

document.querySelectorAll('.social-card').forEach(c => { addTilt(c, 18); addRipple(c); });

/* ────────────────────────────────────────────
   SKILLS DATA + RENDER
──────────────────────────────────────────── */
const SKILLS = [
  { name: 'React',       pct: 92, icon: '<i class="fa-brands fa-react" style="color:#61dafb"></i>',       stroke: '#61dafb' },
  { name: 'Node.js',     pct: 90, icon: '<i class="fa-brands fa-node-js" style="color:#68a063"></i>',      stroke: '#68a063' },
  { name: 'MongoDB',     pct: 88, icon: '<i class="fa-solid fa-leaf" style="color:#47a248"></i>',           stroke: '#47a248' },
  { name: 'JavaScript',  pct: 95, icon: '<i class="fa-brands fa-js" style="color:#f7df1e"></i>',            stroke: '#f7df1e' },
  { name: 'HTML5',       pct: 97, icon: '<i class="fa-brands fa-html5" style="color:#e34f26"></i>',         stroke: '#e34f26' },
  { name: 'CSS3',        pct: 94, icon: '<i class="fa-brands fa-css3-alt" style="color:#2965f1"></i>',      stroke: '#2965f1' },
  { name: 'C / C++',     pct: 85, icon: '<i class="fa-solid fa-c" style="color:#a8b9cc"></i>',              stroke: '#a8b9cc' },
  { name: 'Express',     pct: 89, icon: '<i class="fa-solid fa-server" style="color:#ffffff"></i>',         stroke: '#ffffff' },
  { name: 'Git',         pct: 91, icon: '<i class="fa-brands fa-git-alt" style="color:#f05032"></i>',       stroke: '#f05032' },
  { name: 'Docker',      pct: 78, icon: '<i class="fa-brands fa-docker" style="color:#2496ed"></i>',        stroke: '#2496ed' },
  { name: 'Python',      pct: 80, icon: '<i class="fa-brands fa-python" style="color:#3776ab"></i>',        stroke: '#3776ab' },
  { name: 'Linux',       pct: 86, icon: '<i class="fa-brands fa-linux" style="color:#fcc624"></i>',         stroke: '#fcc624' },
];

const CIRC = 2 * Math.PI * 27; // r=27

const grid = document.getElementById('skills-grid');
SKILLS.forEach(sk => {
  const card = document.createElement('div');
  card.className = 'glass-card skill-card';
  card.dataset.pct = sk.pct;
  card.innerHTML = `
    <div class="ring-wrap">
      <svg class="ring-svg" viewBox="0 0 60 60">
        <circle class="ring-bg" cx="30" cy="30" r="27"/>
        <circle class="ring-fill" cx="30" cy="30" r="27"
          stroke="${sk.stroke}"
          stroke-dasharray="${CIRC}"
          stroke-dashoffset="${CIRC}"
          style="filter:drop-shadow(0 0 6px ${sk.stroke})"/>
      </svg>
      <div class="ring-icon">${sk.icon}</div>
    </div>
    <div class="skill-name">${sk.name}</div>
    <div class="skill-pct">0%</div>
  `;
  grid.appendChild(card);
  addTilt(card, 14);
});

/* ────────────────────────────────────────────
   INTERSECTION OBSERVER — SKILLS RINGS
──────────────────────────────────────────── */
const skillObs = new IntersectionObserver(entries => {
  entries.forEach(entry => {
    if (!entry.isIntersecting) return;
    const card  = entry.target;
    const pct   = parseInt(card.dataset.pct);
    const fill  = card.querySelector('.ring-fill');
    const pctEl = card.querySelector('.skill-pct');
    const offset = CIRC - (pct / 100) * CIRC;
    fill.style.strokeDashoffset = offset;

    let current = 0;
    const step = () => {
      current = Math.min(current + 1, pct);
      pctEl.textContent = current + '%';
      if (current < pct) requestAnimationFrame(step);
    };
    setTimeout(step, 200);
    skillObs.unobserve(card);
  });
}, { threshold: 0.3 });

document.querySelectorAll('.skill-card').forEach(c => skillObs.observe(c));

/* ────────────────────────────────────────────
   SCROLL REVEAL
──────────────────────────────────────────── */
const revealObs = new IntersectionObserver(entries => {
  entries.forEach((entry, i) => {
    if (!entry.isIntersecting) return;
    setTimeout(() => entry.target.classList.add('revealed'), i * 120);
    revealObs.unobserve(entry.target);
  });
}, { threshold: 0.15 });

document.querySelectorAll('.reveal-el').forEach(el => revealObs.observe(el));

/* Career story line draw + paragraph stagger */
const storyObs = new IntersectionObserver(entries => {
  entries.forEach(entry => {
    if (!entry.isIntersecting) return;
    const el = entry.target;
    el.classList.add('line-drawn');
    el.querySelectorAll('p').forEach((p, i) => {
      setTimeout(() => p.classList.add('revealed'), 300 + i * 180);
    });
    storyObs.unobserve(el);
  });
}, { threshold: 0.1 });

const storyEl = document.getElementById('career-story');
if (storyEl) storyObs.observe(storyEl);

/* ────────────────────────────────────────────
   CONTRIBUTION HEATMAP
──────────────────────────────────────────── */
(function buildHeatmap() {
  const WEEKS = 52, DAYS = 7;
  const MONTHS = ['Jan','Feb','Mar','Apr','May','Jun','Jul','Aug','Sep','Oct','Nov','Dec'];

  // generate realistic-looking fake contribution data
  function genData() {
    const data = [];
    const now  = new Date();
    for (let w = 0; w < WEEKS; w++) {
      const col = [];
      for (let d = 0; d < DAYS; d++) {
        const date = new Date(now);
        date.setDate(date.getDate() - ((WEEKS - 1 - w) * 7 + (DAYS - 1 - d)));
        // realistic probability curve
        const rand = Math.random();
        let count = 0;
        if (rand > 0.35) {
          const base = Math.floor(Math.random() * 18);
          count = Math.max(0, base + Math.round(Math.sin(w * 0.3) * 4));
          // spike events
          if (Math.random() > 0.92) count = 30 + Math.floor(Math.random() * 20);
        }
        col.push({ count, date });
      }
      data.push(col);
    }
    return data;
  }

  const data = genData();

  function intensityClass(count) {
    if (count === 0) return 'hm-0';
    if (count < 3)  return 'hm-1';
    if (count < 8)  return 'hm-2';
    if (count < 15) return 'hm-3';
    if (count < 25) return 'hm-4';
    return 'hm-5';
  }

  const root = document.getElementById('heatmap-root');

  // month labels
  const monthRow = document.createElement('div');
  monthRow.style.cssText = 'display:flex; margin-left:32px; margin-bottom:4px; overflow:hidden;';

  const usedMonths = new Set();
  const labels = [];
  data.forEach((col, wi) => {
    const month = col[0].date.getMonth();
    if (!usedMonths.has(month)) { usedMonths.add(month); labels.push({ wi, month }); }
  });
  // place month labels
  const labelWrap = document.createElement('div');
  labelWrap.style.cssText = `position:relative; width:${WEEKS * 15}px; height:16px;`;
  labels.forEach(lb => {
    const span = document.createElement('span');
    span.textContent = MONTHS[lb.month];
    span.style.cssText = `position:absolute; left:${lb.wi * 15}px; font-family:'JetBrains Mono',monospace;
      font-size:.62rem; color:rgba(255,255,255,0.35);`;
    labelWrap.appendChild(span);
  });
  monthRow.appendChild(labelWrap);
  root.appendChild(monthRow);

  // body
  const body = document.createElement('div');
  body.style.cssText = 'display:flex; gap:0; align-items:flex-start;';

  // day labels
  const dayCol = document.createElement('div');
  dayCol.style.cssText = 'display:flex;flex-direction:column;gap:4px;margin-right:6px;padding-top:1px;';
  ['','Mon','','Wed','','Fri',''].forEach(d => {
    const s = document.createElement('span');
    s.textContent = d;
    s.style.cssText = `height:11px;line-height:11px;font-family:'JetBrains Mono',monospace;font-size:.58rem;color:rgba(255,255,255,0.28);`;
    dayCol.appendChild(s);
  });
  body.appendChild(dayCol);

  // grid
  const gridEl = document.createElement('div');
  gridEl.style.cssText = 'display:flex; gap:4px;';

  const tooltip = document.getElementById('hm-tooltip');
  let totalContribs = 0;

  data.forEach(col => {
    const colEl = document.createElement('div');
    colEl.style.cssText = 'display:flex;flex-direction:column;gap:4px;';
    col.forEach(cell => {
      totalContribs += cell.count;
      const sq = document.createElement('div');
      sq.className = `heatmap-cell ${intensityClass(cell.count)}`;
      const dateStr = cell.date.toLocaleDateString('en-US', { month:'short', day:'numeric', year:'numeric' });
      sq.addEventListener('mouseenter', e => {
        tooltip.textContent = `${cell.count} contribution${cell.count !== 1 ? 's' : ''} · ${dateStr}`;
        tooltip.classList.add('visible');
      });
      sq.addEventListener('mousemove', e => {
        tooltip.style.left = (e.clientX + 14) + 'px';
        tooltip.style.top  = (e.clientY - 36) + 'px';
      });
      sq.addEventListener('mouseleave', () => tooltip.classList.remove('visible'));
      colEl.appendChild(sq);
    });
    gridEl.appendChild(colEl);
  });

  body.appendChild(gridEl);
  root.appendChild(body);

  // glow trail on heatmap
  const glowTrail = document.getElementById('glow-trail');
  const hmWrap = document.getElementById('heatmap-wrap');
  hmWrap.addEventListener('mousemove', e => {
    const r = hmWrap.getBoundingClientRect();
    glowTrail.style.left = (e.clientX - r.left) + 'px';
    glowTrail.style.top  = (e.clientY - r.top)  + 'px';
  });

  // count-up total contributions
  const contribHmObs = new IntersectionObserver(entries => {
    if (!entries[0].isIntersecting) return;
    countUp('total-contrib', totalContribs, 1800);
    countUp('streak-count', 47, 1200);
    countUp('repos-count', 38, 1000);
    contribHmObs.disconnect();
  }, { threshold: 0.3 });
  contribHmObs.observe(hmWrap);
})();

function countUp(id, target, duration) {
  const el = document.getElementById(id);
  if (!el) return;
  const start = performance.now();
  const step  = ts => {
    const progress = Math.min((ts - start) / duration, 1);
    const ease = 1 - Math.pow(1 - progress, 4);
    el.textContent = Math.floor(ease * target).toLocaleString();
    if (progress < 1) requestAnimationFrame(step);
    else el.textContent = target.toLocaleString();
  };
  requestAnimationFrame(step);
}

/* ────────────────────────────────────────────
   BOUNCE KEYFRAME (scroll cue)
──────────────────────────────────────────── */
const bounceStyle = document.createElement('style');
bounceStyle.textContent = `
  @keyframes bounce {
    0%,100% { transform: translateY(0); }
    50%      { transform: translateY(8px); }
  }
`;
document.head.appendChild(bounceStyle);

})();
</script>
