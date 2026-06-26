<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Kiran Sagar D S – README</title>
<link href="https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@300;400;700&family=Space+Grotesk:wght@300;400;600;700&display=swap" rel="stylesheet"/>
<style>
  :root {
    --forest:    #14452F;
    --forest-mid:#1d6344;
    --forest-lt: #29855a;
    --mint:      #4fffa0;
    --mint-dim:  #2dcc74;
    --cream:     #f0f9f4;
    --charcoal:  #0a1f14;
    --glass:     rgba(20,69,47,0.45);
    --glass-border: rgba(79,255,160,0.18);
  }

  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  html { scroll-behavior: smooth; }

  body {
    background: var(--charcoal);
    color: var(--cream);
    font-family: 'Space Grotesk', sans-serif;
    overflow-x: hidden;
    min-height: 100vh;
  }

  /* ── PARTICLE CANVAS ─────────────────────────────── */
  #canvas {
    position: fixed;
    inset: 0;
    z-index: 0;
    pointer-events: none;
  }

  /* ── LAYOUT ──────────────────────────────────────── */
  .page {
    position: relative;
    z-index: 1;
    max-width: 900px;
    margin: 0 auto;
    padding: 40px 24px 80px;
  }

  /* ── HERO ────────────────────────────────────────── */
  .hero {
    text-align: center;
    padding: 60px 0 40px;
    position: relative;
  }

  .hero__badge {
    display: inline-block;
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.72rem;
    letter-spacing: 0.2em;
    color: var(--mint);
    border: 1px solid var(--glass-border);
    background: var(--glass);
    padding: 6px 18px;
    border-radius: 50px;
    margin-bottom: 28px;
    opacity: 0;
    animation: fadeUp 0.6s ease 0.2s forwards;
  }

  .hero__name {
    font-size: clamp(2.6rem, 7vw, 5rem);
    font-weight: 700;
    line-height: 1.05;
    letter-spacing: -0.03em;
    background: linear-gradient(135deg, var(--cream) 0%, var(--mint) 60%, var(--mint-dim) 100%);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    opacity: 0;
    animation: fadeUp 0.7s ease 0.4s forwards;
  }

  .hero__title {
    margin-top: 14px;
    font-size: 1.05rem;
    font-weight: 300;
    color: rgba(240,249,244,0.6);
    letter-spacing: 0.04em;
    opacity: 0;
    animation: fadeUp 0.7s ease 0.6s forwards;
  }

  .hero__typing {
    margin-top: 24px;
    font-family: 'JetBrains Mono', monospace;
    font-size: 1.15rem;
    color: var(--mint);
    min-height: 1.6em;
    opacity: 0;
    animation: fadeUp 0.7s ease 0.8s forwards;
  }

  .cursor {
    display: inline-block;
    width: 2px;
    height: 1.1em;
    background: var(--mint);
    vertical-align: middle;
    margin-left: 2px;
    animation: blink 0.9s step-end infinite;
  }

  .hero__links {
    display: flex;
    gap: 14px;
    justify-content: center;
    flex-wrap: wrap;
    margin-top: 32px;
    opacity: 0;
    animation: fadeUp 0.7s ease 1s forwards;
  }

  .btn {
    display: inline-flex;
    align-items: center;
    gap: 8px;
    padding: 10px 22px;
    border-radius: 8px;
    font-size: 0.85rem;
    font-weight: 600;
    text-decoration: none;
    letter-spacing: 0.02em;
    transition: transform 0.2s, box-shadow 0.2s;
    cursor: pointer;
  }
  .btn--primary {
    background: var(--mint);
    color: var(--forest);
  }
  .btn--ghost {
    background: var(--glass);
    color: var(--cream);
    border: 1px solid var(--glass-border);
    backdrop-filter: blur(8px);
  }
  .btn:hover { transform: translateY(-2px); box-shadow: 0 8px 28px rgba(79,255,160,0.22); }

  /* ── DIVIDER ─────────────────────────────────────── */
  .divider {
    width: 100%;
    height: 1px;
    background: linear-gradient(90deg, transparent, var(--glass-border), transparent);
    margin: 52px 0;
  }

  /* ── SECTION HEADER ──────────────────────────────── */
  .sec-label {
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.68rem;
    letter-spacing: 0.22em;
    color: var(--mint);
    text-transform: uppercase;
    margin-bottom: 6px;
  }
  .sec-title {
    font-size: 1.8rem;
    font-weight: 700;
    letter-spacing: -0.02em;
    margin-bottom: 28px;
  }

  /* ── ABOUT ───────────────────────────────────────── */
  .about-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 16px;
  }
  @media(max-width:580px){ .about-grid { grid-template-columns: 1fr; } }

  .about-card {
    background: var(--glass);
    border: 1px solid var(--glass-border);
    border-radius: 14px;
    padding: 22px 24px;
    backdrop-filter: blur(10px);
    transition: transform 0.25s, box-shadow 0.25s;
  }
  .about-card:hover {
    transform: translateY(-4px);
    box-shadow: 0 16px 40px rgba(79,255,160,0.1);
  }
  .about-card .icon { font-size: 1.6rem; margin-bottom: 10px; }
  .about-card h4 { font-size: 0.9rem; font-weight: 600; margin-bottom: 6px; }
  .about-card p { font-size: 0.82rem; color: rgba(240,249,244,0.65); line-height: 1.6; }

  /* ── SKILLS ──────────────────────────────────────── */
  .skills-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
    gap: 14px;
  }

  .skill-group {
    background: var(--glass);
    border: 1px solid var(--glass-border);
    border-radius: 12px;
    padding: 18px 20px;
    backdrop-filter: blur(10px);
    transition: transform 0.2s;
  }
  .skill-group:hover { transform: translateY(-3px); }
  .skill-group h5 {
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.68rem;
    letter-spacing: 0.14em;
    color: var(--mint);
    text-transform: uppercase;
    margin-bottom: 10px;
  }
  .tags { display: flex; flex-wrap: wrap; gap: 6px; }
  .tag {
    font-size: 0.74rem;
    padding: 3px 10px;
    border-radius: 50px;
    background: rgba(79,255,160,0.1);
    border: 1px solid rgba(79,255,160,0.2);
    color: var(--mint);
    font-family: 'JetBrains Mono', monospace;
  }

  /* ── SKILL BARS ──────────────────────────────────── */
  .bar-list { display: flex; flex-direction: column; gap: 14px; }
  .bar-item {}
  .bar-meta { display: flex; justify-content: space-between; font-size: 0.82rem; margin-bottom: 6px; }
  .bar-meta span:last-child { color: var(--mint); font-family: 'JetBrains Mono', monospace; font-size: 0.75rem; }
  .bar-track {
    height: 6px;
    background: rgba(255,255,255,0.07);
    border-radius: 50px;
    overflow: hidden;
  }
  .bar-fill {
    height: 100%;
    border-radius: 50px;
    background: linear-gradient(90deg, var(--forest-lt), var(--mint));
    width: 0;
    transition: width 1.2s cubic-bezier(0.4,0,0.2,1);
  }

  /* ── EXPERIENCE TIMELINE ─────────────────────────── */
  .timeline { position: relative; padding-left: 28px; }
  .timeline::before {
    content: '';
    position: absolute;
    left: 7px; top: 8px; bottom: 8px;
    width: 2px;
    background: linear-gradient(180deg, var(--mint) 0%, var(--forest-lt) 100%);
    border-radius: 2px;
  }
  .tl-item { position: relative; margin-bottom: 30px; }
  .tl-item::before {
    content: '';
    position: absolute;
    left: -24px; top: 6px;
    width: 10px; height: 10px;
    border-radius: 50%;
    background: var(--mint);
    box-shadow: 0 0 0 3px rgba(79,255,160,0.2);
  }
  .tl-date {
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.7rem;
    letter-spacing: 0.1em;
    color: var(--mint);
    margin-bottom: 4px;
  }
  .tl-role { font-size: 1rem; font-weight: 600; margin-bottom: 2px; }
  .tl-org { font-size: 0.82rem; color: rgba(240,249,244,0.55); margin-bottom: 6px; }
  .tl-desc { font-size: 0.82rem; color: rgba(240,249,244,0.7); line-height: 1.6; }

  /* ── PROJECTS ────────────────────────────────────── */
  .projects-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 18px;
  }
  @media(max-width:600px){ .projects-grid { grid-template-columns: 1fr; } }

  .project-card {
    background: var(--glass);
    border: 1px solid var(--glass-border);
    border-radius: 16px;
    padding: 24px;
    backdrop-filter: blur(10px);
    position: relative;
    overflow: hidden;
    transition: transform 0.25s, box-shadow 0.25s;
    text-decoration: none;
    color: inherit;
    display: block;
  }
  .project-card::before {
    content: '';
    position: absolute;
    inset: 0;
    background: radial-gradient(circle at top right, rgba(79,255,160,0.07), transparent 60%);
    pointer-events: none;
  }
  .project-card:hover {
    transform: translateY(-5px);
    box-shadow: 0 20px 50px rgba(79,255,160,0.14);
    border-color: rgba(79,255,160,0.38);
  }
  .project-card h4 { font-size: 1.05rem; font-weight: 700; margin-bottom: 8px; }
  .project-card p { font-size: 0.81rem; color: rgba(240,249,244,0.65); line-height: 1.6; margin-bottom: 14px; }
  .project-techs { display: flex; flex-wrap: wrap; gap: 6px; }
  .project-techs span {
    font-size: 0.68rem;
    font-family: 'JetBrains Mono', monospace;
    padding: 2px 9px;
    border-radius: 4px;
    background: rgba(20,69,47,0.8);
    border: 1px solid rgba(79,255,160,0.15);
    color: var(--mint-dim);
  }
  .project-arrow {
    position: absolute;
    top: 22px; right: 22px;
    font-size: 1.1rem;
    opacity: 0.4;
    transition: opacity 0.2s, transform 0.2s;
  }
  .project-card:hover .project-arrow { opacity: 1; transform: translate(3px,-3px); }

  /* ── STATS ───────────────────────────────────────── */
  .stats-row {
    display: flex;
    gap: 16px;
    flex-wrap: wrap;
  }
  .stat-box {
    flex: 1;
    min-width: 150px;
    background: var(--glass);
    border: 1px solid var(--glass-border);
    border-radius: 14px;
    padding: 24px;
    text-align: center;
    backdrop-filter: blur(10px);
  }
  .stat-box .num {
    font-size: 2.2rem;
    font-weight: 700;
    background: linear-gradient(135deg, var(--cream), var(--mint));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
  }
  .stat-box .lbl { font-size: 0.76rem; color: rgba(240,249,244,0.5); margin-top: 4px; letter-spacing: 0.06em; }

  /* ── CERTS ───────────────────────────────────────── */
  .cert-list { display: flex; flex-direction: column; gap: 10px; }
  .cert-item {
    display: flex;
    align-items: center;
    gap: 14px;
    background: var(--glass);
    border: 1px solid var(--glass-border);
    border-radius: 10px;
    padding: 14px 18px;
    font-size: 0.85rem;
    backdrop-filter: blur(8px);
    transition: transform 0.2s;
  }
  .cert-item:hover { transform: translateX(5px); }
  .cert-dot {
    width: 8px; height: 8px;
    border-radius: 50%;
    background: var(--mint);
    flex-shrink: 0;
  }

  /* ── CONTACT ─────────────────────────────────────── */
  .contact-wrap {
    background: var(--glass);
    border: 1px solid var(--glass-border);
    border-radius: 20px;
    padding: 40px;
    text-align: center;
    backdrop-filter: blur(12px);
    position: relative;
    overflow: hidden;
  }
  .contact-wrap::before {
    content: '';
    position: absolute;
    top: -60px; left: 50%; transform: translateX(-50%);
    width: 300px; height: 300px;
    background: radial-gradient(circle, rgba(79,255,160,0.08) 0%, transparent 70%);
    pointer-events: none;
  }
  .contact-wrap h3 { font-size: 1.6rem; margin-bottom: 10px; }
  .contact-wrap p { font-size: 0.88rem; color: rgba(240,249,244,0.6); margin-bottom: 28px; }
  .contact-links { display: flex; gap: 12px; justify-content: center; flex-wrap: wrap; }

  /* ── FOOTER ──────────────────────────────────────── */
  .footer {
    text-align: center;
    margin-top: 60px;
    font-size: 0.75rem;
    color: rgba(240,249,244,0.3);
    font-family: 'JetBrains Mono', monospace;
  }

  /* ── SCROLL REVEAL ───────────────────────────────── */
  .reveal {
    opacity: 0;
    transform: translateY(30px);
    transition: opacity 0.7s ease, transform 0.7s ease;
  }
  .reveal.visible {
    opacity: 1;
    transform: none;
  }

  /* ── KEYFRAMES ───────────────────────────────────── */
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(20px); }
    to   { opacity: 1; transform: translateY(0); }
  }
  @keyframes blink {
    0%,100% { opacity: 1; }
    50%      { opacity: 0; }
  }
  @keyframes pulse-ring {
    0%   { transform: scale(0.9); box-shadow: 0 0 0 0 rgba(79,255,160,0.4); }
    70%  { transform: scale(1);   box-shadow: 0 0 0 14px rgba(79,255,160,0); }
    100% { transform: scale(0.9); box-shadow: 0 0 0 0 rgba(79,255,160,0); }
  }

  /* ── AVATAR RING ─────────────────────────────────── */
  .avatar-ring {
    width: 90px; height: 90px;
    border-radius: 50%;
    background: linear-gradient(135deg, var(--forest-lt), var(--mint));
    display: flex; align-items: center; justify-content: center;
    margin: 0 auto 22px;
    font-size: 2.2rem;
    animation: pulse-ring 2.4s infinite;
  }

  /* ─── GLITCH TEXT ──────────────────────────────── */
  .glitch {
    position: relative;
    display: inline-block;
  }
  .glitch::before,
  .glitch::after {
    content: attr(data-text);
    position: absolute;
    top: 0; left: 0;
    background: linear-gradient(135deg, var(--cream) 0%, var(--mint) 60%, var(--mint-dim) 100%);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
  }
  .glitch::before {
    animation: glitch1 3.5s infinite;
    clip-path: polygon(0 0,100% 0,100% 35%,0 35%);
  }
  .glitch::after {
    animation: glitch2 3.5s infinite;
    clip-path: polygon(0 65%,100% 65%,100% 100%,0 100%);
  }
  @keyframes glitch1 {
    0%,92%,100% { transform: none; opacity: 0; }
    93%          { transform: translateX(-3px); opacity: 0.7; }
    95%          { transform: translateX(3px); opacity: 0.7; }
    97%          { transform: none; opacity: 0; }
  }
  @keyframes glitch2 {
    0%,92%,100% { transform: none; opacity: 0; }
    94%          { transform: translateX(3px); opacity: 0.7; }
    96%          { transform: translateX(-3px); opacity: 0.7; }
    98%          { transform: none; opacity: 0; }
  }
