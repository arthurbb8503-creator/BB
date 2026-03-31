<!DOCTYPE html>

<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Avaliação de Competências 2025</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=DM+Sans:wght@300;400;500;600&family=DM+Mono:wght@400;500&family=Syne:wght@600;700;800&display=swap" rel="stylesheet">
<style>
/* ── RESET & BASE ─────────────────────────────────────────────────────── */
*,*::before,*::after{margin:0;padding:0;box-sizing:border-box}
html{-webkit-font-smoothing:antialiased;font-size:14px}
body{
  font-family:'DM Sans',sans-serif;
  background:#F0F2F5;
  color:#1A1D23;
  min-height:100vh;
  display:flex;
  flex-direction:column;
}

/* ── CSS VARS ─────────────────────────────────────────────────────────── */
:root{
–navy:#0B1F3A;
–blue:#1560BD;
–blue-light:#EBF2FF;
–teal:#0D6E6E;
–teal-light:#E4F4F4;
–amber:#C97400;
–amber-light:#FFF4E0;
–green:#1A6B3C;
–green-light:#E6F4ED;
–red:#C0392B;
–purple:#5B2C8E;
–purple-light:#F0E8FB;
–slate:#64748B;
–border:#DDE3EC;
–white:#FFFFFF;
–surface:#F8FAFC;
–shadow:0 1px 3px rgba(0,0,0,.08),0 4px 16px rgba(0,0,0,.06);
–shadow-lg:0 8px 32px rgba(0,0,0,.12);
–radius:10px;
–radius-sm:6px;
}

