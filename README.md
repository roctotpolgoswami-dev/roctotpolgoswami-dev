<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Roctotpol Goswami — Profile Preview</title>
<link href="https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@300;400;600;700;800&family=Orbitron:wght@400;700;900&display=swap" rel="stylesheet">
<style>
  :root {
    --acid: #00ff88;
    --cyan: #00e5ff;
    --magenta: #ff006e;
    --dark: #080c10;
    --card: #0d1117;
    --border: #1a2332;
    --muted: #3d5166;
    --text: #c9d1d9;
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    background: var(--dark);
    color: var(--text);
    font-family: 'JetBrains Mono', monospace;
    min-height: 100vh;
    overflow-x: hidden;
    position: relative;
  }

  /* Grid background */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background-image:
      linear-gradient(rgba(0,255,136,0.03) 1px, transparent 1px),
      linear-gradient(90deg, rgba(0,255,136,0.03) 1px, transparent 1px);
    background-size: 40px 40px;
    pointer-events: none;
    z-index: 0;
  }

  .container {
    max-width: 860px;
    margin: 0 auto;
    padding: 40px 24px 80px;
    position: relative;
    z-index: 1;
  }

  /* ── HERO ── */
  .hero {
    text-align: center;
    padding: 60px 0 40px;
    position: relative;
  }

  .hero::before {
    content: '';
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    width: 500px;
    height: 500px;
    background: radial-gradient(circle, rgba(0,255,136,0.06) 0%, transparent 70%);
    pointer-events: none;
  }

  .status-bar {
    display: inline-flex;
    align-items: center;
    gap: 8px;
    background: rgba(0,255,136,0.08);
    border: 1px solid rgba(0,255,136,0.2);
    border-radius: 100px;
    padding: 6px 16px;
    font-size: 11px;
    color: var(--acid);
    letter-spacing: 2px;
    text-transform: uppercase;
    margin-bottom: 28px;
    animation: fadeUp 0.6s ease both;
  }

  .status-dot {
    width: 7px;
    height: 7px;
    background: var(--acid);
    border-radius: 50%;
    animation: pulse 1.8s ease-in-out infinite;
    box-shadow: 0 0 8px var(--acid);
  }

  @keyframes pulse {
    0%, 100% { opacity: 1; transform: scale(1); }
    50% { opacity: 0.4; transform: scale(0.7); }
  }

  .hero-name {
    font-family: 'Orbitron', sans-serif;
    font-size: clamp(28px, 6vw, 52px);
    font-weight: 900;
    line-height: 1.1;
    letter-spacing: -1px;
    animation: fadeUp 0.6s 0.1s ease both;
  }

  .hero-name .first { color: #fff; }
  .hero-name .last {
    background: linear-gradient(90deg, var(--acid), var(--cyan));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
  }

  .hero-handle {
    color: var(--muted);
    font-size: 13px;
    letter-spacing: 3px;
    margin-top: 6px;
    text-transform: uppercase;
    animation: fadeUp 0.6s 0.15s ease both;
  }

  .hero-tagline {
    margin-top: 20px;
    font-size: 14px;
    color: var(--cyan);
    letter-spacing: 1px;
    animation: fadeUp 0.6s 0.2s ease both;
  }

  /* ── TERMINAL ── */
  .terminal {
    background: #0a0f14;
    border: 1px solid var(--border);
    border-radius: 12px;
    overflow: hidden;
    margin: 36px 0;
    box-shadow: 0 0 60px rgba(0,0,0,0.5), 0 0 1px rgba(0,255,136,0.1) inset;
    animation: fadeUp 0.6s 0.3s ease both;
  }

  .terminal-bar {
    background: #111920;
    padding: 10px 16px;
    display: flex;
    align-items: center;
    gap: 8px;
    border-bottom: 1px solid var(--border);
  }

  .dot { width: 12px; height: 12px; border-radius: 50%; }
  .dot.r { background: #ff5f57; }
  .dot.y { background: #febc2e; }
  .dot.g { background: #28c840; }

  .terminal-title {
    font-size: 11px;
    color: var(--muted);
    margin-left: 8px;
    letter-spacing: 1px;
  }

  .terminal-body {
    padding: 24px;
    font-size: 13px;
    line-height: 2;
  }

  .t-line { opacity: 0; animation: typeIn 0.01s ease forwards; }
  .t-line:nth-child(1) { animation-delay: 0.5s; }
  .t-line:nth-child(2) { animation-delay: 0.9s; }
  .t-line:nth-child(3) { animation-delay: 1.3s; }
  .t-line:nth-child(4) { animation-delay: 1.7s; }
  .t-line:nth-child(5) { animation-delay: 2.1s; }
  .t-line:nth-child(6) { animation-delay: 2.5s; }
  .t-line:nth-child(7) { animation-delay: 2.9s; }

  @keyframes typeIn { to { opacity: 1; } }

  .prompt { color: var(--acid); }
  .cmd { color: #fff; }
  .out-label { color: var(--muted); }
  .out-val { color: var(--cyan); }
  .out-str { color: #ffd700; }
  .cursor {
    display: inline-block;
    width: 8px;
    height: 14px;
    background: var(--acid);
    vertical-align: middle;
    animation: blink 1s step-end infinite;
  }
  @keyframes blink { 50% { opacity: 0; } }

  /* ── SECTION TITLES ── */
  .section-label {
    display: flex;
    align-items: center;
    gap: 12px;
    margin: 48px 0 20px;
    font-size: 11px;
    letter-spacing: 3px;
    text-transform: uppercase;
    color: var(--muted);
  }
  .section-label::before, .section-label::after {
    content: '';
    flex: 1;
    height: 1px;
    background: var(--border);
  }
  .section-label span { color: var(--acid); white-space: nowrap; }

  /* ── TECH STACK GRID ── */
  .tech-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(80px, 1fr));
    gap: 10px;
    animation: fadeUp 0.6s 0.4s ease both;
  }

  .tech-chip {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 8px;
    padding: 12px 8px;
    text-align: center;
    font-size: 11px;
    color: var(--muted);
    letter-spacing: 0.5px;
    transition: all 0.2s ease;
    cursor: default;
    position: relative;
    overflow: hidden;
  }

  .tech-chip::before {
    content: '';
    position: absolute;
    inset: 0;
    background: linear-gradient(135deg, rgba(0,255,136,0.05), transparent);
    opacity: 0;
    transition: opacity 0.2s;
  }

  .tech-chip:hover {
    border-color: var(--acid);
    color: var(--acid);
    transform: translateY(-2px);
    box-shadow: 0 8px 24px rgba(0,255,136,0.1);
  }

  .tech-chip:hover::before { opacity: 1; }

  .tech-icon { font-size: 22px; display: block; margin-bottom: 6px; }

  /* ── STATS ROW ── */
  .stats-row {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 12px;
    animation: fadeUp 0.6s 0.5s ease both;
  }

  .stat-card {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 10px;
    padding: 20px;
    text-align: center;
    transition: all 0.2s ease;
    position: relative;
    overflow: hidden;
  }

  .stat-card::after {
    content: '';
    position: absolute;
    bottom: 0;
    left: 0;
    right: 0;
    height: 2px;
    background: linear-gradient(90deg, var(--acid), var(--cyan));
    transform: scaleX(0);
    transition: transform 0.3s ease;
    transform-origin: left;
  }

  .stat-card:hover::after { transform: scaleX(1); }
  .stat-card:hover { border-color: rgba(0,255,136,0.2); transform: translateY(-2px); }

  .stat-num {
    font-family: 'Orbitron', sans-serif;
    font-size: 28px;
    font-weight: 700;
    color: #fff;
  }

  .stat-num .accent { color: var(--acid); }

  .stat-label {
    font-size: 10px;
    color: var(--muted);
    letter-spacing: 2px;
    text-transform: uppercase;
    margin-top: 4px;
  }

  /* ── CURRENTLY BUILDING ── */
  .focus-list {
    display: flex;
    flex-direction: column;
    gap: 10px;
    animation: fadeUp 0.6s 0.6s ease both;
  }

  .focus-item {
    background: var(--card);
    border: 1px solid var(--border);
    border-left: 3px solid var(--acid);
    border-radius: 0 8px 8px 0;
    padding: 14px 18px;
    display: flex;
    align-items: center;
    gap: 14px;
    font-size: 13px;
    transition: all 0.2s ease;
  }

  .focus-item:hover {
    background: rgba(0,255,136,0.04);
    border-left-color: var(--cyan);
    transform: translateX(4px);
  }

  .focus-item:nth-child(2) { border-left-color: var(--cyan); }
  .focus-item:nth-child(3) { border-left-color: var(--magenta); }

  .focus-icon { font-size: 18px; flex-shrink: 0; }

  .focus-text strong { color: #fff; display: block; margin-bottom: 2px; }
  .focus-text small { color: var(--muted); font-size: 11px; }

  /* ── QUOTE ── */
  .quote-block {
    margin: 48px 0 0;
    text-align: center;
    animation: fadeUp 0.6s 0.7s ease both;
  }

  .quote-inner {
    display: inline-block;
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 28px 40px;
    position: relative;
  }

  .quote-inner::before {
    content: '"';
    position: absolute;
    top: -20px;
    left: 24px;
    font-size: 80px;
    color: var(--acid);
    opacity: 0.15;
    font-family: 'Orbitron', sans-serif;
    line-height: 1;
  }

  .quote-text {
    font-size: 16px;
    color: #fff;
    font-weight: 600;
    letter-spacing: 0.5px;
  }

  .quote-attr {
    font-size: 11px;
    color: var(--muted);
    margin-top: 8px;
    letter-spacing: 2px;
    text-transform: uppercase;
  }

  /* ── CONNECT ── */
  .connect-row {
    display: flex;
    justify-content: center;
    gap: 12px;
    margin-top: 32px;
    animation: fadeUp 0.6s 0.8s ease both;
  }

  .connect-btn {
    background: transparent;
    border: 1px solid var(--border);
    border-radius: 8px;
    padding: 12px 20px;
    font-family: 'JetBrains Mono', monospace;
    font-size: 12px;
    color: var(--muted);
    cursor: pointer;
    transition: all 0.2s ease;
    letter-spacing: 1px;
    text-decoration: none;
    display: inline-flex;
    align-items: center;
    gap: 8px;
  }

  .connect-btn:hover {
    border-color: var(--acid);
    color: var(--acid);
    background: rgba(0,255,136,0.05);
    box-shadow: 0 0 20px rgba(0,255,136,0.1);
  }

  /* ── FOOTER ── */
  .footer {
    text-align: center;
    margin-top: 60px;
    font-size: 11px;
    color: var(--muted);
    letter-spacing: 1px;
    animation: fadeUp 0.6s 0.9s ease both;
  }

  /* ── BADGE ── */
  .badge-row {
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
    justify-content: center;
    margin-top: 24px;
    animation: fadeUp 0.6s 0.35s ease both;
  }

  .badge {
    background: rgba(0,229,255,0.08);
    border: 1px solid rgba(0,229,255,0.2);
    color: var(--cyan);
    font-size: 10px;
    letter-spacing: 1.5px;
    text-transform: uppercase;
    padding: 4px 12px;
    border-radius: 100px;
  }

  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(18px); }
    to { opacity: 1; transform: translateY(0); }
  }

  /* ── NOTE ── */
  .preview-note {
    background: rgba(255, 0, 110, 0.08);
    border: 1px solid rgba(255, 0, 110, 0.2);
    border-radius: 8px;
    padding: 12px 18px;
    font-size: 11px;
    color: #ff7eb3;
    letter-spacing: 0.5px;
    margin-bottom: 32px;
    text-align: center;
  }
</style>
</head>
<body>
<div class="container">

  <div class="preview-note">
    ✦ This is a <strong>live preview</strong> of your new GitHub README vibe ✦ Scroll down to see it all
  </div>

  <!-- HERO -->
  <div class="hero">
    <div class="status-bar">
      <span class="status-dot"></span>
      Available for collabs
    </div>

    <div class="hero-name">
      <span class="first">Roctotpol </span>
      <span class="last">Goswami</span>
    </div>
    <div class="hero-handle">@roctotpol · Guwahati, IN</div>
    <div class="hero-tagline">⚡ B.Tech CSE · Builder · Problem Solver · Forever Curious</div>

    <div class="badge-row">
      <span class="badge">Open to Opportunities</span>
      <span class="badge">Learning DSA</span>
      <span class="badge">Web Dev</span>
      <span class="badge">Open Source</span>
    </div>
  </div>

  <!-- TERMINAL -->
  <div class="terminal">
    <div class="terminal-bar">
      <span class="dot r"></span>
      <span class="dot y"></span>
      <span class="dot g"></span>
      <span class="terminal-title">roctotpol@github ~ bash</span>
    </div>
    <div class="terminal-body">
      <div class="t-line"><span class="prompt">❯ </span><span class="cmd">whoami</span></div>
      <div class="t-line"><span class="out-val">roctotpol_goswami</span> <span class="out-label">// B.Tech CSE, Assam</span></div>
      <div class="t-line"><span class="prompt">❯ </span><span class="cmd">cat mission.txt</span></div>
      <div class="t-line"><span class="out-str">"Turn every idea into something real. Ship it. Learn. Repeat."</span></div>
      <div class="t-line"><span class="prompt">❯ </span><span class="cmd">ls skills/</span></div>
      <div class="t-line"><span class="out-val">C++</span> &nbsp;<span class="out-val">Python</span> &nbsp;<span class="out-val">Java</span> &nbsp;<span class="out-val">HTML/CSS/JS</span> &nbsp;<span class="out-val">Git</span> &nbsp;<span class="out-val">Linux</span> &nbsp;<span class="out-val">DSA</span></div>
      <div class="t-line"><span class="prompt">❯ </span><span class="cursor"></span></div>
    </div>
  </div>

  <!-- TECH STACK -->
  <div class="section-label"><span>// Tech Stack</span></div>
  <div class="tech-grid">
    <div class="tech-chip"><span class="tech-icon">⚡</span>C++</div>
    <div class="tech-chip"><span class="tech-icon">🔵</span>C</div>
    <div class="tech-chip"><span class="tech-icon">🐍</span>Python</div>
    <div class="tech-chip"><span class="tech-icon">☕</span>Java</div>
    <div class="tech-chip"><span class="tech-icon">🌐</span>HTML</div>
    <div class="tech-chip"><span class="tech-icon">🎨</span>CSS</div>
    <div class="tech-chip"><span class="tech-icon">✨</span>JavaScript</div>
    <div class="tech-chip"><span class="tech-icon">🌿</span>Git</div>
    <div class="tech-chip"><span class="tech-icon">🐙</span>GitHub</div>
    <div class="tech-chip"><span class="tech-icon">💻</span>VSCode</div>
    <div class="tech-chip"><span class="tech-icon">🐧</span>Linux</div>
    <div class="tech-chip"><span class="tech-icon">🔢</span>DSA</div>
  </div>

  <!-- STATS -->
  <div class="section-label"><span>// At a Glance</span></div>
  <div class="stats-row">
    <div class="stat-card">
      <div class="stat-num">∞<span class="accent">+</span></div>
      <div class="stat-label">Ideas to Code</div>
    </div>
    <div class="stat-card">
      <div class="stat-num">24<span class="accent">/7</span></div>
      <div class="stat-label">In Learning Mode</div>
    </div>
    <div class="stat-card">
      <div class="stat-num">1<span class="accent">K</span></div>
      <div class="stat-label">Cups of ☕ Debugged</div>
    </div>
  </div>

  <!-- CURRENTLY -->
  <div class="section-label"><span>// Currently Focused On</span></div>
  <div class="focus-list">
    <div class="focus-item">
      <span class="focus-icon">🧠</span>
      <div class="focus-text">
        <strong>Data Structures & Algorithms</strong>
        <small>Grinding LeetCode · Building strong fundamentals</small>
      </div>
    </div>
    <div class="focus-item">
      <span class="focus-icon">🛠️</span>
      <div class="focus-text">
        <strong>Building Real Projects</strong>
        <small>Turning concepts into working software</small>
      </div>
    </div>
    <div class="focus-item">
      <span class="focus-icon">🌐</span>
      <div class="focus-text">
        <strong>Web Dev & Software Engineering</strong>
        <small>Exploring full-stack development</small>
      </div>
    </div>
  </div>

  <!-- QUOTE -->
  <div class="quote-block">
    <div class="quote-inner">
      <div class="quote-text">Code. Learn. Build. Repeat.</div>
      <div class="quote-attr">— Roctotpol's Operating System</div>
    </div>
  </div>

  <!-- CONNECT -->
  <div class="section-label"><span>// Connect</span></div>
  <div class="connect-row">
    <a class="connect-btn" href="#">🐙 &nbsp;GitHub</a>
    <a class="connect-btn" href="#">💼 &nbsp;LinkedIn</a>
    <a class="connect-btn" href="#">📬 &nbsp;Email</a>
  </div>

  <div class="footer">
    <p>Profile crafted with intention · Updated 2026</p>
    <p style="margin-top:6px; color: #1e3040;">Made with ❤️ in Assam, India</p>
  </div>

</div>
</body>
</html>
