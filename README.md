<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>WS Express — Motoboy em Marília</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Barlow+Condensed:wght@600;700;800&family=Inter:wght@400;500;600&family=IBM+Plex+Mono:wght@500;600&display=swap" rel="stylesheet">
<style>
  :root{
    --asphalt: #17181B;
    --asphalt-2: #202226;
    --yellow: #F2C230;
    --orange: #D9480F;
    --paper: #F4F2ED;
    --mist: #9A9DA6;
    --line: rgba(244,242,237,0.12);
  }
  *{margin:0;padding:0;box-sizing:border-box;}
  html{scroll-behavior:smooth;}
  body{
    background:var(--asphalt);
    color:var(--paper);
    font-family:'Inter',sans-serif;
    -webkit-font-smoothing:antialiased;
    overflow-x:hidden;
  }
  h1,h2,h3,.display{
    font-family:'Barlow Condensed',sans-serif;
    text-transform:uppercase;
    letter-spacing:0.01em;
    font-weight:800;
  }
  .mono{font-family:'IBM Plex Mono',monospace;}
  a{color:inherit;text-decoration:none;}
  .wrap{max-width:1080px;margin:0 auto;padding:0 24px;}

  /* ---------- NAV ---------- */
  nav{
    position:sticky;top:0;z-index:50;
    background:rgba(23,24,27,0.9);
    backdrop-filter:blur(8px);
    border-bottom:1px solid var(--line);
  }
  nav .wrap{display:flex;align-items:center;justify-content:space-between;height:64px;}
  .brand{display:flex;align-items:center;gap:10px;font-family:'Barlow Condensed';font-weight:800;font-size:22px;letter-spacing:0.02em;}
  .brand .dot{width:10px;height:10px;background:var(--yellow);border-radius:2px;transform:rotate(45deg);}
  .nav-links{display:flex;gap:28px;font-size:14px;color:var(--mist);}
  .nav-links a:hover{color:var(--paper);}
  .nav-cta{
    background:var(--yellow);color:var(--asphalt);padding:9px 18px;border-radius:3px;
    font-weight:600;font-size:14px;
  }
  @media(max-width:720px){.nav-links{display:none;}}

  /* ---------- HERO ---------- */
  .hero{padding:72px 0 40px;position:relative;}
  .eyebrow{
    display:inline-flex;align-items:center;gap:8px;
    color:var(--yellow);font-family:'IBM Plex Mono';font-size:12px;
    letter-spacing:0.12em;text-transform:uppercase;margin-bottom:20px;
  }
  .eyebrow::before{content:'';width:24px;height:1px;background:var(--yellow);}
  .hero h1{font-size:clamp(42px,7vw,74px);line-height:0.98;max-width:820px;}
  .hero h1 span{color:var(--yellow);}
  .hero p.lead{
    font-size:18px;color:var(--mist);max-width:480px;margin-top:22px;line-height:1.55;
  }
  .hero-cta{display:flex;gap:14px;margin-top:34px;flex-wrap:wrap;}
  .btn-primary{
    background:var(--yellow);color:var(--asphalt);padding:14px 26px;border-radius:3px;
    font-weight:600;font-size:15px;display:inline-flex;align-items:center;gap:8px;
    transition:transform .15s ease;
  }
  .btn-primary:hover{transform:translateY(-2px);}
  .btn-ghost{
    border:1px solid var(--line);padding:14px 26px;border-radius:3px;font-size:15px;color:var(--paper);
  }

  /* route map signature */
  .route-box{margin-top:56px;border:1px solid var(--line);border-radius:6px;background:var(--asphalt-2);padding:28px 24px 20px;overflow:hidden;}
  .route-box .cap{display:flex;justify-content:space-between;font-family:'IBM Plex Mono';font-size:11px;color:var(--mist);letter-spacing:0.08em;text-transform:uppercase;margin-bottom:14px;}
  .route-box .cap b{color:var(--yellow);}
  svg#routeSvg{width:100%;height:auto;display:block;}
  .route-dash{stroke-dasharray:10 8;animation:dashmove 2.2s linear infinite;}
  @keyframes dashmove{to{stroke-dashoffset:-36;}}
  .moto{animation:motomove 6s ease-in-out infinite;}
  @keyframes motomove{
    0%{offset-distance:0%;}
    100%{offset-distance:100%;}
  }
  .stop-label{font-family:'IBM Plex Mono';font-size:11px;fill:var(--mist);}
  .stop-dot{fill:var(--yellow);}
  @media (prefers-reduced-motion: reduce){
    .route-dash{animation:none;}
    .moto{animation:none;}
  }

  /* ---------- SECTIONS ---------- */
  section{padding:76px 0;border-top:1px solid var(--line);}
  .section-head{margin-bottom:42px;}
  .section-head .eyebrow{margin-bottom:14px;}
  .section-head h2{font-size:clamp(30px,4vw,42px);}
  .section-head p{color:var(--mist);max-width:520px;margin-top:10px;font-size:15px;}

  /* como funciona */
  .steps{display:grid;grid-template-columns:repeat(3,1fr);gap:24px;}
  .step{border:1px solid var(--line);border-radius:6px;padding:26px 22px;background:var(--asphalt-2);}
  .step .num{font-family:'IBM Plex Mono';color:var(--yellow);font-size:13px;margin-bottom:14px;}
  .step h3{font-size:24px;margin-bottom:8px;}
  .step p{color:var(--mist);font-size:14px;line-height:1.5;}
  @media(max-width:800px){.steps{grid-template-columns:1fr;}}

  /* cobertura */
  .coverage{display:grid;grid-template-columns:1.1fr 0.9fr;gap:40px;align-items:center;}
  .bairro-list{list-style:none;}
  .bairro-list li{
    display:flex;align-items:center;gap:14px;padding:13px 0;border-bottom:1px solid var(--line);font-size:16px;
  }
  .bairro-list li::before{content:'';width:7px;height:7px;background:var(--yellow);border-radius:50%;flex-shrink:0;}
  .coverage-note{background:var(--asphalt-2);border:1px solid var(--line);border-radius:6px;padding:24px;}
  .coverage-note .mono{color:var(--yellow);font-size:12px;letter-spacing:0.08em;text-transform:uppercase;}
  .coverage-note p{margin-top:12px;color:var(--mist);font-size:14px;line-height:1.6;}
  @media(max-width:800px){.coverage{grid-template-columns:1fr;}}

  /* preços - dispatch board */
  .board{border:1px solid var(--line);border-radius:6px;overflow:hidden;background:var(--asphalt-2);}
  .board-row{display:grid;grid-template-columns:2fr 1fr 1fr;padding:18px 24px;border-bottom:1px solid var(--line);align-items:center;}
  .board-row:last-child{border-bottom:none;}
  .board-row.head{background:rgba(242,194,48,0.06);}
  .board-row.head span{font-family:'IBM Plex Mono';font-size:11px;color:var(--yellow);letter-spacing:0.1em;text-transform:uppercase;}
  .board-row .name{font-size:16px;}
  .board-row .desc{font-size:13px;color:var(--mist);margin-top:2px;}
  .board-row .price{font-family:'IBM Plex Mono';font-size:20px;color:var(--yellow);text-align:right;}
  .board-note{color:var(--mist);font-size:13px;margin-top:14px;}

  /* depoimentos */
  .testis{display:grid;grid-template-columns:repeat(3,1fr);gap:20px;}
  .testi{border:1px solid var(--line);border-radius:6px;padding:22px;background:var(--asphalt-2);}
  .testi p{font-size:15px;line-height:1.6;color:var(--paper);}
  .testi .who{margin-top:16px;font-family:'IBM Plex Mono';font-size:12px;color:var(--mist);}
  @media(max-width:800px){.testis{grid-template-columns:1fr;}}

  /* cta final */
  .final-cta{text-align:center;padding:90px 0;}
  .final-cta h2{font-size:clamp(34px,6vw,58px);max-width:700px;margin:0 auto;}
  .final-cta p{color:var(--mist);margin:18px auto 30px;max-width:440px;}

  footer{border-top:1px solid var(--line);padding:30px 0;}
  footer .wrap{display:flex;justify-content:space-between;align-items:center;font-size:13px;color:var(--mist);flex-wrap:wrap;gap:10px;}

  /* whatsapp float */
  .float-wa{
    position:fixed;bottom:22px;right:22px;z-index:60;
    background:var(--yellow);color:var(--asphalt);
    width:56px;height:56px;border-radius:50%;
    display:flex;align-items:center;justify-content:center;
    box-shadow:0 6px 18px rgba(0,0,0,0.4);
    font-size:26px;
  }
