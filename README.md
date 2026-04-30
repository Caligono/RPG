<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Ficha de Personagem</title>
<link href="https://fonts.googleapis.com/css2?family=IM+Fell+English:ital@0;1&family=Courier+Prime:ital,wght@0,400;0,700;1,400&display=swap" rel="stylesheet">
<style>
*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

:root {
  --ink: #0d0d0d;
  --paper: #f9f6f0;
  --paper-alt: #f0ece3;
  --rule: 1px solid #0d0d0d;
  --rule-thick: 2px solid #0d0d0d;
  --muted: #777;
  --fd: 'IM Fell English', serif;
  --fm: 'Courier Prime', monospace;
}

body {
  background: #e8e3d9;
  color: var(--ink);
  font-family: var(--fm);
  font-size: 13px;
  padding: 24px 16px 48px;
  min-height: 100vh;
}

.sheet {
  max-width: 960px;
  margin: 0 auto;
  background: var(--paper);
  border: var(--rule-thick);
  box-shadow: 4px 4px 0 #0d0d0d;
}

.hdr {
  border-bottom: var(--rule-thick);
  display: grid;
  grid-template-columns: 1fr auto 1fr;
  align-items: center;
  padding: 20px 28px;
  gap: 16px;
}
.hdr-left { display: flex; flex-direction: column; gap: 4px; }
.hdr-badge {
  font-size: 9px; letter-spacing: .25em; text-transform: uppercase;
  color: var(--muted); font-family: var(--fm);
}
.hdr-title {
  font-family: var(--fd);
  font-size: 30px;
  letter-spacing: .05em;
  text-align: center;
}
.hdr-right {
  display: flex; flex-direction: column; align-items: flex-end; gap: 4px;
}
.aura-label {
  font-size: 9px; letter-spacing: .2em; text-transform: uppercase; color: var(--muted);
}
.aura-val {
  width: 72px;
  border: var(--rule-thick);
  background: var(--paper);
  font-family: var(--fm);
  font-size: 22px; font-weight: 700;
  text-align: center;
  padding: 4px 0; outline: none;
}
.aura-val:focus { background: var(--paper-alt); }

.sec-title {
  display: flex; align-items: center; justify-content: space-between;
  padding: 6px 14px;
  background: var(--ink);
  color: #f9f6f0;
  font-family: var(--fd);
  font-size: 11px; letter-spacing: .2em; text-transform: uppercase;
}
.sec-title button {
  background: transparent; border: 1px solid rgba(255,255,255,.35);
  color: #f9f6f0; font-family: var(--fm); font-size: 10px;
  padding: 2px 8px; cursor: pointer; letter-spacing: .1em;
  transition: background .1s;
}
.sec-title button:hover { background: rgba(255,255,255,.15); }

.main {
  display: grid;
  grid-template-columns: 230px 1fr;
}
.col-l { border-right: var(--rule-thick); }

.field-wrap { padding: 10px 14px; border-bottom: var(--rule); }
.field-wrap:last-child { border-bottom: none; }
.field-label {
  font-size: 9px; letter-spacing: .2em; text-transform: uppercase;
  color: var(--muted); margin-bottom: 4px;
}
.field-inp {
  width: 100%; border: none; border-bottom: var(--rule);
  background: transparent; font-family: var(--fm); font-size: 13px;
  padding: 2px 0; outline: none; color: var(--ink);
}
.field-inp:focus { background: var(--paper-alt); }
/* ─── TEXTAREA BASE: overflow oculto p/ auto-shrink funcionar ─── */
textarea {
  overflow: hidden;
}

.field-textarea {
  width: 100%; border: none;
  background: transparent; font-family: var(--fm); font-size: 12px;
  padding: 4px 0; outline: none; resize: vertical; line-height: 1.6;
  min-height: 48px; color: var(--ink);
}
.field-textarea:focus { background: var(--paper-alt); }

.attr-row {
  display: flex; align-items: center; justify-content: space-between;
  padding: 8px 14px; border-bottom: var(--rule);
}
.attr-row:last-child { border-bottom: none; }
.attr-name { font-family: var(--fd); font-size: 14px; }
.attr-note { font-size: 10px; color: var(--muted); font-style: italic; display: block; }
.ctrl { display: flex; align-items: center; }
.ctrl-btn {
  width: 26px; height: 26px; border: var(--rule);
  background: var(--paper); font-size: 16px; font-weight: 700;
  cursor: pointer; font-family: var(--fm); display: flex;
  align-items: center; justify-content: center;
  transition: background .1s;
}
.ctrl-btn:hover { background: var(--ink); color: var(--paper); }
.ctrl-val {
  width: 38px; height: 26px;
  border-top: var(--rule); border-bottom: var(--rule);
  border-left: none; border-right: none;
  text-align: center; font-family: var(--fm); font-size: 15px; font-weight: 700;
  background: var(--paper); outline: none;
}
.ctrl-val:focus { background: var(--paper-alt); }

