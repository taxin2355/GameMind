[GameMind_HP .html](https://github.com/user-attachments/files/26328120/GameMind_HP.html)
<!DOCTYPE html>
<html lang="ja">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>GameMind | ゲームスキルと人間力を同時に磨く</title>
<link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@400;700;900&family=Noto+Sans+JP:wght@300;400;700;900&display=swap" rel="stylesheet">
<style>
  :root {
    --blue: #2B4FD4;
    --blue-light: #4A6FEF;
    --blue-dark: #1A35A8;
    --glow: #5B7FFF;
    --bg: #080C18;
    --bg2: #0D1424;
    --bg3: #111A30;
    --text: #E8EEFF;
    --text-muted: #7A8BB5;
    --accent: #00F0FF;
    --gold: #FFD700;
    --white: #ffffff;
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  html { scroll-behavior: smooth; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'Noto Sans JP', sans-serif;
    overflow-x: hidden;
    line-height: 1.7;
  }

  /* ── GRID BG ── */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background-image:
      linear-gradient(rgba(43,79,212,0.06) 1px, transparent 1px),
      linear-gradient(90deg, rgba(43,79,212,0.06) 1px, transparent 1px);
    background-size: 60px 60px;
    pointer-events: none;
    z-index: 0;
  }

  /* ── NAV ── */
  nav {
    position: fixed;
    top: 0; left: 0; right: 0;
    z-index: 100;
    padding: 16px 40px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    background: rgba(8,12,24,0.85);
    backdrop-filter: blur(16px);
    border-bottom: 1px solid rgba(43,79,212,0.25);
  }

  .nav-logo {
    font-family: 'Orbitron', sans-serif;
    font-weight: 900;
    font-size: 1.4rem;
    color: var(--white);
    letter-spacing: 2px;
    text-decoration: none;
  }
  .nav-logo span { color: var(--accent); }

  .nav-links {
    display: flex;
    gap: 32px;
    list-style: none;
  }
  .nav-links a {
    color: var(--text-muted);
    text-decoration: none;
    font-size: 0.85rem;
    font-weight: 700;
    letter-spacing: 1px;
    transition: color 0.2s;
  }
  .nav-links a:hover { color: var(--accent); }

  .nav-cta {
    background: var(--blue);
    color: var(--white) !important;
    padding: 8px 20px;
    border-radius: 4px;
    transition: background 0.2s !important;
  }
  .nav-cta:hover { background: var(--blue-light) !important; color: var(--white) !important; }

  /* ── HERO ── */
  #hero {
    position: relative;
    min-height: 100vh;
    display: flex;
    align-items: center;
    padding: 120px 40px 80px;
    overflow: hidden;
  }

  .hero-glow {
    position: absolute;
    top: 50%; left: 50%;
    transform: translate(-50%, -50%);
    width: 800px; height: 800px;
    background: radial-gradient(circle, rgba(43,79,212,0.18) 0%, transparent 70%);
    pointer-events: none;
  }

  .hero-inner {
    position: relative;
    z-index: 1;
    max-width: 1100px;
    margin: 0 auto;
    width: 100%;
  }

  .hero-badge {
    display: inline-block;
    background: rgba(43,79,212,0.2);
    border: 1px solid rgba(43,79,212,0.5);
    color: var(--accent);
    font-size: 0.75rem;
    font-weight: 700;
    letter-spacing: 3px;
    padding: 6px 16px;
    border-radius: 2px;
    margin-bottom: 28px;
    animation: fadeUp 0.6s ease both;
  }

  .hero-title {
    font-family: 'Orbitron', sans-serif;
    font-weight: 900;
    font-size: clamp(2.4rem, 6vw, 5rem);
    line-height: 1.1;
    letter-spacing: -1px;
    margin-bottom: 16px;
    animation: fadeUp 0.6s 0.1s ease both;
  }

  .hero-title .line2 {
    color: var(--blue-light);
    display: block;
  }

  .hero-sub {
    font-size: clamp(1rem, 2vw, 1.25rem);
    color: var(--text-muted);
    max-width: 560px;
    margin-bottom: 40px;
    font-weight: 300;
    animation: fadeUp 0.6s 0.2s ease both;
  }

  .hero-sub strong {
    color: var(--text);
    font-weight: 700;
  }

  .hero-ctas {
    display: flex;
    gap: 16px;
    flex-wrap: wrap;
    animation: fadeUp 0.6s 0.3s ease both;
  }

  .btn-primary {
    background: var(--blue);
    color: var(--white);
    padding: 16px 36px;
    font-size: 1rem;
    font-weight: 700;
    border: none;
    border-radius: 4px;
    cursor: pointer;
    text-decoration: none;
    display: inline-block;
    transition: background 0.2s, transform 0.15s;
    letter-spacing: 1px;
  }
  .btn-primary:hover { background: var(--blue-light); transform: translateY(-2px); }

  .btn-line {
    background: #06C755;
    color: var(--white);
    padding: 16px 36px;
    font-size: 1rem;
    font-weight: 700;
    border: none;
    border-radius: 4px;
    cursor: pointer;
    text-decoration: none;
    display: inline-block;
    transition: opacity 0.2s, transform 0.15s;
    letter-spacing: 1px;
  }
  .btn-line:hover { opacity: 0.88; transform: translateY(-2px); }

  .hero-stat-row {
    display: flex;
    gap: 48px;
    margin-top: 64px;
    padding-top: 40px;
    border-top: 1px solid rgba(43,79,212,0.2);
    animation: fadeUp 0.6s 0.4s ease both;
    flex-wrap: wrap;
  }

  .hero-stat h3 {
    font-family: 'Orbitron', sans-serif;
    font-size: 2rem;
    font-weight: 900;
    color: var(--white);
  }
  .hero-stat h3 span { color: var(--accent); }
  .hero-stat p {
    font-size: 0.8rem;
    color: var(--text-muted);
    letter-spacing: 1px;
    font-weight: 700;
    margin-top: 4px;
  }

  /* ── SECTION BASE ── */
  section {
    position: relative;
    z-index: 1;
    padding: 100px 40px;
  }

  .section-inner {
    max-width: 1100px;
    margin: 0 auto;
  }

  .section-label {
    font-family: 'Orbitron', sans-serif;
    font-size: 0.7rem;
    letter-spacing: 4px;
    color: var(--accent);
    font-weight: 700;
    margin-bottom: 16px;
    text-transform: uppercase;
  }

  .section-title {
    font-family: 'Noto Sans JP', sans-serif;
    font-weight: 900;
    font-size: clamp(1.8rem, 3.5vw, 2.8rem);
    line-height: 1.25;
    margin-bottom: 20px;
    color: var(--white);
  }

  .section-title span { color: var(--blue-light); }

  .section-desc {
    color: var(--text-muted);
    font-size: 1rem;
    max-width: 580px;
    font-weight: 300;
    margin-bottom: 56px;
  }

  /* ── PHILOSOPHY ── */
  #philosophy { background: var(--bg2); }

  .phil-cards {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 2px;
    background: rgba(43,79,212,0.15);
    border: 1px solid rgba(43,79,212,0.2);
  }

  .phil-card {
    background: var(--bg2);
    padding: 48px 40px;
  }

  .phil-card-num {
    font-family: 'Orbitron', sans-serif;
    font-size: 0.7rem;
    letter-spacing: 3px;
    color: var(--blue-light);
    margin-bottom: 16px;
    font-weight: 700;
  }

  .phil-card h3 {
    font-weight: 900;
    font-size: 1.4rem;
    color: var(--white);
    margin-bottom: 16px;
    line-height: 1.4;
  }

  .phil-card h3 em {
    font-style: normal;
    color: var(--accent);
  }

  .phil-card p {
    color: var(--text-muted);
    font-size: 0.9rem;
    font-weight: 300;
    line-height: 1.8;
  }

  /* ── VS TABLE ── */
  #vs { background: var(--bg); }

  .vs-table {
    width: 100%;
    border-collapse: collapse;
    margin-top: 0;
  }

  .vs-table thead tr {
    background: var(--blue);
  }

  .vs-table th {
    padding: 16px 24px;
    font-family: 'Orbitron', sans-serif;
    font-size: 0.75rem;
    letter-spacing: 2px;
    font-weight: 700;
    color: var(--white);
    text-align: left;
  }

  .vs-table th:first-child { color: rgba(255,255,255,0.6); }

  .vs-table td {
    padding: 14px 24px;
    font-size: 0.9rem;
    border-bottom: 1px solid rgba(43,79,212,0.1);
    color: var(--text-muted);
  }

  .vs-table td:last-child {
    color: var(--text);
    font-weight: 700;
  }

  .vs-table tr:nth-child(even) td { background: rgba(43,79,212,0.04); }
  .vs-table tr:hover td { background: rgba(43,79,212,0.1); }

  /* ── PLANS ── */
  #plans { background: var(--bg2); }

  .plans-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 2px;
    background: rgba(43,79,212,0.12);
  }

  .plan-card {
    background: var(--bg2);
    padding: 40px 32px;
    position: relative;
    transition: background 0.2s;
  }

  .plan-card:hover { background: var(--bg3); }

  .plan-card.featured {
    background: var(--bg3);
    border: 1px solid rgba(43,79,212,0.5);
    z-index: 1;
  }

  .plan-badge {
    position: absolute;
    top: -1px; left: 50%; transform: translateX(-50%);
    background: var(--blue);
    color: var(--white);
    font-size: 0.65rem;
    font-weight: 700;
    letter-spacing: 2px;
    padding: 4px 14px;
    font-family: 'Orbitron', sans-serif;
  }

  .plan-name {
    font-family: 'Orbitron', sans-serif;
    font-size: 0.85rem;
    letter-spacing: 2px;
    color: var(--text-muted);
    margin-bottom: 12px;
    font-weight: 700;
  }

  .plan-price {
    font-family: 'Orbitron', sans-serif;
    font-size: 2.4rem;
    font-weight: 900;
    color: var(--white);
    margin-bottom: 4px;
  }

  .plan-price span {
    font-size: 1rem;
    color: var(--text-muted);
    font-weight: 400;
  }

  .plan-freq {
    font-size: 0.8rem;
    color: var(--text-muted);
    margin-bottom: 28px;
    font-weight: 300;
  }

  .plan-divider {
    height: 1px;
    background: rgba(43,79,212,0.2);
    margin-bottom: 24px;
  }

  .plan-features {
    list-style: none;
    display: flex;
    flex-direction: column;
    gap: 10px;
  }

  .plan-features li {
    font-size: 0.85rem;
    color: var(--text-muted);
    display: flex;
    align-items: flex-start;
    gap: 10px;
    font-weight: 300;
  }

  .plan-features li::before {
    content: '▸';
    color: var(--blue-light);
    flex-shrink: 0;
    margin-top: 1px;
  }

  .plan-cta {
    display: block;
    margin-top: 32px;
    text-align: center;
    padding: 13px;
    font-size: 0.85rem;
    font-weight: 700;
    letter-spacing: 1px;
    border-radius: 3px;
    text-decoration: none;
    transition: all 0.2s;
  }

  .plan-cta-outline {
    border: 1px solid rgba(43,79,212,0.4);
    color: var(--text-muted);
  }
  .plan-cta-outline:hover {
    border-color: var(--blue);
    color: var(--blue-light);
  }

  .plan-cta-filled {
    background: var(--blue);
    color: var(--white);
  }
  .plan-cta-filled:hover { background: var(--blue-light); }

  /* ── GUARANTEE ── */
  .guarantee-box {
    margin-top: 48px;
    padding: 32px 40px;
    background: rgba(43,79,212,0.08);
    border: 1px solid rgba(43,79,212,0.25);
    border-left: 4px solid var(--blue);
    display: flex;
    align-items: flex-start;
    gap: 24px;
  }

  .guarantee-icon {
    font-size: 2.4rem;
    flex-shrink: 0;
  }

  .guarantee-box h4 {
    font-family: 'Orbitron', sans-serif;
    font-size: 0.85rem;
    letter-spacing: 2px;
    color: var(--blue-light);
    margin-bottom: 8px;
    font-weight: 700;
  }

  .guarantee-box p {
    font-size: 0.9rem;
    color: var(--text-muted);
    font-weight: 300;
    line-height: 1.8;
  }

  /* ── SERVICES ── */
  #services { background: var(--bg); }

  .services-grid {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 24px;
  }

  .service-card {
    background: var(--bg3);
    border: 1px solid rgba(43,79,212,0.15);
    padding: 36px;
    border-radius: 2px;
    transition: border-color 0.2s, transform 0.2s;
  }

  .service-card:hover {
    border-color: rgba(43,79,212,0.4);
    transform: translateY(-3px);
  }

  .service-icon {
    font-size: 2rem;
    margin-bottom: 16px;
  }

  .service-card h3 {
    font-weight: 900;
    font-size: 1.05rem;
    color: var(--white);
    margin-bottom: 10px;
  }

  .service-card p {
    font-size: 0.88rem;
    color: var(--text-muted);
    font-weight: 300;
    line-height: 1.8;
  }

  /* ── CTA SECTION ── */
  #cta {
    background: var(--bg2);
    text-align: center;
  }

  #cta .section-inner {
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  .cta-copy {
    font-size: clamp(1.6rem, 3vw, 2.4rem);
    font-weight: 900;
    color: var(--white);
    line-height: 1.35;
    max-width: 640px;
    margin-bottom: 12px;
  }

  .cta-copy span { color: var(--blue-light); }

  .cta-sub {
    font-size: 0.95rem;
    color: var(--text-muted);
    font-weight: 300;
    margin-bottom: 40px;
  }

  .cta-btns {
    display: flex;
    gap: 16px;
    flex-wrap: wrap;
    justify-content: center;
  }

  .cta-guarantee {
    margin-top: 28px;
    font-size: 0.8rem;
    color: var(--text-muted);
    letter-spacing: 1px;
  }

  /* ── FOOTER ── */
  footer {
    background: var(--bg);
    border-top: 1px solid rgba(43,79,212,0.15);
    padding: 40px;
    text-align: center;
  }

  .footer-logo {
    font-family: 'Orbitron', sans-serif;
    font-weight: 900;
    font-size: 1.2rem;
    color: var(--white);
    letter-spacing: 3px;
    margin-bottom: 12px;
  }

  .footer-logo span { color: var(--accent); }

  .footer-tagline {
    font-size: 0.8rem;
    color: var(--text-muted);
    font-weight: 300;
    margin-bottom: 24px;
  }

  .footer-links {
    display: flex;
    gap: 24px;
    justify-content: center;
    list-style: none;
    margin-bottom: 24px;
  }

  .footer-links a {
    font-size: 0.8rem;
    color: var(--text-muted);
    text-decoration: none;
    transition: color 0.2s;
  }

  .footer-links a:hover { color: var(--white); }

  footer small {
    font-size: 0.75rem;
    color: rgba(122,139,181,0.5);
  }

  /* ── ANIMATIONS ── */
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(24px); }
    to   { opacity: 1; transform: translateY(0); }
  }

  .reveal {
    opacity: 0;
    transform: translateY(30px);
    transition: opacity 0.7s ease, transform 0.7s ease;
  }

  .reveal.visible {
    opacity: 1;
    transform: translateY(0);
  }

  /* ── TICKER ── */
  .ticker-wrap {
    overflow: hidden;
    background: var(--blue);
    padding: 10px 0;
    border-top: 1px solid rgba(255,255,255,0.1);
    border-bottom: 1px solid rgba(255,255,255,0.1);
  }

  .ticker {
    display: flex;
    white-space: nowrap;
    animation: ticker 28s linear infinite;
    gap: 0;
  }

  .ticker-item {
    padding: 0 48px;
    font-size: 0.78rem;
    font-weight: 700;
    letter-spacing: 3px;
    color: rgba(255,255,255,0.85);
    font-family: 'Orbitron', sans-serif;
  }

  .ticker-dot {
    color: var(--accent);
    padding: 0 4px;
  }

  @keyframes ticker {
    from { transform: translateX(0); }
    to   { transform: translateX(-50%); }
  }

  /* ── RESPONSIVE ── */
  @media (max-width: 768px) {
    nav { padding: 14px 20px; }
    .nav-links { display: none; }
    section { padding: 72px 20px; }
    #hero { padding: 100px 20px 60px; }
    .phil-cards { grid-template-columns: 1fr; }
    .plans-grid { grid-template-columns: 1fr; }
    .services-grid { grid-template-columns: 1fr; }
    .hero-stat-row { gap: 28px; }
    nav { padding: 14px 20px; }
    .guarantee-box { flex-direction: column; gap: 12px; }
  }
