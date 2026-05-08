[index.html](https://github.com/user-attachments/files/27508652/index.html)
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Aravindh.A — Graphic Designer</title>
<link href="https://fonts.googleapis.com/css2?family=Bebas+Neue&family=DM+Sans:ital,wght@0,300;0,400;0,500;1,300&family=Space+Mono:wght@400;700&display=swap" rel="stylesheet">
<style>
  :root {
    --black: #0a0a0a;
    --white: #f5f0e8;
    --cream: #ede8dd;
    --accent: #ff4d00;
    --accent2: #ffb800;
    --gray: #1a1a1a;
    --mid: #333;
    --muted: #888;
  }

  *, *::before, *::after { margin: 0; padding: 0; box-sizing: border-box; }

  html { scroll-behavior: smooth; }

  body {
    background: var(--black);
    color: var(--white);
    font-family: 'DM Sans', sans-serif;
    overflow-x: hidden;
    cursor: none;
  }

  /* Custom Cursor */
  .cursor {
    position: fixed;
    width: 12px; height: 12px;
    background: var(--accent);
    border-radius: 50%;
    pointer-events: none;
    z-index: 9999;
    transform: translate(-50%, -50%);
    transition: transform 0.1s, width 0.2s, height 0.2s, background 0.2s;
    mix-blend-mode: difference;
  }
  .cursor-ring {
    position: fixed;
    width: 40px; height: 40px;
    border: 1.5px solid rgba(255,77,0,0.5);
    border-radius: 50%;
    pointer-events: none;
    z-index: 9998;
    transform: translate(-50%, -50%);
    transition: transform 0.15s ease, width 0.3s, height 0.3s;
  }
  body:hover .cursor { opacity: 1; }

  /* Noise overlay */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)' opacity='0.04'/%3E%3C/svg%3E");
    pointer-events: none;
    z-index: 9000;
    opacity: 0.4;
  }

  /* NAV */
  nav {
    position: fixed; top: 0; left: 0; right: 0;
    z-index: 100;
    display: flex; align-items: center; justify-content: space-between;
    padding: 24px 60px;
    mix-blend-mode: normal;
  }
  nav::before {
    content: '';
    position: absolute; inset: 0;
    background: linear-gradient(to bottom, rgba(10,10,10,0.95) 0%, transparent 100%);
    pointer-events: none;
  }
  .nav-logo {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 28px;
    letter-spacing: 4px;
    color: var(--white);
    text-decoration: none;
    position: relative;
  }
  .nav-logo span { color: var(--accent); }
  .nav-links { display: flex; gap: 40px; position: relative; }
  .nav-links a {
    font-family: 'Space Mono', monospace;
    font-size: 11px;
    letter-spacing: 2px;
    text-transform: uppercase;
    color: var(--muted);
    text-decoration: none;
    transition: color 0.3s;
    position: relative;
  }
  .nav-links a::after {
    content: '';
    position: absolute; bottom: -4px; left: 0;
    width: 0; height: 1px;
    background: var(--accent);
    transition: width 0.3s;
  }
  .nav-links a:hover { color: var(--white); }
  .nav-links a:hover::after { width: 100%; }

  /* HERO */
  #hero {
    min-height: 100vh;
    display: flex; flex-direction: column;
    justify-content: center;
    padding: 140px 60px 80px;
    position: relative;
    overflow: hidden;
  }
  .hero-bg-text {
    position: absolute;
    top: 50%; left: 50%;
    transform: translate(-50%, -50%);
    font-family: 'Bebas Neue', sans-serif;
    font-size: clamp(120px, 18vw, 260px);
    color: transparent;
    -webkit-text-stroke: 1px rgba(255,255,255,0.03);
    white-space: nowrap;
    pointer-events: none;
    user-select: none;
    animation: bgDrift 20s ease-in-out infinite alternate;
  }
  @keyframes bgDrift {
    from { transform: translate(-50%, -50%) scale(1); }
    to   { transform: translate(-50%, -48%) scale(1.03); }
  }
  .hero-tag {
    font-family: 'Space Mono', monospace;
    font-size: 11px;
    letter-spacing: 4px;
    color: var(--accent);
    text-transform: uppercase;
    margin-bottom: 24px;
    display: flex; align-items: center; gap: 12px;
    opacity: 0; animation: fadeUp 0.8s 0.3s forwards;
  }
  .hero-tag::before {
    content: '';
    width: 40px; height: 1px;
    background: var(--accent);
  }
  .hero-title {
    font-family: 'Bebas Neue', sans-serif;
    font-size: clamp(72px, 10vw, 150px);
    line-height: 0.9;
    letter-spacing: 2px;
    position: relative;
    opacity: 0; animation: fadeUp 0.8s 0.5s forwards;
  }
  .hero-title .line2 {
    color: transparent;
    -webkit-text-stroke: 1.5px var(--white);
  }
  .hero-title .accent-word { color: var(--accent); }
  .hero-sub {
    margin-top: 40px;
    max-width: 480px;
    font-size: 16px;
    line-height: 1.7;
    color: #aaa;
    font-weight: 300;
    opacity: 0; animation: fadeUp 0.8s 0.7s forwards;
  }
  .hero-cta {
    margin-top: 48px;
    display: flex; gap: 20px; align-items: center;
    opacity: 0; animation: fadeUp 0.8s 0.9s forwards;
  }
  .btn-primary {
    background: var(--accent);
    color: #fff;
    padding: 16px 40px;
    font-family: 'Space Mono', monospace;
    font-size: 12px;
    letter-spacing: 2px;
    text-transform: uppercase;
    text-decoration: none;
    border: none; cursor: none;
    position: relative;
    overflow: hidden;
    display: inline-block;
    transition: transform 0.3s;
  }
  .btn-primary::before {
    content: '';
    position: absolute; inset: 0;
    background: var(--accent2);
    transform: translateX(-100%);
    transition: transform 0.4s cubic-bezier(0.77,0,0.175,1);
  }
  .btn-primary:hover::before { transform: translateX(0); }
  .btn-primary span { position: relative; z-index: 1; }
  .btn-outline {
    font-family: 'Space Mono', monospace;
    font-size: 12px;
    letter-spacing: 2px;
    text-transform: uppercase;
    text-decoration: none;
    color: var(--muted);
    display: flex; align-items: center; gap: 8px;
    transition: color 0.3s;
  }
  .btn-outline:hover { color: var(--white); }
  .btn-outline::after { content: '→'; transition: transform 0.3s; }
  .btn-outline:hover::after { transform: translateX(6px); }

  .hero-stats {
    position: absolute; right: 60px; bottom: 80px;
    display: flex; flex-direction: column; gap: 32px;
    opacity: 0; animation: fadeUp 0.8s 1.1s forwards;
  }
  .stat { text-align: right; }
  .stat-num {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 52px;
    color: var(--white);
    line-height: 1;
  }
  .stat-num span { color: var(--accent); }
  .stat-label {
    font-family: 'Space Mono', monospace;
    font-size: 10px;
    letter-spacing: 2px;
    text-transform: uppercase;
    color: var(--muted);
  }

  /* Marquee */
  .marquee-wrap {
    overflow: hidden;
    border-top: 1px solid #222;
    border-bottom: 1px solid #222;
    padding: 16px 0;
    background: var(--gray);
  }
  .marquee-track {
    display: flex; gap: 60px;
    animation: marquee 20s linear infinite;
    width: max-content;
  }
  .marquee-item {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 22px;
    letter-spacing: 4px;
    color: var(--muted);
    white-space: nowrap;
    display: flex; align-items: center; gap: 60px;
  }
  .marquee-item .dot {
    width: 6px; height: 6px;
    background: var(--accent);
    border-radius: 50%;
  }
  @keyframes marquee {
    from { transform: translateX(0); }
    to   { transform: translateX(-50%); }
  }

  /* SECTIONS */
  section { padding: 120px 60px; }
  .section-label {
    font-family: 'Space Mono', monospace;
    font-size: 11px;
    letter-spacing: 4px;
    text-transform: uppercase;
    color: var(--accent);
    margin-bottom: 16px;
    display: flex; align-items: center; gap: 12px;
  }
  .section-label::before {
    content: '';
    width: 30px; height: 1px;
    background: var(--accent);
  }
  .section-title {
    font-family: 'Bebas Neue', sans-serif;
    font-size: clamp(48px, 6vw, 80px);
    line-height: 1;
    letter-spacing: 1px;
  }

  /* ABOUT */
  #about { background: var(--gray); }
  .about-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 80px;
    margin-top: 60px;
    align-items: start;
  }
  .about-text p {
    font-size: 16px;
    line-height: 1.8;
    color: #bbb;
    margin-bottom: 20px;
    font-weight: 300;
  }
  .about-text p strong { color: var(--white); font-weight: 500; }
  .about-visual {
    position: relative;
  }
  .about-card {
    background: #111;
    border: 1px solid #2a2a2a;
    padding: 32px;
    position: relative;
    overflow: hidden;
  }
  .about-card::before {
    content: '';
    position: absolute; top: 0; left: 0;
    width: 4px; height: 100%;
    background: var(--accent);
  }
  .about-card-title {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 14px;
    letter-spacing: 3px;
    color: var(--muted);
    text-transform: uppercase;
    margin-bottom: 20px;
  }
  .tag-list {
    display: flex; flex-wrap: wrap; gap: 10px;
  }
  .tag {
    font-family: 'Space Mono', monospace;
    font-size: 11px;
    padding: 6px 14px;
    border: 1px solid #333;
    color: var(--muted);
    letter-spacing: 1px;
    transition: all 0.3s;
  }
  .tag:hover { border-color: var(--accent); color: var(--white); }

  /* SKILLS */
  #skills { background: var(--black); }
  .skills-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 2px;
    margin-top: 60px;
  }
  .skill-block {
    background: var(--gray);
    padding: 40px 32px;
    position: relative;
    overflow: hidden;
    transition: background 0.3s;
    group: true;
  }
  .skill-block::after {
    content: '';
    position: absolute;
    bottom: 0; left: 0;
    height: 3px; width: 0;
    background: var(--accent);
    transition: width 0.4s cubic-bezier(0.77,0,0.175,1);
  }
  .skill-block:hover::after { width: 100%; }
  .skill-block:hover { background: #1f1f1f; }
  .skill-icon {
    font-size: 32px; margin-bottom: 16px;
    display: block;
  }
  .skill-name {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 26px;
    letter-spacing: 2px;
    margin-bottom: 8px;
    color: var(--white);
  }
  .skill-desc {
    font-size: 13px;
    line-height: 1.6;
    color: var(--muted);
  }
  .skill-level {
    margin-top: 20px;
    height: 2px;
    background: #2a2a2a;
    position: relative;
    overflow: hidden;
  }
  .skill-fill {
    position: absolute; left: 0; top: 0; height: 100%;
    background: linear-gradient(to right, var(--accent), var(--accent2));
    width: 0;
    transition: width 1.2s cubic-bezier(0.77,0,0.175,1);
  }

  /* VIDEO SKILLS HIGHLIGHT */
  #video-skills {
    background: var(--accent);
    padding: 80px 60px;
  }
  .video-inner {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 80px;
    align-items: center;
  }
  .video-text .section-label { color: var(--black); }
  .video-text .section-label::before { background: var(--black); }
  .video-text .section-title { color: var(--black); }
  .video-text p {
    margin-top: 24px;
    font-size: 16px;
    line-height: 1.8;
    color: rgba(0,0,0,0.75);
  }
  .video-tools {
    display: flex; flex-direction: column; gap: 20px;
  }
  .tool-row {
    display: flex; align-items: center; gap: 20px;
  }
  .tool-name {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 22px;
    letter-spacing: 2px;
    color: var(--black);
    min-width: 200px;
  }
  .tool-bar {
    flex: 1;
    height: 4px;
    background: rgba(0,0,0,0.2);
    position: relative;
    overflow: hidden;
  }
  .tool-fill {
    position: absolute; left: 0; top: 0; height: 100%;
    background: var(--black);
    width: 0;
    transition: width 1.2s cubic-bezier(0.77,0,0.175,1);
  }
  .tool-pct {
    font-family: 'Space Mono', monospace;
    font-size: 12px;
    color: var(--black);
    min-width: 40px;
    text-align: right;
  }

  /* EXPERIENCE */
  #experience { background: var(--gray); }
  .exp-timeline {
    margin-top: 60px;
    position: relative;
  }
  .exp-timeline::before {
    content: '';
    position: absolute;
    left: 0; top: 0; bottom: 0;
    width: 1px;
    background: linear-gradient(to bottom, var(--accent), transparent);
  }
  .exp-item {
    padding-left: 40px;
    padding-bottom: 56px;
    position: relative;
    opacity: 0;
    transform: translateX(-20px);
    transition: opacity 0.6s, transform 0.6s;
  }
  .exp-item.visible {
    opacity: 1;
    transform: translateX(0);
  }
  .exp-item::before {
    content: '';
    position: absolute;
    left: -5px; top: 6px;
    width: 11px; height: 11px;
    background: var(--accent);
    border-radius: 50%;
    border: 2px solid var(--gray);
  }
  .exp-date {
    font-family: 'Space Mono', monospace;
    font-size: 11px;
    letter-spacing: 2px;
    color: var(--accent);
    text-transform: uppercase;
    margin-bottom: 8px;
  }
  .exp-role {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 32px;
    letter-spacing: 1px;
    color: var(--white);
    line-height: 1;
    margin-bottom: 4px;
  }
  .exp-company {
    font-size: 14px;
    color: var(--muted);
    margin-bottom: 12px;
  }
  .exp-desc {
    font-size: 14px;
    line-height: 1.7;
    color: #888;
    max-width: 560px;
  }
  .current-badge {
    display: inline-block;
    background: var(--accent);
    color: #fff;
    font-family: 'Space Mono', monospace;
    font-size: 9px;
    letter-spacing: 2px;
    padding: 4px 10px;
    text-transform: uppercase;
    margin-left: 12px;
    vertical-align: middle;
    animation: pulse 2s ease-in-out infinite;
  }
  @keyframes pulse {
    0%, 100% { opacity: 1; }
    50%       { opacity: 0.6; }
  }

  /* WORKS */
  #works { background: var(--black); }
  .works-grid {
    margin-top: 60px;
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 2px;
  }
  .work-item {
    position: relative;
    aspect-ratio: 4/3;
    background: var(--gray);
    overflow: hidden;
    cursor: none;
  }
  .work-item:first-child {
    grid-column: span 2;
    aspect-ratio: unset;
  }
  .work-bg {
    position: absolute; inset: 0;
    display: flex; align-items: center; justify-content: center;
    font-family: 'Bebas Neue', sans-serif;
    font-size: 80px;
    letter-spacing: -2px;
    color: rgba(255,255,255,0.03);
    transition: transform 0.6s ease, color 0.4s;
  }
  .work-item:hover .work-bg {
    transform: scale(1.1);
    color: rgba(255,77,0,0.05);
  }
  .work-overlay {
    position: absolute; inset: 0;
    background: linear-gradient(to top, rgba(0,0,0,0.9) 0%, transparent 60%);
    display: flex; flex-direction: column; justify-content: flex-end;
    padding: 32px;
    transform: translateY(20px);
    opacity: 0;
    transition: all 0.4s ease;
  }
  .work-item:hover .work-overlay {
    transform: translateY(0);
    opacity: 1;
  }
  .work-cat {
    font-family: 'Space Mono', monospace;
    font-size: 10px;
    letter-spacing: 3px;
    color: var(--accent);
    text-transform: uppercase;
    margin-bottom: 8px;
  }
  .work-title {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 28px;
    letter-spacing: 1px;
    color: var(--white);
  }
  .work-gradient {
    position: absolute; inset: 0;
    opacity: 0.4;
    transition: opacity 0.4s;
  }
  .work-item:hover .work-gradient { opacity: 0.6; }

  /* CONTACT */
  #contact {
    background: var(--black);
    border-top: 1px solid #1a1a1a;
  }
  .contact-inner {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 80px;
    align-items: start;
  }
  .contact-big {
    font-family: 'Bebas Neue', sans-serif;
    font-size: clamp(60px, 7vw, 100px);
    line-height: 0.95;
    letter-spacing: 2px;
    margin-top: 24px;
  }
  .contact-big span { color: var(--accent); }
  .contact-form { margin-top: 40px; display: flex; flex-direction: column; gap: 20px; }
  .form-group { display: flex; flex-direction: column; gap: 8px; }
  .form-label {
    font-family: 'Space Mono', monospace;
    font-size: 10px;
    letter-spacing: 3px;
    text-transform: uppercase;
    color: var(--muted);
  }
  .form-input, .form-textarea {
    background: var(--gray);
    border: 1px solid #2a2a2a;
    color: var(--white);
    font-family: 'DM Sans', sans-serif;
    font-size: 15px;
    padding: 14px 18px;
    outline: none;
    cursor: none;
    transition: border-color 0.3s;
    resize: none;
  }
  .form-input:focus, .form-textarea:focus { border-color: var(--accent); }
  .form-textarea { height: 120px; }
  .contact-info { margin-top: 48px; display: flex; flex-direction: column; gap: 24px; }
  .info-row {
    display: flex; flex-direction: column; gap: 4px;
    padding-bottom: 24px;
    border-bottom: 1px solid #1a1a1a;
  }
  .info-row:last-child { border-bottom: none; }
  .info-label {
    font-family: 'Space Mono', monospace;
    font-size: 10px;
    letter-spacing: 3px;
    color: var(--muted);
    text-transform: uppercase;
  }
  .info-val {
    font-size: 16px;
    color: var(--white);
  }

  /* FOOTER */
  footer {
    background: var(--gray);
    padding: 32px 60px;
    display: flex; align-items: center; justify-content: space-between;
    border-top: 1px solid #222;
  }
  .footer-logo {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 22px;
    letter-spacing: 4px;
    color: var(--white);
  }
  .footer-logo span { color: var(--accent); }
  .footer-copy {
    font-family: 'Space Mono', monospace;
    font-size: 10px;
    letter-spacing: 2px;
    color: var(--muted);
    text-transform: uppercase;
  }

  /* Scroll reveal */
  .reveal {
    opacity: 0;
    transform: translateY(30px);
    transition: opacity 0.7s, transform 0.7s;
  }
  .reveal.visible {
    opacity: 1;
    transform: translateY(0);
  }

  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(24px); }
    to   { opacity: 1; transform: translateY(0); }
  }

  /* Floating geometric shapes */
  .shape {
    position: absolute;
    pointer-events: none;
  }
  .shape-circle {
    width: 300px; height: 300px;
    border-radius: 50%;
    border: 1px solid rgba(255,77,0,0.06);
    right: 100px; top: 200px;
    animation: spin 40s linear infinite;
  }
  .shape-circle2 {
    width: 180px; height: 180px;
    border-radius: 50%;
    border: 1px solid rgba(255,184,0,0.08);
    right: 160px; top: 260px;
    animation: spin 25s linear infinite reverse;
  }
  @keyframes spin {
    from { transform: rotate(0deg); }
    to   { transform: rotate(360deg); }
  }

  /* Scroll indicator */
  .scroll-indicator {
    position: absolute; bottom: 48px; left: 60px;
    display: flex; align-items: center; gap: 12px;
    opacity: 0; animation: fadeUp 0.8s 1.3s forwards;
  }
  .scroll-line {
    width: 1px; height: 40px;
    background: linear-gradient(to bottom, var(--accent), transparent);
    animation: scrollAnim 2s ease-in-out infinite;
  }
  .scroll-text {
    font-family: 'Space Mono', monospace;
    font-size: 10px;
    letter-spacing: 3px;
    text-transform: uppercase;
    color: var(--muted);
    writing-mode: vertical-lr;
  }
  @keyframes scrollAnim {
    0%, 100% { transform: scaleY(1); opacity: 1; }
    50% { transform: scaleY(0.5); opacity: 0.5; }
  }

  /* MOBILE */
  @media (max-width: 768px) {
    nav, section, #video-skills, footer { padding-left: 24px; padding-right: 24px; }
    #hero { padding: 120px 24px 80px; }
    .about-grid, .video-inner, .contact-inner { grid-template-columns: 1fr; gap: 40px; }
    .skills-grid, .works-grid { grid-template-columns: 1fr; }
    .work-item:first-child { grid-column: span 1; aspect-ratio: 4/3; }
    .hero-stats { position: static; margin-top: 40px; flex-direction: row; gap: 40px; }
    .stat { text-align: left; }
    nav { padding: 20px 24px; }
    .nav-links { display: none; }
  }