.stat-row {
  display: grid; grid-template-columns: 1fr auto;
  align-items: center; padding: 9px 14px; border-bottom: var(--rule); gap: 8px;
}
.stat-row:last-child { border-bottom: none; }
.stat-label { font-family: var(--fd); font-size: 13px; }
.stat-sub { font-size: 10px; color: var(--muted); font-style: italic; }
.stat-val { font-size: 20px; font-weight: 700; min-width: 32px; text-align: right; }

.tracker-grid { display: grid; grid-template-columns: 1fr 1fr; }
.tracker-item { padding: 10px 14px; border-bottom: var(--rule); }
.tracker-item:first-child { border-right: var(--rule); }
.tracker-lbl { font-size: 9px; letter-spacing: .2em; text-transform: uppercase; color: var(--muted); margin-bottom: 6px; }
.tracker-ctrl { display: flex; align-items: center; }
.t-btn {
  width: 28px; height: 28px; border: var(--rule);
  background: var(--paper); font-size: 18px; font-weight: 700;
  cursor: pointer; font-family: var(--fm); display: flex;
  align-items: center; justify-content: center;
  transition: background .1s;
}
.t-btn:hover { background: var(--ink); color: var(--paper); }
.t-cur {
  width: 50px; height: 28px;
  border-top: var(--rule); border-bottom: var(--rule);
  border-left: none; border-right: none;
  text-align: center; font-family: var(--fm); font-size: 17px; font-weight: 700;
  background: var(--paper); outline: none;
}
.t-cur:focus { background: var(--paper-alt); }
.tracker-max { font-size: 11px; color: var(--muted); margin-left: 8px; }
.tracker-note { margin-top: 6px; }

.money-wrap { padding: 10px 14px; }
.money-row { display: flex; align-items: center; gap: 6px; margin-top: 6px; }
.money-sym { font-size: 15px; font-weight: 700; }
.money-inp {
  flex: 1; border: none; border-bottom: var(--rule);
  background: transparent; font-family: var(--fm); font-size: 16px; font-weight: 700;
  padding: 2px 6px; outline: none; text-align: right;
}
.money-inp:focus { background: var(--paper-alt); }

.col-r { display: flex; flex-direction: column; }

.char-grid-3 { display: grid; grid-template-columns: 1fr 1fr 1fr; border-bottom: var(--rule); }
.char-grid-2 { display: grid; grid-template-columns: 1fr 1fr; border-bottom: var(--rule); }
.char-grid-1 { border-bottom: var(--rule); }
.char-grid-1:last-child { border-bottom: none; }
.cf { padding: 9px 14px; border-right: var(--rule); }
.cf:last-child { border-right: none; }
.cf-lbl { font-size: 9px; letter-spacing: .2em; text-transform: uppercase; color: var(--muted); margin-bottom: 4px; }
.cf-inp {
  width: 100%; border: none; border-bottom: var(--rule);
  background: transparent; font-family: var(--fm); font-size: 13px;
  padding: 2px 0; outline: none;
}
.cf-inp:focus { background: var(--paper-alt); }
.cf-ta {
  width: 100%; border: none;
  background: transparent; font-family: var(--fm); font-size: 12px;
  padding: 3px 0; outline: none; resize: vertical; line-height: 1.6;
  min-height: 40px;
}
.cf-ta:focus { background: var(--paper-alt); }

.sec-block { border-bottom: var(--rule-thick); }
.sec-block:last-child { border-bottom: none; }

.armor-equipped { display: grid; grid-template-columns: 2fr 1fr 2fr; }
.a-cell { padding: 9px 14px; border-right: var(--rule); }
.a-cell:last-child { border-right: none; }
.a-lbl { font-size: 9px; letter-spacing: .2em; text-transform: uppercase; color: var(--muted); margin-bottom: 4px; }
.a-inp {
  width: 100%; border: none; border-bottom: var(--rule);
  background: transparent; font-family: var(--fm); font-size: 13px;
  padding: 2px 0; outline: none;
}
.a-inp:focus { background: var(--paper-alt); }
.a-ta {
  width: 100%; border: none;
  background: transparent; font-family: var(--fm); font-size: 12px;
  padding: 3px 0; outline: none; resize: vertical; line-height: 1.6; min-height: 32px;
}
.a-ta:focus { background: var(--paper-alt); }
.armor-types { padding: 8px 14px; font-size: 11px; color: var(--muted); border-bottom: var(--rule); font-style: italic; }

