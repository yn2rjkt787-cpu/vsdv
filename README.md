<!DOCTYPE html>
<html lang="ko">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>같이뛰자 — 풋살 & 축구 즉석 팀 매칭</title>
<style>
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  :root {
    --green: #1D9E75;
    --green-dark: #0F6E56;
    --green-deeper: #085041;
    --green-light: #E1F5EE;
    --green-mid: #9FE1CB;
    --amber: #EF9F27;
    --amber-light: #FAEEDA;
    --amber-dark: #854F0B;
    --red-light: #FCEBEB;
    --red-dark: #A32D2D;
    --forest-light: #EAF3DE;
    --forest-dark: #3B6D11;
    --bg: #F7F8F6;
    --surface: #FFFFFF;
    --border: rgba(0,0,0,0.1);
    --text-primary: #1A1A18;
    --text-secondary: #5F5E5A;
    --text-muted: #888780;
    --radius-sm: 8px;
    --radius-md: 12px;
    --radius-lg: 16px;
    --radius-full: 9999px;
  }

  body {
    font-family: -apple-system, BlinkMacSystemFont, 'Pretendard', 'Apple SD Gothic Neo', sans-serif;
    background: var(--bg);
    color: var(--text-primary);
    line-height: 1.6;
    min-height: 100vh;
  }

  /* NAV */
  nav {
    position: sticky;
    top: 0;
    background: rgba(255,255,255,0.92);
    backdrop-filter: blur(12px);
    border-bottom: 0.5px solid var(--border);
    z-index: 100;
    padding: 0 2rem;
    height: 56px;
    display: flex;
    align-items: center;
    justify-content: space-between;
  }
  .nav-logo {
    font-size: 18px;
    font-weight: 700;
    color: var(--green-dark);
    letter-spacing: -0.5px;
    text-decoration: none;
  }
  .nav-logo span { color: var(--text-primary); }
  .nav-links { display: flex; align-items: center; gap: 8px; }
  .nav-link {
    color: var(--text-secondary);
    text-decoration: none;
    font-size: 14px;
    padding: 6px 12px;
    border-radius: var(--radius-sm);
    transition: background 0.15s;
  }
  .nav-link:hover { background: var(--green-light); color: var(--green-dark); }
  .nav-cta {
    background: var(--green);
    color: #fff;
    border: none;
    padding: 8px 18px;
    border-radius: var(--radius-full);
    font-size: 14px;
    font-weight: 500;
    cursor: pointer;
    text-decoration: none;
    transition: background 0.15s;
  }
  .nav-cta:hover { background: var(--green-dark); }

  /* HERO */
  .hero {
    background: linear-gradient(160deg, var(--green) 0%, var(--green-deeper) 100%);
    padding: 5rem 2rem 4rem;
    text-align: center;
    position: relative;
    overflow: hidden;
  }
  .hero::before {
    content: '';
    position: absolute;
    top: -80px; right: -80px;
    width: 360px; height: 360px;
    border-radius: 50%;
    background: rgba(255,255,255,0.05);
  }
  .hero::after {
    content: '';
    position: absolute;
    bottom: -100px; left: -60px;
    width: 280px; height: 280px;
    border-radius: 50%;
    background: rgba(255,255,255,0.04);
  }
  .hero-badge {
    display: inline-block;
    background: rgba(255,255,255,0.15);
    color: #fff;
    font-size: 12px;
    padding: 4px 14px;
    border-radius: var(--radius-full);
    border: 0.5px solid rgba(255,255,255,0.3);
    margin-bottom: 1.25rem;
    letter-spacing: 0.5px;
  }
  .hero h1 {
    font-size: clamp(2rem, 5vw, 3rem);
    font-weight: 700;
    color: #fff;
    letter-spacing: -1px;
    line-height: 1.15;
    margin-bottom: 1rem;
  }
  .hero h1 em { font-style: normal; color: #9FE1CB; }
  .hero p {
    font-size: 1.05rem;
    color: rgba(255,255,255,0.8);
    max-width: 480px;
    margin: 0 auto 2rem;
  }
  .hero-btns {
    display: flex;
    gap: 12px;
    justify-content: center;
    flex-wrap: wrap;
  }
  .btn-hero-primary {
    background: #fff;
    color: var(--green-dark);
    border: none;
    padding: 13px 28px;
    border-radius: var(--radius-full);
    font-size: 15px;
    font-weight: 600;
    cursor: pointer;
    text-decoration: none;
    transition: transform 0.15s, box-shadow 0.15s;
    box-shadow: 0 2px 12px rgba(0,0,0,0.15);
    display: inline-flex;
    align-items: center;
    gap: 6px;
  }
  .btn-hero-primary:hover { transform: translateY(-1px); box-shadow: 0 4px 20px rgba(0,0,0,0.2); }
  .btn-hero-secondary {
    background: transparent;
    color: #fff;
    border: 1.5px solid rgba(255,255,255,0.5);
    padding: 13px 28px;
    border-radius: var(--radius-full);
    font-size: 15px;
    cursor: pointer;
    text-decoration: none;
    transition: background 0.15s;
    display: inline-flex;
    align-items: center;
    gap: 6px;
  }
  .btn-hero-secondary:hover { background: rgba(255,255,255,0.12); }
  .hero-stats {
    display: flex;
    justify-content: center;
    gap: 3rem;
    margin-top: 3rem;
    padding-top: 2rem;
    border-top: 0.5px solid rgba(255,255,255,0.15);
  }
  .stat-item { text-align: center; }
  .stat-number { font-size: 1.6rem; font-weight: 700; color: #fff; }
  .stat-label { font-size: 12px; color: rgba(255,255,255,0.65); margin-top: 2px; }

  /* MAIN LAYOUT */
  .container {
    max-width: 1080px;
    margin: 0 auto;
    padding: 0 1.5rem;
  }

  /* FILTER + FEED */
  .feed-section { padding: 2.5rem 0; }
  .section-header {
    display: flex;
    align-items: center;
    justify-content: space-between;
    margin-bottom: 1.25rem;
  }
  .section-title {
    font-size: 18px;
    font-weight: 600;
    color: var(--text-primary);
    display: flex;
    align-items: center;
    gap: 8px;
  }
  .section-title .dot {
    width: 8px; height: 8px;
    border-radius: 50%;
    background: var(--green);
    animation: pulse 2s infinite;
  }
  @keyframes pulse {
    0%, 100% { opacity: 1; }
    50% { opacity: 0.4; }
  }
  .see-all {
    font-size: 13px;
    color: var(--green);
    text-decoration: none;
    font-weight: 500;
  }
  .see-all:hover { text-decoration: underline; }

  .filter-bar {
    display: flex;
    gap: 8px;
    flex-wrap: wrap;
    margin-bottom: 1.5rem;
    align-items: center;
  }
  .filter-label { font-size: 13px; color: var(--text-muted); }
  .filter-btn {
    background: var(--surface);
    border: 0.5px solid var(--border);
    color: var(--text-secondary);
    padding: 6px 16px;
    border-radius: var(--radius-full);
    font-size: 13px;
    cursor: pointer;
    transition: all 0.15s;
    font-family: inherit;
  }
  .filter-btn:hover { border-color: var(--green); color: var(--green); }
  .filter-btn.active {
    background: var(--green);
    color: #fff;
    border-color: var(--green);
  }

  .cards-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
    gap: 14px;
  }
  .match-card {
    background: var(--surface);
    border: 0.5px solid var(--border);
    border-radius: var(--radius-lg);
    padding: 1.25rem;
    cursor: pointer;
    transition: transform 0.15s, box-shadow 0.15s, border-color 0.15s;
    text-decoration: none;
    display: block;
  }
  .match-card:hover {
    transform: translateY(-2px);
    box-shadow: 0 6px 24px rgba(0,0,0,0.08);
    border-color: var(--green-mid);
  }
  .card-top {
    display: flex;
    justify-content: space-between;
    align-items: flex-start;
    margin-bottom: 12px;
  }
  .card-title {
    font-size: 15px;
    font-weight: 600;
    color: var(--text-primary);
    line-height: 1.35;
    flex: 1;
    padding-right: 8px;
  }
  .level-badge {
    font-size: 11px;
    padding: 3px 10px;
    border-radius: var(--radius-full);
    font-weight: 600;
    white-space: nowrap;
    flex-shrink: 0;
  }
  .level-low { background: var(--forest-light); color: var(--forest-dark); }
  .level-mid { background: var(--amber-light); color: var(--amber-dark); }
  .level-high { background: var(--red-light); color: var(--red-dark); }

  .card-meta {
    display: flex;
    flex-direction: column;
    gap: 6px;
    margin-bottom: 14px;
  }
  .meta-row {
    display: flex;
    align-items: center;
    gap: 7px;
    font-size: 13px;
    color: var(--text-secondary);
  }
  .meta-icon { font-size: 14px; flex-shrink: 0; }
  .meta-icon.green { color: var(--green); }

  .card-footer {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding-top: 12px;
    border-top: 0.5px solid var(--border);
  }
  .slots { font-size: 13px; color: var(--text-secondary); }
  .slots strong { color: var(--green); font-weight: 600; }
  .host-row { display: flex; align-items: center; gap: 8px; }
  .avatar {
    width: 28px; height: 28px;
    border-radius: 50%;
    background: var(--green-light);
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 11px;
    font-weight: 600;
    color: var(--green-deeper);
    flex-shrink: 0;
  }
  .host-info { display: flex; flex-direction: column; }
  .host-name { font-size: 12px; color: var(--text-secondary); line-height: 1.2; }
  .manner { font-size: 11px; color: var(--amber); font-weight: 600; }

  /* FEATURES */
  .features-section {
    padding: 3rem 0;
    background: var(--surface);
    border-top: 0.5px solid var(--border);
    border-bottom: 0.5px solid var(--border);
  }
  .features-intro {
    text-align: center;
    margin-bottom: 2.5rem;
  }
  .features-intro h2 {
    font-size: 1.7rem;
    font-weight: 700;
    color: var(--text-primary);
    letter-spacing: -0.5px;
    margin-bottom: 0.5rem;
  }
  .features-intro p {
    font-size: 15px;
    color: var(--text-secondary);
  }
  .features-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
    gap: 16px;
  }
  .feature-card {
    background: var(--bg);
    border-radius: var(--radius-lg);
    padding: 1.5rem;
    border: 0.5px solid var(--border);
    transition: border-color 0.15s;
  }
  .feature-card:hover { border-color: var(--green-mid); }
  .feature-icon-wrap {
    width: 44px; height: 44px;
    border-radius: var(--radius-md);
    background: var(--green-light);
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 22px;
    margin-bottom: 14px;
  }
  .feature-title {
    font-size: 15px;
    font-weight: 600;
    color: var(--text-primary);
    margin-bottom: 6px;
  }
  .feature-desc {
    font-size: 13px;
    color: var(--text-secondary);
    line-height: 1.6;
  }

  /* HOW IT WORKS */
  .how-section { padding: 3rem 0; }
  .how-section h2 {
    font-size: 1.5rem;
    font-weight: 700;
    text-align: center;
    margin-bottom: 2rem;
    letter-spacing: -0.3px;
  }
  .tabs {
    display: flex;
    justify-content: center;
    gap: 4px;
    margin-bottom: 2rem;
  }
  .tab-btn {
    padding: 8px 20px;
    border-radius: var(--radius-full);
    font-size: 14px;
    border: 0.5px solid var(--border);
    background: var(--surface);
    color: var(--text-secondary);
    cursor: pointer;
    font-family: inherit;
    transition: all 0.15s;
  }
  .tab-btn.active {
    background: var(--green);
    color: #fff;
    border-color: var(--green);
  }
  .flow-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(130px, 1fr));
    gap: 0;
    position: relative;
  }
  .flow-grid::before {
    content: '';
    position: absolute;
    top: 20px;
    left: 10%;
    right: 10%;
    height: 1px;
    background: linear-gradient(to right, var(--green-light), var(--green), var(--green-light));
    z-index: 0;
  }
  .flow-step {
    display: flex;
    flex-direction: column;
    align-items: center;
    text-align: center;
    position: relative;
    z-index: 1;
    padding: 0 0.5rem;
  }
  .step-num {
    width: 40px; height: 40px;
    border-radius: 50%;
    background: var(--green);
    color: #fff;
    font-size: 14px;
    font-weight: 700;
    display: flex;
    align-items: center;
    justify-content: center;
    margin-bottom: 10px;
    border: 3px solid var(--bg);
  }
  .step-label {
    font-size: 12px;
    color: var(--text-secondary);
    line-height: 1.4;
  }
  .step-label strong {
    display: block;
    font-size: 13px;
    font-weight: 600;
    color: var(--text-primary);
    margin-bottom: 2px;
  }

  /* WRITE FORM */
  .write-section { padding: 2.5rem 0; }
  .write-card {
    background: var(--surface);
    border: 0.5px solid var(--border);
    border-radius: var(--radius-lg);
    padding: 2rem;
    max-width: 640px;
    margin: 0 auto;
  }
  .write-card h3 {
    font-size: 16px;
    font-weight: 600;
    margin-bottom: 1.25rem;
    color: var(--text-primary);
    display: flex;
    align-items: center;
    gap: 8px;
  }
  .form-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 12px;
    margin-bottom: 12px;
  }
  .form-field { display: flex; flex-direction: column; gap: 5px; }
  .form-field.full { grid-column: 1 / -1; }
  label { font-size: 12px; color: var(--text-secondary); font-weight: 500; }
  input, select, textarea {
    border: 0.5px solid var(--border);
    border-radius: var(--radius-sm);
    padding: 9px 12px;
    font-size: 14px;
    font-family: inherit;
    color: var(--text-primary);
    background: var(--bg);
    transition: border-color 0.15s;
    outline: none;
  }
  input:focus, select:focus, textarea:focus {
    border-color: var(--green);
    background: var(--surface);
  }
  textarea { resize: vertical; min-height: 80px; }
  .submit-btn {
    width: 100%;
    background: var(--green);
    color: #fff;
    border: none;
    padding: 13px;
    border-radius: var(--radius-md);
    font-size: 15px;
    font-weight: 600;
    cursor: pointer;
    font-family: inherit;
    margin-top: 8px;
    transition: background 0.15s;
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 8px;
  }
  .submit-btn:hover { background: var(--green-dark); }

  /* FOOTER */
  footer {
    background: var(--green-deeper);
    color: rgba(255,255,255,0.7);
    padding: 2.5rem 2rem;
    margin-top: 3rem;
    text-align: center;
  }
  .footer-logo {
    font-size: 20px;
    font-weight: 700;
    color: #fff;
    margin-bottom: 0.5rem;
  }
  .footer-desc {
    font-size: 13px;
    color: rgba(255,255,255,0.55);
    margin-bottom: 1.25rem;
  }
  .footer-links {
    display: flex;
    justify-content: center;
    gap: 1.5rem;
    flex-wrap: wrap;
  }
  .footer-links a {
    color: rgba(255,255,255,0.6);
    text-decoration: none;
    font-size: 13px;
  }
  .footer-links a:hover { color: #fff; }
  .footer-copy {
    margin-top: 1.5rem;
    font-size: 12px;
    color: rgba(255,255,255,0.35);
  }

  /* RESPONSIVE */
  @media (max-width: 600px) {
    nav { padding: 0 1rem; }
    .hero { padding: 3.5rem 1.25rem 2.5rem; }
    .hero-stats { gap: 1.5rem; }
    .container { padding: 0 1rem; }
    .form-grid { grid-template-columns: 1fr; }
    .flow-grid::before { display: none; }
    .write-card { padding: 1.25rem; }
    .tabs { flex-wrap: wrap; }
  }
</style>
</head>
<body>

<!-- NAV -->
<nav>
  <a href="#" class="nav-logo">같이<span>뛰자</span> ⚽</a>
  <div class="nav-links">
    <a href="#feed" class="nav-link">경기 찾기</a>
    <a href="#features" class="nav-link">기능</a>
    <a href="#write" class="nav-link">모집 글 쓰기</a>
    <a href="#write" class="nav-cta">+ 모집 시작</a>
  </div>
</nav>

<!-- HERO -->
<section class="hero">
  <div class="hero-badge">⚡ 오늘 뛸 사람, 지금 찾자</div>
  <h1>풋살/축구 팀원 구하기<br><em>5분이면 충분해</em></h1>
  <p>지역·실력·매너 필터로 딱 맞는 팀원을 즉석 매칭. 카톡 단체방 공지는 이제 그만.</p>
  <div class="hero-btns">
    <a href="#write" class="btn-hero-primary">✏️ 모집 글 쓰기</a>
    <a href="#feed" class="btn-hero-secondary">🔍 경기 찾기</a>
  </div>
  <div class="hero-stats">
    <div class="stat-item">
      <div class="stat-number">1,240+</div>
      <div class="stat-label">이번 달 경기</div>
    </div>
    <div class="stat-item">
      <div class="stat-number">8,500+</div>
      <div class="stat-label">가입 유저</div>
    </div>
    <div class="stat-item">
      <div class="stat-number">4.7★</div>
      <div class="stat-label">평균 매너 점수</div>
    </div>
  </div>
</section>

<!-- FEED -->
<section class="feed-section" id="feed">
  <div class="container">
    <div class="section-header">
      <div class="section-title">
        <span class="dot"></span>
        지금 모집 중인 경기
      </div>
      <a href="#" class="see-all">전체 보기 →</a>
    </div>

    <div class="filter-bar">
      <span class="filter-label">필터:</span>
      <button class="filter-btn active" onclick="setFilter(this)">전체</button>
      <button class="filter-btn" onclick="setFilter(this)">5vs5</button>
      <button class="filter-btn" onclick="setFilter(this)">6vs6</button>
      <button class="filter-btn" onclick="setFilter(this)">11vs11</button>
      <button class="filter-btn" onclick="setFilter(this)">초급</button>
      <button class="filter-btn" onclick="setFilter(this)">중급</button>
      <button class="filter-btn" onclick="setFilter(this)">고급</button>
      <button class="filter-btn" onclick="setFilter(this)">오늘만</button>
    </div>

    <div class="cards-grid">
      <!-- Card 1 -->
      <a href="#" class="match-card">
        <div class="card-top">
          <div class="card-title">강남구 6vs6 번개 경기</div>
          <span class="level-badge level-mid">중급</span>
        </div>
        <div class="card-meta">
          <div class="meta-row"><span class="meta-icon green">📅</span> 오늘 (6/15) 오후 7:00</div>
          <div class="meta-row"><span class="meta-icon green">📍</span> 삼성동 풋살파크 A구장</div>
          <div class="meta-row"><span class="meta-icon green">💰</span> 참가비 5,000원</div>
        </div>
        <div class="card-footer">
          <div class="slots">잔여 <strong>2자리</strong> / 6명</div>
          <div class="host-row">
            <div class="avatar">박민</div>
            <div class="host-info">
              <span class="host-name">박민준</span>
              <span class="manner">★ 4.8</span>
            </div>
          </div>
        </div>
      </a>

      <!-- Card 2 -->
      <a href="#" class="match-card">
        <div class="card-top">
          <div class="card-title">신촌 5vs5 — 초보 환영</div>
          <span class="level-badge level-low">초급</span>
        </div>
        <div class="card-meta">
          <div class="meta-row"><span class="meta-icon green">📅</span> 내일 (6/16) 오전 10:00</div>
          <div class="meta-row"><span class="meta-icon green">📍</span> 서대문 실내풋살장</div>
          <div class="meta-row"><span class="meta-icon green">💰</span> 무료</div>
        </div>
        <div class="card-footer">
          <div class="slots">잔여 <strong>4자리</strong> / 5명</div>
          <div class="host-row">
            <div class="avatar">이수</div>
            <div class="host-info">
              <span class="host-name">이수현</span>
              <span class="manner">★ 4.5</span>
            </div>
          </div>
        </div>
      </a>

      <!-- Card 3 -->
      <a href="#" class="match-card">
        <div class="card-top">
          <div class="card-title">잠실 11vs11 주말 리그전</div>
          <span class="level-badge level-high">고급</span>
        </div>
        <div class="card-meta">
          <div class="meta-row"><span class="meta-icon green">📅</span> 6/21 (토) 오후 2:00</div>
          <div class="meta-row"><span class="meta-icon green">📍</span> 잠실 천연잔디구장</div>
          <div class="meta-row"><span class="meta-icon green">💰</span> 참가비 10,000원</div>
        </div>
        <div class="card-footer">
          <div class="slots">잔여 <strong>3자리</strong> / 11명</div>
          <div class="host-row">
            <div class="avatar">김도</div>
            <div class="host-info">
              <span class="host-name">김도현</span>
              <span class="manner">★ 4.9</span>
            </div>
          </div>
        </div>
      </a>

      <!-- Card 4 -->
      <a href="#" class="match-card">
        <div class="card-top">
          <div class="card-title">마포 6vs6 — 직장인 모임</div>
          <span class="level-badge level-mid">중급</span>
        </div>
        <div class="card-meta">
          <div class="meta-row"><span class="meta-icon green">📅</span> 6/17 (수) 오후 8:00</div>
          <div class="meta-row"><span class="meta-icon green">📍</span> 마포 하늘공원 풋살장</div>
          <div class="meta-row"><span class="meta-icon green">💰</span> 참가비 8,000원</div>
        </div>
        <div class="card-footer">
          <div class="slots">잔여 <strong>1자리</strong> / 6명</div>
          <div class="host-row">
            <div class="avatar">최준</div>
            <div class="host-info">
              <span class="host-name">최준혁</span>
              <span class="manner">★ 4.6</span>
            </div>
          </div>
        </div>
      </a>

      <!-- Card 5 -->
      <a href="#" class="match-card">
        <div class="card-top">
          <div class="card-title">성동구 5vs5 퇴근 번개</div>
          <span class="level-badge level-low">초급</span>
        </div>
        <div class="card-meta">
          <div class="meta-row"><span class="meta-icon green">📅</span> 오늘 (6/15) 오후 9:00</div>
          <div class="meta-row"><span class="meta-icon green">📍</span> 성수 실내풋살파크</div>
          <div class="meta-row"><span class="meta-icon green">💰</span> 참가비 3,000원</div>
        </div>
        <div class="card-footer">
          <div class="slots">잔여 <strong>3자리</strong> / 5명</div>
          <div class="host-row">
            <div class="avatar">정소</div>
            <div class="host-info">
              <span class="host-name">정소연</span>
              <span class="manner">★ 4.7</span>
            </div>
          </div>
        </div>
      </a>

      <!-- Card 6 -->
      <a href="#" class="match-card">
        <div class="card-top">
          <div class="card-title">용산 동아리 연습 상대 구함</div>
          <span class="level-badge level-high">고급</span>
        </div>
        <div class="card-meta">
          <div class="meta-row"><span class="meta-icon green">📅</span> 6/20 (금) 오후 6:30</div>
          <div class="meta-row"><span class="meta-icon green">📍</span> 용산 인조잔디구장</div>
          <div class="meta-row"><span class="meta-icon green">💰</span> 무료 (용병 환영)</div>
        </div>
        <div class="card-footer">
          <div class="slots">잔여 <strong>5자리</strong> / 11명</div>
          <div class="host-row">
            <div class="avatar">한FC</div>
            <div class="host-info">
              <span class="host-name">한강FC</span>
              <span class="manner">★ 4.9</span>
            </div>
          </div>
        </div>
      </a>
    </div>
  </div>
</section>

<!-- FEATURES -->
<section class="features-section" id="features">
  <div class="container">
    <div class="features-intro">
      <h2>왜 같이뛰자인가?</h2>
      <p>카톡방 공지, 당근마켓 글쓰기 — 이제 그런 불편함은 끝.</p>
    </div>
    <div class="features-grid">
      <div class="feature-card">
        <div class="feature-icon-wrap">⚡</div>
        <div class="feature-title">즉석 매칭 게시판</div>
        <div class="feature-desc">오늘 저녁도 OK. 지역·인원·시간 딱 맞는 경기를 바로 찾아 신청.</div>
      </div>
      <div class="feature-card">
        <div class="feature-icon-wrap">🏅</div>
        <div class="feature-title">실력 레벨 시스템</div>
        <div class="feature-desc">초급·중급·고급 태그로 비슷한 실력끼리 매칭. 경기 후 상호 평가로 자동 조정.</div>
      </div>
      <div class="feature-card">
        <div class="feature-icon-wrap">⭐</div>
        <div class="feature-title">매너 평점 시스템</div>
        <div class="feature-desc">경기 후 5점 평가. 노쇼·지각·비매너 참가자는 자동 필터링.</div>
      </div>
      <div class="feature-card">
        <div class="feature-icon-wrap">🗺️</div>
        <div class="feature-title">근처 구장 찾기</div>
        <div class="feature-desc">위치 기반 풋살장 조회, 예약 링크 연동. 구장 찾는 시간도 단축.</div>
      </div>
    </div>
  </div>
</section>

<!-- HOW IT WORKS -->
<section class="how-section">
  <div class="container">
    <h2>이용 방법</h2>
    <div class="tabs">
      <button class="tab-btn active" onclick="setTab(this, 'participant')">참가자</button>
      <button class="tab-btn" onclick="setTab(this, 'host')">주최자</button>
    </div>

    <div id="flow-participant" class="flow-grid">
      <div class="flow-step">
        <div class="step-num">1</div>
        <div class="step-label"><strong>필터 설정</strong>지역·레벨 선택</div>
      </div>
      <div class="flow-step">
        <div class="step-num">2</div>
        <div class="step-label"><strong>경기 선택</strong>카드 클릭</div>
      </div>
      <div class="flow-step">
        <div class="step-num">3</div>
        <div class="step-label"><strong>정보 확인</strong>주최자 매너 확인</div>
      </div>
      <div class="flow-step">
        <div class="step-num">4</div>
        <div class="step-label"><strong>신청</strong>포지션 선택 후 신청</div>
      </div>
      <div class="flow-step">
        <div class="step-num">5</div>
        <div class="step-label"><strong>수락 대기</strong>알림으로 확인</div>
      </div>
      <div class="flow-step">
        <div class="step-num">6</div>
        <div class="step-label"><strong>경기 후</strong>매너 평점 작성</div>
      </div>
    </div>

    <div id="flow-host" class="flow-grid" style="display:none;">
      <div class="flow-step">
        <div class="step-num">1</div>
        <div class="step-label"><strong>카카오 로그인</strong>소셜 로그인</div>
      </div>
      <div class="flow-step">
        <div class="step-num">2</div>
        <div class="step-label"><strong>글 작성</strong>경기 정보 입력</div>
      </div>
      <div class="flow-step">
        <div class="step-num">3</div>
        <div class="step-label"><strong>등록 완료</strong>URL 공유</div>
      </div>
      <div class="flow-step">
        <div class="step-num">4</div>
        <div class="step-label"><strong>신청 관리</strong>수락/거절</div>
      </div>
      <div class="flow-step">
        <div class="step-num">5</div>
        <div class="step-label"><strong>경기 진행</strong>참가자 확정</div>
      </div>
      <div class="flow-step">
        <div class="step-num">6</div>
        <div class="step-label"><strong>평점 작성</strong>참가자 매너 평가</div>
      </div>
    </div>
  </div>
</section>

<!-- WRITE FORM -->
<section class="write-section" id="write">
  <div class="container">
    <div class="section-header" style="justify-content:center; margin-bottom:1.5rem;">
      <div class="section-title" style="justify-content:center;">✏️ 모집 글 작성하기</div>
    </div>
    <div class="write-card">
      <h3>⚽ 경기 정보 입력</h3>
      <div class="form-grid">
        <div class="form-field">
          <label for="gtype">경기 유형</label>
          <select id="gtype">
            <option>5vs5</option>
            <option selected>6vs6</option>
            <option>11vs11</option>
          </select>
        </div>
        <div class="form-field">
          <label for="glevel">참가 레벨</label>
          <select id="glevel">
            <option>초급</option>
            <option selected>중급</option>
            <option>고급</option>
            <option>레벨 무관</option>
          </select>
        </div>
        <div class="form-field">
          <label for="gdate">경기 날짜</label>
          <input type="date" id="gdate" value="2026-06-15" />
        </div>
        <div class="form-field">
          <label for="gtime">시작 시간</label>
          <input type="time" id="gtime" value="19:00" />
        </div>
        <div class="form-field full">
          <label for="gloc">구장 위치</label>
          <input type="text" id="gloc" placeholder="구장명 또는 주소 검색" />
        </div>
        <div class="form-field">
          <label for="gfee">참가비 (0 = 무료)</label>
          <input type="number" id="gfee" placeholder="0" min="0" step="1000" />
        </div>
        <div class="form-field">
          <label for="gslots">모집 인원</label>
          <input type="number" id="gslots" placeholder="6" min="2" max="22" />
        </div>
        <div class="form-field full">
          <label for="gdesc">상세 설명 (준비물, 규칙 등)</label>
          <textarea id="gdesc" placeholder="예) 반바지 지참, 스파이크 착용 불가, 경기 후 뒷풀이 예정"></textarea>
        </div>
      </div>
      <button class="submit-btn" onclick="alert('모집 글이 등록되었습니다! 🎉')">
        모집 글 등록하기 →
      </button>
    </div>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <div class="footer-logo">⚽ 같이뛰자</div>
  <div class="footer-desc">풋살 & 축구 즉석 팀 매칭 플랫폼</div>
  <div class="footer-links">
    <a href="#">서비스 소개</a>
    <a href="#">이용약관</a>
    <a href="#">개인정보처리방침</a>
    <a href="#">문의하기</a>
  </div>
  <div class="footer-copy">© 2026 같이뛰자 · Made by 김민규</div>
</footer>

<script>
  function setFilter(btn) {
    document.querySelectorAll('.filter-btn').forEach(b => b.classList.remove('active'));
    btn.classList.add('active');
  }

  function setTab(btn, type) {
    document.querySelectorAll('.tab-btn').forEach(b => b.classList.remove('active'));
    btn.classList.add('active');
    document.getElementById('flow-participant').style.display = type === 'participant' ? 'grid' : 'none';
    document.getElementById('flow-host').style.display = type === 'host' ? 'grid' : 'none';
  }
</script>
</body>
</html>