</style>
</head>
<body>

<!-- Custom Cursor -->
<div class="cursor" id="cursor"></div>
<div class="cursor-ring" id="cursorRing"></div>

<!-- Navigation -->
<nav>
  <a href="#hero" class="nav-logo">ARAVINDH<span>.</span>A</a>
  <div class="nav-links">
    <a href="#about">About</a>
    <a href="#skills">Skills</a>
    <a href="#experience">Work</a>
    <a href="#works">Portfolio</a>
    <a href="#contact">Contact</a>
  </div>
</nav>

<!-- Hero -->
<section id="hero">
  <div class="shape shape-circle"></div>
  <div class="shape shape-circle2"></div>
  <div class="hero-bg-text">DESIGN</div>

  <div class="hero-tag">Available for Freelance</div>
  <h1 class="hero-title">
    CREATIVE<br>
    <span class="line2">GRAPHIC</span><br>
    <span class="accent-word">DESIGNER</span>
  </h1>
  <p class="hero-sub">
    Turning ideas into visually compelling experiences. 5+ years crafting brands, motion, and unforgettable visuals — from pixel to premiere.
  </p>
  <div class="hero-cta">
    <a href="#works" class="btn-primary"><span>View Portfolio</span></a>
    <a href="#contact" class="btn-outline">Let's Talk</a>
  </div>

  <div class="scroll-indicator">
    <div class="scroll-line"></div>
    <span class="scroll-text">Scroll</span>
  </div>

  <div class="hero-stats">
    <div class="stat">
      <div class="stat-num">5<span>+</span></div>
      <div class="stat-label">Years Experience</div>
    </div>
    <div class="stat">
      <div class="stat-num">4<span>+</span></div>
      <div class="stat-label">Companies</div>
    </div>
    <div class="stat">
      <div class="stat-num">10<span>+</span></div>
      <div class="stat-label">Tools Mastered</div>
    </div>
  </div>