.weapon-card {
  border-bottom: var(--rule); padding: 10px 14px;
  display: grid; gap: 6px;
}
.weapon-card:last-child { border-bottom: none; }
.weapon-row-top { display: grid; grid-template-columns: 2fr 1fr 1fr; gap: 8px; }
.weapon-row-mid { display: grid; grid-template-columns: 1fr 1fr 1fr; gap: 8px; }
.weapon-mini-lbl { font-size: 9px; letter-spacing: .15em; text-transform: uppercase; color: var(--muted); margin-bottom: 2px; }
.w-inp {
  width: 100%; border: none; border-bottom: var(--rule);
  background: transparent; font-family: var(--fm); font-size: 12px;
  padding: 2px 0; outline: none;
}
.w-inp:focus { background: var(--paper-alt); }
.w-ta {
  width: 100%; border: none;
  background: transparent; font-family: var(--fm); font-size: 11px;
  padding: 2px 0; outline: none; resize: vertical; min-height: 28px; line-height: 1.5;
}
.w-ta:focus { background: var(--paper-alt); }

.attack-card {
  border-bottom: var(--rule); padding: 10px 14px;
  display: grid; gap: 6px;
}
.attack-card:last-child { border-bottom: none; }

.spell-card {
  border-bottom: var(--rule); padding: 10px 14px;
  display: grid; gap: 6px;
}
.spell-card:last-child { border-bottom: none; }
.spell-row { display: grid; grid-template-columns: 2fr 1fr 1fr; gap: 8px; }
.sp-inp {
  width: 100%; border: none; border-bottom: var(--rule);
  background: transparent; font-family: var(--fm); font-size: 12px;
  padding: 2px 0; outline: none;
}
.sp-inp:focus { background: var(--paper-alt); }
.sp-ta {
  width: 100%; border: none;
  background: transparent; font-family: var(--fm); font-size: 11px;
  padding: 2px 0; outline: none; resize: vertical; min-height: 28px; line-height: 1.5;
}
.sp-ta:focus { background: var(--paper-alt); }

.inv-card {
  border-bottom: var(--rule); padding: 9px 14px;
  display: grid; grid-template-columns: 1fr auto; gap: 8px; align-items: start;
}
.inv-card:last-child { border-bottom: none; }
.inv-main { display: grid; gap: 4px; }
.i-inp {
  width: 100%; border: none; border-bottom: var(--rule);
  background: transparent; font-family: var(--fm); font-size: 12px;
  padding: 2px 0; outline: none;
}
.i-inp:focus { background: var(--paper-alt); }
.i-ta {
  width: 100%; border: none;
  background: transparent; font-family: var(--fm); font-size: 11px; color: var(--muted);
  padding: 2px 0; outline: none; resize: vertical; min-height: 24px; line-height: 1.5;
}
.i-ta:focus { background: var(--paper-alt); }
.inv-qty-lbl { font-size: 9px; letter-spacing: .15em; text-transform: uppercase; color: var(--muted); margin-bottom: 2px; }
.inv-qty-inp {
  width: 100%; border: none; border-bottom: var(--rule);
  background: transparent; font-family: var(--fm); font-size: 14px; font-weight: 700;
  padding: 2px 0; outline: none; text-align: center;
}
.inv-qty-inp:focus { background: var(--paper-alt); }

.notes-area {
  width: 100%; min-height: 120px;
  border: none; background: transparent;
  font-family: var(--fm); font-size: 12px;
  padding: 12px 14px; resize: vertical; outline: none; line-height: 1.8;
}
.notes-area:focus { background: var(--paper-alt); }

.add-btn {
  display: flex; align-items: center; gap: 8px;
  padding: 9px 14px; width: 100%;
  border: none; border-top: var(--rule);
  background: var(--paper-alt);
  font-family: var(--fm); font-size: 11px; letter-spacing: .1em;
  cursor: pointer; text-transform: uppercase; color: var(--muted);
  transition: background .1s, color .1s;
}
.add-btn:hover { background: var(--ink); color: var(--paper); }
.add-icon { width: 16px; height: 16px; border: 1px solid currentColor; display: flex; align-items: center; justify-content: center; font-size: 13px; font-weight: 700; flex-shrink: 0; }

.del-btn {
  background: transparent; border: none; cursor: pointer;
  font-size: 14px; color: var(--muted); padding: 2px 6px;
  font-family: var(--fm);
  transition: color .1s;
  align-self: start;
}
.del-btn:hover { color: var(--ink); }

.footer {
  border-top: var(--rule-thick);
  display: flex; align-items: center; justify-content: space-between;
  padding: 14px 28px;
  background: var(--paper-alt);
}
.footer-note { font-size: 10px; color: var(--muted); font-style: italic; }
.dl-btn {
  display: flex; align-items: center; gap: 10px;
  border: var(--rule-thick); background: var(--paper);
  font-family: var(--fd); font-size: 14px; letter-spacing: .1em;
  padding: 10px 28px; cursor: pointer; text-transform: uppercase;
  transition: background .15s, color .15s;
}
.dl-btn:hover { background: var(--ink); color: var(--paper); }

@media print {
  body { padding: 0; background: white; }
  .sheet { border: 2px solid black; max-width: 100%; box-shadow: none; }
  .footer, .add-btn, .del-btn, .sec-title button { display: none !important; }
  * { -webkit-print-color-adjust: exact; print-color-adjust: exact; }
  .ctrl-btn { display: none !important; }
  .t-btn { display: none !important; }
  textarea { overflow: hidden; }
}

