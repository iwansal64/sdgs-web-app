<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>SDG Report 2025</title>
<link href="https://fonts.googleapis.com/css2?family=Bebas+Neue&family=DM+Sans:wght@300;400;500;700&display=swap" rel="stylesheet">
<style>

  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  :root {
    --gold: #C49A2A;
    --gold-light: #E8C96A;
    --gold-muted: #8B6B1A;
    --orange: #E05C2A;
    --orange-light: #F08050;
    --crimson: #8B1A3A;
    --crimson-light: #C42050;
    --bg-dark: #111111;
    --bg-card: #181818;
    --bg-card2: #1E1E1E;
    --text-white: #F5F0E8;
    --text-muted: #9A9A8A;
    --border: rgba(255,255,255,0.07);
  }

  body {
    background: var(--bg-dark);
    color: var(--text-white);
    font-family: 'DM Sans', sans-serif;
    min-height: 100vh;
    overflow-x: hidden;
  }

  .hero {
    position: relative;
    min-height: 100vh;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: flex-start;
    padding: 80px 60px;
    overflow: hidden;
  }

  .hero::before {
    content: '';
    position: absolute;
    inset: 0;
    background:
      radial-gradient(ellipse 60% 70% at 80% 40%, rgba(196,154,42,0.12) 0%, transparent 60%),
      radial-gradient(ellipse 40% 50% at 20% 80%, rgba(139,26,58,0.15) 0%, transparent 60%),
      radial-gradient(ellipse 50% 60% at 60% 10%, rgba(224,92,42,0.08) 0%, transparent 60%);
    pointer-events: none;
  }

  .hero-badge {
    display: inline-flex;
    align-items: center;
    gap: 10px;
    border: 1px solid var(--gold);
    padding: 6px 16px;
    border-radius: 2px;
    font-size: 11px;
    font-weight: 700;
    letter-spacing: 3px;
    color: var(--gold);
    text-transform: uppercase;
    margin-bottom: 32px;
    animation: fadeSlideUp 0.8s ease both;
  }

  .sdg-wheel {
    width: 14px;
    height: 14px;
    border-radius: 50%;
    background: conic-gradient(
      #E5233D 0deg 26deg, #DDA63A 26deg 52deg, #4C9F38 52deg 78deg,
      #C5192D 78deg 104deg, #FF3A21 104deg 130deg, #26BDE2 130deg 156deg,
      #FCC30B 156deg 182deg, #A21942 182deg 208deg, #FD6925 208deg 234deg,
      #DD1367 234deg 260deg, #FD9D24 260deg 286deg, #BF8B2E 286deg 312deg,
      #3F7E44 312deg 338deg, #0A97D9 338deg 360deg
    );
  }

  .hero-title {
    font-family: 'Bebas Neue', sans-serif;
    font-size: clamp(72px, 12vw, 140px);
    line-height: 0.9;
    letter-spacing: -2px;
    color: var(--text-white);
    animation: fadeSlideUp 0.9s 0.1s ease both;
  }

  .hero-title span.accent-gold { color: var(--gold); }
  .hero-title span.accent-orange { color: var(--orange); }
  .hero-title span.accent-crimson { color: var(--crimson-light); }

  .hero-sub {
    margin-top: 28px;
    max-width: 560px;
    font-size: 16px;
    line-height: 1.7;
    color: var(--text-muted);
    font-weight: 300;
    animation: fadeSlideUp 1s 0.2s ease both;
  }

  .hero-cta {
    margin-top: 44px;
    display: flex;
    gap: 16px;
    flex-wrap: wrap;
    animation: fadeSlideUp 1.1s 0.3s ease both;
  }

  .btn {
    padding: 14px 32px;
    font-family: 'DM Sans', sans-serif;
    font-size: 13px;
    font-weight: 700;
    letter-spacing: 1.5px;
    text-transform: uppercase;
    border: none;
    cursor: pointer;
    border-radius: 2px;
    transition: all 0.25s;
  }

  .btn-primary {
    background: var(--gold);
    color: #111;
  }
  .btn-primary:hover { background: var(--gold-light); transform: translateY(-2px); }

  .btn-ghost {
    background: transparent;
    color: var(--text-white);
    border: 1px solid rgba(255,255,255,0.2);
  }
  .btn-ghost:hover { border-color: var(--text-white); background: rgba(255,255,255,0.05); }

  .hero-year {
    position: absolute;
    right: -20px;
    top: 50%;
    transform: translateY(-50%);
    font-family: 'Bebas Neue', sans-serif;
    font-size: clamp(180px, 28vw, 320px);
    color: rgba(255,255,255,0.03);
    letter-spacing: -8px;
    user-select: none;
    pointer-events: none;
    line-height: 1;
  }

  .scroll-cue {
    position: absolute;
    bottom: 36px;
    left: 60px;
    display: flex;
    align-items: center;
    gap: 12px;
    color: var(--text-muted);
    font-size: 11px;
    letter-spacing: 2px;
    text-transform: uppercase;
    animation: fadeSlideUp 1.3s 0.5s ease both;
  }
  .scroll-line {
    width: 40px;
    height: 1px;
    background: var(--text-muted);
  }


  .stats-strip {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    border-top: 1px solid var(--border);
    border-bottom: 1px solid var(--border);
  }

  .stat-cell {
    padding: 48px 52px;
    border-right: 1px solid var(--border);
    position: relative;
    overflow: hidden;
    transition: background 0.3s;
  }
  .stat-cell:last-child { border-right: none; }
  .stat-cell:hover { background: rgba(255,255,255,0.02); }

  .stat-cell::before {
    content: '';
    position: absolute;
    top: 0; left: 0;
    width: 3px;
    height: 100%;
  }
  .stat-cell.gold::before { background: var(--gold); }
  .stat-cell.orange::before { background: var(--orange); }
  .stat-cell.crimson::before { background: var(--crimson-light); }

  .stat-sdg-label {
    font-size: 10px;
    font-weight: 700;
    letter-spacing: 2.5px;
    text-transform: uppercase;
    color: var(--text-muted);
    margin-bottom: 20px;
  }

  .stat-number {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 80px;
    line-height: 1;
    letter-spacing: -2px;
  }
  .stat-cell.gold .stat-number { color: var(--gold); }
  .stat-cell.orange .stat-number { color: var(--orange); }
  .stat-cell.crimson .stat-number { color: var(--crimson-light); }

  .stat-unit {
    font-family: 'DM Sans', sans-serif;
    font-size: 20px;
    font-weight: 300;
    vertical-align: super;
    margin-left: 2px;
  }

  .stat-desc {
    margin-top: 12px;
    font-size: 14px;
    line-height: 1.55;
    color: var(--text-muted);
    max-width: 260px;
  }


  .section {
    padding: 100px 60px;
  }

  .section-eyebrow {
    font-size: 11px;
    font-weight: 700;
    letter-spacing: 3px;
    text-transform: uppercase;
    color: var(--text-muted);
    margin-bottom: 16px;
    display: flex;
    align-items: center;
    gap: 12px;
  }
  .section-eyebrow::after {
    content: '';
    flex: 1;
    height: 1px;
    background: var(--border);
    max-width: 60px;
  }

  .section-title {
    font-family: 'Bebas Neue', sans-serif;
    font-size: clamp(40px, 5vw, 64px);
    letter-spacing: -1px;
    line-height: 1.05;
    margin-bottom: 60px;
  }


  .card-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 2px;
    background: var(--border);
  }

  .card {
    background: var(--bg-card);
    padding: 44px 40px;
    position: relative;
    overflow: hidden;
    transition: all 0.3s;
    cursor: default;
  }

  .card:hover {
    background: var(--bg-card2);
    transform: translateY(-4px);
    z-index: 2;
    box-shadow: 0 20px 60px rgba(0,0,0,0.5);
  }

  .card-number {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 120px;
    line-height: 1;
    position: absolute;
    top: -10px;
    right: 20px;
    opacity: 0.04;
    pointer-events: none;
  }

  .card-tag {
    display: inline-block;
    padding: 4px 10px;
    font-size: 9px;
    font-weight: 700;
    letter-spacing: 2px;
    text-transform: uppercase;
    border-radius: 2px;
    margin-bottom: 24px;
  }
  .card.gold .card-tag { background: rgba(196,154,42,0.15); color: var(--gold); }
  .card.orange .card-tag { background: rgba(224,92,42,0.15); color: var(--orange); }
  .card.crimson .card-tag { background: rgba(196,32,80,0.15); color: var(--crimson-light); }

  .card-metric {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 56px;
    line-height: 1;
    margin-bottom: 8px;
  }
  .card.gold .card-metric { color: var(--gold); }
  .card.orange .card-metric { color: var(--orange); }
  .card.crimson .card-metric { color: var(--crimson-light); }

  .card-title {
    font-size: 15px;
    font-weight: 700;
    color: var(--text-white);
    margin-bottom: 12px;
    line-height: 1.3;
  }

  .card-body {
    font-size: 13px;
    line-height: 1.65;
    color: var(--text-muted);
  }

  .bar-section {
    padding: 80px 60px;
    background: rgba(255,255,255,0.015);
    border-top: 1px solid var(--border);
    border-bottom: 1px solid var(--border);
  }

  .bar-title {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 48px;
    margin-bottom: 48px;
  }

  .bar-group { margin-bottom: 28px; }

  .bar-label-row {
    display: flex;
    justify-content: space-between;
    align-items: baseline;
    margin-bottom: 8px;
  }

  .bar-label {
    font-size: 12px;
    font-weight: 700;
    letter-spacing: 1.5px;
    text-transform: uppercase;
    color: var(--text-muted);
  }

  .bar-value {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 28px;
  }

  .bar-track {
    height: 6px;
    background: rgba(255,255,255,0.06);
    border-radius: 3px;
    overflow: hidden;
  }

  .bar-fill {
    height: 100%;
    border-radius: 3px;
    transition: width 1.5s cubic-bezier(0.16,1,0.3,1);
    width: 0;
  }
  .bar-fill.gold { background: linear-gradient(90deg, var(--gold-muted), var(--gold-light)); }
  .bar-fill.orange { background: linear-gradient(90deg, #c04010, var(--orange-light)); }
  .bar-fill.crimson { background: linear-gradient(90deg, #6B1030, var(--crimson-light)); }

  /* SUPPLY CHAIN FLOW */
  .flow-section {
    padding: 80px 60px;
  }

  .flow-row {
    display: flex;
    align-items: center;
    gap: 0;
    margin-bottom: 32px;
  }

  .flow-node {
    flex: 1;
    background: var(--bg-card);
    border: 1px solid var(--border);
    padding: 20px;
    text-align: center;
    position: relative;
    transition: all 0.3s;
  }
  .flow-node:hover { background: var(--bg-card2); border-color: var(--gold); }

  .flow-icon { font-size: 28px; margin-bottom: 8px; }

  .flow-label {
    font-size: 10px;
    font-weight: 700;
    letter-spacing: 2px;
    text-transform: uppercase;
    color: var(--text-muted);
  }

  .flow-arrow {
    color: var(--gold);
    font-size: 20px;
    padding: 0 8px;
    flex-shrink: 0;
  }

  .flow-pct-badge {
    display: inline-block;
    font-family: 'Bebas Neue', sans-serif;
    font-size: 40px;
    color: var(--gold);
    margin-right: 16px;
    vertical-align: middle;
  }

  .flow-desc {
    display: inline;
    font-size: 14px;
    color: var(--text-muted);
    vertical-align: middle;
  }


  .footer {
    padding: 48px 60px;
    border-top: 1px solid var(--border);
    display: flex;
    justify-content: space-between;
    align-items: center;
    gap: 24px;
    flex-wrap: wrap;
  }

  .footer-left {
    font-size: 12px;
    color: var(--text-muted);
    letter-spacing: 1px;
  }

  .footer-right {
    font-size: 11px;
    color: var(--text-muted);
    letter-spacing: 1.5px;
    text-transform: uppercase;
  }

  .footer-divider {
    width: 1px;
    height: 40px;
    background: var(--border);
  }


  @keyframes fadeSlideUp {
    from { opacity: 0; transform: translateY(24px); }
    to   { opacity: 1; transform: translateY(0); }
  }


  @media (max-width: 768px) {
    .hero { padding: 60px 24px; }
    .stats-strip { grid-template-columns: 1fr; }
    .stat-cell { border-right: none; border-bottom: 1px solid var(--border); }
    .card-grid { grid-template-columns: 1fr; }
    .section { padding: 60px 24px; }
    .bar-section, .flow-section { padding: 60px 24px; }
    .footer { flex-direction: column; align-items: flex-start; }
    .hero-year { display: none; }
  }
</style>
</head>
<body>


<section class="hero">
  <div class="hero-badge">
    <div class="sdg-wheel"></div>
    The SDG Report · United Nations · 2025
  </div>

  <h1 class="hero-title">
    GLOBAL<br>
    PROGRESS<br>
    <span class="accent-gold">REPORT</span>
  </h1>

  <p class="hero-sub">
    Tracking humanity's most pressing challenges — from food systems and digital equity to child welfare — across the Sustainable Development Goals framework.
  </p>

  <div class="hero-cta">
    <button class="btn btn-primary" onclick={"document.getElementById('main').scrollIntoView({behavior:'smooth'})"}>Explore Data</button>
    <button class="btn btn-ghost" onclick={"window.open('https://unstats.un.org/sdgs/report/2025','_blank')"}>Full Report ↗</button>
  </div>

  <div class="hero-year">2025</div>

  <div class="scroll-cue">
    <span class="scroll-line"></span>
    Scroll to explore
  </div>
</section>


<div class="stats-strip" id="main">
  <div class="stat-cell gold">
    <div class="stat-sdg-label">SDG 12 · Responsible Consumption</div>
    <div class="stat-number">19<span class="stat-unit">%</span></div>
    <div class="stat-desc">of all food is wasted at the consumer level — in homes, grocery stores & restaurants.</div>
  </div>
  <div class="stat-cell orange">
    <div class="stat-sdg-label">SDG 9 · Industry & Innovation</div>
    <div class="stat-number">51<span class="stat-unit">%</span></div>
    <div class="stat-desc">of the global population now has access to 5G connectivity (2024 data).</div>
  </div>
  <div class="stat-cell crimson">
    <div class="stat-sdg-label">SDG 8 · Decent Work</div>
    <div class="stat-number">138<span class="stat-unit">M</span></div>
    <div class="stat-desc">children remain in child labour in 2024 — still 100M+ fewer than in 2000.</div>
  </div>
</div>


<section class="section">
  <div class="section-eyebrow">Key Findings</div>
  <h2 class="section-title">Three Dimensions<br>of Global Change</h2>

  <div class="card-grid">

    <!-- SDG 12 -->
    <div class="card gold">
      <div class="card-number">12</div>
      <div class="card-tag">SDG 12 · Food Systems</div>
      <div class="card-metric">32%</div>
      <div class="card-title">Total Food Loss & Waste</div>
      <div class="card-body">
        13% of food is lost across supply chains — from harvest through storage and processing.
        An additional 19% is wasted by consumers at home, in stores, and restaurants.
        Together this represents one of the largest systemic inefficiencies in the global economy.
      </div>
    </div>

    <!-- SDG 9 -->
    <div class="card orange">
      <div class="card-number">9</div>
      <div class="card-tag">SDG 9 · Connectivity</div>
      <div class="card-metric">84% vs 4%</div>
      <div class="card-title">The 5G Divide</div>
      <div class="card-body">
        High-income countries enjoy 84% 5G coverage, while low-income countries have access to only 4%.
        Despite global 5G reaching half the world's population, the digital divide remains an urgent structural challenge.
      </div>
    </div>

    <!-- SDG 8 -->
    <div class="card crimson">
      <div class="card-number">8</div>
      <div class="card-tag">SDG 8 · Child Labour</div>
      <div class="card-metric">-20M</div>
      <div class="card-title">Progress Since 2020</div>
      <div class="card-body">
        138 million children in child labour — a sobering figure, yet over 20 million fewer than in 2020,
        and more than 100 million fewer than in 2000. Progress is real, but far from complete.
      </div>
    </div>

  </div>
</section>


<section class="bar-section" id="bars">
  <h2 class="bar-title">Coverage & Scale at a Glance</h2>

  <div class="bar-group">
    <div class="bar-label-row">
      <span class="bar-label" style="color:var(--gold)">Food wasted at consumer level</span>
      <span class="bar-value" style="color:var(--gold)">19%</span>
    </div>
    <div class="bar-track"><div class="bar-fill gold" data-width="19"></div></div>
  </div>

  <div class="bar-group">
    <div class="bar-label-row">
      <span class="bar-label" style="color:var(--gold)">Food lost in supply chain</span>
      <span class="bar-value" style="color:var(--gold)">13%</span>
    </div>
    <div class="bar-track"><div class="bar-fill gold" data-width="13"></div></div>
  </div>

  <div class="bar-group">
    <div class="bar-label-row">
      <span class="bar-label" style="color:var(--orange)">5G — high-income countries</span>
      <span class="bar-value" style="color:var(--orange)">84%</span>
    </div>
    <div class="bar-track"><div class="bar-fill orange" data-width="84"></div></div>
  </div>

  <div class="bar-group">
    <div class="bar-label-row">
      <span class="bar-label" style="color:var(--orange)">5G — global average</span>
      <span class="bar-value" style="color:var(--orange)">51%</span>
    </div>
    <div class="bar-track"><div class="bar-fill orange" data-width="51"></div></div>
  </div>

  <div class="bar-group">
    <div class="bar-label-row">
      <span class="bar-label" style="color:var(--orange)">5G — low-income countries</span>
      <span class="bar-value" style="color:var(--orange)">4%</span>
    </div>
    <div class="bar-track"><div class="bar-fill orange" data-width="4"></div></div>
  </div>

  <div class="bar-group">
    <div class="bar-label-row">
      <span class="bar-label" style="color:var(--crimson-light)">Reduction in child labour since 2000</span>
      <span class="bar-value" style="color:var(--crimson-light)">~42%</span>
    </div>
    <div class="bar-track"><div class="bar-fill crimson" data-width="42"></div></div>
  </div>
</section>


<section class="flow-section">
  <div class="section-eyebrow">SDG 12 Deep Dive</div>
  <h2 class="section-title">Where Food<br>Is Lost</h2>

  <div style="margin-bottom:24px">
    <span class="flow-pct-badge">13%</span>
    <span class="flow-desc">lost along the supply chain</span>
  </div>

  <div class="flow-row">
    <div class="flow-node">
      <div class="flow-icon">🌾</div>
      <div class="flow-label">Harvesting</div>
    </div>
    <div class="flow-arrow">→</div>
    <div class="flow-node">
      <div class="flow-icon">🚛</div>
      <div class="flow-label">Transport</div>
    </div>
    <div class="flow-arrow">→</div>
    <div class="flow-node">
      <div class="flow-icon">🏭</div>
      <div class="flow-label">Storage</div>
    </div>
    <div class="flow-arrow">→</div>
    <div class="flow-node">
      <div class="flow-icon">⚙️</div>
      <div class="flow-label">Processing</div>
    </div>
  </div>

  <div style="margin-top:48px; margin-bottom:24px">
    <span class="flow-pct-badge" style="color:var(--gold-light)">19%</span>
    <span class="flow-desc">wasted at the consumer level</span>
  </div>

  <div class="flow-row">
    <div class="flow-node">
      <div class="flow-icon">🏠</div>
      <div class="flow-label">House</div>
    </div>
    <div class="flow-arrow" style="color:var(--gold-light)">→</div>
    <div class="flow-node">
      <div class="flow-icon">🛒</div>
      <div class="flow-label">Grocery Store</div>
    </div>
    <div class="flow-arrow" style="color:var(--gold-light)">→</div>
    <div class="flow-node">
      <div class="flow-icon">🏘️</div>
      <div class="flow-label">Household</div>
    </div>
    <div class="flow-arrow" style="color:var(--gold-light)">→</div>
    <div class="flow-node">
      <div class="flow-icon">🍽️</div>
      <div class="flow-label">Restaurant</div>
    </div>
  </div>
</section>


<footer class="footer">
  <div class="footer-left">
    <div style="font-family:'Bebas Neue',sans-serif; font-size:20px; letter-spacing:1px; color:var(--text-white); margin-bottom:6px;">THE SDG REPORT 2025</div>
    United Nations · Dept. of Economic and Social Affairs
  </div>
  <div class="footer-divider"></div>
  <div class="footer-right">
    Data: unstats.un.org/sdgs/report/2025
  </div>
</footer>

<script>

  const fills = document.querySelectorAll('.bar-fill');
  const observer = new IntersectionObserver(entries => {
    entries.forEach(e => {
      if (e.isIntersecting) {
        const w = e.target.dataset.width;
        e.target.style.width = w + '%';
        observer.unobserve(e.target);
      }
    });
  }, { threshold: 0.3 });

  fills.forEach(f => observer.observe(f));
</script>
</body>
</html>