</style>
</head>
<body>

<nav>
  <div class="wrap">
    <div class="brand"><span class="dot"></span>WS EXPRESS</div>
    <div class="nav-links">
      <a href="#como-funciona">Como funciona</a>
      <a href="#cobertura">Área</a>
      <a href="#precos">Preços</a>
      <a href="#depoimentos">Clientes</a>
    </div>
    <a class="nav-cta" href="https://wa.me/5514991113660" target="_blank" rel="noopener">Pedir agora</a>
  </div>
</nav>

<header class="hero">
  <div class="wrap">
    <div class="eyebrow">Entregas em Marília · SP</div>
    <h1>Sua entrega sai<br><span>em minutos,</span><br>não em horas.</h1>
    <p class="lead">Motoboy próprio para o seu negócio ou para sua encomenda pessoal. Você chama pelo WhatsApp, a gente já está a caminho.</p>
    <div class="hero-cta">
      <a class="btn-primary" href="https://wa.me/5514991113660" target="_blank" rel="noopener">Chamar no WhatsApp →</a>
      <a class="btn-ghost" href="#precos">Ver preços</a>
    </div>

    <div class="route-box">
      <div class="cap"><span>Rota ativa</span><b>Centro → Palmital</b></div>
      <svg id="routeSvg" viewBox="0 0 900 180" xmlns="http://www.w3.org/2000/svg">
        <path id="routePath" d="M40,140 C 180,40 260,150 400,90 S 620,20 860,60" fill="none" stroke="var(--line)" stroke-width="2"/>
        <path d="M40,140 C 180,40 260,150 400,90 S 620,20 860,60" fill="none" stroke="var(--yellow)" stroke-width="2" class="route-dash"/>
        <circle cx="40" cy="140" r="5" class="stop-dot"/>
        <text x="40" y="162" class="stop-label" text-anchor="middle">CENTRO</text>
        <circle cx="400" cy="90" r="5" class="stop-dot"/>
        <text x="400" y="112" class="stop-label" text-anchor="middle">JD. AMÉRICA</text>
        <circle cx="860" cy="60" r="5" class="stop-dot"/>
        <text x="860" y="82" class="stop-label" text-anchor="middle">PALMITAL</text>
        <circle r="6" fill="#D9480F">
          <animateMotion dur="4s" repeatCount="indefinite" rotate="auto"
            path="M40,140 C 180,40 260,150 400,90 S 620,20 860,60"/>
        </circle>
      </svg>
    </div>
  </div>
