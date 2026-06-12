<!DOCTYPE html>
<html lang="ja">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>マーケティング思考の基礎 × 3C分析 — Instagram運用実践レクチャー | SHO-SAN Marketing Academy</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800;900&family=Noto+Sans+JP:wght@400;500;700;900&family=JetBrains+Mono:wght@400;600&display=swap" rel="stylesheet">
<style>
:root{
  --bg:#09090b;
  --bg-soft:#0e0e13;
  --card:#121218;
  --card-hover:#17171f;
  --border:rgba(255,255,255,.08);
  --border-strong:rgba(255,255,255,.14);
  --text:#ededf0;
  --muted:#9b9ba8;
  --faint:#6b6b78;
  --indigo:#6366f1;
  --violet:#8b5cf6;
  --pink:#ec4899;
  --cyan:#22d3ee;
  --sky:#38bdf8;
  --emerald:#34d399;
  --amber:#fbbf24;
  --rose:#fb7185;
  --grad:linear-gradient(135deg,#6366f1 0%,#a855f7 50%,#ec4899 100%);
  --grad-soft:linear-gradient(135deg,rgba(99,102,241,.15),rgba(168,85,247,.15),rgba(236,72,153,.15));
  --c-customer:#38bdf8;
  --c-competitor:#f472b6;
  --c-company:#34d399;
  --radius:14px;
  --sidebar-w:272px;
}
*{margin:0;padding:0;box-sizing:border-box}
html{scroll-behavior:smooth;scroll-padding-top:32px}
body{
  background:var(--bg);
  color:var(--text);
  font-family:'Inter','Noto Sans JP',sans-serif;
  font-size:15.5px;
  line-height:1.85;
  -webkit-font-smoothing:antialiased;
}
::selection{background:rgba(139,92,246,.4)}
a{color:var(--sky);text-decoration:none}
a:hover{text-decoration:underline}

/* ===== Scroll progress ===== */
#progress{position:fixed;top:0;left:0;height:3px;width:0;background:var(--grad);z-index:200;transition:width .1s linear}

/* ===== Layout ===== */
.layout{display:flex;min-height:100vh}
.sidebar{
  position:fixed;top:0;left:0;bottom:0;width:var(--sidebar-w);
  background:rgba(10,10,14,.85);backdrop-filter:blur(14px);
  border-right:1px solid var(--border);
  padding:28px 20px;overflow-y:auto;z-index:100;
  scrollbar-width:thin;scrollbar-color:rgba(255,255,255,.15) transparent;
}
.sidebar::-webkit-scrollbar{width:5px}
.sidebar::-webkit-scrollbar-thumb{background:rgba(255,255,255,.12);border-radius:3px}
.logo{display:flex;align-items:center;gap:10px;margin-bottom:6px}
.logo-mark{
  width:34px;height:34px;border-radius:9px;background:var(--grad);
  display:flex;align-items:center;justify-content:center;
  font-weight:900;font-size:15px;color:#fff;letter-spacing:-.5px;
  box-shadow:0 4px 18px rgba(139,92,246,.45);
}
.logo-text{font-weight:800;font-size:14px;letter-spacing:.02em}
.logo-sub{font-size:10.5px;color:var(--faint);letter-spacing:.14em;text-transform:uppercase;margin-bottom:26px;padding-left:44px}
.nav-group{margin-bottom:20px}
.nav-label{font-size:10.5px;font-weight:700;color:var(--faint);text-transform:uppercase;letter-spacing:.12em;padding:0 10px;margin-bottom:6px}
.nav a{
  display:flex;align-items:center;gap:8px;
  padding:6.5px 10px;border-radius:8px;
  color:var(--muted);font-size:13px;font-weight:500;
  border-left:2px solid transparent;border-radius:0 8px 8px 0;
  transition:all .15s;
}
.nav a:hover{color:var(--text);background:rgba(255,255,255,.04);text-decoration:none}
.nav a.active{color:#fff;background:rgba(139,92,246,.12);border-left-color:var(--violet)}
.nav a .n{font-family:'JetBrains Mono',monospace;font-size:10px;color:var(--faint);min-width:20px}
.nav a.active .n{color:var(--violet)}

.main{margin-left:var(--sidebar-w);flex:1;min-width:0}
.container{max-width:920px;margin:0 auto;padding:0 48px 120px}

/* ===== Hero ===== */
.hero{
  position:relative;padding:110px 0 80px;overflow:hidden;
}
.hero-glow{
  position:absolute;top:-220px;left:50%;transform:translateX(-50%);
  width:900px;height:520px;border-radius:50%;
  background:radial-gradient(ellipse,rgba(99,102,241,.22),rgba(168,85,247,.12) 45%,transparent 70%);
  pointer-events:none;
}
.hero-badge{
  display:inline-flex;align-items:center;gap:8px;
  padding:6px 14px;border-radius:999px;
  background:rgba(139,92,246,.12);border:1px solid rgba(139,92,246,.35);
  font-size:12px;font-weight:600;color:#c4b5fd;letter-spacing:.04em;
  margin-bottom:24px;
}
.hero-badge .dot{width:7px;height:7px;border-radius:50%;background:var(--violet);box-shadow:0 0 10px var(--violet);animation:pulse 2s infinite}
@keyframes pulse{0%,100%{opacity:1}50%{opacity:.4}}
.hero h1{
  font-size:clamp(34px,4.6vw,52px);font-weight:900;line-height:1.25;
  letter-spacing:-.02em;margin-bottom:8px;
}
.grad-text{background:var(--grad);-webkit-background-clip:text;background-clip:text;color:transparent}
.hero-sub{font-size:17px;color:var(--muted);max-width:640px;margin-top:18px}
.hero-meta{display:flex;flex-wrap:wrap;gap:10px;margin-top:30px}
.meta-chip{
  display:inline-flex;align-items:center;gap:7px;padding:7px 14px;
  border:1px solid var(--border);border-radius:999px;
  background:var(--card);font-size:12.5px;color:var(--muted);font-weight:500;
}
.meta-chip b{color:var(--text);font-weight:600}

/* ===== Sections ===== */
section{padding-top:72px}
.part-chip{
  display:inline-flex;align-items:center;gap:10px;
  font-family:'JetBrains Mono',monospace;font-size:12px;font-weight:600;
  letter-spacing:.18em;color:var(--violet);margin-bottom:14px;
}
.part-chip::after{content:"";width:48px;height:1px;background:linear-gradient(90deg,var(--violet),transparent)}
h2{font-size:clamp(26px,3.2vw,34px);font-weight:900;letter-spacing:-.01em;line-height:1.35;margin-bottom:14px}
h3{font-size:21px;font-weight:800;margin:48px 0 14px;letter-spacing:-.01em;display:flex;align-items:center;gap:10px}
h3 .hash{color:var(--violet);font-weight:700}
h4{font-size:16.5px;font-weight:700;margin:28px 0 10px}
p{margin-bottom:14px;color:#c8c8d2}
p b,li b{color:var(--text)}
.lead{font-size:16.5px;color:var(--muted)}
ul.list,ol.list{margin:0 0 16px 22px;color:#c8c8d2}
ul.list li,ol.list li{margin-bottom:8px}
.divider{height:1px;background:linear-gradient(90deg,transparent,var(--border-strong),transparent);margin:64px 0 0}

/* ===== Cards ===== */
.card{
  background:var(--card);border:1px solid var(--border);border-radius:var(--radius);
  padding:24px 26px;margin:18px 0;
  transition:border-color .2s, transform .2s;
}
.card:hover{border-color:var(--border-strong)}
.card-title{font-size:15px;font-weight:700;margin-bottom:8px;display:flex;align-items:center;gap:9px}
.card p:last-child{margin-bottom:0}
.grid2{display:grid;grid-template-columns:1fr 1fr;gap:16px;margin:18px 0}
.grid3{display:grid;grid-template-columns:repeat(3,1fr);gap:16px;margin:18px 0}
.grid2 .card,.grid3 .card{margin:0}
.icon{
  width:30px;height:30px;border-radius:8px;display:inline-flex;align-items:center;justify-content:center;
  font-size:15px;flex-shrink:0;
}

/* ===== Callouts ===== */
.callout{
  display:flex;gap:14px;padding:18px 20px;border-radius:12px;margin:18px 0;
  border:1px solid;font-size:14.5px;
}
.callout .ci{font-size:17px;line-height:1.6}
.callout p{margin:0;color:inherit}
.callout-info{background:rgba(56,189,248,.07);border-color:rgba(56,189,248,.25);color:#bae6fd}
.callout-warn{background:rgba(251,191,36,.06);border-color:rgba(251,191,36,.25);color:#fde68a}
.callout-danger{background:rgba(251,113,133,.07);border-color:rgba(251,113,133,.28);color:#fecdd3}
.callout-success{background:rgba(52,211,153,.07);border-color:rgba(52,211,153,.25);color:#a7f3d0}
.callout b{color:#fff}

/* ===== Quote / point ===== */
.keypoint{
  position:relative;border-radius:var(--radius);padding:26px 28px;margin:24px 0;
  background:var(--grad-soft);border:1px solid rgba(139,92,246,.3);
}
.keypoint::before{
  content:"KEY POINT";position:absolute;top:-9px;left:20px;
  font-family:'JetBrains Mono',monospace;font-size:10px;font-weight:700;letter-spacing:.18em;
  background:var(--bg);color:var(--violet);padding:2px 10px;border:1px solid rgba(139,92,246,.4);border-radius:999px;
}
.keypoint p{margin:0;font-size:16px;font-weight:600;color:#fff;line-height:1.9}

/* ===== Tables ===== */
.table-wrap{overflow-x:auto;margin:18px 0;border:1px solid var(--border);border-radius:12px}
table{width:100%;border-collapse:collapse;font-size:13.5px;min-width:560px}
th{
  background:var(--bg-soft);text-align:left;padding:12px 16px;
  font-size:11.5px;font-weight:700;letter-spacing:.06em;color:var(--muted);text-transform:uppercase;
  border-bottom:1px solid var(--border-strong);white-space:nowrap;
}
td{padding:13px 16px;border-bottom:1px solid var(--border);color:#c8c8d2;vertical-align:top}
tr:last-child td{border-bottom:none}
tr:hover td{background:rgba(255,255,255,.02)}
td b{color:var(--text)}
.tag{
  display:inline-block;padding:2.5px 10px;border-radius:999px;font-size:11px;font-weight:700;letter-spacing:.03em;white-space:nowrap;
}
.tag-sky{background:rgba(56,189,248,.13);color:#7dd3fc;border:1px solid rgba(56,189,248,.3)}
.tag-pink{background:rgba(244,114,182,.13);color:#f9a8d4;border:1px solid rgba(244,114,182,.3)}
.tag-green{background:rgba(52,211,153,.13);color:#6ee7b7;border:1px solid rgba(52,211,153,.3)}
.tag-amber{background:rgba(251,191,36,.13);color:#fcd34d;border:1px solid rgba(251,191,36,.3)}
.tag-violet{background:rgba(139,92,246,.15);color:#c4b5fd;border:1px solid rgba(139,92,246,.35)}
.tag-gray{background:rgba(255,255,255,.06);color:var(--muted);border:1px solid var(--border)}

/* ===== Steps ===== */
.steps{counter-reset:step;margin:22px 0}
.step{
  display:flex;gap:18px;padding:20px 0;border-bottom:1px dashed var(--border);
}
.step:last-child{border-bottom:none}
.step-num{
  counter-increment:step;flex-shrink:0;
  width:40px;height:40px;border-radius:11px;background:var(--grad);
  display:flex;align-items:center;justify-content:center;
  font-weight:800;font-size:16px;color:#fff;
  box-shadow:0 4px 14px rgba(139,92,246,.35);
}
.step-num::before{content:counter(step)}
.step-body h4{margin:4px 0 6px;font-size:16px}
.step-body p{margin-bottom:0;font-size:14.5px;color:var(--muted)}

/* ===== Accordion ===== */
.acc{border:1px solid var(--border);border-radius:12px;margin:12px 0;background:var(--card);overflow:hidden}
.acc-head{
  width:100%;display:flex;align-items:center;justify-content:space-between;gap:12px;
  padding:16px 20px;background:none;border:none;cursor:pointer;
  color:var(--text);font-family:inherit;font-size:14.5px;font-weight:700;text-align:left;
}
.acc-head:hover{background:rgba(255,255,255,.025)}
.acc-head .chev{transition:transform .25s;color:var(--faint);flex-shrink:0}
.acc.open .chev{transform:rotate(90deg)}
.acc-body{max-height:0;overflow:hidden;transition:max-height .35s ease}
.acc-body-inner{padding:2px 20px 18px;font-size:14px;color:var(--muted)}
.acc-body-inner p{font-size:14px}

/* ===== Tabs ===== */
.tabs{margin:20px 0}
.tab-btns{display:flex;gap:6px;border-bottom:1px solid var(--border);flex-wrap:wrap}
.tab-btn{
  padding:10px 18px;background:none;border:none;border-bottom:2px solid transparent;
  color:var(--muted);font-family:inherit;font-size:13.5px;font-weight:600;cursor:pointer;
  margin-bottom:-1px;transition:all .15s;
}
.tab-btn:hover{color:var(--text)}
.tab-btn.active{color:#fff;border-bottom-color:var(--violet)}
.tab-panel{display:none;padding:20px 4px 0}
.tab-panel.active{display:block;animation:fadeIn .3s}
@keyframes fadeIn{from{opacity:0;transform:translateY(5px)}to{opacity:1;transform:none}}

/* ===== Figure / SVG ===== */
.figure{
  background:var(--bg-soft);border:1px solid var(--border);border-radius:var(--radius);
  padding:28px;margin:22px 0;overflow-x:auto;
}
.figure svg{display:block;margin:0 auto;max-width:100%;height:auto}
.fig-cap{
  text-align:center;font-size:12px;color:var(--faint);margin-top:14px;
  font-family:'JetBrains Mono',monospace;letter-spacing:.05em;
}

/* ===== KPI cards ===== */
.kpi-row{display:grid;grid-template-columns:repeat(4,1fr);gap:12px;margin:18px 0}
.kpi{
  background:var(--card);border:1px solid var(--border);border-radius:12px;padding:16px;text-align:center;
}
.kpi .kv{font-size:22px;font-weight:900;font-family:'Inter',sans-serif;letter-spacing:-.02em}
.kpi .kl{font-size:11px;color:var(--muted);margin-top:4px;font-weight:600}
.kpi .kn{font-size:10.5px;color:var(--faint);margin-top:2px}

/* ===== Worksheet ===== */
.worksheet{
  border:1px dashed rgba(139,92,246,.5);border-radius:var(--radius);
  background:rgba(139,92,246,.05);padding:26px 28px;margin:24px 0;
}
.worksheet h4{margin-top:0;display:flex;align-items:center;gap:8px}
.ws-line{border-bottom:1px solid rgba(255,255,255,.12);height:34px;margin:8px 0}

/* ===== Footer ===== */
.footer{
  margin-top:90px;padding:36px 0;border-top:1px solid var(--border);
  display:flex;justify-content:space-between;align-items:center;gap:16px;flex-wrap:wrap;
  color:var(--faint);font-size:12.5px;
}

/* ===== Back to top ===== */
#toTop{
  position:fixed;bottom:28px;right:28px;width:44px;height:44px;border-radius:12px;
  background:var(--card);border:1px solid var(--border-strong);color:var(--text);
  font-size:18px;cursor:pointer;opacity:0;pointer-events:none;transition:all .25s;z-index:150;
}
#toTop.show{opacity:1;pointer-events:auto}
#toTop:hover{background:var(--card-hover);transform:translateY(-2px)}

/* ===== Responsive ===== */
@media(max-width:1080px){
  .sidebar{display:none}
  .main{margin-left:0}
  .container{padding:0 22px 90px}
  .grid2,.grid3,.kpi-row{grid-template-columns:1fr}
  .hero{padding:70px 0 50px}
}
</style>
</head>
<body>

<div id="progress"></div>

<div class="layout">

<!-- ============ SIDEBAR ============ -->
<aside class="sidebar">
  <div class="logo">
    <div class="logo-mark">S</div>
    <div class="logo-text">SHO-SAN</div>
  </div>
  <div class="logo-sub">Marketing Academy</div>

  <nav class="nav">
    <div class="nav-group">
      <div class="nav-label">Introduction</div>
      <a href="#intro"><span class="n">00</span>マーケティングとは何か</a>
    </div>
    <div class="nav-group">
      <div class="nav-label">Part 1 — 基礎の基礎</div>
      <a href="#frameworks"><span class="n">01</span>フレームワークという武器</a>
      <a href="#funnel"><span class="n">02</span>ファネル分析</a>
      <a href="#ulssas"><span class="n">03</span>SNS時代：ULSSAS</a>
      <a href="#w5h1"><span class="n">04</span>5W1H／ロジックツリー</a>
      <a href="#map"><span class="n">05</span>フレームワーク全体地図</a>
    </div>
    <div class="nav-group">
      <div class="nav-label">Part 2 — 3C分析 深堀り</div>
      <a href="#c3-what"><span class="n">06</span>3C分析とは</a>
      <a href="#c3-customer"><span class="n">07</span>Customer：市場・顧客</a>
      <a href="#c3-competitor"><span class="n">08</span>Competitor：競合</a>
      <a href="#c3-company"><span class="n">09</span>Company：自社</a>
      <a href="#c3-ksf"><span class="n">10</span>クロス3C → KSF</a>
      <a href="#c3-fails"><span class="n">11</span>よくある失敗</a>
    </div>
    <div class="nav-group">
      <div class="nav-label">Part 3 — Instagram実践</div>
      <a href="#case"><span class="n">12</span>ケース：工務店</a>
      <a href="#case-3c"><span class="n">13</span>工務店の3C分析</a>
      <a href="#case-strategy"><span class="n">14</span>アカウント戦略設計</a>
      <a href="#case-kpi"><span class="n">15</span>KPI設計と運用</a>
    </div>
    <div class="nav-group">
      <div class="nav-label">Closing</div>
      <a href="#worksheet"><span class="n">16</span>ワークシート</a>
      <a href="#summary"><span class="n">17</span>まとめ</a>
    </div>
  </nav>
</aside>

<!-- ============ MAIN ============ -->
<div class="main">
<div class="container">

<!-- ============ HERO ============ -->
<header class="hero">
  <div class="hero-glow"></div>
  <div class="hero-badge"><span class="dot"></span>SHO-SAN MARKETING ACADEMY — INTERNAL LECTURE</div>
  <h1>マーケティング思考の基礎<br>× <span class="grad-text">3C分析</span>で勝つ<br>Instagram運用</h1>
  <p class="hero-sub">フレームワークを「知っている」から「使って成果を出す」へ。新人・若手のための、現場で本当に使えるマーケティング思考レクチャー。</p>
  <div class="hero-meta">
    <span class="meta-chip">対象：<b>新人〜1年目マーケター</b></span>
    <span class="meta-chip">所要時間：<b>約60分</b></span>
    <span class="meta-chip">実践例：<b>工務店のInstagram運用</b></span>
    <span class="meta-chip">レベル：<b>基礎 → 実務</b></span>
  </div>
</header>

<!-- ============ INTRO ============ -->
<section id="intro">
  <div class="part-chip">INTRODUCTION</div>
  <h2>マーケティングとは「売れる仕組み」をつくること</h2>
  <p class="lead">最初に、すべての土台になる定義を揃えます。ここがズレると、この後のフレームワークが全部「作業」になってしまうからです。</p>

  <p>経営学者ピーター・ドラッカーは <b>「マーケティングの理想は、販売（セリング）を不要にすることだ」</b> と言いました。つまりマーケティングとは、広告を打つことでも、投稿をバズらせることでもなく、<b>「顧客を深く理解し、顧客が自然に『欲しい』と思う状態を設計すること」</b>です。</p>

  <p>Instagram運用も同じです。フォロワーを増やすことが目的ではありません。<b>「誰の、どんな悩みに、自社のどんな価値を届け、最終的にどんな行動（来店・問い合わせ・購入）をしてもらうか」</b>という仕組み全体を設計するのが、私たちの仕事です。</p>

  <div class="keypoint">
    <p>マーケティング = 「売り込む技術」ではなく「選ばれる構造」をつくる仕事。<br>そして優れたマーケターは、センスではなく<b>「思考の型（フレームワーク）」</b>で構造をつくる。</p>
  </div>

  <div class="grid3">
    <div class="card">
      <div class="card-title"><span class="icon" style="background:rgba(56,189,248,.15)">🎯</span>このレクチャーのゴール①</div>
      <p style="font-size:13.5px;color:var(--muted)">主要フレームワークの「位置づけ」が分かり、状況に応じて使い分けられる</p>
    </div>
    <div class="card">
      <div class="card-title"><span class="icon" style="background:rgba(139,92,246,.15)">🔍</span>ゴール②</div>
      <p style="font-size:13.5px;color:var(--muted)">3C分析を「埋める」のではなく「KSF（成功要因）を導く」ために使えるようになる</p>
    </div>
    <div class="card">
      <div class="card-title"><span class="icon" style="background:rgba(236,72,153,.15)">📱</span>ゴール③</div>
      <p style="font-size:13.5px;color:var(--muted)">明日から担当アカウント（Instagram）の戦略を3Cで説明できるようになる</p>
    </div>
  </div>
</section>

<div class="divider"></div>

<!-- ============ PART 1 ============ -->
<section id="frameworks">
  <div class="part-chip">PART 01 — 基礎の基礎</div>
  <h2>フレームワークという「思考の武器」</h2>
  <p class="lead">フレームワークとは、優秀な先人たちが「考えるべき論点」をパターン化してくれた思考の地図です。ただし、地図は眺めるものではなく、目的地に着くために使うもの。</p>

  <h3><span class="hash">#</span>なぜフレームワークを使うのか</h3>
  <div class="grid3">
    <div class="card">
      <div class="card-title"><span class="icon" style="background:rgba(56,189,248,.15)">🧩</span>抜け漏れを防ぐ</div>
      <p style="font-size:13.5px;color:var(--muted)">人間の思考は必ず偏ります。MECE（漏れなくダブりなく）な型に沿うことで、「競合を見ていなかった」「顧客の声を聞いていなかった」を防げる。</p>
    </div>
    <div class="card">
      <div class="card-title"><span class="icon" style="background:rgba(139,92,246,.15)">🗣️</span>共通言語になる</div>
      <p style="font-size:13.5px;color:var(--muted)">「3Cで言うとCompetitorの分析が弱い」と一言で伝わる。チーム・クライアントとの議論速度が劇的に上がる。</p>
    </div>
    <div class="card">
      <div class="card-title"><span class="icon" style="background:rgba(52,211,153,.15)">🔁</span>再現性が生まれる</div>
      <p style="font-size:13.5px;color:var(--muted)">「たまたま当たった施策」を「狙って当てる施策」に変える。成功も失敗も、型があるから振り返れる。</p>
    </div>
  </div>

  <div class="callout callout-warn">
    <span class="ci">⚠️</span>
    <p><b>最重要の注意：フレームワークは「穴埋めゲーム」ではない。</b>枠を埋めて満足するのが三流、埋めた情報から「だから何をすべきか（So What?）」を導くのがプロ。常に「この分析は意思決定を変えるか？」と自問すること。</p>
  </div>
</section>

<section id="funnel">
  <div class="part-chip">PART 01 — 基礎の基礎</div>
  <h2>ファネル分析 — 顧客は階段を登ってくる</h2>
  <p class="lead">顧客は「知らない」状態から、いきなり「買う」には飛びません。認知 → 興味 → 比較検討 → 行動という階段を登ります。この階段を漏斗（ファネル）の形で可視化したのがファネル分析です。</p>

  <div class="figure">
    <svg viewBox="0 0 760 400" xmlns="http://www.w3.org/2000/svg" font-family="Inter,'Noto Sans JP',sans-serif">
      <defs>
        <linearGradient id="f1" x1="0" y1="0" x2="1" y2="0"><stop offset="0" stop-color="#38bdf8"/><stop offset="1" stop-color="#22d3ee"/></linearGradient>
        <linearGradient id="f2" x1="0" y1="0" x2="1" y2="0"><stop offset="0" stop-color="#818cf8"/><stop offset="1" stop-color="#8b5cf6"/></linearGradient>
        <linearGradient id="f3" x1="0" y1="0" x2="1" y2="0"><stop offset="0" stop-color="#a855f7"/><stop offset="1" stop-color="#d946ef"/></linearGradient>
        <linearGradient id="f4" x1="0" y1="0" x2="1" y2="0"><stop offset="0" stop-color="#ec4899"/><stop offset="1" stop-color="#fb7185"/></linearGradient>
      </defs>
      <!-- funnel -->
      <polygon points="120,40 520,40 470,110 170,110" fill="url(#f1)" opacity="0.9"/>
      <polygon points="178,126 462,126 412,196 228,196" fill="url(#f2)" opacity="0.9"/>
      <polygon points="236,212 404,212 366,282 274,282" fill="url(#f3)" opacity="0.9"/>
      <polygon points="282,298 358,298 336,360 304,360" fill="url(#f4)" opacity="0.95"/>
      <!-- labels inside -->
      <text x="320" y="70" text-anchor="middle" fill="#08222e" font-size="16" font-weight="800">認知（Awareness）</text>
      <text x="320" y="92" text-anchor="middle" fill="#08222e" font-size="12" font-weight="600">リーチ 10,000人</text>
      <text x="320" y="155" text-anchor="middle" fill="#fff" font-size="15" font-weight="800">興味・関心（Interest）</text>
      <text x="320" y="177" text-anchor="middle" fill="#e9e4ff" font-size="12" font-weight="600">プロフィールアクセス 500人</text>
      <text x="320" y="241" text-anchor="middle" fill="#fff" font-size="14" font-weight="800">比較・検討（Consideration）</text>
      <text x="320" y="263" text-anchor="middle" fill="#fbe9ff" font-size="12" font-weight="600">保存・再訪・フォロー 150人</text>
      <text x="320" y="327" text-anchor="middle" fill="#fff" font-size="13" font-weight="800">行動（Action）</text>
      <text x="320" y="346" text-anchor="middle" fill="#ffe3ec" font-size="11.5" font-weight="600">問い合わせ 15人</text>
      <!-- conversion arrows -->
      <g font-family="'JetBrains Mono',monospace" font-size="12" font-weight="600">
        <line x1="560" y1="75" x2="560" y2="155" stroke="#6b6b78" stroke-width="1.5"/>
        <text x="575" y="120" fill="#9b9ba8">CVR 5.0%</text>
        <line x1="560" y1="165" x2="560" y2="245" stroke="#6b6b78" stroke-width="1.5"/>
        <text x="575" y="208" fill="#9b9ba8">CVR 30%</text>
        <line x1="560" y1="255" x2="560" y2="330" stroke="#6b6b78" stroke-width="1.5"/>
        <text x="575" y="296" fill="#9b9ba8">CVR 10%</text>
      </g>
    </svg>
    <div class="fig-cap">FIG.01 — パーチェスファネル（数値はInstagram運用の例）</div>
  </div>

  <h3><span class="hash">#</span>ファネルの本当の使い方：「ボトルネック」を特定する</h3>
  <p>ファネル分析の価値は、きれいな図を描くことではなく、<b>「どの段差で顧客が落ちているか＝ボトルネック」を数字で特定する</b>ことにあります。ボトルネックの場所によって、打つべき施策は全く変わります。</p>

  <div class="table-wrap">
    <table>
      <thead><tr><th>落ちている場所</th><th>診断</th><th>Instagramでの処方箋（例）</th></tr></thead>
      <tbody>
        <tr><td><span class="tag tag-sky">認知 ↓</span></td><td>そもそもリーチが少ない</td><td>リール強化・発見タブ最適化・投稿頻度の見直し</td></tr>
        <tr><td><span class="tag tag-violet">認知→興味 ↓</span></td><td>見られても刺さっていない</td><td>冒頭1秒のフック改善・ターゲットと内容のズレ修正</td></tr>
        <tr><td><span class="tag tag-pink">興味→検討 ↓</span></td><td>プロフィールで離脱</td><td>プロフィール文・ハイライト・フィードの世界観統一</td></tr>
        <tr><td><span class="tag tag-amber">検討→行動 ↓</span></td><td>最後の一押しがない</td><td>CTA設計・限定オファー・問い合わせ導線の簡略化</td></tr>
      </tbody>
    </table>
  </div>

  <div class="callout callout-info">
    <span class="ci">💡</span>
    <p><b>プロの視点：</b>「フォロワーを増やしたい」という依頼が来たら、まずファネルのどこが課題なのかを数字で確認する。実はフォロワー数ではなく「プロフィールアクセス→フォロー転換率」が低いだけ、というケースは非常に多い。</p>
  </div>

  <h3><span class="hash">#</span>購買行動モデルの進化：AIDMA → AISAS</h3>
  <p>ファネルの中身（顧客の行動ステップ）は時代と共に進化してきました。マス広告時代の<b>AIDMA</b>から、ネット時代には<b>AISAS</b>（電通提唱）へ。「Search（検索）」と「Share（共有）」が入ったのが革命でした。</p>

  <div class="grid2">
    <div class="card">
      <div class="card-title"><span class="tag tag-gray">マス広告時代</span>AIDMA</div>
      <p style="font-family:'JetBrains Mono',monospace;font-size:13px;color:var(--sky);margin:10px 0">Attention → Interest → Desire → Memory → Action</p>
      <p style="font-size:13.5px;color:var(--muted)">注意 → 興味 → 欲求 → 記憶 → 購買。テレビCMで見て、覚えて、店で買う時代のモデル。</p>
    </div>
    <div class="card">
      <div class="card-title"><span class="tag tag-violet">ネット時代</span>AISAS</div>
      <p style="font-family:'JetBrains Mono',monospace;font-size:13px;color:var(--pink);margin:10px 0">Attention → Interest → <b>Search</b> → Action → <b>Share</b></p>
      <p style="font-size:13.5px;color:var(--muted)">買う前に「検索」し、買った後に「共有」する。共有が次の誰かのAttentionになる循環が生まれた。</p>
    </div>
  </div>
</section>

<section id="ulssas">
  <div class="part-chip">PART 01 — 基礎の基礎</div>
  <h2>SNS時代の購買行動：ULSSAS（ウルサス）</h2>
  <p class="lead">そしてSNS時代。起点は企業の広告ではなく、<b>一般ユーザーの投稿（UGC）</b>になりました。ホットリンク社が提唱したULSSASは、Instagram運用者なら必修のモデルです。</p>

  <div class="figure">
    <svg viewBox="0 0 760 420" xmlns="http://www.w3.org/2000/svg" font-family="Inter,'Noto Sans JP',sans-serif">
      <defs>
        <marker id="arrV" viewBox="0 0 10 10" refX="8" refY="5" markerWidth="7" markerHeight="7" orient="auto-start-reverse">
          <path d="M0,0 L10,5 L0,10 z" fill="#8b5cf6"/>
        </marker>
        <linearGradient id="nodeg" x1="0" y1="0" x2="1" y2="1"><stop offset="0" stop-color="#1c1c26"/><stop offset="1" stop-color="#15151d"/></linearGradient>
      </defs>
      <!-- cycle arrows (hexagon layout) -->
      <g stroke="#8b5cf6" stroke-width="2" fill="none" opacity="0.85">
        <path d="M 455 80 L 565 145" marker-end="url(#arrV)"/>
        <path d="M 610 195 L 610 250" marker-end="url(#arrV)"/>
        <path d="M 565 300 L 460 363" marker-end="url(#arrV)"/>
        <path d="M 300 363 L 196 301" marker-end="url(#arrV)"/>
        <path d="M 150 250 L 150 195" marker-end="url(#arrV)"/>
        <path d="M 195 145 L 305 81" marker-end="url(#arrV)"/>
      </g>
      <!-- nodes -->
      <g>
        <rect x="305" y="30" width="150" height="62" rx="14" fill="url(#nodeg)" stroke="#38bdf8" stroke-width="1.5"/>
        <text x="380" y="56" text-anchor="middle" fill="#38bdf8" font-size="15" font-weight="800">U：UGC</text>
        <text x="380" y="76" text-anchor="middle" fill="#9b9ba8" font-size="11">ユーザー投稿との出会い</text>

        <rect x="540" y="135" width="150" height="62" rx="14" fill="url(#nodeg)" stroke="#818cf8" stroke-width="1.5"/>
        <text x="615" y="161" text-anchor="middle" fill="#a5b4fc" font-size="15" font-weight="800">L：Like</text>
        <text x="615" y="181" text-anchor="middle" fill="#9b9ba8" font-size="11">いいね・保存で反応</text>

        <rect x="540" y="252" width="150" height="62" rx="14" fill="url(#nodeg)" stroke="#a855f7" stroke-width="1.5"/>
        <text x="615" y="278" text-anchor="middle" fill="#d8b4fe" font-size="15" font-weight="800">S：Search 1</text>
        <text x="615" y="298" text-anchor="middle" fill="#9b9ba8" font-size="11">SNS内で検索（#・発見タブ）</text>

        <rect x="305" y="335" width="150" height="62" rx="14" fill="url(#nodeg)" stroke="#d946ef" stroke-width="1.5"/>
        <text x="380" y="361" text-anchor="middle" fill="#f0abfc" font-size="15" font-weight="800">S：Search 2</text>
        <text x="380" y="381" text-anchor="middle" fill="#9b9ba8" font-size="11">Google等で指名検索</text>

        <rect x="72" y="252" width="150" height="62" rx="14" fill="url(#nodeg)" stroke="#ec4899" stroke-width="1.5"/>
        <text x="147" y="278" text-anchor="middle" fill="#f9a8d4" font-size="15" font-weight="800">A：Action</text>
        <text x="147" y="298" text-anchor="middle" fill="#9b9ba8" font-size="11">購買・来店・問い合わせ</text>

        <rect x="72" y="135" width="150" height="62" rx="14" fill="url(#nodeg)" stroke="#fb7185" stroke-width="1.5"/>
        <text x="147" y="161" text-anchor="middle" fill="#fda4af" font-size="15" font-weight="800">S：Spread</text>
        <text x="147" y="181" text-anchor="middle" fill="#9b9ba8" font-size="11">体験を拡散 → 新たなUGCに</text>
      </g>
      <text x="380" y="225" text-anchor="middle" fill="#6b6b78" font-size="12" font-family="'JetBrains Mono',monospace" letter-spacing="2">ULSSAS CYCLE</text>
    </svg>
    <div class="fig-cap">FIG.02 — ULSSAS：UGCを起点に自走する購買サイクル</div>
  </div>

  <p>ファネル（上から下への一方通行）と決定的に違うのは、<b>Spread（拡散）が次のUGCになり、サイクルが自走する</b>こと。つまりSNSマーケティングの目標は「広告を見せ続けること」ではなく、<b>「お客様が語りたくなる体験と、語りやすい仕掛けをつくり、このサイクルを回し始めること」</b>です。</p>

  <div class="callout callout-success">
    <span class="ci">✅</span>
    <p><b>Instagram運用への示唆：</b>①保存されるコンテンツ＝Like起点をつくる ②ハッシュタグ・位置情報＝Search1で見つかる状態をつくる ③お客様が撮りたくなる体験・メンションしたくなる関係＝Spreadを設計する。この3点セットで考える。</p>
  </div>
</section>

<section id="w5h1">
  <div class="part-chip">PART 01 — 基礎の基礎</div>
  <h2>5W1H と ロジックツリー — 「分解」の基本動作</h2>
  <p class="lead">フレームワーク以前の、思考の基本動作が「分解」です。大きくて曖昧な問題は、小さくて具体的な問題に分解した瞬間に解けるようになります。</p>

  <h3><span class="hash">#</span>5W1H：曖昧さを殺す6つの質問</h3>
  <p>5W1Hは小学生でも知っていますが、プロは<b>「要因の深掘り」と「施策の具体化」の両方</b>に使います。例えば「リールが伸びない」という曖昧な悩みを6つの質問で串刺しにすると：</p>

  <div class="table-wrap">
    <table>
      <thead><tr><th>問い</th><th>視点</th><th>「リールが伸びない」への適用例</th></tr></thead>
      <tbody>
        <tr><td><b>Why</b></td><td>目的・原因</td><td>そもそも何のためのリール？ 伸びない原因は視聴維持率？リーチ？</td></tr>
        <tr><td><b>Who</b></td><td>誰に</td><td>誰に届けたい？ 実際に見ているのは誰？（インサイトで確認）</td></tr>
        <tr><td><b>What</b></td><td>何を</td><td>どんな価値（保存したくなる情報？共感？）を渡せている？</td></tr>
        <tr><td><b>When</b></td><td>いつ</td><td>投稿時間はターゲットの閲覧時間と合っている？</td></tr>
        <tr><td><b>Where</b></td><td>どこで</td><td>発見タブ・リールタブ・フォロワーのどこから見られている？</td></tr>
        <tr><td><b>How</b></td><td>どのように</td><td>冒頭1秒のフック、テロップ、長さ、構成はどうなっている？</td></tr>
      </tbody>
    </table>
  </div>

  <h3><span class="hash">#</span>ロジックツリー：MECEに枝分かれさせる</h3>
  <p>分解を図にしたものがロジックツリー。コツは<b>MECE（ミーシー：Mutually Exclusive, Collectively Exhaustive＝漏れなくダブりなく）</b>に分けること。特に強力なのが「数式分解（KPIツリー）」です。</p>

  <div class="figure">
    <svg viewBox="0 0 760 300" xmlns="http://www.w3.org/2000/svg" font-family="Inter,'Noto Sans JP',sans-serif">
      <defs>
        <linearGradient id="rootg" x1="0" y1="0" x2="1" y2="1"><stop offset="0" stop-color="#6366f1"/><stop offset="1" stop-color="#a855f7"/></linearGradient>
      </defs>
      <g stroke="#3f3f4b" stroke-width="1.5" fill="none">
        <path d="M 175 150 C 220 150 220 70 265 70"/>
        <path d="M 175 150 C 220 150 220 150 265 150"/>
        <path d="M 175 150 C 220 150 220 230 265 230"/>
        <path d="M 455 70 C 495 70 495 45 530 45"/>
        <path d="M 455 70 C 495 70 495 95 530 95"/>
        <path d="M 455 150 C 495 150 495 150 530 150"/>
        <path d="M 455 230 C 495 230 495 205 530 205"/>
        <path d="M 455 230 C 495 230 495 255 530 255"/>
      </g>
      <rect x="35" y="122" width="140" height="56" rx="12" fill="url(#rootg)"/>
      <text x="105" y="146" text-anchor="middle" fill="#fff" font-size="13.5" font-weight="800">問い合わせ数</text>
      <text x="105" y="164" text-anchor="middle" fill="#e9e4ff" font-size="10.5">＝ 月15件 → 30件へ</text>
      <g>
        <rect x="265" y="44" width="190" height="50" rx="10" fill="#15151d" stroke="#38bdf8" stroke-width="1.2"/>
        <text x="360" y="65" text-anchor="middle" fill="#7dd3fc" font-size="12.5" font-weight="700">リーチ数</text>
        <text x="360" y="82" text-anchor="middle" fill="#9b9ba8" font-size="10">どれだけの人に届いたか</text>
        <rect x="265" y="124" width="190" height="50" rx="10" fill="#15151d" stroke="#a855f7" stroke-width="1.2"/>
        <text x="360" y="145" text-anchor="middle" fill="#d8b4fe" font-size="12.5" font-weight="700">× プロフィール遷移率</text>
        <text x="360" y="162" text-anchor="middle" fill="#9b9ba8" font-size="10">興味を持たれたか</text>
        <rect x="265" y="204" width="190" height="50" rx="10" fill="#15151d" stroke="#ec4899" stroke-width="1.2"/>
        <text x="360" y="225" text-anchor="middle" fill="#f9a8d4" font-size="12.5" font-weight="700">× 問い合わせ転換率</text>
        <text x="360" y="242" text-anchor="middle" fill="#9b9ba8" font-size="10">行動につながったか</text>
      </g>
      <g font-size="11" fill="#9b9ba8">
        <rect x="530" y="28" width="200" height="34" rx="8" fill="#101016" stroke="#26262f"/>
        <text x="630" y="49" text-anchor="middle">フォロワー外リーチ（発見・リール）</text>
        <rect x="530" y="78" width="200" height="34" rx="8" fill="#101016" stroke="#26262f"/>
        <text x="630" y="99" text-anchor="middle">フォロワー内リーチ（ホーム率）</text>
        <rect x="530" y="133" width="200" height="34" rx="8" fill="#101016" stroke="#26262f"/>
        <text x="630" y="154" text-anchor="middle">投稿の質 × プロフィールの魅力</text>
        <rect x="530" y="188" width="200" height="34" rx="8" fill="#101016" stroke="#26262f"/>
        <text x="630" y="209" text-anchor="middle">CTA・ハイライト・導線設計</text>
        <rect x="530" y="238" width="200" height="34" rx="8" fill="#101016" stroke="#26262f"/>
        <text x="630" y="259" text-anchor="middle">オファー（無料相談・資料）の魅力</text>
      </g>
    </svg>
    <div class="fig-cap">FIG.03 — KPIツリー：「問い合わせ数」の数式分解</div>
  </div>

  <div class="callout callout-info">
    <span class="ci">💡</span>
    <p><b>掛け算で分解する理由：</b>「問い合わせ = リーチ × プロフ遷移率 × 転換率」と数式にすると、どの変数が一番低いか（＝ボトルネック）が一目で分かり、改善インパクトを試算できる。足し算分解より圧倒的に実務で使える。</p>
  </div>
</section>

<section id="map">
  <div class="part-chip">PART 01 — 基礎の基礎</div>
  <h2>フレームワーク全体地図 — 3Cはどこにいる？</h2>
  <p class="lead">マーケティングのフレームワークは無数にありますが、実は「環境分析 → 戦略 → 施策 → 検証」という一本の流れの中に整理できます。3Cはこの流れの<b>心臓部＝環境分析の中核</b>です。</p>

  <div class="figure">
    <svg viewBox="0 0 760 250" xmlns="http://www.w3.org/2000/svg" font-family="Inter,'Noto Sans JP',sans-serif">
      <defs>
        <marker id="arrG" viewBox="0 0 10 10" refX="8" refY="5" markerWidth="8" markerHeight="8" orient="auto">
          <path d="M0,0 L10,5 L0,10 z" fill="#6b6b78"/>
        </marker>
      </defs>
      <g stroke="#4b4b58" stroke-width="2" fill="none">
        <line x1="178" y1="125" x2="206" y2="125" marker-end="url(#arrG)"/>
        <line x1="368" y1="125" x2="396" y2="125" marker-end="url(#arrG)"/>
        <line x1="558" y1="125" x2="586" y2="125" marker-end="url(#arrG)"/>
      </g>
      <!-- Phase 1 -->
      <rect x="18" y="50" width="160" height="150" rx="14" fill="#121218" stroke="rgba(99,102,241,.5)" stroke-width="1.5"/>
      <text x="98" y="78" text-anchor="middle" fill="#a5b4fc" font-size="11" font-weight="700" letter-spacing="2">STEP 1 環境分析</text>
      <text x="98" y="103" text-anchor="middle" fill="#fff" font-size="14" font-weight="800">市場を知る</text>
      <g font-size="11.5" fill="#9b9ba8">
        <text x="98" y="130" text-anchor="middle">PEST（マクロ環境）</text>
        <text x="98" y="152" text-anchor="middle" fill="#c4b5fd" font-weight="800" font-size="13">★ 3C分析</text>
        <text x="98" y="174" text-anchor="middle">SWOT（整理・統合）</text>
      </g>
      <!-- Phase 2 -->
      <rect x="208" y="50" width="160" height="150" rx="14" fill="#121218" stroke="rgba(168,85,247,.5)" stroke-width="1.5"/>
      <text x="288" y="78" text-anchor="middle" fill="#d8b4fe" font-size="11" font-weight="700" letter-spacing="2">STEP 2 戦略</text>
      <text x="288" y="103" text-anchor="middle" fill="#fff" font-size="14" font-weight="800">戦う場所を決める</text>
      <g font-size="11.5" fill="#9b9ba8">
        <text x="288" y="130" text-anchor="middle">STP</text>
        <text x="288" y="152" text-anchor="middle">セグメント／ターゲット</text>
        <text x="288" y="174" text-anchor="middle">ポジショニング</text>
      </g>
      <!-- Phase 3 -->
      <rect x="398" y="50" width="160" height="150" rx="14" fill="#121218" stroke="rgba(236,72,153,.5)" stroke-width="1.5"/>
      <text x="478" y="78" text-anchor="middle" fill="#f9a8d4" font-size="11" font-weight="700" letter-spacing="2">STEP 3 施策</text>
      <text x="478" y="103" text-anchor="middle" fill="#fff" font-size="14" font-weight="800">打ち手に落とす</text>
      <g font-size="11.5" fill="#9b9ba8">
        <text x="478" y="130" text-anchor="middle">4P / 4C</text>
        <text x="478" y="152" text-anchor="middle">コンテンツ企画</text>
        <text x="478" y="174" text-anchor="middle">アカウント設計</text>
      </g>
      <!-- Phase 4 -->
      <rect x="588" y="50" width="160" height="150" rx="14" fill="#121218" stroke="rgba(52,211,153,.5)" stroke-width="1.5"/>
      <text x="668" y="78" text-anchor="middle" fill="#6ee7b7" font-size="11" font-weight="700" letter-spacing="2">STEP 4 検証</text>
      <text x="668" y="103" text-anchor="middle" fill="#fff" font-size="14" font-weight="800">回して改善する</text>
      <g font-size="11.5" fill="#9b9ba8">
        <text x="668" y="130" text-anchor="middle">KPIツリー</text>
        <text x="668" y="152" text-anchor="middle">ファネル分析</text>
        <text x="668" y="174" text-anchor="middle">PDCA / 5W1H</text>
      </g>
    </svg>
    <div class="fig-cap">FIG.04 — フレームワークの全体地図：3Cは戦略の出発点</div>
  </div>

  <div class="table-wrap">
    <table>
      <thead><tr><th>フレームワーク</th><th>一言でいうと</th><th>使うタイミング</th></tr></thead>
      <tbody>
        <tr><td><b>PEST分析</b></td><td>政治・経済・社会・技術のマクロな追い風/向かい風を掴む</td><td>市場参入の検討時、年間計画時</td></tr>
        <tr><td><b style="color:#c4b5fd">3C分析 ★</b></td><td>顧客・競合・自社から「勝てる理由（KSF）」を見つける</td><td><b>戦略を立てる時、必ず最初に</b></td></tr>
        <tr><td><b>SWOT分析</b></td><td>3C等の発見を強み/弱み×機会/脅威に整理し打ち手を出す</td><td>3Cの後の整理・統合</td></tr>
        <tr><td><b>STP</b></td><td>市場を切り分け、狙いを定め、立ち位置を決める</td><td>3Cで掴んだ事実を戦略に変換する時</td></tr>
        <tr><td><b>4P / 4C</b></td><td>製品・価格・流通・販促を顧客視点とセットで設計</td><td>具体的な施策設計時</td></tr>
        <tr><td><b>ファネル / KPIツリー</b></td><td>顧客の階段を数値化しボトルネックを特定</td><td>運用開始後の改善サイクル</td></tr>
      </tbody>
    </table>
  </div>

  <div class="keypoint">
    <p>順番が命。<b>「分析（3C）なしの施策はただのギャンブル、施策に繋がらない分析はただの作文」</b>。<br>だからこそ、すべての起点になる3C分析を徹底的にマスターする。</p>
  </div>
</section>

<div class="divider"></div>

<!-- ============ PART 2 ============ -->
<section id="c3-what">
  <div class="part-chip" style="color:var(--pink)">PART 02 — 3C分析 深堀り</div>
  <h2>3C分析とは — 「勝てる理由」を見つける分析</h2>
  <p class="lead">3C分析は、経営コンサルタント・大前研一氏が世界に広めた戦略フレームワーク。<b>Customer（市場・顧客）、Competitor（競合）、Company（自社）</b>の3視点から事業環境を立体的に捉えます。</p>

  <p>ここで絶対に外してはいけないのが、3C分析の<b>目的</b>です。3つの枠に情報を書き出すことが目的ではありません。3つの円が重なる場所から、<b>KSF（Key Success Factor：その市場で勝つための成功要因）</b>を見つけ出すことが目的です。</p>

  <div class="figure">
    <svg viewBox="0 0 760 480" xmlns="http://www.w3.org/2000/svg" font-family="Inter,'Noto Sans JP',sans-serif">
      <defs>
        <radialGradient id="gc1" cx="0.5" cy="0.5" r="0.5"><stop offset="0" stop-color="#38bdf8" stop-opacity="0.28"/><stop offset="1" stop-color="#38bdf8" stop-opacity="0.07"/></radialGradient>
        <radialGradient id="gc2" cx="0.5" cy="0.5" r="0.5"><stop offset="0" stop-color="#f472b6" stop-opacity="0.28"/><stop offset="1" stop-color="#f472b6" stop-opacity="0.07"/></radialGradient>
        <radialGradient id="gc3" cx="0.5" cy="0.5" r="0.5"><stop offset="0" stop-color="#34d399" stop-opacity="0.28"/><stop offset="1" stop-color="#34d399" stop-opacity="0.07"/></radialGradient>
      </defs>
      <!-- circles -->
      <circle cx="380" cy="170" r="135" fill="url(#gc1)" stroke="#38bdf8" stroke-width="1.8"/>
      <circle cx="295" cy="310" r="135" fill="url(#gc3)" stroke="#34d399" stroke-width="1.8"/>
      <circle cx="465" cy="310" r="135" fill="url(#gc2)" stroke="#f472b6" stroke-width="1.8"/>
      <!-- labels -->
      <text x="380" y="92" text-anchor="middle" fill="#7dd3fc" font-size="17" font-weight="900">Customer</text>
      <text x="380" y="113" text-anchor="middle" fill="#9b9ba8" font-size="12">市場・顧客：何を求めているか</text>
      <text x="218" y="372" text-anchor="middle" fill="#6ee7b7" font-size="17" font-weight="900">Company</text>
      <text x="218" y="393" text-anchor="middle" fill="#9b9ba8" font-size="12">自社：何ができるか</text>
      <text x="545" y="372" text-anchor="middle" fill="#f9a8d4" font-size="17" font-weight="900">Competitor</text>
      <text x="545" y="393" text-anchor="middle" fill="#9b9ba8" font-size="12">競合：何をしているか</text>
      <!-- sweet spot -->
      <g>
        <circle cx="333" cy="243" r="7" fill="#fbbf24"/>
        <circle cx="333" cy="243" r="13" fill="none" stroke="#fbbf24" stroke-width="1.5" opacity="0.5"/>
        <path d="M 333 230 C 330 165 255 140 175 145" stroke="#fbbf24" stroke-width="1.3" fill="none" stroke-dasharray="4 4"/>
        <rect x="30" y="108" width="190" height="74" rx="10" fill="#1a1709" stroke="#fbbf24" stroke-width="1.2"/>
        <text x="125" y="133" text-anchor="middle" fill="#fcd34d" font-size="13" font-weight="800">勝てる領域（KSF）</text>
        <text x="125" y="152" text-anchor="middle" fill="#d9c98a" font-size="10.5">顧客が望み × 自社ができて</text>
        <text x="125" y="168" text-anchor="middle" fill="#d9c98a" font-size="10.5">× 競合がやれていない価値</text>
      </g>
      <!-- danger zone -->
      <g>
        <circle cx="428" cy="243" r="6" fill="#6b6b78"/>
        <path d="M 428 230 C 435 170 520 140 590 145" stroke="#6b6b78" stroke-width="1.2" fill="none" stroke-dasharray="4 4"/>
        <rect x="545" y="108" width="190" height="74" rx="10" fill="#121218" stroke="#3f3f4b" stroke-width="1.2"/>
        <text x="640" y="133" text-anchor="middle" fill="#9b9ba8" font-size="13" font-weight="800">消耗戦の領域</text>
        <text x="640" y="152" text-anchor="middle" fill="#6b6b78" font-size="10.5">顧客が望み、競合もできる</text>
        <text x="640" y="168" text-anchor="middle" fill="#6b6b78" font-size="10.5">→ 価格と物量の勝負になる</text>
      </g>
    </svg>
    <div class="fig-cap">FIG.05 — 3Cの重なりから「勝てる領域」を見つける</div>
  </div>

  <h3><span class="hash">#</span>分析する「順番」がプロと素人を分ける</h3>
  <p>多くの人は書きやすい「自社」から始めますが、これは典型的な間違い。<b>市場は顧客が決める</b>ので、必ず外部環境（Customer → Competitor）から分析し、最後に自社を「相対評価」します。</p>

  <div class="steps">
    <div class="step">
      <div class="step-num"></div>
      <div class="step-body">
        <h4>Customer — 市場・顧客から始める</h4>
        <p>顧客が何を求め、どう行動しているか。すべての判断基準はここ。自社の思い込みではなく、顧客の事実から出発する。</p>
      </div>
    </div>
    <div class="step">
      <div class="step-num"></div>
      <div class="step-body">
        <h4>Competitor — 競合を「顧客の目」で見る</h4>
        <p>その顧客ニーズに対して、競合は何をどこまで提供できているか。空いている場所（=機会）はどこか。</p>
      </div>
    </div>
    <div class="step">
      <div class="step-num"></div>
      <div class="step-body">
        <h4>Company — 最後に自社を相対評価する</h4>
        <p>顧客ニーズと競合の状況を踏まえて初めて、自社の「強み」が決まる。強みとは絶対値ではなく、顧客と競合に対する相対値。</p>
      </div>
    </div>
  </div>

  <div class="callout callout-danger">
    <span class="ci">🚫</span>
    <p><b>「強み」の誤解：</b>「うちは品質に自信がある」は強みではない。顧客がそれを求めていて、競合がそれを提供できていない時に初めて強みになる。<b>強みは自社の中ではなく、顧客と競合との「差分」の中にある。</b></p>
  </div>
</section>

<section id="c3-customer">
  <div class="part-chip" style="color:var(--sky)">PART 02 — 3C分析 深堀り ／ 1つ目のC</div>
  <h2><span style="color:var(--c-customer)">Customer</span> — 市場・顧客分析</h2>
  <p class="lead">Customerは「市場」と「顧客」の2階建てで見ます。マクロ（市場全体の構造）とミクロ（一人の顧客の心理）の両方を行き来できる人が、強いマーケターです。</p>

  <div class="grid2">
    <div class="card" style="border-color:rgba(56,189,248,.3)">
      <div class="card-title"><span class="icon" style="background:rgba(56,189,248,.15)">🌍</span>マクロ：市場を見る</div>
      <ul class="list" style="font-size:13.5px;margin-bottom:0">
        <li><b>市場規模</b>：そのパイはいくらか、何人いるか</li>
        <li><b>成長性</b>：伸びているか、縮んでいるか</li>
        <li><b>購買プロセスの変化</b>：顧客はどこで知り、どこで比較するようになったか</li>
        <li><b>季節性・タイミング</b>：需要の波はいつ来るか</li>
      </ul>
    </div>
    <div class="card" style="border-color:rgba(56,189,248,.3)">
      <div class="card-title"><span class="icon" style="background:rgba(56,189,248,.15)">🧠</span>ミクロ：一人の顧客を見る</div>
      <ul class="list" style="font-size:13.5px;margin-bottom:0">
        <li><b>誰が</b>：デモグラ（年齢・家族構成・年収）＋サイコグラ（価値観）</li>
        <li><b>何に困っていて</b>：解決したい「ジョブ」は何か</li>
        <li><b>何が不安で</b>：購入をためらわせる障壁は何か</li>
        <li><b>どう動くか</b>：情報収集 → 比較 → 決定の実際の行動</li>
      </ul>
    </div>
  </div>

  <h3><span class="hash">#</span>「ニーズ」の一段下、「インサイト」を掘る</h3>
  <p>顧客が口にする要望（ニーズ）の奥には、本人も言語化できていない本音（<b>インサイト</b>）があります。レクチャーで一番覚えてほしい区別がこれです。</p>

  <div class="table-wrap">
    <table>
      <thead><tr><th>層</th><th>例（家づくり検討中の夫婦）</th><th>掘り方</th></tr></thead>
      <tbody>
        <tr><td><span class="tag tag-gray">発言（ウォンツ）</span></td><td>「おしゃれなリビングの施工事例が見たい」</td><td>アンケート・コメントで拾える</td></tr>
        <tr><td><span class="tag tag-sky">ニーズ</span></td><td>「自分たちの予算でどこまでできるか知りたい」</td><td>行動データ（保存・検索ワード）から推測</td></tr>
        <tr><td><span class="tag tag-violet">インサイト</span></td><td>「一生に一度の買い物で<b>絶対に後悔したくない</b>。でも営業されるのが怖くて、まだ会社には接触したくない」</td><td>n=1インタビュー・行動観察・接客現場の声</td></tr>
      </tbody>
    </table>
  </div>

  <div class="callout callout-info">
    <span class="ci">💡</span>
    <p><b>n=1（エヌイチ）分析：</b>1,000人の平均値より、たった1人の本音が戦略を決めることがある。実際に買ってくれたお客様1人に「いつ、何がきっかけで、何と比較して、最後の決め手は何だったか」を聞く。Instagram運用なら、DMや来店客への一言ヒアリングが宝の山。</p>
  </div>

  <h3><span class="hash">#</span>Instagramで使えるCustomerデータ源</h3>
  <ul class="list">
    <li><b>インサイト機能</b>：フォロワーの年齢・性別・地域・アクティブ時間帯</li>
    <li><b>保存数・保存率</b>：「後でじっくり見たい」＝検討度の高さを示す最重要シグナル</li>
    <li><b>コメント・DM・質問スタンプ</b>：顧客の言葉そのもの（言葉遣いごとコンテンツに転用できる）</li>
    <li><b>ハッシュタグ・発見タブの検索行動</b>：顧客が「何と検索して」自分たちに辿り着くか</li>
    <li><b>UGC（お客様の投稿）</b>：顧客が自社の何を「語りたい」と思っているか</li>
  </ul>
</section>

<section id="c3-competitor">
  <div class="part-chip" style="color:var(--pink)">PART 02 — 3C分析 深堀り ／ 2つ目のC</div>
  <h2><span style="color:var(--c-competitor)">Competitor</span> — 競合分析</h2>
  <p class="lead">競合とは「同業他社」ではありません。<b>「顧客がそのお金と時間を使う、他の選択肢すべて」</b>です。この定義を間違えると、見当違いの戦いを始めることになります。</p>

  <div class="grid3">
    <div class="card" style="border-color:rgba(244,114,182,.3)">
      <div class="card-title"><span class="tag tag-pink">直接競合</span></div>
      <p style="font-size:13.5px;color:var(--muted)">同じニーズを同じ手段で満たす相手。<br><b>例：</b>同商圏の他の工務店・ハウスメーカー</p>
    </div>
    <div class="card" style="border-color:rgba(244,114,182,.3)">
      <div class="card-title"><span class="tag tag-pink">間接競合</span></div>
      <p style="font-size:13.5px;color:var(--muted)">同じニーズを別の手段で満たす相手。<br><b>例：</b>建売住宅、中古＋リノベ、「賃貸のまま」という選択</p>
    </div>
    <div class="card" style="border-color:rgba(244,114,182,.3)">
      <div class="card-title"><span class="tag tag-pink">注意の競合</span></div>
      <p style="font-size:13.5px;color:var(--muted)">SNS上で顧客の「時間」を奪い合う相手。<br><b>例：</b>発見タブに並ぶ全アカウント。同業以外もタイムラインでは敵</p>
    </div>
  </div>

  <h3><span class="hash">#</span>競合の「結果」と「要因」を分けて見る</h3>
  <p>プロの競合分析は2段構えです。まず<b>結果</b>（売上、シェア、フォロワー数、エンゲージメント）を見て、次にその結果を生んでいる<b>要因</b>（戦略、リソース、体制）を推察する。結果だけ見て「フォロワー多くていいなあ」で終わるのは分析ではありません。</p>

  <div class="grid2">
    <div class="card">
      <div class="card-title"><span class="icon" style="background:rgba(244,114,182,.15)">📊</span>結果を見る（What）</div>
      <ul class="list" style="font-size:13.5px;margin-bottom:0">
        <li>フォロワー数・増加ペース</li>
        <li>平均いいね・コメント数 → <b>エンゲージメント率</b></li>
        <li>伸びている投稿TOP5の共通点</li>
        <li>リール再生数と頻度</li>
      </ul>
    </div>
    <div class="card">
      <div class="card-title"><span class="icon" style="background:rgba(244,114,182,.15)">🔬</span>要因を推察する（Why）</div>
      <ul class="list" style="font-size:13.5px;margin-bottom:0">
        <li>誰に向けたアカウント設計か（プロフ文・ハイライト）</li>
        <li>コンテンツの型・投稿頻度・制作体制</li>
        <li>どんなCTA・導線で刈り取っているか</li>
        <li><b>逆に「やっていないこと」は何か</b> ← 機会の発見</li>
      </ul>
    </div>
  </div>

  <div class="keypoint">
    <p>競合分析のゴールは「真似すること」ではなく、<b>「競合がまだ満たせていない顧客ニーズ＝空白地帯」を見つけること</b>。見るべきは競合の強さよりも「穴」。</p>
  </div>
</section>

<section id="c3-company">
  <div class="part-chip" style="color:var(--emerald)">PART 02 — 3C分析 深堀り ／ 3つ目のC</div>
  <h2><span style="color:var(--c-company)">Company</span> — 自社分析</h2>
  <p class="lead">最後に自社。ここまでのCustomer・Competitorの分析が揃って初めて、自社の何が「武器」になるのかが決まります。</p>

  <h3><span class="hash">#</span>自社の棚卸し：4つの引き出し</h3>
  <div class="grid2">
    <div class="card" style="border-color:rgba(52,211,153,.3)">
      <div class="card-title"><span class="icon" style="background:rgba(52,211,153,.15)">🏭</span>有形資産</div>
      <p style="font-size:13.5px;color:var(--muted)">商品・設備・立地・価格・実績数。例：自社大工、モデルハウス、施工実績120棟</p>
    </div>
    <div class="card" style="border-color:rgba(52,211,153,.3)">
      <div class="card-title"><span class="icon" style="background:rgba(52,211,153,.15)">💎</span>無形資産</div>
      <p style="font-size:13.5px;color:var(--muted)">ブランド、専門知識、職人の技術、地域の信頼、お客様との関係性。<b>SNSで一番効くのはここ</b></p>
    </div>
    <div class="card" style="border-color:rgba(52,211,153,.3)">
      <div class="card-title"><span class="icon" style="background:rgba(52,211,153,.15)">🧑‍🤝‍🧑</span>ヒト・体制</div>
      <p style="font-size:13.5px;color:var(--muted)">誰が発信できるか、現場に同行できるか、返信は誰がするか。運用の持続性を決める</p>
    </div>
    <div class="card" style="border-color:rgba(52,211,153,.3)">
      <div class="card-title"><span class="icon" style="background:rgba(52,211,153,.15)">📖</span>ストーリー</div>
      <p style="font-size:13.5px;color:var(--muted)">創業の経緯、こだわりの理由、失敗から学んだこと。共感を生む唯一無二の素材</p>
    </div>
  </div>

  <h3><span class="hash">#</span>「本物の強み」をテストする：VRIOの簡易版</h3>
  <p>棚卸しした資産が本当に戦略の核になるかは、3つの質問でテストできます（VRIO分析の実務向け簡易版）。</p>

  <ul class="list">
    <li><b>① 価値があるか（Value）</b>：顧客はそれにお金や時間を払いたいと思うか？ → Customerの分析と照合</li>
    <li><b>② 希少か（Rarity）</b>：競合も同じことを言えてしまわないか？ → Competitorの分析と照合</li>
    <li><b>③ 真似されにくいか（Inimitability）</b>：明日から競合が真似できることか、長年積み上げた資産か？</li>
  </ul>

  <div class="callout callout-warn">
    <span class="ci">⚠️</span>
    <p><b>「想いの強さ」「品質へのこだわり」「丁寧な対応」は、ほぼ全社が言う。</b>言った瞬間に希少性テスト②で脱落する。具体的な数字・固有名詞・証拠（お客様の声、現場写真）まで落として初めて武器になる。</p>
  </div>
</section>

<section id="c3-ksf">
  <div class="part-chip" style="color:var(--amber)">PART 02 — 3C分析 深堀り ／ 統合</div>
  <h2>クロス3C — 3つのCを「掛け合わせて」KSFを導く</h2>
  <p class="lead">3つのCを別々に書き出しただけでは、まだ分析の50%。ここからが本番です。3つの円を重ね、「勝てる領域」を言語化します。</p>

  <h3><span class="hash">#</span>KSF導出の公式</h3>
  <div class="keypoint">
    <p style="font-size:17px;text-align:center">
      <span style="color:var(--c-customer)">顧客が強く求めていて</span> ×
      <span style="color:var(--c-competitor)">競合が提供できていなくて</span> ×
      <span style="color:var(--c-company)">自社なら提供できる</span><br>
      <span style="font-size:14px;color:var(--muted)">この3条件を同時に満たす価値 ＝</span> <b class="grad-text" style="font-size:20px">KSF（勝てる理由）</b>
    </p>
  </div>

  <p>このKSFが決まると、その後のすべてが芋づる式に決まります。<b>STP（誰に・どんな立ち位置で）→ コンセプト → コンテンツの方針 → KPI</b>。逆に言えば、KSFが曖昧なまま投稿を始めると、「なんとなく綺麗な写真を上げ続けるアカウント」が出来上がります。</p>

  <h3><span class="hash">#</span>3つの円の重なりは4パターンある</h3>
  <div class="table-wrap">
    <table>
      <thead><tr><th>重なり</th><th>意味</th><th>取るべきスタンス</th></tr></thead>
      <tbody>
        <tr><td><span class="tag tag-amber">顧客 × 自社 ◯ × 競合 ✕</span></td><td><b>勝てる領域（スイートスポット）</b></td><td>ここに集中投資。発信の核にする</td></tr>
        <tr><td><span class="tag tag-gray">顧客 × 自社 ◯ × 競合 ◯</span></td><td>消耗戦の領域（コモディティ）</td><td>やるが、差別化の主軸にはしない</td></tr>
        <tr><td><span class="tag tag-gray">顧客 ✕ × 自社 ◯</span></td><td>独りよがりの領域</td><td>発信しても響かない。封印するか、需要を再検証</td></tr>
        <tr><td><span class="tag tag-gray">顧客 ◯ × 自社 ✕</span></td><td>能力ギャップの領域</td><td>中長期で獲得するか、潔く捨てる</td></tr>
      </tbody>
    </table>
  </div>
</section>

<section id="c3-fails">
  <div class="part-chip" style="color:var(--rose)">PART 02 — 3C分析 深堀り ／ 落とし穴</div>
  <h2>3C分析・よくある5つの失敗</h2>
  <p class="lead">先輩たちが実際にやらかしてきた失敗集です。クリックして開いてください。</p>

  <div class="acc">
    <button class="acc-head">❌ 失敗①：自社（Company）から書き始める<span class="chev">▶</span></button>
    <div class="acc-body"><div class="acc-body-inner">
      <p>自社のことは書きやすいので、つい最初に埋めたくなる。しかし自社起点で考えると「うちの強みはこれだから、これを発信しよう」という<b>プロダクトアウトの押し売り設計</b>になる。必ずCustomer → Competitor → Companyの順で。自社の強みは「最後に決まるもの」。</p>
    </div></div>
  </div>
  <div class="acc">
    <button class="acc-head">❌ 失敗②：「事実」と「解釈」を混ぜる<span class="chev">▶</span></button>
    <div class="acc-body"><div class="acc-body-inner">
      <p>「競合A社はInstagramに力を入れていない（解釈）」ではなく「競合A社は直近3ヶ月で投稿12回、リール0本、平均いいね40（事実）」と書く。事実と解釈を分けて書かないと、チームの議論が「印象の言い合い」になる。<b>分析シートには必ず出典・取得日を書く</b>のがプロの作法。</p>
    </div></div>
  </div>
  <div class="acc">
    <button class="acc-head">❌ 失敗③：埋めて満足する（So What? がない）<span class="chev">▶</span></button>
    <div class="acc-body"><div class="acc-body-inner">
      <p>3つの枠がびっしり埋まった美しいスライドが完成し、全員が満足して、何も変わらない——最悪のパターン。各枠の最後に必ず「<b>つまり、だから何をする？</b>」の一行を書く。KSFと「やらないことリスト」まで出して、初めて3C分析は完了。</p>
    </div></div>
  </div>
  <div class="acc">
    <button class="acc-head">❌ 失敗④：一度やって終わりにする<span class="chev">▶</span></button>
    <div class="acc-body"><div class="acc-body-inner">
      <p>市場も競合もアルゴリズムも動き続ける。特にSNSは変化が速く、半年前の競合分析はもう古い。<b>四半期に一度は3Cを見直す</b>。運用レポートに「競合の動き」欄を常設しておくと、自然に更新され続ける仕組みになる。</p>
    </div></div>
  </div>
  <div class="acc">
    <button class="acc-head">❌ 失敗⑤：デスクリサーチだけで完結させる<span class="chev">▶</span></button>
    <div class="acc-body"><div class="acc-body-inner">
      <p>検索とAIで集めた二次情報だけの3Cは、競合も同じものが作れる＝差別化の種にならない。<b>一次情報（お客様への直接ヒアリング、現場観察、自分で競合の資料請求をしてみる）</b>こそが、自社だけのKSFを生む。「競合の資料請求・体験予約をしてみる」は新人でも今日できる最強の競合分析。</p>
    </div></div>
  </div>
</section>

<div class="divider"></div>

<!-- ============ PART 3 ============ -->
<section id="case">
  <div class="part-chip" style="color:var(--cyan)">PART 03 — INSTAGRAM実践ケース</div>
  <h2>ケーススタディ：工務店「ヒカリ工務店」のInstagram戦略</h2>
  <p class="lead">ここからが本番。Part 1・2で学んだ思考を、実際のInstagram運用にフル適用します。題材は架空の工務店ですが、数字も課題も現場のリアルに寄せています。</p>

  <div class="card" style="background:linear-gradient(135deg,rgba(34,211,238,.06),rgba(99,102,241,.06));border-color:rgba(34,211,238,.3)">
    <div class="card-title"><span class="icon" style="background:rgba(34,211,238,.15)">🏠</span>クライアント概要（架空）</div>
    <div class="table-wrap" style="margin-bottom:0">
      <table>
        <tbody>
          <tr><td style="width:180px"><b>会社</b></td><td>株式会社ヒカリ工務店（地方都市・商圏人口約40万人）</td></tr>
          <tr><td><b>事業</b></td><td>注文住宅（年間18棟）・坪単価65万円〜・設計士直営の自由設計、自然素材が得意</td></tr>
          <tr><td><b>現状</b></td><td>フォロワー約800人。完成写真を不定期投稿。リール未活用。Instagram経由の問い合わせ月1〜2件</td></tr>
          <tr><td><b>ゴール（KGI）</b></td><td>12ヶ月でInstagram経由の資料請求・見学予約を<b>月10件</b>に（受注2棟/年相当）</td></tr>
          <tr><td><b>体制</b></td><td>広報担当1名（兼任）＋現場監督・設計士が撮影協力可。週2〜3投稿が現実ライン</td></tr>
        </tbody>
      </table>
    </div>
  </div>

  <div class="callout callout-info">
    <span class="ci">📐</span>
    <p><b>進め方：</b>①3C分析でKSFを導く → ②アカウントコンセプトとコンテンツ戦略に変換 → ③KPIツリーで運用を回す。Part 1の「環境分析→戦略→施策→検証」の流れそのまま。</p>
  </div>
</section>

<section id="case-3c">
  <div class="part-chip" style="color:var(--cyan)">PART 03 — INSTAGRAM実践ケース</div>
  <h2>工務店の3C分析 — 実演</h2>
  <p class="lead">タブを切り替えて、Customer → Competitor → Company → クロス3Cの順に見てください。各タブ最後の「So What?」が分析の出口です。</p>

  <div class="tabs">
    <div class="tab-btns">
      <button class="tab-btn active" data-tab="t-customer">① Customer</button>
      <button class="tab-btn" data-tab="t-competitor">② Competitor</button>
      <button class="tab-btn" data-tab="t-company">③ Company</button>
      <button class="tab-btn" data-tab="t-ksf">④ クロス3C → KSF</button>
    </div>

    <div class="tab-panel active" id="t-customer">
      <h4 style="color:var(--c-customer)">市場（マクロ）の事実</h4>
      <ul class="list">
        <li>商圏の新築着工は緩やかに減少。ただし<b>「後悔しない家づくり」系の情報需要は増加</b>（資材高騰・住宅ローン金利上昇で失敗への不安が増大）</li>
        <li>家づくり検討者の情報収集は <b>Instagram・YouTube・住宅系アプリが主戦場</b>に。展示場来場は「ほぼ決めた後」の最終確認に後ろ倒し</li>
        <li>初回接触の時点で、顧客は平均数ヶ月〜1年分の情報を溜め込んでいる（=SNS上で比較検討が終わっている）</li>
      </ul>
      <h4 style="color:var(--c-customer)">顧客（ミクロ）：コアターゲットのn=1像</h4>
      <div class="card">
        <p style="font-size:14px;margin-bottom:8px"><b>佐藤夫妻（夫34歳・妻31歳・子2歳）｜世帯年収650万円｜土地から探す初めての家づくり</b></p>
        <ul class="list" style="font-size:13.5px;margin-bottom:8px">
          <li>妻が平日の夜、子どもの寝かしつけ後にInstagramで「#後悔しない家づくり」「#間取り」を検索、気になる投稿を<b>保存して週末に夫婦会議</b></li>
          <li>表のニーズ：「おしゃれな施工事例」「間取りのアイデア」「相場感」</li>
          <li><b>インサイト：「一生に一度の買い物で絶対に失敗したくない。でも知識がないまま営業マンに会うのが怖い。会う前に『正解』を知っておきたい」</b></li>
          <li>不安要素：総額いくらかかるのか誰も教えてくれない／営業トークと本音の区別がつかない</li>
        </ul>
      </div>
      <div class="callout callout-success" style="margin-top:14px">
        <span class="ci">➡️</span>
        <p><b>So What?</b> 顧客が本当に欲しいのは「映え」ではなく<b>「失敗回避の判断材料」</b>。保存して夫婦会議に使える「検討の道具」になる情報が刺さる。接触障壁は「営業されたくない」なので、売り込み色は徹底排除すべき。</p>
      </div>
    </div>

    <div class="tab-panel" id="t-competitor">
      <h4 style="color:var(--c-competitor)">競合アカウント分析（事実ベース・取得日を必ず記録）</h4>
      <div class="table-wrap">
        <table>
          <thead><tr><th>競合</th><th>フォロワー</th><th>投稿傾向</th><th>強み</th><th>穴（やれていないこと）</th></tr></thead>
          <tbody>
            <tr>
              <td><b>大手ハウスメーカーS社</b><br><span class="tag tag-gray">直接競合</span></td>
              <td>5.2万<br>（全国アカ）</td>
              <td>ブランドムービー・完成美写真。本部の一括運用</td>
              <td>圧倒的認知・信頼・物量</td>
              <td>地域感ゼロ。価格非公開。現場やつくり手の顔が見えない</td>
            </tr>
            <tr>
              <td><b>地場ビルダーA社</b><br><span class="tag tag-pink">最重要競合</span></td>
              <td>1.4万</td>
              <td>ルームツアーリール週2本。おしゃれ系で統一感あり</td>
              <td>リール運用がうまい。世界観の統一</td>
              <td><b>価格・コスト・失敗談に一切触れない</b>。コメント返信なし</td>
            </tr>
            <tr>
              <td><b>ローコストB社</b><br><span class="tag tag-gray">直接競合</span></td>
              <td>3,000</td>
              <td>「月々◯万円」価格訴求のフィード中心</td>
              <td>価格の分かりやすさ</td>
              <td>品質・性能の根拠説明がない。口コミに施工品質の不安</td>
            </tr>
            <tr>
              <td><b>建売・中古リノベ・賃貸継続</b><br><span class="tag tag-gray">間接競合</span></td>
              <td>—</td>
              <td>「注文住宅は高い・大変」という顧客の思い込みが実体</td>
              <td>手軽さ・予算の読みやすさ</td>
              <td>「自分たちらしい暮らし」への憧れには応えられない</td>
            </tr>
          </tbody>
        </table>
      </div>
      <div class="callout callout-success">
        <span class="ci">➡️</span>
        <p><b>So What?</b> 商圏内の競合は「美しい完成形」を見せる競争に集中しており、<b>「お金のリアル」「過程」「失敗を防ぐ知識」は完全な空白地帯</b>。ここは顧客のインサイト（失敗回避）と完璧に重なる。</p>
      </div>
    </div>

    <div class="tab-panel" id="t-company">
      <h4 style="color:var(--c-company)">自社の棚卸し → VRIO簡易テスト</h4>
      <div class="table-wrap">
        <table>
          <thead><tr><th>資産</th><th>価値ある?</th><th>希少?</th><th>真似されにくい?</th><th>判定</th></tr></thead>
          <tbody>
            <tr><td>設計士と直接話せる家づくり</td><td>◯ 失敗回避ニーズに直結</td><td>◯ 商圏内で稀</td><td>◯ 体制の問題で大手は不可</td><td><span class="tag tag-green">武器になる</span></td></tr>
            <tr><td>社長が「価格の内訳公開」に前向き</td><td>◎ 最大の不安に直撃</td><td>◎ 誰もやっていない</td><td>◯ 利益構造を晒す覚悟は真似困難</td><td><span class="tag tag-green">最強の武器</span></td></tr>
            <tr><td>自然素材の施工ノウハウ</td><td>◯ 関心層には刺さる</td><td>△ 県内に同訴求2社</td><td>◯ 職人の経験値</td><td><span class="tag tag-amber">サブ武器</span></td></tr>
            <tr><td>完成写真のクオリティ</td><td>◯</td><td>✕ A社の方が上</td><td>✕</td><td><span class="tag tag-gray">主軸にしない</span></td></tr>
            <tr><td>OB顧客との強い関係（年1感謝祭）</td><td>◯ リアルな声=UGC源泉</td><td>◯</td><td>◎ 18年の蓄積</td><td><span class="tag tag-green">武器になる</span></td></tr>
          </tbody>
        </table>
      </div>
      <p style="font-size:13.5px;color:var(--muted)">制約も直視する：広報1名兼任 → 週2〜3投稿が上限。よって「物量で勝つ」戦略は最初から捨て、「1本の濃度で勝つ」戦略を選ぶ。</p>
      <div class="callout callout-success">
        <span class="ci">➡️</span>
        <p><b>So What?</b> 「写真の美しさ」でA社と殴り合うのは消耗戦（しかも負ける）。自社が勝てるのは<b>「透明性」と「専門家が直接語る信頼」</b>。制約（少人数）はむしろ「顔が見える」発信と相性が良い。</p>
      </div>
    </div>

    <div class="tab-panel" id="t-ksf">
      <h4 style="color:var(--amber)">3つのCを重ねる</h4>
      <div class="grid3">
        <div class="card" style="border-color:rgba(56,189,248,.4)">
          <p style="font-size:12px;color:var(--c-customer);font-weight:800;margin-bottom:6px">CUSTOMER</p>
          <p style="font-size:13.5px;margin:0">「絶対に後悔したくない。営業に会う前に、お金と失敗のリアルを知りたい」</p>
        </div>
        <div class="card" style="border-color:rgba(244,114,182,.4)">
          <p style="font-size:12px;color:var(--c-competitor);font-weight:800;margin-bottom:6px">COMPETITOR</p>
          <p style="font-size:13.5px;margin:0">全社が「美しい完成形」を競い、価格・過程・失敗には誰も触れない</p>
        </div>
        <div class="card" style="border-color:rgba(52,211,153,.4)">
          <p style="font-size:12px;color:var(--c-company);font-weight:800;margin-bottom:6px">COMPANY</p>
          <p style="font-size:13.5px;margin:0">設計士直営の専門性 × 価格を開示できる覚悟 × OB顧客のリアルな声</p>
        </div>
      </div>
      <div class="keypoint">
        <p style="text-align:center">KSF：<b class="grad-text" style="font-size:19px">「家づくりのお金と失敗を、商圏で一番正直に語る存在になる」</b><br>
        <span style="font-size:13.5px;color:var(--muted)">コンセプト案：『建てる前に、ぜんぶ話す工務店。』— 売り込まず、判断材料を渡し続けることで「会う前から信頼されている」状態をつくる</span></p>
      </div>
      <p style="font-size:13.5px;color:var(--muted)">同時に「やらないこと」も決まる：①映え一辺倒の投稿はしない ②物量競争はしない ③フォロワー数をKGIにしない。<b>やらないことを決められるのが、3C分析をやった証拠。</b></p>
    </div>
  </div>
</section>

<section id="case-strategy">
  <div class="part-chip" style="color:var(--cyan)">PART 03 — INSTAGRAM実践ケース</div>
  <h2>KSFをアカウント戦略に変換する</h2>
  <p class="lead">分析はここからが回収フェーズ。KSFを「ポジショニング → アカウント設計 → コンテンツの柱」へ翻訳します。</p>

  <h3><span class="hash">#</span>ポジショニングマップ：空白を獲りに行く</h3>
  <div class="figure">
    <svg viewBox="0 0 760 460" xmlns="http://www.w3.org/2000/svg" font-family="Inter,'Noto Sans JP',sans-serif">
      <defs>
        <marker id="arrAx" viewBox="0 0 10 10" refX="8" refY="5" markerWidth="7" markerHeight="7" orient="auto">
          <path d="M0,0 L10,5 L0,10 z" fill="#6b6b78"/>
        </marker>
      </defs>
      <!-- axes -->
      <line x1="380" y1="420" x2="380" y2="40" stroke="#4b4b58" stroke-width="1.5" marker-end="url(#arrAx)"/>
      <line x1="80" y1="230" x2="690" y2="230" stroke="#4b4b58" stroke-width="1.5" marker-end="url(#arrAx)"/>
      <text x="380" y="28" text-anchor="middle" fill="#9b9ba8" font-size="12.5" font-weight="700">お金・過程の透明性：高い</text>
      <text x="380" y="445" text-anchor="middle" fill="#6b6b78" font-size="12.5">透明性：低い（完成形のみ見せる）</text>
      <text x="78" y="212" text-anchor="start" fill="#6b6b78" font-size="12.5">情報：イメージ・世界観</text>
      <text x="692" y="212" text-anchor="end" fill="#9b9ba8" font-size="12.5" font-weight="700">情報：実用・判断材料</text>
      <!-- sweet spot zone -->
      <rect x="470" y="60" width="200" height="120" rx="14" fill="rgba(251,191,36,.07)" stroke="#fbbf24" stroke-width="1.3" stroke-dasharray="5 5"/>
      <text x="570" y="50" text-anchor="middle" fill="#fcd34d" font-size="11.5" font-weight="700">空白地帯（KSFが示す場所）</text>
      <!-- competitors -->
      <g text-anchor="middle">
        <circle cx="200" cy="330" r="26" fill="rgba(255,255,255,.06)" stroke="#6b6b78" stroke-width="1.3"/>
        <text x="200" y="334" fill="#9b9ba8" font-size="11" font-weight="700">大手S社</text>
        <text x="200" y="372" fill="#6b6b78" font-size="10.5">ブランド世界観・価格非公開</text>
        <circle cx="285" cy="300" r="26" fill="rgba(244,114,182,.1)" stroke="#f472b6" stroke-width="1.3"/>
        <text x="285" y="304" fill="#f9a8d4" font-size="11" font-weight="700">A社</text>
        <text x="293" y="268" fill="#9b9ba8" font-size="10.5">おしゃれリール・中身は薄い</text>
        <circle cx="480" cy="300" r="26" fill="rgba(255,255,255,.06)" stroke="#6b6b78" stroke-width="1.3"/>
        <text x="480" y="304" fill="#9b9ba8" font-size="11" font-weight="700">B社</text>
        <text x="488" y="345" fill="#6b6b78" font-size="10.5">価格は出すが根拠なし</text>
        <!-- hikari -->
        <circle cx="572" cy="120" r="34" fill="rgba(34,211,238,.13)" stroke="#22d3ee" stroke-width="2"/>
        <text x="572" y="117" fill="#67e8f9" font-size="11.5" font-weight="800">ヒカリ</text>
        <text x="572" y="132" fill="#67e8f9" font-size="11.5" font-weight="800">工務店</text>
      </g>
    </svg>
    <div class="fig-cap">FIG.06 — ポジショニングマップ：競合がいない×顧客が求める象限へ</div>
  </div>

  <h3><span class="hash">#</span>アカウント設計の3点セット：「誰に・何を・なぜ自分が」</h3>
  <div class="grid3">
    <div class="card">
      <div class="card-title"><span class="icon" style="background:rgba(56,189,248,.15)">👥</span>誰に</div>
      <p style="font-size:13.5px;color:var(--muted)">商圏40万人のうち、3年以内に家づくりを考える28〜38歳夫婦。特に「情報収集はするが、まだ会社に接触していない」検討初期層</p>
    </div>
    <div class="card">
      <div class="card-title"><span class="icon" style="background:rgba(139,92,246,.15)">🎁</span>何を</div>
      <p style="font-size:13.5px;color:var(--muted)">売り込みではなく「後悔しないための判断材料」。お金のリアル、間取りの失敗例、現場の真実</p>
    </div>
    <div class="card">
      <div class="card-title"><span class="icon" style="background:rgba(52,211,153,.15)">🛡️</span>なぜ自分が</div>
      <p style="font-size:13.5px;color:var(--muted)">設計士直営だから専門的に語れる。地元18年・OB施主の実例があるから具体的に語れる。価格を開示する覚悟があるから正直に語れる</p>
    </div>
  </div>

  <h3><span class="hash">#</span>コンテンツピラー（投稿の柱）と配分</h3>
  <div class="table-wrap">
    <table>
      <thead><tr><th>柱</th><th>配分</th><th>役割（ファネル位置）</th><th>具体ネタ例</th></tr></thead>
      <tbody>
        <tr>
          <td><b>💰 お金のリアル</b></td><td><span class="tag tag-violet">30%</span></td>
          <td>認知＋保存獲得（発見タブ狙い）</td>
          <td>「坪単価65万の家、総額の内訳ぜんぶ見せます」「予算オーバーする人の共通点3つ」「ローン金利0.5%差のリアルな差額」</td>
        </tr>
        <tr>
          <td><b>📐 失敗回避ナレッジ</b></td><td><span class="tag tag-violet">30%</span></td>
          <td>保存・シェア獲得（夫婦会議の道具）</td>
          <td>「住んで3年のOB施主が語る後悔ポイント」「コンセント位置の失敗あるある」「契約前に必ず聞くべき10の質問」</td>
        </tr>
        <tr>
          <td><b>🔨 過程と人</b></td><td><span class="tag tag-violet">25%</span></td>
          <td>信頼醸成・フォロー転換</td>
          <td>「基礎工事で見るべきポイント（現場監督が解説）」「設計士の打ち合わせ風景」「上棟日の1日密着リール」</td>
        </tr>
        <tr>
          <td><b>🏡 暮らしの実例</b></td><td><span class="tag tag-violet">15%</span></td>
          <td>検討深化・行動喚起</td>
          <td>「OB宅訪問：30坪3,200万の家、住んでみてどう？」入居後インタビュー（UGC連動・Spread起点）</td>
        </tr>
      </tbody>
    </table>
  </div>

  <div class="callout callout-info">
    <span class="ci">💡</span>
    <p><b>設計の意図：</b>各柱がULSSASとファネルの特定の段差を担当している。「映える完成写真」を主役にしない理由は、3C分析でその領域が消耗戦と判明したから。<b>戦略とは投稿ネタの好き嫌いではなく、分析の帰結。</b></p>
  </div>
</section>

<section id="case-kpi">
  <div class="part-chip" style="color:var(--cyan)">PART 03 — INSTAGRAM実践ケース</div>
  <h2>KPI設計 — 数字で運用を回す</h2>
  <p class="lead">最後に検証の仕組み。KGI（最終目標）から逆算してKPIツリーを組み、週次・月次で回します。フォロワー数を目標にしない理由もここで明確になります。</p>

  <h3><span class="hash">#</span>KGIからの逆算</h3>
  <p>KGI＝資料請求・見学予約 <b>月10件</b>。Part 1のKPIツリーに当てはめると：</p>
  <p style="font-family:'JetBrains Mono',monospace;font-size:13.5px;background:var(--bg-soft);border:1px solid var(--border);border-radius:10px;padding:16px 20px;overflow-x:auto">
  月間リーチ <b style="color:#7dd3fc">80,000</b> × プロフ遷移率 <b style="color:#d8b4fe">2.5%</b>（2,000人） × CV率 <b style="color:#f9a8d4">0.5%</b> ＝ <b style="color:#fcd34d">10件</b></p>

  <div class="kpi-row">
    <div class="kpi"><div class="kv" style="color:#7dd3fc">3.0%+</div><div class="kl">保存率</div><div class="kn">保存数÷リーチ。最重要先行指標</div></div>
    <div class="kpi"><div class="kv" style="color:#d8b4fe">2.5%+</div><div class="kl">プロフィール遷移率</div><div class="kn">投稿→プロフの興味転換</div></div>
    <div class="kpi"><div class="kv" style="color:#f9a8d4">8.0%+</div><div class="kl">フォロー転換率</div><div class="kn">プロフ訪問→フォロー</div></div>
    <div class="kpi"><div class="kv" style="color:#fcd34d">10件/月</div><div class="kl">資料請求・見学予約</div><div class="kn">KGI。リンク計測必須</div></div>
  </div>

  <div class="callout callout-warn">
    <span class="ci">⚠️</span>
    <p><b>フォロワー数をKGIにしない理由：</b>このビジネスは商圏40万人のローカル事業。全国から10万フォロワーを集めても1棟も売れない。<b>「商圏内の検討層に深く刺さっているか」を示す保存率・問い合わせ数</b>こそが見るべき数字。これも3C（Customer分析）の帰結。</p>
  </div>

  <h3><span class="hash">#</span>運用サイクル：週次と月次で見るものを分ける</h3>
  <div class="grid2">
    <div class="card">
      <div class="card-title"><span class="tag tag-sky">週次（30分）</span>投稿単位のPDCA</div>
      <ul class="list" style="font-size:13.5px;margin-bottom:0">
        <li>各投稿の保存率・リーチ・プロフ遷移を記録</li>
        <li>勝ち投稿の「型」を特定 → 翌週に横展開</li>
        <li>5W1Hで負け投稿を要因分解（Who向け？How見せた？）</li>
      </ul>
    </div>
    <div class="card">
      <div class="card-title"><span class="tag tag-violet">月次（2時間）</span>戦略単位のPDCA</div>
      <ul class="list" style="font-size:13.5px;margin-bottom:0">
        <li>KPIツリー全体の数値更新・ボトルネック特定</li>
        <li>競合アカウント定点観測（投稿数・伸びた投稿・新施策）</li>
        <li>DM・コメントから新たな顧客インサイトを採集 → 3C更新</li>
      </ul>
    </div>
  </div>

  <h3><span class="hash">#</span>90日ロードマップ</h3>
  <div class="steps">
    <div class="step">
      <div class="step-num"></div>
      <div class="step-body">
        <h4>Day 1–30：土台づくり</h4>
        <p>プロフィール・ハイライト刷新（「会う前にぜんぶ分かる」構成）／コンテンツピラー4本で各2投稿ずつテスト／OB施主3組にインタビューしてネタを貯める</p>
      </div>
    </div>
    <div class="step">
      <div class="step-num"></div>
      <div class="step-body">
        <h4>Day 31–60：勝ち筋の特定</h4>
        <p>保存率3%超の投稿の型を特定し比率を寄せる／リール週1本を定常化（現場系）／「お金のリアル」シリーズ化開始</p>
      </div>
    </div>
    <div class="step">
      <div class="step-num"></div>
      <div class="step-body">
        <h4>Day 61–90：刈り取り導線の接続</h4>
        <p>ハイライトから資料請求LPへの導線計測開始／月1の見学会をストーリーズで告知テスト／月次レポートで3C見直し（競合の追随チェック）</p>
      </div>
    </div>
  </div>
</section>

<div class="divider"></div>

<!-- ============ CLOSING ============ -->
<section id="worksheet">
  <div class="part-chip" style="color:var(--emerald)">WORKSHOP</div>
  <h2>ワーク：自分の担当アカウントで3Cをやってみる</h2>
  <p class="lead">レクチャーの仕上げです。担当アカウント（なければ好きなブランド）について、30分で以下を埋めてください。<b>順番厳守、各項目に必ずSo What?を書くこと。</b></p>

  <div class="worksheet">
    <h4>📘 STEP 1 — Customer（10分）</h4>
    <p style="font-size:13.5px;color:var(--muted)">コア顧客1人を想定し、「発言（ウォンツ）」「ニーズ」「インサイト」の3層で書く。最後に So What? を1行。</p>
    <div class="ws-line"></div><div class="ws-line"></div><div class="ws-line"></div>
  </div>
  <div class="worksheet">
    <h4>📕 STEP 2 — Competitor（10分）</h4>
    <p style="font-size:13.5px;color:var(--muted)">競合アカウントを2つ開き、「事実（数字）」と「穴（やれていないこと）」を書く。間接競合も1つ挙げる。</p>
    <div class="ws-line"></div><div class="ws-line"></div><div class="ws-line"></div>
  </div>
  <div class="worksheet">
    <h4>📗 STEP 3 — Company → KSF（10分）</h4>
    <p style="font-size:13.5px;color:var(--muted)">自社資産をVRIO簡易テストにかけ、「顧客が望み×競合ができず×自社ができる」を1文で書く。＋「やらないこと」を1つ。</p>
    <div class="ws-line"></div><div class="ws-line"></div><div class="ws-line"></div>
  </div>

  <div class="callout callout-success">
    <span class="ci">✅</span>
    <p><b>提出物：</b>KSFの1文と「やらないこと」1つをチームSlackに投稿。次回レクチャーで全員分をレビューします。完璧さより「事実に基づいているか」「So What?があるか」を見ます。</p>
  </div>
</section>

<section id="summary">
  <div class="part-chip">CLOSING</div>
  <h2>まとめ — 今日持ち帰る7行</h2>

  <div class="card" style="background:var(--grad-soft);border-color:rgba(139,92,246,.35)">
    <ol class="list" style="margin-bottom:0;font-size:15px;line-height:2.2">
      <li>マーケティングとは<b>「選ばれる構造」をつくる仕事</b>。フレームワークはそのための思考の型</li>
      <li>顧客は階段（ファネル）を登る。改善は<b>ボトルネックの特定</b>から</li>
      <li>SNS時代の購買はULSSAS。<b>UGCが起点、Spreadまで設計する</b></li>
      <li>3Cの目的は枠埋めではなく<b>KSF（勝てる理由）の発見</b></li>
      <li>順番は必ず <b style="color:var(--c-customer)">Customer</b> → <b style="color:var(--c-competitor)">Competitor</b> → <b style="color:var(--c-company)">Company</b>。強みは「差分」の中にある</li>
      <li>分析には必ず<b>「So What?（だから何をする）」と「やらないこと」</b>をつける</li>
      <li>3Cは生もの。<b>一次情報で更新し続ける</b>者だけが勝ち続ける</li>
    </ol>
  </div>

  <p style="margin-top:28px">フレームワークは覚えただけでは1円にもなりません。<b>明日、担当アカウントのインサイトを開き、競合を3つ観察し、お客様の声を1つ拾う</b>——そこから本気のマーケティングが始まります。</p>
</section>

<footer class="footer">
  <div>© 2026 SHO-SAN Inc. — Marketing Academy 社内研修資料</div>
  <div>3C Analysis × Instagram Lecture / v1.0</div>
</footer>

</div><!-- /container -->
</div><!-- /main -->
</div><!-- /layout -->

<button id="toTop" title="トップへ">↑</button>

<script>
// ===== Scroll progress =====
const progress = document.getElementById('progress');
const toTop = document.getElementById('toTop');
window.addEventListener('scroll', () => {
  const h = document.documentElement;
  const pct = (h.scrollTop) / (h.scrollHeight - h.clientHeight) * 100;
  progress.style.width = pct + '%';
  toTop.classList.toggle('show', h.scrollTop > 600);
}, { passive: true });
toTop.addEventListener('click', () => window.scrollTo({ top: 0, behavior: 'smooth' }));

// ===== Scrollspy =====
const navLinks = [...document.querySelectorAll('.nav a')];
const sections = navLinks
  .map(a => document.querySelector(a.getAttribute('href')))
  .filter(Boolean);
const spy = new IntersectionObserver(entries => {
  entries.forEach(e => {
    if (e.isIntersecting) {
      navLinks.forEach(a => a.classList.toggle('active', a.getAttribute('href') === '#' + e.target.id));
    }
  });
}, { rootMargin: '-20% 0px -65% 0px' });
sections.forEach(s => spy.observe(s));

// ===== Accordion =====
document.querySelectorAll('.acc-head').forEach(btn => {
  btn.addEventListener('click', () => {
    const acc = btn.parentElement;
    const body = acc.querySelector('.acc-body');
    const isOpen = acc.classList.contains('open');
    if (isOpen) {
      body.style.maxHeight = '0';
      acc.classList.remove('open');
    } else {
      body.style.maxHeight = body.scrollHeight + 'px';
      acc.classList.add('open');
    }
  });
});

// ===== Tabs =====
document.querySelectorAll('.tabs').forEach(tabs => {
  const btns = tabs.querySelectorAll('.tab-btn');
  const panels = tabs.querySelectorAll('.tab-panel');
  btns.forEach(btn => {
    btn.addEventListener('click', () => {
      btns.forEach(b => b.classList.remove('active'));
      panels.forEach(p => p.classList.remove('active'));
      btn.classList.add('active');
      tabs.querySelector('#' + btn.dataset.tab).classList.add('active');
    });
  });
});
</script>

</body>
</html>