</section>

<!-- Marquee -->
<div class="marquee-wrap">
  <div class="marquee-track">
    <div class="marquee-item">GRAPHIC DESIGN <span class="dot"></span></div>
    <div class="marquee-item">VIDEO EDITING <span class="dot"></span></div>
    <div class="marquee-item">MOTION GRAPHICS <span class="dot"></span></div>
    <div class="marquee-item">UI/UX DESIGN <span class="dot"></span></div>
    <div class="marquee-item">BRAND IDENTITY <span class="dot"></span></div>
    <div class="marquee-item">3D ANIMATION <span class="dot"></span></div>
    <div class="marquee-item">PRINT DESIGN <span class="dot"></span></div>
    <div class="marquee-item">VISUAL STORYTELLING <span class="dot"></span></div>
    <!-- repeat for seamless loop -->
    <div class="marquee-item">GRAPHIC DESIGN <span class="dot"></span></div>
    <div class="marquee-item">VIDEO EDITING <span class="dot"></span></div>
    <div class="marquee-item">MOTION GRAPHICS <span class="dot"></span></div>
    <div class="marquee-item">UI/UX DESIGN <span class="dot"></span></div>
    <div class="marquee-item">BRAND IDENTITY <span class="dot"></span></div>
    <div class="marquee-item">3D ANIMATION <span class="dot"></span></div>
    <div class="marquee-item">PRINT DESIGN <span class="dot"></span></div>
    <div class="marquee-item">VISUAL STORYTELLING <span class="dot"></span></div>
  </div>