</style>
</head>
<body>

<!-- NAV -->
<nav>
  <a class="nav-logo" href="#">Game<span>Mind</span></a>
  <ul class="nav-links">
    <li><a href="#philosophy">理念</a></li>
    <li><a href="#vs">特徴</a></li>
    <li><a href="#plans">料金</a></li>
    <li><a href="#services">サービス</a></li>
    <li><a href="#cta" class="nav-cta">無料相談</a></li>
  </ul>
</nav>

<!-- HERO -->
<section id="hero">
  <div class="hero-glow"></div>
  <div class="hero-inner">
    <div class="hero-badge">APEX LEGENDS / VALORANT / STREET FIGHTER 6 対応</div>
    <h1 class="hero-title">
      ゲームで、<br>
      <span class="line2">人間が育つ。</span>
    </h1>
    <p class="hero-sub">
      <strong>ゲームスキルと人間力を同時に磨く</strong>──<br>
      GameMindは、好きなことを極めながら<br>
      社会で通用する力を身につける場所です。
    </p>
    <div class="hero-ctas">
      <a href="#cta" class="btn-primary">無料相談をする</a>
      <a href="#cta" class="btn-line">📲 LINEで相談</a>
    </div>
    <div class="hero-stat-row">
      <div class="hero-stat">
        <h3>1<span>on</span>1</h3>
        <p>完全マンツーマン指導</p>
      </div>
      <div class="hero-stat">
        <h3>3<span>プラン</span></h3>
        <p>¥14,000〜 ライフスタイルに合わせて</p>
      </div>
      <div class="hero-stat">
        <h3>3<span>タイトル</span></h3>
        <p>Apex / VALORANT / SF6 対応</p>
      </div>
    </div>
  </div>