</header>

<section id="como-funciona">
  <div class="wrap">
    <div class="section-head">
      <div class="eyebrow">Como funciona</div>
      <h2>Três passos até a porta</h2>
    </div>
    <div class="steps">
      <div class="step">
        <div class="num">01 / CHAMADA</div>
        <h3>Chame no WhatsApp</h3>
        <p>Descreva a coleta e a entrega. Em poucos minutos você recebe o valor da corrida.</p>
      </div>
      <div class="step">
        <div class="num">02 / COLETA</div>
        <h3>Motoboy busca no local</h3>
        <p>Endereço confirmado, coleta rápida — sem enrolação, sem espera longa.</p>
      </div>
      <div class="step">
        <div class="num">03 / ENTREGA</div>
        <h3>Aviso na entrega</h3>
        <p>Você recebe a confirmação assim que o pacote chega ao destino.</p>
      </div>
    </div>
  </div>
</section>

<section id="cobertura">
  <div class="wrap coverage">
    <div>
      <div class="section-head">
        <div class="eyebrow">Área de cobertura</div>
        <h2>Rodamos toda Marília</h2>
        <p>Cobertura nos principais bairros da cidade, com prioridade para região central e adjacências.</p>
      </div>
      <ul class="bairro-list">
        <li>Centro</li>
        <li>Jardim América</li>
        <li>Palmital / Altos do Palmital</li>
        <li>Jardim Aeroporto</li>
        <li>Jardim Alvorada</li>
        <li>Demais bairros sob consulta</li>
      </ul>
    </div>
    <div class="coverage-note">
      <div class="mono">Fora da área listada?</div>
      <p>Atendemos também bairros vizinhos e distritos próximos — envie o endereço de coleta e de entrega pelo WhatsApp que confirmamos o valor e o prazo na hora.</p>
    </div>
  </div>