@media (max-width: 700px) {
  .main { grid-template-columns: 1fr; }
  .col-l { border-right: none; border-bottom: var(--rule-thick); }
  .hdr { grid-template-columns: 1fr; gap: 10px; }
  .hdr-title { text-align: left; }
  .hdr-right { align-items: flex-start; }
  .char-grid-3 { grid-template-columns: 1fr 1fr; }
  .weapon-row-top, .weapon-row-mid { grid-template-columns: 1fr 1fr; }
  .spell-row { grid-template-columns: 1fr 1fr; }
  .armor-equipped { grid-template-columns: 1fr 1fr; }
}
@media (max-width: 480px) {
  .char-grid-3, .char-grid-2 { grid-template-columns: 1fr; }
  .char-grid-3 .cf, .char-grid-2 .cf { border-right: none; border-bottom: var(--rule); }
  .char-grid-3 .cf:last-child, .char-grid-2 .cf:last-child { border-bottom: none; }
  .weapon-row-top, .weapon-row-mid, .spell-row, .armor-equipped { grid-template-columns: 1fr; }
}
</style>
</head>
<body>
<div class="sheet" id="sheet">

  <!-- HEADER -->
  <div class="hdr">
    <div class="hdr-left">
      <span class="hdr-badge">Sistema de Jogo</span>
    </div>
    <div class="hdr-title">Ficha de Personagem</div>
    <div class="hdr-right">
      <span class="aura-label">Pontos de Aura</span>
      <input class="aura-val" type="text" id="aura" placeholder="—">
    </div>
  </div>

  <div class="main">

    <!-- COLUNA ESQUERDA -->
    <div class="col-l">

      <!-- ATRIBUTOS -->
      <div class="sec-block">
        <div class="sec-title"><span>Atributos</span></div>
        <div class="attr-row">
          <div>
            <span class="attr-name">Corpo</span>
            <span class="attr-note" id="note-corpo"></span>
          </div>
          <div class="ctrl">
            <button class="ctrl-btn" onclick="changeAttr('corpo',-1)">−</button>
            <input class="ctrl-val" type="number" id="corpo" value="1" min="1">
            <button class="ctrl-btn" onclick="changeAttr('corpo',1)">+</button>
          </div>
        </div>
        <div class="attr-row">
          <div>
            <span class="attr-name">Mente</span>
            <span class="attr-note" id="note-mente"></span>
          </div>
          <div class="ctrl">
            <button class="ctrl-btn" onclick="changeAttr('mente',-1)">−</button>
            <input class="ctrl-val" type="number" id="mente" value="1" min="1">
            <button class="ctrl-btn" onclick="changeAttr('mente',1)">+</button>
          </div>
        </div>
        <div class="attr-row" style="border-bottom:none">
          <div>
            <span class="attr-name">Magia</span>
            <span class="attr-note" id="note-magia"></span>
          </div>
          <div class="ctrl">
            <button class="ctrl-btn" onclick="changeAttr('magia',-1)">−</button>
            <input class="ctrl-val" type="number" id="magia" value="1" min="1">
            <button class="ctrl-btn" onclick="changeAttr('magia',1)">+</button>
          </div>
        </div>
        <div class="field-wrap" style="border-top:var(--rule)">
          <div class="field-label">Notas de Atributos</div>
          <textarea class="field-textarea" placeholder="Observações sobre seus atributos..."></textarea>
        </div>
      </div>

      <!-- ESTATÍSTICAS -->
      <div class="sec-block">
        <div class="sec-title"><span>Estatísticas</span></div>
        <div class="stat-row">
          <div>
            <div class="stat-label">Defesa</div>
            <div class="stat-sub">⌊ Corpo ÷ 2 ⌋</div>
          </div>
          <div class="stat-val" id="defesa">0</div>
        </div>
        <div class="stat-row">
          <div>
            <div class="stat-label">Sentidos</div>
            <div class="stat-sub">igual a Mente</div>
          </div>
          <div class="stat-val" id="sentidos">1</div>
        </div>
        <div class="stat-row" style="border-bottom:none">
          <div>
            <div class="stat-label">Defesa Total</div>
            <div class="stat-sub">Defesa + bônus armadura</div>
          </div>
          <div class="stat-val" id="defesa-total">0</div>
        </div>
      </div>

      <!-- RECURSOS -->
      <div class="sec-block">
        <div class="sec-title"><span>Recursos</span></div>
        <div class="tracker-grid">
          <div class="tracker-item">
            <div class="tracker-lbl">Pontos de Vida</div>
            <div class="tracker-ctrl">
              <button class="t-btn" onclick="changeTracker('pv',-1)">−</button>
              <input class="t-cur" type="number" id="pv-cur" value="12" min="0">
              <button class="t-btn" onclick="changeTracker('pv',1)">+</button>
            </div>
            <div class="tracker-max">max: <span id="pv-max">12</span></div>
            <div class="tracker-note">
              <textarea class="field-textarea" style="min-height:28px;font-size:10px" placeholder="Notas de PV..."></textarea>
            </div>
          </div>
          <div class="tracker-item" style="border-bottom:none">
            <div class="tracker-lbl">Mana</div>
            <div class="tracker-ctrl">
              <button class="t-btn" onclick="changeTracker('mana',-1)">−</button>
              <input class="t-cur" type="number" id="mana-cur" value="8" min="0">
              <button class="t-btn" onclick="changeTracker('mana',1)">+</button>
            </div>
            <div class="tracker-max">max: <span id="mana-max">8</span></div>
            <div class="tracker-note">
              <textarea class="field-textarea" style="min-height:28px;font-size:10px" placeholder="Notas de Mana..."></textarea>
            </div>
          </div>
        </div>
      </div>

      <!-- DINHEIRO -->
      <div class="sec-block">
        <div class="sec-title"><span>Dinheiro</span></div>
        <div class="money-wrap">
          <div class="money-row">
            <span class="money-sym">$</span>
            <input class="money-inp" type="number" id="dinheiro" value="0" min="0" placeholder="0">
          </div>
          <div style="margin-top:8px">
            <textarea class="field-textarea" style="min-height:28px;font-size:10px" placeholder="Notas sobre finanças..."></textarea>
          </div>
        </div>
      </div>

    </div><!-- /col-l -->

    <!-- COLUNA DIREITA -->
    <div class="col-r">

      <!-- PERSONAGEM -->
      <div class="sec-block">
        <div class="sec-title"><span>Personagem</span></div>
        <div class="char-grid-3">
          <div class="cf"><div class="cf-lbl">Nome</div><input class="cf-inp" type="text" placeholder="—"></div>
          <div class="cf"><div class="cf-lbl">Idade</div><input class="cf-inp" type="text" placeholder="—"></div>
          <div class="cf"><div class="cf-lbl">Sexo</div><input class="cf-inp" type="text" placeholder="—"></div>
        </div>
        <div class="char-grid-2">
          <div class="cf"><div class="cf-lbl">Alinhamento</div><input class="cf-inp" type="text" placeholder="—"></div>
          <div class="cf"><div class="cf-lbl">Classe / Origem</div><input class="cf-inp" type="text" placeholder="—"></div>
        </div>
        <div class="char-grid-2">
          <div class="cf"><div class="cf-lbl">Raça / Espécie</div><input class="cf-inp" type="text" placeholder="—"></div>
          <div class="cf"><div class="cf-lbl">Nível</div><input class="cf-inp" type="text" placeholder="—"></div>
        </div>
        <div class="char-grid-1">
          <div class="cf"><div class="cf-lbl">Aparência</div><textarea class="cf-ta" placeholder="Descreva a aparência do personagem..."></textarea></div>
        </div>
        <div class="char-grid-1" style="border-bottom:none">
          <div class="cf"><div class="cf-lbl">História / Notas do Personagem</div><textarea class="cf-ta" style="min-height:60px" placeholder="Background, motivações, segredos..."></textarea></div>
        </div>
      </div>

      <!-- ARMADURA -->
      <div class="sec-block">
        <div class="sec-title"><span>Armadura Equipada</span></div>
        <div class="armor-types">
          Leve: +1 Defesa &nbsp;|&nbsp; Média: +2 Defesa &nbsp;|&nbsp; Pesada: +3 Defesa &nbsp;|&nbsp; Escudo: +1 Defesa
        </div>
        <div class="armor-equipped">
          <div class="a-cell">
            <div class="a-lbl">Tipo de Armadura</div>
            <select class="a-inp" id="armor-type" onchange="applyArmorType()">
              <option value="">Nenhuma (0)</option>
              <option value="1">Leve (+1)</option>
              <option value="2">Média (+2)</option>
              <option value="3">Pesada (+3)</option>
              <option value="1">Escudo (+1)</option>
              <option value="custom">Personalizada</option>
            </select>
          </div>
          <div class="a-cell">
            <div class="a-lbl">Bônus de Defesa</div>
            <input class="a-inp" type="number" id="armor-bonus" value="0" min="0" oninput="updateDerivedStats()">
          </div>
          <div class="a-cell" style="border-right:none">
            <div class="a-lbl">Nome / Descrição</div>
            <input class="a-inp" type="text" id="armor-name" placeholder="ex: Cota de Malha">
          </div>
        </div>
        <div style="padding:0 14px 10px">
          <div class="a-lbl" style="margin-top:8px">Notas da Armadura</div>
          <textarea class="a-ta" placeholder="Propriedades especiais, origem, história..."></textarea>
        </div>
      </div>

      <!-- ATAQUES -->
      <div class="sec-block">
        <div class="sec-title">
          <span>Ataques</span>
          <button onclick="addAttack()">+ Adicionar Ataque</button>
        </div>
        <div id="attacks-list"></div>
        <button class="add-btn" onclick="addAttack()">
          <span class="add-icon">+</span> Adicionar Ataque
        </button>
      </div>

      <!-- ARMAS -->
      <div class="sec-block">
        <div class="sec-title">
          <span>Armas</span>
          <button onclick="addWeapon()">+ Adicionar Arma</button>
        </div>
        <div id="weapons-list"></div>
        <button class="add-btn" onclick="addWeapon()">
          <span class="add-icon">+</span> Adicionar Arma
        </button>
      </div>

      <!-- MAGIAS -->
      <div class="sec-block">
        <div class="sec-title">
          <span>Magias</span>
          <button onclick="addSpell()">+ Adicionar Magia</button>
        </div>
        <div id="spells-list"></div>
        <button class="add-btn" onclick="addSpell()">
          <span class="add-icon">+</span> Adicionar Magia
        </button>
      </div>

      <!-- INVENTÁRIO -->
      <div class="sec-block">
        <div class="sec-title">
          <span>Inventário</span>
          <button onclick="addItem()">+ Adicionar Item</button>
        </div>
        <div id="inv-list"></div>
        <button class="add-btn" onclick="addItem()">
          <span class="add-icon">+</span> Adicionar Item
        </button>
      </div>

      <!-- ANOTAÇÕES -->
      <div class="sec-block" style="border-bottom:none">
        <div class="sec-title"><span>Anotações</span></div>
        <textarea class="notes-area" placeholder="Notas de sessão, missões, NPCs, segredos, lembretes..."></textarea>
      </div>

    </div><!-- /col-r -->
  </div><!-- /main -->

  <!-- FOOTER -->
  <div class="footer">
    <span class="footer-note">Botões e campos vazios não aparecerão no PDF</span>
    <button class="dl-btn" onclick="downloadPDF()">⬓ Baixar Ficha em PDF</button>
  </div>