</style>
</head>
<body>

<canvas id="canvas"></canvas>

<div class="page">

  <!-- ── HERO ── -->
  <section class="hero">
    <div class="avatar-ring">👨‍💻</div>
    <div class="hero__badge">// SOFTWARE ENGINEER · FULL STACK · AI</div>
    <h1 class="hero__name">
      <span class="glitch" data-text="Kiran Sagar D S">Kiran Sagar D S</span>
    </h1>
    <p class="hero__title">B.E. Computer Science of Technology · SNS College of Engineering · 2026</p>
    <div class="hero__typing">
      <span id="typed-text"></span><span class="cursor"></span>
    </div>
    <div class="hero__links">
      <a class="btn btn--primary" href="https://www.linkedin.com/in/kiransagards11" target="_blank">
        🔗 LinkedIn
      </a>
      <a class="btn btn--ghost" href="https://github.com/KiranSagar115" target="_blank">
        🐙 GitHub
      </a>
      <a class="btn btn--ghost" href="mailto:kiransagards1105@gmail.com">
        ✉️ Email
      </a>
    </div>
  </section>

  <div class="divider"></div>

  <!-- ── STATS ── -->
  <section class="reveal">
    <div class="stats-row">
      <div class="stat-box">
        <div class="num" data-target="8.1">0</div>
        <div class="lbl">CGPA</div>
      </div>
      <div class="stat-box">
        <div class="num" data-target="3">0</div>
        <div class="lbl">INTERNSHIPS</div>
      </div>
      <div class="stat-box">
        <div class="num" data-target="3">0</div>
        <div class="lbl">LIVE PROJECTS</div>
      </div>
      <div class="stat-box">
        <div class="num" data-target="2">0</div>
        <div class="lbl">PUBLICATIONS</div>
      </div>
    </div>
  </section>

  <div class="divider"></div>

  <!-- ── ABOUT ── -->
  <section class="reveal">
    <div class="sec-label">// 01 · ABOUT</div>
    <h2 class="sec-title">Who Am I?</h2>
    <div class="about-grid">
      <div class="about-card">
        <div class="icon">🤖</div>
        <h4>AI & Full-Stack Developer</h4>
        <p>Building AI-powered apps using RAG, OLLAMA models, prompt engineering, and the MERN stack to solve real-world problems.</p>
      </div>
      <div class="about-card">
        <div class="icon">🧠</div>
        <h4>Problem Solver</h4>
        <p>Passionate about debugging complex systems and architecting clean, scalable solutions that combine intelligence with performance.</p>
      </div>
      <div class="about-card">
        <div class="icon">🔬</div>
        <h4>Published Researcher</h4>
        <p>Two peer-reviewed journal publications on AI-powered platforms – HRMS and the AIGENT learning ecosystem.</p>
      </div>
      <div class="about-card">
        <div class="icon">🌱</div>
        <h4>Continuous Learner</h4>
        <p>Certified in Azure AI, Python, Full-Stack, and Node.js. Always adapting to new AI tools and paradigms.</p>
      </div>
    </div>
  </section>

  <div class="divider"></div>

  <!-- ── SKILLS ── -->
  <section class="reveal">
    <div class="sec-label">// 02 · SKILLS</div>
    <h2 class="sec-title">Tech Arsenal</h2>

    <div class="skills-grid" style="margin-bottom:28px;">
      <div class="skill-group">
        <h5>Languages</h5>
        <div class="tags">
          <span class="tag">Python</span>
          <span class="tag">JavaScript</span>
        </div>
      </div>
      <div class="skill-group">
        <h5>Frontend</h5>
        <div class="tags">
          <span class="tag">React.js</span>
          <span class="tag">Vite</span>
          <span class="tag">Tailwind CSS</span>
          <span class="tag">HTML/CSS</span>
        </div>
      </div>
      <div class="skill-group">
        <h5>Backend & DB</h5>
        <div class="tags">
          <span class="tag">Node.js</span>
          <span class="tag">Express.js</span>
          <span class="tag">MongoDB</span>
        </div>
      </div>
      <div class="skill-group">
        <h5>AI & ML</h5>
        <div class="tags">
          <span class="tag">RAG</span>
          <span class="tag">OLLAMA</span>
          <span class="tag">Gemini AI</span>
          <span class="tag">DeepFace</span>
          <span class="tag">Prompt Eng.</span>
        </div>
      </div>
      <div class="skill-group">
        <h5>Tools</h5>
        <div class="tags">
          <span class="tag">Git</span>
          <span class="tag">GitHub</span>
          <span class="tag">Tavily</span>
          <span class="tag">Azure AI</span>
        </div>
      </div>
    </div>

    <div class="bar-list" id="skill-bars">
      <div class="bar-item">
        <div class="bar-meta"><span>Full-Stack Development</span><span>88%</span></div>
        <div class="bar-track"><div class="bar-fill" data-pct="88"></div></div>
      </div>
      <div class="bar-item">
        <div class="bar-meta"><span>Python & AI Tooling</span><span>85%</span></div>
        <div class="bar-track"><div class="bar-fill" data-pct="85"></div></div>
      </div>
      <div class="bar-item">
        <div class="bar-meta"><span>React.js / Frontend</span><span>82%</span></div>
        <div class="bar-track"><div class="bar-fill" data-pct="82"></div></div>
      </div>
      <div class="bar-item">
        <div class="bar-meta"><span>Prompt Engineering & RAG</span><span>80%</span></div>
        <div class="bar-track"><div class="bar-fill" data-pct="80"></div></div>
      </div>
      <div class="bar-item">
        <div class="bar-meta"><span>Node.js / Express</span><span>78%</span></div>
        <div class="bar-track"><div class="bar-fill" data-pct="78"></div></div>
      </div>
    </div>
  </section>

  <div class="divider"></div>

  <!-- ── EXPERIENCE ── -->
  <section class="reveal">
    <div class="sec-label">// 03 · EXPERIENCE</div>
    <h2 class="sec-title">Work Timeline</h2>
    <div class="timeline">
      <div class="tl-item">
        <div class="tl-date">AUG 2024 – JULY 2025</div>
        <div class="tl-role">Full Stack Development Intern</div>
        <div class="tl-org">SNS iHub</div>
        <div class="tl-desc">Built full-stack applications on MERN stack and integrated AI features hands-on. Longest and most impactful internship—delivered production-grade projects.</div>
      </div>
      <div class="tl-item">
        <div class="tl-date">JULY 2024</div>
        <div class="tl-role">Frontend Development Intern</div>
        <div class="tl-org">Hitshoppers</div>
        <div class="tl-desc">Developed responsive UI components using HTML, CSS, JavaScript and React for real-world e-commerce interfaces.</div>
      </div>
      <div class="tl-item">
        <div class="tl-date">JUNE 2024</div>
        <div class="tl-role">Python Programming Intern</div>
        <div class="tl-org">InternPE</div>
        <div class="tl-desc">Learned core Python concepts and built logic-based programs to sharpen algorithmic thinking and scripting fundamentals.</div>
      </div>
    </div>
  </section>

  <div class="divider"></div>

  <!-- ── PROJECTS ── -->
  <section class="reveal">
    <div class="sec-label">// 04 · PROJECTS</div>
    <h2 class="sec-title">What I've Built</h2>
    <div class="projects-grid">

      <a class="project-card" 
        <span class="project-arrow">↗</span>
        <h4>ImparaCode AI</h4>
        <p>AI-powered coding mentor with Chat (doubt solving), Learn (topic-wise content) and Code Debug modules. Built with React, Node.js & Gemini AI.</p>
        <div class="project-techs">
          <span>React</span><span>Node.js</span><span>Gemini AI</span><span>Vite</span>
        </div>
      </a>

      <div class="project-card">
        <span class="project-arrow">↗</span>
        <h4>AI-Powered HRMS</h4>
        <p>Face recognition–based attendance system using DeepFace and webcam capture with real-time AI face matching and automated punch in/out.</p>
        <div class="project-techs">
          <span>DeepFace</span><span>MongoDB</span><span>React</span><span>Vite</span>
        </div>
      </div>

      <div class="project-card">
        <span class="project-arrow">↗</span>
        <h4>Placement Preparator Agent</h4>
        <p>AI assistant fetching recent placement questions customized by company, experience level, and interview round (HR / Technical / Coding).</p>
        <div class="project-techs">
          <span>Tavily</span><span>Gemini</span><span>Python</span><span>RAG</span>
        </div>
      </div>

    </div>
  </section>

  <div class="divider"></div>

  <!-- ── CERTIFICATIONS ── -->
  <section class="reveal">
    <div class="sec-label">// 05 · CERTIFICATIONS</div>
    <h2 class="sec-title">Credentials</h2>
    <div class="cert-list">
      <div class="cert-item"><div class="cert-dot"></div>Azure AI Fundamentals – Microsoft</div>
      <div class="cert-item"><div class="cert-dot"></div>Python – Kaggle & PrepInsta</div>
      <div class="cert-item"><div class="cert-dot"></div>Full-Stack Bootcamp – Board Infinity</div>
      <div class="cert-item"><div class="cert-dot"></div>Node.js – PrepInsta</div>
      <div class="cert-item"><div class="cert-dot"></div>NASSCOM – DAF</div>
      <div class="cert-item"><div class="cert-dot"></div>HackNext Series 2 – 30 Hr Continuous Hackathon (Conducted)</div>
    </div>
  </section>

  <div class="divider"></div>

  <!-- ── CONTACT ── -->
  <section class="reveal">
    <div class="contact-wrap">
      <h3>Let's Build Something Intelligent 🚀</h3>
      <p>Open to full-time roles, collaborations, and AI research projects.</p>
      <div class="contact-links">
        <a class="btn btn--primary" href="mailto:kiransagards1105@gmail.com">✉️ kiransagards1105@gmail.com</a>
        
      </div>
    </div>
  </section>

  <div class="footer">
    <p>© 2026 Kiran Sagar D S &nbsp;·&nbsp; crafted with 💚 &nbsp;·&nbsp; <span style="color:var(--mint);">#14452F</span></p>
  </div>