/* ── TOP NAV ──────────────────────────────────────────────────────────── */
.topbar{
background:var(–navy);
padding:0 32px;
height:56px;
display:flex;
align-items:center;
justify-content:space-between;
position:sticky;top:0;z-index:100;
box-shadow:0 2px 12px rgba(0,0,0,.3);
}
.topbar-brand{
display:flex;align-items:center;gap:12px;
}
.topbar-logo{
width:32px;height:32px;background:var(–blue);
border-radius:8px;display:flex;align-items:center;justify-content:center;
font-family:‘Syne’,sans-serif;font-weight:800;font-size:.9rem;color:#fff;
}
.topbar-title{
font-family:‘Syne’,sans-serif;font-weight:700;font-size:.95rem;
color:#fff;letter-spacing:.3px;
}
.topbar-title span{color:rgba(255,255,255,.45);font-weight:400;font-size:.8rem;margin-left:6px;}
.topbar-actions{display:flex;align-items:center;gap:10px;}
.btn-print,.btn-reset{
font-family:‘DM Sans’,sans-serif;font-size:.75rem;font-weight:600;
padding:7px 16px;border-radius:6px;border:none;cursor:pointer;
transition:all .15s;letter-spacing:.3px;text-transform:uppercase;
}
.btn-print{background:var(–blue);color:#fff;}
.btn-print:hover{background:#1a6fd4;}
.btn-reset{background:rgba(255,255,255,.1);color:rgba(255,255,255,.8);}
.btn-reset:hover{background:rgba(255,255,255,.18);}

/* ── LAYOUT ───────────────────────────────────────────────────────────── */
.main{
display:grid;
grid-template-columns:240px 1fr;
gap:0;
flex:1;
}

/* ── SIDEBAR ──────────────────────────────────────────────────────────── */
.sidebar{
background:var(–white);
border-right:1px solid var(–border);
padding:24px 0;
position:sticky;top:56px;
height:calc(100vh - 56px);
overflow-y:auto;
}
.sidebar::-webkit-scrollbar{width:4px;}
.sidebar::-webkit-scrollbar-thumb{background:var(–border);border-radius:4px;}

.sidebar-section{margin-bottom:8px;}
.sidebar-section-label{
font-size:.65rem;font-weight:700;letter-spacing:2px;
text-transform:uppercase;color:var(–slate);
padding:12px 20px 6px;
}
.nav-item{
display:flex;align-items:center;gap:10px;
padding:9px 20px;cursor:pointer;
transition:all .15s;border-left:3px solid transparent;
text-decoration:none;color:inherit;
}
.nav-item:hover{background:var(–surface);color:var(–blue);}
.nav-item.active{
background:var(–blue-light);border-left-color:var(–blue);
color:var(–blue);
}
.nav-item .nav-dot{
width:8px;height:8px;border-radius:50%;flex-shrink:0;
background:var(–border);
}
.nav-item.active .nav-dot,.nav-item:hover .nav-dot{background:currentColor;}
.nav-item .nav-label{font-size:.82rem;font-weight:500;line-height:1.3;}
.nav-item .nav-score{
margin-left:auto;font-family:‘DM Mono’,monospace;
font-size:.75rem;font-weight:500;
background:var(–border);color:var(–slate);
padding:2px 7px;border-radius:20px;flex-shrink:0;
}
.nav-item.active .nav-score{background:var(–blue);color:#fff;}

.sidebar-final{
margin:16px 12px 0;
background:var(–navy);
border-radius:var(–radius);
padding:14px;
}
.sidebar-final .sf-label{
font-size:.65rem;font-weight:700;letter-spacing:2px;text-transform:uppercase;
color:rgba(255,255,255,.4);margin-bottom:8px;
}
.sidebar-final .sf-scores{display:flex;gap:8px;}
.sf-score-box{
flex:1;background:rgba(255,255,255,.08);border-radius:6px;
padding:8px;text-align:center;
}
.sf-score-box .sf-num{
font-family:‘DM Mono’,monospace;font-size:1.6rem;font-weight:500;
color:#fff;line-height:1;
display:block;margin-bottom:3px;
}
.sf-score-box .sf-type{
font-size:.6rem;font-weight:600;letter-spacing:1.5px;
text-transform:uppercase;color:rgba(255,255,255,.4);
}

/* ── CONTENT ──────────────────────────────────────────────────────────── */
.content{
padding:28px 32px;
overflow-y:auto;
}

/* ── INFO CARD ────────────────────────────────────────────────────────── */
.info-card{
background:var(–white);border-radius:var(–radius);
border:1px solid var(–border);
padding:20px 24px;margin-bottom:24px;
display:flex;gap:24px;align-items:center;
box-shadow:var(–shadow);
}
.info-field{display:flex;flex-direction:column;gap:4px;flex:1;}
.info-field label{
font-size:.65rem;font-weight:700;letter-spacing:2px;
text-transform:uppercase;color:var(–slate);
}
.info-field input,.info-field select{
font-family:‘DM Sans’,sans-serif;font-size:.9rem;font-weight:500;
border:1.5px solid var(–border);border-radius:6px;
padding:8px 12px;color:var(–navy);background:var(–surface);
outline:none;transition:border-color .15s;width:100%;
}
.info-field input:focus,.info-field select:focus{
border-color:var(–blue);background:#fff;
}
.info-divider{width:1px;background:var(–border);align-self:stretch;}

/* ── TABS ─────────────────────────────────────────────────────────────── */
.tabs{
display:flex;gap:4px;margin-bottom:24px;
background:var(–white);padding:4px;border-radius:10px;
border:1px solid var(–border);box-shadow:var(–shadow);
}
.tab-btn{
flex:1;padding:10px 16px;border:none;cursor:pointer;
border-radius:8px;font-family:‘DM Sans’,sans-serif;
font-size:.8rem;font-weight:600;letter-spacing:.3px;
text-transform:uppercase;transition:all .15s;
color:var(–slate);background:transparent;
}
.tab-btn.active{
background:var(–navy);color:#fff;
box-shadow:0 2px 8px rgba(11,31,58,.25);
}
.tab-btn:not(.active):hover{background:var(–surface);color:var(–navy);}
.tab-panel{display:none;}
.tab-panel.active{display:block;}

/* ── SECTION CARD ─────────────────────────────────────────────────────── */
.comp-section{
background:var(–white);border-radius:var(–radius);
border:1px solid var(–border);margin-bottom:16px;
overflow:hidden;box-shadow:var(–shadow);
}
.comp-header{
display:flex;align-items:center;justify-content:space-between;
padding:14px 20px;cursor:pointer;
border-left:4px solid transparent;
transition:background .15s;user-select:none;
}
.comp-header:hover{background:var(–surface);}
.comp-header.open{border-left-color:currentColor;}
.comp-header-left{display:flex;align-items:center;gap:12px;}
.comp-color-dot{width:10px;height:10px;border-radius:50%;flex-shrink:0;}
.comp-name{font-family:‘Syne’,sans-serif;font-size:.9rem;font-weight:700;}
.comp-desc{font-size:.76rem;color:var(–slate);margin-top:2px;max-width:560px;}
.comp-header-right{display:flex;align-items:center;gap:12px;flex-shrink:0;}
.score-badge{
display:flex;flex-direction:column;align-items:center;
min-width:52px;
}
.score-badge .sb-num{
font-family:‘DM Mono’,monospace;font-size:1.4rem;font-weight:500;
line-height:1;
}
.score-badge .sb-type{
font-size:.55rem;font-weight:700;letter-spacing:1.5px;
text-transform:uppercase;color:var(–slate);margin-top:2px;
}
.score-vs{color:var(–border);font-size:1rem;line-height:1;}
.chevron{
font-size:.75rem;color:var(–slate);
transition:transform .2s;
}
.comp-header.open .chevron{transform:rotate(180deg);}

/* ── TABLE ────────────────────────────────────────────────────────────── */
.comp-body{display:none;border-top:1px solid var(–border);}
.comp-body.open{display:block;}

.eval-table{width:100%;border-collapse:collapse;}
.eval-table thead tr{background:var(–surface);border-bottom:1px solid var(–border);}
.eval-table thead th{
padding:10px 14px;font-size:.65rem;font-weight:700;
letter-spacing:1.5px;text-transform:uppercase;color:var(–slate);
text-align:left;white-space:nowrap;
}
.eval-table thead th:nth-child(2),
.eval-table thead th:nth-child(3),
.eval-table thead th:nth-child(4),
.eval-table thead th:nth-child(5){text-align:center;}

.eval-table tbody tr{
border-bottom:1px solid var(–border);
transition:background .1s;
}
.eval-table tbody tr:last-child{border-bottom:none;}
.eval-table tbody tr:hover{background:#FAFBFF;}
.eval-table tbody tr.low-score{background:#FFF8F7;}

.cell-behavior{
padding:11px 14px;font-size:.82rem;line-height:1.5;
color:var(–navy);max-width:340px;
}
.cell-behavior .beh-icon{margin-right:4px;font-size:.8rem;}

.cell-freq{padding:8px 10px;text-align:center;}
.freq-select{
font-family:‘DM Sans’,sans-serif;font-size:.78rem;font-weight:500;
border:1.5px solid var(–border);border-radius:6px;
padding:6px 8px;outline:none;cursor:pointer;
transition:all .15s;width:140px;
background:var(–surface);color:var(–navy);
-webkit-appearance:none;appearance:none;
background-image:url(“data:image/svg+xml,%3Csvg xmlns=‘http://www.w3.org/2000/svg’ width=‘10’ height=‘6’ fill=‘none’%3E%3Cpath d=‘M1 1l4 4 4-4’ stroke=’%2364748B’ stroke-width=‘1.5’ stroke-linecap=‘round’ stroke-linejoin=‘round’/%3E%3C/svg%3E”);
background-repeat:no-repeat;background-position:right 8px center;
padding-right:24px;
}
.freq-select:focus{border-color:var(–blue);background:#fff;}
.freq-select.score-1{border-color:#E74C3C;background:#FFF5F5;color:#C0392B;}
.freq-select.score-2{border-color:#E67E22;background:#FFF8F0;color:#C97400;}
.freq-select.score-3{border-color:#F1C40F;background:#FFFDE7;color:#946B00;}
.freq-select.score-4{border-color:#27AE60;background:#F0FFF6;color:#1A6B3C;}
.freq-select.score-5{border-color:#2980B9;background:#EBF5FF;color:#1560BD;}

.cell-score{padding:8px 10px;text-align:center;}
.score-chip{
display:inline-flex;align-items:center;justify-content:center;
width:32px;height:32px;border-radius:50%;
font-family:‘DM Mono’,monospace;font-size:.85rem;font-weight:500;
border:2px solid transparent;
}
.score-chip.s0{background:var(–surface);color:var(–slate);border-color:var(–border);}
.score-chip.s1{background:#FDECEC;color:#C0392B;border-color:#F1ABAB;}
.score-chip.s2{background:#FFF2E5;color:#C97400;border-color:#F5C98A;}
.score-chip.s3{background:#FFFBE6;color:#946B00;border-color:#EDD97A;}
.score-chip.s4{background:#E8F8EF;color:#1A6B3C;border-color:#8ED8AA;}
.score-chip.s5{background:#E8F2FF;color:#1560BD;border-color:#8DB8F5;}

.cell-orient{
padding:8px 14px;font-size:.76rem;color:var(–red);
font-style:italic;max-width:220px;line-height:1.45;
}
.cell-orient:empty::before,.cell-orient.empty::before{
content:’—’;color:var(–border);font-style:normal;
}

/* ── COMP SUMMARY FOOTER ──────────────────────────────────────────────── */
.comp-footer{
display:flex;align-items:center;justify-content:space-between;
padding:12px 20px;background:var(–surface);
border-top:1px solid var(–border);
}
.comp-footer-label{
font-size:.72rem;font-weight:600;color:var(–slate);
letter-spacing:.5px;
}
.comp-footer-scores{display:flex;align-items:center;gap:20px;}
.footer-score{display:flex;align-items:center;gap:8px;}
.footer-score .fs-label{
font-size:.68rem;font-weight:600;letter-spacing:1px;
text-transform:uppercase;color:var(–slate);
}
.footer-score .fs-value{
font-family:‘DM Mono’,monospace;font-size:1.1rem;font-weight:500;
}
.footer-score .fs-desc{
font-size:.7rem;color:var(–slate);font-style:italic;
}
.fs-divider{width:1px;height:24px;background:var(–border);}

/* ── RESUMO TAB ───────────────────────────────────────────────────────── */
.resumo-grid{display:grid;grid-template-columns:1fr 1fr;gap:20px;margin-bottom:24px;}
.resumo-card{
background:var(–white);border-radius:var(–radius);
border:1px solid var(–border);box-shadow:var(–shadow);
overflow:hidden;
}
.resumo-card-header{
padding:14px 20px;
font-family:‘Syne’,sans-serif;font-size:.85rem;font-weight:700;
color:#fff;
}
.resumo-card-body{padding:0;}
.resumo-row{
display:flex;align-items:center;justify-content:space-between;
padding:11px 20px;border-bottom:1px solid var(–border);
}
.resumo-row:last-child{border-bottom:none;}
.resumo-row .rr-name{font-size:.82rem;font-weight:500;color:var(–navy);}
.resumo-row .rr-scores{display:flex;align-items:center;gap:8px;}
.rr-score{
font-family:‘DM Mono’,monospace;font-size:.9rem;font-weight:500;
padding:3px 10px;border-radius:4px;min-width:32px;text-align:center;
}
.rr-score.auto{background:var(–blue-light);color:var(–blue);}
.rr-score.lider{background:var(–green-light);color:var(–green);}
.rr-score.diff-pos{color:var(–green);}
.rr-score.diff-neg{color:var(–red);}
.rr-score.diff-0{color:var(–slate);}

.final-banner{
background:var(–navy);border-radius:var(–radius);
padding:28px 32px;display:flex;align-items:center;
justify-content:space-between;box-shadow:var(–shadow-lg);
margin-bottom:24px;
}
.fb-left .fb-title{
font-family:‘Syne’,sans-serif;font-size:1.1rem;font-weight:800;
color:#fff;margin-bottom:4px;
}
.fb-left .fb-desc{font-size:.8rem;color:rgba(255,255,255,.45);}
.fb-right{display:flex;gap:24px;align-items:center;}
.fb-score-block{text-align:center;}
.fb-score-block .fbs-num{
font-family:‘DM Mono’,monospace;font-size:3rem;font-weight:400;
color:#fff;line-height:1;display:block;
}
.fb-score-block .fbs-label{
font-size:.62rem;font-weight:700;letter-spacing:2px;
text-transform:uppercase;color:rgba(255,255,255,.4);
margin-top:4px;display:block;
}
.fb-divider{width:1px;height:60px;background:rgba(255,255,255,.12);}
.fb-level{
background:rgba(255,255,255,.06);border-radius:8px;
padding:14px 18px;max-width:280px;
}
.fb-level .fbl-title{
font-size:.65rem;font-weight:700;letter-spacing:2px;
text-transform:uppercase;color:rgba(255,255,255,.4);margin-bottom:6px;
}
.fb-level .fbl-text{font-size:.8rem;color:rgba(255,255,255,.8);line-height:1.6;}

/* ── SCALE LEGEND ─────────────────────────────────────────────────────── */
.scale-legend{
display:flex;gap:8px;margin-bottom:24px;
}
.scale-item{
flex:1;border-radius:8px;padding:12px 14px;
border:1.5px solid transparent;
}
.scale-item .si-num{
font-family:‘DM Mono’,monospace;font-size:1.4rem;font-weight:500;
display:block;margin-bottom:4px;
}
.scale-item .si-name{font-size:.72rem;font-weight:700;display:block;margin-bottom:3px;}
.scale-item .si-desc{font-size:.66rem;line-height:1.45;opacity:.75;}
.scale-item.l1{background:#FFF5F5;border-color:#F1ABAB;color:#C0392B;}
.scale-item.l2{background:#FFF2E5;border-color:#F5C98A;color:#C97400;}
.scale-item.l3{background:#FFFBE6;border-color:#EDD97A;color:#946B00;}
.scale-item.l4{background:#E8F8EF;border-color:#8ED8AA;color:#1A6B3C;}
.scale-item.l5{background:#E8F2FF;border-color:#8DB8F5;color:#1560BD;}

/* ── PRINT ────────────────────────────────────────────────────────────── */
@media print{
.topbar,.sidebar,.tabs,.btn-print,.btn-reset{display:none!important;}
.main{grid-template-columns:1fr;}
.content{padding:16px;}
.comp-body{display:block!important;}
body{background:#fff;}
.comp-section{break-inside:avoid;margin-bottom:12px;}
}

/* ── ANIMATIONS ───────────────────────────────────────────────────────── */
@keyframes fadeIn{from{opacity:0;transform:translateY(6px)}to{opacity:1;transform:translateY(0)}}
.tab-panel.active{animation:fadeIn .2s ease;}
.comp-body.open{animation:fadeIn .15s ease;}
</style>

</head>
<body>

<!-- ═══ TOP NAR ═══════════════════════════════════════════════════════════ -->

<header class="topbar">
  <div class="topbar-brand">
    <div class="topbar-logo">AC</div>
    <div class="topbar-title">Avaliação de Competências <span>2025</span></div>
  </div>
  <div class="topbar-actions">
    <button class="btn-reset" onclick="resetAll()">↺ Limpar tudo</button>
    <button class="btn-print" onclick="window.print()">⎙ Imprimir</button>
  </div>
</header>

<div class="main">

<!-- ═══ SIDEBAR ══════════════════════════════════════════════════════════ -->

<aside class="sidebar">
  <div class="sidebar-section">
    <div class="sidebar-section-label">Navegação</div>
    <a class="nav-item active" onclick="switchTab('ng',this)" href="#">
      <div class="nav-dot"></div>
      <div class="nav-label">Não Gerenciais</div>
      <div class="nav-score" id="nav-score-ng">—</div>
    </a>
    <a class="nav-item" onclick="switchTab('g',this)" href="#">
      <div class="nav-dot"></div>
      <div class="nav-label">Gerenciais</div>
      <div class="nav-score" id="nav-score-g">—</div>
    </a>
    <a class="nav-item" onclick="switchTab('resumo',this)" href="#">
      <div class="nav-dot"></div>
      <div class="nav-label">Resumo Consolidado</div>
    </a>
  </div>

  <div class="sidebar-section" style="margin-top:8px">
    <div class="sidebar-section-label">Competências — N.G.</div>
    <a class="nav-item" onclick="scrollTo('ng','cativa')" href="#">
      <div class="nav-dot" style="background:#1560BD"></div>
      <div class="nav-label">Cativa o Cliente</div>
      <div class="nav-score" id="sb-ng-cativa">—</div>
    </a>
    <a class="nav-item" onclick="scrollTo('ng','potencializa')" href="#">
      <div class="nav-dot" style="background:#0D6E6E"></div>
      <div class="nav-label">Potencializa Resultados</div>
      <div class="nav-score" id="sb-ng-potencializa">—</div>
    </a>
    <a class="nav-item" onclick="scrollTo('ng','coragem')" href="#">
      <div class="nav-dot" style="background:#C97400"></div>
      <div class="nav-label">Posiciona-se com Coragem</div>
      <div class="nav-score" id="sb-ng-coragem">—</div>
    </a>
    <a class="nav-item" onclick="scrollTo('ng','desenvolve')" href="#">
      <div class="nav-dot" style="background:#5B2C8E"></div>
      <div class="nav-label">Desenvolve-se Continuamente</div>
      <div class="nav-score" id="sb-ng-desenvolve">—</div>
    </a>
    <a class="nav-item" onclick="scrollTo('ng','adapta')" href="#">
      <div class="nav-dot" style="background:#1A6B3C"></div>
      <div class="nav-label">Adapta-se Rapidamente</div>
      <div class="nav-score" id="sb-ng-adapta">—</div>
    </a>
    <a class="nav-item" onclick="scrollTo('ng','diversidade')" href="#">
      <div class="nav-dot" style="background:#4A4A4A"></div>
      <div class="nav-label">Promove Diversidade</div>
      <div class="nav-score" id="sb-ng-diversidade">—</div>
    </a>
  </div>

  <div class="sidebar-final">
    <div class="sf-label">Nota Final Consolidada</div>
    <div class="sf-scores">
      <div class="sf-score-box">
        <span class="sf-num" id="sf-auto">—</span>
        <span class="sf-type">Auto</span>
      </div>
      <div class="sf-score-box">
        <span class="sf-num" id="sf-lider">—</span>
        <span class="sf-type">Líder</span>
      </div>
    </div>
  </div>
</aside>

<!-- ═══ CONTENT ══════════════════════════════════════════════════════════ -->

<main class="content">

  <!-- Info Card -->

  <div class="info-card">
    <div class="info-field" style="max-width:220px">
      <label>Funcionário</label>
      <input type="text" id="nome-func" placeholder="Nome completo" oninput="saveInfo()">
    </div>
    <div class="info-divider"></div>
    <div class="info-field" style="max-width:180px">
      <label>Cargo / Função</label>
      <input type="text" id="cargo" placeholder="Ex: Assistente" oninput="saveInfo()">
    </div>
    <div class="info-divider"></div>
    <div class="info-field" style="max-width:180px">
      <label>Avaliador (Líder)</label>
      <input type="text" id="lider" placeholder="Nome do líder" oninput="saveInfo()">
    </div>
    <div class="info-divider"></div>
    <div class="info-field" style="max-width:140px">
      <label>Período</label>
      <input type="text" id="periodo" placeholder="Ex: Jun/2025" oninput="saveInfo()">
    </div>
  </div>

  <!-- TABS -->

  <div class="tabs">
    <button class="tab-btn active" onclick="switchTab('ng',this)">Comportamentos Não Gerenciais</button>
    <button class="tab-btn" onclick="switchTab('g',this)">Comportamentos Gerenciais</button>
    <button class="tab-btn" onclick="switchTab('resumo',this)">Resumo Consolidado</button>
  </div>

  <!-- ═══ TAB: NÃO GERENCIAIS ════════════════════════════════════════════ -->

  <div class="tab-panel active" id="tab-ng">

```
<!-- CATIVA O CLIENTE -->
<div class="comp-section" id="ng-cativa">
  <div class="comp-header open" onclick="toggleSection(this)" style="color:var(--blue)">
    <div class="comp-header-left">
      <div class="comp-color-dot" style="background:var(--blue)"></div>
      <div>
        <div class="comp-name">Cativa o Cliente</div>
        <div class="comp-desc">Constrói relacionamentos sólidos, fornecendo soluções ágeis e zelando pela satisfação do cliente.</div>
      </div>
    </div>
    <div class="comp-header-right">
      <div class="score-badge">
        <span class="sb-num" id="score-ng-cativa-auto" style="color:var(--blue)">—</span>
        <span class="sb-type">Auto</span>
      </div>
      <div class="score-vs">·</div>
      <div class="score-badge">
        <span class="sb-num" id="score-ng-cativa-lider" style="color:var(--green)">—</span>
        <span class="sb-type">Líder</span>
      </div>
      <span class="chevron">▾</span>
    </div>
  </div>
  <div class="comp-body open">
    <table class="eval-table">
      <thead><tr>
        <th style="width:38%">Comportamento</th>
        <th style="width:16%">Auto-Avaliação</th>
        <th style="width:6%">Score</th>
        <th style="width:16%">Avaliação Líder</th>
        <th style="width:6%">Score</th>
        <th>Orientação (quando score &lt; 3)</th>
      </tr></thead>
      <tbody id="tb-ng-cativa">
      </tbody>
    </table>
    <div class="comp-footer">
      <div class="comp-footer-label">Nota da Competência</div>
      <div class="comp-footer-scores">
        <div class="footer-score">
          <span class="fs-label">Auto</span>
          <span class="fs-value" id="cf-ng-cativa-auto" style="color:var(--blue)">—</span>
        </div>
        <div class="fs-divider"></div>
        <div class="footer-score">
          <span class="fs-label">Líder</span>
          <span class="fs-value" id="cf-ng-cativa-lider" style="color:var(--green)">—</span>
          <span class="fs-desc" id="cf-ng-cativa-desc"></span>
        </div>
      </div>
    </div>
  </div>
</div>

<!-- POTENCIALIZA RESULTADOS -->
<div class="comp-section" id="ng-potencializa">
  <div class="comp-header" onclick="toggleSection(this)" style="color:var(--teal)">
    <div class="comp-header-left">
      <div class="comp-color-dot" style="background:var(--teal)"></div>
      <div>
        <div class="comp-name">Potencializa Resultados</div>
        <div class="comp-desc">Organiza o trabalho de forma eficiente, buscando soluções inovadoras e otimizando processos.</div>
      </div>
    </div>
    <div class="comp-header-right">
      <div class="score-badge"><span class="sb-num" id="score-ng-potencializa-auto" style="color:var(--teal)">—</span><span class="sb-type">Auto</span></div>
      <div class="score-vs">·</div>
      <div class="score-badge"><span class="sb-num" id="score-ng-potencializa-lider" style="color:var(--green)">—</span><span class="sb-type">Líder</span></div>
      <span class="chevron">▾</span>
    </div>
  </div>
  <div class="comp-body">
    <table class="eval-table"><thead><tr>
      <th style="width:38%">Comportamento</th><th style="width:16%">Auto-Avaliação</th><th style="width:6%">Score</th><th style="width:16%">Avaliação Líder</th><th style="width:6%">Score</th><th>Orientação</th>
    </tr></thead><tbody id="tb-ng-potencializa"></tbody></table>
    <div class="comp-footer">
      <div class="comp-footer-label">Nota da Competência</div>
      <div class="comp-footer-scores">
        <div class="footer-score"><span class="fs-label">Auto</span><span class="fs-value" id="cf-ng-potencializa-auto" style="color:var(--teal)">—</span></div>
        <div class="fs-divider"></div>
        <div class="footer-score"><span class="fs-label">Líder</span><span class="fs-value" id="cf-ng-potencializa-lider" style="color:var(--green)">—</span><span class="fs-desc" id="cf-ng-potencializa-desc"></span></div>
      </div>
    </div>
  </div>
</div>

<!-- POSICIONA-SE COM CORAGEM -->
<div class="comp-section" id="ng-coragem">
  <div class="comp-header" onclick="toggleSection(this)" style="color:var(--amber)">
    <div class="comp-header-left">
      <div class="comp-color-dot" style="background:var(--amber)"></div>
      <div>
        <div class="comp-name">Posiciona-se com Coragem</div>
        <div class="comp-desc">Posiciona-se de forma assertiva e construtiva, promovendo a solução de conflitos com ética e firmeza.</div>
      </div>
    </div>
    <div class="comp-header-right">
      <div class="score-badge"><span class="sb-num" id="score-ng-coragem-auto" style="color:var(--amber)">—</span><span class="sb-type">Auto</span></div>
      <div class="score-vs">·</div>
      <div class="score-badge"><span class="sb-num" id="score-ng-coragem-lider" style="color:var(--green)">—</span><span class="sb-type">Líder</span></div>
      <span class="chevron">▾</span>
    </div>
  </div>
  <div class="comp-body">
    <table class="eval-table"><thead><tr>
      <th style="width:38%">Comportamento</th><th style="width:16%">Auto-Avaliação</th><th style="width:6%">Score</th><th style="width:16%">Avaliação Líder</th><th style="width:6%">Score</th><th>Orientação</th>
    </tr></thead><tbody id="tb-ng-coragem"></tbody></table>
    <div class="comp-footer">
      <div class="comp-footer-label">Nota da Competência</div>
      <div class="comp-footer-scores">
        <div class="footer-score"><span class="fs-label">Auto</span><span class="fs-value" id="cf-ng-coragem-auto" style="color:var(--amber)">—</span></div>
        <div class="fs-divider"></div>
        <div class="footer-score"><span class="fs-label">Líder</span><span class="fs-value" id="cf-ng-coragem-lider" style="color:var(--green)">—</span><span class="fs-desc" id="cf-ng-coragem-desc"></span></div>
      </div>
    </div>
  </div>
</div>

<!-- DESENVOLVE-SE CONTINUAMENTE -->
<div class="comp-section" id="ng-desenvolve">
  <div class="comp-header" onclick="toggleSection(this)" style="color:var(--purple)">
    <div class="comp-header-left">
      <div class="comp-color-dot" style="background:var(--purple)"></div>
      <div>
        <div class="comp-name">Desenvolve-se Continuamente</div>
        <div class="comp-desc">Desenvolve-se de forma contínua, aproveitando feedbacks e oportunidades de aprendizado.</div>
      </div>
    </div>
    <div class="comp-header-right">
      <div class="score-badge"><span class="sb-num" id="score-ng-desenvolve-auto" style="color:var(--purple)">—</span><span class="sb-type">Auto</span></div>
      <div class="score-vs">·</div>
      <div class="score-badge"><span class="sb-num" id="score-ng-desenvolve-lider" style="color:var(--green)">—</span><span class="sb-type">Líder</span></div>
      <span class="chevron">▾</span>
    </div>
  </div>
  <div class="comp-body">
    <table class="eval-table"><thead><tr>
      <th style="width:38%">Comportamento</th><th style="width:16%">Auto-Avaliação</th><th style="width:6%">Score</th><th style="width:16%">Avaliação Líder</th><th style="width:6%">Score</th><th>Orientação</th>
    </tr></thead><tbody id="tb-ng-desenvolve"></tbody></table>
    <div class="comp-footer">
      <div class="comp-footer-label">Nota da Competência</div>
      <div class="comp-footer-scores">
        <div class="footer-score"><span class="fs-label">Auto</span><span class="fs-value" id="cf-ng-desenvolve-auto" style="color:var(--purple)">—</span></div>
        <div class="fs-divider"></div>
        <div class="footer-score"><span class="fs-label">Líder</span><span class="fs-value" id="cf-ng-desenvolve-lider" style="color:var(--green)">—</span><span class="fs-desc" id="cf-ng-desenvolve-desc"></span></div>
      </div>
    </div>
  </div>
</div>

<!-- ADAPTA-SE RAPIDAMENTE -->
<div class="comp-section" id="ng-adapta">
  <div class="comp-header" onclick="toggleSection(this)" style="color:var(--green)">
    <div class="comp-header-left">
      <div class="comp-color-dot" style="background:var(--green)"></div>
      <div>
        <div class="comp-name">Adapta-se Rapidamente</div>
        <div class="comp-desc">Mostra-se flexível diante de desafios, adaptando-se rapidamente a mudanças de cenário.</div>
      </div>
    </div>
    <div class="comp-header-right">
      <div class="score-badge"><span class="sb-num" id="score-ng-adapta-auto" style="color:var(--green)">—</span><span class="sb-type">Auto</span></div>
      <div class="score-vs">·</div>
      <div class="score-badge"><span class="sb-num" id="score-ng-adapta-lider" style="color:var(--green)">—</span><span class="sb-type">Líder</span></div>
      <span class="chevron">▾</span>
    </div>
  </div>
  <div class="comp-body">
    <table class="eval-table"><thead><tr>
      <th style="width:38%">Comportamento</th><th style="width:16%">Auto-Avaliação</th><th style="width:6%">Score</th><th style="width:16%">Avaliação Líder</th><th style="width:6%">Score</th><th>Orientação</th>
    </tr></thead><tbody id="tb-ng-adapta"></tbody></table>
    <div class="comp-footer">
      <div class="comp-footer-label">Nota da Competência</div>
      <div class="comp-footer-scores">
        <div class="footer-score"><span class="fs-label">Auto</span><span class="fs-value" id="cf-ng-adapta-auto" style="color:var(--green)">—</span></div>
        <div class="fs-divider"></div>
        <div class="footer-score"><span class="fs-label">Líder</span><span class="fs-value" id="cf-ng-adapta-lider" style="color:var(--green)">—</span><span class="fs-desc" id="cf-ng-adapta-desc"></span></div>
      </div>
    </div>
  </div>
</div>

<!-- PROMOVE DIVERSIDADE -->
<div class="comp-section" id="ng-diversidade">
  <div class="comp-header" onclick="toggleSection(this)" style="color:#4A4A4A">
    <div class="comp-header-left">
      <div class="comp-color-dot" style="background:#4A4A4A"></div>
      <div>
        <div class="comp-name">Promove Diversidade e Inovação</div>
        <div class="comp-desc">Promove ambiente colaborativo e aberto à diversidade, favorecendo a troca de ideias.</div>
      </div>
    </div>
    <div class="comp-header-right">
      <div class="score-badge"><span class="sb-num" id="score-ng-diversidade-auto" style="color:#4A4A4A">—</span><span class="sb-type">Auto</span></div>
      <div class="score-vs">·</div>
      <div class="score-badge"><span class="sb-num" id="score-ng-diversidade-lider" style="color:var(--green)">—</span><span class="sb-type">Líder</span></div>
      <span class="chevron">▾</span>
    </div>
  </div>
  <div class="comp-body">
    <table class="eval-table"><thead><tr>
      <th style="width:38%">Comportamento</th><th style="width:16%">Auto-Avaliação</th><th style="width:6%">Score</th><th style="width:16%">Avaliação Líder</th><th style="width:6%">Score</th><th>Orientação</th>
    </tr></thead><tbody id="tb-ng-diversidade"></tbody></table>
    <div class="comp-footer">
      <div class="comp-footer-label">Nota da Competência</div>
      <div class="comp-footer-scores">
        <div class="footer-score"><span class="fs-label">Auto</span><span class="fs-value" id="cf-ng-diversidade-auto" style="color:#4A4A4A">—</span></div>
        <div class="fs-divider"></div>
        <div class="footer-score"><span class="fs-label">Líder</span><span class="fs-value" id="cf-ng-diversidade-lider" style="color:var(--green)">—</span><span class="fs-desc" id="cf-ng-diversidade-desc"></span></div>
      </div>
    </div>
  </div>
</div>
```

  </div><!-- /tab-ng -->

  <!-- ═══ TAB: GERENCIAIS ════════════════════════════════════════════════ -->

  <div class="tab-panel" id="tab-g">

```
<!-- Each gerencial section follows same pattern -->
<div class="comp-section" id="g-lidera">
  <div class="comp-header open" onclick="toggleSection(this)" style="color:var(--blue)">
    <div class="comp-header-left">
      <div class="comp-color-dot" style="background:var(--blue)"></div>
      <div>
        <div class="comp-name">Lidera pelo Exemplo</div>
        <div class="comp-desc">Lidera alinhado aos valores e objetivos estratégicos, compartilhando o entendimento sobre a organização.</div>
      </div>
    </div>
    <div class="comp-header-right">
      <div class="score-badge"><span class="sb-num" id="score-g-lidera-auto" style="color:var(--blue)">—</span><span class="sb-type">Auto</span></div>
      <div class="score-vs">·</div>
      <div class="score-badge"><span class="sb-num" id="score-g-lidera-lider" style="color:var(--green)">—</span><span class="sb-type">Líder</span></div>
      <span class="chevron">▾</span>
    </div>
  </div>
  <div class="comp-body open">
    <table class="eval-table"><thead><tr><th style="width:38%">Comportamento</th><th style="width:16%">Auto-Avaliação</th><th style="width:6%">Score</th><th style="width:16%">Avaliação Líder</th><th style="width:6%">Score</th><th>Orientação</th></tr></thead><tbody id="tb-g-lidera"></tbody></table>
    <div class="comp-footer"><div class="comp-footer-label">Nota da Competência</div><div class="comp-footer-scores"><div class="footer-score"><span class="fs-label">Auto</span><span class="fs-value" id="cf-g-lidera-auto" style="color:var(--blue)">—</span></div><div class="fs-divider"></div><div class="footer-score"><span class="fs-label">Líder</span><span class="fs-value" id="cf-g-lidera-lider" style="color:var(--green)">—</span><span class="fs-desc" id="cf-g-lidera-desc"></span></div></div></div>
  </div>
</div>

<div class="comp-section" id="g-orienta">
  <div class="comp-header" onclick="toggleSection(this)" style="color:var(--teal)">
    <div class="comp-header-left"><div class="comp-color-dot" style="background:var(--teal)"></div><div><div class="comp-name">Orienta o Desenvolvimento</div><div class="comp-desc">Fornece orientações e feedbacks, promovendo ambiente favorável ao desenvolvimento das pessoas.</div></div></div>
    <div class="comp-header-right"><div class="score-badge"><span class="sb-num" id="score-g-orienta-auto" style="color:var(--teal)">—</span><span class="sb-type">Auto</span></div><div class="score-vs">·</div><div class="score-badge"><span class="sb-num" id="score-g-orienta-lider" style="color:var(--green)">—</span><span class="sb-type">Líder</span></div><span class="chevron">▾</span></div>
  </div>
  <div class="comp-body"><table class="eval-table"><thead><tr><th style="width:38%">Comportamento</th><th style="width:16%">Auto-Avaliação</th><th style="width:6%">Score</th><th style="width:16%">Avaliação Líder</th><th style="width:6%">Score</th><th>Orientação</th></tr></thead><tbody id="tb-g-orienta"></tbody></table><div class="comp-footer"><div class="comp-footer-label">Nota da Competência</div><div class="comp-footer-scores"><div class="footer-score"><span class="fs-label">Auto</span><span class="fs-value" id="cf-g-orienta-auto" style="color:var(--teal)">—</span></div><div class="fs-divider"></div><div class="footer-score"><span class="fs-label">Líder</span><span class="fs-value" id="cf-g-orienta-lider" style="color:var(--green)">—</span><span class="fs-desc" id="cf-g-orienta-desc"></span></div></div></div></div>
</div>

<div class="comp-section" id="g-planeja">
  <div class="comp-header" onclick="toggleSection(this)" style="color:var(--amber)">
    <div class="comp-header-left"><div class="comp-color-dot" style="background:var(--amber)"></div><div><div class="comp-name">Planeja e Alinha</div><div class="comp-desc">Organiza e orienta a atuação da equipe, compartilhando expectativas de desempenho de forma clara.</div></div></div>
    <div class="comp-header-right"><div class="score-badge"><span class="sb-num" id="score-g-planeja-auto" style="color:var(--amber)">—</span><span class="sb-type">Auto</span></div><div class="score-vs">·</div><div class="score-badge"><span class="sb-num" id="score-g-planeja-lider" style="color:var(--green)">—</span><span class="sb-type">Líder</span></div><span class="chevron">▾</span></div>
  </div>
  <div class="comp-body"><table class="eval-table"><thead><tr><th style="width:38%">Comportamento</th><th style="width:16%">Auto-Avaliação</th><th style="width:6%">Score</th><th style="width:16%">Avaliação Líder</th><th style="width:6%">Score</th><th>Orientação</th></tr></thead><tbody id="tb-g-planeja"></tbody></table><div class="comp-footer"><div class="comp-footer-label">Nota da Competência</div><div class="comp-footer-scores"><div class="footer-score"><span class="fs-label">Auto</span><span class="fs-value" id="cf-g-planeja-auto" style="color:var(--amber)">—</span></div><div class="fs-divider"></div><div class="footer-score"><span class="fs-label">Líder</span><span class="fs-value" id="cf-g-planeja-lider" style="color:var(--green)">—</span><span class="fs-desc" id="cf-g-planeja-desc"></span></div></div></div></div>
</div>

<div class="comp-section" id="g-cativa">
  <div class="comp-header" onclick="toggleSection(this)" style="color:var(--purple)">
    <div class="comp-header-left"><div class="comp-color-dot" style="background:var(--purple)"></div><div><div class="comp-name">Cativa o Cliente (Gerencial)</div><div class="comp-desc">Constrói relacionamentos sólidos, fornecendo soluções ágeis e zelando pela satisfação e fidelização.</div></div></div>
    <div class="comp-header-right"><div class="score-badge"><span class="sb-num" id="score-g-cativa-auto" style="color:var(--purple)">—</span><span class="sb-type">Auto</span></div><div class="score-vs">·</div><div class="score-badge"><span class="sb-num" id="score-g-cativa-lider" style="color:var(--green)">—</span><span class="sb-type">Líder</span></div><span class="chevron">▾</span></div>
  </div>
  <div class="comp-body"><table class="eval-table"><thead><tr><th style="width:38%">Comportamento</th><th style="width:16%">Auto-Avaliação</th><th style="width:6%">Score</th><th style="width:16%">Avaliação Líder</th><th style="width:6%">Score</th><th>Orientação</th></tr></thead><tbody id="tb-g-cativa"></tbody></table><div class="comp-footer"><div class="comp-footer-label">Nota da Competência</div><div class="comp-footer-scores"><div class="footer-score"><span class="fs-label">Auto</span><span class="fs-value" id="cf-g-cativa-auto" style="color:var(--purple)">—</span></div><div class="fs-divider"></div><div class="footer-score"><span class="fs-label">Líder</span><span class="fs-value" id="cf-g-cativa-lider" style="color:var(--green)">—</span><span class="fs-desc" id="cf-g-cativa-desc"></span></div></div></div></div>
</div>

<div class="comp-section" id="g-potencializa">
  <div class="comp-header" onclick="toggleSection(this)" style="color:var(--green)">
    <div class="comp-header-left"><div class="comp-color-dot" style="background:var(--green)"></div><div><div class="comp-name">Potencializa Resultados (Gerencial)</div><div class="comp-desc">Organiza o trabalho sob sua condução de forma eficiente, buscando soluções inovadoras para maximizar resultados.</div></div></div>
    <div class="comp-header-right"><div class="score-badge"><span class="sb-num" id="score-g-potencializa-auto" style="color:var(--green)">—</span><span class="sb-type">Auto</span></div><div class="score-vs">·</div><div class="score-badge"><span class="sb-num" id="score-g-potencializa-lider" style="color:var(--green)">—</span><span class="sb-type">Líder</span></div><span class="chevron">▾</span></div>
  </div>
  <div class="comp-body"><table class="eval-table"><thead><tr><th style="width:38%">Comportamento</th><th style="width:16%">Auto-Avaliação</th><th style="width:6%">Score</th><th style="width:16%">Avaliação Líder</th><th style="width:6%">Score</th><th>Orientação</th></tr></thead><tbody id="tb-g-potencializa"></tbody></table><div class="comp-footer"><div class="comp-footer-label">Nota da Competência</div><div class="comp-footer-scores"><div class="footer-score"><span class="fs-label">Auto</span><span class="fs-value" id="cf-g-potencializa-auto" style="color:var(--green)">—</span></div><div class="fs-divider"></div><div class="footer-score"><span class="fs-label">Líder</span><span class="fs-value" id="cf-g-potencializa-lider" style="color:var(--green)">—</span><span class="fs-desc" id="cf-g-potencializa-desc"></span></div></div></div></div>
</div>
```

  </div><!-- /tab-g -->

  <!-- ═══ TAB: RESUMO ════════════════════════════════════════════════════ -->

  <div class="tab-panel" id="tab-resumo">

```
<!-- Escala -->
<div class="scale-legend">
  <div class="scale-item l1"><span class="si-num">1</span><span class="si-name">Não Possui</span><span class="si-desc">Requer suporte constante e orientação contínua.</span></div>
  <div class="scale-item l2"><span class="si-num">2</span><span class="si-name">Em Desenvolvimento</span><span class="si-desc">Demonstra algumas habilidades, necessita orientação.</span></div>
  <div class="scale-item l3"><span class="si-num">3</span><span class="si-name">Atende</span><span class="si-desc">Atende plenamente às expectativas com autonomia.</span></div>
  <div class="scale-item l4"><span class="si-num">4</span><span class="si-name">Supera</span><span class="si-desc">Alto nível de competência, referência positiva.</span></div>
  <div class="scale-item l5"><span class="si-num">5</span><span class="si-name">Referência</span><span class="si-desc">Excelência reconhecida, multiplica conhecimentos.</span></div>
</div>

<!-- Final Banner -->
<div class="final-banner">
  <div class="fb-left">
    <div class="fb-title">Nota Final Consolidada</div>
    <div class="fb-desc">Média das competências não gerenciais + gerenciais avaliadas pelo líder</div>
  </div>
  <div class="fb-right">
    <div class="fb-score-block">
      <span class="fbs-num" id="resumo-final-auto">—</span>
      <span class="fbs-label">Auto-avaliação</span>
    </div>
    <div class="fb-divider"></div>
    <div class="fb-score-block">
      <span class="fbs-num" id="resumo-final-lider">—</span>
      <span class="fbs-label">Avaliação Líder</span>
    </div>
    <div class="fb-divider"></div>
    <div class="fb-level">
      <div class="fbl-title">Nível de Desempenho</div>
      <div class="fbl-text" id="resumo-nivel-desc">Preencha as avaliações nas abas anteriores para obter a nota final consolidada.</div>
    </div>
  </div>
</div>

<!-- Grid de resumo -->
<div class="resumo-grid">
  <div class="resumo-card">
    <div class="resumo-card-header" style="background:var(--blue)">Comportamentos Não Gerenciais</div>
    <div class="resumo-card-body" id="resumo-ng"></div>
  </div>
  <div class="resumo-card">
    <div class="resumo-card-header" style="background:var(--teal)">Comportamentos Gerenciais</div>
    <div class="resumo-card-body" id="resumo-g"></div>
  </div>
</div>
```

  </div><!-- /tab-resumo -->

</main>
</div>

<script>
// ══════════════════════════════════════════════════════════════════════════
//  DATA
// ══════════════════════════════════════════════════════════════════════════
const FREQ_MAP = {"Raramente":1,"As vezes":2,"Muitas vezes":3,"Constantemente":4,"Sempre":5};
const FREQS = ["","Raramente","As vezes","Muitas vezes","Constantemente","Sempre"];
const NIVEL = {
  1:"Não Possui autonomia. Requer suporte e orientação contínua.",
  2:"Em Desenvolvimento. Demonstra algumas habilidades, ainda necessita de orientação.",
  3:"Atende plenamente às expectativas, conduz atividades com autonomia.",
  4:"Supera as expectativas. Alto nível de competência, referência positiva.",
  5:"É Referência na empresa. Excelência reconhecida, multiplica conhecimentos."
};

const DATA = {
  ng: {
    cativa: {
      rows:[
        ["🔹 Recebo cada cliente com um sorriso e uma saudação calorosa.","Utilizar os relatórios de simulação para antecipar as necessidades dos clientes."],
        ["🔹 Chamo os clientes pelo nome sempre que possível.","Manter a quantidade mínima de 10 contatos de crédito do 732 com efetividade acima de 30%."],
        ["🔹 Faço perguntas poderosas para entender melhor as necessidades do cliente.","Ser cuidadoso com a ambiência da agência para o público interno e externo."],
        ["🔹 Demonstro empatia e preocupação genuína em cada atendimento.","Organizar as filas para que os clientes sejam atendidos no menor tempo possível."],
        ["🔹 Pratico escuta ativa para identificar oportunidades de negócio.","Utilizar as ferramentas para definir os melhores públicos para abordagem."],
        ["🔹 Utilizo sempre a melhor oferta da plataforma, verificando o motivo da visita do cliente.","Utilizar as ferramentas de monitoramento de filas para maior conversão de negócios."],
        ["🔹 Utilizo a Jornada do Propósito para me auxiliar nas consultorias.",""],
        ["🔹 Cuido da ambiência da agência para proporcionar uma experiência agradável ao cliente.",""],
        ["🔹 Conheço profundamente os produtos do banco para oferecer as melhores soluções.","Dar feedbacks para colegas com nota individual de atendimento abaixo de 4,8."]
      ]
    },
    potencializa:{
      rows:[
        ["🔹 Otimizo o tempo de atendimento e apresentação de ofertas.","Posicionar-se entre os 40% melhores e/ou saber quantos pontos precisa para estar nessas posições."],
        ["🔹 Utilizo relatórios estratégicos para identificar os melhores públicos para oferta.","Conhecer os melhores públicos dos relatórios 2794, 732, 1586, 2033, 832, 1036."],
        ["🔹 Aproveito os momentos de menor movimento para realizar ofertas ativas.","Conhecer os principais relatórios e utilizar para maior eficiência em vendas."],
        ["🔹 Presto contas diariamente sobre minha produção e resultados.","Responder dentro do prazo todas as demandas da estadual e da comercial."],
        ["🔹 Utilizo uma esteira de negócios para planejar e gerenciar minhas ofertas.","Manter a caixa de e-mail organizada, com e-mails lidos e assuntos tratados."],
        ["🔹 Mantenho minha caixa de e-mail, mesa e pendências organizadas.","Disseminar com a equipe as melhores formas de abordagem negocial."],
        ["🔹 Busco estar entre os primeiros colocados nos rankings (Prêmio Conexão/PIT).","Utilizar todas as ferramentas disponibilizadas pelo banco para efetividade nas vendas."],
        ["🔹 Analiso o desempenho da agência (Conexão), sugerindo estratégias de melhoria.",""],
        ["🔹 Utilizo a Jornada do Propósito para engajar e direcionar meu trabalho.",""],
        ["🔹 Adoto as melhores abordagens comerciais, utilizando perguntas poderosas e gatilhos mentais.",""]
      ]
    },
    coragem:{
      rows:[
        ["🔹 Sou referência na agência para resolver conflitos de maneira eficiente.","Fazer os devidos acompanhamentos da GDP, conversando e registrando oportunidades de melhoria."],
        ["🔹 Mantenho a calma em situações de pressão e conflito.","Ser referência para solução de conflitos na agência."],
        ["🔹 Lido com a pressão de forma produtiva e gerencio meu estresse para manter um ambiente saudável.","Manter a calma durante situações conflituosas mesmo sob pressão."],
        ["🔹 Trato conflitos com sensibilidade e assertividade, garantindo o engajamento dos envolvidos.","Lidar com a pressão de forma produtiva e administrar o estresse e a motivação."],
        ["🔹 Dou feedbacks construtivos, inclusive para meus pares e gestores, registrando na Avaliação de Competências.","Comunicar-se de forma respeitosa e assertiva, apresentando argumentos consistentes."]
      ]
    },
    desenvolve:{
      rows:[
        ["🔹 Faço a trilha estratégica, escolhendo cursos que impactam meu dia a dia.","Selecionar os cursos da trilha que realmente são aplicáveis para o dia a dia."],
        ["🔹 Busco aprendizado contínuo além da UniBB, ouvindo podcasts, lendo livros e assistindo vídeos.","Fazer mensalmente sua autoavaliação, buscando pontos de melhoria."],
        ["🔹 Realizo certificações profissionais para aprimorar minhas competências.","Fazer cursos adicionais à trilha, para adquirir novos conhecimentos."],
        ["🔹 Estou me preparando para o PIT (Programa Interno de Talentos).","Ler livros, ouvir podcasts e vídeos que ajudam a aprimorar os conhecimentos."],
        ["🔹 Tenho interesse em continuar minha formação (pós-graduação, mestrado, doutorado).","Fazer cursos fora do ambiente da UNIBB."],
        ["🔹 Tenho um plano de carreira bem definido e sei quais são os próximos passos.","Aprimorar o conhecimento para utilizar ferramentas do Excel, Teams, Outlook entre outras."],
        ["🔹 Busco mentores dentro e fora do banco para orientar meu crescimento profissional.",""],
        ["🔹 Solicito feedbacks ao meu gestor pelo menos uma vez por mês.",""],
        ["🔹 Reflito conscientemente sobre minhas expectativas de encarreiramento.","Refletir sobre as expectativas de encarreiramento, identificando o que será necessário desenvolver."]
      ]
    },
    adapta:{
      rows:[
        ["🔹 Reformulo minha estratégia quando percebo que algo não está funcionando.","Refazer a estratégia do mês para melhorar o resultado."],
        ["🔹 Busco maneiras de obter melhores resultados com menor esforço.","Pensar e implementar novas formas de fazer, buscando a melhoria contínua."],
        ["🔹 Mantenho uma visão otimista sobre o futuro, encarando adversidades como aprendizado.","Antecipar-se às mudanças e se preparar para lidar com elas."],
        ["🔹 Entendo rapidamente os indicadores do Conexão e me adapto para a entrega do resultado esperado.","Manter o foco e a compostura em situações de tensão, abordando problemas com visão de futuro."],
        ["🔹 Sou hábil no gerenciamento do estresse e sou referência de força e confiança em situações de tensão.",""]
      ]
    },
    diversidade:{
      rows:[
        ["🔹 Participo ativamente das reuniões da equipe, trazendo sugestões de melhoria.","Compartilhar ideias de estratégias nas reuniões, inclusive da Comercial."],
        ["🔹 Busco novas formas de entregar resultados de maneira mais eficiente.","Incentivar os colegas da agência a trazerem ideias para melhorar a estratégia da equipe."],
        ["🔹 Enxergo novas ferramentas como oportunidades de melhoria no meu trabalho.","Buscar interações na equipe, estimulando o diálogo e o feedback constantes."],
        ["🔹 Demonstro interesse genuíno pelas características e valores individuais dos colegas.","Valorizar a diversidade e a colaboração como formas de fomento à melhoria de resultados."],
        ["🔹 Estimulo o diálogo e feedbacks constantes na equipe para aprimorar processos e soluções.","Demonstrar genuíno interesse e respeito pelas características e valores individuais das pessoas."]
      ]
    }
  },
  g: {
    lidera:{
      rows:[
        ["Sou responsável pelos principais negócios da agência, seja fechando ou participando da negociação.","Ser responsável pelos principais negócios da agência."],
        ["Quando temos uma campanha, sou o primeiro a vender o produto para dar o exemplo.","Ser o primeiro a vender o produto quando há uma campanha, para dar o exemplo."],
        ["Sou visto como referência em negociação na agência.","Ser visto como referência em negociação na agência."],
        ["Cuido das pessoas e por isso sou visto como um líder inspirador.","Ser visto como um líder inspirador."],
        ["Sou o primeiro a concluir a trilha de capacitação, escolhendo cursos que me ajudem no dia a dia.","Ser o primeiro a concluir a trilha de capacitação."],
        ["Dou exemplo em consultoria e cuidado com os clientes para que minha equipe copie meus comportamentos.","Minha equipe copiar meus comportamentos e minha forma de atender os clientes."],
        ["Comunico o propósito do banco constantemente para a equipe.","Comunicar o propósito do banco constantemente para a equipe."],
        ["Explico a estratégia corporativa do banco para a equipe, fazendo um link com o Conexão.","Explicar a estratégia corporativa do banco para a equipe."],
        ["Conheço os principais clientes da carteira/grupo negocial.","Conhecer os principais clientes da agência, tanto na PJ como na PF."],
        ["Me atualizo constantemente, lendo diariamente a agência de notícias e as principais novidades do meu mercado.","Atualizar-se constantemente, lendo diariamente a agência de notícias."]
      ]
    },
    orienta:{
      rows:[
        ["Indico cursos que auxiliem os colegas em seu desenvolvimento.","Indicar cursos que auxiliem os colegas em seu desenvolvimento."],
        ["Dou feedback pelo menos uma vez por semana, dizendo exatamente o que o colega precisa melhorar.","Dar feedback pelo menos uma vez por semana."],
        ["Incentivo os colegas a me darem feedbacks.","Incentivar os colegas a darem feedbacks."],
        ["Olho semanalmente o Placar Individual dos colegas, incentivando a busca pelas primeiras colocações.","Olhar semanalmente os Dashboards e incentivar os colegas a buscarem as primeiras colocações."],
        ["Reconheço os colegas que apresentaram melhoria em suas competências e/ou que se destacaram.","Reconhecer os colegas que apresentaram melhoria em suas competências."],
        ["Conheço os objetivos de carreira de todos os meus liderados e os apoio nos próximos passos.","Conhecer os objetivos de carreira de todos os liderados."],
        ["Faço no mínimo 2 anotações de GDP por mês para cada um dos meus liderados.","Fazer no mínimo 2 anotações de GDP por mês para cada liderado."],
        ["Cuido do desenvolvimento de cada um da equipe, sem abandonar ninguém.","Cuidar do desenvolvimento de cada um da equipe."],
        ["Defino notas da Avaliação de Competências antecipadamente (até o segundo mês).",""],
        ["Utilizo as 12 perguntas da Gallup para conversas individuais com os liderados.",""],
        ["Incentivo a formação e performance dos colegas para alcançarem o PIT.",""]
      ]
    },
    planeja:{
      rows:[
        ["Defino diariamente o que é esperado de cada funcionário em ofertas e negócios.","Definir diariamente o que é esperado de cada funcionário em ofertas e negócios."],
        ["Acompanho intradia e sistematicamente o desempenho de cada um, orientando quando necessário.","Acompanhar intradia e sistematicamente o desempenho de cada um."],
        ["Em relação ao Mobilização, tenho planejado meu mês, semana e dia, ajustando a estratégia.","Ter planejado o mês, semana e dia, ajustando a estratégia quando necessário."],
        ["Organizo a equipe para a entrega das Mobilizações.","Organizar a equipe para a entrega dos desafios como o TOPSEG."],
        ["Tenho planejado exatamente o que precisa ser feito para o atingimento dos objetivos.","Ter planejado exatamente o que precisa ser feito para o atingimento dos objetivos."],
        ["Priorizo os negócios em detrimento a questões mais operacionais.","Priorizar os negócios em detrimento a questões mais operacionais."],
        ["Mantenho a velocidade de entrega nos indicadores do Conexão com planejamento e gestão.","Manter a velocidade de entrega nos indicadores do Conexão."],
        ["Uso a planilha de acompanhamento individual e diário, baseado nas necessidades do Placar Individual.",""],
        ["Faço diariamente o Minuto de Ouro, com orientações para o dia.",""],
        ["Sigo as orientações estratégicas da regional, bem como o calendário tático proposto.",""]
      ]
    },
    cativa:{
      rows:[
        ["Utilizo os relatórios de simulação e públicos estratégicos para antecipar as necessidades dos clientes.","Utilizar os relatórios de simulação e públicos estratégicos."],
        ["Mantenho a quantidade mínima de 10 contatos de crédito do 732, com efetividade acima de 30%.","Manter a quantidade mínima de 10 contatos de crédito do 732."],
        ["Sou cuidadoso com a ambiência da agência, seja para o público interno, seja para o externo.","Ser cuidadoso com a ambiência da agência."],
        ["Organizo as filas e o atendimento para que os clientes sejam atendidos no menor tempo possível.","Organizar as filas e o atendimento."],
        ["Utilizo as ferramentas para definir os melhores públicos para abordagem.","Utilizar as ferramentas para definir os melhores públicos."],
        ["Utilizo as ferramentas de monitoramento de filas para conseguir maior conversão de negócios.","Utilizar as ferramentas de monitoramento de filas."],
        ["Defino novas formas de reduzir o fluxo operacional da agência.",""],
        ["Dou feedbacks para colegas com nota individual de atendimento abaixo de 4,8.","Dar feedbacks para colegas com nota individual de atendimento abaixo de 4,8."],
        ["Dou feedbacks para colegas com incidência de reclamações e cancelamento de vendas com impacto no IQV.","Dar feedbacks para colegas com incidência de reclamações."],
        ["Conheço profundamente os produtos do banco para ter autoridade para discutir com a equipe e clientes.","Conhecer profundamente os produtos do banco."],
        ["Utilizo perguntas poderosas para melhorar a consultoria para os clientes.",""],
        ["Conheço e sou referência para os principais clientes da agência.","Conhecer e ser referência para os principais clientes da agência."]
      ]
    },
    potencializa:{
      rows:[
        ["Tenho me posicionado entre os 10% melhores posicionados e/ou sei exatamente quantos pontos preciso.","Posicionar-se entre os 40% melhores e/ou saber quantos pontos precisa."],
        ["Conheço os melhores públicos dos principais relatórios e oriento constantemente a equipe.","Conhecer profundamente os melhores públicos dos relatórios 2794, 732, 1586, 2033, 832, 1036."],
        ["Defino novas formas de atuar para ter mais efetividade nos negócios e ganho de escala.","Conhecer os principais relatórios e utilizar para maior eficiência em vendas."],
        ["Respondo dentro do prazo todas as demandas da estadual e da comercial.","Responder dentro do prazo todas as demandas da estadual e da comercial."],
        ["Mantenho minha caixa de e-mail organizada, com os e-mails lidos e assuntos tratados.","Manter a caixa de e-mail organizada."],
        ["Dissemino com a equipe as melhores formas de abordagem negocial.","Disseminar com a equipe as melhores formas de abordagem negocial."],
        ["Utilizo todas as ferramentas disponibilizadas pelo banco para melhoria da efetividade nas vendas.","Utilizar todas as ferramentas disponibilizadas pelo banco."],
        ["Tenho o Teams e Outlook baixados no celular corporativo para facilitar a comunicação.",""]
      ]
    }
  }
};

// ══════════════════════════════════════════════════════════════════════════
//  STATE
// ══════════════════════════════════════════════════════════════════════════
const state = {};  // state['ng-cativa-0-auto'] = 3

function getKey(tab, comp, idx, type){ return `${tab}-${comp}-${idx}-${type}`; }
function getVal(tab, comp, idx, type){ return state[getKey(tab,comp,idx,type)] || 0; }
function setVal(tab, comp, idx, type, v){
  state[getKey(tab,comp,idx,type)] = v;
  recalcComp(tab, comp);
  updateSidebar();
  updateResumo();
  saveState();
}

// ══════════════════════════════════════════════════════════════════════════
//  BUILD TABLES
// ══════════════════════════════════════════════════════════════════════════
function buildTables(){
  for(const tab of ['ng','g']){
    for(const comp of Object.keys(DATA[tab])){
      const tbody = document.getElementById(`tb-${tab}-${comp}`);
      if(!tbody) continue;
      DATA[tab][comp].rows.forEach(([beh, orient], idx) => {
        const tr = document.createElement('tr');
        tr.id = `row-${tab}-${comp}-${idx}`;
        tr.innerHTML = `
          <td class="cell-behavior"><span class="beh-icon"></span>${beh}</td>
          <td class="cell-freq">
            <select class="freq-select" onchange="onFreqChange('${tab}','${comp}',${idx},'auto',this)">
              ${FREQS.map(f=>`<option value="${f}">${f||'— Selecione —'}</option>`).join('')}
            </select>
          </td>
          <td class="cell-score"><span class="score-chip s0" id="chip-${tab}-${comp}-${idx}-auto">—</span></td>
          <td class="cell-freq">
            <select class="freq-select" onchange="onFreqChange('${tab}','${comp}',${idx},'lider',this)">
              ${FREQS.map(f=>`<option value="${f}">${f||'— Selecione —'}</option>`).join('')}
            </select>
          </td>
          <td class="cell-score"><span class="score-chip s0" id="chip-${tab}-${comp}-${idx}-lider">—</span></td>
          <td class="cell-orient empty" id="orient-${tab}-${comp}-${idx}">${orient||''}</td>
        `;
        tbody.appendChild(tr);
      });
    }
  }
}

function onFreqChange(tab, comp, idx, type, sel){
  const v = FREQ_MAP[sel.value] || 0;
  setVal(tab, comp, idx, type, v);
  // Style chip
  const chip = document.getElementById(`chip-${tab}-${comp}-${idx}-${type}`);
  chip.textContent = v || '—';
  chip.className = `score-chip s${v}`;
  // Style select
  sel.className = `freq-select${v ? ' score-'+v : ''}`;
  // Show/hide orientation
  if(type === 'lider'){
    const orient = document.getElementById(`orient-${tab}-${comp}-${idx}`);
    const orientText = DATA[tab][comp].rows[idx][1];
    if(v > 0 && v < 3 && orientText){
      orient.textContent = orientText;
      orient.classList.remove('empty');
      document.getElementById(`row-${tab}-${comp}-${idx}`).classList.add('low-score');
    } else {
      orient.textContent = orientText ? '' : '';
      orient.classList.add('empty');
      document.getElementById(`row-${tab}-${comp}-${idx}`).classList.remove('low-score');
    }
  }
}

// ══════════════════════════════════════════════════════════════════════════
//  CALC
// ══════════════════════════════════════════════════════════════════════════
function avg(arr){ const f=arr.filter(v=>v>0); return f.length?Math.floor(f.reduce((a,b)=>a+b,0)/f.length):0; }

function recalcComp(tab, comp){
  const rows = DATA[tab][comp].rows;
  const autoVals = rows.map((_,i)=>getVal(tab,comp,i,'auto'));
  const liderVals = rows.map((_,i)=>getVal(tab,comp,i,'lider'));
  const autoScore = avg(autoVals);
  const liderScore = avg(liderVals);

  setDisplay(`score-${tab}-${comp}-auto`, autoScore);
  setDisplay(`score-${tab}-${comp}-lider`, liderScore);
  setDisplay(`cf-${tab}-${comp}-auto`, autoScore);
  setDisplay(`cf-${tab}-${comp}-lider`, liderScore);

  const descEl = document.getElementById(`cf-${tab}-${comp}-desc`);
  if(descEl) descEl.textContent = liderScore ? `· ${['','Não Possui','Em Desenvolvimento','Atende','Supera','Referência'][liderScore]}` : '';

  // Sidebar mini scores
  if(tab==='ng'){
    const sb = document.getElementById(`sb-ng-${comp}`);
    if(sb) sb.textContent = liderScore||'—';
  }
}

function setDisplay(id, val){
  const el = document.getElementById(id);
  if(el) el.textContent = val || '—';
}

function recalcAll(){
  for(const tab of ['ng','g']){
    for(const comp of Object.keys(DATA[tab])){
      recalcComp(tab, comp);
    }
  }
}

function getCompScore(tab, comp, type){
  const rows = DATA[tab][comp].rows;
  return avg(rows.map((_,i)=>getVal(tab,comp,i,type)));
}

function updateSidebar(){
  const ngAuto  = avg(Object.keys(DATA.ng).map(c=>getCompScore('ng',c,'auto')));
  const ngLider = avg(Object.keys(DATA.ng).map(c=>getCompScore('ng',c,'lider')));
  const gAuto   = avg(Object.keys(DATA.g).map(c=>getCompScore('g',c,'auto')));
  const gLider  = avg(Object.keys(DATA.g).map(c=>getCompScore('g',c,'lider')));

  document.getElementById('nav-score-ng').textContent = ngLider||'—';
  document.getElementById('nav-score-g').textContent  = gLider||'—';

  const allAuto  = avg([ngAuto, gAuto].filter(v=>v>0));
  const allLider = avg([ngLider, gLider].filter(v=>v>0));
  document.getElementById('sf-auto').textContent  = allAuto||'—';
  document.getElementById('sf-lider').textContent = allLider||'—';
}

function updateResumo(){
  // NG
  const ngDiv = document.getElementById('resumo-ng');
  ngDiv.innerHTML = '';
  let ngAutoScores=[], ngLiderScores=[];
  for(const comp of Object.keys(DATA.ng)){
    const a = getCompScore('ng',comp,'auto');
    const l = getCompScore('ng',comp,'lider');
    if(a) ngAutoScores.push(a);
    if(l) ngLiderScores.push(l);
    const names = {cativa:'Cativa o Cliente',potencializa:'Potencializa Resultados',coragem:'Posiciona-se com Coragem',desenvolve:'Desenvolve-se Continuamente',adapta:'Adapta-se Rapidamente',diversidade:'Promove Diversidade e Inovação'};
    const diff = (a&&l) ? l-a : null;
    ngDiv.innerHTML += `<div class="resumo-row">
      <div class="rr-name">${names[comp]}</div>
      <div class="rr-scores">
        <span class="rr-score auto">${a||'—'}</span>
        <span class="rr-score lider">${l||'—'}</span>
        ${diff!==null?`<span class="rr-score ${diff>0?'diff-pos':diff<0?'diff-neg':'diff-0'}">${diff>0?'+':''}${diff}</span>`:''}
      </div>
    </div>`;
  }
  // NG total row
  const ngA = avg(ngAutoScores), ngL = avg(ngLiderScores);
  const ngDiff = (ngA&&ngL)?ngL-ngA:null;
  ngDiv.innerHTML += `<div class="resumo-row" style="background:var(--blue-light);font-weight:600">
    <div class="rr-name">Nota Não Gerenciais</div>
    <div class="rr-scores">
      <span class="rr-score auto">${ngA||'—'}</span>
      <span class="rr-score lider">${ngL||'—'}</span>
      ${ngDiff!==null?`<span class="rr-score ${ngDiff>0?'diff-pos':ngDiff<0?'diff-neg':'diff-0'}">${ngDiff>0?'+':''}${ngDiff}</span>`:''}
    </div>
  </div>`;

  // G
  const gDiv = document.getElementById('resumo-g');
  gDiv.innerHTML = '';
  let gAutoScores=[], gLiderScores=[];
  for(const comp of Object.keys(DATA.g)){
    const a = getCompScore('g',comp,'auto');
    const l = getCompScore('g',comp,'lider');
    if(a) gAutoScores.push(a);
    if(l) gLiderScores.push(l);
    const names = {lidera:'Lidera pelo Exemplo',orienta:'Orienta o Desenvolvimento',planeja:'Planeja e Alinha',cativa:'Cativa o Cliente',potencializa:'Potencializa Resultados'};
    const diff = (a&&l)?l-a:null;
    gDiv.innerHTML += `<div class="resumo-row">
      <div class="rr-name">${names[comp]}</div>
      <div class="rr-scores">
        <span class="rr-score auto">${a||'—'}</span>
        <span class="rr-score lider">${l||'—'}</span>
        ${diff!==null?`<span class="rr-score ${diff>0?'diff-pos':diff<0?'diff-neg':'diff-0'}">${diff>0?'+':''}${diff}</span>`:''}
      </div>
    </div>`;
  }
  const gA = avg(gAutoScores), gL = avg(gLiderScores);
  const gDiff = (gA&&gL)?gL-gA:null;
  gDiv.innerHTML += `<div class="resumo-row" style="background:var(--teal-light);font-weight:600">
    <div class="rr-name">Nota Gerenciais</div>
    <div class="rr-scores">
      <span class="rr-score auto">${gA||'—'}</span>
      <span class="rr-score lider">${gL||'—'}</span>
      ${gDiff!==null?`<span class="rr-score ${gDiff>0?'diff-pos':gDiff<0?'diff-neg':'diff-0'}">${gDiff>0?'+':''}${gDiff}</span>`:''}
    </div>
  </div>`;

  // Final
  const allAuto  = avg([ngA,gA].filter(v=>v>0));
  const allLider = avg([ngL,gL].filter(v=>v>0));
  document.getElementById('resumo-final-auto').textContent  = allAuto||'—';
  document.getElementById('resumo-final-lider').textContent = allLider||'—';
  document.getElementById('resumo-nivel-desc').textContent  = allLider ? NIVEL[allLider] : 'Preencha as avaliações nas abas anteriores para obter a nota final consolidada.';
}

// ══════════════════════════════════════════════════════════════════════════
//  UI INTERACTIONS
// ══════════════════════════════════════════════════════════════════════════
function toggleSection(header){
  header.classList.toggle('open');
  header.nextElementSibling.classList.toggle('open');
}

let currentTab = 'ng';
function switchTab(tab, triggerEl){
  currentTab = tab;
  document.querySelectorAll('.tab-panel').forEach(p=>p.classList.remove('active'));
  document.querySelectorAll('.tab-btn').forEach(b=>b.classList.remove('active'));
  document.querySelectorAll('.nav-item').forEach(n=>n.classList.remove('active'));

  document.getElementById(`tab-${tab}`).classList.add('active');

  // Activate correct tab button
  document.querySelectorAll('.tab-btn').forEach(b=>{
    if((tab==='ng'&&b.textContent.includes('Não Gerenciais'))||
       (tab==='g'&&b.textContent.includes('Gerenciais')&&!b.textContent.includes('Não'))||
       (tab==='resumo'&&b.textContent.includes('Resumo')))
      b.classList.add('active');
  });

  // Activate sidebar nav
  if(triggerEl && triggerEl.classList && triggerEl.classList.contains('nav-item'))
    triggerEl.classList.add('active');
}

function scrollTo(tab, comp){
  switchTab(tab, null);
  setTimeout(()=>{
    const el = document.getElementById(`${tab}-${comp}`);
    if(el) el.scrollIntoView({behavior:'smooth', block:'start'});
  }, 50);
}

function saveInfo(){
  try{
    localStorage.setItem('ac_info', JSON.stringify({
      nome: document.getElementById('nome-func').value,
      cargo: document.getElementById('cargo').value,
      lider: document.getElementById('lider').value,
      periodo: document.getElementById('periodo').value,
    }));
  }catch(e){}
}

function saveState(){
  try{ localStorage.setItem('ac_state', JSON.stringify(state)); }catch(e){}
}

function loadState(){
  try{
    const info = JSON.parse(localStorage.getItem('ac_info')||'{}');
    if(info.nome) document.getElementById('nome-func').value = info.nome;
    if(info.cargo) document.getElementById('cargo').value = info.cargo;
    if(info.lider) document.getElementById('lider').value = info.lider;
    if(info.periodo) document.getElementById('periodo').value = info.periodo;

    const saved = JSON.parse(localStorage.getItem('ac_state')||'{}');
    Object.assign(state, saved);

    // Re-apply state to selects
    for(const key of Object.keys(state)){
      const v = state[key];
      if(!v) continue;
      const [tab,comp,idx,type] = key.split('-');
      if(!DATA[tab]||!DATA[tab][comp]) continue;
      const freqVal = FREQS[v];
      const tbodyId = `tb-${tab}-${comp}`;
      const tbody = document.getElementById(tbodyId);
      if(!tbody) continue;
      const row = tbody.rows[parseInt(idx)];
      if(!row) continue;
      const selIdx = type==='auto'?0:1;
      const sels = row.querySelectorAll('select');
      if(sels[selIdx]){
        sels[selIdx].value = freqVal;
        sels[selIdx].className = `freq-select score-${v}`;
        const chip = row.querySelector(`#chip-${tab}-${comp}-${idx}-${type}`);
        if(chip){chip.textContent=v;chip.className=`score-chip s${v}`;}
        if(type==='lider'){
          const orient = document.getElementById(`orient-${tab}-${comp}-${idx}`);
          const orientText = DATA[tab][comp].rows[parseInt(idx)][1];
          if(v < 3 && orientText){
            orient.textContent = orientText;
            orient.classList.remove('empty');
            const rowEl = document.getElementById(`row-${tab}-${comp}-${idx}`);
            if(rowEl) rowEl.classList.add('low-score');
          }
        }
      }
    }
    recalcAll();
    updateSidebar();
    updateResumo();
  }catch(e){}
}

function resetAll(){
  if(!confirm('Limpar todas as avaliações? Esta ação não pode ser desfeita.')) return;
  Object.keys(state).forEach(k=>delete state[k]);
  document.querySelectorAll('.freq-select').forEach(s=>{s.value='';s.className='freq-select';});
  document.querySelectorAll('.score-chip').forEach(c=>{c.textContent='—';c.className='score-chip s0';});
  document.querySelectorAll('.cell-orient').forEach(o=>o.classList.add('empty'));
  document.querySelectorAll('tbody tr').forEach(r=>r.classList.remove('low-score'));
  recalcAll();
  updateSidebar();
  updateResumo();
  try{localStorage.removeItem('ac_state');}catch(e){}
}

// ══════════════════════════════════════════════════════════════════════════
//  INIT
// ══════════════════════════════════════════════════════════════════════════
buildTables();
loadState();
</script>

</body>
</html>