</div>

<script>
function el(id) { return document.getElementById(id); }
function getN(id) { return parseInt(el(id).value) || 0; }

function updateDerivedStats() {
  const corpo = getN('corpo');
  const mente = getN('mente');
  const magia = getN('magia');

  const pvMax = 10 + corpo * 2;
  el('pv-max').textContent = pvMax;
  if (getN('pv-cur') > pvMax) el('pv-cur').value = pvMax;

  const manaMax = 6 + magia * 2;
  el('mana-max').textContent = manaMax;
  if (getN('mana-cur') > manaMax) el('mana-cur').value = manaMax;

  const defesa = Math.floor(corpo / 2);
  el('defesa').textContent = defesa;
  el('sentidos').textContent = mente;

  const armorBonus = getN('armor-bonus');
  el('defesa-total').textContent = defesa + armorBonus;
}

function changeAttr(name, delta) {
  const input = el(name);
  const current = parseInt(input.value) || 1;
  if (delta > 0) {
    input.value = current + 1;
  } else {
    if (current <= 1) return;
    input.value = current - 1;
  }
  updateDerivedStats();
}

['corpo','mente','magia'].forEach(name => {
  el(name).addEventListener('change', () => updateDerivedStats());
});

function changeTracker(type, delta) {
  const input = el(type + '-cur');
  const maxEl = el(type + '-max');
  const max = parseInt(maxEl.textContent);
  let val = (parseInt(input.value) || 0) + delta;
  val = Math.max(0, Math.min(max, val));
  input.value = val;
}