</div>

<!-- About -->
<section id="about">
  <div class="section-label">Who I Am</div>
  <h2 class="section-title reveal">About Me</h2>
  <div class="about-grid">
    <div class="about-text reveal">
      <p>Creative professional who transitioned from <strong>Mechanical Engineering</strong> to graphic design — bringing technical precision to visual storytelling. My engineering background gives me a unique analytical edge in solving design problems.</p>
      <p>With <strong>5+ years of experience</strong> across Adobe Creative Suite and video production tools, I create work that's not just beautiful but strategically effective. Currently expanding into <strong>UI/UX design</strong> and <strong>3D animation</strong>.</p>
      <p>I thrive in collaborative environments, approach every challenge with logical thinking, and am driven by continuous learning and meaningful work.</p>
    </div>
    <div class="about-visual reveal">
      <div class="about-card" style="margin-bottom: 16px;">
        <div class="about-card-title">Education</div>
        <p style="color: var(--white); font-size: 15px; margin-bottom: 4px;">B.E. — Mechanical Engineering</p>
        <p style="color: var(--muted); font-size: 13px;">ST.Michael College of Engineering & Technology</p>
        <p style="color: var(--accent); font-family: 'Space Mono', monospace; font-size: 11px; margin-top: 8px;">2013 — 2017</p>
      </div>
      <div class="about-card">
        <div class="about-card-title">Core Strengths</div>
        <div class="tag-list">
          <span class="tag">Critical Thinking</span>
          <span class="tag">Team Collaboration</span>
          <span class="tag">Detail-Oriented</span>
          <span class="tag">Deadline-Driven</span>
          <span class="tag">Mentoring</span>
          <span class="tag">Problem Solving</span>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- Skills -->