</section>

<!-- TICKER -->
<div class="ticker-wrap">
  <div class="ticker">
    <span class="ticker-item">GAME COACHING <span class="ticker-dot">◆</span></span>
    <span class="ticker-item">1on1 COACHING <span class="ticker-dot">◆</span></span>
    <span class="ticker-item">MINDSET TRAINING <span class="ticker-dot">◆</span></span>
    <span class="ticker-item">HUMAN DEVELOPMENT <span class="ticker-dot">◆</span></span>
    <span class="ticker-item">RANK UP SUPPORT <span class="ticker-dot">◆</span></span>
    <span class="ticker-item">GAME COACHING <span class="ticker-dot">◆</span></span>
    <span class="ticker-item">1on1 COACHING <span class="ticker-dot">◆</span></span>
    <span class="ticker-item">MINDSET TRAINING <span class="ticker-dot">◆</span></span>
    <span class="ticker-item">HUMAN DEVELOPMENT <span class="ticker-dot">◆</span></span>
    <span class="ticker-item">RANK UP SUPPORT <span class="ticker-dot">◆</span></span>
  </div>
</div>

<!-- PHILOSOPHY -->
<section id="philosophy">
  <div class="section-inner">
    <p class="section-label reveal">PHILOSOPHY</p>
    <h2 class="section-title reveal">理念 ＆ コンセプト</h2>
    <p class="section-desc reveal">GameMindが目指すのは、ゲームを「最適な習い事の文化」として社会に根付かせること。</p>

    <div class="phil-cards reveal">
      <div class="phil-card">
        <div class="phil-card-num">— 理念 —</div>
        <h3>ゲームを、<em>最適な習い事の</em><br>文化を創る。</h3>
        <p>ゲームは努力・戦略・チームワークを鍛える力を持っている。GameMindはゲームを「単なる娯楽」から「人間を育てる最良の習い事」へと昇華させ、その文化を社会に根付かせることを目指す。</p>
      </div>
      <div class="phil-card">
        <div class="phil-card-num">— コンセプト —</div>
        <h3>ゲームスキルと<br><em>人間力を同時に磨く。</em></h3>
        <p>ゲームが持つ弊害（他責・利己・無計画）を意図的に矯正しながら、ゲームの上達と人間としての成長を同時に実現する。好きなことを極めながら、社会に貢献できる人間を育てる。</p>
      </div>
    </div>
  </div>