</section>

<section id="precos">
  <div class="wrap">
    <div class="section-head">
      <div class="eyebrow">Tabela</div>
      <h2>Preços claros, sem surpresa</h2>
    </div>
    <div class="board">
      <div class="board-row head">
        <span>Serviço</span><span>Prazo médio</span><span>Valor</span>
      </div>
      <div class="board-row">
        <div><div class="name">Corrida no bairro</div><div class="desc">Coleta e entrega no mesmo bairro ou vizinho</div></div>
        <div class="mono">15–25 min</div>
        <div class="price">R$ 10</div>
      </div>
      <div class="board-row">
        <div><div class="name">Corrida entre bairros</div><div class="desc">Cruzando a cidade, distâncias maiores</div></div>
        <div class="mono">25–40 min</div>
        <div class="price">R$ 15</div>
      </div>
      <div class="board-row">
        <div><div class="name">Pacote mensal comércio</div><div class="desc">Entregas recorrentes para lojas e restaurantes</div></div>
        <div class="mono">sob demanda</div>
        <div class="price">Consultar</div>
      </div>
    </div>
    <p class="board-note">* Valores de referência — ajuste conforme a distância real e o combustível na sua região.</p>
  </div>
</section>

<section id="depoimentos">
  <div class="wrap">
    <div class="section-head">
      <div class="eyebrow">Quem já pediu</div>
      <h2>Confiança de quem usa toda semana</h2>
    </div>
    <div class="testis">
      <div class="testi"><p>Chamo sempre que preciso mandar documento urgente. Nunca atrasou.</p><div class="who">— Cliente do Centro</div></div>
      <div class="testi"><p>Uso pra entregar os pedidos da minha loja. Combinei um pacote fixo por mês.</p><div class="who">— Comércio local</div></div>
      <div class="testi"><p>Rápido pra combinar pelo WhatsApp e o valor já vem certo antes de confirmar.</p><div class="who">— Cliente do Jardim América</div></div>
    </div>
  </div>
</section>

<section class="final-cta">
  <div class="wrap">
    <h2>Precisa entregar algo <span style="color:var(--yellow)">agora</span>?</h2>
    <p>Chame no WhatsApp e receba o valor da corrida na hora.</p>
    <a class="btn-primary" href="https://wa.me/5514991113660" target="_blank" rel="noopener">Chamar no WhatsApp →</a>
  </div>
</section>

<footer>
  <div class="wrap">
    <div>WS Express — Motoboy em Marília</div>
    <div>Marília, SP · Atendimento via WhatsApp</div>
  </div>
</footer>

<a class="float-wa" href="https://wa.me/5514991113660" target="_blank" rel="noopener" aria-label="Chamar no WhatsApp">💬</a>

</body>
</html>