<section id="skills">
  <div class="section-label">What I Do</div>
  <h2 class="section-title reveal">Technical Skills</h2>
  <div class="skills-grid reveal">

    <div class="skill-block">
      <span class="skill-icon">🎨</span>
      <div class="skill-name">Adobe Photoshop</div>
      <div class="skill-desc">Photo manipulation, compositing, retouching & digital art creation at expert level.</div>
      <div class="skill-level"><div class="skill-fill" data-width="95"></div></div>
    </div>

    <div class="skill-block">
      <span class="skill-icon">✏️</span>
      <div class="skill-name">Adobe Illustrator</div>
      <div class="skill-desc">Vector illustration, logo design, brand identity & scalable graphic systems.</div>
      <div class="skill-level"><div class="skill-fill" data-width="95"></div></div>
    </div>

    <div class="skill-block">
      <span class="skill-icon">📐</span>
      <div class="skill-name">Adobe InDesign</div>
      <div class="skill-desc">Editorial, layout, print production, brochures, magazines & packaging design.</div>
      <div class="skill-level"><div class="skill-fill" data-width="92"></div></div>
    </div>

    <div class="skill-block" style="background: #111;">
      <span class="skill-icon">🎬</span>
      <div class="skill-name">After Effects</div>
      <div class="skill-desc">Motion graphics, visual effects, title animations & dynamic content creation.</div>
      <div class="skill-level"><div class="skill-fill" data-width="90"></div></div>
    </div>

    <div class="skill-block" style="background: #111;">
      <span class="skill-icon">🎞️</span>
      <div class="skill-name">Premiere Pro</div>
      <div class="skill-desc">Professional video editing, color grading, sound design & multi-cam production.</div>
      <div class="skill-level"><div class="skill-fill" data-width="90"></div></div>
    </div>

    <div class="skill-block" style="background: #111;">
      <span class="skill-icon">📱</span>
      <div class="skill-name">UI/UX — Figma</div>
      <div class="skill-desc">Wireframing, prototyping, design systems & user-centered interface design.</div>
      <div class="skill-level"><div class="skill-fill" data-width="75"></div></div>
    </div>

  </div>