</section>

<!-- VS TABLE -->
<section id="vs">
  <div class="section-inner">
    <p class="section-label reveal">TRANSFORMATION</p>
    <h2 class="section-title reveal">GameMindで<span>変わるもの</span></h2>
    <p class="section-desc reveal">ゲームの弊害を逆手に取り、人間力へと転換します。</p>

    <div class="reveal">
      <table class="vs-table">
        <thead>
          <tr>
            <th>ゲームが生む弊害</th>
            <th>GameMindで育てるもの</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td>他責・言い訳グセ</td>
            <td>✦ 自己責任・原因分析力</td>
          </tr>
          <tr>
            <td>利己的なプレイスタイル</td>
            <td>✦ 協調性・チームへの貢献意識</td>
          </tr>
          <tr>
            <td>感情的・衝動的な判断</td>
            <td>✦ 冷静な判断・感情コントロール</td>
          </tr>
          <tr>
            <td>なんとなくプレイの繰り返し</td>
            <td>✦ 目標設定・PDCAを回す習慣</td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</section>

<!-- PLANS -->
<section id="plans">
  <div class="section-inner">
    <p class="section-label reveal">PRICING</p>
    <h2 class="section-title reveal">料金<span>プラン</span></h2>
    <p class="section-desc reveal">ライフスタイルに合わせて3プランからお選びいただけます。</p>

    <p class="section-desc reveal" style="font-size:0.82rem; margin-top:-32px; margin-bottom:12px;">
      ※ 10:00〜18:00 のセッションは全プラン <strong style="color:var(--accent)">−1,500円</strong> で受講できます。<br>
      曜日固定制・振替は月1回まで・有効期限は1ヶ月です。
    </p>

    <div class="plans-grid reveal">
      <!-- LIGHT -->
      <div class="plan-card">
        <div class="plan-name">LIGHT</div>
        <div class="plan-price">¥14,000<span>/月</span></div>
        <div class="plan-freq">月2回（2時間利用可）</div>
        <div class="plan-divider"></div>
        <ul class="plan-features">
          <li>マンツーマンコーチング × 2回</li>
          <li>練習メニューの提供</li>
          <li>マインドセット指導</li>
          <li>受講者限定カジュアル大会</li>
        </ul>
        <a href="#cta" class="plan-cta plan-cta-outline">お試し・忙しい方向け</a>
      </div>

      <!-- NORMAL -->
      <div class="plan-card featured">
        <div class="plan-badge">RECOMMENDED</div>
        <div class="plan-name">NORMAL</div>
        <div class="plan-price">¥18,000<span>/月</span></div>
        <div class="plan-freq">月3回</div>
        <div class="plan-divider"></div>
        <ul class="plan-features">
          <li>マンツーマンコーチング × 3回</li>
          <li>練習メニューの提供</li>
          <li>マインドセット指導</li>
          <li>受講者限定カジュアル大会</li>
          <li>Discord進捗管理</li>
        </ul>
        <a href="#cta" class="plan-cta plan-cta-filled">最も選ばれているプラン</a>
      </div>

      <!-- PROFESSIONAL -->
      <div class="plan-card">
        <div class="plan-name">PROFESSIONAL</div>
        <div class="plan-price">¥22,000<span>/月</span></div>
        <div class="plan-freq">月4回</div>
        <div class="plan-divider"></div>
        <ul class="plan-features">
          <li>マンツーマンコーチング × 4回</li>
          <li>練習メニューの提供</li>
          <li>マインドセット指導</li>
          <li>受講者限定カジュアル大会</li>
          <li>Discord進捗管理</li>
          <li>追加セッション ¥7,000/回</li>
        </ul>
        <a href="#cta" class="plan-cta plan-cta-outline">本気で上達したい方向け</a>
      </div>
    </div>

  </div>