</div>

<script>
/* ── PARTICLE SYSTEM ─────────────────────────────────── */
const canvas = document.getElementById('canvas');
const ctx = canvas.getContext('2d');
let W, H, particles = [];

function resize() {
  W = canvas.width  = window.innerWidth;
  H = canvas.height = window.innerHeight;
}
resize();
window.addEventListener('resize', resize);

function Particle() {
  this.reset();
}
Particle.prototype.reset = function() {
  this.x  = Math.random() * W;
  this.y  = Math.random() * H;
  this.r  = Math.random() * 1.4 + 0.3;
  this.vx = (Math.random() - 0.5) * 0.4;
  this.vy = (Math.random() - 0.5) * 0.4;
  this.a  = Math.random() * 0.45 + 0.05;
};
Particle.prototype.update = function() {
  this.x += this.vx;
  this.y += this.vy;
  if (this.x < 0 || this.x > W || this.y < 0 || this.y > H) this.reset();
};

for (let i = 0; i < 80; i++) particles.push(new Particle());

function drawParticles() {
  ctx.clearRect(0, 0, W, H);
  particles.forEach(p => {
    p.update();
    ctx.beginPath();
    ctx.arc(p.x, p.y, p.r, 0, Math.PI * 2);
    ctx.fillStyle = `rgba(79,255,160,${p.a})`;
    ctx.fill();
  });
  // connect close particles
  for (let i = 0; i < particles.length; i++) {
    for (let j = i+1; j < particles.length; j++) {
      const dx = particles[i].x - particles[j].x;
      const dy = particles[i].y - particles[j].y;
      const d  = Math.sqrt(dx*dx + dy*dy);
      if (d < 100) {
        ctx.beginPath();
        ctx.moveTo(particles[i].x, particles[i].y);
        ctx.lineTo(particles[j].x, particles[j].y);
        ctx.strokeStyle = `rgba(79,255,160,${0.08 * (1 - d/100)})`;
        ctx.lineWidth = 0.6;
        ctx.stroke();
      }
    }
  }
  requestAnimationFrame(drawParticles);
}
drawParticles();