</section>

<!-- Video Editing Highlight -->
<section id="video-skills" style="padding: 80px 60px;">
  <div class="video-inner">
    <div class="video-text reveal">
      <div class="section-label">Specialization</div>
      <h2 class="section-title">Video<br>Editing &<br>Motion</h2>
      <p>5+ years of professional video production experience — from raw footage to polished, broadcast-ready content. Expert in storytelling through motion, color science, and sound design.</p>
      <div style="margin-top: 32px; display: flex; gap: 32px;">
        <div>
          <div style="font-family:'Bebas Neue',sans-serif;font-size:48px;color:var(--black);line-height:1;">5+</div>
          <div style="font-family:'Space Mono',monospace;font-size:10px;letter-spacing:2px;color:rgba(0,0,0,0.6);text-transform:uppercase;">Years in Video</div>
        </div>
        <div>
          <div style="font-family:'Bebas Neue',sans-serif;font-size:48px;color:var(--black);line-height:1;">100+</div>
          <div style="font-family:'Space Mono',monospace;font-size:10px;letter-spacing:2px;color:rgba(0,0,0,0.6);text-transform:uppercase;">Projects Cut</div>
        </div>
      </div>
    </div>
    <div class="video-tools reveal">
      <div class="tool-row">
        <span class="tool-name">Premiere Pro</span>
        <div class="tool-bar"><div class="tool-fill" data-width="95"></div></div>
        <span class="tool-pct">95%</span>
      </div>
      <div class="tool-row">
        <span class="tool-name">After Effects</span>
        <div class="tool-bar"><div class="tool-fill" data-width="90"></div></div>
        <span class="tool-pct">90%</span>
      </div>
      <div class="tool-row">
        <span class="tool-name">Color Grading</span>
        <div class="tool-bar"><div class="tool-fill" data-width="85"></div></div>
        <span class="tool-pct">85%</span>
      </div>
      <div class="tool-row">
        <span class="tool-name">Motion Graphics</span>
        <div class="tool-bar"><div class="tool-fill" data-width="88"></div></div>
        <span class="tool-pct">88%</span>
      </div>
      <div class="tool-row">
        <span class="tool-name">Sound Design</span>
        <div class="tool-bar"><div class="tool-fill" data-width="78"></div></div>
        <span class="tool-pct">78%</span>
      </div>
    </div>
  </div>