</section>

<!-- SERVICES -->
<section id="services">
  <div class="section-inner">
    <p class="section-label reveal">SERVICES</p>
    <h2 class="section-title reveal">サービス<span>内容</span></h2>
    <p class="section-desc reveal">ランクアップに必要なスキルとマインドを、体系的にサポートします。</p>

    <div class="services-grid reveal">
      <div class="service-card">
        <div class="service-icon">🎮</div>
        <h3>マンツーマンゲームコーチング</h3>
        <p>専属コーチによる60分の個別セッション。プレイ分析から弱点特定、改善策の提示まで、あなたに最適化されたコーチングを提供します。</p>
      </div>
      <div class="service-card">
        <div class="service-icon">🧠</div>
        <h3>マインドセット動画（個別作成）</h3>
        <p>あなたの課題に合わせて個別制作する動画コンテンツ。他責・感情的プレイなどの弊害を矯正し、人間力を同時に高めます。</p>
      </div>
      <div class="service-card">
        <div class="service-icon">📋</div>
        <h3>オーダーメイド練習メニュー</h3>
        <p>使える時間とプレイスタイルに合わせた練習メニューを毎月提供。効率的に弱点を克服し、最短でランクアップを実現します。</p>
      </div>
      <div class="service-card">
        <div class="service-icon">🏆</div>
        <h3>受講者限定カジュアル大会</h3>
        <p>受講生同士で切磋琢磨できる限定大会を定期開催。実戦経験を積みながら、仲間とのつながりも育てます。</p>
      </div>
    </div>
  </div>
