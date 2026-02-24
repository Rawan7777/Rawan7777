<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Bilal Rouane — Developer Profile</title>
<link href="https://fonts.googleapis.com/css2?family=Space+Mono:wght@400;700&family=Syne:wght@400;600;800&display=swap" rel="stylesheet">
<style>
  :root {
    --bg: #0a0c10;
    --surface: #0d1117;
    --panel: #161b22;
    --border: #21262d;
    --accent: #58a6ff;
    --accent2: #3fb950;
    --accent3: #f78166;
    --text: #e6edf3;
    --muted: #8b949e;
    --glow: rgba(88,166,255,0.15);
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'Syne', sans-serif;
    min-height: 100vh;
    overflow-x: hidden;
  }

  /* Grid background */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background-image:
      linear-gradient(rgba(88,166,255,0.03) 1px, transparent 1px),
      linear-gradient(90deg, rgba(88,166,255,0.03) 1px, transparent 1px);
    background-size: 40px 40px;
    pointer-events: none;
    z-index: 0;
  }

  .container {
    max-width: 900px;
    margin: 0 auto;
    padding: 40px 24px 80px;
    position: relative;
    z-index: 1;
  }

  /* HERO */
  .hero {
    text-align: center;
    padding: 60px 0 40px;
    position: relative;
  }

  .hero-glow {
    position: absolute;
    top: 0; left: 50%;
    transform: translateX(-50%);
    width: 500px; height: 300px;
    background: radial-gradient(ellipse, rgba(88,166,255,0.12) 0%, transparent 70%);
    pointer-events: none;
  }

  .hero-tag {
    display: inline-block;
    font-family: 'Space Mono', monospace;
    font-size: 11px;
    letter-spacing: 3px;
    color: var(--accent);
    text-transform: uppercase;
    border: 1px solid rgba(88,166,255,0.3);
    padding: 4px 14px;
    border-radius: 20px;
    margin-bottom: 20px;
    animation: fadeUp 0.6s ease both;
  }

  .hero-name {
    font-size: clamp(42px, 8vw, 72px);
    font-weight: 800;
    letter-spacing: -2px;
    line-height: 1;
    animation: fadeUp 0.6s 0.1s ease both;
  }

  .hero-name span {
    background: linear-gradient(135deg, #58a6ff 0%, #a5d6ff 50%, #58a6ff 100%);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
  }

  .hero-sub {
    font-family: 'Space Mono', monospace;
    color: var(--muted);
    font-size: 13px;
    margin-top: 12px;
    letter-spacing: 1px;
    animation: fadeUp 0.6s 0.2s ease both;
  }

  .hero-links {
    display: flex;
    gap: 12px;
    justify-content: center;
    margin-top: 28px;
    animation: fadeUp 0.6s 0.3s ease both;
  }

  .badge {
    display: inline-flex;
    align-items: center;
    gap: 7px;
    font-family: 'Space Mono', monospace;
    font-size: 11px;
    font-weight: 700;
    padding: 8px 16px;
    border-radius: 6px;
    text-decoration: none;
    letter-spacing: 0.5px;
    transition: all 0.2s;
    border: 1px solid transparent;
  }

  .badge:hover { transform: translateY(-2px); filter: brightness(1.2); }

  .badge-blue { background: rgba(88,166,255,0.1); color: var(--accent); border-color: rgba(88,166,255,0.3); }
  .badge-red { background: rgba(234,67,53,0.1); color: #ea4335; border-color: rgba(234,67,53,0.3); }
  .badge-black { background: rgba(255,255,255,0.05); color: var(--text); border-color: var(--border); }

  /* SECTION */
  .section {
    margin-top: 48px;
    animation: fadeUp 0.6s 0.4s ease both;
  }

  .section-label {
    font-family: 'Space Mono', monospace;
    font-size: 10px;
    letter-spacing: 4px;
    text-transform: uppercase;
    color: var(--accent);
    margin-bottom: 16px;
    display: flex;
    align-items: center;
    gap: 12px;
  }

  .section-label::after {
    content: '';
    flex: 1;
    height: 1px;
    background: linear-gradient(90deg, var(--border), transparent);
  }

  /* CODE BLOCK */
  .code-block {
    background: var(--panel);
    border: 1px solid var(--border);
    border-radius: 12px;
    overflow: hidden;
    font-family: 'Space Mono', monospace;
  }

  .code-header {
    background: var(--surface);
    padding: 10px 16px;
    display: flex;
    align-items: center;
    gap: 8px;
    border-bottom: 1px solid var(--border);
  }

  .dot { width: 10px; height: 10px; border-radius: 50%; }
  .dot-r { background: #f78166; }
  .dot-y { background: #e3b341; }
  .dot-g { background: #3fb950; }

  .code-filename {
    font-size: 11px;
    color: var(--muted);
    margin-left: 8px;
  }

  .code-body {
    padding: 20px 24px;
    font-size: 13px;
    line-height: 1.8;
    overflow-x: auto;
  }

  .kw { color: #ff7b72; }
  .fn { color: #d2a8ff; }
  .cl { color: #79c0ff; }
  .str { color: #a5d6ff; }
  .cm { color: #8b949e; font-style: italic; }
  .self-kw { color: #ff7b72; }
  .var { color: #e6edf3; }
  .bracket { color: #e3b341; }

  /* SKILLS GRID */
  .skills-grid {
    display: grid;
    gap: 12px;
  }

  .skill-group {
    background: var(--panel);
    border: 1px solid var(--border);
    border-radius: 10px;
    padding: 16px 20px;
  }

  .skill-group-title {
    font-family: 'Space Mono', monospace;
    font-size: 10px;
    letter-spacing: 2px;
    text-transform: uppercase;
    color: var(--muted);
    margin-bottom: 12px;
  }

  .skill-tags {
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
  }

  .skill-tag {
    font-family: 'Space Mono', monospace;
    font-size: 11px;
    padding: 5px 12px;
    border-radius: 4px;
    border: 1px solid;
    font-weight: 700;
    letter-spacing: 0.5px;
    transition: all 0.2s;
  }

  .skill-tag:hover { transform: translateY(-2px); filter: brightness(1.3); }

  .tag-c { color: #58a6ff; border-color: rgba(88,166,255,0.3); background: rgba(88,166,255,0.07); }
  .tag-py { color: #3fb950; border-color: rgba(63,185,80,0.3); background: rgba(63,185,80,0.07); }
  .tag-web { color: #e3b341; border-color: rgba(227,179,65,0.3); background: rgba(227,179,65,0.07); }
  .tag-db { color: #d2a8ff; border-color: rgba(210,168,255,0.3); background: rgba(210,168,255,0.07); }
  .tag-tool { color: #f78166; border-color: rgba(247,129,102,0.3); background: rgba(247,129,102,0.07); }
  .tag-design { color: #79c0ff; border-color: rgba(121,192,255,0.3); background: rgba(121,192,255,0.07); }

  /* STATUS LIST */
  .status-list {
    display: grid;
    gap: 8px;
  }

  .status-item {
    background: var(--panel);
    border: 1px solid var(--border);
    border-radius: 8px;
    padding: 12px 16px;
    display: flex;
    align-items: center;
    gap: 12px;
    font-size: 14px;
    transition: border-color 0.2s, background 0.2s;
  }

  .status-item:hover {
    border-color: rgba(88,166,255,0.3);
    background: rgba(88,166,255,0.03);
  }

  .status-icon {
    font-size: 16px;
    width: 24px;
    text-align: center;
  }

  .status-text strong { color: var(--accent); }

  /* STATS */
  .stats-row {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 12px;
  }

  .stat-card {
    background: var(--panel);
    border: 1px solid var(--border);
    border-radius: 10px;
    overflow: hidden;
  }

  .stat-card img {
    width: 100%;
    display: block;
  }

  /* QUOTE */
  .quote-block {
    text-align: center;
    padding: 40px 0 20px;
    font-family: 'Space Mono', monospace;
    font-size: 13px;
    color: var(--muted);
    font-style: italic;
    animation: fadeUp 0.6s 0.5s ease both;
  }

  .quote-block::before {
    content: '"';
    display: block;
    font-size: 48px;
    color: rgba(88,166,255,0.2);
    font-style: normal;
    line-height: 1;
    margin-bottom: 8px;
  }

  /* ANIMATIONS */
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(20px); }
    to { opacity: 1; transform: translateY(0); }
  }

  /* FOOTER */
  .footer {
    text-align: center;
    margin-top: 48px;
    font-family: 'Space Mono', monospace;
    font-size: 10px;
    letter-spacing: 2px;
    color: var(--border);
  }
</style>
</head>
<body>
<div class="container">

  <!-- HERO -->
  <div class="hero">
    <div class="hero-glow"></div>
    <div class="hero-tag">📍 Morocco · 1337 | 42 Network</div>
    <h1 class="hero-name">Hi, I'm <span>Bilal Rouane</span></h1>
    <p class="hero-sub">Systems · Frontend · Linux · Always building</p>
    <div class="hero-links">
      <a href="https://www.linkedin.com/in/bilal-rouane-01aa3a372/" class="badge badge-blue" target="_blank">
        <svg width="14" height="14" viewBox="0 0 24 24" fill="currentColor"><path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433a2.062 2.062 0 0 1-2.063-2.065 2.064 2.064 0 1 1 2.063 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/></svg>
        LinkedIn
      </a>
      <a href="mailto:bilal.rouane702@gmail.com" class="badge badge-red">
        <svg width="14" height="14" viewBox="0 0 24 24" fill="currentColor"><path d="M24 5.457v13.909c0 .904-.732 1.636-1.636 1.636h-3.819V11.73L12 16.364l-6.545-4.636v9.273H1.636A1.636 1.636 0 0 1 0 19.366V5.457c0-.301.082-.586.241-.847l.81.810L12 14.09l10.949-8.67.81-.81c.159.261.241.546.241.847z"/><path d="M23.09 4.655L12 13.09.91 4.655C1.238 4.241 1.81 4 2.455 4h19.09c.645 0 1.217.241 1.545.655z"/></svg>
        Email
      </a>
      <a href="https://www.1337.ma/" class="badge badge-black" target="_blank">
        <span style="font-weight:800;font-size:13px;">42</span>
        1337 School
      </a>
    </div>
  </div>

  <!-- ABOUT -->
  <div class="section">
    <div class="section-label">About</div>
    <div class="code-block">
      <div class="code-header">
        <div class="dot dot-r"></div>
        <div class="dot dot-y"></div>
        <div class="dot dot-g"></div>
        <span class="code-filename">bilal.py</span>
      </div>
      <div class="code-body">
<pre><span class="kw">class</span> <span class="cl">Bilal</span>:
    <span class="kw">def</span> <span class="fn">__init__</span>(<span class="self-kw">self</span>):
        <span class="self-kw">self</span>.name      = <span class="str">"Bilal Rouane"</span>
        <span class="self-kw">self</span>.school    = <span class="str">"1337 — 42 Network 🎓"</span>
        <span class="self-kw">self</span>.location  = <span class="str">"Morocco 🇲🇦"</span>
        <span class="self-kw">self</span>.interests = <span class="bracket">[</span><span class="str">"Systems Programming"</span>, <span class="str">"Frontend Dev"</span>, <span class="str">"Linux"</span><span class="bracket">]</span>
        <span class="self-kw">self</span>.languages = <span class="bracket">[</span><span class="str">"C"</span>, <span class="str">"C++"</span>, <span class="str">"Python"</span>, <span class="str">"JavaScript"</span>, <span class="str">"PHP"</span><span class="bracket">]</span>
        <span class="self-kw">self</span>.contact   = <span class="str">"bilal.rouane702@gmail.com"</span>

    <span class="kw">def</span> <span class="fn">say_hi</span>(<span class="self-kw">self</span>):
        <span class="fn">print</span>(<span class="str">"Thanks for stopping by! Let's build something cool. 🤝"</span>)

<span class="var">me</span> = <span class="cl">Bilal</span>()
<span class="var">me</span>.<span class="fn">say_hi</span>()</pre>
      </div>
    </div>
  </div>

  <!-- SKILLS -->
  <div class="section">
    <div class="section-label">Languages & Tools</div>
    <div class="skills-grid">
      <div class="skill-group">
        <div class="skill-group-title">Systems & Scripting</div>
        <div class="skill-tags">
          <span class="skill-tag tag-c">C</span>
          <span class="skill-tag tag-c">C++</span>
          <span class="skill-tag tag-py">Python</span>
          <span class="skill-tag tag-tool">Linux</span>
          <span class="skill-tag tag-tool">Git</span>
        </div>
      </div>
      <div class="skill-group">
        <div class="skill-group-title">Frontend</div>
        <div class="skill-tags">
          <span class="skill-tag tag-web">HTML5</span>
          <span class="skill-tag tag-web">CSS3</span>
          <span class="skill-tag tag-web">JavaScript</span>
        </div>
      </div>
      <div class="skill-group">
        <div class="skill-group-title">Backend & Database</div>
        <div class="skill-tags">
          <span class="skill-tag tag-db">PHP</span>
          <span class="skill-tag tag-db">MySQL</span>
        </div>
      </div>
      <div class="skill-group">
        <div class="skill-group-title">Design</div>
        <div class="skill-tags">
          <span class="skill-tag tag-design">Photoshop</span>
        </div>
      </div>
    </div>
  </div>

  <!-- GITHUB STATS -->
  <div class="section">
    <div class="section-label">GitHub Stats</div>
    <div class="stats-row">
      <div class="stat-card">
        <img src="https://github-readme-stats.vercel.app/api?username=bilalrouane&show_icons=true&theme=tokyonight&include_all_commits=true&count_private=true&hide_border=true" alt="GitHub Stats" loading="lazy">
      </div>
      <div class="stat-card">
        <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=bilalrouane&layout=compact&theme=tokyonight&hide_border=true&langs_count=8" alt="Top Languages" loading="lazy">
      </div>
    </div>
    <div class="stat-card" style="margin-top:12px; text-align:center; background: var(--panel); border: 1px solid var(--border); border-radius: 10px; overflow:hidden;">
      <img src="https://streak-stats.demolab.com?user=bilalrouane&theme=tokyonight&hide_border=true" alt="GitHub Streak" loading="lazy" style="max-width:100%;">
    </div>
  </div>

  <!-- WHAT I'M UP TO -->
  <div class="section">
    <div class="section-label">Currently</div>
    <div class="status-list">
      <div class="status-item">
        <span class="status-icon">🏫</span>
        <span class="status-text">Studying at <strong>1337</strong> — part of the global <strong>42 Network</strong></span>
      </div>
      <div class="status-item">
        <span class="status-icon">⚙️</span>
        <span class="status-text">Strengthening <strong>C</strong> foundations through low-level peer-to-peer projects</span>
      </div>
      <div class="status-item">
        <span class="status-icon">🐍</span>
        <span class="status-text">Leveling up in <strong>Python</strong> — data structures, OOP, file I/O</span>
      </div>
      <div class="status-item">
        <span class="status-icon">🌐</span>
        <span class="status-text">Building frontend interfaces with <strong>HTML / CSS / JS</strong></span>
      </div>
      <div class="status-item">
        <span class="status-icon">🐧</span>
        <span class="status-text">Diving deeper into <strong>Linux</strong> internals and system programming</span>
      </div>
      <div class="status-item">
        <span class="status-icon">📬</span>
        <span class="status-text">Always open to chat: <strong>bilal.rouane702@gmail.com</strong></span>
      </div>
    </div>
  </div>

  <!-- ASK ME ABOUT -->
  <div class="section">
    <div class="section-label">Ask Me About</div>
    <div class="skill-group">
      <div class="skill-tags">
        <span class="skill-tag tag-c">C</span>
        <span class="skill-tag tag-py">Python</span>
        <span class="skill-tag tag-web">Frontend Web</span>
        <span class="skill-tag tag-tool">Linux</span>
        <span class="skill-tag tag-db">42 / 1337 Curriculum</span>
      </div>
    </div>
  </div>

  <!-- QUOTE -->
  <div class="quote-block">
    "The best error message is the one that never shows up."<br>
    <span style="color: var(--accent); font-style: normal; margin-top: 6px; display: block;">— Thomas Fuchs</span>
  </div>

  <div class="footer">BILAL ROUANE · MOROCCO · 2025</div>

</div>
</body>
</html>