function applyArmorType() {
  const sel = el('armor-type').value;
  const bonusInput = el('armor-bonus');
  if (sel === '') bonusInput.value = 0;
  else if (sel === 'custom') { /* leave as is */ }
  else bonusInput.value = parseInt(sel) || 0;
  updateDerivedStats();
}

let weaponCount = 0;
function addWeapon() {
  weaponCount++;
  const id = 'w' + weaponCount;
  const div = document.createElement('div');
  div.className = 'weapon-card';
  div.id = id;
  div.innerHTML = `
    <div class="weapon-row-top">
      <div><div class="weapon-mini-lbl">Arma</div><input class="w-inp" type="text" placeholder="Nome da arma" data-wf="name"></div>
      <div><div class="weapon-mini-lbl">Dano</div><input class="w-inp" type="text" placeholder="1d6" data-wf="dano"></div>
      <div><div class="weapon-mini-lbl">Bônus</div><input class="w-inp" type="text" placeholder="+0" data-wf="bonus"></div>
    </div>
    <div class="weapon-row-mid">
      <div><div class="weapon-mini-lbl">Munição Atual</div><input class="w-inp" type="number" placeholder="—" min="0" data-wf="mun-cur"></div>
      <div><div class="weapon-mini-lbl">Munição Total</div><input class="w-inp" type="number" placeholder="—" min="0" data-wf="mun-tot"></div>
      <div><div class="weapon-mini-lbl">Habilidade Especial</div><input class="w-inp" type="text" placeholder="—" data-wf="habil"></div>
    </div>
    <div><div class="weapon-mini-lbl">Descrição</div><textarea class="w-ta" rows="2" placeholder="Origem, aparência, quirks..." data-wf="desc"></textarea></div>
    <div style="text-align:right"><button class="del-btn" onclick="removeCard('${id}')">✕ remover</button></div>
  `;
  el('weapons-list').appendChild(div);
}