</section>

<!-- Experience -->
<section id="experience">
  <div class="section-label">Career Path</div>
  <h2 class="section-title reveal">Experience</h2>
  <div class="exp-timeline" style="margin-top:60px;">

    <div class="exp-item">
      <div class="exp-date">Sep 2025 — Present</div>
      <div class="exp-role">Graphic Designer <span class="current-badge">Current</span></div>
      <div class="exp-company">AGX Retail Solutions Pvt. Ltd. · Bangalore</div>
      <div class="exp-desc">Leading visual design across retail campaigns, digital assets, and brand communication. Developing motion graphics and video content for product launches and in-store experiences.</div>
    </div>

    <div class="exp-item">
      <div class="exp-date">Jul 2024 — Jun 2025</div>
      <div class="exp-role">Sr. Graphic Designer</div>
      <div class="exp-company">Vibrant Screen Pvt. Ltd. · Bangalore</div>
      <div class="exp-desc">Elevated to senior role overseeing design quality, mentoring junior designers, and delivering high-impact video editing and motion work for client campaigns and digital media.</div>
    </div>

    <div class="exp-item">
      <div class="exp-date">Oct 2023 — Jun 2024</div>
      <div class="exp-role">Graphic Designer</div>
      <div class="exp-company">Flatworld Solutions Pvt. Ltd. · Bangalore</div>
      <div class="exp-desc">Designed across print, digital and video mediums. Produced post-production content and managed multi-platform visual assets for international clients.</div>
    </div>

    <div class="exp-item">
      <div class="exp-date">Jun 2021 — Sep 2023</div>
      <div class="exp-role">Graphic Designer</div>
      <div class="exp-company">Silicon India Pvt. Ltd. · Bangalore</div>
      <div class="exp-desc">Foundation role building expertise in Adobe Creative Suite, brand design, and video production. Collaborated on marketing campaigns, corporate communications and event branding.</div>
    </div>

  </div>
</section>

<!-- Portfolio / Works -->
<section id="works">
  <div class="section-label">Selected Work</div>
  <h2 class="section-title reveal">Portfolio</h2>
  <div class="works-grid reveal">

    <div class="work-item">
      <div class="work-gradient" style="background: linear-gradient(135deg, #1a0a00, #ff4d00);"></div>
      <div class="work-bg">BRAND</div>
      <div class="work-overlay">
        <div class="work-cat">Brand Identity</div>
        <div class="work-title">Brand Design & Visual Systems</div>
      </div>
    </div>

    <div class="work-item">
      <div class="work-gradient" style="background: linear-gradient(135deg, #0a0010, #7b2fff);"></div>
      <div class="work-bg">FILM</div>
      <div class="work-overlay">
        <div class="work-cat">Video Production</div>
        <div class="work-title">Motion & Video Reel</div>
      </div>
    </div>

    <div class="work-item">
      <div class="work-gradient" style="background: linear-gradient(135deg, #001510, #00c49a);"></div>
      <div class="work-bg">UI</div>
      <div class="work-overlay">
        <div class="work-cat">UI/UX Design</div>
        <div class="work-title">App Interface Design</div>
      </div>
    </div>

    <div class="work-item">
      <div class="work-gradient" style="background: linear-gradient(135deg, #100a00, #ffb800);"></div>
      <div class="work-bg">PRINT</div>
      <div class="work-overlay">
        <div class="work-cat">Print & Editorial</div>
        <div class="work-title">Magazine & Layout Design</div>
      </div>
    </div>

    <div class="work-item">
      <div class="work-gradient" style="background: linear-gradient(135deg, #00050f, #0077ff);"></div>
      <div class="work-bg">MOTION</div>
      <div class="work-overlay">
        <div class="work-cat">Motion Graphics</div>
        <div class="work-title">Social & Digital Animation</div>
      </div>
    </div>

  </div>
  <div style="margin-top:40px; text-align:center;">
    <a href="#" class="btn-primary" style="display:inline-block;"><span>View Full Portfolio →</span></a>
  </div>
</section>

