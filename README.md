<!DOCTYPE html>
<html lang="ru">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, viewport-fit=cover">
<title>EpicTowers — Minecraft PvP сервер</title>
<meta name="description" content="EpicTowers — Minecraft PvP сервер в режиме Towers. Честная игра, дружное комьюнити, адекватная админка. IP: epictowers777.mcsh.io">
<link rel="icon" href="data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 100 100'%3E%3Crect width='100' height='100' fill='%230a0f0c'/%3E%3Crect x='22' y='42' width='18' height='42' fill='%23e5493c'/%3E%3Crect x='22' y='30' width='18' height='10' fill='%23e5493c'/%3E%3Crect x='60' y='24' width='18' height='60' fill='%233fb56a'/%3E%3Crect x='60' y='12' width='18' height='10' fill='%233fb56a'/%3E%3C/svg%3E">
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Unbounded:wght@500;700;800&amp;family=Inter:wght@400;500;600;700&amp;family=JetBrains+Mono:wght@400;600&amp;display=swap" rel="stylesheet">
<style>
  :root{
    --void:#0a0f0c;
    --deepstone:#141c17;
    --deepstone-soft:#1b251e;
    --deepstone-line:#26332b;
    --redstone:#e5493c;
    --redstone-soft:rgba(229,73,60,.16);
    --emerald:#3fb56a;
    --emerald-soft:rgba(63,181,106,.16);
    --gold:#ecc25a;
    --ash:#9fb0a6;
    --white:#f4f7f5;
    --font-display:'Unbounded',sans-serif;
    --font-body:'Inter',sans-serif;
    --font-mono:'JetBrains Mono',monospace;
    --nav-h:76px;
  }

  *,*::before,*::after{box-sizing:border-box;margin:0;padding:0}
  html{scroll-behavior:smooth;scroll-padding-top:var(--nav-h)}
  body{
    background:var(--void);
    color:var(--white);
    font-family:var(--font-body);
    line-height:1.55;
    -webkit-font-smoothing:antialiased;
    overflow-x:hidden;
  }
  img{max-width:100%;display:block}
  a{color:inherit;text-decoration:none}
  ul{list-style:none}
  button{font:inherit;cursor:pointer;border:none;background:none;color:inherit}
  h1,h2,h3{font-family:var(--font-display);line-height:1.15;letter-spacing:-0.01em}
  :focus-visible{outline:2px solid var(--gold);outline-offset:3px}

  .container{width:100%;max-width:1180px;margin:0 auto;padding:0 24px}
  section{position:relative}

  /* ---------- background texture ---------- */
  body::before{
    content:"";
    position:fixed;inset:0;
    background-image:
      linear-gradient(rgba(255,255,255,.025) 1px,transparent 1px),
      linear-gradient(90deg,rgba(255,255,255,.025) 1px,transparent 1px);
    background-size:34px 34px;
    pointer-events:none;
    z-index:0;
    mask-image:radial-gradient(ellipse 90% 70% at 50% 0%,#000 40%,transparent 85%);
  }

  /* ---------- pixel panel (signature motif) ---------- */
  .pixel-panel{
    --notch:10px;
    --accent:var(--ash);
    position:relative;
    background:var(--deepstone);
    clip-path:polygon(0 var(--notch),var(--notch) var(--notch),var(--notch) 0,calc(100% - var(--notch)) 0,calc(100% - var(--notch)) var(--notch),100% var(--notch),100% calc(100% - var(--notch)),calc(100% - var(--notch)) calc(100% - var(--notch)),calc(100% - var(--notch)) 100%,var(--notch) 100%,var(--notch) calc(100% - var(--notch)),0 calc(100% - var(--notch)));
    box-shadow:inset 0 0 0 2px var(--accent);
  }
  .pixel-btn{
    --notch:8px;
    clip-path:polygon(0 var(--notch),var(--notch) var(--notch),var(--notch) 0,calc(100% - var(--notch)) 0,calc(100% - var(--notch)) var(--notch),100% var(--notch),100% calc(100% - var(--notch)),calc(100% - var(--notch)) calc(100% - var(--notch)),calc(100% - var(--notch)) 100%,var(--notch) 100%,var(--notch) calc(100% - var(--notch)),0 calc(100% - var(--notch)));
  }

  /* ---------- reveal on scroll ---------- */
  .reveal{opacity:0;transform:translateY(22px);transition:opacity .7s ease,transform .7s ease}
  .reveal.visible{opacity:1;transform:none}
  @media (prefers-reduced-motion:reduce){
    .reveal{opacity:1!important;transform:none!important;transition:none!important}
    *{animation-duration:.01ms!important;animation-iteration-count:1!important;transition-duration:.01ms!important;scroll-behavior:auto!important}
  }

  /* ================= NAV ================= */
  .nav{
    position:fixed;top:0;left:0;right:0;z-index:100;
    height:var(--nav-h);
    display:flex;align-items:center;
    background:rgba(10,15,12,0);
    border-bottom:1px solid transparent;
    transition:background .3s ease,border-color .3s ease;
  }
  .nav.scrolled{background:rgba(10,15,12,.86);backdrop-filter:blur(10px);border-color:var(--deepstone-line)}
  .nav .container{display:flex;align-items:center;justify-content:space-between;width:100%}
  .logo{display:flex;align-items:center;gap:10px;font-family:var(--font-display);font-weight:700;font-size:1.05rem;letter-spacing:.02em}
  .logo-mark{width:26px;height:26px;position:relative;flex:none}
  .logo-mark span{position:absolute;bottom:0;width:9px}
  .logo-mark span:first-child{left:0;height:20px;background:var(--redstone)}
  .logo-mark span:last-child{right:0;height:26px;background:var(--emerald)}
  .nav-links{display:flex;align-items:center;gap:2px}
  .nav-link{display:block;padding:10px 16px;font-size:.92rem;font-weight:500;color:var(--ash);border-radius:2px;transition:color .2s ease}
  .nav-link:hover{color:var(--white)}
  .nav-discord{
    margin-left:10px;padding:10px 20px;background:var(--emerald);color:var(--void);
    font-weight:700;font-size:.88rem;
  }
  .nav-toggle{display:none;flex-direction:column;gap:5px;width:30px;padding:6px}
  .nav-toggle span{height:2px;background:var(--white);width:100%;transition:transform .25s ease,opacity .25s ease}
  .nav-toggle.open span:nth-child(1){transform:translateY(7px) rotate(45deg)}
  .nav-toggle.open span:nth-child(2){opacity:0}
  .nav-toggle.open span:nth-child(3){transform:translateY(-7px) rotate(-45deg)}

  /* ================= HERO ================= */
  .hero{
    min-height:100svh;
    display:flex;align-items:center;
    padding:calc(var(--nav-h) + 40px) 0 80px;
    overflow:hidden;
  }
  .tower{
    position:absolute;bottom:0;width:min(30vw,360px);height:70%;
    clip-path:polygon(0% 100%,0% 34%,16% 34%,16% 18%,32% 18%,32% 34%,48% 34%,48% 8%,64% 8%,64% 34%,80% 34%,80% 18%,96% 18%,96% 34%,100% 34%,100% 100%);
    opacity:.4;z-index:0;
  }
  .tower.left{left:0;background:linear-gradient(180deg,var(--redstone),transparent 92%);filter:drop-shadow(0 0 60px rgba(229,73,60,.35))}
  .tower.right{right:0;background:linear-gradient(180deg,var(--emerald),transparent 92%);filter:drop-shadow(0 0 60px rgba(63,181,106,.35));transform:scaleX(-1)}
  .hero .container{position:relative;z-index:1}
  .hero-inner{max-width:720px;margin:0 auto;text-align:center}
  .eyebrow{
    display:inline-flex;align-items:center;gap:8px;
    font-family:var(--font-mono);font-size:.78rem;letter-spacing:.14em;
    color:var(--gold);text-transform:uppercase;margin-bottom:22px;
  }
  .eyebrow::before,.eyebrow::after{content:"";width:22px;height:1px;background:var(--gold);opacity:.5}
  .hero h1{
    font-size:clamp(2.6rem,7vw,4.6rem);font-weight:800;
    background:linear-gradient(90deg,var(--redstone),var(--white) 45%,var(--emerald));
    -webkit-background-clip:text;background-clip:text;color:transparent;-webkit-text-fill-color:transparent;
    margin-bottom:20px;
  }
  .hero-sub{color:var(--ash);font-size:clamp(1rem,2vw,1.15rem);max-width:540px;margin:0 auto 36px}
  .ip-bar{
    display:flex;align-items:center;gap:0;max-width:440px;margin:0 auto 18px;
    background:var(--deepstone);
  }
  .ip-bar span{
    flex:1;font-family:var(--font-mono);font-size:.95rem;padding:15px 18px;color:var(--white);
    overflow:hidden;text-overflow:ellipsis;white-space:nowrap;text-align:left;
  }
  .copy-btn{
    flex:none;padding:15px 20px;background:var(--emerald);color:var(--void);font-weight:700;font-size:.85rem;
    display:flex;align-items:center;gap:7px;transition:background .2s ease;
  }
  .copy-btn:hover{background:#4dc978}
  .copy-btn.copied{background:var(--gold)}
  .status-pill{
    display:inline-flex;align-items:center;gap:9px;
    font-family:var(--font-mono);font-size:.82rem;color:var(--ash);
    padding:9px 16px;background:var(--deepstone-soft);margin-bottom:32px;
  }
  .status-dot{width:8px;height:8px;border-radius:50%;background:var(--ash);flex:none}
  .status-dot.online{background:var(--emerald);box-shadow:0 0 0 3px var(--emerald-soft)}
  .status-dot.offline{background:var(--redstone);box-shadow:0 0 0 3px var(--redstone-soft)}
  .status-dot.pulse{animation:pulse 1.6s ease-in-out infinite}
  @keyframes pulse{0%,100%{opacity:1}50%{opacity:.35}}
  .hero-ctas{display:flex;gap:14px;justify-content:center;flex-wrap:wrap}
  .btn{
    padding:15px 28px;font-weight:700;font-size:.92rem;display:inline-flex;align-items:center;gap:9px;
    transition:transform .2s ease,background .2s ease;
  }
  .btn:hover{transform:translateY(-2px)}
  .btn-outline{background:transparent;box-shadow:inset 0 0 0 2px var(--redstone);color:var(--white)}
  .btn-outline:hover{background:var(--redstone-soft)}
  .btn-solid{background:var(--redstone);color:var(--white)}
  .btn-solid:hover{background:#f05c4e}

  /* ================= SECTION HEADS ================= */
  .section-head{max-width:600px;margin-bottom:56px}
  .section-head .tag{font-family:var(--font-mono);font-size:.78rem;letter-spacing:.12em;text-transform:uppercase;color:var(--gold);display:block;margin-bottom:14px}
  .section-head h2{font-size:clamp(1.8rem,4vw,2.6rem);margin-bottom:16px}
  .section-head p{color:var(--ash);font-size:1.02rem}
  .center{text-align:center;margin-left:auto;margin-right:auto}

  /* ================= ABOUT ================= */
  #about{padding:120px 0}
  .about-grid{display:grid;grid-template-columns:1fr 1.1fr;gap:64px;align-items:start}
  .about-statement{font-family:var(--font-display);font-size:clamp(1.3rem,2.6vw,1.8rem);font-weight:500;line-height:1.4}
  .about-statement em{font-style:normal;color:var(--emerald)}
  .about-statement .r{color:var(--redstone)}
  .pillars{display:grid;grid-template-columns:1fr 1fr;gap:16px}
  .pillar{--accent:var(--deepstone-line);padding:26px 22px}
  .pillar .ico{font-size:1.5rem;margin-bottom:14px;display:block}
  .pillar h3{font-family:var(--font-body);font-size:1rem;font-weight:700;margin-bottom:8px}
  .pillar p{color:var(--ash);font-size:.9rem}

  /* ================= RULES ================= */
  #rules{padding:120px 0;background:linear-gradient(180deg,transparent,rgba(20,28,23,.5) 15%,rgba(20,28,23,.5) 85%,transparent)}
  .rules-cols{display:grid;grid-template-columns:1fr 1fr;gap:40px}
  .rules-col-head{display:flex;align-items:center;gap:12px;margin-bottom:24px;padding-bottom:16px;border-bottom:1px solid var(--deepstone-line)}
  .rules-col-head .n{font-family:var(--font-mono);font-size:.8rem;color:var(--void);background:var(--accent);width:26px;height:26px;display:flex;align-items:center;justify-content:center;flex:none;font-weight:700}
  .rules-col-head h3{font-size:1.15rem}
  .rules-col.game .n{background:var(--emerald)}
  .rules-col.discord .n{background:var(--redstone)}
  .rule{display:flex;gap:16px;padding:18px 0;border-bottom:1px solid var(--deepstone-line)}
  .rule:last-child{border-bottom:none}
  .rule-num{font-family:var(--font-mono);color:var(--ash);font-size:.82rem;flex:none;padding-top:2px}
  .rule-ico{font-size:1.15rem;flex:none;line-height:1}
  .rule-body{flex:1}
  .rule-body h4{font-size:.96rem;font-weight:600;margin-bottom:4px}
  .rule-body p{color:var(--ash);font-size:.86rem;line-height:1.5}
  .ban-pill{
    flex:none;align-self:flex-start;font-family:var(--font-mono);font-size:.72rem;
    padding:5px 10px;background:var(--redstone-soft);color:#ff8a7d;white-space:nowrap;height:fit-content;
  }

  /* ================= STORE ================= */
  #store{padding:120px 0}
  .store-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:18px}
  .rank-card{--accent:var(--deepstone-line);padding:30px 24px;text-align:center;display:flex;flex-direction:column;align-items:center}
  .rank-card .ico{font-size:2rem;margin-bottom:16px}
  .rank-card h3{font-family:var(--font-display);font-size:1.15rem;font-weight:700;letter-spacing:.03em;margin-bottom:18px}
  .rank-price{font-family:var(--font-mono);font-weight:600;font-size:1.55rem;color:var(--white);margin-bottom:6px}
  .rank-rub{font-family:var(--font-mono);font-size:.85rem;color:var(--ash);margin-bottom:22px}
  .rank-card .btn{width:100%;justify-content:center;padding:12px;font-size:.82rem}
  .rank-card.spotlight{
    background:linear-gradient(165deg,var(--deepstone-soft),var(--deepstone));
    grid-column:span 1;
  }
  .rank-card.spotlight .ico{font-size:2.4rem}
  .spot-tag{
    font-family:var(--font-mono);font-size:.7rem;letter-spacing:.1em;color:var(--void);
    background:var(--gold);padding:4px 10px;margin-bottom:14px;
  }

  /* ================= DISCORD CTA ================= */
  #community{padding:100px 0}
  .discord-banner{
    padding:64px 40px;text-align:center;
    background:radial-gradient(ellipse at 50% 0%,var(--emerald-soft),transparent 60%),var(--deepstone);
    --accent:var(--emerald);
  }
  .discord-banner h2{font-size:clamp(1.6rem,3.4vw,2.3rem);margin-bottom:14px}
  .discord-banner p{color:var(--ash);max-width:480px;margin:0 auto 30px}

  /* ================= FOOTER ================= */
  footer{padding:56px 0 40px;border-top:1px solid var(--deepstone-line)}
  .footer-top{display:flex;justify-content:space-between;align-items:center;flex-wrap:wrap;gap:24px;margin-bottom:36px}
  .footer-links{display:flex;gap:28px;flex-wrap:wrap}
  .footer-links a{color:var(--ash);font-size:.9rem;transition:color .2s ease}
  .footer-links a:hover{color:var(--white)}
  .footer-bottom{display:flex;justify-content:space-between;flex-wrap:wrap;gap:12px;color:var(--ash);font-size:.82rem;font-family:var(--font-mono)}

  /* ================= RESPONSIVE ================= */
  @media (max-width:980px){
    .about-grid{grid-template-columns:1fr;gap:44px}
    .store-grid{grid-template-columns:repeat(2,1fr)}
    .rules-cols{gap:28px}
  }
  @media (max-width:768px){
    .nav-links{
      position:fixed;top:var(--nav-h);left:0;right:0;bottom:0;
      background:rgba(10,15,12,.98);backdrop-filter:blur(10px);
      flex-direction:column;align-items:stretch;padding:20px;gap:4px;
      transform:translateX(100%);transition:transform .3s ease;
    }
    .nav-links.open{transform:translateX(0)}
    .nav-link{padding:16px 12px;font-size:1.05rem;border-bottom:1px solid var(--deepstone-line)}
    .nav-discord{margin:14px 12px 0;text-align:center;justify-content:center;display:flex}
    .nav-toggle{display:flex}
    .tower{width:38vw;opacity:.28}
    .rules-cols{grid-template-columns:1fr}
    .store-grid{grid-template-columns:1fr}
    .pillars{grid-template-columns:1fr}
    .ip-bar{flex-direction:column}
    .ip-bar span{text-align:center;padding:14px}
    .copy-btn{width:100%;justify-content:center}
    .footer-top{flex-direction:column;align-items:flex-start}
    #about,#rules,#store{padding:80px 0}
  }
  @media (max-width:480px){
    .container{padding:0 18px}
    .hero-ctas{flex-direction:column;width:100%}
    .btn{width:100%;justify-content:center}
    .eyebrow{font-size:.68rem}
  }
</style>
</head>
<body>

<nav class="nav" id="site-nav">
  <div class="container">
    <a href="#home" class="logo">
      <span class="logo-mark"><span></span><span></span></span>
      EpicTowers
    </a>
    <ul class="nav-links" id="nav-links">
      <li><a href="#home" class="nav-link">Главная</a></li>
      <li><a href="#about" class="nav-link">О сервере</a></li>
      <li><a href="#rules" class="nav-link">Правила</a></li>
      <li><a href="#store" class="nav-link">Привилегии</a></li>
      <li><a href="https://discord.gg/BBkdcHsP2" target="_blank" rel="noopener" class="nav-link nav-discord pixel-btn">Discord</a></li>
    </ul>
    <button class="nav-toggle" id="nav-toggle" aria-label="Меню" aria-expanded="false">
      <span></span><span></span><span></span>
    </button>
  </div>
</nav>

<main>

  <!-- ================= HERO ================= -->
  <section class="hero" id="home">
    <div class="tower left"></div>
    <div class="tower right"></div>
    <div class="container">
      <div class="hero-inner">
        <span class="eyebrow">PvP · TOWERS · RU СЕРВЕР</span>
        <h1>EPICTOWERS</h1>
        <p class="hero-sub">Держи башню, разноси врагов и находи своих. Сервер, где честная игра и живое комьюнити важнее доната.</p>

        <div class="ip-bar pixel-panel" style="--accent:var(--deepstone-line)">
          <span id="ip-text">epictowers777.mcsh.io</span>
          <button class="copy-btn" id="copy-ip-btn">
            <span id="copy-btn-text">Скопировать</span>
          </button>
        </div>

        <div class="status-pill pixel-panel" style="--accent:var(--deepstone-line)">
          <span class="status-dot pulse" id="status-dot"></span>
          <span id="status-text">Проверяем статус сервера…</span>
        </div>

        <div class="hero-ctas">
          <button class="btn btn-solid pixel-btn" id="hero-copy-btn">Скопировать IP</button>
          <a href="https://discord.gg/BBkdcHsP2" target="_blank" rel="noopener" class="btn btn-outline pixel-btn">Discord →</a>
        </div>
      </div>
    </div>
  </section>

  <!-- ================= ABOUT ================= -->
  <section id="about">
    <div class="container">
      <div class="about-grid">
        <div class="reveal">
          <span class="tag" style="margin-bottom:14px;display:block">О сервере</span>
          <p class="about-statement">Мы годами видели, что убивает серверы: читеры, токсичные админы и мёртвые чаты.<br><br>EpicTowers — <em>наоборот</em>. Честные бои на башнях, адекватная модерация и люди, к которым <span class="r">хочется</span> возвращаться каждый день.</p>
        </div>
        <div class="pillars reveal">
          <div class="pillar pixel-panel" style="--accent:var(--emerald)">
            <span class="ico">🛡️</span>
            <h3>Честная игра</h3>
            <p>Античит и живая модерация — побеждает скилл, а не кошелёк.</p>
          </div>
          <div class="pillar pixel-panel" style="--accent:var(--redstone)">
            <span class="ico">🤝</span>
            <h3>Дружное комьюнити</h3>
            <p>Помогаем новичкам освоиться и не банят за вопрос в чате.</p>
          </div>
          <div class="pillar pixel-panel" style="--accent:var(--gold)">
            <span class="ico">⚖️</span>
            <h3>Адекватная админка</h3>
            <p>Разбираем жалобы по правилам, а не по настроению.</p>
          </div>
          <div class="pillar pixel-panel" style="--accent:var(--deepstone-line)">
            <span class="ico">⚙️</span>
            <h3>Стабильность</h3>
            <p>Сервер, который не падает в разгар боя за башню.</p>
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- ================= RULES ================= -->
  <section id="rules">
    <div class="container">
      <div class="section-head center reveal">
        <span class="tag">Правила</span>
        <h2>Коротко и по делу</h2>
        <p>Чтобы игра была честной для всех — восемь пунктов, ознакомиться недолго.</p>
      </div>

      <div class="rules-cols">
        <div class="rules-col game reveal">
          <div class="rules-col-head">
            <span class="n">1</span>
            <h3>Игровые правила</h3>
          </div>

          <div class="rule">
            <span class="rule-ico">⚔️</span>
            <div class="rule-body">
              <h4>1.1 Читы</h4>
              <p>Использование чит-клиентов и модификаций, дающих нечестное преимущество (killaura, x-ray, fly, aim-bot, no-fall и т.д.)</p>
            </div>
            <span class="ban-pill">Бан 7 дней</span>
          </div>

          <div class="rule">
            <span class="rule-ico">📦</span>
            <div class="rule-body">
              <h4>1.2 Дюп ресурсов и оружия</h4>
              <p>Дублирование предметов и оружия любым способом.</p>
            </div>
            <span class="ban-pill">Бан 3 дня</span>
          </div>

          <div class="rule">
            <span class="rule-ico">🎨</span>
            <div class="rule-body">
              <h4>1.3 Ресурспаки с преимуществом</h4>
              <p>Текстур-паки, дающие игровое преимущество: просмотр сквозь лаву, x-ray, «радужные» руды и т.д.</p>
            </div>
            <span class="ban-pill">Бан 3 дня</span>
          </div>

          <div class="rule">
            <span class="rule-ico">📢</span>
            <div class="rule-body">
              <h4>1.4 Спам и реклама</h4>
              <p>Любой спам в чате, а также реклама сторонних ресурсов (казино, запрещённые вещества и т.д.)</p>
            </div>
            <span class="ban-pill">Бан 5 дней</span>
          </div>
        </div>

        <div class="rules-col discord reveal">
          <div class="rules-col-head">
            <span class="n">2</span>
            <h3>Правила Discord</h3>
          </div>

          <div class="rule">
            <span class="rule-ico">🔞</span>
            <div class="rule-body">
              <h4>2.1 18+ контент</h4>
              <p>Публикация любого NSFW-контента.</p>
            </div>
            <span class="ban-pill">Бан 3 дня</span>
          </div>

          <div class="rule">
            <span class="rule-ico">📢</span>
            <div class="rule-body">
              <h4>2.2 Спам и реклама</h4>
              <p>Спам в любом виде, реклама сторонних ресурсов (казино, запрещённые вещества и т.д.)</p>
            </div>
            <span class="ban-pill">Бан 4 дня</span>
          </div>

          <div class="rule">
            <span class="rule-ico">🚫</span>
            <div class="rule-body">
              <h4>2.3 Нацистская символика</h4>
              <p>Публикация нацистской символики (включая свастику), а также отрицание Холокоста.</p>
            </div>
            <span class="ban-pill">Бан 6 дней</span>
          </div>

          <div class="rule">
            <span class="rule-ico">🔒</span>
            <div class="rule-body">
              <h4>2.4 Докс</h4>
              <p>Распространение чужих персональных данных и попытки установить личность другого человека.</p>
            </div>
            <span class="ban-pill">Бан 10 дней</span>
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- ================= STORE ================= -->
  <section id="store">
    <div class="container">
      <div class="section-head center reveal">
        <span class="tag">Привилегии</span>
        <h2>Поддержи сервер</h2>
        <p>Разовая покупка, без обязательной подписки.</p>
      </div>

      <div class="store-grid reveal">
        <div class="rank-card pixel-panel" style="--accent:#d9c25c">
          <span class="ico">👑</span>
          <h3 style="color:#d9c25c">VIP</h3>
          <div class="rank-price">150.000</div>
          <div class="rank-rub">19 ₽</div>
          <a href="https://discord.gg/BBkdcHsP2" target="_blank" rel="noopener" class="btn btn-outline pixel-btn" style="box-shadow:inset 0 0 0 2px #d9c25c">Купить</a>
        </div>

        <div class="rank-card pixel-panel" style="--accent:#b083e0">
          <span class="ico">👑</span>
          <h3 style="color:#b083e0">MVP</h3>
          <div class="rank-price">300.000</div>
          <div class="rank-rub">29 ₽</div>
          <a href="https://discord.gg/BBkdcHsP2" target="_blank" rel="noopener" class="btn btn-outline pixel-btn" style="box-shadow:inset 0 0 0 2px #b083e0">Купить</a>
        </div>

        <div class="rank-card pixel-panel" style="--accent:#e0a83e">
          <span class="ico">👑</span>
          <h3 style="color:#e0a83e">MVP+</h3>
          <div class="rank-price">850.000</div>
          <div class="rank-rub">59 ₽</div>
          <a href="https://discord.gg/BBkdcHsP2" target="_blank" rel="noopener" class="btn btn-outline pixel-btn" style="box-shadow:inset 0 0 0 2px #e0a83e">Купить</a>
        </div>

        <div class="rank-card pixel-panel" style="--accent:#c7cdd1">
          <span class="ico">🛡️</span>
          <h3 style="color:#c7cdd1">SILVER</h3>
          <div class="rank-price">5.000.000</div>
          <div class="rank-rub">79 ₽</div>
          <a href="https://discord.gg/BBkdcHsP2" target="_blank" rel="noopener" class="btn btn-outline pixel-btn" style="box-shadow:inset 0 0 0 2px #c7cdd1">Купить</a>
        </div>

        <div class="rank-card pixel-panel" style="--accent:#6ecbe0">
          <span class="ico">💎</span>
          <h3 style="color:#6ecbe0">DIAMOND</h3>
          <div class="rank-price">15.000.000</div>
          <div class="rank-rub">129 ₽</div>
          <a href="https://discord.gg/BBkdcHsP2" target="_blank" rel="noopener" class="btn btn-outline pixel-btn" style="box-shadow:inset 0 0 0 2px #6ecbe0">Купить</a>
        </div>

        <div class="rank-card pixel-panel spotlight" style="--accent:var(--redstone)">
          <span class="spot-tag">Топ привилегия</span>
          <span class="ico">👹</span>
          <h3 style="color:var(--redstone)">AEWJN</h3>
          <div class="rank-price">50.000.000</div>
          <div class="rank-rub">299 ₽</div>
          <a href="https://discord.gg/BBkdcHsP2" target="_blank" rel="noopener" class="btn btn-solid pixel-btn">Купить</a>
        </div>
      </div>
    </div>
  </section>

  <!-- ================= DISCORD CTA ================= -->
  <section id="community">
    <div class="container">
      <div class="discord-banner pixel-panel reveal">
        <h2>Присоединяйся к комьюнити</h2>
        <p>Ивенты, розыгрыши привилегий, помощь новичкам и просто адекватный чат — всё в нашем Discord.</p>
        <a href="https://discord.gg/BBkdcHsP2" target="_blank" rel="noopener" class="btn btn-solid pixel-btn" style="background:var(--emerald)">Перейти в Discord →</a>
      </div>
    </div>
  </section>

</main>

<footer>
  <div class="container">
    <div class="footer-top">
      <a href="#home" class="logo">
        <span class="logo-mark"><span></span><span></span></span>
        EpicTowers
      </a>
      <ul class="footer-links">
        <li><a href="#about">О сервере</a></li>
        <li><a href="#rules">Правила</a></li>
        <li><a href="#store">Привилегии</a></li>
        <li><a href="https://discord.gg/BBkdcHsP2" target="_blank" rel="noopener">Discord</a></li>
      </ul>
    </div>
    <div class="footer-bottom">
      <span>epictowers777.mcsh.io</span>
      <span>© 2026 EpicTowers</span>
    </div>
  </div>
</footer>

<script>
  // ---- mobile nav ----
  const navToggle = document.getElementById('nav-toggle');
  const navLinks = document.getElementById('nav-links');
  navToggle.addEventListener('click', () => {
    const open = navLinks.classList.toggle('open');
    navToggle.classList.toggle('open');
    navToggle.setAttribute('aria-expanded', open ? 'true' : 'false');
  });
  document.querySelectorAll('.nav-link').forEach(link => {
    link.addEventListener('click', () => {
      navLinks.classList.remove('open');
      navToggle.classList.remove('open');
    });
  });

  // ---- sticky nav bg on scroll ----
  const nav = document.getElementById('site-nav');
  const onScroll = () => nav.classList.toggle('scrolled', window.scrollY > 16);
  document.addEventListener('scroll', onScroll, { passive:true });
  onScroll();

  // ---- copy IP ----
  const SERVER_IP = 'epictowers777.mcsh.io';
  function flashCopied(btnTextEl, btnEl){
    const original = btnTextEl.textContent;
    btnTextEl.textContent = 'Скопировано!';
    if (btnEl) btnEl.classList.add('copied');
    setTimeout(() => {
      btnTextEl.textContent = original;
      if (btnEl) btnEl.classList.remove('copied');
    }, 2000);
  }
  async function copyIP(btnTextEl, btnEl){
    try{
      await navigator.clipboard.writeText(SERVER_IP);
    }catch(e){
      const input = document.createElement('input');
      input.value = SERVER_IP;
      document.body.appendChild(input);
      input.select();
      try{ document.execCommand('copy'); }catch(err){}
      document.body.removeChild(input);
    }
    flashCopied(btnTextEl, btnEl);
  }
  document.getElementById('copy-ip-btn').addEventListener('click', function(){
    copyIP(document.getElementById('copy-btn-text'), this);
  });
  document.getElementById('hero-copy-btn').addEventListener('click', function(){
    copyIP(this, this);
  });

  // ---- live server status ----
  async function fetchStatus(){
    const dot = document.getElementById('status-dot');
    const text = document.getElementById('status-text');
    try{
      const res = await fetch('https://api.mcsrvstat.us/3/' + SERVER_IP);
      const data = await res.json();
      dot.classList.remove('pulse');
      if(data && data.online){
        dot.classList.add('online');
        dot.classList.remove('offline');
        if(data.players && typeof data.players.online === 'number'){
          text.textContent = 'Онлайн · ' + data.players.online + '/' + data.players.max + ' игроков';
        } else {
          text.textContent = 'Сервер онлайн';
        }
      } else {
        dot.classList.add('offline');
        dot.classList.remove('online');
        text.textContent = 'Сервер сейчас офлайн';
      }
    }catch(e){
      dot.classList.remove('pulse');
      dot.classList.add('offline');
      text.textContent = 'Статус недоступен';
    }
  }
  fetchStatus();
  setInterval(fetchStatus, 60000);

  // ---- scroll reveal ----
  const revealEls = document.querySelectorAll('.reveal');
  if('IntersectionObserver' in window){
    const io = new IntersectionObserver((entries) => {
      entries.forEach(entry => {
        if(entry.isIntersecting){
          entry.target.classList.add('visible');
          io.unobserve(entry.target);
        }
      });
    }, { threshold:0.12 });
    revealEls.forEach(el => io.observe(el));
  } else {
    revealEls.forEach(el => el.classList.add('visible'));
  }
</script>
</body>
</html>