/* ── TYPING ANIMATION ────────────────────────────────── */
const phrases = [
  'Full-Stack Developer 🔧',
  'AI Agent Builder 🤖',
  'React Enthusiast ⚛️',
  'Problem Solver 🧠',
  'MERN Stack Dev 🌿',
];
let pi = 0, ci = 0, deleting = false;
const typedEl = document.getElementById('typed-text');

function type() {
  const phrase = phrases[pi];
  if (!deleting) {
    typedEl.textContent = phrase.slice(0, ++ci);
    if (ci === phrase.length) { deleting = true; setTimeout(type, 1800); return; }
  } else {
    typedEl.textContent = phrase.slice(0, --ci);
    if (ci === 0) { deleting = false; pi = (pi+1) % phrases.length; }
  }
  setTimeout(type, deleting ? 45 : 80);
}
type();

/* ── SCROLL REVEAL ───────────────────────────────────── */
const reveals = document.querySelectorAll('.reveal');
const io = new IntersectionObserver((entries) => {
  entries.forEach(e => { if (e.isIntersecting) { e.target.classList.add('visible'); io.unobserve(e.target); } });
}, { threshold: 0.12 });
reveals.forEach(el => io.observe(el));

/* ── COUNTER ANIMATION ───────────────────────────────── */
const counterIO = new IntersectionObserver((entries) => {
  entries.forEach(e => {
    if (e.isIntersecting) {
      e.target.querySelectorAll('.num').forEach(el => {
        const target = parseFloat(el.dataset.target);
        const isFloat = target % 1 !== 0;
        let start = 0, duration = 1200, step = 16;
        const inc = target / (duration / step);
        const timer = setInterval(() => {
          start = Math.min(start + inc, target);
          el.textContent = isFloat ? start.toFixed(1) : Math.floor(start);
          if (start >= target) clearInterval(timer);
        }, step);
      });
      counterIO.unobserve(e.target);
    }
  });
}, { threshold: 0.3 });
document.querySelectorAll('.stats-row').forEach(el => counterIO.observe(el.closest('.reveal') || el));

/* ── SKILL BAR ANIMATION ─────────────────────────────── */
const barIO = new IntersectionObserver((entries) => {
  entries.forEach(e => {
    if (e.isIntersecting) {
      e.target.querySelectorAll('.bar-fill').forEach((bar, i) => {
        setTimeout(() => { bar.style.width = bar.dataset.pct + '%'; }, i * 120);
      });
      barIO.unobserve(e.target);
    }
  });
}, { threshold: 0.3 });
document.querySelectorAll('#skill-bars').forEach(el => {
  const section = el.closest('.reveal') || el;
  barIO.observe(section);
});
</script>
</body>
</html>