</section>

<!-- CTA -->
<section id="cta">
  <div class="section-inner">
    <p class="section-label reveal">GET STARTED</p>
    <p class="cta-copy reveal">まずは、<span>無料相談</span>から<br>はじめましょう。</p>
    <p class="cta-sub reveal">LINEで気軽にご相談いただけます。<br>未成年の方は保護者の方もお気軽にどうぞ。</p>
    <div class="cta-btns reveal">
      <a href="#" class="btn-primary">無料相談フォームへ</a>
      <a href="#" class="btn-line">📲 LINEで相談する</a>
    </div>
    <p class="cta-guarantee reveal">未成年の方は保護者の方もお気軽にどうぞ</p>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <div class="footer-logo">Game<span>Mind</span></div>
  <div class="footer-tagline">ゲームスキルと人間力を同時に磨く</div>
  <ul class="footer-links">
    <li><a href="#philosophy">理念</a></li>
    <li><a href="#vs">特徴</a></li>
    <li><a href="#plans">料金</a></li>
    <li><a href="#services">サービス</a></li>
    <li><a href="#cta">お問い合わせ</a></li>
    <li><a href="#tokushoho">特定商取引法に基づく表記</a></li>
  </ul>
  <small>© 2025 GameMind. All rights reserved.</small>
