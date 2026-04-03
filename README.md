[tackle-box.html](https://github.com/user-attachments/files/26467902/tackle-box.html)
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>The Tackle Box – The Angler's Guide</title>
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@400;700;900&family=Libre+Baskerville:ital,wght@0,400;0,700;1,400&family=Source+Code+Pro:wght@400;600&display=swap" rel="stylesheet"/>
<style>
  :root {
    --ink: #1a1208;
    --paper: #f5efe2;
    --paper2: #ede4cf;
    --water: #2c6e7a;
    --water-dark: #1a4a54;
    --moss: #4a6741;
    --mud: #7a5c38;
    --gold: #c4922a;
    --gold-light: #e8b84b;
    --rust: #8b3a1e;
    --cream: #f9f3e3;
    --border: #c9b99a;
  }
  * { box-sizing: border-box; margin: 0; padding: 0; }
  body { font-family: 'Libre Baskerville', Georgia, serif; background: var(--paper); color: var(--ink); }

  /* HEADER */
  header {
    background: linear-gradient(135deg, #0a2028 0%, #1a4a54 50%, #2c6e7a 100%);
    color: var(--paper); text-align: center;
    padding: 3rem 1.5rem 2.5rem; position: relative; overflow: hidden;
    border-bottom: 5px solid var(--gold);
  }
  header::before {
    content:''; position:absolute; inset:0;
    background: repeating-linear-gradient(0deg, transparent, transparent 40px, rgba(255,255,255,.015) 40px, rgba(255,255,255,.015) 41px),
                repeating-linear-gradient(90deg, transparent, transparent 60px, rgba(255,255,255,.015) 60px, rgba(255,255,255,.015) 61px);
    pointer-events:none;
  }
  .hbadge {
    display:inline-flex; align-items:center; justify-content:center;
    width:82px; height:82px; border-radius:50%;
    border:2px solid rgba(196,146,42,.6);
    background:rgba(196,146,42,.12);
    font-size:2.5rem; margin-bottom:1rem;
    animation:float 4s ease-in-out infinite;
  }
  @keyframes float{0%,100%{transform:translateY(0)}50%{transform:translateY(-8px)}}
  h1 { font-family:'Playfair Display',serif; font-weight:900; font-size:clamp(2.5rem,6vw,4.6rem); line-height:1; color:#fff; text-shadow:2px 4px 24px rgba(0,0,0,.5); }
  h1 span { color:var(--gold-light); }
  .subtitle { font-family:'Source Code Pro',monospace; font-size:.82rem; letter-spacing:.36em; text-transform:uppercase; color:rgba(255,255,255,.55); margin-top:.5rem; }
  .hline { width:140px; height:2px; background:linear-gradient(90deg,transparent,var(--gold),transparent); margin:1.1rem auto 0; }

  /* NAV */
  nav {
    background:var(--water-dark); border-bottom:3px solid var(--gold);
    display:flex; justify-content:center;
    position:sticky; top:0; z-index:100; overflow-x:auto;
  }
  nav button {
    font-family:'Source Code Pro',monospace; font-size:.78rem;
    letter-spacing:.12em; text-transform:uppercase; font-weight:600;
    color:rgba(255,255,255,.58); background:transparent; border:none;
    padding:1rem 1.8rem; cursor:pointer; transition:all .25s; white-space:nowrap;
    position:relative;
  }
  nav button::after { content:''; position:absolute; bottom:-3px; left:0; right:0; height:3px; background:var(--gold-light); transform:scaleX(0); transition:transform .25s; }
  nav button:hover { color:rgba(255,255,255,.92); background:rgba(255,255,255,.05); }
  nav button.active { color:#fff; background:rgba(196,146,42,.15); }
  nav button.active::after { transform:scaleX(1); }

  /* LAYOUT */
  main { max-width:1160px; margin:0 auto; padding:2.5rem 1.5rem 5rem; }
  .tab-panel { display:none; animation:fadeIn .4s ease; }
  .tab-panel.active { display:block; }
  @keyframes fadeIn { from{opacity:0;transform:translateY(12px)} to{opacity:1;transform:translateY(0)} }

  .sec-title { font-family:'Playfair Display',serif; font-size:clamp(1.9rem,4vw,2.7rem); font-weight:900; color:var(--water-dark); }
  .sec-title em { color:var(--gold); font-style:normal; }
  .sec-lead { color:#6b5a44; font-style:italic; font-size:1rem; border-left:3px solid var(--gold); padding-left:1rem; margin:.5rem 0 2.2rem; }

  /* ── CONDITION SECTION ── */
  .cond-section { margin-bottom:3rem; }
  .cond-section-header {
    display:flex; align-items:center; gap:1rem;
    background:var(--water-dark);
    color:#fff; padding:1rem 1.4rem;
    border-radius:4px 4px 0 0;
    border-bottom:3px solid var(--gold);
  }
  .cond-section-header .ci { font-size:2rem; }
  .cond-h-title { font-family:'Playfair Display',serif; font-size:1.5rem; font-weight:700; }
  .cond-h-sub { font-family:'Source Code Pro',monospace; font-size:.68rem; letter-spacing:.15em; text-transform:uppercase; color:var(--gold-light); margin-top:.15rem; }
  .cond-section-body { background:var(--cream); border:1.5px solid var(--border); border-top:none; border-radius:0 0 4px 4px; padding:1.4rem; }
  .cond-tip-bar {
    background:rgba(44,110,122,.1); border-left:3px solid var(--water);
    padding:.65rem 1rem; font-size:.84rem; font-style:italic; color:#2a4a52;
    border-radius:0 3px 3px 0; margin-bottom:1.2rem;
  }

  /* bait grid inside each condition */
  .bait-grid { display:grid; grid-template-columns:repeat(auto-fill,minmax(230px,1fr)); gap:1rem; }
  .bait-card {
    background:#fff; border:1.5px solid var(--border); border-radius:3px;
    padding:1rem 1.1rem 1rem;
    transition:transform .2s, box-shadow .2s;
    box-shadow:2px 2px 0 rgba(0,0,0,.05);
  }
  .bait-card:hover { transform:translateY(-3px); box-shadow:4px 8px 20px rgba(0,0,0,.1); }
  .bait-icon-row { display:flex; align-items:center; gap:.5rem; margin-bottom:.45rem; }
  .bait-emoji { font-size:1.5rem; }
  .bait-name { font-family:'Playfair Display',serif; font-size:1rem; font-weight:700; color:var(--water-dark); }
  .bait-type { font-family:'Source Code Pro',monospace; font-size:.62rem; letter-spacing:.13em; text-transform:uppercase; color:var(--mud); margin-bottom:.45rem; }
  .bait-desc { font-size:.82rem; line-height:1.6; color:#3a3020; margin-bottom:.55rem; }
  .bait-meta { display:flex; flex-wrap:wrap; gap:.3rem; }
  .bm { font-family:'Source Code Pro',monospace; font-size:.66rem; padding:.18rem .5rem; border-radius:2px; border:1px solid; font-weight:600; }
  .bm-color { background:rgba(196,146,42,.1); color:var(--mud); border-color:rgba(196,146,42,.3); }
  .bm-size  { background:rgba(44,110,122,.1); color:var(--water-dark); border-color:rgba(44,110,122,.3); }
  .bm-depth { background:rgba(74,103,65,.1); color:var(--moss); border-color:rgba(74,103,65,.3); }
  .bm-action{ background:rgba(139,58,30,.1); color:var(--rust); border-color:rgba(139,58,30,.25); }

  /* ── CLIMATE TAB ── */
  .climate-grid { display:grid; grid-template-columns:repeat(auto-fill,minmax(330px,1fr)); gap:1.8rem; }
  .climate-card { border-radius:5px; overflow:hidden; border:1.5px solid var(--border); box-shadow:3px 3px 0 rgba(0,0,0,.07); transition:transform .2s,box-shadow .2s; }
  .climate-card:hover { transform:translateY(-4px); box-shadow:6px 12px 28px rgba(0,0,0,.13); }
  .climate-hdr { padding:1.1rem 1.4rem .7rem; }
  .climate-card:nth-child(1) .climate-hdr { background:#1a3a28; }
  .climate-card:nth-child(2) .climate-hdr { background:#1a3050; }
  .climate-card:nth-child(3) .climate-hdr { background:#0f2f36; }
  .climate-card:nth-child(4) .climate-hdr { background:#2e1a0a; }
  .climate-card:nth-child(5) .climate-hdr { background:#2a1a2a; }
  .climate-card:nth-child(6) .climate-hdr { background:#1a2a10; }
  .climate-hdr h3 { font-family:'Playfair Display',serif; font-size:1.3rem; font-weight:700; color:#fff; }
  .climate-region { font-family:'Source Code Pro',monospace; font-size:.66rem; letter-spacing:.2em; text-transform:uppercase; color:var(--gold-light); margin-top:.2rem; }
  .climate-body { padding:1.1rem 1.4rem 1.4rem; background:var(--cream); }
  .climate-body p { font-size:.85rem; line-height:1.7; color:#4a3c2a; margin-bottom:.9rem; }
  .season-block { margin-top:.8rem; }
  .season-title { font-family:'Source Code Pro',monospace; font-size:.66rem; letter-spacing:.16em; text-transform:uppercase; color:var(--mud); font-weight:600; margin-bottom:.35rem; }
  .season-baits { list-style:none; }
  .season-baits li { font-size:.83rem; line-height:1.55; padding:.12rem 0; display:flex; gap:.5rem; }
  .season-baits li::before { content:'›'; color:var(--gold); font-weight:bold; font-size:1rem; flex-shrink:0; }
  .tags { display:flex; flex-wrap:wrap; gap:.35rem; margin-top:.4rem; }
  .tag { font-family:'Source Code Pro',monospace; font-size:.7rem; padding:.22rem .55rem; border-radius:2px; font-weight:600; letter-spacing:.04em; }
  .tw { background:rgba(44,110,122,.12); color:var(--water-dark); border:1px solid rgba(44,110,122,.25); }
  .tg { background:rgba(196,146,42,.12); color:var(--mud); border:1px solid rgba(196,146,42,.3); }
  .tm { background:rgba(74,103,65,.12); color:var(--moss); border:1px solid rgba(74,103,65,.25); }
  .tr { background:rgba(139,58,30,.1); color:var(--rust); border:1px solid rgba(139,58,30,.2); }

  /* ── KNOTS TAB ── */
  .knots-grid { display:grid; grid-template-columns:repeat(auto-fill,minmax(320px,1fr)); gap:1.8rem; }
  .knot-card { background:var(--cream); border:1.5px solid var(--border); border-radius:4px; overflow:hidden; box-shadow:3px 3px 0 rgba(0,0,0,.07); transition:transform .2s,box-shadow .2s; }
  .knot-card:hover { transform:translateY(-4px); box-shadow:6px 12px 28px rgba(0,0,0,.13); }
  .knot-hdr { padding:.9rem 1.3rem .6rem; border-bottom:1px solid var(--border); background:var(--water-dark); }
  .knot-name { font-family:'Playfair Display',serif; font-size:1.3rem; font-weight:700; color:#fff; }
  .knot-rating { font-family:'Source Code Pro',monospace; font-size:.66rem; letter-spacing:.12em; text-transform:uppercase; color:var(--gold-light); margin-top:.2rem; }
  .knot-body { padding:1rem 1.3rem 1.3rem; }
  .knot-desc { font-size:.85rem; line-height:1.65; color:#4a3c2a; margin-bottom:.9rem; }
  .knot-steps { list-style:none; counter-reset:steps; }
  .knot-steps li { counter-increment:steps; display:flex; gap:.7rem; font-size:.81rem; line-height:1.55; padding:.28rem 0; align-items:flex-start; border-bottom:1px dashed rgba(0,0,0,.07); }
  .knot-steps li:last-child { border-bottom:none; }
  .knot-steps li::before { content:counter(steps); font-family:'Source Code Pro',monospace; font-size:.66rem; font-weight:600; background:var(--water); color:#fff; width:20px; height:20px; border-radius:50%; display:flex; align-items:center; justify-content:center; flex-shrink:0; margin-top:1px; }
  .knot-use { margin-top:.8rem; background:rgba(74,103,65,.1); border-left:3px solid var(--moss); padding:.55rem .9rem; font-size:.8rem; font-style:italic; color:#3a5040; border-radius:0 3px 3px 0; }

  /* ── TABLES ── */
  .ref-wrap { overflow-x:auto; margin-top:1.5rem; }
  .ref-table { width:100%; border-collapse:collapse; font-size:.84rem; }
  .ref-table thead tr { background:var(--water-dark); color:#fff; }
  .ref-table th { padding:.7rem 1rem; text-align:left; font-family:'Source Code Pro',monospace; font-weight:600; letter-spacing:.1em; text-transform:uppercase; font-size:.68rem; }
  .ref-table td { padding:.6rem 1rem; }
  .ref-table tr:nth-child(odd) td { background:var(--cream); }
  .ref-table tr:nth-child(even) td { background:var(--paper2); }
  .ref-table tbody td { border-bottom:1px solid var(--border); }

  .ornament { text-align:center; color:var(--gold); font-size:1.1rem; letter-spacing:.5em; margin:2.5rem 0; opacity:.5; }
  .h3-sec { font-family:'Playfair Display',serif; font-size:1.5rem; color:var(--water-dark); margin-bottom:1rem; }

  footer { background:var(--water-dark); color:rgba(255,255,255,.5); text-align:center; padding:1.8rem; font-family:'Source Code Pro',monospace; font-size:.7rem; letter-spacing:.12em; text-transform:uppercase; border-top:3px solid var(--gold); }
  footer span { color:var(--gold-light); }
  ::-webkit-scrollbar { width:8px; height:8px; }
  ::-webkit-scrollbar-track { background:var(--paper); }
  ::-webkit-scrollbar-thumb { background:var(--water); border-radius:4px; }
</style>
</head>
<body>

<header>
  <div class="hbadge">🎣</div>
  <h1>The <span>Tackle Box</span></h1>
  <p class="subtitle">The Angler's Guide</p>
  <div class="hline"></div>
</header>

<nav>
  <button class="active" onclick="showTab('lures',this)">🌊 Lure Conditions</button>
  <button onclick="showTab('climate',this)">🌎 Climate Guide</button>
  <button onclick="showTab('knots',this)">🪢 Knots</button>
</nav>

<main>

<!-- ═══════════════════════════════════════════
     TAB 1 — LURE CONDITIONS
═══════════════════════════════════════════ -->
<div id="tab-lures" class="tab-panel active">

  <div class="sec-title">Best Lures by <em>Condition</em></div>
  <p class="sec-lead">Bass behavior shifts with every change in sky, water, and temperature. Match your bait to the moment and put more fish in the boat.</p>

  <!-- ░░ CLOUDY ░░ -->
  <div class="cond-section">
    <div class="cond-section-header">
      <span class="ci">☁️</span>
      <div><div class="cond-h-title">Overcast / Cloudy</div><div class="cond-h-sub">Low light · Bass roam shallow &amp; feed aggressively</div></div>
    </div>
    <div class="cond-section-body">
      <div class="cond-tip-bar">💡 Cloudy days compress the strike zone upward — bass leave the bottom and hunt shallow. Go bigger, louder, and faster than normal. Best topwater window outside of dawn.</div>
      <div class="bait-grid">
        <div class="bait-card">
          <div class="bait-icon-row"><span class="bait-emoji">🌀</span><span class="bait-name">Spinnerbait</span></div>
          <div class="bait-type">Vibration · Search Bait</div>
          <div class="bait-desc">The undisputed king of cloudy conditions. Tandem willow blades for clear water, big Colorado blades for stained. Slow roll it just under the surface with a white or chartreuse skirt.</div>
          <div class="bait-meta"><span class="bm bm-color">White / Chartreuse</span><span class="bm bm-size">3/8–3/4 oz</span><span class="bm bm-depth">0–6 ft</span><span class="bm bm-action">Medium-Fast</span></div>
        </div>
        <div class="bait-card">
          <div class="bait-icon-row"><span class="bait-emoji">⚡</span><span class="bait-name">Buzzbait</span></div>
          <div class="bait-type">Topwater · Surface</div>
          <div class="bait-desc">Clouds give you a full-day topwater window that normally only lasts 30 minutes at dawn. Burn it along wood, grass edges, and dock shadows. Hesitate on the strike — wait until you feel the weight.</div>
          <div class="bait-meta"><span class="bm bm-color">Black / White</span><span class="bm bm-size">3/8–1/2 oz</span><span class="bm bm-depth">Surface</span><span class="bm bm-action">Fast</span></div>
        </div>
        <div class="bait-card">
          <div class="bait-icon-row"><span class="bait-emoji">🔔</span><span class="bait-name">Chatterbait</span></div>
          <div class="bait-type">Bladed Jig · Vibration</div>
          <div class="bait-desc">The hex blade creates a thumping, lateral wobble unlike anything else. Rig with a swimbait or craw trailer. Burn it fast through open water or slow-roll under docks in low light.</div>
          <div class="bait-meta"><span class="bm bm-color">Green Pumpkin / White</span><span class="bm bm-size">1/2 oz</span><span class="bm bm-depth">0–8 ft</span><span class="bm bm-action">Medium</span></div>
        </div>
        <div class="bait-card">
          <div class="bait-icon-row"><span class="bait-emoji">🪝</span><span class="bait-name">Dark Swim Jig</span></div>
          <div class="bait-type">Jig · Versatile</div>
          <div class="bait-desc">Black and blue skirt gives a massive, bold silhouette under overcast skies. Slow roll it just above bottom or through submerged grass. Add a chunk trailer for more bulk and displacement.</div>
          <div class="bait-meta"><span class="bm bm-color">Black/Blue</span><span class="bm bm-size">3/8–1/2 oz</span><span class="bm bm-depth">2–10 ft</span><span class="bm bm-action">Slow-Medium</span></div>
        </div>
        <div class="bait-card">
          <div class="bait-icon-row"><span class="bait-emoji">🐟</span><span class="bait-name">Big Swimbait</span></div>
          <div class="bait-type">Soft Plastic · Search</div>
          <div class="bait-desc">Cloudy days are prime time for a big paddle tail swimbait on a heavy swimbait hook. Bass are loose and willing to chase. 5–7" shad-pattern swimbaits on a 3/4 oz head are lethal in stained water.</div>
          <div class="bait-meta"><span class="bm bm-color">Shad / Bluegill</span><span class="bm bm-size">5–7"</span><span class="bm bm-depth">4–10 ft</span><span class="bm bm-action">Medium</span></div>
        </div>
        <div class="bait-card">
          <div class="bait-icon-row"><span class="bait-emoji">🎯</span><span class="bait-name">Popper</span></div>
          <div class="bait-type">Topwater · Surface</div>
          <div class="bait-desc">Under clouds, bass investigate the surface longer. Work a popper with sharp pops and 2–3 second pauses. Chug it near any visible structure — stumps, bridge pilings, lay-down trees.</div>
          <div class="bait-meta"><span class="bm bm-color">Bone / Chrome</span><span class="bm bm-size">1/2–3/4 oz</span><span class="bm bm-depth">Surface</span><span class="bm bm-action">Pop &amp; Pause</span></div>
        </div>
      </div>
    </div>
  </div>

  <!-- ░░ COLD WATER ░░ -->
  <div class="cond-section">
    <div class="cond-section-header">
      <span class="ci">🥶</span>
      <div><div class="cond-h-title">Cold Water</div><div class="cond-h-sub">Below 50°F · Slow down, go finesse</div></div>
    </div>
    <div class="cond-section-body">
      <div class="cond-tip-bar">💡 Bass metabolism slows drastically below 50°F. They won't chase. Put it on their nose and pause longer than you're comfortable with. 8–12 second pauses are not uncommon in January.</div>
      <div class="bait-grid">
        <div class="bait-card">
          <div class="bait-icon-row"><span class="bait-emoji">🪩</span><span class="bait-name">Ned Rig</span></div>
          <div class="bait-type">Finesse · Bottom</div>
          <div class="bait-desc">The ultimate cold-water finesse weapon. A 2.75"–3.5" EZ Craw or TRD mushroomed on a 1/8 oz jig head. Drag it with just your rod tip trembling — the bait stands up on bottom and drives them nuts.</div>
          <div class="bait-meta"><span class="bm bm-color">Green Pumpkin / Goby</span><span class="bm bm-size">2.75–3.5"</span><span class="bm bm-depth">6–20 ft</span><span class="bm bm-action">Dead Slow</span></div>
        </div>
        <div class="bait-card">
          <div class="bait-icon-row"><span class="bait-emoji">💀</span><span class="bait-name">Jerkbait</span></div>
          <div class="bait-type">Hard Bait · Suspending</div>
          <div class="bait-desc">A suspending jerkbait in cold water is the closest thing to cheating. Twitch-twitch-PAUSE. Let it hang motionless for 8–12 seconds. Bass will track it, then explode on it when it sits still. Use Megabass Vision 110 or Rapala Shadow Rap.</div>
          <div class="bait-meta"><span class="bm bm-color">Ghost Minnow / Chartreuse</span><span class="bm bm-size">4–5"</span><span class="bm bm-depth">3–8 ft</span><span class="bm bm-action">Twitch-Pause</span></div>
        </div>
        <div class="bait-card">
          <div class="bait-icon-row"><span class="bait-emoji">🥄</span><span class="bait-name">Blade Bait</span></div>
          <div class="bait-type">Metal · Vertical</div>
          <div class="bait-desc">The Silver Buddy, Heddon Sonar, and similar blade baits excel in vertical presentations. Drop straight down on main lake structure, lift 12–18 inches, let flutter back down. Deadly on deep fish holding near current.</div>
          <div class="bait-meta"><span class="bm bm-color">Silver / Chrome</span><span class="bm bm-size">1/2–3/4 oz</span><span class="bm bm-depth">10–30 ft</span><span class="bm bm-action">Vertical Jig</span></div>
        </div>
        <div class="bait-card">
          <div class="bait-icon-row"><span class="bait-emoji">🥄</span><span class="bait-name">Jigging Spoon</span></div>
          <div class="bait-type">Metal · Vertical</div>
          <div class="bait-desc">When bass are stacked on a point or hump in 20+ feet, a 3/4–1 oz jigging spoon fishes straight down through the school. Let it freefall on a slack line — the flutter on the drop is the strike trigger.</div>
          <div class="bait-meta"><span class="bm bm-color">Gold / Silver</span><span class="bm bm-size">3/4–1 oz</span><span class="bm bm-depth">15–40 ft</span><span class="bm bm-action">Vertical Drop</span></div>
        </div>
        <div class="bait-card">
          <div class="bait-icon-row"><span class="bait-emoji">🐛</span><span class="bait-name">Drop Shot Worm</span></div>
          <div class="bait-type">Finesse · Suspended</div>
          <div class="bait-desc">A 4" Robo Worm or Finesse worm on a drop shot holds the bait inches off the bottom right in the fish's face. Shake in place — barely move it. Perfect for cold-water fish hugging bottom structure on sonar.</div>
          <div class="bait-meta"><span class="bm bm-color">Aarons Magic / Morning Dawn</span><span class="bm bm-size">4"</span><span class="bm bm-depth">8–25 ft</span><span class="bm bm-action">Shake in Place</span></div>
        </div>
        <div class="bait-card">
          <div class="bait-icon-row"><span class="bait-emoji">🦐</span><span class="bait-name">Shaky Head</span></div>
          <div class="bait-type">Finesse · Bottom</div>
          <div class="bait-desc">A 5" straight worm on a 1/8 oz shaky head jig. Drag it painfully slow with occasional quivers. The tail vibrates on bottom with the slightest movement. Highly effective on pressured, cold fish.</div>
          <div class="bait-meta"><span class="bm bm-color">Green Pumpkin / Black</span><span class="bm bm-size">5–6"</span><span class="bm bm-depth">5–18 ft</span><span class="bm bm-action">Ultra Slow Drag</span></div>
        </div>
        <div class="bait-card">
          <div class="bait-icon-row"><span class="bait-emoji">🐚</span><span class="bait-name">Football Jig</span></div>
          <div class="bait-type">Jig · Bottom</div>
          <div class="bait-desc">A 3/4 oz football jig crawled slowly across rocky bottom in cold water mimics a dying crawfish — irresistible. Use a craw trailer and let it sit for 10+ seconds after every lift. Target 15–25 ft ledges.</div>
          <div class="bait-meta"><span class="bm bm-color">Brown/Orange / Black Blue</span><span class="bm bm-size">3/4 oz</span><span class="bm bm-depth">12–25 ft</span><span class="bm bm-action">Crawl &amp; Pause</span></div>
        </div>
      </div>
    </div>
  </div>

  <!-- ░░ HOT SUMMER ░░ -->
  <div class="cond-section">
    <div class="cond-section-header">
      <span class="ci">🔥</span>
      <div><div class="cond-h-title">Hot Summer</div><div class="cond-h-sub">Above 80°F water · Fish deep, early, or at night</div></div>
    </div>
    <div class="cond-section-body">
      <div class="cond-tip-bar">💡 Be on the water at first light. The topwater bite lives and dies in the first 45 minutes. After that, follow the thermocline — bass stack on ledges and offshore humps 12–22 ft deep.</div>
      <div class="bait-grid">
        <div class="bait-card">
          <div class="bait-icon-row"><span class="bait-emoji">🐠</span><span class="bait-name">Deep Diving Crankbait</span></div>
          <div class="bait-type">Hard Bait · Offshore</div>
          <div class="bait-desc">A Strike King 6XD, Norman Deep Little N, or Rapala DT-16 reaching 16–20 ft is your primary summer tool. Deflect it off rocks, stumps, and ledge edges. When it bangs bottom and bounces sideways — that's the strike trigger.</div>
          <div class="bait-meta"><span class="bm bm-color">Blueback Herring / Chartreuse</span><span class="bm bm-size">2–3 oz</span><span class="bm bm-depth">14–22 ft</span><span class="bm bm-action">Steady Crank</span></div>
        </div>
        <div class="bait-card">
          <div class="bait-icon-row"><span class="bait-emoji">🎣</span><span class="bait-name">Carolina Rig</span></div>
          <div class="bait-type">Rig · Deep Bottom</div>
          <div class="bait-desc">A 1 oz bullet weight on 20 lb mono, 18-inch fluoro leader with a lizard or creature bait. The weight drags bottom while the bait floats up in the strike zone. Perfect for covering offshore structure — drag it, reel up slack, repeat.</div>
          <div class="bait-meta"><span class="bm bm-color">June Bug / Green Pumpkin</span><span class="bm bm-size">1 oz + 6" bait</span><span class="bm bm-depth">12–25 ft</span><span class="bm bm-action">Drag &amp; Hop</span></div>
        </div>
        <div class="bait-card">
          <div class="bait-icon-row"><span class="bait-emoji">📍</span><span class="bait-name">Drop Shot</span></div>
          <div class="bait-type">Finesse · Suspended</div>
          <div class="bait-desc">When bass are suspended 2–3 feet off the bottom on your sonar, a drop shot is the only bait that targets that exact depth zone. Keep the weight on the bottom and shake the bait in place. Deadly on spotted bass and smallmouth in summer heat.</div>
          <div class="bait-meta"><span class="bm bm-color">Aarons Magic / Watermelon</span><span class="bm bm-size">4–5"</span><span class="bm bm-depth">10–30 ft</span><span class="bm bm-action">Shake in Place</span></div>
        </div>
        <div class="bait-card">
          <div class="bait-icon-row"><span class="bait-emoji">🦶</span><span class="bait-name">Topwater Frog</span></div>
          <div class="bait-type">Topwater · Matted Grass</div>
          <div class="bait-desc">At first light in summer, punch a hollow-body frog across matted vegetation, lily pad fields, and scum lines. Walk it slowly. The strike is violent and often visible before you feel it. Wait a full beat before setting the hook hard.</div>
          <div class="bait-meta"><span class="bm bm-color">Black / Green Frog</span><span class="bm bm-size">1/2–3/4 oz</span><span class="bm bm-depth">Surface</span><span class="bm bm-action">Walk-the-Dog</span></div>
        </div>
        <div class="bait-card">
          <div class="bait-icon-row"><span class="bait-emoji">🌙</span><span class="bait-name">Night Crawler (8–10" Worm)</span></div>
          <div class="bait-type">Soft Plastic · Night</div>
          <div class="bait-desc">In summer, giant bass feed shallow at night when surface temps cool. A 10" black ribbon tail worm on a 3/0 offset hook, Texas rig, no weight — float it along the surface over grass mats after dark. Old school. Deadly.</div>
          <div class="bait-meta"><span class="bm bm-color">Black / Purple</span><span class="bm bm-size">8–10"</span><span class="bm bm-depth">Surface–2 ft</span><span class="bm bm-action">Slow Float</span></div>
        </div>
        <div class="bait-card">
          <div class="bait-icon-row"><span class="bait-emoji">⚽</span><span class="bait-name">Football Jig</span></div>
          <div class="bait-type">Jig · Deep Structure</div>
          <div class="bait-desc">On ledges and rocky offshore humps in 15–25 ft of water, a football jig is unmatched. Drag it across the bottom slowly, pausing on any irregularity. Use a Zoom Super Chunk trailer in hot weather — the big tail pushes water.</div>
          <div class="bait-meta"><span class="bm bm-color">Watermelon Red / Brown Orange</span><span class="bm bm-size">3/4–1 oz</span><span class="bm bm-depth">14–28 ft</span><span class="bm bm-action">Slow Drag</span></div>
        </div>
        <div class="bait-card">
          <div class="bait-icon-row"><span class="bait-emoji">🌊</span><span class="bait-name">Swimbait (Underspin)</span></div>
          <div class="bait-type">Swimbait · Mid-Depth</div>
          <div class="bait-desc">An underspin jig with a 3.8" Keitech Swing Impact FAT is a deadly mid-summer bait. The spinning blade flashes below the soft plastic body. Slow-roll it over offshore structure at 12–18 ft. Counted down to precise depths.</div>
          <div class="bait-meta"><span class="bm bm-color">Sexy Shad / Ayu</span><span class="bm bm-size">3.8–5"</span><span class="bm bm-depth">10–20 ft</span><span class="bm bm-action">Slow Roll</span></div>
        </div>
      </div>
    </div>
  </div>

  <!-- ░░ CLEAR WATER ░░ -->
  <div class="cond-section">
    <div class="cond-section-header">
      <span class="ci">💎</span>
      <div><div class="cond-h-title">Clear Water</div><div class="cond-h-sub">High visibility · Go natural, small, and stealthy</div></div>
    </div>
    <div class="cond-section-body">
      <div class="cond-tip-bar">💡 In clear water bass inspect everything. Downsize. Match natural forage colors. Switch to 8–10 lb fluorocarbon — it's nearly invisible and has no stretch for solid hooksets. Stay back from the fish and make long casts.</div>
      <div class="bait-grid">
        <div class="bait-card">
          <div class="bait-icon-row"><span class="bait-emoji">🐛</span><span class="bait-name">Wacky Rig Senko</span></div>
          <div class="bait-type">Soft Plastic · Natural Fall</div>
          <div class="bait-desc">A 5" Gary Yamamoto Senko hooked wacky-style through the middle falls with a side-to-side flap that is absolutely irresistible in clear water. Use an O-ring to hook through it — one bait can catch 20 fish. Weightless or with a 1/16 oz wacky weight.</div>
          <div class="bait-meta"><span class="bm bm-color">Watermelon / Green Pumpkin</span><span class="bm bm-size">5"</span><span class="bm bm-depth">2–15 ft</span><span class="bm bm-action">Natural Fall</span></div>
        </div>
        <div class="bait-card">
          <div class="bait-icon-row"><span class="bait-emoji">🦈</span><span class="bait-name">Keitech Swimbait</span></div>
          <div class="bait-type">Soft Plastic · Finesse</div>
          <div class="bait-desc">The Keitech Swing Impact FAT 3.3"–3.8" on a 3/16–1/4 oz round ball head is one of the deadliest clear-water baits ever made. The paddle tail creates lifelike vibration at any speed. Natural shad and baitfish colors only.</div>
          <div class="bait-meta"><span class="bm bm-color">Ayu / Sexy Shad / Smoke</span><span class="bm bm-size">3.3–3.8"</span><span class="bm bm-depth">4–18 ft</span><span class="bm bm-action">Slow Roll</span></div>
        </div>
        <div class="bait-card">
          <div class="bait-icon-row"><span class="bait-emoji">🔱</span><span class="bait-name">Drop Shot</span></div>
          <div class="bait-type">Finesse · Suspended</div>
          <div class="bait-desc">Drop shot is built for clear water. A finesse worm nose-hooked with the hook pointing up, 10–14" above the weight, shaken in place on 8 lb fluorocarbon. Invisible leader, natural presentation, and it stays in the strike zone indefinitely.</div>
          <div class="bait-meta"><span class="bm bm-color">Watermelon Seed / Aarons Magic</span><span class="bm bm-size">4–5"</span><span class="bm bm-depth">6–25 ft</span><span class="bm bm-action">Shake in Place</span></div>
        </div>
        <div class="bait-card">
          <div class="bait-icon-row"><span class="bait-emoji">🏄</span><span class="bait-name">Spy Bait / I-Swimmer</span></div>
          <div class="bait-type">Hard Bait · Glide</div>
          <div class="bait-desc">The Deps Oregle, Jackall I-Shad, or Lucky Craft Pointer spy bait is a clear-water specialist. Cast long, let it sink to depth, and reel slowly with zero rod movement. The twin blade props spin on the fall and retrieve — incredible for wary, line-shy fish.</div>
          <div class="bait-meta"><span class="bm bm-color">Ghost Minnow / Bone</span><span class="bm bm-size">2.5–3.5"</span><span class="bm bm-depth">4–15 ft</span><span class="bm bm-action">Steady Reel</span></div>
        </div>
        <div class="bait-card">
          <div class="bait-icon-row"><span class="bait-emoji">🎭</span><span class="bait-name">Glide Bait</span></div>
          <div class="bait-type">Hard Bait · Big Bait</div>
          <div class="bait-desc">In reservoirs with clear water and large forage (trout, big shad), a glide bait like the Megabass Magdraft or Deps Slide Swimmer triggers trophy largemouth and smallmouth. Slow sweeping rod pulls make the bait S-curve through the water column.</div>
          <div class="bait-meta"><span class="bm bm-color">Trout / Shad</span><span class="bm bm-size">6–8"</span><span class="bm bm-depth">4–15 ft</span><span class="bm bm-action">Glide &amp; Pause</span></div>
        </div>
        <div class="bait-card">
          <div class="bait-icon-row"><span class="bait-emoji">🐜</span><span class="bait-name">Tiny Tube Jig</span></div>
          <div class="bait-type">Soft Plastic · Finesse</div>
          <div class="bait-desc">A 3" tube jig on a 3/16 oz internal tube head is a clear-water classic, especially for smallmouth. Crawl it over rocks like a crawfish. The tentacles flutter on every pause. Strike King Bitsy Tube and Berkley Powerbait Tubes in goby or smoke colors.</div>
          <div class="bait-meta"><span class="bm bm-color">Smoke / Goby / Green Pumpkin</span><span class="bm bm-size">3"</span><span class="bm bm-depth">4–20 ft</span><span class="bm bm-action">Hop &amp; Crawl</span></div>
        </div>
      </div>
    </div>
  </div>

  <!-- ░░ MUDDY / STAINED ░░ -->
  <div class="cond-section">
    <div class="cond-section-header">
      <span class="ci">🟤</span>
      <div><div class="cond-h-title">Muddy / Stained Water</div><div class="cond-h-sub">Low visibility · Big profile, loud, and bright</div></div>
    </div>
    <div class="cond-section-body">
      <div class="cond-tip-bar">💡 Bass can't see more than 6 inches. They navigate by lateral line vibration and sound. Go big, go bright, go loud. Upsize everything — bait, hook, and line. Target current seams where clear and stained water meet.</div>
      <div class="bait-grid">
        <div class="bait-card">
          <div class="bait-icon-row"><span class="bait-emoji">💥</span><span class="bait-name">Lipless Rattletrap</span></div>
          <div class="bait-type">Hard Bait · Search</div>
          <div class="bait-desc">The Bill Lewis Rat-L-Trap is arguably the best lure ever made for muddy water. The BB rattles are loud enough to locate bass by sound alone. Chartreuse/orange or fire tiger finish. Burn it fast, rip it through grass, let it free-fall on slack line.</div>
          <div class="bait-meta"><span class="bm bm-color">Chartreuse/Orange / Fire Tiger</span><span class="bm bm-size">1/2–3/4 oz</span><span class="bm bm-depth">2–10 ft</span><span class="bm bm-action">Fast Burn</span></div>
        </div>
        <div class="bait-card">
          <div class="bait-icon-row"><span class="bait-emoji">🌀</span><span class="bait-name">Big Colorado Spinnerbait</span></div>
          <div class="bait-type">Vibration · Search</div>
          <div class="bait-desc">In muddy water, go to a single large Colorado blade — maximum thump and vibration. Chartreuse or white skirt with a 5" swimbait trailer. The blade's water displacement telegraphs the bait's location to bass 20+ feet away.</div>
          <div class="bait-meta"><span class="bm bm-color">Chartreuse / White</span><span class="bm bm-size">3/4–1 oz</span><span class="bm bm-depth">0–6 ft</span><span class="bm bm-action">Slow Roll</span></div>
        </div>
        <div class="bait-card">
          <div class="bait-icon-row"><span class="bait-emoji">🎪</span><span class="bait-name">Bright Crankbait</span></div>
          <div class="bait-type">Hard Bait · Reaction</div>
          <div class="bait-desc">A chartreuse/black-back squarebill crankbait is electric in 2–4 ft of muddy water. Bash it off wood, rocks, and riprap. The deflection pause triggers reaction bites. Strike King 1.5 and 2.5 squarebills are the gold standard.</div>
          <div class="bait-meta"><span class="bm bm-color">Chartreuse/Black / Fire Tiger</span><span class="bm bm-size">1/2 oz</span><span class="bm bm-depth">2–5 ft</span><span class="bm bm-action">Bang &amp; Deflect</span></div>
        </div>
        <div class="bait-card">
          <div class="bait-icon-row"><span class="bait-emoji">🪝</span><span class="bait-name">Black/Blue Jig</span></div>
          <div class="bait-type">Jig · Flipping</div>
          <div class="bait-desc">Black and blue creates the darkest, most visible silhouette in murky water — bass track it by outline and sound. Flip it tight to wood, stumps, and dock posts. Use a craw trailer and 20 lb fluorocarbon. You need a fast, powerful hookset in muddy water.</div>
          <div class="bait-meta"><span class="bm bm-color">Black/Blue</span><span class="bm bm-size">1/2–3/4 oz</span><span class="bm bm-depth">0–8 ft</span><span class="bm bm-action">Flip &amp; Drop</span></div>
        </div>
        <div class="bait-card">
          <div class="bait-icon-row"><span class="bait-emoji">🔊</span><span class="bait-name">Rattle Jig</span></div>
          <div class="bait-type">Jig · Sound</div>
          <div class="bait-desc">A jig with a built-in rattle chamber (Booyah Boo Jig, Strike King Denny Brauer Rattling Jig) is a stealthy way to add noise. Fish can home in on it from distance in zero visibility. Pop it off bottom to rattle, then let it fall again.</div>
          <div class="bait-meta"><span class="bm bm-color">Black Blue / Chartreuse</span><span class="bm bm-size">1/2 oz</span><span class="bm bm-depth">2–10 ft</span><span class="bm bm-action">Hop &amp; Drop</span></div>
        </div>
        <div class="bait-card">
          <div class="bait-icon-row"><span class="bait-emoji">🐍</span><span class="bait-name">Big Creature Bait (Flipping)</span></div>
          <div class="bait-type">Soft Plastic · Flipping</div>
          <div class="bait-desc">A 4" Zoom Brush Hog or Strike King Rage Craw on a 1 oz tungsten weight punches into flooded bushes and wood in muddy spring water. Bass hold tight to cover — your bait needs to land right in their face. Use heavy braid, no leader.</div>
          <div class="bait-meta"><span class="bm bm-color">Black Blue / Junebug</span><span class="bm bm-size">4"</span><span class="bm bm-depth">0–6 ft</span><span class="bm bm-action">Punch &amp; Drop</span></div>
        </div>
      </div>
    </div>
  </div>

  <!-- ░░ RAIN / STORM ░░ -->
  <div class="cond-section">
    <div class="cond-section-header">
      <span class="ci">🌧️</span>
      <div><div class="cond-h-title">Rain &amp; Pre-Storm</div><div class="cond-h-sub">Barometric drop · Feeding frenzy window</div></div>
    </div>
    <div class="cond-section-body">
      <div class="cond-tip-bar">💡 The 2 hours before a cold front is the single most productive bass-fishing window. Falling barometric pressure triggers a feeding frenzy. After the front passes and pressure rises, fishing slows dramatically for 24–48 hours.</div>
      <div class="bait-grid">
        <div class="bait-card">
          <div class="bait-icon-row"><span class="bait-emoji">🐸</span><span class="bait-name">Topwater Frog</span></div>
          <div class="bait-type">Topwater · Surface</div>
          <div class="bait-desc">Rain creates thousands of tiny dimples on the surface that confuse bass about where exactly your frog is. Walk it slowly across grass, slop, and open pockets. The bite is violent — rain often makes bass throw caution to the wind entirely.</div>
          <div class="bait-meta"><span class="bm bm-color">Black / Leopard Frog</span><span class="bm bm-size">1/2 oz</span><span class="bm bm-depth">Surface</span><span class="bm bm-action">Walk &amp; Pause</span></div>
        </div>
        <div class="bait-card">
          <div class="bait-icon-row"><span class="bait-emoji">⚡</span><span class="bait-name">Buzzbait</span></div>
          <div class="bait-type">Topwater · Surface</div>
          <div class="bait-desc">Wind and rain chop mask the buzzbait's approach. Bass hear the gurgling blade before they see it. Burn it along the bank just before the storm. This is the best window all year for a big buzzbait bite — don't hesitate.</div>
          <div class="bait-meta"><span class="bm bm-color">White / Black</span><span class="bm bm-size">1/2 oz</span><span class="bm bm-depth">Surface</span><span class="bm bm-action">Fast</span></div>
        </div>
        <div class="bait-card">
          <div class="bait-icon-row"><span class="bait-emoji">🔔</span><span class="bait-name">Chatterbait</span></div>
          <div class="bait-type">Bladed Jig · Search</div>
          <div class="bait-desc">During and after rain, baitfish wash into shallow areas near drain pipes, creek mouths, and culverts. A white chatterbait burned through these zones intercepts feeding bass. Add a white paddle tail trailer. This is an aggressive, fast presentation.</div>
          <div class="bait-meta"><span class="bm bm-color">White / Chartreuse</span><span class="bm bm-size">1/2 oz</span><span class="bm bm-depth">0–5 ft</span><span class="bm bm-action">Fast Burn</span></div>
        </div>
        <div class="bait-card">
          <div class="bait-icon-row"><span class="bait-emoji">🪝</span><span class="bait-name">Flipping Jig</span></div>
          <div class="bait-type">Jig · Shallow Cover</div>
          <div class="bait-desc">Right before a front, bass push under the thickest overhead cover they can find — flooded bushes, dock edges, grass mats. A heavy flipping jig punched under this cover with a craw trailer puts it exactly where the fish are hiding.</div>
          <div class="bait-meta"><span class="bm bm-color">Black Blue / Pumpkin</span><span class="bm bm-size">3/4–1 oz</span><span class="bm bm-depth">0–4 ft</span><span class="bm bm-action">Flip &amp; Drop</span></div>
        </div>
        <div class="bait-card">
          <div class="bait-icon-row"><span class="bait-emoji">🌀</span><span class="bait-name">Big Spinnerbait</span></div>
          <div class="bait-type">Vibration · Bank</div>
          <div class="bait-desc">A 3/4 oz double willow spinnerbait bombed along the bank during rain is a classic storm pattern. Chartreuse blades flash through the surface chop. Cover water fast — bass are scattered and aggressive. Every 20 feet could hold a fish.</div>
          <div class="bait-meta"><span class="bm bm-color">Chartreuse/White</span><span class="bm bm-size">3/4 oz</span><span class="bm bm-depth">0–6 ft</span><span class="bm bm-action">Fast Burn</span></div>
        </div>
        <div class="bait-card">
          <div class="bait-icon-row"><span class="bait-emoji">🔴</span><span class="bait-name">Red Craw Squarebill</span></div>
          <div class="bait-type">Crankbait · Shallow</div>
          <div class="bait-desc">After rain, crawfish become highly active in shallow water — a red or red/orange squarebill crankbait triggers some of the most explosive bites of the year. Bash it off wood and riprap in 1–4 ft. The red coloration mimics a fleeing crawfish perfectly.</div>
          <div class="bait-meta"><span class="bm bm-color">Red Craw / Crawdad</span><span class="bm bm-size">1/2 oz</span><span class="bm bm-depth">1–4 ft</span><span class="bm bm-action">Bang &amp; Deflect</span></div>
        </div>
      </div>
    </div>
  </div>

  <!-- ░░ SUNNY / BRIGHT ░░ -->
  <div class="cond-section">
    <div class="cond-section-header">
      <span class="ci">☀️</span>
      <div><div class="cond-h-title">Bright Bluebird Day</div><div class="cond-h-sub">High pressure · Bass lock into shade &amp; structure</div></div>
    </div>
    <div class="cond-section-body">
      <div class="cond-tip-bar">💡 A bluebird sky is the toughest bass fishing condition. Every bass in the lake is under something. Fish the shade — dock shadows, grass edges, tree overhangs, bridge pilings. Slow down and be precise rather than covering water.</div>
      <div class="bait-grid">
        <div class="bait-card">
          <div class="bait-icon-row"><span class="bait-emoji">🌵</span><span class="bait-name">Texas Rig Creature Bait</span></div>
          <div class="bait-type">Soft Plastic · Flipping</div>
          <div class="bait-desc">On sunny days, flip a Texas rig into every shady spot you can find — dock walkways, between pontoon pontoons, under overhanging branches. A Zoom Brush Hog or Rage Craw in 1/2 oz tungsten weight. Put it in the shade; wait for the thump.</div>
          <div class="bait-meta"><span class="bm bm-color">Green Pumpkin / Black Blue</span><span class="bm bm-size">4"</span><span class="bm bm-depth">0–8 ft</span><span class="bm bm-action">Flip &amp; Drop</span></div>
        </div>
        <div class="bait-card">
          <div class="bait-icon-row"><span class="bait-emoji">🦐</span><span class="bait-name">Shaky Head</span></div>
          <div class="bait-type">Finesse · Structure</div>
          <div class="bait-desc">A finesse shaky head fished painfully slow in the shade of a dock or bridge pillar is a go-to on high-pressure bluebird days. The bait stands vertically on the hook, tail quivering. Drag it 6 inches, pause 10 seconds. Repeat.</div>
          <div class="bait-meta"><span class="bm bm-color">Green Pumpkin / Black</span><span class="bm bm-size">5–7"</span><span class="bm bm-depth">4–15 ft</span><span class="bm bm-action">Ultra Slow Drag</span></div>
        </div>
        <div class="bait-card">
          <div class="bait-icon-row"><span class="bait-emoji">🎯</span><span class="bait-name">Mid-Depth Crankbait</span></div>
          <div class="bait-type">Hard Bait · Structure</div>
          <div class="bait-desc">On sunny days bass slide off shallow flats into shaded channel edges at 6–12 ft. A Strike King 5XD or similar mid-depth crankbait worked along the break line hits them where they live. Use a pause-and-go retrieve rather than straight cranking.</div>
          <div class="bait-meta"><span class="bm bm-color">Sexy Shad / Blueback</span><span class="bm bm-size">3/4 oz</span><span class="bm bm-depth">8–14 ft</span><span class="bm bm-action">Pause &amp; Go</span></div>
        </div>
        <div class="bait-card">
          <div class="bait-icon-row"><span class="bait-emoji">🧱</span><span class="bait-name">Punch Rig</span></div>
          <div class="bait-type">Soft Plastic · Vegetation</div>
          <div class="bait-desc">When bass bury under matted vegetation to escape the sun, punch through with a 1.5–2 oz tungsten weight and a compact craw bait on a heavy flipping hook. 65 lb braid is mandatory. The bait must punch through the mat cleanly and sink fast.</div>
          <div class="bait-meta"><span class="bm bm-color">Black Blue / Watermelon</span><span class="bm bm-size">1.5–2 oz punch</span><span class="bm bm-depth">Under mat</span><span class="bm bm-action">Drop &amp; Shake</span></div>
        </div>
        <div class="bait-card">
          <div class="bait-icon-row"><span class="bait-emoji">🪝</span><span class="bait-name">Dock Skipping Jig</span></div>
          <div class="bait-type">Jig · Skipping</div>
          <div class="bait-desc">The best bass on sunny days are deep under floating docks — places no one else can reach. A flat-sided 3/8 oz finesse jig skipped 15–20 ft back under the dock puts your bait right on their nose. Takes practice but the payoff is huge.</div>
          <div class="bait-meta"><span class="bm bm-color">Green Pumpkin / Smoke</span><span class="bm bm-size">3/8 oz</span><span class="bm bm-depth">0–5 ft (under dock)</span><span class="bm bm-action">Skip &amp; Drag</span></div>
        </div>
        <div class="bait-card">
          <div class="bait-icon-row"><span class="bait-emoji">🐜</span><span class="bait-name">Ned Rig</span></div>
          <div class="bait-type">Finesse · Bottom</div>
          <div class="bait-desc">When all else fails on a tough sunny day, a Ned rig will catch fish. Its tiny profile and subtle action works on bass that have lockjaw. Cast it to the shaded edge of any structure and don't move it. The tail wiggles on its own — let it do the work.</div>
          <div class="bait-meta"><span class="bm bm-color">Green Pumpkin / Goby</span><span class="bm bm-size">3"</span><span class="bm bm-depth">4–20 ft</span><span class="bm bm-action">Minimal Movement</span></div>
        </div>
      </div>
    </div>
  </div>

  <!-- ░░ SPRING SPAWN ░░ -->
  <div class="cond-section">
    <div class="cond-section-header">
      <span class="ci">🌸</span>
      <div><div class="cond-h-title">Spring / Spawn Season</div><div class="cond-h-sub">55–68°F water · Shallow flats &amp; bedding areas</div></div>
    </div>
    <div class="cond-section-body">
      <div class="cond-tip-bar">💡 Spring fishing has three phases: pre-spawn (aggressive feeding), spawn (territorial, defensive), and post-spawn (recovery). The biggest females of the year are caught in pre-spawn — they're gorging before they go to the bed.</div>
      <div class="bait-grid">
        <div class="bait-card">
          <div class="bait-icon-row"><span class="bait-emoji">🦎</span><span class="bait-name">Soft Plastic Lizard</span></div>
          <div class="bait-type">Soft Plastic · Spawn Trigger</div>
          <div class="bait-desc">The classic spawn bait. Bass absolutely cannot tolerate a lizard near their bed — it represents a nest predator eating their eggs. Texas rig weightless and twitch it over visible beds. You'll see the bass attack it before you feel the bite. Wait for it to take it deep.</div>
          <div class="bait-meta"><span class="bm bm-color">June Bug / Green Pumpkin / Watermelon Red</span><span class="bm bm-size">6"</span><span class="bm bm-depth">1–4 ft</span><span class="bm bm-action">Twitch &amp; Pause</span></div>
        </div>
        <div class="bait-card">
          <div class="bait-icon-row"><span class="bait-emoji">🏃</span><span class="bait-name">Squarebill Crankbait</span></div>
          <div class="bait-type">Hard Bait · Reaction</div>
          <div class="bait-desc">The pre-spawn crankbait bite is one of the year's best. Squarebills deflect off stumps, rocks, and laydowns on shallow spawning flats in 2–5 ft. The erratic action triggers reaction strikes from pre-spawn females stacking up to move shallow.</div>
          <div class="bait-meta"><span class="bm bm-color">Red Craw / Chartreuse Shad</span><span class="bm bm-size">1/2 oz</span><span class="bm bm-depth">2–5 ft</span><span class="bm bm-action">Bang &amp; Deflect</span></div>
        </div>
        <div class="bait-card">
          <div class="bait-icon-row"><span class="bait-emoji">💥</span><span class="bait-name">Lipless Crankbait</span></div>
          <div class="bait-type">Hard Bait · Grass</div>
          <div class="bait-desc">In early spring when new grass is emerging in 2–4 ft, ripping a Rat-L-Trap through the tops is one of the most explosive patterns in all of bass fishing. Let it settle into the grass, then rip upward. The bait pops free and triggers a vicious reaction bite.</div>
          <div class="bait-meta"><span class="bm bm-color">Red/Chrome / Chartreuse</span><span class="bm bm-size">1/2 oz</span><span class="bm bm-depth">2–5 ft</span><span class="bm bm-action">Rip &amp; Kill</span></div>
        </div>
        <div class="bait-card">
          <div class="bait-icon-row"><span class="bait-emoji">🔔</span><span class="bait-name">Chatterbait + Swimbait</span></div>
          <div class="bait-type">Bladed Jig · Covering Water</div>
          <div class="bait-desc">In pre-spawn, bass have moved up but can be anywhere across a flat. A chatterbait with a swimbait trailer lets you cover 300 yards of bank in minutes. When you get a bite, slow down with a follow-up bait. Keitech 3.8 or Strike King Rage Swimmer trailer.</div>
          <div class="bait-meta"><span class="bm bm-color">White / Green Pumpkin</span><span class="bm bm-size">1/2 oz</span><span class="bm bm-depth">2–6 ft</span><span class="bm bm-action">Medium-Fast</span></div>
        </div>
        <div class="bait-card">
          <div class="bait-icon-row"><span class="bait-emoji">🎣</span><span class="bait-name">Suspending Jerkbait</span></div>
          <div class="bait-type">Hard Bait · Pre-Spawn Cold</div>
          <div class="bait-desc">Cold fronts in early spring push bass off shallow flats temporarily. A suspending jerkbait in 4–8 ft of water, worked with long pauses, targets those fish suspended in the water column on their way to the shallows. Key bait for 50–55°F transitions.</div>
          <div class="bait-meta"><span class="bm bm-color">Ghost Minnow / Pearl</span><span class="bm bm-size">4–5"</span><span class="bm bm-depth">4–8 ft</span><span class="bm bm-action">Twitch-Twitch-Pause</span></div>
        </div>
        <div class="bait-card">
          <div class="bait-icon-row"><span class="bait-emoji">🐸</span><span class="bait-name">Bed Frog / Swimbait</span></div>
          <div class="bait-type">Soft Plastic · Sight Fishing</div>
          <div class="bait-desc">A 4–5" full-body swimbait like a Berkley Powerbait MaxScent or a small paddle tail imitating a bluegill fry sight-fished over a visible bed is deadly for big females. Cast past the bed, swim it in slowly. The female will charge and engulf it defensively.</div>
          <div class="bait-meta"><span class="bm bm-color">Bluegill / Natural Shad</span><span class="bm bm-size">4–5"</span><span class="bm bm-depth">1–3 ft</span><span class="bm bm-action">Slow Swim</span></div>
        </div>
        <div class="bait-card">
          <div class="bait-icon-row"><span class="bait-emoji">🐝</span><span class="bait-name">Ned Rig / Finesse Craw</span></div>
          <div class="bait-type">Finesse · Post-Spawn</div>
          <div class="bait-desc">Post-spawn females are lethargic and recovering — they won't chase. A Ned rig or small finesse craw on a mushroom head fished directly on the bed or near the spawning area is the best way to target these recovering giants. Patience is everything.</div>
          <div class="bait-meta"><span class="bm bm-color">Watermelon / Green Pumpkin</span><span class="bm bm-size">2.75–3"</span><span class="bm bm-depth">1–5 ft</span><span class="bm bm-action">Dead Stick</span></div>
        </div>
      </div>
    </div>
  </div>

  <!-- ░░ FALL ░░ -->
  <div class="cond-section">
    <div class="cond-section-header">
      <span class="ci">🍂</span>
      <div><div class="cond-h-title">Fall Turnover &amp; Autumn Feed</div><div class="cond-h-sub">Cooling water · Bass chase shad into the shallows</div></div>
    </div>
    <div class="cond-section-body">
      <div class="cond-tip-bar">💡 Fall is the most exciting bass fishing of the year. Cooling water pulls bass shallow to feed on shad and bream. They chase bait aggressively in packs — find the bait, find the fish. Cover water fast with reaction baits before the lake turns over.</div>
      <div class="bait-grid">
        <div class="bait-card">
          <div class="bait-icon-row"><span class="bait-emoji">💥</span><span class="bait-name">Lipless Rattletrap</span></div>
          <div class="bait-type">Hard Bait · Shad Imitation</div>
          <div class="bait-desc">Fall and a Rat-L-Trap go together like peanut butter and jelly. Shad are everywhere and bass are herding them. A 1/2 oz chrome/blue Rat-L-Trap ripped through shad schools on main lake points is one of the most thrilling bites in bass fishing.</div>
          <div class="bait-meta"><span class="bm bm-color">Chrome Blue / Tennessee Shad</span><span class="bm bm-size">1/2 oz</span><span class="bm bm-depth">2–12 ft</span><span class="bm bm-action">Fast Burn / Rip</span></div>
        </div>
        <div class="bait-card">
          <div class="bait-icon-row"><span class="bait-emoji">🎤</span><span class="bait-name">Walking Topwater (Spook)</span></div>
          <div class="bait-type">Topwater · Walk-the-Dog</div>
          <div class="bait-desc">When bass are busting shad on the surface in fall, a Heddon Zara Spook walked through the melee is electric. Twitch-twitch rhythm side to side. Cast into the boil, walk it out — bass will swirl under it, miss it, and attack again. Best morning bite of the year.</div>
          <div class="bait-meta"><span class="bm bm-color">Bone / Chrome Shad</span><span class="bm bm-size">3/4 oz</span><span class="bm bm-depth">Surface</span><span class="bm bm-action">Walk-the-Dog</span></div>
        </div>
        <div class="bait-card">
          <div class="bait-icon-row"><span class="bait-emoji">🌀</span><span class="bait-name">White Spinnerbait</span></div>
          <div class="bait-type">Vibration · Search</div>
          <div class="bait-desc">A white double-willow spinnerbait burned through creek arms and pockets loaded with shad matches the hatch perfectly. Willow blades flash like scales. Fish it fast, just under the surface so bass can see it from above. Add a white shad trailer for bulk.</div>
          <div class="bait-meta"><span class="bm bm-color">White / Silver</span><span class="bm bm-size">1/2–3/4 oz</span><span class="bm bm-depth">0–6 ft</span><span class="bm bm-action">Fast Burn</span></div>
        </div>
        <div class="bait-card">
          <div class="bait-icon-row"><span class="bait-emoji">🏃</span><span class="bait-name">Squarebill Crankbait</span></div>
          <div class="bait-type">Hard Bait · Shallow</div>
          <div class="bait-desc">As water temps drop into the low 60s, bass move shallow and squarebills smash through banks. Bash it off riprap, seawalls, dock posts, and laydowns. Shad or natural color patterns mirror the baitfish that bass are pushing to the banks daily.</div>
          <div class="bait-meta"><span class="bm bm-color">Sexy Shad / Citrus Shad</span><span class="bm bm-size">1/2 oz</span><span class="bm bm-depth">1–4 ft</span><span class="bm bm-action">Medium-Fast</span></div>
        </div>
        <div class="bait-card">
          <div class="bait-icon-row"><span class="bait-emoji">🐟</span><span class="bait-name">Big Shad Swimbait</span></div>
          <div class="bait-type">Swimbait · Match the Hatch</div>
          <div class="bait-desc">In fall when shad are 4–5" long, a matching swimbait on a 1/2 oz swimbait jig head or flutter spoon is unbeatable. Cast into schools of visible baitfish and swim through at the same pace as the natural bait. Oversized bass follow shad schools all fall.</div>
          <div class="bait-meta"><span class="bm bm-color">Pearl / Shad</span><span class="bm bm-size">4–5"</span><span class="bm bm-depth">4–12 ft</span><span class="bm bm-action">Steady Swim</span></div>
        </div>
        <div class="bait-card">
          <div class="bait-icon-row"><span class="bait-emoji">🎪</span><span class="bait-name">Jerkbait (Fall Transition)</span></div>
          <div class="bait-type">Hard Bait · Suspending</div>
          <div class="bait-desc">As water temperatures cool below 60°F in late fall, a suspending jerkbait becomes a primary pattern. Bass are transitioning from summer depth to winter patterns. Work it with quick twitches and shorter pauses than in winter — 2–4 second pauses.</div>
          <div class="bait-meta"><span class="bm bm-color">Ghost Shad / Chartreuse Shad</span><span class="bm bm-size">4–5"</span><span class="bm bm-depth">3–8 ft</span><span class="bm bm-action">Twitch-Pause</span></div>
        </div>
      </div>
    </div>
  </div>

  <div class="ornament">— ✦ ✦ ✦ —</div>
  <div class="h3-sec">Master Quick Reference</div>
  <div class="ref-wrap">
    <table class="ref-table">
      <thead><tr><th>Condition</th><th>#1 Pick</th><th>Color</th><th>Depth</th><th>Speed</th></tr></thead>
      <tbody>
        <tr><td>☁️ Cloudy</td><td><b>Spinnerbait</b></td><td>White/Chartreuse</td><td>0–6 ft</td><td>Medium-Fast</td></tr>
        <tr><td>🥶 Cold Water</td><td><b>Ned Rig</b></td><td>Green Pumpkin</td><td>8–20 ft</td><td>Dead Slow</td></tr>
        <tr><td>🔥 Hot Summer</td><td><b>Deep Crankbait</b></td><td>Blueback Herring</td><td>14–22 ft</td><td>Medium</td></tr>
        <tr><td>💎 Clear Water</td><td><b>Wacky Senko</b></td><td>Watermelon</td><td>2–12 ft</td><td>Natural Fall</td></tr>
        <tr><td>🟤 Muddy Water</td><td><b>Rattletrap</b></td><td>Chartreuse/Orange</td><td>2–8 ft</td><td>Fast Burn</td></tr>
        <tr><td>🌧️ Rain/Storm</td><td><b>Chatterbait</b></td><td>White/Green</td><td>0–4 ft</td><td>Fast</td></tr>
        <tr><td>☀️ Sunny</td><td><b>Texas Rig</b></td><td>Black/Blue</td><td>Shade/Structure</td><td>Slow</td></tr>
        <tr><td>🌸 Spring Spawn</td><td><b>Plastic Lizard</b></td><td>June Bug/Red</td><td>1–4 ft</td><td>Twitch &amp; Pause</td></tr>
        <tr><td>🍂 Fall</td><td><b>Lipless Rattletrap</b></td><td>Chrome/Blue</td><td>2–12 ft</td><td>Fast Rip</td></tr>
      </tbody>
    </table>
  </div>

</div><!-- /tab-lures -->


<!-- ═══════════════════════════════════════════
     TAB 2 — CLIMATE GUIDE
═══════════════════════════════════════════ -->
<div id="tab-climate" class="tab-panel">
  <div class="sec-title">Bass Fishing by <em>Climate &amp; Region</em></div>
  <p class="sec-lead">Where you fish shapes everything — water temps, forage, cover types, and seasonal timing vary wildly by geography. Know your region, own your water.</p>

  <div class="climate-grid">

    <div class="climate-card">
      <div class="climate-hdr"><h3>Southern Reservoirs</h3><div class="climate-region">🌡️ Tennessee · Alabama · Texas · Mississippi</div></div>
      <div class="climate-body">
        <p>Long hot summers drive bass deep onto offshore structure for months. Spring spawn arrives early (Feb–Mar). Short mild winters mean fish stay active year-round. Ledge fishing in June–August is world-class.</p>
        <div class="season-block">
          <div class="season-title">Pre-Spawn / Spring (Feb–Apr)</div>
          <ul class="season-baits">
            <li><strong>Squarebill Crankbait</strong> — deflect off stumps on spawning flats</li>
            <li><strong>Lipless Crankbait</strong> — rip through emerging grass in 2–4 ft</li>
            <li><strong>Chatterbait</strong> — cover water on pre-spawn flats fast</li>
            <li><strong>Jerkbait</strong> — during cold fronts in 50–55°F water</li>
          </ul>
        </div>
        <div class="season-block">
          <div class="season-title">Summer (May–Sep)</div>
          <ul class="season-baits">
            <li><strong>Football Jig</strong> — ledges, 15–28 ft, drag slow</li>
            <li><strong>Deep Diving Crankbait (6XD)</strong> — offshore humps and ledges</li>
            <li><strong>Drop Shot</strong> — suspended fish on sonar, 10–25 ft</li>
            <li><strong>Carolina Rig</strong> — secondary points and offshore ridges</li>
            <li><strong>Swimbait (Underspin)</strong> — slow-roll at thermocline depth</li>
          </ul>
        </div>
        <div class="season-block">
          <div class="season-title">Fall (Oct–Nov)</div>
          <ul class="season-baits">
            <li><strong>Lipless Rattletrap</strong> — shad schools in creek arms</li>
            <li><strong>Spinnerbait</strong> — white, burn along the bank</li>
            <li><strong>Walking Topwater</strong> — morning surface busts</li>
          </ul>
        </div>
        <div class="season-block">
          <div class="season-title">Winter (Dec–Jan)</div>
          <ul class="season-baits">
            <li><strong>Jerkbait</strong> — suspend on main lake points</li>
            <li><strong>Ned Rig</strong> — finesse on rocky bottom</li>
            <li><strong>Blade Bait</strong> — vertical jigging over deep structure</li>
          </ul>
        </div>
      </div>
    </div>

    <div class="climate-card">
      <div class="climate-hdr"><h3>Mountain Streams &amp; Rivers</h3><div class="climate-region">🏔️ Appalachians · Ozarks · Rockies</div></div>
      <div class="climate-body">
        <p>Smallmouth bass dominate cold, clear, rocky streams. Current seams, eddies, and deep pools are prime real estate. Forage is primarily crawfish, hellgrammites, and minnows. Wading in summer is extraordinary.</p>
        <div class="season-block">
          <div class="season-title">Spring (Mar–May)</div>
          <ul class="season-baits">
            <li><strong>Crawfish Crankbait</strong> — deflect off rocks in riffles</li>
            <li><strong>Tube Jig</strong> — crawl over rocky bottom, crawfish imitation</li>
            <li><strong>Ned Rig</strong> — eddy pockets behind large boulders</li>
            <li><strong>Inline Spinner (Mepps)</strong> — swing downstream through current</li>
          </ul>
        </div>
        <div class="season-block">
          <div class="season-title">Summer (Jun–Aug)</div>
          <ul class="season-baits">
            <li><strong>Topwater Popper</strong> — slicks below rapids in low light</li>
            <li><strong>Small Crankbait (DR Flat)</strong> — below drops and ledges</li>
            <li><strong>Grub Jig</strong> — smoke curly tail, 1/4 oz, current seams</li>
            <li><strong>Drop Shot</strong> — deep pools, 10–20 ft in summer heat</li>
            <li><strong>Soft Jerkbait</strong> — Super Fluke in slow pools</li>
          </ul>
        </div>
        <div class="season-block">
          <div class="season-title">Fall / Winter</div>
          <ul class="season-baits">
            <li><strong>Brown Tube Jig</strong> — crawfish pattern, deep pools</li>
            <li><strong>Blade Bait</strong> — vertical in the deepest holes</li>
            <li><strong>Football Jig</strong> — crawl rocky flats, very slow</li>
          </ul>
        </div>
      </div>
    </div>

    <div class="climate-card">
      <div class="climate-hdr"><h3>Great Lakes &amp; Northern Lakes</h3><div class="climate-region">🧊 Michigan · Wisconsin · Minnesota · Ontario</div></div>
      <div class="climate-body">
        <p>Short, intense fishing windows define the north. The spawn happens 6–8 weeks later than the south. Smallmouth dominate and can exceed 7 lbs. Ice-out in April triggers some of the most aggressive shallow feeding of the year.</p>
        <div class="season-block">
          <div class="season-title">Ice-Out / Early Spring (Apr–May)</div>
          <ul class="season-baits">
            <li><strong>Jerkbait</strong> — dark, natural colors in 46–52°F water</li>
            <li><strong>Finesse Jig (1/4 oz)</strong> — rocky shallow points, slow</li>
            <li><strong>Tube Bait (3")</strong> — rock piles and gravel, crawl slow</li>
            <li><strong>Drop Shot</strong> — first sunny shorelines that warm early</li>
          </ul>
        </div>
        <div class="season-block">
          <div class="season-title">Late Spring / Spawn (Jun)</div>
          <ul class="season-baits">
            <li><strong>Soft Plastic Lizard</strong> — sight fishing spawning bass</li>
            <li><strong>Ned Rig</strong> — post-spawn recovery on beds</li>
            <li><strong>Swimbait on shaky head</strong> — cruise lanes near nests</li>
          </ul>
        </div>
        <div class="season-block">
          <div class="season-title">Summer (Jul–Aug)</div>
          <ul class="season-baits">
            <li><strong>Topwater Walker</strong> — incredible dawn bite on flats</li>
            <li><strong>Big Ned Rig / Tube</strong> — rocky points, 8–18 ft</li>
            <li><strong>Swimbait (Keitech)</strong> — suspended over rock humps</li>
            <li><strong>Drop Shot</strong> — deep clear structure, 15–30 ft</li>
          </ul>
        </div>
        <div class="season-block">
          <div class="season-title">Fall Turnover (Sep–Oct)</div>
          <ul class="season-baits">
            <li><strong>Lipless Crank</strong> — shad schools, aggressive burn</li>
            <li><strong>Big Crankbait</strong> — main lake points transitioning deep</li>
            <li><strong>Spinnerbait</strong> — bank feeding frenzies</li>
          </ul>
        </div>
      </div>
    </div>

    <div class="climate-card">
      <div class="climate-hdr"><h3>Florida &amp; Coastal Lowlands</h3><div class="climate-region">🌴 Florida · Louisiana · Georgia · Carolinas</div></div>
      <div class="climate-body">
        <p>Home of the Florida-strain largemouth — the largest bass in the world, capable of exceeding 20 lbs. Shallow, weedy, warm lakes year-round. Vegetation is the entire game here — learn to fish grass or you won't catch fish.</p>
        <div class="season-block">
          <div class="season-title">Winter Spawn (Dec–Feb)</div>
          <ul class="season-baits">
            <li><strong>Plastic Lizard</strong> — spawn trigger on beds, sight fish</li>
            <li><strong>Shaky Head</strong> — slow drag near beds post-front</li>
            <li><strong>Wacky Senko (5")</strong> — weightless over sand/shell beds</li>
            <li><strong>Swimjig</strong> — slow roll along edge of grass during spawn</li>
          </ul>
        </div>
        <div class="season-block">
          <div class="season-title">Spring / Early Summer (Mar–Jun)</div>
          <ul class="season-baits">
            <li><strong>Hollow Body Frog</strong> — walk over hydrilla, pepper grass, and matted salvia</li>
            <li><strong>Punch Rig</strong> — 2 oz tungsten through thick mats</li>
            <li><strong>Swim Jig</strong> — slow roll along grass walls</li>
            <li><strong>Topwater Spook</strong> — walk along edge of grass at dawn</li>
          </ul>
        </div>
        <div class="season-block">
          <div class="season-title">Hot Summer (Jul–Sep)</div>
          <ul class="season-baits">
            <li><strong>Punch Rig</strong> — fish are under the mat all day</li>
            <li><strong>Big Worm (10")</strong> — night fishing vegetation edges</li>
            <li><strong>Swimjig + paddle trailer</strong> — inside edges of grass in current</li>
          </ul>
        </div>
        <div class="season-block">
          <div class="season-title">Fall / Rainy Season (Oct–Nov)</div>
          <ul class="season-baits">
            <li><strong>Spinnerbait</strong> — white, through flooded brush after rains</li>
            <li><strong>Lipless Crank</strong> — rip through dying grass edges</li>
            <li><strong>Squarebill</strong> — blow-downs and cypress trees</li>
          </ul>
        </div>
      </div>
    </div>

    <div class="climate-card">
      <div class="climate-hdr"><h3>Midwest Farm Ponds</h3><div class="climate-region">🌽 Ohio · Indiana · Iowa · Missouri · Illinois</div></div>
      <div class="climate-body">
        <p>Small farm ponds hold enormous bass with almost zero fishing pressure. Bluegill and crawfish are the primary forage. Bank fishing often outproduces a boat. A simple rod and reel can catch the biggest bass of your life here.</p>
        <div class="season-block">
          <div class="season-title">Spring (Apr–May)</div>
          <ul class="season-baits">
            <li><strong>Rebel Crawdad</strong> — bang off dam faces and rocky banks</li>
            <li><strong>Inline Spinner (Roostertail)</strong> — fan cast the entire pond</li>
            <li><strong>Wacky Senko</strong> — pitch to visible beds along the banks</li>
            <li><strong>Topwater Frog / Buzzbait</strong> — morning bite along grass</li>
          </ul>
        </div>
        <div class="season-block">
          <div class="season-title">Summer (Jun–Aug)</div>
          <ul class="season-baits">
            <li><strong>Bluegill Swimbait</strong> — match the primary forage, 4–5"</li>
            <li><strong>Wacky Rig / Ned Rig</strong> — under dock shade and overhanging trees</li>
            <li><strong>Buzzbait (dusk)</strong> — along the grass bank at last light</li>
            <li><strong>Texas Rig (crawfish)</strong> — flip to the shade of overhanging brush</li>
          </ul>
        </div>
        <div class="season-block">
          <div class="season-title">Fall (Sep–Nov)</div>
          <ul class="season-baits">
            <li><strong>Squarebill Crankbait</strong> — shad pattern, bang the banks</li>
            <li><strong>Spinnerbait</strong> — white/chartreuse along the entire bank</li>
            <li><strong>Jig + Craw</strong> — near the dam drop-off as water cools</li>
          </ul>
        </div>
        <div class="season-block">
          <div class="season-title">Winter (Dec–Mar)</div>
          <ul class="season-baits">
            <li><strong>Ned Rig</strong> — near the dam, deepest water in the pond</li>
            <li><strong>Jerkbait</strong> — long pauses on sunny afternoons when water warms 2–3°</li>
          </ul>
        </div>
      </div>
    </div>

    <div class="climate-card">
      <div class="climate-hdr"><h3>Western Reservoirs</h3><div class="climate-region">🏜️ California · Arizona · Nevada · Oregon</div></div>
      <div class="climate-body">
        <p>California's Delta, Clear Lake, and western impoundments produce giant spotted bass and largemouth. Swimbait fishing was essentially invented here. Deep, clear reservoirs with rocky structure. Trout, shad, and crawfish as key forage.</p>
        <div class="season-block">
          <div class="season-title">Winter / Pre-Spawn (Jan–Mar)</div>
          <ul class="season-baits">
            <li><strong>Big Swimbait (5–8")</strong> — trout imitation, slow roll main lake</li>
            <li><strong>Glide Bait</strong> — large S-curve glide bait on clear main lake points</li>
            <li><strong>Jerkbait</strong> — suspending in 6–12 ft near rocky points</li>
          </ul>
        </div>
        <div class="season-block">
          <div class="season-title">Spring (Apr–May)</div>
          <ul class="season-baits">
            <li><strong>Underspin + Keitech</strong> — staging fish 8–15 ft near spawning bays</li>
            <li><strong>Wacky Senko</strong> — sight fishing the beds in clear water</li>
            <li><strong>Drop Shot</strong> — 10 lb fluoro, natural colors, spawning flats</li>
          </ul>
        </div>
        <div class="season-block">
          <div class="season-title">Summer / Fall (Jun–Nov)</div>
          <ul class="season-baits">
            <li><strong>Drop Shot</strong> — deep, clear structure, 20–40 ft for spotted bass</li>
            <li><strong>10" Ribbon Tail Worm</strong> — drag slowly along rocky ledges</li>
            <li><strong>Big Swimbait</strong> — dawn patrol on the surface and upper water column</li>
            <li><strong>Football Jig</strong> — rocky humps and points, 15–25 ft</li>
            <li><strong>Shakey Head</strong> — finesse on pressured spotted bass</li>
          </ul>
        </div>
      </div>
    </div>

  </div>
</div><!-- /tab-climate -->


<!-- ═══════════════════════════════════════════
     TAB 3 — KNOTS
═══════════════════════════════════════════ -->
<div id="tab-knots" class="tab-panel">
  <div class="sec-title">Essential Fishing <em>Knots</em></div>
  <p class="sec-lead">A lost fish from a failed knot is the worst feeling in angling. Know these knots cold — tie them in the dark, in the rain, with cold hands — and you'll never lose a fish to gear failure.</p>

  <div class="knots-grid">

    <div class="knot-card">
      <div class="knot-hdr"><div class="knot-name">Palomar Knot</div><div class="knot-rating">★★★★★ — 95–100% · All Lines · Hooks &amp; Jigs</div></div>
      <div class="knot-body">
        <p class="knot-desc">The strongest, most reliable hook knot in existence. Works perfectly with braid, fluorocarbon, and monofilament. Every serious bass angler's default for hooks, jigs, and lures with split rings.</p>
        <ol class="knot-steps">
          <li>Double 6 inches of line and pass the loop through the hook eye</li>
          <li>Tie a simple overhand knot in the doubled line — hook hanging loose below</li>
          <li>Pass the loop over the entire hook up past the eye</li>
          <li>Pull both the tag end and standing line simultaneously to tighten — moisten first</li>
          <li>Clip tag end to ¼ inch</li>
        </ol>
        <div class="knot-use">✅ Best for: all hooks, jig heads, and lures with split rings. Works on braid, fluoro, and mono. If you learn only one knot, make it this one.</div>
      </div>
    </div>

    <div class="knot-card">
      <div class="knot-hdr"><div class="knot-name">Improved Clinch Knot</div><div class="knot-rating">★★★★☆ — 90–95% · Mono &amp; Fluoro · Fastest to Tie</div></div>
      <div class="knot-body">
        <p class="knot-desc">The world's most widely used fishing knot. Quick to tie and rock-solid on monofilament and fluorocarbon up to 20 lb. The field-standard knot for crankbaits and everyday lure changes.</p>
        <ol class="knot-steps">
          <li>Thread 6–7 inches of line through the hook or lure eye</li>
          <li>Wrap the tag end around the standing line 5–7 times (more wraps for lighter line)</li>
          <li>Pass the tag end back through the small loop formed right next to the eye</li>
          <li>Now pass the tag end through the large loop you just created</li>
          <li>Moisten and pull the standing line tight; trim the tag end</li>
        </ol>
        <div class="knot-use">✅ Best for: crankbaits, spinners, and all terminal tackle on mono or fluoro. Not ideal for heavy braid — use Palomar instead above 30 lb braid.</div>
      </div>
    </div>

    <div class="knot-card">
      <div class="knot-hdr"><div class="knot-name">Non-Slip Loop Knot</div><div class="knot-rating">★★★★★ — 100% · Maximum Lure Action</div></div>
      <div class="knot-body">
        <p class="knot-desc">Creates a fixed loop that lets your lure swing freely for maximum action. Absolutely critical for jerkbaits, topwater walkers, and any lure that depends on free, natural movement. The loop never collapses under load.</p>
        <ol class="knot-steps">
          <li>Tie a simple overhand knot 10 inches from the tag end — do NOT tighten yet</li>
          <li>Pass the tag end through the lure's hook eye or line tie</li>
          <li>Feed the tag end back through the center of the overhand knot</li>
          <li>Wrap the tag end around the standing line 3–6 times (3 for heavy; 6 for light)</li>
          <li>Pass the tag end back through the overhand knot from the same side you entered</li>
          <li>Moisten and pull the standing line until the knot slides down to form a small fixed loop; trim</li>
        </ol>
        <div class="knot-use">✅ Best for: jerkbaits (Megabass Vision 110, Rapala Shadow Rap), topwater walkers (Zara Spook), and glide baits where free-swinging action is essential.</div>
      </div>
    </div>

    <div class="knot-card">
      <div class="knot-hdr"><div class="knot-name">Alberto Knot</div><div class="knot-rating">★★★★☆ — Braid-to-Fluoro · Slim Profile</div></div>
      <div class="knot-body">
        <p class="knot-desc">The best knot for connecting braided main line to a fluorocarbon or mono leader. The slim, tapered profile slides through rod guides smoothly with zero catching. Holds exceptionally well even when the braid and leader have very different diameters.</p>
        <ol class="knot-steps">
          <li>Make a loop in the leader line (fluoro) and hold it pinched between your fingers</li>
          <li>Pass 12–15 inches of braid through the loop, going toward the tag end of the fluoro</li>
          <li>Wrap the braid around both strands of the loop 7 times, moving toward the open end</li>
          <li>Wrap back 7 times in the opposite direction over the exact same wraps</li>
          <li>Pass the braid back through the original leader loop from the same direction you entered</li>
          <li>Moisten both ends, pull both lines firmly and simultaneously until tight; trim both tags</li>
        </ol>
        <div class="knot-use">✅ Best for: 20–65 lb braid connected to 10–25 lb fluoro leader. Drop shots, finesse spinning, and any clear-water presentation needing a fluorocarbon leader.</div>
      </div>
    </div>

    <div class="knot-card">
      <div class="knot-hdr"><div class="knot-name">Double Uni Knot</div><div class="knot-rating">★★★★☆ — Line-to-Line · Simple &amp; Fast</div></div>
      <div class="knot-body">
        <p class="knot-desc">The simplest and most reliable line-to-line connection. Great when you need to attach a leader quickly without the Alberto's complexity. Slightly bulkier profile, but completely dependable in the field on both spinning and baitcasting setups.</p>
        <ol class="knot-steps">
          <li>Overlap the two lines for about 6 inches, lying side by side facing opposite directions</li>
          <li>Fold back one line and tie a uni knot (4–5 wraps) around both lines; pull snug</li>
          <li>Repeat the exact same uni knot with the other line in the opposite direction</li>
          <li>Moisten both knots and pull the two standing lines apart — the knots slide together and join</li>
          <li>Pull firmly from both ends until fully snug; trim both tag ends</li>
        </ol>
        <div class="knot-use">✅ Best for: joining similar-diameter lines. Mono-to-mono or mono-to-fluoro when speed matters over perfection. Standard leader knot for spin fishing.</div>
      </div>
    </div>

    <div class="knot-card">
      <div class="knot-hdr"><div class="knot-name">Snell Knot</div><div class="knot-rating">★★★★★ — 100% · Best Hookset Alignment</div></div>
      <div class="knot-body">
        <p class="knot-desc">The Snell knot ties line directly to the hook shank — aligning the pull force perfectly with the hook point for devastating, straight-pull hooksets. Tournament anglers and flipping specialists swear by it for heavy cover fishing where you need absolute power.</p>
        <ol class="knot-steps">
          <li>Pass 6–8 inches of line through the hook eye from the front (hook point side) toward the back</li>
          <li>Form a loop and hold it against the hook shank between your thumb and forefinger</li>
          <li>Wrap the tag end around the hook shank AND through the loop 5–7 times, moving toward the hook bend</li>
          <li>After the final wrap, pass the tag end back through the large loop near the eye</li>
          <li>Moisten and pull the standing line tight while pushing the wraps toward the eye; trim the tag</li>
        </ol>
        <div class="knot-use">✅ Best for: offset EWG hooks, heavy flipping hooks, and punch rigs. The aligned pull means more fish stay pinned in heavy cover. Use 20 lb+ fluorocarbon.</div>
      </div>
    </div>

    <div class="knot-card">
      <div class="knot-hdr"><div class="knot-name">San Diego Jam Knot</div><div class="knot-rating">★★★★★ — 95–100% · Heavy Mono &amp; Fluoro</div></div>
      <div class="knot-body">
        <p class="knot-desc">An upgraded clinch knot that excels with heavier lines (15–30 lb) where the standard improved clinch weakens. The extra back-pass through the wraps creates a cinching effect that grips heavy line with incredible holding power. Favorite of big-bait anglers.</p>
        <ol class="knot-steps">
          <li>Thread 8–10 inches of line through the hook or lure eye</li>
          <li>Wrap the tag end around the standing line 6–8 times, moving away from the eye</li>
          <li>Pass the tag end back through the loop closest to the eye (between eye and first wrap)</li>
          <li>Then pass the tag end back through the large loop formed by the previous step</li>
          <li>Moisten thoroughly and pull both ends tight; slide knot to the eye and trim</li>
        </ol>
        <div class="knot-use">✅ Best for: heavy fluoro or mono (15–30 lb) on big baits — swimbaits, big jigs, and punching rigs where the improved clinch loses strength on heavy line.</div>
      </div>
    </div>

    <div class="knot-card">
      <div class="knot-hdr"><div class="knot-name">FG Knot</div><div class="knot-rating">★★★★★ — 98–100% · Thinnest Braid-to-Leader</div></div>
      <div class="knot-body">
        <p class="knot-desc">The FG knot is the slimmest, strongest braid-to-leader connection available — it passes through guides like it's not there. Preferred by tournament anglers over the Alberto for spinning reels because the ultra-thin profile casts farther and causes zero guide noise. Takes practice to master but worth every minute.</p>
        <ol class="knot-steps">
          <li>Tension the fluoro leader against your body; hold the braid in your hands above it</li>
          <li>Weave the braid over-under-over the leader 20 times in one direction in a tight X pattern</li>
          <li>Weave back 20 times in the opposite direction, creating a tightly wrapped section</li>
          <li>Tie two half-hitches around the leader to lock the wraps in place</li>
          <li>Tie 5–6 more half-hitches around just the braid to finish; trim both tags</li>
        </ol>
        <div class="knot-use">✅ Best for: spinning reel setups where line must pass the guide knot smoothly on every cast. Drop shot, Ned rig, finesse fishing. Learn this knot — it will change your fishing.</div>
      </div>
    </div>

  </div>

  <div class="ornament">— ✦ ✦ ✦ —</div>

  <div class="h3-sec">Which Knot for Which Situation?</div>
  <div class="ref-wrap">
    <table class="ref-table">
      <thead><tr><th>Situation</th><th>Best Knot</th><th>Line Type</th><th>Notes</th></tr></thead>
      <tbody>
        <tr><td>Hook or jig to any line</td><td><b>Palomar</b></td><td>All</td><td>Default choice. Never fails.</td></tr>
        <tr><td>Crankbait / lure on mono/fluoro</td><td><b>Improved Clinch</b></td><td>Mono / Fluoro ≤20 lb</td><td>Fastest tie on the water</td></tr>
        <tr><td>Jerkbait or topwater for action</td><td><b>Non-Slip Loop</b></td><td>Any</td><td>Free swing = more strikes</td></tr>
        <tr><td>Heavy mono / fluoro lure connection</td><td><b>San Diego Jam</b></td><td>Mono / Fluoro 15–30 lb</td><td>Better than clinch on heavy line</td></tr>
        <tr><td>Braid main line → fluoro leader</td><td><b>Alberto Knot</b></td><td>Braid + Fluoro</td><td>Slim, reliable, easy to learn</td></tr>
        <tr><td>Braid → leader (spinning / finesse)</td><td><b>FG Knot</b></td><td>Braid + Fluoro</td><td>Thinnest, strongest — best for spinning</td></tr>
        <tr><td>Two similar lines joined fast</td><td><b>Double Uni</b></td><td>Mono / Fluoro</td><td>Quick field repair</td></tr>
        <tr><td>Heavy cover flipping / punching</td><td><b>Snell Knot</b></td><td>Heavy Mono / Fluoro</td><td>Best hookset alignment possible</td></tr>
      </tbody>
    </table>
  </div>

  <div style="margin-top:2rem;background:rgba(44,110,122,.08);border:1.5px solid rgba(44,110,122,.25);border-radius:4px;padding:1.6rem;">
    <h4 style="font-family:'Playfair Display',serif;font-size:1.15rem;color:var(--water-dark);margin-bottom:.7rem;">🏆 Pro Tips on Knot Tying</h4>
    <ul style="list-style:none;font-size:.88rem;line-height:2;color:#2a3a30;">
      <li>💧 <strong>Always wet your knot</strong> before tightening. Dry friction burns weaken line by up to 30%.</li>
      <li>✂️ <strong>Trim tag ends to ¼".</strong> Long tags catch weeds and alter lure action on every cast.</li>
      <li>🔬 <strong>Inspect after every fish.</strong> Run the line through your fingers — any nick, rough spot, or kink means retie immediately.</li>
      <li>📏 <strong>More wraps ≠ stronger</strong> on heavy line. 4–5 wraps for 20 lb+; 6–7 wraps for 6–12 lb line.</li>
      <li>🎯 <strong>Practice at home.</strong> Tie every knot 20–30 times until your hands can do it automatically. The ability to tie a good knot in the dark with cold wet hands is what separates anglers from fishermen.</li>
      <li>🧪 <strong>Test before you fish.</strong> Pull hard on the knot with your hands before the first cast. If it slips — retie. A knot that fails under hand pressure will fail on a fish.</li>
    </ul>
  </div>

</div><!-- /tab-knots -->

</main>

<footer>
  <p>🎣 <span>The Tackle Box</span> · The Angler's Guide · Built for Bass Fishermen Everywhere</p>
  <p style="margin-top:.35rem;font-size:.62rem;opacity:.5;">Fish responsibly · Practice catch &amp; release on trophy fish · Know your local regulations</p>
</footer>

<script>
function showTab(name, btn) {
  document.querySelectorAll('.tab-panel').forEach(p => p.classList.remove('active'));
  document.querySelectorAll('nav button').forEach(b => b.classList.remove('active'));
  document.getElementById('tab-' + name).classList.add('active');
  btn.classList.add('active');
  window.scrollTo({ top: 0, behavior: 'smooth' });
}
</script>
</body>
</html>