<!-- Contact -->
<section id="contact">
  <div class="contact-inner">
    <div>
      <div class="section-label reveal">Let's Work Together</div>
      <h2 class="contact-big reveal">GOT A<br>PROJECT<span>?</span><br>LET'S<br>TALK.</h2>
      <div class="contact-info reveal">
        <div class="info-row">
          <span class="info-label">Email</span>
          <span class="info-val">aravindhanbunathan@gmail.com</span>
        </div>
        <div class="info-row">
          <span class="info-label">Phone</span>
          <span class="info-val">+91 852-504-2637</span>
        </div>
        <div class="info-row">
          <span class="info-label">Location</span>
          <span class="info-val">Old Airport, Bangalore</span>
        </div>
        <div class="info-row">
          <span class="info-label">Status</span>
          <span class="info-val" style="display:flex;align-items:center;gap:10px;">
            <span style="width:8px;height:8px;border-radius:50%;background:var(--accent);display:inline-block;animation:pulse 2s infinite;"></span>
            Available for Opportunities
          </span>
        </div>
      </div>
    </div>
    <div class="reveal">
      <div class="contact-form">
        <div class="form-group">
          <label class="form-label">Your Name</label>
          <input class="form-input" type="text" placeholder="John Doe">
        </div>
        <div class="form-group">
          <label class="form-label">Email Address</label>
          <input class="form-input" type="email" placeholder="hello@company.com">
        </div>
        <div class="form-group">
          <label class="form-label">Project Type</label>
          <input class="form-input" type="text" placeholder="Brand Design / Video Editing / UI Design">
        </div>
        <div class="form-group">
          <label class="form-label">Message</label>
          <textarea class="form-textarea" placeholder="Tell me about your project..."></textarea>
        </div>
        <button class="btn-primary" style="align-self:flex-start;border:none;cursor:none;" onclick="alert('Message sent! Aravindh will get back to you soon.')">
          <span>Send Message →</span>
        </button>
      </div>
    </div>
  </div>
</section>

<!-- Footer -->
<footer>
  <div class="footer-logo">ARAVINDH<span>.</span>A</div>
  <div class="footer-copy">© 2025 — Graphic Designer, Bangalore</div>
</footer>

<script>
  // Custom cursor
  const cursor = document.getElementById('cursor');
  const ring = document.getElementById('cursorRing');
  let mx = 0, my = 0, rx = 0, ry = 0;

  document.addEventListener('mousemove', e => {
    mx = e.clientX; my = e.clientY;
    cursor.style.left = mx + 'px';
    cursor.style.top  = my + 'px';
  });

  (function animRing() {
    rx += (mx - rx) * 0.12;
    ry += (my - ry) * 0.12;
    ring.style.left = rx + 'px';
    ring.style.top  = ry + 'px';
    requestAnimationFrame(animRing);
  })();

  document.querySelectorAll('a, button, .work-item, .skill-block').forEach(el => {
    el.addEventListener('mouseenter', () => {
      cursor.style.width = '20px'; cursor.style.height = '20px';
      ring.style.width = '60px'; ring.style.height = '60px';
    });
    el.addEventListener('mouseleave', () => {
      cursor.style.width = '12px'; cursor.style.height = '12px';
      ring.style.width = '40px'; ring.style.height = '40px';
    });
  });

  // Scroll reveal
  const revealEls = document.querySelectorAll('.reveal, .exp-item');
  const observer = new IntersectionObserver(entries => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        entry.target.classList.add('visible');

        // Animate skill bars
        entry.target.querySelectorAll('.skill-fill, .tool-fill').forEach(bar => {
          setTimeout(() => {
            bar.style.width = bar.dataset.width + '%';
          }, 200);
        });
      }
    });
  }, { threshold: 0.15 });

  revealEls.forEach(el => observer.observe(el));

  // Animate skill bars that are in view on load
  document.querySelectorAll('.skill-fill, .tool-fill').forEach(bar => {
    const section = bar.closest('section');
    const sectionObserver = new IntersectionObserver(entries => {
      entries.forEach(e => {
        if (e.isIntersecting) {
          setTimeout(() => { bar.style.width = bar.dataset.width + '%'; }, 300);
          sectionObserver.disconnect();
        }
      });
    }, { threshold: 0.2 });
    if (section) sectionObserver.observe(section);
  });

  // Smooth nav active state
  const sections = document.querySelectorAll('section[id]');
  const navLinks = document.querySelectorAll('.nav-links a');
  window.addEventListener('scroll', () => {
    let current = '';
    sections.forEach(s => {
      if (window.scrollY >= s.offsetTop - 100) current = s.id;
    });
    navLinks.forEach(a => {
      a.style.color = a.getAttribute('href') === '#' + current ? 'var(--white)' : '';
    });
  });

  // Staggered experience items
  document.querySelectorAll('.exp-item').forEach((item, i) => {
    item.style.transitionDelay = (i * 0.15) + 's';
  });
</script>
</body>
</html>
