[elliot-watson-portfolio.html](https://github.com/user-attachments/files/29859149/elliot-watson-portfolio.html)
# personal-website<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Elliot Watson II — AI-Native Builder</title>
<meta name="description" content="Elliot Watson II. Logistics operator turned AI-native builder. Amazon DSP, High Line Moving, Pursuit, MedAI.">

<!--
  ============================================================
  PLACEHOLDERS TO REPLACE BEFORE PUBLISHING — search for "[[":
  [[EMAIL]]      — your real email
  [[LINKEDIN]]   — your LinkedIn URL
  [[GITHUB]]     — your GitHub URL (optional, delete row if none)
  [[RESUME]]     — link to your resume PDF
  [[LOCATION]]   — city/borough if you want it public
  [[DATES]]      — years at Amazon DSP / High Line Moving, if you want them shown
  Also: swap any [add metric] bracket with a real number, or delete that line.
  ============================================================
-->

<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Oswald:wght@400;500;600;700&family=IBM+Plex+Sans:wght@400;500;600&family=IBM+Plex+Mono:wght@400;500&display=swap" rel="stylesheet">

<style>
  :root{
    --bg:        #14161A;
    --bg-panel:  #1B1E23;
    --bg-panel2: #20242B;
    --ink:       #ECEAE4;
    --ink-dim:   #90949C;
    --ink-faint: #5B5F66;
    --caution:   #F5B700;
    --caution-soft: #6b5a1c;
    --signal:    #5EEAD4;
    --signal-soft: #2c4f4a;
    --line:      #2C3036;
    --line-soft: #22262c;

    --font-display: 'Oswald', 'Arial Narrow', sans-serif;
    --font-body: 'IBM Plex Sans', system-ui, -apple-system, sans-serif;
    --font-mono: 'IBM Plex Mono', 'SFMono-Regular', Menlo, Consolas, monospace;

    --max: 1120px;
  }

  *{ box-sizing: border-box; }
  html{ scroll-behavior: smooth; }

  body{
    margin:0;
    background: var(--bg);
    color: var(--ink);
    font-family: var(--font-body);
    line-height: 1.6;
    -webkit-font-smoothing: antialiased;
  }

  ::selection{ background: var(--caution); color: #14161A; }

  a{ color: inherit; }

  :focus-visible{
    outline: 2px solid var(--caution);
    outline-offset: 3px;
  }

  .wrap{
    max-width: var(--max);
    margin: 0 auto;
    padding: 0 24px;
  }

  .eyebrow{
    font-family: var(--font-mono);
    font-size: 0.72rem;
    letter-spacing: 0.14em;
    text-transform: uppercase;
    color: var(--ink-faint);
  }

  h1,h2,h3{
    font-family: var(--font-display);
    text-transform: uppercase;
    letter-spacing: 0.01em;
    margin: 0;
    line-height: 1.05;
  }

  .badge{
    display:inline-flex;
    align-items:center;
    gap:6px;
    font-family: var(--font-mono);
    font-size: 0.68rem;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    padding: 4px 10px;
    border: 1px solid var(--line);
    border-radius: 3px;
  }
  .badge::before{
    content:"";
    width:6px; height:6px;
    border-radius:50%;
    display:inline-block;
  }
  .badge--shipped{ color: var(--signal); border-color: var(--signal-soft); }
  .badge--shipped::before{ background: var(--signal); }
  .badge--progress{ color: var(--caution); border-color: var(--caution-soft); }
  .badge--progress::before{ background: var(--caution); animation: pulse 1.8s ease-in-out infinite; }

  @keyframes pulse{
    0%,100%{ opacity:1; }
    50%{ opacity:0.35; }
  }

  /* ---------- TOP BAR ---------- */
  .topbar{
    position: sticky;
    top: 0;
    z-index: 50;
    background: rgba(20,22,26,0.88);
    backdrop-filter: blur(6px);
    border-bottom: 1px solid var(--line-soft);
  }
  .topbar__inner{
    display:flex;
    align-items:center;
    justify-content:space-between;
    padding: 14px 24px;
    max-width: var(--max);
    margin: 0 auto;
    font-family: var(--font-mono);
    font-size: 0.75rem;
  }
  .topbar__id{
    letter-spacing: 0.08em;
    color: var(--ink-dim);
  }
  .topbar__id strong{ color: var(--ink); font-weight: 500; }
  .topbar nav{ display:flex; gap: 22px; flex-wrap: wrap; }
  .topbar nav a{
    text-decoration:none;
    color: var(--ink-dim);
    letter-spacing: 0.08em;
    text-transform: uppercase;
    transition: color 0.15s ease;
  }
  .topbar nav a:hover{ color: var(--caution); }

  /* ---------- HERO ---------- */
  .hero{
    padding: 96px 0 64px;
    border-bottom: 1px solid var(--line-soft);
    position: relative;
    overflow: hidden;
  }
  .hero__meta{
    font-family: var(--font-mono);
    font-size: 0.78rem;
    color: var(--ink-faint);
    letter-spacing: 0.06em;
    margin-bottom: 28px;
    display:flex;
    gap: 18px;
    flex-wrap: wrap;
  }
  .hero__meta span{ white-space: nowrap; }
  .hero__meta span::before{ content: "// "; color: var(--line); }

  .hero h1{
    font-size: clamp(2.3rem, 6vw, 4.4rem);
    max-width: 15ch;
    opacity: 0;
    transform: translateY(14px);
    animation: stamp 0.7s cubic-bezier(.2,.8,.2,1) 0.15s forwards;
  }
  .hero h1 .accent{ color: var(--caution); }

  @keyframes stamp{
    0%{ opacity:0; transform: translateY(14px) scale(0.985); }
    60%{ opacity:1; }
    100%{ opacity:1; transform: translateY(0) scale(1); }
  }

  .hero__sub{
    margin-top: 22px;
    max-width: 56ch;
    font-size: 1.08rem;
    color: var(--ink-dim);
  }
  .hero__sub strong{ color: var(--ink); font-weight: 500; }

  .hero__ctas{
    margin-top: 34px;
    display:flex;
    gap: 14px;
    flex-wrap: wrap;
  }
  .btn{
    font-family: var(--font-mono);
    font-size: 0.8rem;
    letter-spacing: 0.06em;
    text-transform: uppercase;
    text-decoration: none;
    padding: 13px 20px;
    border-radius: 2px;
    display:inline-block;
    transition: all 0.15s ease;
    border: 1px solid transparent;
  }
  .btn--primary{
    background: var(--caution);
    color: #14161A;
    font-weight: 500;
  }
  .btn--primary:hover{ background: #ffd23f; }
  .btn--ghost{
    border-color: var(--line);
    color: var(--ink);
  }
  .btn--ghost:hover{ border-color: var(--signal); color: var(--signal); }

  /* ---------- TICKER (signature element) ---------- */
  .ticker{
    border-bottom: 1px solid var(--line-soft);
    background: var(--bg-panel);
    overflow: hidden;
    white-space: nowrap;
    padding: 11px 0;
  }
  .ticker__track{
    display: inline-flex;
    animation: scroll 32s linear infinite;
  }
  .ticker__seg{
    font-family: var(--font-mono);
    font-size: 0.76rem;
    letter-spacing: 0.05em;
    color: var(--ink-dim);
    padding-right: 48px;
  }
  .ticker__seg .dot{ color: var(--ink-faint); padding: 0 10px; }
  .ticker__seg .ok{ color: var(--signal); }
  .ticker__seg .live{ color: var(--caution); }

  @keyframes scroll{
    from{ transform: translateX(0); }
    to{ transform: translateX(-50%); }
  }

  /* ---------- SECTION shell ---------- */
  section{ padding: 80px 0; border-bottom: 1px solid var(--line-soft); }
  .section__head{ margin-bottom: 44px; }
  .section__head .eyebrow{ margin-bottom: 10px; }
  .section__head h2{ font-size: clamp(1.6rem, 3.4vw, 2.5rem); }
  .section__lede{
    margin-top: 14px;
    max-width: 62ch;
    color: var(--ink-dim);
    font-size: 1rem;
  }

  .reveal{
    opacity: 0;
    transform: translateY(18px);
    transition: opacity 0.6s ease, transform 0.6s ease;
  }
  .reveal.is-visible{ opacity: 1; transform: translateY(0); }

  /* ---------- STOPS ---------- */
  .stops{ display: grid; gap: 18px; }
  .stop{
    position: relative;
    background: var(--bg-panel);
    border: 1px solid var(--line);
    border-radius: 4px;
    padding: 30px 28px;
    display: grid;
    grid-template-columns: 100px 1fr;
    gap: 26px;
    overflow: hidden;
  }
  .stop::before{
    content:"";
    position:absolute;
    top:0; left:-40%;
    width: 40%; height: 100%;
    background: linear-gradient(90deg, transparent, rgba(94,234,212,0.08), transparent);
    transition: left 0.6s ease;
    pointer-events:none;
  }
  .stop:hover::before{ left: 120%; }

  .stop__num{
    font-family: var(--font-mono);
    color: var(--ink-faint);
    font-size: 0.78rem;
    letter-spacing: 0.05em;
  }
  .stop__num b{
    display:block;
    font-family: var(--font-display);
    font-size: 2.6rem;
    color: var(--line);
    line-height: 1;
    margin-top: 4px;
  }
  .stop__body h3{
    font-size: 1.3rem;
    margin-bottom: 6px;
  }
  .stop__role{
    font-family: var(--font-mono);
    font-size: 0.78rem;
    color: var(--ink-dim);
    margin-bottom: 14px;
    letter-spacing: 0.02em;
  }
  .stop__body p{
    color: var(--ink-dim);
    max-width: 60ch;
    margin: 0 0 12px;
  }
  .stop__badges{ display:flex; gap:10px; margin-top: 14px; flex-wrap: wrap; }

  @media (max-width: 640px){
    .stop{ grid-template-columns: 1fr; gap: 10px; }
    .stop__num b{ font-size: 1.8rem; }
  }

  /* ---------- LOOP DIAGRAM ---------- */
  .loop{
    display:grid;
    grid-template-columns: 1fr 1fr;
    gap: 40px;
    align-items: center;
  }
  .loop__text p{ color: var(--ink-dim); max-width: 46ch; }
  .loop__text p strong{ color: var(--ink); }
  .loop svg{ width: 100%; height: auto; }

  @media (max-width: 800px){
    .loop{ grid-template-columns: 1fr; }
  }

  /* ---------- MEDAI SPEC SHEET ---------- */
  .spec{
    background: var(--bg-panel);
    border: 1px solid var(--line);
    border-radius: 4px;
    overflow: hidden;
  }
  .spec__top{
    display:flex;
    justify-content: space-between;
    align-items:center;
    padding: 20px 26px;
    border-bottom: 1px solid var(--line);
    flex-wrap: wrap;
    gap: 12px;
  }
  .spec__top h3{ font-size: 1.1rem; letter-spacing: 0.04em; }
  .spec__row{
    display:grid;
    grid-template-columns: 200px 1fr;
    gap: 20px;
    padding: 22px 26px;
    border-bottom: 1px solid var(--line-soft);
  }
  .spec__row:last-child{ border-bottom:none; }
  .spec__label{
    font-family: var(--font-mono);
    font-size: 0.74rem;
    letter-spacing: 0.08em;
    text-transform: uppercase;
    color: var(--signal);
  }
  .spec__val{ color: var(--ink-dim); }
  .spec__val strong{ color: var(--ink); font-weight: 500; }

  @media (max-width: 640px){
    .spec__row{ grid-template-columns: 1fr; gap: 6px; }
  }

  /* ---------- MANIFEST / SKILLS ---------- */
  .manifest{
    display:grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 1px;
    background: var(--line);
    border: 1px solid var(--line);
    border-radius: 4px;
    overflow:hidden;
  }
  .manifest__col{ background: var(--bg-panel); padding: 26px 24px; }
  .manifest__col h4{
    font-family: var(--font-mono);
    font-size: 0.72rem;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    color: var(--ink-faint);
    margin: 0 0 16px;
  }
  .manifest__col ul{ list-style:none; margin:0; padding:0; }
  .manifest__col li{
    padding: 9px 0;
    border-top: 1px solid var(--line-soft);
    font-size: 0.92rem;
    color: var(--ink-dim);
  }
  .manifest__col li:first-of-type{ border-top:none; }
  .manifest__col li strong{ color: var(--ink); font-weight: 500; }

  @media (max-width: 800px){
    .manifest{ grid-template-columns: 1fr; }
  }

  /* ---------- CONTACT ---------- */
  .contact{ border-bottom:none; }
  .contact__panel{
    background: var(--bg-panel);
    border: 1px solid var(--line);
    border-radius: 4px;
    padding: 46px;
    display:flex;
    justify-content: space-between;
    align-items:flex-end;
    flex-wrap: wrap;
    gap: 30px;
  }
  .contact__panel h2{
    font-size: clamp(1.6rem, 4vw, 2.6rem);
    max-width: 14ch;
  }
  .contact__links{
    font-family: var(--font-mono);
    font-size: 0.9rem;
    display:flex;
    flex-direction:column;
    gap: 10px;
  }
  .contact__links a{
    text-decoration:none;
    color: var(--ink-dim);
    border-bottom: 1px solid var(--line);
    padding-bottom: 2px;
    transition: color 0.15s ease, border-color 0.15s ease;
  }
  .contact__links a:hover{ color: var(--caution); border-color: var(--caution); }

  footer{
    padding: 26px 0 60px;
    text-align:center;
    font-family: var(--font-mono);
    font-size: 0.7rem;
    color: var(--ink-faint);
    letter-spacing: 0.08em;
  }

  @media (prefers-reduced-motion: reduce){
    *, *::before, *::after{
      animation-duration: 0.001ms !important;
      animation-iteration-count: 1 !important;
      transition-duration: 0.001ms !important;
      scroll-behavior: auto !important;
    }
    .ticker__track{ animation: none; }
  }
</style>
</head>
<body>

<div class="topbar">
  <div class="topbar__inner">
    <div class="topbar__id"><strong>E. WATSON II</strong> — AI-Native Builder</div>
    <nav>
      <a href="#stops">Route</a>
      <a href="#system">System</a>
      <a href="#medai">MedAI</a>
      <a href="#manifest">Manifest</a>
      <a href="#contact">Contact</a>
    </nav>
  </div>
</div>

<header class="hero">
  <div class="wrap">
    <div class="hero__meta">
      <span>Manifest No. EW‑002</span>
      <span>Route: Dock → Code</span>
      <span>Status: Active</span>
    </div>
    <h1>Proof on the dock. <span class="accent">Proof in the code.</span></h1>
    <p class="hero__sub">
      <strong>Elliot Watson II</strong> builds systems the way he ran routes — under real time pressure,
      with no room for theory that doesn't survive contact with the floor. Years inside Amazon DSP and
      High Line Moving logistics. Now applying the same execution discipline to AI-native product
      development at Pursuit, building MedAI.
    </p>
    <div class="hero__ctas">
      <a class="btn btn--primary" href="#medai">See the MedAI build</a>
      <a class="btn btn--ghost" href="[[RESUME]]">Resume ↗</a>
      <a class="btn btn--ghost" href="mailto:[[EMAIL]]">Get in touch</a>
    </div>
  </div>
</header>

<div class="ticker" aria-hidden="true">
  <div class="ticker__track">
    <span class="ticker__seg">SCAN 001 <span class="dot">·</span> AMAZON DSP <span class="dot">·</span> <span class="ok">ROUTE COMPLETE</span> <span class="dot">//</span> SCAN 002 <span class="dot">·</span> HIGH LINE MOVING <span class="dot">·</span> <span class="ok">ROUTE COMPLETE</span> <span class="dot">//</span> SCAN 003 <span class="dot">·</span> PURSUIT AI‑NATIVE BUILDER <span class="dot">·</span> <span class="live">IN PROGRESS</span> <span class="dot">//</span> SCAN 004 <span class="dot">·</span> MEDAI <span class="dot">·</span> <span class="live">BUILDING</span> <span class="dot">//</span> STATUS <span class="dot">·</span> IN TRANSIT <span class="dot">//</span></span>
    <span class="ticker__seg">SCAN 001 <span class="dot">·</span> AMAZON DSP <span class="dot">·</span> <span class="ok">ROUTE COMPLETE</span> <span class="dot">//</span> SCAN 002 <span class="dot">·</span> HIGH LINE MOVING <span class="dot">·</span> <span class="ok">ROUTE COMPLETE</span> <span class="dot">//</span> SCAN 003 <span class="dot">·</span> PURSUIT AI‑NATIVE BUILDER <span class="dot">·</span> <span class="live">IN PROGRESS</span> <span class="dot">//</span> SCAN 004 <span class="dot">·</span> MEDAI <span class="dot">·</span> <span class="live">BUILDING</span> <span class="dot">//</span> STATUS <span class="dot">·</span> IN TRANSIT <span class="dot">//</span></span>
  </div>
</div>

<section id="stops">
  <div class="wrap">
    <div class="section__head reveal">
      <div class="eyebrow">The Route</div>
      <h2>Three real stops, in order</h2>
      <p class="section__lede">
        Not a numbered list for decoration — this is the actual sequence. Each stop fed the next.
      </p>
    </div>

    <div class="stops">
      <div class="stop reveal">
        <div class="stop__num">STOP<b>01</b></div>
        <div class="stop__body">
          <h3>Dock &amp; Route</h3>
          <div class="stop__role">Amazon DSP · High Line Moving — Logistics &amp; Warehouse Floor [[DATES]]</div>
          <p>
            Years running routes and managing floor operations, where every inefficiency cost money and
            every broken process showed up immediately — not in a postmortem. This is where the execution
            discipline comes from. [add metric — routes/day, on-time %, whatever's real]
          </p>
          <div class="stop__badges"><span class="badge badge--shipped">Complete</span></div>
        </div>
      </div>

      <div class="stop reveal">
        <div class="stop__num">STOP<b>02</b></div>
        <div class="stop__body">
          <h3>Pursuit</h3>
          <div class="stop__role">AI-Native Builder Program — Queens, NY</div>
          <p>
            Reset the skill baseline and rebuilt from execution up — full-stack, AI-native product
            development, learned by shipping real code instead of stopping at architecture and PRDs.
          </p>
          <div class="stop__badges"><span class="badge badge--progress">In progress</span></div>
        </div>
      </div>

      <div class="stop reveal">
        <div class="stop__num">STOP<b>03</b></div>
        <div class="stop__body">
          <h3>MedAI</h3>
          <div class="stop__role">Multi-agent post-discharge care system — Pursuit portfolio project</div>
          <p>
            Architecting and building a system for patients most likely to fall through the cracks after
            discharge — including a proxy-user model for patients who can't reliably self-report. Details
            below.
          </p>
          <div class="stop__badges"><span class="badge badge--progress">Building</span></div>
        </div>
      </div>
    </div>
  </div>
</section>

<section id="system">
  <div class="wrap">
    <div class="section__head reveal">
      <div class="eyebrow">System Thinking</div>
      <h2>Compounding loops, not isolated tasks</h2>
    </div>

    <div class="loop reveal">
      <div class="loop__text">
        <p>
          The throughline is simple: <strong>he sees compounding loops where others see isolated tasks.</strong>
          Ops discipline sharpens systems thinking. Systems thinking ships product. Shipped product
          proves the discipline again — and the loop tightens each pass.
        </p>
        <p>
          It's the same lens applied twice: once on a dock floor where every broken process was visible
          in real time, now inside a multi-agent architecture where the same is true.
        </p>
      </div>
      <svg viewBox="0 0 400 340" xmlns="http://www.w3.org/2000/svg" role="img" aria-label="Diagram of a three-part compounding loop: operations discipline, systems thinking, shipped product, feeding back into operations discipline.">
        <defs>
          <marker id="arrow" viewBox="0 0 10 10" refX="8" refY="5" markerWidth="7" markerHeight="7" orient="auto-start-reverse">
            <path d="M0,0 L10,5 L0,10 z" fill="#5EEAD4"></path>
          </marker>
        </defs>

        <path d="M 130 70 A 130 130 0 0 1 320 190" fill="none" stroke="#5EEAD4" stroke-width="2" marker-end="url(#arrow)"></path>
        <path d="M 320 220 A 130 130 0 0 1 150 300" fill="none" stroke="#5EEAD4" stroke-width="2" marker-end="url(#arrow)"></path>
        <path d="M 120 280 A 130 130 0 0 1 105 100" fill="none" stroke="#5EEAD4" stroke-width="2" marker-end="url(#arrow)"></path>

        <g>
          <circle cx="110" cy="70" r="58" fill="#1B1E23" stroke="#2C3036"></circle>
          <text x="110" y="65" text-anchor="middle" fill="#ECEAE4" font-family="Oswald, sans-serif" font-size="14" letter-spacing="0.5">OPS</text>
          <text x="110" y="82" text-anchor="middle" fill="#ECEAE4" font-family="Oswald, sans-serif" font-size="14" letter-spacing="0.5">DISCIPLINE</text>
        </g>

        <g>
          <circle cx="330" cy="205" r="58" fill="#1B1E23" stroke="#2C3036"></circle>
          <text x="330" y="200" text-anchor="middle" fill="#ECEAE4" font-family="Oswald, sans-serif" font-size="14">SYSTEMS</text>
          <text x="330" y="217" text-anchor="middle" fill="#ECEAE4" font-family="Oswald, sans-serif" font-size="14">THINKING</text>
        </g>

        <g>
          <circle cx="105" cy="290" r="58" fill="#1B1E23" stroke="#2C3036"></circle>
          <text x="105" y="285" text-anchor="middle" fill="#ECEAE4" font-family="Oswald, sans-serif" font-size="14">SHIPPED</text>
          <text x="105" y="302" text-anchor="middle" fill="#ECEAE4" font-family="Oswald, sans-serif" font-size="14">PRODUCT</text>
        </g>
      </svg>
    </div>
  </div>
</section>

<section id="medai">
  <div class="wrap">
    <div class="section__head reveal">
      <div class="eyebrow">Build Log</div>
      <h2>MedAI</h2>
      <p class="section__lede">
        A multi-agent post-discharge follow-up system, built for the patients most likely to slip
        through — including the ones who can't reliably speak for themselves.
      </p>
    </div>

    <div class="spec reveal">
      <div class="spec__top">
        <h3>System Spec — MedAI</h3>
        <span class="badge badge--progress">Status: In development</span>
      </div>
      <div class="spec__row">
        <div class="spec__label">Problem</div>
        <div class="spec__val">Patients fall through the cracks after discharge — <strong>especially</strong> those who
          can't reliably self-report symptoms, medication adherence, or complications.</div>
      </div>
      <div class="spec__row">
        <div class="spec__label">Architecture</div>
        <div class="spec__val"><strong>Multi-agent orchestration</strong> coordinating follow-up, escalation, and
          check-in logic across a patient's post-discharge window.</div>
      </div>
      <div class="spec__row">
        <div class="spec__label">Proxy-user model</div>
        <div class="spec__val">Extends the system's reach to <strong>cognitively vulnerable patients</strong> —
          designed so a trusted proxy can act on the patient's behalf without breaking the follow-up loop.</div>
      </div>
      <div class="spec__row">
        <div class="spec__label">Accountability layer</div>
        <div class="spec__val"><strong>Structured logging and a UI layer</strong> so care teams can see what the
          system did, when, and why — not a black box.</div>
      </div>
      <div class="spec__row">
        <div class="spec__label">Context</div>
        <div class="spec__val">Built as a portfolio project through <strong>Pursuit's AI-native builder program</strong>,
          Queens, NY.</div>
      </div>
    </div>
  </div>
</section>

<section id="manifest">
  <div class="wrap">
    <div class="section__head reveal">
      <div class="eyebrow">Cargo Manifest</div>
      <h2>What's on the truck</h2>
    </div>

    <div class="manifest reveal">
      <div class="manifest__col">
        <h4>Operations</h4>
        <ul>
          <li><strong>Route &amp; floor operations</strong> under hard time windows</li>
          <li><strong>Process design</strong> where failures are immediate, not deferred</li>
          <li><strong>Throughput &amp; efficiency</strong> thinking, dock to delivery</li>
        </ul>
      </div>
      <div class="manifest__col">
        <h4>AI-Native Building</h4>
        <ul>
          <li><strong>Multi-agent system architecture</strong></li>
          <li><strong>Agent orchestration</strong> &amp; prompt engineering</li>
          <li><strong>Full-stack</strong> AI-native product development</li>
        </ul>
      </div>
      <div class="manifest__col">
        <h4>Systems Thinking</h4>
        <ul>
          <li><strong>Compounding-loop / flywheel</strong> design</li>
          <li><strong>Proxy-user modeling</strong> for vulnerable end users</li>
          <li><strong>Structured logging</strong> for auditability</li>
        </ul>
      </div>
    </div>
  </div>
</section>

<section id="contact" class="contact">
  <div class="wrap">
    <div class="contact__panel reveal">
      <h2>Delivery confirmation.</h2>
      <div class="contact__links">
        <a href="mailto:[[EMAIL]]">[[EMAIL]]</a>
        <a href="[[LINKEDIN]]">LinkedIn ↗</a>
        <a href="[[GITHUB]]">GitHub ↗</a>
        <a href="[[RESUME]]">Resume (PDF) ↗</a>
      </div>
    </div>
  </div>
</section>

<footer>MANIFEST CLOSED // SIGNED: E. WATSON II // [[LOCATION]]</footer>

<script>
  // Scroll-reveal
  const revealEls = document.querySelectorAll('.reveal');
  if ('IntersectionObserver' in window) {
    const io = new IntersectionObserver((entries) => {
      entries.forEach(entry => {
        if (entry.isIntersecting) {
          entry.target.classList.add('is-visible');
          io.unobserve(entry.target);
        }
      });
    }, { threshold: 0.15 });
    revealEls.forEach(el => io.observe(el));
  } else {
    revealEls.forEach(el => el.classList.add('is-visible'));
  }
</script>

</body>
</html>