let spellCount = 0;
function addAttack() {
  attackCount++;
  const id = 'at' + attackCount;
  const div = document.createElement('div');
  div.className = 'attack-card';
  div.id = id;
  div.innerHTML = `
    <div class="spell-row">
      <div><div class="weapon-mini-lbl">Nome do Ataque</div><input class="sp-inp" type="text" placeholder="—" data-af="name"></div>
      <div><div class="weapon-mini-lbl">Dano</div><input class="sp-inp" type="text" placeholder="ex: 1d8" data-af="dano"></div>
      <div><div class="weapon-mini-lbl">Bônus de Ataque</div><input class="sp-inp" type="text" placeholder="ex: +3" data-af="bonus"></div>
    </div>
    <div class="spell-row">
      <div><div class="weapon-mini-lbl">Atributo Base</div><input class="sp-inp" type="text" placeholder="ex: Corpo" data-af="atributo"></div>
      <div><div class="weapon-mini-lbl">Alcance</div><input class="sp-inp" type="text" placeholder="ex: Corpo/2 m" data-af="alcance"></div>
      <div><div class="weapon-mini-lbl">Tipo</div><input class="sp-inp" type="text" placeholder="ex: Físico, Mágico" data-af="tipo"></div>
    </div>
    <div><div class="weapon-mini-lbl">Efeito / Descrição</div><textarea class="sp-ta" rows="2" placeholder="Condições, efeitos especiais, como funciona..." data-af="desc"></textarea></div>
    <div style="text-align:right"><button class="del-btn" onclick="removeCard('${id}')">✕ remover</button></div>
  `;
  el('attacks-list').appendChild(div);
}

let attackCount = 0;
function addSpell() {
  spellCount++;
  const id = 'sp' + spellCount;
  const div = document.createElement('div');
  div.className = 'spell-card';
  div.id = id;
  div.innerHTML = `
    <div class="spell-row">
      <div><div class="weapon-mini-lbl">Nome da Magia</div><input class="sp-inp" type="text" placeholder="—" data-sf="name"></div>
      <div><div class="weapon-mini-lbl">Custo de Mana</div><input class="sp-inp" type="text" placeholder="—" data-sf="custo"></div>
      <div><div class="weapon-mini-lbl">Dano / Cura</div><input class="sp-inp" type="text" placeholder="—" data-sf="dano"></div>
    </div>
    <div class="spell-row">
      <div><div class="weapon-mini-lbl">Efeito</div><input class="sp-inp" type="text" placeholder="—" data-sf="efeito"></div>
      <div><div class="weapon-mini-lbl">Alcance</div><input class="sp-inp" type="text" placeholder="—" data-sf="alcance"></div>
      <div><div class="weapon-mini-lbl">Duração</div><input class="sp-inp" type="text" placeholder="—" data-sf="dur"></div>
    </div>
    <div><div class="weapon-mini-lbl">Descrição / Notas</div><textarea class="sp-ta" rows="2" placeholder="Como a magia se manifesta, restrições, lore..." data-sf="desc"></textarea></div>
    <div style="text-align:right"><button class="del-btn" onclick="removeCard('${id}')">✕ remover</button></div>
  `;
  el('spells-list').appendChild(div);
}

let invCount = 0;
function addItem() {
  invCount++;
  const id = 'it' + invCount;
  const div = document.createElement('div');
  div.className = 'inv-card';
  div.id = id;
  div.innerHTML = `
    <div class="inv-main">
      <input class="i-inp" type="text" placeholder="Nome do item" data-if="name">
      <textarea class="i-ta" rows="1" placeholder="Descrição, propriedades..." data-if="desc"></textarea>
    </div>
    <div style="display:flex;flex-direction:column;align-items:center;gap:4px">
      <div class="inv-qty-lbl">Qtd.</div>
      <input class="inv-qty-inp" type="number" value="1" min="0" data-if="qty">
      <button class="del-btn" onclick="removeCard('${id}')" style="margin-top:4px">✕</button>
    </div>
  `;
  el('inv-list').appendChild(div);
}

function removeCard(id) {
  const node = document.getElementById(id);
  if (node) node.remove();
}

