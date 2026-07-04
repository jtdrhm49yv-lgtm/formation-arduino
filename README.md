<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
<title>Arduino — Cours Complet Débutant | Formation Technique</title>
<style>
:root{
  --bg:#0a1f1f;
  --bg2:#0e2929;
  --card:#123434;
  --card2:#16403f;
  --teal:#1e5f5c;
  --teal-l:#2d8a85;
  --amber:#f0a500;
  --amber-l:#ffc93c;
  --txt:#e8f0ef;
  --txt2:#a8c5c2;
  --ok:#4caf7d;
  --warn:#ff6b5b;
  --code-bg:#081818;
  --radius:14px;
}
*{margin:0;padding:0;box-sizing:border-box;-webkit-tap-highlight-color:transparent}
html{scroll-behavior:smooth}
body{
  font-family:-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,sans-serif;
  background:var(--bg);
  color:var(--txt);
  line-height:1.65;
  font-size:16px;
  overflow-x:hidden;
}
/* ===== HEADER ===== */
.hdr{
  position:sticky;top:0;z-index:100;
  background:linear-gradient(180deg,var(--bg2) 0%,rgba(14,41,41,.96) 100%);
  backdrop-filter:blur(10px);
  border-bottom:1px solid rgba(240,165,0,.25);
  padding:10px 14px;
}
.hdr-top{display:flex;align-items:center;justify-content:space-between;gap:8px}
.hdr h1{font-size:15px;font-weight:700;color:var(--amber);letter-spacing:.3px}
.hdr .sub{font-size:11px;color:var(--txt2)}
.menu-btn{
  background:var(--card2);border:1px solid var(--teal-l);color:var(--amber);
  border-radius:10px;padding:7px 12px;font-size:13px;font-weight:600;cursor:pointer;
}
.progress-wrap{margin-top:8px;height:5px;background:rgba(255,255,255,.08);border-radius:3px;overflow:hidden}
.progress-bar{height:100%;width:0%;background:linear-gradient(90deg,var(--teal-l),var(--amber));border-radius:3px;transition:width .4s ease}
/* ===== MENU MODULES ===== */
.menu{
  position:fixed;inset:0;z-index:200;background:rgba(8,20,20,.97);
  display:none;overflow-y:auto;padding:20px 16px 60px;
}
.menu.open{display:block}
.menu h2{color:var(--amber);font-size:18px;margin-bottom:4px}
.menu p{color:var(--txt2);font-size:13px;margin-bottom:18px}
.menu-close{position:absolute;top:16px;right:16px;background:var(--card2);border:1px solid var(--teal-l);color:var(--txt);border-radius:50%;width:36px;height:36px;font-size:17px;cursor:pointer}
.menu-item{
  display:flex;align-items:center;gap:12px;
  background:var(--card);border:1px solid rgba(45,138,133,.35);
  border-radius:var(--radius);padding:13px 14px;margin-bottom:10px;cursor:pointer;
  transition:transform .15s,border-color .15s;
}
.menu-item:active{transform:scale(.98)}
.menu-item.done{border-color:var(--ok)}
.menu-item .num{
  min-width:34px;height:34px;border-radius:9px;
  background:var(--teal);color:var(--amber-l);
  display:flex;align-items:center;justify-content:center;
  font-weight:800;font-size:14px;
}
.menu-item.done .num{background:var(--ok);color:#08211a}
.menu-item .mi-t{font-size:14px;font-weight:600}
.menu-item .mi-s{font-size:11.5px;color:var(--txt2)}
/* ===== MODULES ===== */
.module{display:none;padding:18px 16px 110px;max-width:760px;margin:0 auto;animation:fadeIn .35s ease}
.module.active{display:block}
@keyframes fadeIn{from{opacity:0;transform:translateY(8px)}to{opacity:1;transform:none}}
.mod-tag{
  display:inline-block;background:var(--teal);color:var(--amber-l);
  font-size:11px;font-weight:700;letter-spacing:1.2px;text-transform:uppercase;
  padding:4px 12px;border-radius:20px;margin-bottom:10px;
}
.module h2{font-size:24px;line-height:1.25;margin-bottom:6px;color:#fff}
.module h2 span{color:var(--amber)}
.mod-intro{color:var(--txt2);font-size:14.5px;margin-bottom:20px}
.module h3{
  font-size:17px;color:var(--amber-l);margin:26px 0 10px;
  padding-left:12px;border-left:4px solid var(--amber);
}
.module h4{font-size:15px;color:var(--teal-l);margin:18px 0 8px}
.module p{margin-bottom:12px;font-size:15px}
.module strong{color:var(--amber-l)}
.module ul,.module ol{margin:0 0 14px 20px}
.module li{margin-bottom:7px;font-size:15px}
/* ===== ENCADRÉS ===== */
.enclair{
  background:linear-gradient(135deg,rgba(30,95,92,.5),rgba(18,52,52,.8));
  border:1px solid var(--teal-l);border-radius:var(--radius);
  padding:14px 16px;margin:16px 0;
}
.enclair .box-t{color:var(--amber);font-weight:800;font-size:13px;letter-spacing:1px;text-transform:uppercase;margin-bottom:6px}
.enclair .box-t::before{content:"💡 "}
.exemple{
  background:linear-gradient(135deg,rgba(240,165,0,.12),rgba(18,52,52,.8));
  border:1px solid rgba(240,165,0,.5);border-radius:var(--radius);
  padding:14px 16px;margin:16px 0;
}
.exemple .box-t{color:var(--amber);font-weight:800;font-size:13px;letter-spacing:1px;text-transform:uppercase;margin-bottom:6px}
.exemple .box-t::before{content:"🔧 "}
.attention{
  background:rgba(255,107,91,.1);border:1px solid var(--warn);
  border-radius:var(--radius);padding:14px 16px;margin:16px 0;
}
.attention .box-t{color:var(--warn);font-weight:800;font-size:13px;letter-spacing:1px;text-transform:uppercase;margin-bottom:6px}
.attention .box-t::before{content:"⚠️ "}
.astuce{
  background:rgba(76,175,125,.1);border:1px solid var(--ok);
  border-radius:var(--radius);padding:14px 16px;margin:16px 0;
}
.astuce .box-t{color:var(--ok);font-weight:800;font-size:13px;letter-spacing:1px;text-transform:uppercase;margin-bottom:6px}
.astuce .box-t::before{content:"✅ "}
.enclair p,.exemple p,.attention p,.astuce p{margin-bottom:6px;font-size:14px}
.enclair p:last-child,.exemple p:last-child,.attention p:last-child,.astuce p:last-child{margin-bottom:0}
/* ===== CODE ===== */
pre{
  background:var(--code-bg);border:1px solid rgba(45,138,133,.4);
  border-radius:12px;padding:14px;margin:14px 0;
  overflow-x:auto;-webkit-overflow-scrolling:touch;
  font-size:13.5px;line-height:1.65;
}
code{font-family:'SF Mono',Menlo,Consolas,monospace;color:#eefaf6}
p code,li code,td code{
  background:var(--code-bg);padding:2px 7px;border-radius:6px;
  font-size:13px;color:var(--amber-l);border:1px solid rgba(45,138,133,.3);
}
.cm{color:#9ed4cc;font-style:italic}       /* commentaire */
.kw{color:#ff9d5c}       /* mot-clé */
.fn{color:#7de8db}       /* fonction */
.st{color:#c9ef92}       /* string */
.nb{color:#ffc93c}       /* nombre */
/* ===== TABLEAUX ===== */
.tbl-wrap{overflow-x:auto;-webkit-overflow-scrolling:touch;margin:14px 0}
table{width:100%;border-collapse:collapse;font-size:13.5px;min-width:420px}
th{background:var(--teal);color:var(--amber-l);padding:9px 10px;text-align:left;font-size:12.5px;letter-spacing:.5px}
td{padding:9px 10px;border-bottom:1px solid rgba(45,138,133,.25)}
tr:nth-child(even) td{background:rgba(255,255,255,.025)}
/* ===== SCHÉMAS ASCII / MONTAGES ===== */
.schema{
  background:var(--code-bg);border:1px dashed var(--teal-l);
  border-radius:12px;padding:14px;margin:14px 0;
  font-family:'SF Mono',Menlo,monospace;font-size:12px;line-height:1.5;
  overflow-x:auto;white-space:pre;color:#d8f0ea;
}
.schema .lbl{color:var(--amber)}
/* ===== QUIZ ===== */
.quiz{
  background:var(--card);border:1px solid var(--teal-l);
  border-radius:var(--radius);padding:16px;margin:20px 0;
}
.quiz .q-t{color:var(--amber);font-weight:800;font-size:13px;letter-spacing:1px;text-transform:uppercase;margin-bottom:8px}
.quiz .q-t::before{content:"❓ "}
.quiz .q-q{font-weight:600;margin-bottom:12px;font-size:15px}
.q-opt{
  display:block;width:100%;text-align:left;
  background:var(--bg2);border:1px solid rgba(45,138,133,.4);color:var(--txt);
  border-radius:10px;padding:11px 13px;margin-bottom:8px;
  font-size:14px;cursor:pointer;transition:all .15s;
}
.q-opt:active{transform:scale(.985)}
.q-opt.good{background:rgba(76,175,125,.25);border-color:var(--ok);color:#c9f5dd}
.q-opt.bad{background:rgba(255,107,91,.18);border-color:var(--warn);color:#ffd0c9}
.q-exp{display:none;margin-top:10px;font-size:13.5px;color:var(--txt2);border-top:1px dashed rgba(45,138,133,.4);padding-top:10px}
.q-exp.show{display:block}
/* ===== NAV BAS ===== */
.nav-bot{
  position:fixed;bottom:0;left:0;right:0;z-index:90;
  background:linear-gradient(0deg,var(--bg2) 60%,rgba(14,41,41,.9));
  backdrop-filter:blur(10px);
  border-top:1px solid rgba(240,165,0,.25);
  padding:10px 14px calc(10px + env(safe-area-inset-bottom));
  display:flex;gap:10px;align-items:center;justify-content:space-between;
}
.nav-btn{
  flex:1;background:var(--card2);border:1px solid var(--teal-l);color:var(--txt);
  border-radius:12px;padding:12px;font-size:14px;font-weight:700;cursor:pointer;
  transition:transform .12s;
}
.nav-btn:active{transform:scale(.97)}
.nav-btn.primary{background:linear-gradient(135deg,var(--amber),#d99400);color:#1a1200;border:none}
.nav-btn:disabled{opacity:.35}
.nav-pos{font-size:12px;color:var(--txt2);min-width:52px;text-align:center;font-weight:700}
/* ===== DIVERS ===== */
.pin-badge{
  display:inline-block;background:var(--teal);color:var(--amber-l);
  border-radius:6px;padding:1px 8px;font-size:12.5px;font-weight:700;
  font-family:Menlo,monospace;
}
.big-icon{font-size:38px;text-align:center;margin:10px 0}
.hero-card{
  background:linear-gradient(145deg,var(--card2),var(--card));
  border:1px solid var(--teal-l);border-radius:18px;
  padding:20px;margin:16px 0;text-align:center;
}
.hero-card .hc-big{font-size:34px;font-weight:900;color:var(--amber)}
.hero-card .hc-lbl{font-size:13px;color:var(--txt2)}
.recap{
  background:var(--card);border-left:4px solid var(--amber);
  border-radius:0 var(--radius) var(--radius) 0;
  padding:14px 16px;margin:24px 0 10px;
}
.recap .r-t{color:var(--amber);font-weight:800;font-size:13px;letter-spacing:1px;text-transform:uppercase;margin-bottom:8px}
.recap .r-t::before{content:"📌 "}
.recap li{font-size:14px}
/* ===== MODE ÉDITION ===== */
.edit-banner{
  display:none;position:sticky;top:64px;z-index:95;
  background:linear-gradient(135deg,#f0a500,#d98e00);color:#1a1200;
  padding:8px 12px;margin:0;
  font-size:12.5px;font-weight:700;
}
body.editing .edit-banner{display:block}
.edit-banner .eb-row{display:flex;gap:6px;flex-wrap:wrap;margin-top:6px}
.eb-btn{
  background:#1a1200;color:#ffc93c;border:none;border-radius:8px;
  padding:8px 10px;font-size:12px;font-weight:700;cursor:pointer;flex:1;min-width:70px;
}
.eb-btn:active{transform:scale(.96)}
body.editing .module.active{
  outline:2px dashed #f0a500;outline-offset:6px;border-radius:8px;
}
body.editing .module.active [contenteditable]{caret-color:#f0a500}
.edit-toast{
  position:fixed;bottom:90px;left:50%;transform:translateX(-50%);
  background:#123434;border:1px solid var(--ok);color:#c9f5dd;
  border-radius:12px;padding:10px 18px;font-size:13px;font-weight:600;
  z-index:300;opacity:0;transition:opacity .3s;pointer-events:none;max-width:88%;text-align:center;
}
.edit-toast.show{opacity:1}
/* ===== MODE ÉDITION ===== */
.edit-bar{
  display:none;position:fixed;top:74px;left:8px;right:8px;z-index:95;
  background:linear-gradient(135deg,#2a1f00,#1a1400);
  border:1px solid var(--amber);border-radius:12px;
  padding:8px 10px;gap:6px;align-items:center;flex-wrap:wrap;
  box-shadow:0 4px 18px rgba(0,0,0,.5);
}
.edit-bar .eb-lbl{color:var(--amber);font-size:11px;font-weight:800;letter-spacing:1px;margin-right:2px}
.edit-bar button{
  background:var(--card2);border:1px solid var(--amber);color:var(--amber-l);
  border-radius:8px;padding:7px 10px;font-size:12.5px;font-weight:700;cursor:pointer;
}
body.editing .module{outline:2px dashed rgba(240,165,0,.5);outline-offset:6px;border-radius:8px}
body.editing .module[contenteditable]:focus-within{outline-color:var(--amber)}
body.editing{padding-top:56px}
/* ===== FIGURES SVG ===== */
.fig{
  background:var(--card);border:1px solid rgba(45,138,133,.4);
  border-radius:var(--radius);padding:12px 10px 10px;margin:16px 0;text-align:center;
}
.fig svg{max-width:100%;height:auto;display:block;margin:0 auto}
.fig .fig-cap{font-size:12.5px;color:var(--txt2);margin-top:8px;font-style:italic}
@media(min-width:700px){body{font-size:17px}.module h2{font-size:28px}}
</style>
</head>
<body>

<!-- ============ HEADER ============ -->
<header class="hdr">
  <div class="hdr-top">
    <div>
      <h1 id="courseTitle">⚡ ARDUINO — LE COURS COMPLET</h1>
      <div class="sub">Formation débutant · Électronique &amp; programmation</div>
    </div>
    <button class="menu-btn" onclick="toggleMenu()">☰ Modules</button>
    <button class="menu-btn" id="editBtn" onclick="editGate()" title="Édition">✎</button>
  </div>
  <div class="progress-wrap"><div class="progress-bar" id="pbar"></div></div>
</header>

<!-- ============ BARRE ÉDITION (accès protégé) ============ -->
<div class="edit-bar" id="editBar">
  <span class="eb-lbl">✎ ÉDITION</span>
  <button onclick="editSave()">💾 Enregistrer</button>
  <button onclick="editExport()">⬇️ Exporter</button>
  <button onclick="editCode()">🔑 Code</button>
  <button onclick="editReset()">↩️ Réinit.</button>
  <button onclick="editQuit()">✕ Quitter</button>
</div>

<!-- ============ BANNIÈRE MODE ÉDITION ============ -->
<div class="edit-banner" id="editBanner">
  ✏️ MODE ÉDITION — touche le texte pour le modifier, puis Enregistrer.
  <div class="eb-row">
    <button class="eb-btn" onclick="saveEdits()">💾 Enregistrer</button>
    <button class="eb-btn" onclick="exportHTML()">📤 Exporter HTML</button>
    <button class="eb-btn" onclick="resetModule()">↩️ Rétablir module</button>
    <button class="eb-btn" onclick="exitEdit()">🔒 Quitter</button>
  </div>
</div>
<div class="edit-toast" id="editToast"></div>


<!-- ============ MENU ============ -->
<div class="menu" id="menu">
  <button class="menu-close" onclick="toggleMenu()">✕</button>
  <h2>📚 Sommaire du cours</h2>
  <p>12 modules · progresse à ton rythme, chaque module se termine par un quiz.</p>
  <div id="menuList"></div>
</div>

<!-- ============ MODULE 1 ============ -->
<section class="module" id="m1">
  <span class="mod-tag">Module 1 / 12</span>
  <h2>C'est quoi <span>Arduino</span>, et pourquoi ça te concerne ?</h2>
  <p class="mod-intro">Avant de toucher au moindre fil, on pose les bases : ce qu'est une carte Arduino, ce qu'elle sait faire, et pourquoi c'est l'outil idéal pour un technicien de maintenance qui veut passer au niveau supérieur.</p>

  <div class="big-icon">🧠 + 🔌 = 🤖</div>

  <h3>1.1 — La définition simple</h3>
  <p>Arduino, c'est un <strong>mini-ordinateur programmable</strong> de la taille d'une carte bancaire. Il ne fait pas tourner Windows ni des vidéos YouTube. Il fait une seule chose, mais il la fait très bien : <strong>lire des capteurs, prendre des décisions, et commander des actionneurs</strong>.</p>
  <p>Le cœur de la carte, c'est un <strong>microcontrôleur</strong> : une puce qui contient un processeur, de la mémoire et des entrées/sorties, le tout dans un seul composant. Tu écris un programme sur ton ordinateur (ou ton téléphone), tu l'envoies dans la puce, et la carte l'exécute en boucle, toute seule, dès qu'elle est alimentée.</p>

  <div class="enclair">
    <div class="box-t">En clair</div>
    <p>Un Arduino, c'est comme un <strong>petit automate programmable (API/PLC) de poche</strong>. Sur nos machines, l'ECU lit les capteurs de pression et commande les électrovannes. L'Arduino fait exactement le même travail, à petite échelle, et c'est TOI qui écris sa logique.</p>
  </div>

  <h3>1.2 — Le trio magique : Entrée → Traitement → Sortie</h3>
  <p>Tout ce qu'on fera dans ce cours repose sur ce schéma. Grave-le dans ta tête :</p>
  <div class="schema"><span class="lbl">  ENTRÉES              TRAITEMENT             SORTIES</span>
 ┌──────────┐        ┌─────────────┐        ┌──────────┐
 │ Capteurs │──────► │   ARDUINO   │──────► │ Actionneurs
 │ Boutons  │        │ (ton code)  │        │ LED, relais
 │ Sondes   │        │             │        │ moteurs, buzzer
 └──────────┘        └─────────────┘        └──────────┘
   "je mesure"        "je décide"            "j'agis"</div>
  <ul>
    <li><strong>Entrées :</strong> température, pression, bouton poussoir, niveau, vibration…</li>
    <li><strong>Traitement :</strong> ton programme compare, calcule, décide. « Si la température dépasse 80 °C… »</li>
    <li><strong>Sorties :</strong> « …alors j'allume l'alarme et je coupe le relais. »</li>
  </ul>

  <div class="exemple">
    <div class="box-t">Exemple concret — terrain</div>
    <p>Sur une foreuse, le calculateur lit le capteur de température du compresseur (<strong>entrée</strong>), compare à un seuil (<strong>traitement</strong>), et déclenche le voyant + la réduction de régime (<strong>sortie</strong>). Avec un Arduino à 15 000 FCFA, tu peux reproduire cette logique pour surveiller n'importe quel équipement de l'atelier : un groupe électrogène, une pompe, un compresseur d'atelier.</p>
  </div>


  <div class="fig"><svg viewBox="0 0 360 170" xmlns="http://www.w3.org/2000/svg" font-family="sans-serif">
    <text x="90" y="16" fill="#4caf7d" font-size="12" font-weight="800" text-anchor="middle">CAPTEURS (entrées)</text>
    <text x="268" y="16" fill="#f0a500" font-size="12" font-weight="800" text-anchor="middle">ACTIONNEURS (sorties)</text>
    <line x1="180" y1="10" x2="180" y2="160" stroke="#2d8a85" stroke-dasharray="4 4"/>
    <!-- sonde temp -->
    <rect x="30" y="38" width="44" height="16" rx="8" fill="#b9c7c5"/>
    <rect x="74" y="42" width="26" height="8" rx="4" fill="#8a9a98"/>
    <path d="M30 46 C 14 46 12 60 18 66" stroke="#333" stroke-width="3" fill="none"/>
    <text x="60" y="72" fill="#e8f0ef" font-size="10" text-anchor="middle">sonde température</text>
    <!-- bouton -->
    <rect x="38" y="92" width="40" height="40" rx="6" fill="#0a1c1c" stroke="#2d8a85"/>
    <circle cx="58" cy="112" r="12" fill="#ff5b4d"/>
    <circle cx="58" cy="112" r="12" fill="none" stroke="#7a2018"/>
    <text x="58" y="148" fill="#e8f0ef" font-size="10" text-anchor="middle">bouton poussoir</text>
    <!-- pressostat -->
    <circle cx="130" cy="52" r="16" fill="#8a9a98"/>
    <rect x="124" y="66" width="12" height="14" fill="#6a7a78"/>
    <text x="130" y="96" fill="#e8f0ef" font-size="10" text-anchor="middle">pressostat</text>
    <!-- LED -->
    <circle cx="212" cy="46" r="11" fill="#ff5b4d"/>
    <path d="M212 35 a11 11 0 0 1 0 22" fill="#ffd0c9" opacity=".35"/>
    <line x1="208" y1="57" x2="208" y2="74" stroke="#b9c7c5" stroke-width="2"/>
    <line x1="216" y1="57" x2="216" y2="70" stroke="#b9c7c5" stroke-width="2"/>
    <text x="212" y="88" fill="#e8f0ef" font-size="10" text-anchor="middle">LED</text>
    <!-- buzzer -->
    <circle cx="272" cy="50" r="16" fill="#0a1c1c" stroke="#2d8a85"/>
    <circle cx="272" cy="50" r="4" fill="#177a72"/>
    <text x="272" y="88" fill="#e8f0ef" font-size="10" text-anchor="middle">buzzer</text>
    <!-- moteur -->
    <circle cx="330" cy="50" r="16" fill="#8a9a98"/>
    <rect x="326" y="30" width="8" height="8" fill="#6a7a78"/>
    <text x="330" y="55" fill="#0a1c1c" font-size="13" font-weight="800" text-anchor="middle">M</text>
    <text x="330" y="88" fill="#e8f0ef" font-size="10" text-anchor="middle">moteur</text>
    <!-- relais -->
    <rect x="238" y="102" width="52" height="34" rx="4" fill="#3d8bfd"/>
    <text x="264" y="123" fill="#fff" font-size="9" font-weight="700" text-anchor="middle">RELAIS</text>
    <text x="264" y="152" fill="#e8f0ef" font-size="10" text-anchor="middle">relais de puissance</text>
    <!-- électrovanne -->
    <rect x="310" y="104" width="18" height="26" rx="3" fill="#177a72" stroke="#2d8a85"/>
    <rect x="304" y="126" width="30" height="10" rx="2" fill="#8a9a98"/>
    <text x="322" y="152" fill="#e8f0ef" font-size="10" text-anchor="middle">électrovanne</text>
  </svg><div class="fig-cap">Fig. 1 — À gauche, ce que l'Arduino lit. À droite, ce qu'il commande.</div></div>
  <h3>1.3 — Pourquoi Arduino et pas autre chose ?</h3>
  <ul>
    <li><strong>C'est pas cher :</strong> une carte UNO officielle coûte ~25 €, les clones ~5 €.</li>
    <li><strong>C'est robuste :</strong> difficile à griller si tu respectes quelques règles (on les verra).</li>
    <li><strong>C'est documenté :</strong> des millions d'utilisateurs, des milliers de tutos et de bibliothèques prêtes à l'emploi.</li>
    <li><strong>C'est une porte d'entrée :</strong> les compétences Arduino (GPIO, PWM, I2C, SPI, CAN…) sont exactement celles utilisées dans les calculateurs de nos machines.</li>
  </ul>

  <h3>1.4 — La famille Arduino en 2026</h3>
  <div class="tbl-wrap"><table>
    <tr><th>Carte</th><th>Pour quoi faire ?</th><th>Niveau</th></tr>
    <tr><td><strong>UNO R3</strong></td><td>Apprendre. LA carte de référence, celle de ce cours.</td><td>Débutant</td></tr>
    <tr><td><strong>Nano</strong></td><td>Même puce que la UNO, format mini. Projets compacts.</td><td>Débutant</td></tr>
    <tr><td><strong>Mega 2560</strong></td><td>Beaucoup d'entrées/sorties (54 pins). Gros projets.</td><td>Intermédiaire</td></tr>
    <tr><td><strong>UNO R4 WiFi</strong></td><td>UNO modernisée : 32 bits, WiFi, CAN bus intégré.</td><td>Intermédiaire</td></tr>
    <tr><td><strong>UNO Q</strong></td><td>Carte hybride : un microcontrôleur temps réel + un processeur Linux avec WiFi, pour l'IA embarquée.</td><td>Avancé</td></tr>
    <tr><td><strong>ESP32</strong> (hors Arduino)</td><td>Compatible IDE Arduino, WiFi/Bluetooth, très puissant, très utilisé en IoT industriel.</td><td>Intermédiaire</td></tr>
  </table></div>

  <div class="astuce">
    <div class="box-t">Mon conseil</div>
    <p>Commence avec une <strong>UNO R3</strong> (ou un clone) + un kit de démarrage avec breadboard, LED, résistances, boutons et quelques capteurs. Tout ce cours est basé dessus. L'ESP32 et la UNO Q viendront plus tard, quand les bases seront solides.</p>
  </div>

  <h3>1.5 — Ce que tu sauras faire à la fin de ce cours</h3>
  <ol>
    <li>Câbler un montage propre sur breadboard sans rien griller.</li>
    <li>Écrire, comprendre et corriger un programme Arduino.</li>
    <li>Lire des capteurs (numériques et analogiques) et afficher les mesures.</li>
    <li>Commander LED, buzzer, relais et petits moteurs.</li>
    <li>Construire un vrai projet de surveillance type « mini-PdM » pour l'atelier.</li>
  </ol>

  <div class="recap">
    <div class="r-t">À retenir</div>
    <ul>
      <li>Arduino = microcontrôleur programmable : il lit, il décide, il agit.</li>
      <li>Le schéma universel : <strong>Entrée → Traitement → Sortie</strong>.</li>
      <li>C'est le même principe que les calculateurs de nos machines, en version apprentissage.</li>
      <li>Carte de départ recommandée : <strong>UNO R3</strong>.</li>
    </ul>
  </div>

  <div class="quiz">
    <div class="q-t">Quiz Module 1</div>
    <div class="q-q">Un capteur de température branché sur l'Arduino, c'est quoi dans le schéma Entrée → Traitement → Sortie ?</div>
    <button class="q-opt" onclick="qz(this,false)">Une sortie</button>
    <button class="q-opt" onclick="qz(this,true)">Une entrée</button>
    <button class="q-opt" onclick="qz(this,false)">Le traitement</button>
    <div class="q-exp">✅ Le capteur <strong>fournit une information</strong> à l'Arduino : c'est une entrée. Le traitement, c'est ton code. La sortie, c'est ce que l'Arduino commande (LED, relais…).</div>
  </div>
</section>

<!-- ============ MODULE 2 ============ -->
<section class="module" id="m2">
  <span class="mod-tag">Module 2 / 12</span>
  <h2>L'électricité <span>de base</span> — juste ce qu'il faut</h2>
  <p class="mod-intro">Pas besoin d'un diplôme d'ingénieur. Mais sans ces 4 notions — tension, courant, résistance, loi d'Ohm — tu vas griller des composants. On fait simple et on relie tout au terrain.</p>

  <h3>2.1 — Tension, courant, résistance : l'analogie de l'eau</h3>
  <p>Imagine un circuit hydraulique (ça, tu connais 😄) :</p>
  <div class="tbl-wrap"><table>
    <tr><th>Électricité</th><th>Hydraulique</th><th>Unité</th></tr>
    <tr><td><strong>Tension (U)</strong></td><td>La pression dans le circuit</td><td>Volt (V)</td></tr>
    <tr><td><strong>Courant (I)</strong></td><td>Le débit qui circule</td><td>Ampère (A)</td></tr>
    <tr><td><strong>Résistance (R)</strong></td><td>Un étranglement / une restriction</td><td>Ohm (Ω)</td></tr>
  </table></div>
  <div class="enclair">
    <div class="box-t">En clair</div>
    <p>Plus la <strong>pression</strong> (tension) est forte, plus le <strong>débit</strong> (courant) est important. Plus la <strong>restriction</strong> (résistance) est serrée, plus le débit diminue. C'est exactement comme un limiteur de débit sur un circuit hydraulique de foreuse.</p>
  </div>

  <h3>2.2 — La loi d'Ohm : LA formule à connaître</h3>
  <div class="hero-card">
    <div class="hc-big">U = R × I</div>
    <div class="hc-lbl">Tension (V) = Résistance (Ω) × Courant (A)</div>
  </div>
  <p>De cette formule, tu déduis les deux autres :</p>
  <ul>
    <li><code>I = U / R</code> → pour calculer le courant qui va circuler</li>
    <li><code>R = U / I</code> → pour calculer la résistance qu'il te faut</li>
  </ul>

  <div class="exemple">
    <div class="box-t">Exemple concret — calcul réel</div>
    <p>Tu veux brancher une LED sur une sortie Arduino (5 V). La LED consomme environ 2 V et supporte 20 mA maximum. Quelle résistance mettre en série ?</p>
    <p>Tension à « absorber » par la résistance : 5 V − 2 V = <strong>3 V</strong>.<br>
    R = U / I = 3 / 0,020 = <strong>150 Ω</strong>.<br>
    On prend la valeur standard juste au-dessus : <strong>220 Ω</strong>. Marge de sécurité, LED protégée. C'est LE calcul que tu referas 100 fois.</p>
  </div>

  <h3>2.3 — Les limites de l'Arduino UNO (à respecter !)</h3>
  <div class="tbl-wrap"><table>
    <tr><th>Paramètre</th><th>Valeur</th><th>Conséquence si dépassé</th></tr>
    <tr><td>Tension logique des pins</td><td><strong>5 V</strong></td><td>Au-delà → pin grillée</td></tr>
    <tr><td>Courant max par pin</td><td><strong>20 mA</strong> (40 mA absolu)</td><td>Pin ou puce détruite</td></tr>
    <tr><td>Courant total toutes pins</td><td>~200 mA</td><td>Puce en surchauffe</td></tr>
    <tr><td>Alimentation VIN</td><td>7 à 12 V recommandé</td><td>Régulateur en surchauffe au-delà</td></tr>
  </table></div>

  <div class="attention">
    <div class="box-t">Règle d'or</div>
    <p><strong>Une pin Arduino ne pilote JAMAIS directement une charge de puissance.</strong> Un moteur, une pompe, un gyrophare 24 V ? Tu passes par un relais ou un transistor. La pin envoie le signal de commande, le relais fait le travail de puissance. Exactement comme une électrovanne pilote reçoit 24 V de l'ECU mais c'est le tiroir hydraulique qui envoie la puissance.</p>
  </div>

  <h3>2.4 — Série et parallèle en 30 secondes</h3>
  <div class="schema"><span class="lbl">SÉRIE</span> (le courant traverse tout, un seul chemin)
  ──[R1]──[R2]──   →  R total = R1 + R2

<span class="lbl">PARALLÈLE</span> (le courant se partage, plusieurs chemins)
  ──┬─[R1]─┬──
    └─[R2]─┘    →  R total diminue (plus petit que la plus petite)</div>
  <p>Pour ce cours, retiens surtout : <strong>la résistance de protection d'une LED se met en série avec la LED</strong>. Peu importe avant ou après, le courant est le même dans toute la branche.</p>

  <h3>2.5 — Lire une résistance (code couleur)</h3>
  <div class="tbl-wrap"><table>
    <tr><th>Couleur</th><th>Chiffre</th><th>Multiplicateur</th></tr>
    <tr><td>Noir</td><td>0</td><td>×1</td></tr>
    <tr><td>Marron</td><td>1</td><td>×10</td></tr>
    <tr><td>Rouge</td><td>2</td><td>×100</td></tr>
    <tr><td>Orange</td><td>3</td><td>×1 000</td></tr>
    <tr><td>Jaune</td><td>4</td><td>×10 000</td></tr>
    <tr><td>Vert</td><td>5</td><td>×100 000</td></tr>
    <tr><td>Bleu</td><td>6</td><td>×1 000 000</td></tr>
    <tr><td>Violet</td><td>7</td><td>—</td></tr>
    <tr><td>Gris</td><td>8</td><td>—</td></tr>
    <tr><td>Blanc</td><td>9</td><td>—</td></tr>
  </table></div>
  <p>Exemple : <strong>Rouge-Rouge-Marron</strong> = 2, 2, ×10 = <strong>220 Ω</strong>. La 4ᵉ bague (or/argent) c'est la tolérance.</p>
  <div class="astuce">
    <div class="box-t">Astuce d'atelier</div>
    <p>Dans le doute, sors le multimètre en position Ω et mesure. C'est plus rapide que de déchiffrer les couleurs sous un mauvais éclairage — et ça te fait pratiquer le multimètre.</p>
  </div>

  <div class="recap">
    <div class="r-t">À retenir</div>
    <ul>
      <li>Tension = pression, courant = débit, résistance = restriction.</li>
      <li><strong>U = R × I</strong> — tu dois savoir jongler avec.</li>
      <li>LED sur pin 5 V → résistance <strong>220 Ω</strong> en série, toujours.</li>
      <li>Max <strong>20 mA par pin</strong>. La puissance passe par relais/transistor.</li>
    </ul>
  </div>

  <div class="quiz">
    <div class="q-t">Quiz Module 2</div>
    <div class="q-q">Tu veux alimenter un composant qui consomme 25 mA sous une pin Arduino. C'est bon ?</div>
    <button class="q-opt" onclick="qz(this,false)">Oui, aucun problème</button>
    <button class="q-opt" onclick="qz(this,true)">Non, on dépasse les 20 mA recommandés par pin</button>
    <button class="q-opt" onclick="qz(this,false)">Oui, si le fil est assez gros</button>
    <div class="q-exp">✅ 25 mA &gt; 20 mA recommandés. Ça peut « marcher » un temps, mais tu fatigues la puce. Solution propre : transistor ou relais pour piloter la charge.</div>
  </div>
</section>
<!-- ============ MODULE 3 ============ -->
<section class="module" id="m3">
  <span class="mod-tag">Module 3 / 12</span>
  <h2>Anatomie de la carte <span>UNO</span></h2>
  <p class="mod-intro">Tour du propriétaire. Chaque zone de la carte a un rôle précis. Quand tu sauras la lire comme un schéma hydraulique, la moitié du travail est faite.</p>

  <h3>3.1 — Vue d'ensemble</h3>
  <div class="fig"><svg viewBox="0 0 380 250" xmlns="http://www.w3.org/2000/svg" font-family="sans-serif">
    <!-- PCB -->
    <rect x="40" y="30" width="300" height="190" rx="10" fill="#177a72" stroke="#0e544e" stroke-width="3"/>
    <!-- USB -->
    <rect x="20" y="48" width="52" height="38" rx="4" fill="#b9c7c5" stroke="#7a8a88"/>
    <text x="46" y="70" fill="#333" font-size="10" font-weight="800" text-anchor="middle">USB</text>
    <!-- Jack -->
    <rect x="24" y="160" width="46" height="34" rx="4" fill="#0a1c1c"/>
    <circle cx="30" cy="177" r="7" fill="#000" stroke="#333"/>
    <text x="52" y="181" fill="#a8c5c2" font-size="8.5" text-anchor="middle">7-12V</text>
    <!-- Header numérique -->
    <rect x="110" y="36" width="216" height="18" rx="3" fill="#0a1c1c"/>
    <text x="218" y="49" fill="#ffc93c" font-size="9.5" font-weight="700" text-anchor="middle" letter-spacing="1">D13 D12 ~D11 ~D10 ~D9 D8 | D7 ~D6 ~D5 D4 ~D3 D2 D1 D0</text>
    <!-- ATmega -->
    <rect x="140" y="105" width="150" height="34" rx="4" fill="#0a1c1c"/>
    <text x="215" y="126" fill="#e8f0ef" font-size="11" font-weight="700" text-anchor="middle">ATmega328P</text>
    <!-- LED L -->
    <rect x="96" y="70" width="14" height="9" rx="2" fill="#ffc93c"/>
    <text x="103" y="93" fill="#e8f0ef" font-size="9" text-anchor="middle">LED «L»</text>
    <!-- Reset -->
    <rect x="300" y="66" width="26" height="20" rx="4" fill="#8a9a98"/>
    <circle cx="313" cy="76" r="6" fill="#ff5b4d"/>
    <text x="313" y="100" fill="#e8f0ef" font-size="8.5" text-anchor="middle">RESET</text>
    <!-- Header alim -->
    <rect x="96" y="196" width="118" height="18" rx="3" fill="#0a1c1c"/>
    <text x="155" y="209" fill="#ff9d5c" font-size="9.5" font-weight="700" text-anchor="middle">5V 3.3V GND GND VIN</text>
    <!-- Header analogique -->
    <rect x="226" y="196" width="100" height="18" rx="3" fill="#0a1c1c"/>
    <text x="276" y="209" fill="#6fd3c7" font-size="9.5" font-weight="700" text-anchor="middle">A0 A1 A2 A3 A4 A5</text>
    <!-- Légendes externes -->
    <text x="218" y="20" fill="#f0a500" font-size="11" font-weight="800" text-anchor="middle">PINS NUMÉRIQUES (~ = PWM)</text>
    <text x="155" y="238" fill="#f0a500" font-size="10.5" font-weight="800" text-anchor="middle">ALIMENTATION</text>
    <text x="276" y="238" fill="#f0a500" font-size="10.5" font-weight="800" text-anchor="middle">ANALOGIQUE</text>
  </svg><div class="fig-cap">Fig. 2 — La carte Arduino UNO et ses zones clés.</div></div>

  <div class="schema"><span class="lbl">        CARTE ARDUINO UNO — vue de dessus</span>
 ┌────────────────────────────────────────────┐
 │ [USB]                    PINS NUMÉRIQUES    │
 │  port de       ┌──── D13 D12 ~D11 ~D10 ~D9 │
 │  programmation │      D8 D7 ~D6 ~D5 D4 ~D3 │
 │                │      D2 D1(TX) D0(RX)     │
 │ [JACK 7-12V]   │                           │
 │  alimentation  │   ┌─────────────┐         │
 │  externe       │   │ ATmega328P  │ ← le    │
 │                │   │ (le cerveau)│   cerveau
 │  ALIMENTATION  │   └─────────────┘         │
 │  5V 3.3V GND × 2   ENTRÉES ANALOGIQUES     │
 │  VIN               A0 A1 A2 A3 A4 A5       │
 └────────────────────────────────────────────┘
   ~ devant un numéro = pin capable de PWM</div>

  <h3>3.2 — Les zones importantes</h3>
  <h4>🔌 Le port USB</h4>
  <p>Il sert à trois choses : <strong>programmer</strong> la carte, l'<strong>alimenter</strong> (5 V depuis le PC ou un chargeur), et <strong>communiquer</strong> avec elle (moniteur série, module 9). Pendant tout l'apprentissage, l'USB suffit.</p>

  <h4>⚡ L'alimentation</h4>
  <ul>
    <li><span class="pin-badge">USB</span> : 5 V, parfait pour apprendre.</li>
    <li><span class="pin-badge">Jack DC</span> : 7 à 12 V (batterie, adaptateur). Un régulateur interne fabrique le 5 V.</li>
    <li><span class="pin-badge">VIN</span> : même chose que le jack, mais par pin.</li>
    <li><span class="pin-badge">5V</span> et <span class="pin-badge">3.3V</span> : des <strong>sorties</strong> pour alimenter tes capteurs.</li>
    <li><span class="pin-badge">GND</span> : la masse, le 0 V. <strong>Tout circuit doit être relié au GND.</strong></li>
  </ul>
  <div class="attention">
    <div class="box-t">Attention</div>
    <p>Ne branche <strong>jamais</strong> du 12 V ou du 24 V directement sur une pin ou sur la sortie 5V. Le 7-12 V, c'est uniquement sur le jack ou VIN. Sur une machine, tu ne branches pas la ligne 24 V batterie sur une entrée capteur de l'ECU — même logique ici.</p>
  </div>

  <h4>🟠 Les pins numériques D0 à D13</h4>
  <p>Chaque pin peut être configurée en <strong>entrée</strong> (lire un bouton, un capteur tout-ou-rien) ou en <strong>sortie</strong> (allumer une LED, commander un relais). Elles ne connaissent que deux états : <strong>HIGH (5 V)</strong> ou <strong>LOW (0 V)</strong>. Comme un contact : ouvert ou fermé.</p>
  <ul>
    <li>Les pins marquées <strong>~</strong> (3, 5, 6, 9, 10, 11) savent aussi faire du <strong>PWM</strong> (module 8).</li>
    <li><span class="pin-badge">D0</span> et <span class="pin-badge">D1</span> servent à la liaison série avec le PC : <strong>évite de les utiliser</strong> pour tes montages.</li>
    <li><span class="pin-badge">D13</span> est reliée à une LED intégrée sur la carte — pratique pour tester sans rien câbler.</li>
  </ul>

  <h4>🔵 Les entrées analogiques A0 à A5</h4>
  <p>Elles mesurent une <strong>tension variable</strong> entre 0 et 5 V et la convertissent en nombre de 0 à 1023. C'est là qu'on branche potentiomètres, sondes de température analogiques, capteurs de pression 0-5 V… On détaille tout au module 8.</p>

  <div class="enclair">
    <div class="box-t">En clair</div>
    <p>Pins numériques = <strong>capteurs tout-ou-rien</strong> (fin de course, pressostat, contact de porte). Entrées analogiques = <strong>capteurs proportionnels</strong> (sonde de température, transducteur de pression 0-5 V, jauge de niveau). Exactement la distinction qu'on fait sur les entrées d'un calculateur machine.</p>
  </div>

  <h3>3.3 — Le cerveau : l'ATmega328P</h3>
  <div class="tbl-wrap"><table>
    <tr><th>Caractéristique</th><th>Valeur</th><th>Commentaire</th></tr>
    <tr><td>Processeur</td><td>8 bits, 16 MHz</td><td>Lent pour un PC, largement suffisant ici</td></tr>
    <tr><td>Mémoire Flash</td><td>32 Ko</td><td>C'est là que vit ton programme</td></tr>
    <tr><td>SRAM</td><td>2 Ko</td><td>Les variables pendant l'exécution</td></tr>
    <tr><td>EEPROM</td><td>1 Ko</td><td>Mémoire qui survit à la coupure de courant</td></tr>
  </table></div>
  <p>32 Ko ça paraît minuscule, mais un programme de surveillance complet avec affichage tient dans 10 Ko. Les calculateurs des premières machines à injection électronique n'avaient pas beaucoup plus.</p>

  <h3>3.4 — La breadboard (plaque d'essai)</h3>
  <p>C'est ta table de montage sans soudure. Comprendre ses connexions internes est <strong>obligatoire</strong> :</p>
  <div class="schema"><span class="lbl">   BREADBOARD — connexions internes</span>
  + ───────────────────────  ← rail + (relié sur toute la ligne)
  − ───────────────────────  ← rail − (idem)

     a b c d e   f g h i j
  1  ●─●─●─●─●   ●─●─●─●─●   ← chaque rangée de 5 trous
  2  ●─●─●─●─●   ●─●─●─●─●     est reliée ensemble
  3  ●─●─●─●─●   ●─●─●─●─●
         ↑ fossé central : les deux côtés
           ne sont PAS reliés entre eux</div>
  <ul>
    <li>Les <strong>rails latéraux + et −</strong> : distribue le 5V et le GND de l'Arduino dessus.</li>
    <li>Chaque <strong>rangée de 5 trous</strong> est reliée en interne : deux composants sur la même rangée sont connectés.</li>
    <li>Le <strong>fossé central</strong> isole les deux moitiés — c'est fait pour enjamber les circuits intégrés.</li>
  </ul>
  <div class="astuce">
    <div class="box-t">Bonnes pratiques de câblage</div>
    <p>Fils <strong>rouges</strong> pour le +5V, <strong>noirs</strong> pour le GND, autres couleurs pour les signaux. Câble toujours <strong>hors tension</strong> (USB débranché), vérifie, puis branche. C'est la consignation version électronique.</p>
  </div>

  <div class="recap">
    <div class="r-t">À retenir</div>
    <ul>
      <li>D0-D13 = numérique (HIGH/LOW), A0-A5 = analogique (0-1023).</li>
      <li>Le ~ signale les pins PWM ; D13 a une LED intégrée ; D0/D1 réservées à la liaison série.</li>
      <li>5V/3.3V sont des sorties pour capteurs ; VIN/jack acceptent 7-12 V.</li>
      <li>Breadboard : rangées de 5 reliées, rails + / − sur les côtés.</li>
    </ul>
  </div>

  <div class="quiz">
    <div class="q-t">Quiz Module 3</div>
    <div class="q-q">Tu veux lire un capteur de pression qui sort une tension proportionnelle 0-5 V. Tu le branches où ?</div>
    <button class="q-opt" onclick="qz(this,false)">Sur D7</button>
    <button class="q-opt" onclick="qz(this,true)">Sur A0 (entrée analogique)</button>
    <button class="q-opt" onclick="qz(this,false)">Sur la pin 5V</button>
    <div class="q-exp">✅ Signal proportionnel = entrée <strong>analogique</strong> (A0-A5). Une pin numérique ne verrait que HIGH ou LOW. La pin 5V est une alimentation, jamais une entrée de mesure.</div>
  </div>
</section>

<!-- ============ MODULE 4 ============ -->
<section class="module" id="m4">
  <span class="mod-tag">Module 4 / 12</span>
  <h2>Premier programme : <span>Blink</span></h2>
  <p class="mod-intro">Le rite de passage de tout électronicien : faire clignoter une LED. Simple en apparence, mais tu vas y apprendre TOUTE la structure d'un programme Arduino.</p>

  <h3>4.1 — Installer l'environnement</h3>
  <ol>
    <li>Télécharge l'<strong>IDE Arduino</strong> (gratuit) sur <code>arduino.cc</code> → rubrique Software. Windows, Mac ou Linux.</li>
    <li>Branche la carte en USB. Le PC installe le pilote tout seul (ou presque).</li>
    <li>Dans l'IDE : menu <strong>Outils → Carte → Arduino UNO</strong>, puis <strong>Outils → Port</strong> → choisis le port COM où la carte apparaît.</li>
  </ol>
  <div class="astuce">
    <div class="box-t">Alternative sans PC</div>
    <p>Pas d'ordinateur sous la main ? L'éditeur en ligne <strong>Arduino Cloud Editor</strong> fonctionne depuis un navigateur. Et pour t'exercer au code sans matériel, le simulateur <strong>Wokwi</strong> (wokwi.com) tourne même sur iPhone : tu câbles et programmes un Arduino virtuel. Excellent pour réviser ce cours n'importe où.</p>
  </div>

  <h3>4.2 — La structure d'un programme Arduino</h3>
  <p>Tout programme (on dit un <strong>sketch</strong>) contient obligatoirement deux fonctions :</p>
  <pre><code><span class="kw">void</span> <span class="fn">setup</span>() {
  <span class="cm">// Exécuté UNE SEULE FOIS au démarrage</span>
  <span class="cm">// → configuration des pins, initialisations</span>
}

<span class="kw">void</span> <span class="fn">loop</span>() {
  <span class="cm">// Exécuté EN BOUCLE, sans fin,</span>
  <span class="cm">// tant que la carte est alimentée</span>
}</code></pre>
  <div class="enclair">
    <div class="box-t">En clair</div>
    <p><code>setup()</code> = la <strong>mise en service</strong> : ce que tu fais une fois au démarrage machine (initialisation, autotests). <code>loop()</code> = le <strong>cycle automate</strong> : le calculateur relit ses entrées et met à jour ses sorties en permanence, des milliers de fois par seconde. Un ECU de foreuse fonctionne exactement comme ça.</p>
  </div>

  <h3>4.3 — Le code Blink, ligne par ligne</h3>
  <pre><code><span class="cm">// BLINK — fait clignoter la LED intégrée (pin 13)</span>

<span class="kw">void</span> <span class="fn">setup</span>() {
  <span class="fn">pinMode</span>(<span class="nb">13</span>, <span class="kw">OUTPUT</span>);      <span class="cm">// pin 13 déclarée en SORTIE</span>
}

<span class="kw">void</span> <span class="fn">loop</span>() {
  <span class="fn">digitalWrite</span>(<span class="nb">13</span>, <span class="kw">HIGH</span>); <span class="cm">// 5 V sur la pin → LED allumée</span>
  <span class="fn">delay</span>(<span class="nb">1000</span>);            <span class="cm">// attendre 1000 ms = 1 seconde</span>
  <span class="fn">digitalWrite</span>(<span class="nb">13</span>, <span class="kw">LOW</span>);  <span class="cm">// 0 V sur la pin → LED éteinte</span>
  <span class="fn">delay</span>(<span class="nb">1000</span>);            <span class="cm">// attendre encore 1 seconde</span>
}</code></pre>
  <p>Trois fonctions nouvelles, que tu utiliseras dans tous tes projets :</p>
  <div class="tbl-wrap"><table>
    <tr><th>Fonction</th><th>Rôle</th></tr>
    <tr><td><code>pinMode(pin, mode)</code></td><td>Déclare la pin en <code>OUTPUT</code>, <code>INPUT</code> ou <code>INPUT_PULLUP</code></td></tr>
    <tr><td><code>digitalWrite(pin, état)</code></td><td>Met la sortie à <code>HIGH</code> (5 V) ou <code>LOW</code> (0 V)</td></tr>
    <tr><td><code>delay(ms)</code></td><td>Met le programme en pause (millisecondes)</td></tr>
  </table></div>

  <h3>4.4 — Téléverser et vérifier</h3>
  <ol>
    <li>Clique sur <strong>✓ Vérifier</strong> : l'IDE compile ton code et signale les erreurs.</li>
    <li>Clique sur <strong>→ Téléverser</strong> : le programme est envoyé dans la carte. Les LED TX/RX clignotent pendant le transfert.</li>
    <li>La LED « L » de la carte doit clignoter au rythme d'une seconde. 🎉</li>
  </ol>
  <div class="attention">
    <div class="box-t">Les erreurs classiques du débutant</div>
    <p><strong>« expected ';' »</strong> → tu as oublié un point-virgule en fin de ligne.<br>
    <strong>Port grisé</strong> → câble USB de charge seulement (sans fils data) : change de câble.<br>
    <strong>Majuscules :</strong> le langage distingue <code>digitalWrite</code> de <code>DigitalWrite</code>. Respecte la casse au caractère près.</p>
  </div>

  <h3>4.5 — Exerce-toi : modifie Blink</h3>
  <ol>
    <li>Fais clignoter <strong>2× plus vite</strong> (indice : les delay).</li>
    <li>Fais un motif <strong>« flash court, pause longue »</strong> : 100 ms allumé, 900 ms éteint — comme un gyrophare de balisage.</li>
    <li>Branche une vraie LED externe : pin <span class="pin-badge">D8</span> → résistance 220 Ω → LED (patte longue côté résistance) → GND. Adapte le code (13 → 8).</li>
  </ol>
  <div class="fig"><svg viewBox="0 0 380 130" xmlns="http://www.w3.org/2000/svg" font-family="sans-serif">
    <!-- bord de carte -->
    <rect x="10" y="20" width="60" height="90" rx="8" fill="#177a72" stroke="#0e544e" stroke-width="2"/>
    <text x="40" y="45" fill="#e8f0ef" font-size="9" font-weight="700" text-anchor="middle">UNO</text>
    <rect x="62" y="52" width="14" height="10" fill="#0a1c1c"/>
    <text x="52" y="60" fill="#ffc93c" font-size="9" font-weight="800" text-anchor="end">D8</text>
    <rect x="62" y="86" width="14" height="10" fill="#0a1c1c"/>
    <text x="52" y="94" fill="#ff9d5c" font-size="9" font-weight="800" text-anchor="end">GND</text>
    <!-- fil D8 -> résistance -->
    <line x1="76" y1="57" x2="130" y2="57" stroke="#f0a500" stroke-width="3"/>
    <!-- résistance -->
    <rect x="130" y="48" width="70" height="18" rx="8" fill="#d8c49a" stroke="#a08b5f"/>
    <rect x="142" y="48" width="7" height="18" fill="#c0392b"/>
    <rect x="156" y="48" width="7" height="18" fill="#c0392b"/>
    <rect x="170" y="48" width="7" height="18" fill="#6b3f1f"/>
    <rect x="186" y="48" width="6" height="18" fill="#d4af37"/>
    <text x="165" y="84" fill="#e8f0ef" font-size="10" text-anchor="middle">220 Ω</text>
    <!-- fil résistance -> LED -->
    <line x1="200" y1="57" x2="252" y2="57" stroke="#f0a500" stroke-width="3"/>
    <!-- LED -->
    <circle cx="270" cy="52" r="16" fill="#ff5b4d"/>
    <path d="M270 36 a16 16 0 0 1 0 32" fill="#ffd0c9" opacity=".35"/>
    <line x1="264" y1="68" x2="264" y2="91" stroke="#b9c7c5" stroke-width="2.5"/>
    <line x1="276" y1="68" x2="276" y2="84" stroke="#b9c7c5" stroke-width="2.5"/>
    <text x="264" y="106" fill="#4caf7d" font-size="9" text-anchor="middle">+ (longue)</text>
    <text x="292" y="90" fill="#a8c5c2" font-size="9">− (courte)</text>
    <!-- retour GND -->
    <path d="M276 84 L 300 84 L 300 118 L 69 118 L 69 96" stroke="#8a9a98" stroke-width="3" fill="none"/>
    <text x="185" y="114" fill="#a8c5c2" font-size="9.5" text-anchor="middle">retour au GND</text>
  </svg><div class="fig-cap">Fig. 3 — Le montage LED de base : pin D8 → résistance 220 Ω → LED → GND.</div></div>

  <div class="exemple">
    <div class="box-t">Exemple concret</div>
    <p>Le motif « flash court / pause longue », c'est exactement un <strong>code de clignotement diagnostic</strong> : sur beaucoup de moteurs, le voyant défaut clignote un code (2 flashs, pause, 3 flashs = code 23). Avec ce que tu viens d'apprendre, tu peux déjà reproduire un annonceur de code défaut. On le fera proprement au module 6 avec les boucles.</p>
  </div>

  <div class="recap">
    <div class="r-t">À retenir</div>
    <ul>
      <li><code>setup()</code> : une fois au démarrage. <code>loop()</code> : en boucle infinie.</li>
      <li><code>pinMode</code> → configurer, <code>digitalWrite</code> → commander, <code>delay</code> → attendre.</li>
      <li>Chaque instruction se termine par un <strong>;</strong> — et la casse compte.</li>
      <li>Vérifier ✓ puis Téléverser →. Erreur de compilation = lis le message, il dit tout.</li>
    </ul>
  </div>

  <div class="quiz">
    <div class="q-t">Quiz Module 4</div>
    <div class="q-q">Que fait <code>delay(500)</code> ?</div>
    <button class="q-opt" onclick="qz(this,false)">Attend 500 secondes</button>
    <button class="q-opt" onclick="qz(this,true)">Met le programme en pause 500 millisecondes (0,5 s)</button>
    <button class="q-opt" onclick="qz(this,false)">Fait clignoter 500 fois</button>
    <div class="q-exp">✅ <code>delay()</code> compte en <strong>millisecondes</strong>. 1000 ms = 1 s, donc 500 ms = une demi-seconde. Pendant un delay, l'Arduino ne fait RIEN d'autre — on verra plus tard comment éviter ça avec millis().</div>
  </div>
</section>
<!-- ============ MODULE 5 ============ -->
<section class="module" id="m5">
  <span class="mod-tag">Module 5 / 12</span>
  <h2>Le langage : <span>variables et calculs</span></h2>
  <p class="mod-intro">Un programme sans variables, c'est une machine sans capteurs : elle ne retient rien. Ici tu apprends à stocker, nommer et manipuler des valeurs.</p>

  <h3>5.1 — C'est quoi une variable ?</h3>
  <p>Une variable, c'est une <strong>petite case mémoire avec un nom</strong>, dans laquelle tu ranges une valeur qui peut changer pendant l'exécution.</p>
  <pre><code><span class="kw">int</span> temperature = <span class="nb">25</span>;   <span class="cm">// je crée une case "temperature" avec 25 dedans</span>
temperature = <span class="nb">78</span>;        <span class="cm">// je remplace le contenu par 78</span>
temperature = temperature + <span class="nb">2</span>; <span class="cm">// je prends la valeur, j'ajoute 2 → 80</span></code></pre>
  <div class="enclair">
    <div class="box-t">En clair</div>
    <p>Pense aux variables comme aux <strong>paramètres affichés sur l'écran de diagnostic</strong> d'une machine : « Temp huile : 78 °C », « Pression percussion : 160 bar », « Heures moteur : 12450 ». Chacune est une case mémoire mise à jour en permanence par le calculateur. Toi, tu vas créer les tiennes.</p>
  </div>

  <h3>5.2 — Les types de variables essentiels</h3>
  <div class="tbl-wrap"><table>
    <tr><th>Type</th><th>Contenu</th><th>Plage</th><th>Exemple</th></tr>
    <tr><td><code>int</code></td><td>Nombre entier</td><td>−32 768 à +32 767</td><td><code>int rpm = 1800;</code></td></tr>
    <tr><td><code>long</code></td><td>Grand entier</td><td>± 2 milliards</td><td><code>long heures = 125000;</code></td></tr>
    <tr><td><code>float</code></td><td>Nombre à virgule</td><td>± 3,4 × 10³⁸</td><td><code>float temp = 78.5;</code></td></tr>
    <tr><td><code>bool</code></td><td>Vrai / faux</td><td><code>true</code> ou <code>false</code></td><td><code>bool alarme = false;</code></td></tr>
    <tr><td><code>char</code></td><td>Un caractère</td><td>'A', 'z', '5'…</td><td><code>char lettre = 'A';</code></td></tr>
    <tr><td><code>String</code></td><td>Du texte</td><td>—</td><td><code>String msg = "OK";</code></td></tr>
  </table></div>
  <div class="attention">
    <div class="box-t">Piège classique</div>
    <p>Un <code>int</code> qui dépasse 32 767 <strong>déborde</strong> et repart en négatif ! Pour compter des millisecondes ou des heures de fonctionnement, utilise <code>long</code> (ou <code>unsigned long</code>). Un compteur horaire en <code>int</code>, c'est la panne assurée au bout de 9 heures de millis().</p>
  </div>

  <h3>5.3 — Constantes et bonnes pratiques de nommage</h3>
  <pre><code><span class="cm">// Les broches et les seuils ne changent jamais → const</span>
<span class="kw">const int</span> PIN_LED_ALARME = <span class="nb">8</span>;
<span class="kw">const int</span> PIN_CAPTEUR    = <span class="kw">A0</span>;
<span class="kw">const float</span> SEUIL_TEMP   = <span class="nb">80.0</span>;  <span class="cm">// °C</span>

<span class="cm">// Les mesures changent → variables normales</span>
<span class="kw">float</span> temperatureHuile = <span class="nb">0</span>;
<span class="kw">bool</span>  alarmeActive     = <span class="kw">false</span>;</code></pre>
  <ul>
    <li>Des <strong>noms parlants</strong> : <code>temperatureHuile</code>, pas <code>t</code> ni <code>x2</code>.</li>
    <li>Les constantes en <strong>MAJUSCULES</strong> : d'un coup d'œil tu sais que ça ne bouge pas.</li>
    <li>Déclare les pins en <code>const int</code> tout en haut du programme : si tu recâbles, tu ne modifies qu'une ligne.</li>
  </ul>

  <h3>5.4 — Les opérations</h3>
  <div class="tbl-wrap"><table>
    <tr><th>Opérateur</th><th>Rôle</th><th>Exemple</th><th>Résultat</th></tr>
    <tr><td><code>+ − * /</code></td><td>Calculs de base</td><td><code>10 / 4</code> (entiers)</td><td><code>2</code> (⚠ division entière !)</td></tr>
    <tr><td><code>%</code></td><td>Reste de division</td><td><code>10 % 4</code></td><td><code>2</code></td></tr>
    <tr><td><code>++</code> / <code>--</code></td><td>+1 / −1</td><td><code>compteur++;</code></td><td>compteur augmente de 1</td></tr>
    <tr><td><code>+=</code></td><td>Ajouter à</td><td><code>total += 5;</code></td><td>total = total + 5</td></tr>
  </table></div>
  <div class="attention">
    <div class="box-t">Le piège de la division entière</div>
    <p><code>int a = 10 / 4;</code> donne <strong>2</strong>, pas 2,5 ! Entre entiers, la virgule est jetée. Pour un résultat précis : <code>float a = 10.0 / 4.0;</code> → 2,5. Ce piège fausse silencieusement les conversions capteur — méfiance.</p>
  </div>

  <div class="exemple">
    <div class="box-t">Exemple concret — conversion capteur</div>
    <p>Un transducteur de pression 0-250 bar sort 0-5 V, lu comme 0-1023 sur A0. La conversion en bar :</p>
    <pre><code><span class="kw">int</span> brut = <span class="fn">analogRead</span>(<span class="kw">A0</span>);          <span class="cm">// 0 à 1023</span>
<span class="kw">float</span> pression = brut * <span class="nb">250.0</span> / <span class="nb">1023.0</span>; <span class="cm">// en bar</span></code></pre>
    <p>Remarque le <code>250.0</code> et non <code>250</code> : c'est ce qui force le calcul en virgule flottante. C'est exactement la mise à l'échelle qu'un calculateur applique à ses transducteurs.</p>
  </div>

  <div class="recap">
    <div class="r-t">À retenir</div>
    <ul>
      <li>Variable = case mémoire nommée. Type = ce qu'on peut y mettre.</li>
      <li><code>int</code> pour les entiers, <code>float</code> pour les virgules, <code>bool</code> pour vrai/faux, <code>long</code> pour les gros compteurs.</li>
      <li>Pins et seuils en <code>const</code> + MAJUSCULES en tête de programme.</li>
      <li>Division entre entiers = virgule perdue → mets des <code>.0</code>.</li>
    </ul>
  </div>

  <div class="quiz">
    <div class="q-t">Quiz Module 5</div>
    <div class="q-q">Quel type pour stocker une température moteur du genre 78,5 °C ?</div>
    <button class="q-opt" onclick="qz(this,false)"><code>int</code></button>
    <button class="q-opt" onclick="qz(this,true)"><code>float</code></button>
    <button class="q-opt" onclick="qz(this,false)"><code>bool</code></button>
    <div class="q-exp">✅ Une valeur à virgule → <code>float</code>. Un <code>int</code> stockerait 78 en perdant le ,5. Le <code>bool</code> ne connaît que true/false — parfait pour « alarme active ? », pas pour une mesure.</div>
  </div>
</section>

<!-- ============ MODULE 6 ============ -->
<section class="module" id="m6">
  <span class="mod-tag">Module 6 / 12</span>
  <h2>Décider et répéter : <span>if, else, boucles</span></h2>
  <p class="mod-intro">C'est ici que ton Arduino devient intelligent. Les conditions lui permettent de décider, les boucles de répéter. 90 % de la logique d'un automate tient dans ce module.</p>

  <h3>6.1 — La condition if / else</h3>
  <pre><code><span class="kw">if</span> (temperatureHuile &gt; <span class="nb">80.0</span>) {
  <span class="fn">digitalWrite</span>(PIN_LED_ALARME, <span class="kw">HIGH</span>);  <span class="cm">// trop chaud → alarme</span>
} <span class="kw">else</span> {
  <span class="fn">digitalWrite</span>(PIN_LED_ALARME, <span class="kw">LOW</span>);   <span class="cm">// sinon → tout va bien</span>
}</code></pre>
  <p>Lecture : « <strong>SI</strong> la condition entre parenthèses est vraie, exécute le premier bloc { }. <strong>SINON</strong>, exécute le bloc du else. »</p>

  <h4>Les opérateurs de comparaison</h4>
  <div class="tbl-wrap"><table>
    <tr><th>Opérateur</th><th>Signification</th><th>Exemple</th></tr>
    <tr><td><code>&gt;</code> / <code>&lt;</code></td><td>plus grand / plus petit</td><td><code>temp &gt; 80</code></td></tr>
    <tr><td><code>&gt;=</code> / <code>&lt;=</code></td><td>≥ / ≤</td><td><code>rpm &lt;= 2200</code></td></tr>
    <tr><td><code>==</code></td><td>est égal à</td><td><code>etat == HIGH</code></td></tr>
    <tr><td><code>!=</code></td><td>est différent de</td><td><code>mode != 0</code></td></tr>
  </table></div>
  <div class="attention">
    <div class="box-t">LE piège n°1 de tous les débutants</div>
    <p><code>=</code> c'est <strong>affecter</strong> (mettre une valeur dans la variable). <code>==</code> c'est <strong>comparer</strong>. Écrire <code>if (etat = HIGH)</code> au lieu de <code>if (etat == HIGH)</code> compile sans erreur… et la condition est toujours vraie. Ce bug a fait perdre des heures à des générations entières. Sois vigilant.</p>
  </div>

  <h4>Combiner des conditions : ET, OU, NON</h4>
  <pre><code><span class="cm">// && = ET : les deux doivent être vraies</span>
<span class="kw">if</span> (temp &gt; <span class="nb">80</span> && rpm &gt; <span class="nb">1500</span>) { ... }

<span class="cm">// || = OU : au moins une doit être vraie</span>
<span class="kw">if</span> (pression &lt; <span class="nb">2</span> || niveau &lt; <span class="nb">10</span>) { ... }

<span class="cm">// ! = NON : inverse</span>
<span class="kw">if</span> (!alarmeActive) { ... }  <span class="cm">// si alarme PAS active</span></code></pre>
  <div class="exemple">
    <div class="box-t">Exemple concret — logique de protection</div>
    <p>Une protection compresseur type : « déclencher si la température dépasse 110 °C <strong>OU</strong> si la pression d'huile tombe sous 2 bar <strong>ET</strong> que le moteur tourne ». En code :</p>
    <pre><code><span class="kw">if</span> (tempCompresseur &gt; <span class="nb">110</span> || (pressionHuile &lt; <span class="nb">2.0</span> && moteurTourne)) {
  <span class="fn">arretUrgence</span>();
}</code></pre>
    <p>Les parenthèses groupent le ET avant le OU. C'est mot pour mot une ligne de logique de sécurité machine.</p>
  </div>

  <h3>6.2 — Enchaîner les cas : else if</h3>
  <pre><code><span class="kw">if</span> (temp &lt; <span class="nb">60</span>) {
  <span class="cm">// zone froide : voyant vert</span>
} <span class="kw">else if</span> (temp &lt; <span class="nb">80</span>) {
  <span class="cm">// zone normale : rien</span>
} <span class="kw">else if</span> (temp &lt; <span class="nb">95</span>) {
  <span class="cm">// zone d'alerte : voyant orange</span>
} <span class="kw">else</span> {
  <span class="cm">// zone critique : alarme + dérating</span>
}</code></pre>
  <p>Les conditions sont testées <strong>dans l'ordre</strong>, et seule la première vraie est exécutée. C'est le principe des seuils étagés : pré-alarme, alarme, arrêt.</p>

  <h3>6.3 — La boucle for : répéter un nombre défini de fois</h3>
  <pre><code><span class="cm">// Clignoter 5 fois</span>
<span class="kw">for</span> (<span class="kw">int</span> i = <span class="nb">0</span>; i &lt; <span class="nb">5</span>; i++) {
  <span class="fn">digitalWrite</span>(<span class="nb">13</span>, <span class="kw">HIGH</span>);
  <span class="fn">delay</span>(<span class="nb">200</span>);
  <span class="fn">digitalWrite</span>(<span class="nb">13</span>, <span class="kw">LOW</span>);
  <span class="fn">delay</span>(<span class="nb">200</span>);
}</code></pre>
  <p>Décomposition de <code>for (int i = 0; i &lt; 5; i++)</code> :</p>
  <ol>
    <li><code>int i = 0</code> → point de départ : un compteur i à zéro</li>
    <li><code>i &lt; 5</code> → condition : on continue tant que c'est vrai</li>
    <li><code>i++</code> → à chaque tour, i augmente de 1 (0, 1, 2, 3, 4 → stop)</li>
  </ol>

  <div class="exemple">
    <div class="box-t">Exemple concret — annonceur de code défaut</div>
    <p>Le fameux code panne par clignotements, version propre :</p>
    <pre><code><span class="kw">void</span> <span class="fn">flasherCode</span>(<span class="kw">int</span> nombre) {
  <span class="kw">for</span> (<span class="kw">int</span> i = <span class="nb">0</span>; i &lt; nombre; i++) {
    <span class="fn">digitalWrite</span>(<span class="nb">13</span>, <span class="kw">HIGH</span>); <span class="fn">delay</span>(<span class="nb">300</span>);
    <span class="fn">digitalWrite</span>(<span class="nb">13</span>, <span class="kw">LOW</span>);  <span class="fn">delay</span>(<span class="nb">300</span>);
  }
  <span class="fn">delay</span>(<span class="nb">1500</span>); <span class="cm">// pause entre les groupes</span>
}
<span class="cm">// Dans loop() : flasherCode(2); flasherCode(3); → code "23"</span></code></pre>
    <p>Au passage tu viens de voir ta première <strong>fonction personnalisée</strong> : un bloc de code réutilisable avec un paramètre. On en reparle au module 11.</p>
  </div>

  <h3>6.4 — La boucle while : répéter tant qu'une condition dure</h3>
  <pre><code><span class="kw">while</span> (<span class="fn">digitalRead</span>(PIN_BOUTON) == <span class="kw">LOW</span>) {
  <span class="cm">// on attend ici tant que le bouton n'est pas pressé</span>
}</code></pre>
  <p>Attention : si la condition ne devient jamais fausse, le programme reste bloqué. À utiliser avec précaution.</p>

  <div class="recap">
    <div class="r-t">À retenir</div>
    <ul>
      <li><code>if / else if / else</code> = la prise de décision, testée dans l'ordre.</li>
      <li><code>==</code> compare, <code>=</code> affecte. Ne les confonds JAMAIS.</li>
      <li><code>&&</code> (ET), <code>||</code> (OU), <code>!</code> (NON) pour les logiques combinées.</li>
      <li><code>for</code> répète N fois, <code>while</code> répète tant que c'est vrai.</li>
    </ul>
  </div>

  <div class="quiz">
    <div class="q-t">Quiz Module 6</div>
    <div class="q-q">Que fait <code>if (temp &gt; 80 && niveau &lt; 20)</code> ?</div>
    <button class="q-opt" onclick="qz(this,false)">Vrai si l'une OU l'autre condition est vraie</button>
    <button class="q-opt" onclick="qz(this,true)">Vrai seulement si les DEUX conditions sont vraies en même temps</button>
    <button class="q-opt" onclick="qz(this,false)">Vrai si temp est différent de 80</button>
    <div class="q-exp">✅ <code>&&</code> = ET logique : il faut température &gt; 80 <strong>ET</strong> niveau &lt; 20 simultanément. Pour un OU, c'est <code>||</code>.</div>
  </div>
</section>
<!-- ============ MODULE 7 ============ -->
<section class="module" id="m7">
  <span class="mod-tag">Module 7 / 12</span>
  <h2>Entrées numériques : <span>boutons et contacts</span></h2>
  <p class="mod-intro">Jusqu'ici l'Arduino ne faisait qu'obéir à son programme. Maintenant il va réagir au monde extérieur : boutons, fins de course, pressostats, contacts de porte…</p>

  <h3>7.1 — Lire une pin numérique</h3>
  <pre><code><span class="kw">int</span> etat = <span class="fn">digitalRead</span>(<span class="nb">2</span>);  <span class="cm">// renvoie HIGH (5V) ou LOW (0V)</span></code></pre>
  <p>C'est le miroir de <code>digitalWrite</code> : au lieu d'imposer un état, on <strong>lit</strong> l'état présent sur la pin.</p>

  <h3>7.2 — Le problème de la pin « en l'air »</h3>
  <p>Une entrée non connectée à rien est dite <strong>flottante</strong> : elle capte les parasites ambiants et sa lecture devient aléatoire (HIGH, LOW, HIGH…). Il faut <strong>toujours</strong> forcer un état de repos avec une résistance :</p>
  <div class="schema"><span class="lbl">PULL-UP (repos = HIGH)          PULL-DOWN (repos = LOW)</span>
   5V                              5V
    │                               │
   [R 10kΩ]                       [bouton]
    │                               │
    ├────► pin D2                   ├────► pin D2
    │                               │
  [bouton]                        [R 10kΩ]
    │                               │
   GND                             GND

 bouton relâché → HIGH          bouton relâché → LOW
 bouton pressé  → LOW           bouton pressé  → HIGH</div>

  <h3>7.3 — La solution élégante : INPUT_PULLUP</h3>
  <p>Bonne nouvelle : l'ATmega328P intègre déjà des résistances pull-up internes. Il suffit de les activer :</p>
  <pre><code><span class="kw">const int</span> PIN_BOUTON = <span class="nb">2</span>;

<span class="kw">void</span> <span class="fn">setup</span>() {
  <span class="fn">pinMode</span>(PIN_BOUTON, <span class="kw">INPUT_PULLUP</span>); <span class="cm">// pull-up interne activée</span>
  <span class="fn">pinMode</span>(<span class="nb">13</span>, <span class="kw">OUTPUT</span>);
}

<span class="kw">void</span> <span class="fn">loop</span>() {
  <span class="kw">if</span> (<span class="fn">digitalRead</span>(PIN_BOUTON) == <span class="kw">LOW</span>) {  <span class="cm">// LOW = pressé !</span>
    <span class="fn">digitalWrite</span>(<span class="nb">13</span>, <span class="kw">HIGH</span>);
  } <span class="kw">else</span> {
    <span class="fn">digitalWrite</span>(<span class="nb">13</span>, <span class="kw">LOW</span>);
  }
}</code></pre>
  <p>Câblage ultra simple : <strong>une patte du bouton sur D2, l'autre sur GND</strong>. C'est tout. Pas de résistance externe.</p>
  <div class="fig"><svg viewBox="0 0 340 140" xmlns="http://www.w3.org/2000/svg" font-family="sans-serif">
    <!-- bouton vu de dessus -->
    <rect x="40" y="30" width="70" height="70" rx="8" fill="#0a1c1c" stroke="#2d8a85" stroke-width="2"/>
    <circle cx="75" cy="65" r="22" fill="#8a9a98"/>
    <circle cx="75" cy="65" r="14" fill="#5f6f6d"/>
    <line x1="48" y1="30" x2="48" y2="14" stroke="#b9c7c5" stroke-width="3"/>
    <line x1="102" y1="30" x2="102" y2="14" stroke="#b9c7c5" stroke-width="3"/>
    <line x1="48" y1="100" x2="48" y2="116" stroke="#b9c7c5" stroke-width="3"/>
    <line x1="102" y1="100" x2="102" y2="116" stroke="#b9c7c5" stroke-width="3"/>
    <text x="75" y="134" fill="#e8f0ef" font-size="10" text-anchor="middle">bouton 4 pattes</text>
    <!-- câblage -->
    <line x1="48" y1="14" x2="200" y2="14" stroke="#f0a500" stroke-width="3"/>
    <text x="212" y="18" fill="#ffc93c" font-size="11" font-weight="800">→ D2 (INPUT_PULLUP)</text>
    <line x1="48" y1="116" x2="200" y2="116" stroke="#8a9a98" stroke-width="3"/>
    <text x="212" y="120" fill="#a8c5c2" font-size="11" font-weight="800">→ GND</text>
    <text x="230" y="62" fill="#a8c5c2" font-size="10">repos = HIGH</text>
    <text x="230" y="78" fill="#4caf7d" font-size="10" font-weight="700">appui = LOW</text>
  </svg><div class="fig-cap">Fig. 4 — Câblage minimal avec pull-up interne : deux fils, zéro résistance externe.</div></div>

  <div class="enclair">
    <div class="box-t">En clair — la logique inversée</div>
    <p>Avec une pull-up, la logique est <strong>inversée</strong> : repos = HIGH, appui = LOW. Ça surprend au début, mais c'est un standard industriel : beaucoup d'entrées de calculateurs machines fonctionnent en « actif à la masse » (le capteur tire la ligne au GND). Un fil coupé se lit HIGH = état de repos → la coupure de câble est détectable. C'est de la sécurité intégrée.</p>
  </div>

  <h3>7.4 — Les rebonds (bouncing) et comment les gérer</h3>
  <p>Un bouton mécanique ne se ferme pas proprement : les contacts <strong>rebondissent</strong> pendant quelques millisecondes, générant une rafale de HIGH/LOW. Si tu comptes les appuis, un seul appui peut en compter cinq !</p>
  <pre><code><span class="cm">// Anti-rebond simple : on ignore tout pendant 50 ms après un appui</span>
<span class="kw">if</span> (<span class="fn">digitalRead</span>(PIN_BOUTON) == <span class="kw">LOW</span>) {
  compteur++;
  <span class="fn">delay</span>(<span class="nb">50</span>);                                <span class="cm">// laisse les rebonds passer</span>
  <span class="kw">while</span> (<span class="fn">digitalRead</span>(PIN_BOUTON) == <span class="kw">LOW</span>);  <span class="cm">// attend le relâchement</span>
}</code></pre>
  <div class="exemple">
    <div class="box-t">Exemple concret — comptage de cycles</div>
    <p>Tu veux compter les cycles d'un vérin avec un capteur fin de course pour la maintenance préventive (graissage toutes les 5 000 manœuvres). Sans anti-rebond, ton compteur dériverait de 3 à 5× la réalité. Le même phénomène existe sur les entrées comptage rapide des automates — ils intègrent un filtre réglable pour exactement cette raison.</p>
  </div>

  <h3>7.5 — Mémoriser un état : le toggle</h3>
  <p>Un appui allume, l'appui suivant éteint — comme un bouton marche/arrêt :</p>
  <pre><code><span class="kw">bool</span> sortieActive = <span class="kw">false</span>;

<span class="kw">void</span> <span class="fn">loop</span>() {
  <span class="kw">if</span> (<span class="fn">digitalRead</span>(PIN_BOUTON) == <span class="kw">LOW</span>) {
    sortieActive = !sortieActive;        <span class="cm">// inverse l'état mémorisé</span>
    <span class="fn">digitalWrite</span>(<span class="nb">13</span>, sortieActive);
    <span class="fn">delay</span>(<span class="nb">50</span>);
    <span class="kw">while</span> (<span class="fn">digitalRead</span>(PIN_BOUTON) == <span class="kw">LOW</span>);
  }
}</code></pre>

  <h3>7.6 — Piloter du lourd : le module relais</h3>
  <p>Pour commander une charge 12 V / 24 V / 230 V (ventilateur, pompe, sirène), on utilise un <strong>module relais</strong> : trois fils côté Arduino (VCC 5V, GND, IN sur une pin), et côté puissance les bornes COM / NO / NC comme n'importe quel relais.</p>
  <div class="fig"><svg viewBox="0 0 360 160" xmlns="http://www.w3.org/2000/svg" font-family="sans-serif">
    <rect x="60" y="20" width="240" height="120" rx="8" fill="#177a72" stroke="#0e544e" stroke-width="3"/>
    <!-- cube relais -->
    <rect x="90" y="38" width="90" height="66" rx="4" fill="#3d8bfd" stroke="#2b62b3"/>
    <text x="135" y="66" fill="#fff" font-size="10" font-weight="800" text-anchor="middle">RELAIS</text>
    <text x="135" y="82" fill="#dce9ff" font-size="8.5" text-anchor="middle">bobine 5V / 10A 250V</text>
    <!-- bornier puissance -->
    <rect x="204" y="36" width="72" height="70" rx="4" fill="#2fae63"/>
    <circle cx="226" cy="52" r="7" fill="#0a1c1c"/>
    <circle cx="226" cy="72" r="7" fill="#0a1c1c"/>
    <circle cx="226" cy="92" r="7" fill="#0a1c1c"/>
    <text x="248" y="56" fill="#fff" font-size="10" font-weight="800">NO</text>
    <text x="248" y="76" fill="#fff" font-size="10" font-weight="800">COM</text>
    <text x="248" y="96" fill="#fff" font-size="10" font-weight="800">NC</text>
    <!-- pins commande -->
    <line x1="96" y1="140" x2="96" y2="156" stroke="#b9c7c5" stroke-width="3"/>
    <line x1="120" y1="140" x2="120" y2="156" stroke="#b9c7c5" stroke-width="3"/>
    <line x1="144" y1="140" x2="144" y2="156" stroke="#b9c7c5" stroke-width="3"/>
    <text x="82" y="130" fill="#ffc93c" font-size="9" font-weight="700">IN</text>
    <text x="108" y="130" fill="#ff9d5c" font-size="9" font-weight="700">VCC</text>
    <text x="136" y="130" fill="#a8c5c2" font-size="9" font-weight="700">GND</text>
    <text x="120" y="30" fill="#0a1c1c" font-size="1">.</text>
    <text x="30" y="80" fill="#f0a500" font-size="10" font-weight="800" text-anchor="middle" transform="rotate(-90 30 80)">CÔTÉ ARDUINO</text>
    <text x="330" y="80" fill="#f0a500" font-size="10" font-weight="800" text-anchor="middle" transform="rotate(90 330 80)">CÔTÉ PUISSANCE</text>
  </svg><div class="fig-cap">Fig. 5 — Module relais : 3 fils de commande (5 V) à gauche, la charge de puissance à droite.</div></div>

  <div class="attention">
    <div class="box-t">Sécurité</div>
    <p>La plupart des modules relais du commerce sont <strong>actifs à LOW</strong> (LOW = relais collé). Teste avant de conclure à une panne. Et si tu commutes du 230 V : isolation soignée, boîtier fermé, et jamais de test à main levée. Les règles de l'atelier s'appliquent aussi sur la paillasse.</p>
  </div>

  <div class="recap">
    <div class="r-t">À retenir</div>
    <ul>
      <li><code>digitalRead(pin)</code> renvoie HIGH ou LOW.</li>
      <li>Jamais d'entrée flottante → <code>INPUT_PULLUP</code> + bouton vers GND.</li>
      <li>Avec pull-up : <strong>appui = LOW</strong>. Logique inversée, standard industriel.</li>
      <li>Contact mécanique = rebonds → anti-rebond obligatoire pour compter.</li>
      <li>Charges de puissance → module relais, jamais la pin en direct.</li>
    </ul>
  </div>

  <div class="quiz">
    <div class="q-t">Quiz Module 7</div>
    <div class="q-q">Bouton câblé en INPUT_PULLUP, une patte sur D2, l'autre sur GND. Quand on APPUIE, digitalRead(2) renvoie :</div>
    <button class="q-opt" onclick="qz(this,false)">HIGH</button>
    <button class="q-opt" onclick="qz(this,true)">LOW</button>
    <button class="q-opt" onclick="qz(this,false)">1023</button>
    <div class="q-exp">✅ L'appui relie la pin au GND → <strong>LOW</strong>. Au repos, la pull-up interne tire la pin à 5 V → HIGH. Le 1023, c'est le monde analogique (module suivant !).</div>
  </div>
</section>

<!-- ============ MODULE 8 ============ -->
<section class="module" id="m8">
  <span class="mod-tag">Module 8 / 12</span>
  <h2>Le monde <span>analogique</span> : mesurer et doser</h2>
  <p class="mod-intro">Le tout-ou-rien, c'est bien. Mais le monde réel est proportionnel : une température monte progressivement, une pression varie en continu. Voici comment l'Arduino mesure… et dose.</p>

  <h3>8.1 — analogRead : mesurer une tension</h3>
  <p>Les pins A0-A5 sont reliées à un <strong>CAN (convertisseur analogique-numérique)</strong> 10 bits : il transforme une tension 0-5 V en nombre <strong>0 à 1023</strong>.</p>
  <div class="hero-card">
    <div class="hc-big">0 V → 0&nbsp;&nbsp;|&nbsp;&nbsp;5 V → 1023</div>
    <div class="hc-lbl">Résolution : 5 V / 1024 pas ≈ 4,9 mV par unité</div>
  </div>
  <pre><code><span class="kw">int</span> brut = <span class="fn">analogRead</span>(<span class="kw">A0</span>);              <span class="cm">// 0..1023</span>
<span class="kw">float</span> tension = brut * <span class="nb">5.0</span> / <span class="nb">1023.0</span>;     <span class="cm">// conversion en volts</span></code></pre>
  <div class="enclair">
    <div class="box-t">En clair</div>
    <p>C'est exactement ce que fait un calculateur avec ses transducteurs : le capteur de pression sort 0,5-4,5 V, le CAN du calculateur convertit en valeur numérique, et le logiciel met à l'échelle en bar. Quand tu lis « Pression : 165 bar » sur l'écran de diag, il y a eu un <code>analogRead</code> + une mise à l'échelle quelque part.</p>
  </div>

  <h3>8.2 — Premier montage : le potentiomètre</h3>
  <div class="schema"><span class="lbl">POTENTIOMÈTRE (3 pattes)</span>
  patte 1 ──► 5V
  patte 2 (curseur, au milieu) ──► A0
  patte 3 ──► GND

 Tourner le bouton = faire varier la tension
 du curseur entre 0 et 5 V → 0 à 1023 sur A0</div>
  <p>Le potentiomètre est un diviseur de tension réglable. C'est le composant d'apprentissage parfait — et c'est aussi le principe des capteurs de position à piste résistive (pédales, manipulateurs).</p>
  <div class="fig"><svg viewBox="0 0 320 150" xmlns="http://www.w3.org/2000/svg" font-family="sans-serif">
    <circle cx="120" cy="60" r="42" fill="#0a1c1c" stroke="#2d8a85" stroke-width="2"/>
    <circle cx="120" cy="60" r="16" fill="#8a9a98"/>
    <line x1="120" y1="60" x2="132" y2="46" stroke="#0a1c1c" stroke-width="4"/>
    <line x1="92" y1="98" x2="92" y2="122" stroke="#b9c7c5" stroke-width="3"/>
    <line x1="120" y1="102" x2="120" y2="122" stroke="#b9c7c5" stroke-width="3"/>
    <line x1="148" y1="98" x2="148" y2="122" stroke="#b9c7c5" stroke-width="3"/>
    <text x="92" y="138" fill="#ff9d5c" font-size="10" font-weight="800" text-anchor="middle">5V</text>
    <text x="120" y="138" fill="#ffc93c" font-size="10" font-weight="800" text-anchor="middle">A0</text>
    <text x="148" y="138" fill="#a8c5c2" font-size="10" font-weight="800" text-anchor="middle">GND</text>
    <text x="230" y="46" fill="#e8f0ef" font-size="11" text-anchor="middle">Tourner le bouton =</text>
    <text x="230" y="63" fill="#e8f0ef" font-size="11" text-anchor="middle">tension variable 0-5 V</text>
    <text x="230" y="80" fill="#6fd3c7" font-size="11" font-weight="700" text-anchor="middle">→ 0 à 1023 sur A0</text>
    <text x="230" y="106" fill="#a8c5c2" font-size="9.5" text-anchor="middle">patte du milieu = curseur</text>
  </svg><div class="fig-cap">Fig. 6 — Le potentiomètre : un diviseur de tension réglable, ton premier capteur analogique.</div></div>


  <h3>8.3 — map() : la mise à l'échelle toute faite</h3>
  <pre><code><span class="cm">// Convertir 0..1023 en 0..100 %</span>
<span class="kw">int</span> pourcent = <span class="fn">map</span>(brut, <span class="nb">0</span>, <span class="nb">1023</span>, <span class="nb">0</span>, <span class="nb">100</span>);

<span class="cm">// Capteur 0,5-4,5V (102..921) vers 0..250 bar</span>
<span class="kw">int</span> pression = <span class="fn">map</span>(brut, <span class="nb">102</span>, <span class="nb">921</span>, <span class="nb">0</span>, <span class="nb">250</span>);</code></pre>
  <p><code>map(valeur, deMin, deMax, versMin, versMax)</code> fait la règle de trois pour toi. Note : elle travaille en entiers ; pour de la précision décimale, fais le calcul en <code>float</code> à la main.</p>
  <div class="astuce">
    <div class="box-t">Astuce diagnostic</div>
    <p>Les capteurs industriels utilisent souvent 0,5-4,5 V plutôt que 0-5 V. Pourquoi ? Parce que 0 V exactement = <strong>fil coupé ou court-circuit à la masse</strong>, et 5 V = <strong>court au +</strong>. La plage « vivante » décalée permet de détecter les défauts de câblage. Tu peux implémenter la même surveillance : si brut &lt; 50 ou &gt; 980 → défaut capteur !</p>
  </div>

  <h3>8.4 — analogWrite : le PWM, ou comment doser une sortie</h3>
  <p>L'Arduino ne sait pas produire une vraie tension variable. Il triche intelligemment avec le <strong>PWM (Pulse Width Modulation — modulation de largeur d'impulsion)</strong> : il découpe le 5 V en impulsions très rapides (~490 Hz) et fait varier le <strong>rapport cyclique</strong> (le % de temps à l'état haut).</p>
  <div class="schema"><span class="lbl">PWM — rapport cyclique</span>
 25%  ▄▄░░░░░░▄▄░░░░░░   → LED faible / moteur lent
 50%  ▄▄▄▄░░░░▄▄▄▄░░░░   → moyen
 90%  ▄▄▄▄▄▄▄░▄▄▄▄▄▄▄░   → presque plein régime

 analogWrite(pin, 0..255)   0=0%  128=50%  255=100%</div>
  <pre><code><span class="cm">// Faire respirer une LED sur la pin ~9</span>
<span class="kw">for</span> (<span class="kw">int</span> i = <span class="nb">0</span>; i &lt;= <span class="nb">255</span>; i++) {
  <span class="fn">analogWrite</span>(<span class="nb">9</span>, i);
  <span class="fn">delay</span>(<span class="nb">4</span>);
}</code></pre>
  <ul>
    <li>Uniquement sur les pins marquées <strong>~</strong> : 3, 5, 6, 9, 10, 11.</li>
    <li>Échelle <strong>0-255</strong> (8 bits), à ne pas confondre avec le 0-1023 de la lecture !</li>
  </ul>
  <div class="exemple">
    <div class="box-t">Exemple concret — le PWM est partout sur nos machines</div>
    <p>Les électrovannes proportionnelles des circuits hydrauliques sont pilotées en <strong>PWM par le calculateur</strong> : le rapport cyclique règle le courant dans la bobine, donc la position du tiroir, donc le débit. Quand tu mesures 40 % de rapport cyclique sur une vanne proportionnelle avec l'oscillo, c'est exactement le principe d'<code>analogWrite(pin, 102)</code>. Même physique, autre échelle de puissance.</p>
  </div>

  <h3>8.5 — Montage complet : potentiomètre → LED dosée</h3>
  <pre><code><span class="kw">const int</span> PIN_POT = <span class="kw">A0</span>;
<span class="kw">const int</span> PIN_LED = <span class="nb">9</span>;   <span class="cm">// pin PWM (~)</span>

<span class="kw">void</span> <span class="fn">setup</span>() {
  <span class="fn">pinMode</span>(PIN_LED, <span class="kw">OUTPUT</span>);
}

<span class="kw">void</span> <span class="fn">loop</span>() {
  <span class="kw">int</span> brut = <span class="fn">analogRead</span>(PIN_POT);          <span class="cm">// 0..1023</span>
  <span class="kw">int</span> pwm  = <span class="fn">map</span>(brut, <span class="nb">0</span>, <span class="nb">1023</span>, <span class="nb">0</span>, <span class="nb">255</span>); <span class="cm">// 0..255</span>
  <span class="fn">analogWrite</span>(PIN_LED, pwm);
}</code></pre>
  <p>Quatre lignes utiles, et tu as un variateur complet : lecture, mise à l'échelle, commande. C'est le squelette de la moitié des systèmes de régulation.</p>

  <div class="recap">
    <div class="r-t">À retenir</div>
    <ul>
      <li><code>analogRead</code> : tension 0-5 V → nombre <strong>0-1023</strong> (10 bits).</li>
      <li><code>analogWrite</code> : PWM <strong>0-255</strong>, pins ~ uniquement. Ce n'est pas une vraie tension analogique !</li>
      <li><code>map()</code> fait la règle de trois entre deux échelles.</li>
      <li>Plage capteur 0,5-4,5 V = détection de fil coupé intégrée.</li>
    </ul>
  </div>

  <div class="quiz">
    <div class="q-t">Quiz Module 8</div>
    <div class="q-q">analogRead(A0) renvoie 512. Quelle est environ la tension sur A0 ?</div>
    <button class="q-opt" onclick="qz(this,false)">5 V</button>
    <button class="q-opt" onclick="qz(this,true)">2,5 V</button>
    <button class="q-opt" onclick="qz(this,false)">0,5 V</button>
    <div class="q-exp">✅ 512 ≈ la moitié de 1023 → moitié de 5 V = <strong>2,5 V</strong>. Formule : tension = brut × 5,0 / 1023.</div>
  </div>
</section>
<!-- ============ MODULE 9 ============ -->
<section class="module" id="m9">
  <span class="mod-tag">Module 9 / 12</span>
  <h2>Le moniteur série : <span>ton outil de diagnostic</span></h2>
  <p class="mod-intro">Comment savoir ce qui se passe DANS l'Arduino ? Le moniteur série est ta valise de diagnostic : il affiche en temps réel les valeurs, les états, les messages de ton programme.</p>

  <h3>9.1 — Mise en route</h3>
  <pre><code><span class="kw">void</span> <span class="fn">setup</span>() {
  Serial.<span class="fn">begin</span>(<span class="nb">9600</span>);   <span class="cm">// ouvre la liaison série à 9600 bauds</span>
}

<span class="kw">void</span> <span class="fn">loop</span>() {
  Serial.<span class="fn">println</span>(<span class="st">"Systeme demarre"</span>);   <span class="cm">// texte + retour à la ligne</span>
  Serial.<span class="fn">print</span>(<span class="st">"Temp: "</span>);              <span class="cm">// texte SANS retour à la ligne</span>
  Serial.<span class="fn">println</span>(temperature);         <span class="cm">// la valeur, puis retour ligne</span>
  <span class="fn">delay</span>(<span class="nb">1000</span>);
}</code></pre>
  <p>Dans l'IDE : icône <strong>loupe 🔍 en haut à droite</strong> (ou Outils → Moniteur série). Règle la vitesse en bas à droite sur <strong>9600</strong> — elle doit correspondre au <code>Serial.begin()</code>, sinon tu verras des caractères illisibles.</p>
  <div class="enclair">
    <div class="box-t">En clair</div>
    <p>Le moniteur série, c'est ton <strong>outil de diagnostic branché sur le calculateur</strong> : la fenêtre de données temps réel où défilent les paramètres. La vitesse en bauds, c'est comme la vitesse d'un bus de communication machine : les deux côtés doivent parler à la même cadence, sinon c'est du charabia.</p>
  </div>

  <h3>9.2 — Le réflexe du débogage</h3>
  <p>Ton programme ne fait pas ce que tu veux ? <strong>Affiche tout.</strong> C'est LE réflexe professionnel :</p>
  <pre><code><span class="kw">int</span> brut = <span class="fn">analogRead</span>(<span class="kw">A0</span>);
Serial.<span class="fn">print</span>(<span class="st">"brut="</span>);   Serial.<span class="fn">print</span>(brut);
Serial.<span class="fn">print</span>(<span class="st">"  temp="</span>); Serial.<span class="fn">println</span>(temperature);</code></pre>
  <div class="exemple">
    <div class="box-t">Exemple concret — méthode de diagnostic</div>
    <p>C'est la même démarche qu'un dépannage capteur sur machine : tu ne remplaces pas la sonde au hasard, tu <strong>mesures la valeur brute au calculateur</strong> (tension, résistance), puis la valeur interprétée à l'écran de diag, et tu compares. Ici pareil : la valeur brute (0-1023) te dit si le câblage est bon, la valeur convertie te dit si ton calcul est bon. Deux étages, deux vérifications.</p>
  </div>

  <h3>9.3 — Le traceur série : la courbe en direct</h3>
  <p>Menu <strong>Outils → Traceur série</strong> : chaque <code>Serial.println(valeur)</code> devient un point sur un graphique en temps réel. Idéal pour visualiser une température qui monte, un signal bruité, un capteur instable.</p>
  <div class="astuce">
    <div class="box-t">Pour tracer plusieurs courbes</div>
    <p>Sépare les valeurs par une tabulation : <code>Serial.print(temp); Serial.print("\t"); Serial.println(pression);</code> → deux courbes superposées. Ton premier enregistreur de données ! C'est l'embryon de la collecte de données pour la maintenance prédictive.</p>
  </div>

  <h3>9.4 — Recevoir des commandes depuis le PC</h3>
  <pre><code><span class="kw">void</span> <span class="fn">loop</span>() {
  <span class="kw">if</span> (Serial.<span class="fn">available</span>() &gt; <span class="nb">0</span>) {     <span class="cm">// des données sont arrivées ?</span>
    <span class="kw">char</span> cmd = Serial.<span class="fn">read</span>();        <span class="cm">// lire un caractère</span>
    <span class="kw">if</span> (cmd == <span class="st">'a'</span>) <span class="fn">digitalWrite</span>(<span class="nb">13</span>, <span class="kw">HIGH</span>);  <span class="cm">// 'a' = allumer</span>
    <span class="kw">if</span> (cmd == <span class="st">'e'</span>) <span class="fn">digitalWrite</span>(<span class="nb">13</span>, <span class="kw">LOW</span>);   <span class="cm">// 'e' = éteindre</span>
  }
}</code></pre>
  <p>Tape « a » ou « e » dans la barre du moniteur et envoie : tu pilotes la carte au clavier. Tu viens de créer ta première <strong>interface de commande</strong> — le principe d'un test d'actionneur forcé en mode diagnostic.</p>

  <h3>9.5 — millis() : chronométrer sans bloquer</h3>
  <p><code>delay()</code> a un gros défaut : il <strong>fige tout le programme</strong>. Pendant un delay(1000), l'Arduino ne lit plus les boutons, ne surveille plus les capteurs. La solution pro : <code>millis()</code>, qui renvoie le nombre de millisecondes écoulées depuis le démarrage.</p>
  <pre><code><span class="kw">unsigned long</span> dernierEnvoi = <span class="nb">0</span>;

<span class="kw">void</span> <span class="fn">loop</span>() {
  <span class="cm">// Toutes les 1000 ms, sans jamais bloquer :</span>
  <span class="kw">if</span> (<span class="fn">millis</span>() - dernierEnvoi &gt;= <span class="nb">1000</span>) {
    dernierEnvoi = <span class="fn">millis</span>();
    Serial.<span class="fn">println</span>(<span class="fn">analogRead</span>(<span class="kw">A0</span>));
  }
  <span class="cm">// Ici, le reste du programme continue de tourner :</span>
  <span class="cm">// lecture boutons, surveillance alarmes, etc.</span>
}</code></pre>
  <div class="enclair">
    <div class="box-t">En clair</div>
    <p><code>delay()</code> = arrêter toute la machine pour attendre. <code>millis()</code> = regarder sa montre en continuant de travailler. Un calculateur ne se fige jamais une seconde entière : il gère toutes ses tâches en parallèle grâce à cette technique. À partir de maintenant, prends l'habitude du millis() pour tout ce qui est périodique.</p>
  </div>

  <div class="recap">
    <div class="r-t">À retenir</div>
    <ul>
      <li><code>Serial.begin(9600)</code> dans setup, puis <code>print</code>/<code>println</code> partout où tu veux voir ce qui se passe.</li>
      <li>Même vitesse des deux côtés, sinon caractères illisibles.</li>
      <li>Traceur série = courbes temps réel gratuites.</li>
      <li><code>millis()</code> remplace <code>delay()</code> dès que le programme doit rester réactif.</li>
    </ul>
  </div>

  <div class="quiz">
    <div class="q-t">Quiz Module 9</div>
    <div class="q-q">Le moniteur série affiche des caractères bizarres du genre ⸮⸮⸮. Cause probable ?</div>
    <button class="q-opt" onclick="qz(this,false)">La carte est grillée</button>
    <button class="q-opt" onclick="qz(this,true)">La vitesse du moniteur ne correspond pas au Serial.begin()</button>
    <button class="q-opt" onclick="qz(this,false)">Il manque une résistance</button>
    <div class="q-exp">✅ Désaccord de vitesse (bauds) = charabia garanti. Vérifie que le moniteur est réglé sur la même valeur que <code>Serial.begin()</code>. Réflexe identique sur un bus machine : vitesses incompatibles = trames illisibles.</div>
  </div>
</section>

<!-- ============ MODULE 10 ============ -->
<section class="module" id="m10">
  <span class="mod-tag">Module 10 / 12</span>
  <h2>Les capteurs <span>indispensables</span></h2>
  <p class="mod-intro">Maintenant qu'on sait lire, décider et afficher, équipons-nous. Voici les capteurs que tu utiliseras dans 90 % des projets, avec leur câblage et leur code.</p>
  <div class="fig"><svg viewBox="0 0 380 190" xmlns="http://www.w3.org/2000/svg" font-family="sans-serif">
    <!-- LM35 TO-92 -->
    <path d="M40 40 A 30 30 0 0 1 100 40 L 100 78 L 40 78 Z" fill="#0a1c1c" stroke="#2d8a85"/>
    <text x="70" y="64" fill="#e8f0ef" font-size="9" font-weight="700" text-anchor="middle">LM35</text>
    <line x1="52" y1="78" x2="52" y2="104" stroke="#b9c7c5" stroke-width="2.5"/>
    <line x1="70" y1="78" x2="70" y2="104" stroke="#b9c7c5" stroke-width="2.5"/>
    <line x1="88" y1="78" x2="88" y2="104" stroke="#b9c7c5" stroke-width="2.5"/>
    <text x="52" y="116" fill="#ff9d5c" font-size="8" text-anchor="middle">5V</text>
    <text x="70" y="116" fill="#ffc93c" font-size="8" text-anchor="middle">OUT</text>
    <text x="88" y="116" fill="#a8c5c2" font-size="8" text-anchor="middle">GND</text>
    <text x="70" y="140" fill="#e8f0ef" font-size="10" font-weight="700" text-anchor="middle">LM35</text>
    <text x="70" y="154" fill="#a8c5c2" font-size="9" text-anchor="middle">10 mV / °C</text>
    <!-- DS18B20 étanche -->
    <rect x="150" y="34" width="24" height="64" rx="10" fill="#b9c7c5" stroke="#7a8a88"/>
    <rect x="154" y="26" width="16" height="12" rx="4" fill="#8a9a98"/>
    <path d="M162 98 C 162 120 190 118 196 136" stroke="#222" stroke-width="4" fill="none"/>
    <text x="162" y="140" fill="#e8f0ef" font-size="10" font-weight="700" text-anchor="middle">DS18B20</text>
    <text x="162" y="154" fill="#a8c5c2" font-size="9" text-anchor="middle">sonde étanche 1-Wire</text>
    <text x="162" y="167" fill="#a8c5c2" font-size="9" text-anchor="middle">±0,5 °C</text>
    <!-- HC-SR04 -->
    <rect x="236" y="40" width="128" height="60" rx="6" fill="#177a72" stroke="#0e544e" stroke-width="2"/>
    <circle cx="268" cy="70" r="21" fill="#0a1c1c" stroke="#8a9a98" stroke-width="3"/>
    <circle cx="332" cy="70" r="21" fill="#0a1c1c" stroke="#8a9a98" stroke-width="3"/>
    <circle cx="268" cy="70" r="9" fill="#123434"/>
    <circle cx="332" cy="70" r="9" fill="#123434"/>
    <text x="268" y="74" fill="#6fd3c7" font-size="8" text-anchor="middle">T</text>
    <text x="332" y="74" fill="#6fd3c7" font-size="8" text-anchor="middle">R</text>
    <line x1="276" y1="104" x2="276" y2="118" stroke="#b9c7c5" stroke-width="2.5"/>
    <line x1="296" y1="104" x2="296" y2="118" stroke="#b9c7c5" stroke-width="2.5"/>
    <line x1="316" y1="104" x2="316" y2="118" stroke="#b9c7c5" stroke-width="2.5"/>
    <line x1="336" y1="104" x2="336" y2="118" stroke="#b9c7c5" stroke-width="2.5"/>
    <text x="300" y="140" fill="#e8f0ef" font-size="10" font-weight="700" text-anchor="middle">HC-SR04 ultrason</text>
    <text x="300" y="154" fill="#a8c5c2" font-size="9" text-anchor="middle">distance / niveau 2 cm - 4 m</text>
    <text x="300" y="167" fill="#a8c5c2" font-size="9" text-anchor="middle">VCC · TRIG · ECHO · GND</text>
  </svg><div class="fig-cap">Fig. 7 — Les trois capteurs stars du module : LM35, DS18B20 et HC-SR04.</div></div>


  <h3>10.1 — Température : la thermistance NTC / le LM35</h3>
  <h4>Le LM35 (le plus simple pour débuter)</h4>
  <p>Trois pattes : 5V, sortie, GND. Il sort <strong>10 mV par °C</strong>, directement. Pas d'étalonnage.</p>
  <pre><code><span class="kw">int</span> brut = <span class="fn">analogRead</span>(<span class="kw">A0</span>);
<span class="kw">float</span> tension = brut * <span class="nb">5.0</span> / <span class="nb">1023.0</span>;
<span class="kw">float</span> tempC = tension * <span class="nb">100.0</span>;   <span class="cm">// 10 mV/°C → ×100</span></code></pre>
  <h4>La thermistance NTC (celle de nos machines)</h4>
  <p>Une <strong>NTC</strong> voit sa résistance <strong>diminuer quand la température monte</strong>. C'est LA technologie des sondes de température moteur, huile hydraulique, compresseur… Sur Arduino, on la monte en diviseur de tension avec une résistance fixe de 10 kΩ :</p>
  <div class="schema"><span class="lbl">Montage diviseur NTC</span>
  5V ──[R fixe 10kΩ]──┬──► A0
                      │
                    [NTC 10kΩ]
                      │
                     GND
  Chaud → R(NTC) baisse → tension sur A0 baisse</div>
  <div class="exemple">
    <div class="box-t">Exemple concret — diagnostic sonde</div>
    <p>C'est exactement pour ça qu'au multimètre, une sonde de température moteur débranchée doit afficher une résistance qui <strong>correspond au tableau constructeur</strong> (ex. ~2,5 kΩ à 20 °C, ~300 Ω à 80 °C selon modèle). Si tu comprends le montage NTC sur Arduino, tu comprends le circuit d'entrée du calculateur — et tu sais pourquoi une sonde en court-circuit affiche une température délirante à l'écran.</p>
  </div>

  <h3>10.2 — Le DS18B20 : la sonde numérique de précision</h3>
  <p>Sonde étanche, précision ±0,5 °C, plusieurs sondes sur <strong>un seul fil</strong> de données (bus 1-Wire). Il faut une résistance de 4,7 kΩ entre la pin data et le 5V, et deux bibliothèques :</p>
  <pre><code><span class="kw">#include</span> <span class="st">&lt;OneWire.h&gt;</span>
<span class="kw">#include</span> <span class="st">&lt;DallasTemperature.h&gt;</span>

OneWire bus(<span class="nb">2</span>);                    <span class="cm">// data sur D2</span>
DallasTemperature sondes(&bus);

<span class="kw">void</span> <span class="fn">setup</span>() {
  Serial.<span class="fn">begin</span>(<span class="nb">9600</span>);
  sondes.<span class="fn">begin</span>();
}

<span class="kw">void</span> <span class="fn">loop</span>() {
  sondes.<span class="fn">requestTemperatures</span>();
  Serial.<span class="fn">println</span>(sondes.<span class="fn">getTempCByIndex</span>(<span class="nb">0</span>));
  <span class="fn">delay</span>(<span class="nb">1000</span>);
}</code></pre>
  <div class="astuce">
    <div class="box-t">Installer une bibliothèque</div>
    <p>IDE → menu <strong>Croquis → Inclure une bibliothèque → Gérer les bibliothèques</strong> → tape le nom (ex. « DallasTemperature ») → Installer. Les bibliothèques sont des blocs de code écrits par la communauté : tu profites du travail des autres, comme un catalogue de pièces standard.</p>
  </div>

  <h3>10.3 — Distance : l'ultrason HC-SR04</h3>
  <p>Il envoie un « ping » ultrasonore et mesure le temps de l'écho. Portée 2 cm à 4 m.</p>
  <pre><code><span class="kw">const int</span> TRIG = <span class="nb">9</span>, ECHO = <span class="nb">10</span>;

<span class="kw">void</span> <span class="fn">setup</span>() {
  <span class="fn">pinMode</span>(TRIG, <span class="kw">OUTPUT</span>); <span class="fn">pinMode</span>(ECHO, <span class="kw">INPUT</span>);
  Serial.<span class="fn">begin</span>(<span class="nb">9600</span>);
}

<span class="kw">void</span> <span class="fn">loop</span>() {
  <span class="fn">digitalWrite</span>(TRIG, <span class="kw">LOW</span>);  <span class="fn">delayMicroseconds</span>(<span class="nb">2</span>);
  <span class="fn">digitalWrite</span>(TRIG, <span class="kw">HIGH</span>); <span class="fn">delayMicroseconds</span>(<span class="nb">10</span>);
  <span class="fn">digitalWrite</span>(TRIG, <span class="kw">LOW</span>);
  <span class="kw">long</span> duree = <span class="fn">pulseIn</span>(ECHO, <span class="kw">HIGH</span>);      <span class="cm">// µs aller-retour</span>
  <span class="kw">float</span> cm = duree * <span class="nb">0.0343</span> / <span class="nb">2</span>;         <span class="cm">// vitesse du son</span>
  Serial.<span class="fn">println</span>(cm);
  <span class="fn">delay</span>(<span class="nb">200</span>);
}</code></pre>
  <div class="exemple">
    <div class="box-t">Exemple concret</div>
    <p>Applications directes à l'atelier : <strong>mesure de niveau sans contact</strong> dans une cuve de gasoil ou d'huile usagée (le capteur regarde la surface depuis le haut), détection de présence d'un véhicule dans une baie, alarme de recul. Le principe temps-de-vol est aussi celui des capteurs de niveau à ultrasons industriels.</p>
  </div>

  <h3>10.4 — Vibration et environnement : le tour d'horizon</h3>
  <div class="tbl-wrap"><table>
    <tr><th>Capteur</th><th>Mesure</th><th>Interface</th><th>Usage terrain</th></tr>
    <tr><td>DHT22</td><td>Température + humidité air</td><td>1 fil numérique</td><td>Ambiance local électrique, container</td></tr>
    <tr><td>SW-420</td><td>Vibration (tout-ou-rien)</td><td>Numérique</td><td>Détection machine en marche / choc</td></tr>
    <tr><td>MPU6050</td><td>Accélérations 3 axes + gyro</td><td>I2C</td><td>Analyse vibratoire simple, inclinaison</td></tr>
    <tr><td>ACS712</td><td>Courant (A)</td><td>Analogique</td><td>Surveillance conso d'un moteur électrique</td></tr>
    <tr><td>Diviseur + zener</td><td>Tension batterie</td><td>Analogique</td><td>Surveillance batterie 12/24 V (avec diviseur !)</td></tr>
  </table></div>
  <div class="attention">
    <div class="box-t">Rappel vital</div>
    <p>Pour mesurer une tension supérieure à 5 V (batterie 12 V ou 24 V), il faut <strong>obligatoirement un pont diviseur de tension</strong> pour ramener le signal sous 5 V. Deux résistances (ex. 47 kΩ / 10 kΩ pour du 24 V max) et la loi d'Ohm du module 2. Brancher du 24 V en direct sur A0 = pin morte instantanément.</p>
  </div>

  <h3>10.5 — L'écran LCD I2C : afficher sans PC</h3>
  <p>Un écran LCD 16×2 avec module I2C se branche en 4 fils : 5V, GND, <span class="pin-badge">SDA→A4</span>, <span class="pin-badge">SCL→A5</span>. Bibliothèque « LiquidCrystal I2C » :</p>
  <pre><code><span class="kw">#include</span> <span class="st">&lt;LiquidCrystal_I2C.h&gt;</span>
LiquidCrystal_I2C lcd(<span class="nb">0x27</span>, <span class="nb">16</span>, <span class="nb">2</span>);

<span class="kw">void</span> <span class="fn">setup</span>() {
  lcd.<span class="fn">init</span>();
  lcd.<span class="fn">backlight</span>();
  lcd.<span class="fn">print</span>(<span class="st">"Temp huile:"</span>);
}

<span class="kw">void</span> <span class="fn">loop</span>() {
  lcd.<span class="fn">setCursor</span>(<span class="nb">0</span>, <span class="nb">1</span>);      <span class="cm">// colonne 0, ligne 2</span>
  lcd.<span class="fn">print</span>(temperature);
  lcd.<span class="fn">print</span>(<span class="st">" C  "</span>);
  <span class="fn">delay</span>(<span class="nb">500</span>);
}</code></pre>
  <p>L'I2C est un <strong>bus deux fils</strong> (données + horloge) qui accepte plusieurs périphériques chacun avec son adresse (ici 0x27). C'est un cousin simplifié des bus de communication qu'on retrouve partout en électronique embarquée.</p>

  <div class="recap">
    <div class="r-t">À retenir</div>
    <ul>
      <li>LM35 = simple (10 mV/°C). NTC = la techno de nos sondes machines, en diviseur de tension.</li>
      <li>DS18B20 = précis, étanche, plusieurs sondes sur un fil.</li>
      <li>HC-SR04 = distance/niveau par temps de vol.</li>
      <li>Tension &gt; 5 V à mesurer → <strong>pont diviseur obligatoire</strong>.</li>
      <li>LCD I2C = affichage autonome en 4 fils (A4/A5).</li>
    </ul>
  </div>

  <div class="quiz">
    <div class="q-t">Quiz Module 10</div>
    <div class="q-q">Une NTC est plongée dans de l'huile qui chauffe. Sa résistance :</div>
    <button class="q-opt" onclick="qz(this,false)">Augmente</button>
    <button class="q-opt" onclick="qz(this,true)">Diminue</button>
    <button class="q-opt" onclick="qz(this,false)">Ne change pas</button>
    <div class="q-exp">✅ NTC = Negative Temperature Coefficient : la résistance <strong>diminue</strong> quand la température monte. C'est pour ça qu'une sonde moteur affiche quelques centaines d'ohms à chaud et plusieurs kΩ à froid.</div>
  </div>
</section>
<!-- ============ MODULE 11 ============ -->
<section class="module" id="m11">
  <span class="mod-tag">Module 11 / 12</span>
  <h2>Projet complet : <span>surveillance d'un équipement</span></h2>
  <p class="mod-intro">On assemble TOUT : un système de surveillance de température avec seuils étagés, alarme, relais de ventilation et affichage. Un vrai mini-système de protection, comme sur une machine.</p>

  <h3>11.1 — Le cahier des charges</h3>
  <p>Surveiller la température d'un équipement (compresseur d'atelier, groupe électrogène, moteur électrique de pompe) :</p>
  <ul>
    <li><strong>&lt; 60 °C</strong> : tout va bien, LED verte.</li>
    <li><strong>60-80 °C</strong> : zone d'attention, LED orange + démarrage ventilation (relais).</li>
    <li><strong>&gt; 80 °C</strong> : alarme, LED rouge clignotante + buzzer + ventilation.</li>
    <li>Affichage permanent de la température sur le moniteur série.</li>
    <li>Un bouton pour <strong>acquitter</strong> le buzzer (l'alarme visuelle reste).</li>
  </ul>
  <div class="enclair">
    <div class="box-t">En clair</div>
    <p>C'est l'architecture standard de toute protection machine : <strong>pré-alarme → action corrective automatique → alarme + acquittement opérateur</strong>. Un système de protection de température compresseur suit exactement cette logique à trois étages. Tu construis une version miniature du vrai.</p>
  </div>

  <h3>11.2 — Le câblage</h3>
  <div class="tbl-wrap"><table>
    <tr><th>Élément</th><th>Pin Arduino</th><th>Notes</th></tr>
    <tr><td>Sonde LM35 (ou NTC en diviseur)</td><td><span class="pin-badge">A0</span></td><td>5V / A0 / GND</td></tr>
    <tr><td>LED verte + R 220 Ω</td><td><span class="pin-badge">D4</span></td><td>→ GND</td></tr>
    <tr><td>LED orange + R 220 Ω</td><td><span class="pin-badge">D5</span></td><td>→ GND</td></tr>
    <tr><td>LED rouge + R 220 Ω</td><td><span class="pin-badge">D6</span></td><td>→ GND</td></tr>
    <tr><td>Buzzer actif</td><td><span class="pin-badge">D7</span></td><td>+ sur D7, − sur GND</td></tr>
    <tr><td>Module relais (ventilateur)</td><td><span class="pin-badge">D8</span></td><td>VCC/GND/IN</td></tr>
    <tr><td>Bouton acquittement</td><td><span class="pin-badge">D2</span></td><td>INPUT_PULLUP → GND</td></tr>
  </table></div>

  <h3>11.3 — Le code complet, commenté</h3>
  <pre><code><span class="cm">/* =========================================================
   SURVEILLANCE TEMPÉRATURE ÉQUIPEMENT — v1.0
   3 seuils, ventilation auto, alarme acquittable
   ========================================================= */</span>

<span class="cm">// ---- Broches ----</span>
<span class="kw">const int</span> PIN_SONDE   = <span class="kw">A0</span>;
<span class="kw">const int</span> PIN_LED_V   = <span class="nb">4</span>;
<span class="kw">const int</span> PIN_LED_O   = <span class="nb">5</span>;
<span class="kw">const int</span> PIN_LED_R   = <span class="nb">6</span>;
<span class="kw">const int</span> PIN_BUZZER  = <span class="nb">7</span>;
<span class="kw">const int</span> PIN_RELAIS  = <span class="nb">8</span>;
<span class="kw">const int</span> PIN_ACQUIT  = <span class="nb">2</span>;

<span class="cm">// ---- Seuils (à adapter à ton équipement) ----</span>
<span class="kw">const float</span> SEUIL_VENTIL = <span class="nb">60.0</span>;
<span class="kw">const float</span> SEUIL_ALARME = <span class="nb">80.0</span>;

<span class="cm">// ---- Variables d'état ----</span>
<span class="kw">float</span> temperature   = <span class="nb">0</span>;
<span class="kw">bool</span>  buzzerAcquitte = <span class="kw">false</span>;
<span class="kw">unsigned long</span> tMesure = <span class="nb">0</span>;
<span class="kw">unsigned long</span> tCligno = <span class="nb">0</span>;
<span class="kw">bool</span>  etatCligno = <span class="kw">false</span>;

<span class="kw">void</span> <span class="fn">setup</span>() {
  <span class="fn">pinMode</span>(PIN_LED_V,  <span class="kw">OUTPUT</span>);
  <span class="fn">pinMode</span>(PIN_LED_O,  <span class="kw">OUTPUT</span>);
  <span class="fn">pinMode</span>(PIN_LED_R,  <span class="kw">OUTPUT</span>);
  <span class="fn">pinMode</span>(PIN_BUZZER, <span class="kw">OUTPUT</span>);
  <span class="fn">pinMode</span>(PIN_RELAIS, <span class="kw">OUTPUT</span>);
  <span class="fn">pinMode</span>(PIN_ACQUIT, <span class="kw">INPUT_PULLUP</span>);
  Serial.<span class="fn">begin</span>(<span class="nb">9600</span>);
  Serial.<span class="fn">println</span>(<span class="st">"Surveillance temperature - demarrage"</span>);
}

<span class="cm">// ---- Lecture sonde LM35, moyennée sur 10 mesures ----</span>
<span class="kw">float</span> <span class="fn">lireTemperature</span>() {
  <span class="kw">long</span> somme = <span class="nb">0</span>;
  <span class="kw">for</span> (<span class="kw">int</span> i = <span class="nb">0</span>; i &lt; <span class="nb">10</span>; i++) {
    somme += <span class="fn">analogRead</span>(PIN_SONDE);
    <span class="fn">delay</span>(<span class="nb">2</span>);
  }
  <span class="kw">float</span> brut = somme / <span class="nb">10.0</span>;
  <span class="kw">return</span> brut * <span class="nb">5.0</span> / <span class="nb">1023.0</span> * <span class="nb">100.0</span>;  <span class="cm">// LM35 : 10 mV/°C</span>
}

<span class="kw">void</span> <span class="fn">loop</span>() {
  <span class="cm">// --- 1. Mesure toutes les 500 ms (sans bloquer) ---</span>
  <span class="kw">if</span> (<span class="fn">millis</span>() - tMesure &gt;= <span class="nb">500</span>) {
    tMesure = <span class="fn">millis</span>();
    temperature = <span class="fn">lireTemperature</span>();
    Serial.<span class="fn">print</span>(<span class="st">"Temp: "</span>);
    Serial.<span class="fn">print</span>(temperature, <span class="nb">1</span>);
    Serial.<span class="fn">println</span>(<span class="st">" C"</span>);
  }

  <span class="cm">// --- 2. Bouton d'acquittement ---</span>
  <span class="kw">if</span> (<span class="fn">digitalRead</span>(PIN_ACQUIT) == <span class="kw">LOW</span>) {
    buzzerAcquitte = <span class="kw">true</span>;
    <span class="fn">delay</span>(<span class="nb">50</span>);  <span class="cm">// anti-rebond</span>
  }

  <span class="cm">// --- 3. Logique à 3 étages ---</span>
  <span class="kw">if</span> (temperature &lt; SEUIL_VENTIL) {
    <span class="cm">// ZONE VERTE : normal</span>
    <span class="fn">digitalWrite</span>(PIN_LED_V, <span class="kw">HIGH</span>);
    <span class="fn">digitalWrite</span>(PIN_LED_O, <span class="kw">LOW</span>);
    <span class="fn">digitalWrite</span>(PIN_LED_R, <span class="kw">LOW</span>);
    <span class="fn">digitalWrite</span>(PIN_RELAIS, <span class="kw">LOW</span>);
    <span class="fn">digitalWrite</span>(PIN_BUZZER, <span class="kw">LOW</span>);
    buzzerAcquitte = <span class="kw">false</span>;   <span class="cm">// réarmement auto en zone verte</span>
  }
  <span class="kw">else if</span> (temperature &lt; SEUIL_ALARME) {
    <span class="cm">// ZONE ORANGE : ventilation forcée</span>
    <span class="fn">digitalWrite</span>(PIN_LED_V, <span class="kw">LOW</span>);
    <span class="fn">digitalWrite</span>(PIN_LED_O, <span class="kw">HIGH</span>);
    <span class="fn">digitalWrite</span>(PIN_LED_R, <span class="kw">LOW</span>);
    <span class="fn">digitalWrite</span>(PIN_RELAIS, <span class="kw">HIGH</span>);
    <span class="fn">digitalWrite</span>(PIN_BUZZER, <span class="kw">LOW</span>);
  }
  <span class="kw">else</span> {
    <span class="cm">// ZONE ROUGE : alarme</span>
    <span class="fn">digitalWrite</span>(PIN_LED_V, <span class="kw">LOW</span>);
    <span class="fn">digitalWrite</span>(PIN_LED_O, <span class="kw">LOW</span>);
    <span class="fn">digitalWrite</span>(PIN_RELAIS, <span class="kw">HIGH</span>);

    <span class="cm">// LED rouge clignotante avec millis()</span>
    <span class="kw">if</span> (<span class="fn">millis</span>() - tCligno &gt;= <span class="nb">300</span>) {
      tCligno = <span class="fn">millis</span>();
      etatCligno = !etatCligno;
      <span class="fn">digitalWrite</span>(PIN_LED_R, etatCligno);
    }

    <span class="cm">// Buzzer, sauf si acquitté</span>
    <span class="fn">digitalWrite</span>(PIN_BUZZER, buzzerAcquitte ? <span class="kw">LOW</span> : <span class="kw">HIGH</span>);
  }
}</code></pre>

  <h3>11.4 — Ce que ce code t'apprend</h3>
  <ul>
    <li><strong>Fonction personnalisée</strong> <code>lireTemperature()</code> : le code est rangé, réutilisable, lisible.</li>
    <li><strong>Moyennage de mesure</strong> (10 lectures) : filtre le bruit, comme le filtrage des entrées analogiques d'un calculateur.</li>
    <li><strong>millis() partout</strong> : la mesure, le clignotement et le bouton fonctionnent en parallèle, rien ne bloque.</li>
    <li><strong>Réarmement automatique</strong> en zone verte : l'acquittement ne reste pas coincé.</li>
    <li><strong>Hystérésis manquante</strong> — exprès ! Vois l'exercice ci-dessous.</li>
  </ul>

  <div class="exemple">
    <div class="box-t">Exercice — ajoute l'hystérésis</div>
    <p>Défaut actuel : à exactement 60,0 °C, le relais peut <strong>battre</strong> (ON/OFF/ON/OFF) au gré du bruit de mesure — le claquement de relais que tu connais bien sur les thermostats fatigués. Solution industrielle : l'<strong>hystérésis</strong>. Ventilation ON à 60 °C, mais OFF seulement en dessous de 55 °C. À toi de modifier le code (indice : mémorise l'état du ventilateur dans un <code>bool</code> et utilise deux seuils différents pour l'allumage et l'extinction).</p>
  </div>

  <h3>11.5 — Les extensions possibles</h3>
  <ol>
    <li><strong>Écran LCD I2C</strong> (module 10) pour un affichage autonome sans PC.</li>
    <li><strong>Compteur horaire</strong> : cumule le temps passé en zone rouge dans une variable <code>unsigned long</code> — précieuse info de maintenance.</li>
    <li><strong>Enregistrement EEPROM</strong> : sauvegarder la température max atteinte, même après coupure de courant (<code>EEPROM.write</code>).</li>
    <li><strong>Deuxième sonde</strong> : différentiel entrée/sortie d'un refroidisseur = état d'encrassement du radiateur. Ça, c'est déjà de la maintenance prédictive.</li>
  </ol>

  <div class="recap">
    <div class="r-t">À retenir</div>
    <ul>
      <li>Un projet réel = câblage propre + constantes en tête + fonctions dédiées + millis().</li>
      <li>Moyenner les mesures analogiques = toujours.</li>
      <li>L'hystérésis évite les battements de relais aux seuils.</li>
      <li>Ce squelette (mesure → seuils → actions → acquittement) sert pour TOUT système de surveillance.</li>
    </ul>
  </div>

  <div class="quiz">
    <div class="q-t">Quiz Module 11</div>
    <div class="q-q">Pourquoi moyenner 10 lectures analogiques au lieu d'une seule ?</div>
    <button class="q-opt" onclick="qz(this,false)">Pour aller plus vite</button>
    <button class="q-opt" onclick="qz(this,true)">Pour filtrer le bruit de mesure et stabiliser la valeur</button>
    <button class="q-opt" onclick="qz(this,false)">Parce que analogRead ne marche qu'une fois sur dix</button>
    <div class="q-exp">✅ Chaque lecture individuelle fluctue (bruit électrique, parasites). La moyenne lisse ces variations — même principe que le filtrage des entrées capteur dans un calculateur. Sans ça, tes seuils déclencheraient de façon erratique.</div>
  </div>
</section>

<!-- ============ MODULE 12 ============ -->
<section class="module" id="m12">
  <span class="mod-tag">Module 12 / 12</span>
  <h2>Et maintenant ? <span>La suite du parcours</span></h2>
  <p class="mod-intro">Tu as les fondations. Voici la carte routière pour transformer ces bases en compétences d'électronique industrielle et de maintenance 4.0.</p>

  <h3>12.1 — Récapitulatif de ce que tu maîtrises</h3>
  <div class="tbl-wrap"><table>
    <tr><th>Compétence</th><th>Fonctions clés</th></tr>
    <tr><td>Structure d'un programme</td><td><code>setup()</code>, <code>loop()</code></td></tr>
    <tr><td>Sorties numériques</td><td><code>pinMode</code>, <code>digitalWrite</code></td></tr>
    <tr><td>Entrées numériques</td><td><code>digitalRead</code>, <code>INPUT_PULLUP</code>, anti-rebond</td></tr>
    <tr><td>Mesure analogique</td><td><code>analogRead</code>, mise à l'échelle, moyennage</td></tr>
    <tr><td>Commande proportionnelle</td><td><code>analogWrite</code> (PWM)</td></tr>
    <tr><td>Logique</td><td><code>if/else</code>, <code>&&</code>, <code>||</code>, <code>for</code>, <code>while</code></td></tr>
    <tr><td>Diagnostic</td><td>Moniteur série, traceur, <code>millis()</code></td></tr>
    <tr><td>Capteurs &amp; bus</td><td>NTC, DS18B20 (1-Wire), LCD (I2C), bibliothèques</td></tr>
  </table></div>

  <h3>12.2 — Étape suivante n°1 : l'ESP32</h3>
  <p>Même environnement de programmation, mais avec <strong>WiFi et Bluetooth intégrés</strong>, plus de puissance, plus de mémoire. C'est la carte reine de l'IoT industriel : ton système de surveillance du module 11 peut envoyer ses mesures sur ton téléphone, vers un tableau de bord web, ou vers une base de données.</p>
  <div class="fig"><svg viewBox="0 0 340 190" xmlns="http://www.w3.org/2000/svg" font-family="sans-serif">
    <rect x="70" y="20" width="200" height="150" rx="10" fill="#0a1c1c" stroke="#2d8a85" stroke-width="3"/>
    <!-- zone antenne -->
    <rect x="120" y="26" width="100" height="26" rx="4" fill="#123434"/>
    <path d="M130 39 h12 v-7 h12 v14 h12 v-14 h12 v14 h12 v-14 h12 v7 h12" stroke="#f0a500" stroke-width="2.5" fill="none"/>
    <text x="170" y="66" fill="#a8c5c2" font-size="8.5" text-anchor="middle">antenne Wi-Fi / Bluetooth</text>
    <!-- blindage ESP32 -->
    <rect x="120" y="74" width="100" height="56" rx="4" fill="#8a9a98" stroke="#5f6f6d"/>
    <text x="170" y="100" fill="#0a1c1c" font-size="13" font-weight="900" text-anchor="middle">ESP32</text>
    <text x="170" y="116" fill="#2a3a38" font-size="8" text-anchor="middle">240 MHz · 2 cœurs</text>
    <!-- USB -->
    <rect x="146" y="152" width="48" height="20" rx="3" fill="#b9c7c5"/>
    <text x="170" y="165" fill="#333" font-size="8.5" font-weight="700" text-anchor="middle">USB</text>
    <!-- pins -->
    <g stroke="#f0a500" stroke-width="3">
      <line x1="70" y1="40" x2="54" y2="40"/><line x1="70" y1="58" x2="54" y2="58"/>
      <line x1="70" y1="76" x2="54" y2="76"/><line x1="70" y1="94" x2="54" y2="94"/>
      <line x1="70" y1="112" x2="54" y2="112"/><line x1="70" y1="130" x2="54" y2="130"/>
      <line x1="270" y1="40" x2="286" y2="40"/><line x1="270" y1="58" x2="286" y2="58"/>
      <line x1="270" y1="76" x2="286" y2="76"/><line x1="270" y1="94" x2="286" y2="94"/>
      <line x1="270" y1="112" x2="286" y2="112"/><line x1="270" y1="130" x2="286" y2="130"/>
    </g>
    <!-- badge 3.3V -->
    <rect x="6" y="78" width="44" height="30" rx="8" fill="#f0a500"/>
    <text x="28" y="92" fill="#1a1200" font-size="10" font-weight="900" text-anchor="middle">3,3 V</text>
    <text x="28" y="103" fill="#1a1200" font-size="8" font-weight="700" text-anchor="middle">logique !</text>
    <text x="308" y="90" fill="#6fd3c7" font-size="9" font-weight="700" text-anchor="middle" transform="rotate(90 308 90)">GPIO ×30+</text>
  </svg><div class="fig-cap">Fig. 8 — L'ESP32 : Wi-Fi et Bluetooth intégrés, mais logique 3,3 V — pas 5 V tolérant.</div></div>

  <div class="attention">
    <div class="box-t">Différence critique</div>
    <p>L'ESP32 travaille en <strong>3,3 V</strong>, pas en 5 V ! Ses pins ne tolèrent pas le 5 V. Vérifie toujours la tension logique avant de recycler un montage UNO. C'est un réflexe général : la cohabitation de domaines de tension (1,8 V / 3,3 V / 5 V) est partout dans l'électronique moderne — même les cartes Arduino récentes mélangent plusieurs domaines logiques.</p>
  </div>

  <h3>12.3 — Étape suivante n°2 : le bus CAN</h3>
  <p>Avec un module MCP2515 (ou une carte à contrôleur CAN intégré), ton Arduino peut <strong>écouter un bus CAN</strong> : trames, identifiants, données. Pour un technicien qui travaille sur des machines communicantes, c'est l'étape qui relie directement l'apprentissage Arduino au diagnostic des équipements réels : tu peux construire ton propre espion de bus, décoder des trames, comprendre physiquement ce que l'outil de diagnostic te montre.</p>

  <h3>12.4 — Étape suivante n°3 : vers la maintenance prédictive</h3>
  <ol>
    <li><strong>Collecter</strong> : Arduino/ESP32 + capteurs (température, vibration, courant) sur un équipement.</li>
    <li><strong>Historiser</strong> : envoi vers une carte SD, un serveur, ou un tableur.</li>
    <li><strong>Analyser</strong> : tendances, dérives, seuils dynamiques — c'est là que la data science entre en jeu.</li>
    <li><strong>Prédire</strong> : détecter la dérive AVANT la panne. Le graal de la maintenance 4.0.</li>
  </ol>
  <div class="enclair">
    <div class="box-t">En clair</div>
    <p>La chaîne complète : <strong>le capteur mesure → l'Arduino collecte → les données s'accumulent → l'analyse prédit</strong>. Chaque module de ce cours était une brique de cette chaîne. Un technicien qui maîtrise à la fois le terrain, l'électronique embarquée et l'analyse de données, c'est un profil rare et recherché.</p>
  </div>

  <h3>12.5 — Les bons réflexes pour progresser</h3>
  <ul>
    <li><strong>Un projet à la fois</strong>, du simple au complexe. Termine avant de commencer le suivant.</li>
    <li><strong>Câble hors tension</strong>, vérifie deux fois, alimente une fois.</li>
    <li><strong>Commente ton code</strong> : le toi de dans 6 mois te remerciera.</li>
    <li><strong>Serial.print est ton ami</strong> : au moindre doute, affiche.</li>
    <li><strong>Garde tes montages en photo</strong> et tes codes versionnés (GitHub) : ta bibliothèque personnelle de solutions.</li>
    <li><strong>Simule sur Wokwi</strong> quand tu n'as pas le matériel sous la main.</li>
  </ul>

  <h3>12.6 — Quiz final de certification 🎓</h3>
  <div class="quiz">
    <div class="q-t">Question 1/4</div>
    <div class="q-q">Quelle fonction configure une pin en entrée avec résistance de rappel interne ?</div>
    <button class="q-opt" onclick="qz(this,false)"><code>digitalRead(pin, PULLUP)</code></button>
    <button class="q-opt" onclick="qz(this,true)"><code>pinMode(pin, INPUT_PULLUP)</code></button>
    <button class="q-opt" onclick="qz(this,false)"><code>analogWrite(pin, HIGH)</code></button>
    <div class="q-exp">✅ <code>pinMode(pin, INPUT_PULLUP)</code> : entrée + pull-up interne. Le bouton se câble alors simplement vers GND.</div>
  </div>
  <div class="quiz">
    <div class="q-t">Question 2/4</div>
    <div class="q-q">analogWrite(9, 128) produit :</div>
    <button class="q-opt" onclick="qz(this,false)">Une tension continue de 128 V</button>
    <button class="q-opt" onclick="qz(this,true)">Un signal PWM à ~50 % de rapport cyclique</button>
    <button class="q-opt" onclick="qz(this,false)">Une lecture de la pin 9</button>
    <div class="q-exp">✅ 128/255 ≈ 50 %. Le PWM découpe le 5 V en impulsions — même principe que la commande des électrovannes proportionnelles.</div>
  </div>
  <div class="quiz">
    <div class="q-t">Question 3/4</div>
    <div class="q-q">Pour mesurer la tension d'une batterie 24 V avec l'Arduino, il faut :</div>
    <button class="q-opt" onclick="qz(this,false)">Brancher la batterie directement sur A0</button>
    <button class="q-opt" onclick="qz(this,true)">Un pont diviseur de tension pour ramener le signal sous 5 V</button>
    <button class="q-opt" onclick="qz(this,false)">Utiliser une pin PWM</button>
    <div class="q-exp">✅ 24 V direct sur une pin = destruction immédiate. Le pont diviseur (deux résistances) ramène la tension dans la plage 0-5 V mesurable.</div>
  </div>
  <div class="quiz">
    <div class="q-t">Question 4/4</div>
    <div class="q-q">Pourquoi préférer millis() à delay() dans un système de surveillance ?</div>
    <button class="q-opt" onclick="qz(this,false)">millis() est plus précis pour les pauses</button>
    <button class="q-opt" onclick="qz(this,true)">delay() fige tout le programme, millis() permet de rester réactif sur toutes les tâches</button>
    <button class="q-opt" onclick="qz(this,false)">delay() consomme plus d'énergie</button>
    <div class="q-exp">✅ Pendant un delay(), plus rien n'est surveillé : boutons ignorés, alarmes retardées. Avec millis(), toutes les tâches tournent en parallèle — comme un vrai calculateur qui ne se fige jamais.</div>
  </div>

  <div class="hero-card">
    <div class="hc-big">🎓 Félicitations !</div>
    <div class="hc-lbl">Tu as terminé le cours complet Arduino débutant.<br>Prochaine étape : monte le projet du module 11 en vrai, puis passe à l'ESP32 et au bus CAN.</div>
  </div>
</section>
<!-- ============ NAVIGATION BAS ============ -->
<div class="nav-bot">
  <button class="nav-btn" id="btnPrev" onclick="go(-1)">◀ Préc.</button>
  <div class="nav-pos" id="navPos">1 / 12</div>
  <button class="nav-btn primary" id="btnNext" onclick="go(1)">Suiv. ▶</button>
</div>

<script>
/* ===== DONNÉES MODULES ===== */
const MODS = [
  {t:"C'est quoi Arduino ?", s:"Le concept, le trio E/T/S, la famille de cartes"},
  {t:"L'électricité de base", s:"Tension, courant, loi d'Ohm, limites de la carte"},
  {t:"Anatomie de la carte UNO", s:"Pins, alimentation, breadboard"},
  {t:"Premier programme : Blink", s:"IDE, setup/loop, téléversement"},
  {t:"Variables et calculs", s:"Types, constantes, conversions capteur"},
  {t:"Décider et répéter", s:"if/else, ET/OU, boucles for et while"},
  {t:"Boutons et contacts", s:"digitalRead, pull-up, anti-rebond, relais"},
  {t:"Le monde analogique", s:"analogRead, map(), PWM"},
  {t:"Le moniteur série", s:"Diagnostic, traceur, millis()"},
  {t:"Les capteurs indispensables", s:"NTC, DS18B20, ultrason, LCD I2C"},
  {t:"Projet : surveillance équipement", s:"Le système complet à 3 seuils"},
  {t:"La suite du parcours", s:"ESP32, bus CAN, prédictif + quiz final"}
];
let cur = 0;
const done = new Set();

/* ===== NAVIGATION ===== */
function render(){
  document.querySelectorAll('.module').forEach((m,i)=>m.classList.toggle('active', i===cur));
  document.getElementById('navPos').textContent = (cur+1)+" / "+MODS.length;
  document.getElementById('btnPrev').disabled = (cur===0);
  document.getElementById('btnNext').textContent = (cur===MODS.length-1) ? "Fin 🎓" : "Suiv. ▶";
  document.getElementById('pbar').style.width = ((cur+1)/MODS.length*100)+"%";
  window.scrollTo({top:0, behavior:'instant'});
  try{ localStorage.setItem('arduinoCoursePos', cur); }catch(e){}
}
function go(d){
  done.add(cur);
  cur = Math.max(0, Math.min(MODS.length-1, cur+d));
  buildMenu();
  render();
}
function goTo(i){
  cur = i;
  toggleMenu();
  render();
}

/* ===== MENU ===== */
function buildMenu(){
  const list = document.getElementById('menuList');
  list.innerHTML = MODS.map((m,i)=>
    `<div class="menu-item ${done.has(i)?'done':''}" onclick="goTo(${i})">
       <div class="num">${done.has(i)?'✓':(i+1)}</div>
       <div><div class="mi-t">${m.t}</div><div class="mi-s">${m.s}</div></div>
     </div>`).join('');
}
function toggleMenu(){
  document.getElementById('menu').classList.toggle('open');
}

/* ===== QUIZ ===== */
function qz(btn, correct){
  if(editing) return;
  const quiz = btn.closest('.quiz');
  quiz.querySelectorAll('.q-opt').forEach(b=>b.disabled=true);
  btn.classList.add(correct ? 'good' : 'bad');
  if(!correct){
    // montrer la bonne réponse
    quiz.querySelectorAll('.q-opt').forEach(b=>{
      if(b.getAttribute('onclick').includes('true')) b.classList.add('good');
    });
  }
  quiz.querySelector('.q-exp').classList.add('show');
}

/* ===== SWIPE (navigation tactile) ===== */
let sx=0, sy=0;
document.addEventListener('touchstart', e=>{
  sx=e.touches[0].clientX; sy=e.touches[0].clientY;
},{passive:true});
document.addEventListener('touchend', e=>{
  const dx=e.changedTouches[0].clientX-sx, dy=e.changedTouches[0].clientY-sy;
  if(!editMode && Math.abs(dx)>90 && Math.abs(dy)<60 && !document.getElementById('menu').classList.contains('open')){
    go(dx<0 ? 1 : -1);
  }
},{passive:true});


/* ===================================================
   MODE ÉDITION PROTÉGÉ
   - Déclenchement : 5 taps rapides sur le titre du header
   - Code d'accès : constante EDIT_CODE ci-dessous
   - Modifs sauvées en localStorage (cet appareil)
   - Export HTML = fichier avec modifs intégrées,
     à re-téléverser sur GitHub pour publier à tous
   =================================================== */
const EDIT_CODE = "GF-DRILL-2026";   // ← change ce code ici si besoin
let editMode = false;
const ORIGINALS = {};                 // contenu d'origine de chaque module
const LS_EDITS = 'arduinoCourseEdits';

function toast(msg){
  const t = document.getElementById('editToast');
  t.textContent = msg;
  t.classList.add('show');
  setTimeout(()=>t.classList.remove('show'), 2200);
}

/* --- Déclencheur secret : 5 taps sur le titre en < 3 s --- */
let tapCount = 0, tapTimer = null;
document.getElementById('courseTitle').addEventListener('click', ()=>{
  tapCount++;
  clearTimeout(tapTimer);
  tapTimer = setTimeout(()=>tapCount=0, 3000);
  if(tapCount >= 5){
    tapCount = 0;
    askEditCode();
  }
});

function askEditCode(){
  if(editMode){ exitEdit(); return; }
  const code = prompt("🔐 Code d'accès au mode édition :");
  if(code === null) return;
  if(code === EDIT_CODE){
    enterEdit();
  } else {
    toast("❌ Code incorrect");
  }
}

function enterEdit(){
  editMode = true;
  document.body.classList.add('editing');
  document.querySelectorAll('.module').forEach(m=>{
    m.setAttribute('contenteditable','true');
    m.setAttribute('spellcheck','false');
  });
  toast("✏️ Mode édition activé");
}

function exitEdit(){
  editMode = false;
  document.body.classList.remove('editing');
  document.querySelectorAll('.module').forEach(m=>{
    m.removeAttribute('contenteditable');
    m.removeAttribute('spellcheck');
  });
  toast("🔒 Mode édition quitté");
}

/* --- Sauvegarde locale de tous les modules --- */
function saveEdits(){
  const edits = {};
  document.querySelectorAll('.module').forEach(m=>{
    if(m.innerHTML !== ORIGINALS[m.id]) edits[m.id] = m.innerHTML;
  });
  try{
    localStorage.setItem(LS_EDITS, JSON.stringify(edits));
    const n = Object.keys(edits).length;
    toast(n ? "💾 Enregistré ("+n+" module(s) modifié(s))" : "💾 Aucune modification à enregistrer");
  }catch(e){
    toast("⚠️ Échec sauvegarde (mémoire pleine ?)");
  }
}

/* --- Rétablir le module affiché à sa version d'origine --- */
function resetModule(){
  const m = document.querySelector('.module.active');
  if(!m) return;
  if(!confirm("Rétablir ce module à sa version d'origine ?")) return;
  m.innerHTML = ORIGINALS[m.id];
  saveEditsSilent();
  toast("↩️ Module rétabli");
}
function saveEditsSilent(){
  const edits = {};
  document.querySelectorAll('.module').forEach(mm=>{
    if(mm.innerHTML !== ORIGINALS[mm.id]) edits[mm.id] = mm.innerHTML;
  });
  try{ localStorage.setItem(LS_EDITS, JSON.stringify(edits)); }catch(e){}
}

/* --- Restaurer les modifs sauvées au chargement --- */
function loadEdits(){
  document.querySelectorAll('.module').forEach(m=>{
    ORIGINALS[m.id] = m.innerHTML;   // version d'origine du fichier
  });
  try{
    const saved = JSON.parse(localStorage.getItem(LS_EDITS) || '{}');
    for(const id in saved){
      const m = document.getElementById(id);
      if(m) m.innerHTML = saved[id];
    }
  }catch(e){}
}

/* --- Export HTML : fichier complet avec modifs intégrées --- */
function exportHTML(){
  saveEditsSilent();
  const clone = document.documentElement.cloneNode(true);

  // Nettoyage : sortir du mode édition dans la copie
  clone.querySelector('body').classList.remove('editing');
  clone.querySelectorAll('.module').forEach(m=>{
    m.removeAttribute('contenteditable');
    m.removeAttribute('spellcheck');
  });
  // Réinitialiser les quiz répondus
  clone.querySelectorAll('.q-opt').forEach(b=>{
    b.disabled = false;
    b.classList.remove('good','bad');
  });
  clone.querySelectorAll('.q-exp').forEach(x=>x.classList.remove('show'));
  // Masquer bannière/toast dans la copie
  const eb = clone.querySelector('#editBanner'); if(eb) eb.style.display='';
  const et = clone.querySelector('#editToast'); if(et){ et.classList.remove('show'); et.textContent=''; }

  const html = '<!DOCTYPE html>\n' + clone.outerHTML;
  const blob = new Blob([html], {type:'text/html'});
  const url = URL.createObjectURL(blob);
  const a = document.createElement('a');
  a.href = url;
  a.download = 'cours-arduino-debutant.html';
  document.body.appendChild(a);
  a.click();
  a.remove();
  setTimeout(()=>URL.revokeObjectURL(url), 4000);
  toast("📤 Fichier exporté — remplace-le sur GitHub pour publier");
}


/* ===== MODE ÉDITION (accès protégé — réservé à l'administrateur) ===== */
const DEFAULT_HASH='2e6htn7ach6'; /* code par défaut : admin2026 — à changer via 🔑 */
function cyrb53(str,seed=0){let h1=0xdeadbeef^seed,h2=0x41c6ce57^seed;for(let i=0,ch;i<str.length;i++){ch=str.charCodeAt(i);h1=Math.imul(h1^ch,2654435761);h2=Math.imul(h2^ch,1597334677);}h1=Math.imul(h1^(h1>>>16),2246822507);h1^=Math.imul(h2^(h2>>>13),3266489909);h2=Math.imul(h2^(h2>>>16),2246822507);h2^=Math.imul(h1^(h1>>>13),3266489909);return(4294967296*(2097151&h2)+(h1>>>0)).toString(36);}
function editHash(){try{return localStorage.getItem('ardEditHash')||DEFAULT_HASH;}catch(e){return DEFAULT_HASH;}}
let editing=false;

function editGate(){
  if(editing){editQuit();return;}
  const c=prompt("🔒 Code d'accès édition :");
  if(c===null)return;
  if(cyrb53(c)===editHash()){enterEdit();}
  else alert("Code incorrect.");
}
function enterEdit(){
  editing=true;
  document.body.classList.add('editing');
  document.getElementById('editBar').style.display='flex';
  document.querySelectorAll('.module').forEach(m=>m.setAttribute('contenteditable','true'));
}
function editQuit(){
  editing=false;
  document.body.classList.remove('editing');
  document.getElementById('editBar').style.display='none';
  document.querySelectorAll('.module').forEach(m=>m.removeAttribute('contenteditable'));
}
function editSave(){
  const data={};
  document.querySelectorAll('.module').forEach(m=>data[m.id]=m.innerHTML);
  try{
    localStorage.setItem('ardCourseEdits',JSON.stringify(data));
    alert("✅ Enregistré sur cet appareil.\n\nPour publier à l'équipe : ⬇️ Exporter, puis remplace le fichier sur GitHub.");
  }catch(e){alert("Erreur d'enregistrement : "+e);}
}
function editApply(){
  try{
    const raw=localStorage.getItem('ardCourseEdits');
    if(!raw)return;
    const data=JSON.parse(raw);
    for(const id in data){const m=document.getElementById(id);if(m)m.innerHTML=data[id];}
  }catch(e){}
}
function editReset(){
  if(confirm("Supprimer toutes les modifications locales et revenir à la version d'origine ?")){
    try{localStorage.removeItem('ardCourseEdits');}catch(e){}
    location.reload();
  }
}
function editCode(){
  const n=prompt("🔑 Nouveau code d'accès (garde-le pour toi) :");
  if(!n)return;
  try{
    localStorage.setItem('ardEditHash',cyrb53(n));
    alert("Code changé sur cet appareil.\nExporte le fichier : le nouveau code sera intégré à la version publiée.");
  }catch(e){}
}
function editExport(){
  const clone=document.documentElement.cloneNode(true);
  clone.querySelectorAll('[contenteditable]').forEach(m=>m.removeAttribute('contenteditable'));
  const bar=clone.querySelector('#editBar'); if(bar)bar.style.display='none';
  const bd=clone.querySelector('body'); if(bd)bd.classList.remove('editing');
  clone.querySelectorAll('.q-opt').forEach(b=>{b.removeAttribute('disabled');b.classList.remove('good','bad');});
  clone.querySelectorAll('.q-exp').forEach(x=>x.classList.remove('show'));
  clone.querySelectorAll('.module').forEach((m,i)=>m.classList.toggle('active',i===0));
  const mn=clone.querySelector('#menu'); if(mn)mn.classList.remove('open');
  let out='<!DOCTYPE html>\n'+clone.outerHTML;
  out=out.replace(/const DEFAULT_HASH='[^']*'/, "const DEFAULT_HASH='"+editHash()+"'");
  const blob=new Blob([out],{type:'text/html'});
  const a=document.createElement('a');
  a.href=URL.createObjectURL(blob);
  a.download='cours-arduino-debutant.html';
  document.body.appendChild(a); a.click(); a.remove();
  setTimeout(()=>URL.revokeObjectURL(a.href),3000);
}

/* ===== INIT ===== */
try{
  const saved = parseInt(localStorage.getItem('arduinoCoursePos'));
  if(!isNaN(saved) && saved>=0 && saved<MODS.length){ cur=saved; for(let i=0;i<saved;i++) done.add(i); }
}catch(e){}
loadEdits();
editApply();
buildMenu();
render();
</script>
</body>
</html>