</footer>

<!-- 特定商取引法に基づく表記 -->
<section id="tokushoho" style="background:var(--bg); border-top:1px solid rgba(43,79,212,0.2); padding:80px 40px;">
  <div class="section-inner" style="max-width:800px;">
    <p class="section-label">LEGAL</p>
    <h2 class="section-title" style="font-size:1.6rem; margin-bottom:32px;">特定商取引法に基づく表記</h2>

    <table style="width:100%; border-collapse:collapse; font-size:0.88rem; line-height:1.9;">
      <tbody>
        <tr style="border-bottom:1px solid rgba(43,79,212,0.12);">
          <th style="padding:14px 16px; text-align:left; color:var(--text-muted); font-weight:700; width:36%; vertical-align:top; white-space:nowrap;">事業者名</th>
          <td style="padding:14px 16px; color:var(--text);">GameMind（ゲームマインド）</td>
        </tr>
        <tr style="border-bottom:1px solid rgba(43,79,212,0.12);">
          <th style="padding:14px 16px; text-align:left; color:var(--text-muted); font-weight:700; vertical-align:top;">運営責任者</th>
          <td style="padding:14px 16px; color:var(--text);">（お問い合わせ時にお知らせいたします）</td>
        </tr>
        <tr style="border-bottom:1px solid rgba(43,79,212,0.12);">
          <th style="padding:14px 16px; text-align:left; color:var(--text-muted); font-weight:700; vertical-align:top;">所在地</th>
          <td style="padding:14px 16px; color:var(--text);">（請求があった場合、遅滞なく開示いたします）</td>
        </tr>
        <tr style="border-bottom:1px solid rgba(43,79,212,0.12);">
          <th style="padding:14px 16px; text-align:left; color:var(--text-muted); font-weight:700; vertical-align:top;">お問い合わせ</th>
          <td style="padding:14px 16px; color:var(--text);">X（旧Twitter）@game_taxin へのDM、またはLINEにてご連絡ください</td>
        </tr>
        <tr style="border-bottom:1px solid rgba(43,79,212,0.12);">
          <th style="padding:14px 16px; text-align:left; color:var(--text-muted); font-weight:700; vertical-align:top;">販売価格</th>
          <td style="padding:14px 16px; color:var(--text);">
            ライトプラン：¥14,000／月<br>
            ノーマルプラン：¥18,000／月<br>
            プロフェッショナルプラン：¥22,000／月<br>
            追加セッション：¥7,000／回<br>
            ※ 10:00〜18:00 のセッションは全プラン −1,500円
          </td>
        </tr>
        <tr style="border-bottom:1px solid rgba(43,79,212,0.12);">
          <th style="padding:14px 16px; text-align:left; color:var(--text-muted); font-weight:700; vertical-align:top;">料金以外の費用</th>
          <td style="padding:14px 16px; color:var(--text);">通信費・利用端末等はお客様のご負担となります</td>
        </tr>
        <tr style="border-bottom:1px solid rgba(43,79,212,0.12);">
          <th style="padding:14px 16px; text-align:left; color:var(--text-muted); font-weight:700; vertical-align:top;">支払い方法</th>
          <td style="padding:14px 16px; color:var(--text);">詳細は無料相談時にご案内いたします</td>
        </tr>
        <tr style="border-bottom:1px solid rgba(43,79,212,0.12);">
          <th style="padding:14px 16px; text-align:left; color:var(--text-muted); font-weight:700; vertical-align:top;">支払い時期</th>
          <td style="padding:14px 16px; color:var(--text);">入会確定時</td>
        </tr>
        <tr style="border-bottom:1px solid rgba(43,79,212,0.12);">
          <th style="padding:14px 16px; text-align:left; color:var(--text-muted); font-weight:700; vertical-align:top;">サービス提供時期</th>
          <td style="padding:14px 16px; color:var(--text);">入会確定・お支払い確認後、日程調整のうえ速やかに開始いたします</td>
        </tr>
        <tr style="border-bottom:1px solid rgba(43,79,212,0.12);">
          <th style="padding:14px 16px; text-align:left; color:var(--text-muted); font-weight:700; vertical-align:top;">返品・キャンセル</th>
          <td style="padding:14px 16px; color:var(--text);">
            サービスの性質上、原則として入会後のキャンセル・返金はお受けしておりません。詳細はお問い合わせください。
          </td>
        </tr>
        <tr style="border-bottom:1px solid rgba(43,79,212,0.12);">
          <th style="padding:14px 16px; text-align:left; color:var(--text-muted); font-weight:700; vertical-align:top;">有効期限・その他</th>
          <td style="padding:14px 16px; color:var(--text);">有効期限は1ヶ月、曜日固定制、振替は月1回まで</td>
        </tr>
        <tr>
          <th style="padding:14px 16px; text-align:left; color:var(--text-muted); font-weight:700; vertical-align:top;">未成年の方</th>
          <td style="padding:14px 16px; color:var(--text);">未成年の方が入会される場合は、保護者の方の同意が必要です</td>
        </tr>
      </tbody>
    </table>

    <!-- 商標・免責事項 -->
    <div style="margin-top:56px; padding-top:32px; border-top:1px solid rgba(43,79,212,0.12);">
      <p style="font-size:0.78rem; color:var(--text-muted); line-height:2; font-weight:300;">
        <strong style="color:var(--text-muted); font-weight:700;">【商標・著作権に関する表記】</strong><br>
        「Apex Legends」は Electronic Arts Inc. の登録商標です。<br>
        「VALORANT」は Riot Games, Inc. の登録商標です。<br>
        「ストリートファイター6（Street Fighter 6）」は株式会社カプコンの登録商標です。<br>
        「Discord」は Discord Inc. の商標です。<br>
        「LINE」は LINE ヤフー株式会社の商標または登録商標です。<br>
        「X（旧Twitter）」は X Corp. の商標または登録商標です。<br>
        当サービスは上記各社と一切関係ありません。各ゲームタイトルはコーチング対象として記載しているものであり、各社の公認・推薦を意味するものではありません。
      </p>
      <p style="font-size:0.78rem; color:var(--text-muted); line-height:2; font-weight:300; margin-top:16px;">
        <strong style="color:var(--text-muted); font-weight:700;">【免責事項】</strong><br>
        ゲームのランクやスキルの向上は個人差があり、すべての方に同等の成果を保証するものではありません。当サービスを利用したことによる損害・不利益について、運営は一切の責任を負いかねます。<br>
        料金・サービス内容・規約は予告なく変更される場合があります。最新情報は必ずお問い合わせにてご確認ください。
      </p>
    </div>
  </div>
</section>

<script>
  // Intersection Observer for reveal animations
  const reveals = document.querySelectorAll('.reveal');
  const observer = new IntersectionObserver((entries) => {
    entries.forEach((entry, i) => {
      if (entry.isIntersecting) {
        setTimeout(() => entry.target.classList.add('visible'), i * 80);
        observer.unobserve(entry.target);
      }
    });
  }, { threshold: 0.1 });
  reveals.forEach(el => observer.observe(el));
</script>
</body>
</html>
