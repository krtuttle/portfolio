<!DOCTYPE html>
<html lang="ko">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>안태영 — 게임 기획자 포트폴리오</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Noto+Sans+KR:wght@300;400;500;700;900&family=Rajdhani:wght@500;700&display=swap" rel="stylesheet">
<link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/orioncactus/pretendard@v1.3.9/dist/web/static/pretendard.min.css">
<style>
  :root {
    --red: #e8393a;
    --gold: #f4a623;
    --bg: #0a0a0e;
    --surface: #111118;
    --surface2: #1a1a24;
    --text: #f0ede8;
    --muted: #8e8e9e;
    --border: rgba(255,255,255,0.07);
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }
  html { scroll-behavior: smooth; }
  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'Pretendard', 'Noto Sans KR', sans-serif;
    font-weight: 400;
    overflow-x: hidden;
  }

  /* NAV */
  nav {
    position: fixed; top: 0; left: 0; right: 0; z-index: 100;
    padding: 1.2rem 3rem;
    display: flex; align-items: center; justify-content: space-between;
    background: linear-gradient(to bottom, rgba(10,10,14,0.97), transparent);
  }
  .nav-logo {
    font-family: 'Pretendard', 'Noto Sans KR', sans-serif;
    font-size: 1.1rem; letter-spacing: 0.08em; font-weight: 800;
    color: var(--text); text-decoration: none;
  }
  .nav-links { display: flex; gap: 2rem; }
  .nav-links a {
    color: rgba(255,255,255,0.6); text-decoration: none;
    font-size: 0.82rem; letter-spacing: 0.1em; text-transform: uppercase;
    font-weight: 400;
    transition: color 0.2s;
  }
  .nav-links a:hover { color: var(--text); }
  .nav-links a.active { color: var(--red); }

  /* HERO */
  .hero {
    min-height: 100vh;
    display: flex; flex-direction: column;
    justify-content: flex-end;
    padding: 0 3rem 6rem;
    position: relative; overflow: hidden;
  }
  .hero-bg-img {
    position: absolute; inset: 0;
    background-image: url('https://img.youtube.com/vi/Rnz5ALqJwDM/maxresdefault.jpg');
    background-size: cover; background-position: center 30%;
    filter: brightness(0.35);
    transform: scale(1.05);
  }
  .hero-bg-overlay {
    position: absolute; inset: 0;
    background:
      linear-gradient(to right, rgba(10,10,14,0.92) 40%, rgba(10,10,14,0.5) 100%),
      linear-gradient(to top, rgba(10,10,14,1) 0%, transparent 50%);
  }
  .hero-grid {
    position: absolute; inset: 0;
    background-image:
      linear-gradient(rgba(255,255,255,0.03) 1px, transparent 1px),
      linear-gradient(90deg, rgba(255,255,255,0.03) 1px, transparent 1px);
    background-size: 60px 60px;
    mask-image: radial-gradient(ellipse 80% 80% at 30% 50%, black 20%, transparent 70%);
  }
  .hero-label {
    font-family: 'Rajdhani', sans-serif;
    font-size: 0.75rem; letter-spacing: 0.25em; text-transform: uppercase;
    color: var(--red); margin-bottom: 1.2rem;
    display: flex; align-items: center; gap: 0.8rem;
  }
  .hero-label::before { content: ''; display: inline-block; width: 32px; height: 1px; background: var(--red); }
  .hero-title {
    font-family: 'Pretendard', 'Noto Sans KR', sans-serif;
    font-weight: 900;
    font-size: clamp(3.2rem, 8vw, 7rem);
    line-height: 1.15; letter-spacing: -0.02em; margin-bottom: 0.6rem;
    text-shadow: 0 2px 20px rgba(0,0,0,0.5);
  }
  .hero-title .accent { color: var(--red); }
  .hero-sub {
    font-size: 1rem; color: rgba(255,255,255,0.55);
    letter-spacing: 0.04em; margin-bottom: 3rem;
    line-height: 1.8; max-width: 480px;
  }
  .hero-meta { display: flex; gap: 3rem; align-items: center; flex-wrap: wrap; }
  .hero-stat-num {
    font-family: 'Rajdhani', sans-serif;
    font-size: 2rem; font-weight: 700; color: var(--text); line-height: 1;
  }
  .hero-stat-num span { color: var(--gold); font-size: 1.2rem; }
  .hero-stat-label { font-size: 0.7rem; color: var(--muted); letter-spacing: 0.1em; text-transform: uppercase; margin-top: 0.2rem; }
  .hero-divider { width: 1px; height: 40px; background: var(--border); }
  .hero-cta {
    display: inline-flex; align-items: center; gap: 0.6rem;
    background: var(--red); color: white; text-decoration: none;
    padding: 0.75rem 1.8rem; font-size: 0.8rem;
    letter-spacing: 0.12em; text-transform: uppercase; font-weight: 500;
    transition: background 0.2s, transform 0.2s;
  }
  .hero-cta:hover { background: #ff4546; transform: translateY(-1px); }
  .scroll-hint {
    position: absolute; bottom: 2.5rem; left: 50%; transform: translateX(-50%);
    display: flex; flex-direction: column; align-items: center; gap: 0.6rem;
    color: rgba(255,255,255,0.6); font-size: 0.72rem; letter-spacing: 0.2em; text-transform: uppercase;
    font-family: 'Rajdhani', sans-serif; font-weight: 500;
    opacity: 0; animation: scrollHintIn 0.6s ease both;
    animation-delay: 1s;
  }
  .scroll-mouse {
    width: 22px; height: 36px; border: 2px solid rgba(255,255,255,0.4);
    border-radius: 11px; position: relative;
  }
  .scroll-mouse::after {
    content: ''; position: absolute; top: 6px; left: 50%; transform: translateX(-50%);
    width: 3px; height: 8px; background: var(--red); border-radius: 2px;
    animation: scrollDot 1.8s ease-in-out infinite;
    animation-delay: 1.8s;
  }
  .scroll-chevron {
    display: flex; flex-direction: column; align-items: center; gap: 2px;
    animation: scrollChevron 1.8s ease-in-out infinite;
    animation-delay: 1.8s;
  }
  .scroll-chevron span {
    display: block; width: 10px; height: 10px;
    border-right: 2px solid rgba(255,255,255,0.35);
    border-bottom: 2px solid rgba(255,255,255,0.35);
    transform: rotate(45deg);
  }
  .scroll-chevron span:nth-child(1) { opacity: 0.3; }
  .scroll-chevron span:nth-child(2) { opacity: 0.6; }
  .scroll-chevron span:nth-child(3) { opacity: 1; }
  @keyframes scrollHintIn {
    from { opacity: 0; }
    to { opacity: 1; }
  }
  @keyframes scrollDot {
    0% { transform: translateX(-50%) translateY(0); opacity: 1; }
    60% { transform: translateX(-50%) translateY(14px); opacity: 0; }
    100% { transform: translateX(-50%) translateY(0); opacity: 1; }
  }
  @keyframes scrollChevron {
    0% { transform: translateY(0); opacity: 1; }
    50% { transform: translateY(6px); opacity: 0.4; }
    100% { transform: translateY(0); opacity: 1; }
  }

  /* PORTFOLIO CTA SECTION */
  .portfolio-cta-section {
    text-align: center; padding: 6rem 3rem;
    position: relative; overflow: hidden;
  }
  .portfolio-cta-section::before {
    content: ''; position: absolute; top: 0; left: 0; right: 0; height: 1px;
    background: linear-gradient(90deg, transparent, var(--red), transparent);
  }
  .portfolio-cta-btn {
    display: inline-flex; align-items: center; gap: 0.8rem;
    background: var(--red); color: white; text-decoration: none;
    padding: 1rem 2.8rem; font-size: 0.95rem;
    letter-spacing: 0.08em; font-weight: 600;
    font-family: 'Pretendard', 'Noto Sans KR', sans-serif;
    transition: background 0.2s, transform 0.2s, box-shadow 0.2s;
    box-shadow: 0 4px 20px rgba(232,57,58,0.25);
  }
  .portfolio-cta-btn:hover {
    background: #ff4546; transform: translateY(-2px);
    box-shadow: 0 6px 28px rgba(232,57,58,0.4);
  }
  .portfolio-cta-sub {
    font-size: 0.8rem; color: var(--muted); margin-top: 1rem;
    letter-spacing: 0.06em;
  }

  /* SECTION COMMON */
  section { padding: 7rem 3rem; }
  .section-label {
    font-family: 'Rajdhani', sans-serif;
    font-size: 0.7rem; letter-spacing: 0.3em; text-transform: uppercase;
    color: var(--red); margin-bottom: 1rem;
    display: flex; align-items: center; gap: 0.8rem;
  }
  .section-label::before { content: ''; display: inline-block; width: 20px; height: 1px; background: var(--red); }
  .section-title { font-family: 'Pretendard', 'Noto Sans KR', sans-serif; font-weight: 800; font-size: clamp(2rem, 4vw, 3rem); line-height: 1.25; margin-bottom: 1rem; }

  /* IMPACT */
  .impact { background: var(--surface); position: relative; }
  .impact::before {
    content: ''; position: absolute; top: 0; left: 0; right: 0; height: 1px;
    background: linear-gradient(90deg, transparent, var(--red), transparent);
  }
  .impact-grid { display: grid; grid-template-columns: repeat(4, 1fr); }
  .impact-item { padding: 3rem 2rem; border-right: 1px solid var(--border); }
  .impact-item:last-child { border-right: none; }
  .impact-num { font-family: 'Rajdhani', sans-serif; font-size: 3.5rem; font-weight: 700; line-height: 1; color: var(--text); margin-bottom: 0.3rem; }
  .impact-num .unit { color: var(--gold); font-size: 2rem; }
  .impact-desc { font-size: 0.85rem; color: var(--muted); line-height: 1.7; }
  .impact-desc strong { display: block; color: var(--text); font-size: 0.9rem; font-weight: 500; margin-bottom: 0.3rem; }

  /* WORKS */
  .works-intro { display: flex; justify-content: space-between; align-items: flex-end; margin-bottom: 3.5rem; }
  .works-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 1.5rem; }

  .work-card {
    background: var(--surface); border: 1px solid var(--border);
    overflow: hidden; transition: transform 0.3s, border-color 0.3s;
  }
  .work-card:hover { transform: translateY(-4px); border-color: rgba(255,255,255,0.15); }

  .work-thumb { width: 100%; aspect-ratio: 16/9; overflow: hidden; position: relative; }
  .work-thumb img { width: 100%; height: 100%; object-fit: cover; transition: transform 0.5s ease; display: block; }
  .work-card:hover .work-thumb img { transform: scale(1.04); }
  .work-thumb-overlay {
    position: absolute; inset: 0;
    background: linear-gradient(to bottom, transparent 40%, rgba(17,17,24,0.92) 100%);
  }
  .work-thumb-badge {
    position: absolute; top: 0.8rem; left: 0.8rem;
    font-family: 'Rajdhani', sans-serif;
    font-size: 0.6rem; letter-spacing: 0.2em; text-transform: uppercase;
    padding: 0.2rem 0.6rem;
    background: rgba(10,10,14,0.75); border: 1px solid rgba(255,255,255,0.12);
  }
  .work-thumb-badge.red { color: var(--red); }
  .work-thumb-badge.gold { color: var(--gold); }
  .work-thumb-badge.teal { color: #4ecdc4; }

  .work-thumb-ue5 {
    width: 100%; aspect-ratio: 16/9;
    background: var(--surface2); position: relative; overflow: hidden;
    display: flex; align-items: center; justify-content: center;
  }
  .work-thumb-ue5::before {
    content: ''; position: absolute; inset: 0;
    background-image:
      linear-gradient(rgba(232,57,58,0.05) 1px, transparent 1px),
      linear-gradient(90deg, rgba(232,57,58,0.05) 1px, transparent 1px);
    background-size: 28px 28px;
  }
  .ue5-logo {
    font-family: 'Rajdhani', sans-serif; font-size: 2.5rem; font-weight: 700;
    color: rgba(232,57,58,0.4); letter-spacing: 0.1em;
    position: relative; z-index: 1; text-align: center; line-height: 1.2;
  }
  .ue5-logo span { display: block; font-size: 0.65rem; letter-spacing: 0.3em; color: rgba(255,255,255,0.12); margin-top: 0.4rem; }

  .work-body { padding: 1.6rem 1.8rem 2rem; }
  .work-type { font-size: 0.65rem; letter-spacing: 0.15em; text-transform: uppercase; color: var(--muted); margin-bottom: 0.6rem; }
  .work-title { font-family: 'Pretendard', 'Noto Sans KR', sans-serif; font-weight: 800; font-size: 1.25rem; margin-bottom: 0.8rem; line-height: 1.2; }
  .work-desc { font-size: 0.8rem; color: var(--muted); line-height: 1.8; margin-bottom: 1.2rem; }
  .work-tags { display: flex; flex-wrap: wrap; gap: 0.4rem; margin-bottom: 1.2rem; }
  .tag { font-size: 0.62rem; letter-spacing: 0.06em; padding: 0.22rem 0.55rem; border: 1px solid var(--border); color: var(--muted); }
  .work-user { font-size: 0.78rem; color: var(--text); line-height: 1.7; padding-top: 1rem; border-top: 1px solid var(--border); font-style: italic; }
  .work-user::before { content: '" '; color: var(--red); font-style: normal; font-weight: 700; font-size: 1rem; }

  /* SKILLS */
  .skills { background: var(--surface); }
  .skills-layout { display: grid; grid-template-columns: 1fr 1fr; gap: 4rem; margin-top: 3rem; }
  .skill-group-title { font-family: 'Rajdhani', sans-serif; font-size: 0.7rem; letter-spacing: 0.25em; text-transform: uppercase; color: var(--gold); margin-bottom: 1.5rem; }
  .skill-item { display: flex; justify-content: space-between; align-items: center; padding: 0.8rem 0; border-bottom: 1px solid var(--border); }
  .skill-name { font-size: 0.88rem; color: var(--text); }
  .skill-level { display: flex; gap: 3px; }
  .skill-dot { width: 6px; height: 6px; border-radius: 50%; background: var(--border); }
  .skill-dot.on { background: var(--red); }

  /* AI */
  .ai-cards { display: grid; grid-template-columns: repeat(3, 1fr); gap: 1.5rem; margin-top: 3rem; }
  .ai-card { border: 1px solid var(--border); padding: 2rem; }
  .ai-card-title { font-weight: 500; font-size: 1rem; margin-bottom: 0.8rem; }
  .ai-card-desc { font-size: 0.8rem; color: var(--muted); line-height: 1.8; margin-bottom: 1rem; }
  .ai-result { font-family: 'Rajdhani', sans-serif; font-size: 1.1rem; font-weight: 700; color: var(--gold); }

  /* EVAL */
  .eval { background: var(--surface); }
  .eval-row { display: flex; align-items: stretch; gap: 1px; background: var(--border); margin-top: 3rem; }
  .eval-item { flex: 1; background: var(--surface2); padding: 2rem; text-align: center; }
  .eval-year { font-family: 'Rajdhani', sans-serif; font-size: 0.7rem; letter-spacing: 0.2em; color: var(--muted); margin-bottom: 0.5rem; }
  .eval-grade { font-family: 'Rajdhani', sans-serif; font-size: 2.5rem; font-weight: 700; line-height: 1; }
  .eval-grade.a { color: var(--gold); }
  .eval-grade.b { color: var(--text); }
  .eval-quote { margin-top: 3rem; padding: 2.5rem; border: 1px solid var(--border); position: relative; }
  .eval-quote::before { content: '"'; position: absolute; top: -0.8rem; left: 2rem; font-family: 'Pretendard', 'Noto Sans KR', sans-serif; font-weight: 800; font-size: 4rem; color: var(--red); line-height: 1; }
  .eval-quote p { font-size: 0.9rem; color: var(--muted); line-height: 2; font-style: italic; }
  .eval-quote p strong { color: var(--text); font-style: normal; }

  /* CONTACT */
  .contact { text-align: center; padding: 8rem 3rem; position: relative; overflow: hidden; }
  .contact::before {
    content: '안태영'; position: absolute;
    font-family: 'Pretendard', 'Noto Sans KR', sans-serif; font-weight: 800; font-size: clamp(6rem, 20vw, 16rem);
    color: rgba(255,255,255,0.02); top: 50%; left: 50%;
    transform: translate(-50%, -50%); white-space: nowrap; pointer-events: none;
  }
  .contact-sub { font-size: 0.8rem; letter-spacing: 0.2em; text-transform: uppercase; color: var(--muted); margin-bottom: 1.5rem; }
  .contact-title { font-family: 'Pretendard', 'Noto Sans KR', sans-serif; font-weight: 800; font-size: clamp(2rem, 5vw, 4rem); margin-bottom: 2.5rem; line-height: 1.3; }
  .contact-links { display: flex; gap: 1.5rem; justify-content: center; flex-wrap: wrap; }
  .contact-link {
    display: inline-flex; align-items: center; gap: 0.5rem;
    color: var(--text); text-decoration: none; font-size: 0.85rem;
    letter-spacing: 0.06em; padding: 0.8rem 1.8rem;
    border: 1px solid var(--border); transition: border-color 0.2s, color 0.2s;
  }
  .contact-link:hover { border-color: var(--red); color: var(--red); }
  .contact-link.primary { background: var(--red); border-color: var(--red); color: white; }
  .contact-link.primary:hover { background: #ff4546; border-color: #ff4546; }

  footer { padding: 2rem 3rem; border-top: 1px solid var(--border); display: flex; justify-content: space-between; align-items: center; }
  footer p { font-size: 0.75rem; color: var(--muted); }

  .fade-in { opacity: 0; transform: translateY(24px); transition: opacity 0.7s ease, transform 0.7s ease; }
  .fade-in.visible { opacity: 1; transform: translateY(0); }

  /* MOBILE NAV */
  .nav-hamburger {
    display: none; cursor: pointer; z-index: 101;
    flex-direction: column; gap: 5px; padding: 4px;
  }
  .nav-hamburger span {
    display: block; width: 22px; height: 2px; background: var(--text);
    transition: transform 0.3s, opacity 0.3s;
  }
  .nav-hamburger.active span:nth-child(1) { transform: rotate(45deg) translate(5px, 5px); }
  .nav-hamburger.active span:nth-child(2) { opacity: 0; }
  .nav-hamburger.active span:nth-child(3) { transform: rotate(-45deg) translate(5px, -5px); }

  .nav-overlay {
    display: none; position: fixed; inset: 0; z-index: 99;
    background: rgba(10,10,14,0.97);
    flex-direction: column; align-items: center; justify-content: center; gap: 2.5rem;
  }
  .nav-overlay.open { display: flex; }
  .nav-overlay a {
    color: var(--text); text-decoration: none;
    font-family: 'Pretendard', 'Noto Sans KR', sans-serif;
    font-size: 1.3rem; font-weight: 600; letter-spacing: 0.08em;
    transition: color 0.2s;
  }
  .nav-overlay a:hover, .nav-overlay a.active { color: var(--red); }

  @media (max-width: 960px) {
    nav { padding: 1rem 1.5rem; }
    .nav-links { display: none; }
    .nav-hamburger { display: flex; }

    section { padding: 4rem 1.2rem; }
    .hero { padding: 0 1.5rem 4rem; }

    .hero-title { font-size: clamp(2.5rem, 12vw, 4.5rem); }
    .hero-sub { font-size: 0.88rem; margin-bottom: 2rem; }
    .hero-meta { gap: 1.5rem; }
    .hero-stat-num { font-size: 1.5rem; }
    .hero-stat-num span { font-size: 1rem; }
    .hero-stat-label { font-size: 0.62rem; }
    .hero-cta { padding: 0.65rem 1.2rem; font-size: 0.72rem; margin-left: 0 !important; }
    .hero-divider { height: 30px; }

    .scroll-hint { bottom: 1.5rem; }
    .scroll-mouse { width: 18px; height: 30px; }
    .scroll-hint span { font-size: 0.6rem; }

    .impact-grid { grid-template-columns: repeat(2, 1fr); }
    .impact-item { padding: 1.8rem 1.2rem; border-right: none; border-bottom: 1px solid var(--border); }
    .impact-item:nth-child(odd) { border-right: 1px solid var(--border); }
    .impact-num { font-size: 2.5rem; }

    .works-grid { grid-template-columns: 1fr; }
    .works-intro { flex-direction: column; align-items: flex-start; gap: 1rem; }
    .work-body { padding: 1.2rem 1.4rem 1.6rem; }

    .section-title { font-size: clamp(1.6rem, 5vw, 2.2rem); }

    .skills { padding: 4rem 1.2rem; }
    .skills-layout { grid-template-columns: 1fr; gap: 2rem; }
    .skill-name { font-size: 0.82rem; }

    .ai-cards { grid-template-columns: 1fr; }

    .eval-row { flex-wrap: wrap; }
    .eval-item { flex: 0 0 calc(50% - 1px); padding: 1.5rem 1rem; }
    .eval-grade { font-size: 2rem; }
    .eval-quote { padding: 1.8rem 1.2rem; }
    .eval-quote p { font-size: 0.82rem; }

    .portfolio-cta-section { padding: 4rem 1.5rem; }
    .portfolio-cta-btn { padding: 0.85rem 2rem; font-size: 0.88rem; }

    .contact { padding: 5rem 1.5rem; }
    .contact-title { font-size: clamp(1.6rem, 6vw, 2.5rem); }
    .contact-links { flex-direction: column; gap: 0.8rem; align-items: center; }
    .contact-link { width: 100%; max-width: 320px; justify-content: center; font-size: 0.8rem; }

    footer { flex-direction: column; gap: 0.5rem; text-align: center; padding: 1.5rem; }
  }

  @media (max-width: 480px) {
    .hero { padding: 0 1rem 3.5rem; }
    section { padding: 3.5rem 1rem; }
    .hero-title { font-size: clamp(2.2rem, 11vw, 3.5rem); }
    .hero-meta { gap: 1rem; flex-wrap: wrap; }
    .hero-cta { width: 100%; justify-content: center; margin-top: 0.5rem; }

    .impact-grid { grid-template-columns: 1fr; }
    .impact-item { border-right: none !important; }
    .impact-num { font-size: 2.2rem; }

    .eval-item { flex: 0 0 calc(50% - 1px); padding: 1.2rem 0.8rem; }
    .eval-grade { font-size: 1.8rem; }
  }
</style>
</head>
<body>

<nav>
  <a href="#" class="nav-logo">안태영</a>
  <div class="nav-links">
    <a href="#works">작업물</a>
    <a href="#skills">역량</a>
    <a href="#ai">AI 활용</a>
    <a href="#eval">사내 평가</a>
    <a href="#contact">연락처</a>
  </div>
  <div class="nav-hamburger" onclick="toggleMobileNav()">
    <span></span><span></span><span></span>
  </div>
</nav>

<div class="nav-overlay" id="mobileNav">
  <a href="#works" onclick="closeMobileNav()">작업물</a>
  <a href="#skills" onclick="closeMobileNav()">역량</a>
  <a href="#ai" onclick="closeMobileNav()">AI 활용</a>
  <a href="#eval" onclick="closeMobileNav()">사내 평가</a>
  <a href="#contact" onclick="closeMobileNav()">연락처</a>
</div>

<!-- HERO -->
<section class="hero" id="hero">
  <div class="hero-bg-img"></div>
  <div class="hero-bg-overlay"></div>
  <div class="hero-grid"></div>
  <div style="position: relative; z-index: 1;">
    <p class="hero-label fade-in">Level · Monster Combat Designer</p>
    <h1 class="hero-title fade-in">유저들이<br>인정한<br><span class="accent">인게임</span><br>기획자</h1>
    <p class="hero-sub fade-in">기획서는 알기 쉽게 · 기획은 재미 있게 · 협업은 효율 있게<br>넷마블몬스터 5년 1개월, 몰입도 높은 보스 콘텐츠 전문</p>
    <div class="hero-meta fade-in">
      <div class="hero-stat">
        <div class="hero-stat-num">5<span>년 1개월</span></div>
        <div class="hero-stat-label">총 경력</div>
      </div>
      <div class="hero-divider"></div>
      <div class="hero-stat">
        <div class="hero-stat-num" style="color:var(--gold)">A</div>
        <div class="hero-stat-label">최고 평가 달성 · 2023</div>
      </div>
      <div class="hero-divider"></div>
      <div class="hero-stat">
        <div class="hero-stat-num">UE5</div>
        <div class="hero-stat-label">신작 프로토타입</div>
      </div>
      <a href="https://drive.google.com/file/d/1IU25V4H21Mq0Vg3aLlixBbhvBfxYz_vs/view?usp=sharing" target="_blank" class="hero-cta" style="margin-left: 1.5rem;">상세 포트폴리오 바로 보기 →</a>
    </div>
  </div>
  <div class="scroll-hint">
    <div class="scroll-mouse"></div>
    <span>SCROLL DOWN</span>
    <div class="scroll-chevron"><span></span><span></span><span></span></div>
  </div>
</section>

<!-- IMPACT -->
<section class="impact" id="impact">
  <div class="impact-grid">
    <div class="impact-item fade-in">
      <div class="impact-num"><span class="count-up" data-target="98" data-suffix="%">0%</span></div>
      <div class="impact-desc"><strong>업무 공수 단축</strong>AI 스크립트 오타 검사기로<br>30분 작업을 1분으로 압축</div>
    </div>
    <div class="impact-item fade-in">
      <div class="impact-num"><span class="count-up" data-target="85" data-suffix="%">0%</span></div>
      <div class="impact-desc"><strong>시네마틱 작업 감소</strong>연출 툴 개선으로<br>1주일 → 1일로 단축</div>
    </div>
    <div class="impact-item fade-in">
      <div class="impact-num"><span class="count-up" data-target="3000" data-suffix="%">0%</span></div>
      <div class="impact-desc"><strong>개인 생산성 상승</strong>자동화 툴 도입으로<br>팀 전체 효율 극대화</div>
    </div>
    <div class="impact-item fade-in">
      <div class="impact-num"><span class="count-up" data-target="4635" data-suffix="">0</span><span class="unit"> hrs</span></div>
      <div class="impact-desc"><strong>누적 플레이 타임</strong>PS · Steam · Mobile · VR<br>전 플랫폼을 아우르는 게이머</div>
    </div>
  </div>
</section>

<!-- WORKS -->
<section id="works">
  <div class="works-intro">
    <div>
      <p class="section-label fade-in">주요 작업물</p>
      <h2 class="section-title fade-in">유저가 반응한<br>보스들</h2>
    </div>
    <p style="font-size: 0.8rem; color: var(--muted); max-width: 280px; text-align: right; line-height: 1.8;" class="fade-in">
      Marvel Future Fight 내<br>직접 기획·제작한 레이드 보스 및<br>UE5 미공개 신작 프로토타입
    </p>
  </div>

  <div class="works-grid">

    <div class="work-card fade-in">
      <div class="work-thumb-ue5">
        <div class="ue5-logo">TRINITY<span>UE5 · 미공개 신작 · 기밀</span></div>
      </div>
      <div class="work-body">
        <p class="work-type" style="color:var(--red)">UE5 · 2025 · 프로토타입</p>
        <h3 class="work-title">Trinity 프로토타입</h3>
        <p class="work-desc">15~20분 분량으로 게임의 핵심 요소와 조작법 전체를 소개. 몬스터 스킬/AI, 비헤이비어 트리, 몽타주 작업 전담.</p>
        <div class="work-tags"><span class="tag">스킬·AI 기획</span><span class="tag">비헤이비어 트리</span><span class="tag">FUN QA 주도</span><span class="tag">이펙트 기획</span></div>
        <p class="work-user">핵심 관련 인사 모두 프로토타입을 끝까지 플레이하고 매우 긍정적인 반응을 얻어 결과로 돌출</p>
      </div>
    </div>

    <div class="work-card fade-in">
      <div class="work-thumb">
        <img src="https://img.youtube.com/vi/Rnz5ALqJwDM/maxresdefault.jpg" alt="도르마무 월드 보스 레이드">
        <div class="work-thumb-overlay"></div>
        <span class="work-thumb-badge gold">3인 협동 레이드 · 2022</span>
      </div>
      <div class="work-body">
        <p class="work-type" style="color:var(--gold)">MFF · 거대 보스 레이드</p>
        <h3 class="work-title">도르마무</h3>
        <p class="work-desc">미숙한 플레이어가 패턴을 자연스럽게 학습하고, 숙련자 간 경쟁을 유발하는 구조 설계. "무한한 반복"이라는 캐릭터성을 패턴에 직접 녹여냄.</p>
        <div class="work-tags"><span class="tag">핵심 시스템 기획</span><span class="tag">AI·내비게이션</span><span class="tag">BGM 기획</span><span class="tag">밸런스</span></div>
        <p class="work-user">드디어 레이드다운 레이드가 나온느낌 — 이게 도르마무여 아르고스여</p>
      </div>
    </div>

    <div class="work-card fade-in">
      <div class="work-thumb">
        <img src="https://img.youtube.com/vi/xbUGkgiJzDI/maxresdefault.jpg" alt="다크피닉스 월드 보스 레전드">
        <div class="work-thumb-overlay"></div>
        <span class="work-thumb-badge teal">싱글 보스 레이드 · 2022</span>
      </div>
      <div class="work-body">
        <p class="work-type" style="color:#4ecdc4">MFF · 월드 보스 레전드</p>
        <h3 class="work-title">다크 피닉스</h3>
        <p class="work-desc">전조증상 명확화, 하이리스크-하이리턴, 탄막 심화를 3대 기획 축으로. 코믹스 서사를 패턴에 직접 반영한 연출 기획.</p>
        <div class="work-tags"><span class="tag">2페이즈 전환</span><span class="tag">투명 기믹</span><span class="tag">이펙트 기획</span><span class="tag">UI 명세</span></div>
        <p class="work-user">어렵지만 짜증나지는 않습니다. 확실히 재밌게 즐기기 아주 나이스한 게임 모드</p>
      </div>
    </div>

    <div class="work-card fade-in">
      <div class="work-thumb">
        <img src="https://img.youtube.com/vi/wdJmFklDYJs/hqdefault.jpg" alt="블랙스완 월드 보스+">
        <div class="work-thumb-overlay"></div>
        <span class="work-thumb-badge red">싱글 보스 레이드+ · 2024</span>
      </div>
      <div class="work-body">
        <p class="work-type" style="color:var(--red)">MFF · 월드 보스 레전드+</p>
        <h3 class="work-title">블랙 스완</h3>
        <p class="work-desc">신규 능력치 대미지를 핵심 공략 요소로 삼아 보상·패널티 구간 설계. 보스 상태별 카메라 연출로 몰입감 강화.</p>
        <div class="work-tags"><span class="tag">방어막 시스템</span><span class="tag">BGM 기획</span><span class="tag">카메라 연출</span><span class="tag">밸런스</span></div>
        <p class="work-user">몇년만에 제대로 나온 월보 — 블랙스완은 정말 멋있습니다, 전투는 단순하지만 꽤나 매력적</p>
      </div>
    </div>

    <div class="work-card fade-in">
      <div class="work-thumb">
        <img src="https://img.youtube.com/vi/Yp-A8Xd6cbc/maxresdefault.jpg" alt="보스·오브젝트 복합 상호작용">
        <div class="work-thumb-overlay"></div>
        <span class="work-thumb-badge gold">기술 역량 · AI 구조</span>
      </div>
      <div class="work-body">
        <p class="work-type" style="color:var(--gold)">복합 상호작용 설계</p>
        <h3 class="work-title">보스·오브젝트<br>복합 상호작용 AI</h3>
        <p class="work-desc">운석 오브젝트 AI와 보스 AI를 연동해 코인 획득·폭발 명령을 실시간 교환하는 복합 구조. 비헤이비어 트리 직접 구현.</p>
        <div class="work-tags"><span class="tag">보스 AI</span><span class="tag">오브젝트 AI</span><span class="tag">비헤이비어 트리</span></div>
        <p class="work-user">플레이어·보스·오브젝트 3자 실시간 상호작용으로 전략적 플레이 유도</p>
      </div>
    </div>

    <div class="work-card fade-in">
      <div class="work-thumb">
        <img src="https://img.youtube.com/vi/uC9oeD3Vjuo/maxresdefault.jpg" alt="스테이지 기믹 실시간 행동 전환">
        <div class="work-thumb-overlay"></div>
        <span class="work-thumb-badge teal">기술 역량 · 실시간 전환</span>
      </div>
      <div class="work-body">
        <p class="work-type" style="color:#4ecdc4">실시간 행동 전환 설계</p>
        <h3 class="work-title">기믹 수행에 따른<br>보스 실시간 전환</h3>
        <p class="work-desc">기믹 성공/실패 여부에 따라 보스 AI가 즉시 페이즈 전환. 강제 명령 송신 방식으로 오브젝트 AI와 연동.</p>
        <div class="work-tags"><span class="tag">실시간 AI 전환</span><span class="tag">디버프 시스템</span><span class="tag">페이즈 설계</span></div>
        <p class="work-user">기믹 성공/실패가 보스의 행동을 즉각 바꾸는 반응형 전투 설계</p>
      </div>
    </div>

  </div>
</section>

<!-- SKILLS -->
<section class="skills" id="skills">
  <p class="section-label fade-in">핵심 역량</p>
  <h2 class="section-title fade-in">무엇을 잘 하는가</h2>
  <div class="skills-layout">
    <div>
      <p class="skill-group-title">기획 역량</p>
      <div class="skill-item fade-in"><span class="skill-name">몬스터 스킬 / 패턴 (AI) 기획·제작</span><div class="skill-level"><div class="skill-dot on"></div><div class="skill-dot on"></div><div class="skill-dot on"></div><div class="skill-dot on"></div><div class="skill-dot on"></div></div></div>
      <div class="skill-item fade-in"><span class="skill-name">스테이지 기획 · 밸런스</span><div class="skill-level"><div class="skill-dot on"></div><div class="skill-dot on"></div><div class="skill-dot on"></div><div class="skill-dot on"></div><div class="skill-dot on"></div></div></div>
      <div class="skill-item fade-in"><span class="skill-name">비헤이비어 트리 설계 · 제작</span><div class="skill-level"><div class="skill-dot on"></div><div class="skill-dot on"></div><div class="skill-dot on"></div><div class="skill-dot on"></div><div class="skill-dot"></div></div></div>
      <div class="skill-item fade-in"><span class="skill-name">이펙트 · BGM · 애니메이션 기획 / 관련 팀 협업</span><div class="skill-level"><div class="skill-dot on"></div><div class="skill-dot on"></div><div class="skill-dot on"></div><div class="skill-dot on"></div><div class="skill-dot"></div></div></div>
      <div class="skill-item fade-in"><span class="skill-name">기능 명세 / 클라이언트 협업</span><div class="skill-level"><div class="skill-dot on"></div><div class="skill-dot on"></div><div class="skill-dot on"></div><div class="skill-dot on"></div><div class="skill-dot"></div></div></div>
    </div>
    <div>
      <p class="skill-group-title">툴 & 협업</p>
      <div class="skill-item fade-in"><span class="skill-name">Unreal Engine 5 (몽타주·비헤이비어)</span><div class="skill-level"><div class="skill-dot on"></div><div class="skill-dot on"></div><div class="skill-dot on"></div><div class="skill-dot on"></div><div class="skill-dot"></div></div></div>
      <div class="skill-item fade-in"><span class="skill-name">AI 바이브 코딩 (Chat GPT · Gemini · Claude)</span><div class="skill-level"><div class="skill-dot on"></div><div class="skill-dot on"></div><div class="skill-dot on"></div><div class="skill-dot on"></div><div class="skill-dot"></div></div></div>
      <div class="skill-item fade-in"><span class="skill-name">프로세스 개선 · 위키 제작</span><div class="skill-level"><div class="skill-dot on"></div><div class="skill-dot on"></div><div class="skill-dot on"></div><div class="skill-dot on"></div><div class="skill-dot on"></div></div></div>
      <div class="skill-item fade-in"><span class="skill-name">밸런스 문서 양식 설계</span><div class="skill-level"><div class="skill-dot on"></div><div class="skill-dot on"></div><div class="skill-dot on"></div><div class="skill-dot on"></div><div class="skill-dot"></div></div></div>
      <div class="skill-item fade-in"><span class="skill-name">파트원 가이드 · 육성</span><div class="skill-level"><div class="skill-dot on"></div><div class="skill-dot on"></div><div class="skill-dot on"></div><div class="skill-dot on"></div><div class="skill-dot"></div></div></div>
    </div>
  </div>
</section>

<!-- AI -->
<section id="ai">
  <p class="section-label fade-in">AI 활용 능력</p>
  <h2 class="section-title fade-in">만들어서<br>증명했습니다</h2>
  <div class="ai-cards">
    <div class="ai-card fade-in">
      <p class="ai-card-title">스테이지 스크립트 오타 검사기</p>
      <p class="ai-card-desc">Chat GPT 4.0 + Python으로 에디터 빌드 오류를 유발하는 오타·문법 오류를 자동 탐지. 파일 실시간 수정·저장·몬스터 수량 카운팅까지.</p>
      <p class="ai-result">공수 98.3% 단축</p>
    </div>
    <div class="ai-card fade-in">
      <p class="ai-card-title">보드게임 '스컬킹' 계산기 앱</p>
      <p class="ai-card-desc">Gemini + Flutter로 직접 제작. 시중 앱의 불편함(플레이어 수 제약, 광고, 라운드 제한)을 모두 해소. 기획→개발→배포 전 과정 주도.</p>
      <p class="ai-result">기획·개발·배포 직접 수행</p>
    </div>
    <div class="ai-card fade-in">
      <p class="ai-card-title">보드게임 '티츄' 계산기 앱</p>
      <p class="ai-card-desc">복잡한 티츄 점수 계산을 초보자도 직관적으로 입력할 수 있도록 UX 설계. Gemini + Flutter, 과거 기록 열람 기능까지 포함.</p>
      <p class="ai-result">초보자 접근성 중심 UX 설계</p>
    </div>
  </div>
</section>

<!-- EVAL -->
<section class="eval" id="eval">
  <p class="section-label fade-in">사내 평가</p>
  <h2 class="section-title fade-in">5년 연속<br>B+ 이상</h2>
  <div class="eval-row">
    <div class="eval-item fade-in"><div class="eval-year">2021</div><div class="eval-grade b">B+</div></div>
    <div class="eval-item fade-in"><div class="eval-year">2022</div><div class="eval-grade b">B+</div></div>
    <div class="eval-item fade-in"><div class="eval-year">2023</div><div class="eval-grade a">A</div></div>
    <div class="eval-item fade-in"><div class="eval-year">2024</div><div class="eval-grade b">B+</div></div>
    <div class="eval-item fade-in"><div class="eval-year">2025</div><div class="eval-grade b">B+</div></div>
  </div>
  <div class="eval-quote fade-in">
    <p><strong>업무 처리가 빠르고 많은 업무의 일정 관리를 빈틈없이 해내어 신뢰가 높습니다.</strong> 엑셀 함수나 파이썬을 공부하여 업무에 적용하거나 지라를 이용해 히스토리를 남겨 파트 내 효율성 증대에 기여하고 있습니다. 말은 못 이상을 해내려 노력하고 솔선수범하여 자발적으로 업무를 맡으려 합니다.</p>
  </div>
</section>

<!-- PORTFOLIO CTA -->
<section class="portfolio-cta-section">
  <a href="https://drive.google.com/file/d/1IU25V4H21Mq0Vg3aLlixBbhvBfxYz_vs/view?usp=sharing" target="_blank" class="portfolio-cta-btn fade-in">상세 포트폴리오 보기 →</a>
  <p class="portfolio-cta-sub fade-in">기획 의도, 상세 설계, 프로세스 개선 사례까지 확인할 수 있습니다</p>
</section>

<!-- CONTACT -->
<section class="contact" id="contact">
  <p class="contact-sub fade-in">지금 바로 연락하세요</p>
  <h2 class="contact-title fade-in">함께 만들고 싶은<br>게임이 있다면</h2>
  <div class="contact-links fade-in">
    <a href="tel:010-8586-4524" class="contact-link">📞 010-8586-4524</a>
    <a href="mailto:xodud0816@gmail.com" class="contact-link primary">✉ xodud0816@gmail.com</a>
  </div>
</section>

<footer>
  <p>© 2026 안태영 포트폴리오</p>
  <p>레벨 · 몬스터 전투 기획자</p>
</footer>

<script>
  const fadeEls = document.querySelectorAll('.fade-in');
  const obs = new IntersectionObserver(entries => {
    entries.forEach(e => { if (e.isIntersecting) { setTimeout(() => e.target.classList.add('visible'), 60); obs.unobserve(e.target); } });
  }, { threshold: 0.1 });
  fadeEls.forEach(el => obs.observe(el));

  const counters = document.querySelectorAll('.count-up');
  const cObs = new IntersectionObserver(entries => {
    entries.forEach(entry => {
      if (!entry.isIntersecting) return;
      const el = entry.target;
      const target = parseInt(el.dataset.target);
      const suffix = el.dataset.suffix || '';
      const start = performance.now();
      const animate = now => {
        const p = Math.min((now - start) / 1400, 1);
        const eased = 1 - Math.pow(1 - p, 3);
        el.textContent = Math.round(eased * target).toLocaleString() + suffix;
        if (p < 1) requestAnimationFrame(animate);
      };
      requestAnimationFrame(animate);
      cObs.unobserve(el);
    });
  }, { threshold: 0.5 });
  counters.forEach(el => cObs.observe(el));

  // YouTube 썸네일 폴백: maxresdefault 실패 시 hqdefault로 전환
  document.querySelectorAll('.work-thumb img').forEach(img => {
    img.addEventListener('error', function() {
      if (this.src.includes('maxresdefault')) {
        this.src = this.src.replace('maxresdefault', 'hqdefault');
      }
    });
  });

  // 스크롤 위치에 따라 내비 탭 활성화
  const navLinks = document.querySelectorAll('.nav-links a');
  const sections = Array.from(navLinks).map(a => {
    const id = a.getAttribute('href').slice(1);
    return { link: a, el: document.getElementById(id) };
  }).filter(s => s.el);

  function updateActiveNav() {
    const scrollY = window.scrollY + 120;
    const atBottom = (window.innerHeight + window.scrollY) >= (document.body.scrollHeight - 100);
    navLinks.forEach(a => a.classList.remove('active'));

    if (atBottom) {
      // 페이지 하단 도달 시 마지막 탭(연락처) 활성화
      const last = sections[sections.length - 1];
      if (last) last.link.classList.add('active');
    } else {
      let current = null;
      sections.forEach(s => {
        if (s.el.offsetTop <= scrollY) current = s;
      });
      if (current) current.link.classList.add('active');
    }
  }
  window.addEventListener('scroll', updateActiveNav, { passive: true });
  updateActiveNav();

  // 스크롤 시 스크롤 힌트 숨기기 (바운스 중에는 무시)
  const scrollHint = document.querySelector('.scroll-hint');
  let bouncing = false;
  window.addEventListener('scroll', () => {
    if (bouncing) return;
    if (window.scrollY > 50 && scrollHint) {
      scrollHint.style.opacity = '0';
      scrollHint.style.transition = 'opacity 0.4s ease';
    }
  }, { passive: true });

  // 페이지 진입 시 스크롤 유도 바운스 (스크롤 힌트 등장 후 실행)
  setTimeout(() => {
    if (window.scrollY > 5) return;
    bouncing = true;
    const duration = 1400;
    const distance = 150;
    const start = performance.now();
    function bounce(now) {
      const t = Math.min((now - start) / duration, 1);
      const y = distance * Math.sin(t * Math.PI);
      window.scrollTo(0, y);
      if (t < 1) {
        requestAnimationFrame(bounce);
      } else {
        window.scrollTo(0, 0);
        bouncing = false;
      }
    }
    requestAnimationFrame(bounce);
  }, 2200);

  // 모바일 내비게이션
  function toggleMobileNav() {
    const overlay = document.getElementById('mobileNav');
    const hamburger = document.querySelector('.nav-hamburger');
    overlay.classList.toggle('open');
    hamburger.classList.toggle('active');
    document.body.style.overflow = overlay.classList.contains('open') ? 'hidden' : '';
  }
  function closeMobileNav() {
    const overlay = document.getElementById('mobileNav');
    const hamburger = document.querySelector('.nav-hamburger');
    overlay.classList.remove('open');
    hamburger.classList.remove('active');
    document.body.style.overflow = '';
  }
  // 전역 접근
  window.toggleMobileNav = toggleMobileNav;
  window.closeMobileNav = closeMobileNav;
</script>
</body>
</html>