function downloadPDF() {
  const marked = [];

  // ── Helpers ──────────────────────────────────────────
  function isEmpty(el) {
    if (el.tagName === 'SELECT') return el.value === '' || el.value === '0';
    if (el.type === 'number') {
      const def = el.dataset.printDefault ?? null;
      if (def !== null) return el.value === def;
      return el.value === '0' || el.value === '';
    }
    return el.value.trim() === '';
  }

  function hideEl(node) {
    node.dataset.printHidden = '1';
    node.style.display = 'none';
    marked.push(node);
  }

  // ── 1. Campos individuais vazios (inputs, selects, textareas não tracker) ──
  document.querySelectorAll(
    '.cf-inp, .cf-ta, .field-textarea, .a-inp, .a-ta, .money-inp, .notes-area, .aura-val'
  ).forEach(field => {
    if (isEmpty(field)) {
      // Sobe para o wrapper mais próximo com label para esconder o bloco todo
      const wrap = field.closest('.cf, .field-wrap, .money-wrap, .a-cell') || field.parentElement;
      if (wrap && !wrap.dataset.printHidden) hideEl(wrap);
    }
  });

  // ── 2. Cartões dinâmicos: esconde os vazios ──
  document.querySelectorAll('.weapon-card').forEach(card => {
    const filled = [...card.querySelectorAll('input[data-wf],textarea[data-wf]')].some(i => i.value.trim() !== '');
    if (!filled) hideEl(card);
  });
  document.querySelectorAll('.attack-card').forEach(card => {
    const filled = [...card.querySelectorAll('input[data-af],textarea[data-af]')].some(i => i.value.trim() !== '');
    if (!filled) hideEl(card);
  });
  document.querySelectorAll('.spell-card').forEach(card => {
    const filled = [...card.querySelectorAll('input[data-sf],textarea[data-sf]')].some(i => i.value.trim() !== '');
    if (!filled) hideEl(card);
  });
  document.querySelectorAll('.inv-card').forEach(card => {
    const nameEl = card.querySelector('input[data-if="name"]');
    if (!nameEl || nameEl.value.trim() === '') hideEl(card);
  });

  // ── 3. Seções inteiras: se não tiver nenhum conteúdo visível, esconde tudo ──
  document.querySelectorAll('.sec-block').forEach(block => {
    // Verifica inputs/textareas não escondidos com conteúdo
    const hasContent = [...block.querySelectorAll('input, textarea, select')].some(f => {
      if (f.closest('[data-print-hidden]')) return false;
      return !isEmpty(f);
    });
    // Verifica se há cartões dinâmicos visíveis
    const hasVisibleCards = [...block.querySelectorAll(
      '.weapon-card, .attack-card, .spell-card, .inv-card'
    )].some(c => !c.dataset.printHidden);

    if (!hasContent && !hasVisibleCards) hideEl(block);
  });

  window.print();

  // ── Restaura tudo após imprimir ──
  setTimeout(() => {
    marked.forEach(node => {
      delete node.dataset.printHidden;
      node.style.display = '';
    });
  }, 1500);
}

updateDerivedStats();
addAttack();
addWeapon();
addSpell();
addItem();

/* ═══════════════════════════════
   AUTO-SHRINK FONT FOR TEXTAREAS
   Reduz a fonte até o conteúdo caber
   na altura atual do elemento.
═══════════════════════════════ */
function autoShrinkTextarea(ta) {
  // Reset para o tamanho base antes de medir
  const baseSize = parseFloat(ta.dataset.baseFontSize || getComputedStyle(ta).fontSize);
  if (!ta.dataset.baseFontSize) ta.dataset.baseFontSize = baseSize;

  let size = baseSize;
  ta.style.fontSize = size + 'px';

  // Encolhe até scrollHeight caber na clientHeight
  // Limite mínimo: 7px para ainda ser legível
  while (ta.scrollHeight > ta.clientHeight && size > 7) {
    size -= 0.5;
    ta.style.fontSize = size + 'px';
  }

  // Se o texto cabe, tenta subir de volta até o tamanho base
  // (útil quando o usuário apaga texto)
  while (size < baseSize) {
    const next = Math.min(size + 0.5, baseSize);
    ta.style.fontSize = next + 'px';
    if (ta.scrollHeight > ta.clientHeight) {
      ta.style.fontSize = size + 'px';
      break;
    }
    size = next;
  }
}

function initShrinkable(ta) {
  // Guarda o tamanho base na primeira vez
  if (!ta.dataset.baseFontSize) {
    ta.dataset.baseFontSize = parseFloat(getComputedStyle(ta).fontSize);
  }
  ta.addEventListener('input', () => autoShrinkTextarea(ta));
  // Roda uma vez caso já tenha conteúdo
  autoShrinkTextarea(ta);
}

// Aplica em todos os textareas existentes
document.querySelectorAll('textarea').forEach(initShrinkable);

// Observer para pegar textareas adicionados dinamicamente
// (armas, magias, ataques, itens)
const taObserver = new MutationObserver(mutations => {
  mutations.forEach(m => {
    m.addedNodes.forEach(node => {
      if (node.nodeType !== 1) return;
      if (node.tagName === 'TEXTAREA') initShrinkable(node);
      node.querySelectorAll && node.querySelectorAll('textarea').forEach(initShrinkable);
    });
  });
});
taObserver.observe(document.body, { childList: true, subtree: true });
</script>
</body>
</html>
