<!DOCTYPE html>
<html lang="de">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Blackjack Kartenzähler</title>
<style>
  @import url('https://fonts.googleapis.com/css2?family=DM+Mono:wght@300;400;500&family=DM+Sans:wght@300;400;500&display=swap');

  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  :root {
    --bg: #f5f3ef;
    --surface: #ffffff;
    --border: #e0ddd8;
    --text: #1a1916;
    --muted: #888580;
    --highlight: #2d6a4f;
    --highlight-bg: rgba(45, 106, 79, 0.18);
    --red: #c0392b;
    --empty: #ccc9c3;
  }

  body {
    font-family: 'DM Sans', sans-serif;
    background: var(--bg);
    color: var(--text);
    min-height: 100vh;
    padding: 2rem 1rem;
  }

  header {
    display: flex;
    align-items: baseline;
    justify-content: space-between;
    max-width: 1100px;
    margin: 0 auto 1.5rem;
  }

  h1 {
    font-family: 'DM Mono', monospace;
    font-size: 14px;
    font-weight: 400;
    letter-spacing: 0.08em;
    text-transform: uppercase;
    color: var(--muted);
  }

  .meta {
    font-family: 'DM Mono', monospace;
    font-size: 13px;
    color: var(--muted);
  }

  .stats {
    display: flex;
    gap: 0.75rem;
    max-width: 1100px;
    margin: 0 auto 1.5rem;
  }

  .stat {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 6px;
    padding: 8px 16px;
  }

  .stat-label {
    font-size: 11px;
    letter-spacing: 0.06em;
    text-transform: uppercase;
    color: var(--muted);
    margin-bottom: 2px;
  }

  .stat-val {
    font-family: 'DM Mono', monospace;
    font-size: 18px;
    font-weight: 500;
    color: var(--text);
  }

  /* Grid: always 13 columns, cards sized via fixed min width */
  .grid {
    display: grid;
    grid-template-columns: repeat(13, minmax(0, 1fr));
    gap: 8px;
    max-width: 1100px;
    margin: 0 auto;
    /* ensure grid never gets too narrow */
    min-width: 0;
  }

  .card-wrap {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 5px;
    min-width: 0;
  }

  .card {
    width: 100%;
    aspect-ratio: 2/3;
    border-radius: 6px;
    border: 1px solid var(--border);
    background: var(--surface);
    display: flex;
    align-items: center;
    justify-content: center;
    font-family: 'DM Mono', monospace;
    /* font scales with viewport, always readable */
    font-size: clamp(11px, 3.5vw, 26px);
    font-weight: 500;
    color: var(--text);
    cursor: pointer;
    transition: transform 0.1s ease, border-color 0.15s ease;
    position: relative;
    user-select: none;
  }

  .card.red { color: var(--red); }

  .card:hover:not(.empty) {
    transform: translateY(-3px);
    border-color: #aaa8a2;
  }

  @keyframes flash {
    0%   { transform: scale(1); }
    40%  { transform: scale(0.91); }
    100% { transform: scale(1); }
  }
  .card.flash { animation: flash 0.18s ease; }

  .card.empty {
    color: var(--empty);
    border-color: #e8e5e0;
    cursor: default;
  }

  .card.best {
    background: var(--highlight-bg);
    border-color: rgba(45, 106, 79, 0.35);
  }
  .card.red.best { color: var(--red); }

  .key-hint {
    position: absolute;
    bottom: 4px;
    right: 5px;
    font-size: clamp(7px, 1.5vw, 11px);
    color: var(--muted);
    opacity: 0.5;
    font-family: 'DM Mono', monospace;
  }

  .card-count {
    font-family: 'DM Mono', monospace;
    font-size: clamp(9px, 2vw, 13px);
    color: var(--muted);
    text-align: center;
  }

  .card-prob {
    font-family: 'DM Mono', monospace;
    font-size: clamp(9px, 2vw, 13px);
    font-weight: 500;
    color: var(--text);
    text-align: center;
    white-space: nowrap;
  }

  .card-prob.best-prob { color: var(--highlight); }

  .reset-wrap {
    display: flex;
    justify-content: center;
    max-width: 1100px;
    margin: 2rem auto 0;
  }

  .reset-btn {
    font-family: 'DM Mono', monospace;
    font-size: 14px;
    letter-spacing: 0.07em;
    text-transform: uppercase;
    padding: 14px 48px;
    border-radius: 7px;
    border: 1px solid var(--border);
    background: var(--surface);
    color: var(--muted);
    cursor: pointer;
    transition: background 0.12s, color 0.12s, border-color 0.12s;
  }

  .reset-btn:hover {
    background: var(--text);
    color: var(--bg);
    border-color: var(--text);
  }

  .hint-bar {
    max-width: 1100px;
    margin: 1.25rem auto 0;
    text-align: center;
    font-family: 'DM Mono', monospace;
    font-size: 11px;
    color: var(--muted);
    letter-spacing: 0.03em;
    opacity: 0.7;
  }
</style>
</head>
<body>

<header>
  <h1>Blackjack Kartenzähler</h1>
  <span class="meta" id="deck-info">52 Karten</span>
</header>

<div class="stats">
  <div class="stat">
    <div class="stat-label">Im Deck</div>
    <div class="stat-val" id="total-val">52</div>
  </div>
  <div class="stat">
    <div class="stat-label">Gezogen</div>
    <div class="stat-val" id="drawn-val">0</div>
  </div>
</div>

<div class="grid" id="grid"></div>

<div class="reset-wrap">
  <button class="reset-btn" onclick="reset()">Zurücksetzen</button>
</div>

<div class="hint-bar">
  Tippen / Klick = −1 &nbsp;·&nbsp; Rechtsklick / Lang drücken = +1
  <br>Tasten: 2–9 · 0=10 · Q=J · W=Q · E=K · R=A
</div>

<script>
  const CARDS = [
    { label: '2',  key: '2', red: false },
    { label: '3',  key: '3', red: false },
    { label: '4',  key: '4', red: false },
    { label: '5',  key: '5', red: false },
    { label: '6',  key: '6', red: false },
    { label: '7',  key: '7', red: false },
    { label: '8',  key: '8', red: false },
    { label: '9',  key: '9', red: false },
    { label: '10', key: '0', red: false },
    { label: 'J',  key: 'q', red: false },
    { label: 'Q',  key: 'w', red: false },
    { label: 'K',  key: 'e', red: false },
    { label: 'A',  key: 'r', red: true  },
  ];

  const KEY_MAP = {};
  CARDS.forEach(c => KEY_MAP[c.key] = c.label);

  const counts = {};
  CARDS.forEach(c => counts[c.label] = 4);

  const cardEls = {};

  function total() {
    return Object.values(counts).reduce((a, b) => a + b, 0);
  }

  function getBestSet() {
    const t = total();
    if (t === 0) return new Set();
    let bestP = -1;
    CARDS.forEach(c => { const p = counts[c.label] / t; if (p > bestP) bestP = p; });
    const nonEmpty = CARDS.filter(c => counts[c.label] > 0);
    const allEqual = nonEmpty.every(c => Math.abs(counts[c.label] / t - bestP) < 1e-9);
    if (allEqual) return new Set();
    const result = new Set();
    CARDS.forEach(c => {
      if (counts[c.label] > 0 && Math.abs(counts[c.label] / t - bestP) < 1e-9) result.add(c.label);
    });
    return result;
  }

  function flashCard(label) {
    const el = cardEls[label];
    if (!el) return;
    el.classList.remove('flash');
    void el.offsetWidth;
    el.classList.add('flash');
  }

  function decrement(label) {
    if (counts[label] <= 0) return;
    counts[label]--;
    flashCard(label);
    render();
  }

  function increment(label) {
    if (counts[label] >= 4) return;
    counts[label]++;
    flashCard(label);
    render();
  }

  function render() {
    const grid = document.getElementById('grid');
    const t = total();
    const bestSet = getBestSet();
    grid.innerHTML = '';

    CARDS.forEach(c => {
      const cnt = counts[c.label];
      const prob = t > 0 ? (cnt / t * 100) : 0;
      const isBest = bestSet.has(c.label);
      const isEmpty = cnt === 0;

      const wrap = document.createElement('div');
      wrap.className = 'card-wrap';

      const card = document.createElement('div');
      card.className = 'card' + (c.red ? ' red' : '') + (isEmpty ? ' empty' : '') + (isBest ? ' best' : '');
      card.innerHTML = c.label + '<span class="key-hint">' + c.key.toUpperCase() + '</span>';
      cardEls[c.label] = card;

      let pressTimer = null;
      let didLongPress = false;

      card.addEventListener('click', () => {
        if (didLongPress) { didLongPress = false; return; }
        decrement(c.label);
      });

      card.addEventListener('contextmenu', e => {
        e.preventDefault();
        increment(c.label);
      });

      card.addEventListener('touchstart', () => {
        didLongPress = false;
        pressTimer = setTimeout(() => {
          didLongPress = true;
          increment(c.label);
        }, 500);
      }, { passive: true });

      card.addEventListener('touchend', () => { if (pressTimer) clearTimeout(pressTimer); });
      card.addEventListener('touchmove', () => { if (pressTimer) clearTimeout(pressTimer); });

      const countEl = document.createElement('div');
      countEl.className = 'card-count';
      countEl.textContent = cnt + 'x';

      const probEl = document.createElement('div');
      probEl.className = 'card-prob' + (isBest ? ' best-prob' : '');
      probEl.textContent = t > 0 ? prob.toFixed(1) + '%' : '—';

      wrap.appendChild(card);
      wrap.appendChild(countEl);
      wrap.appendChild(probEl);
      grid.appendChild(wrap);
    });

    document.getElementById('total-val').textContent = t;
    document.getElementById('drawn-val').textContent = 52 - t;
    document.getElementById('deck-info').textContent = t + ' Karten';
  }

  function reset() {
    CARDS.forEach(c => counts[c.label] = 4);
    render();
  }

  document.addEventListener('keydown', e => {
    if (e.target.tagName === 'INPUT' || e.target.tagName === 'TEXTAREA') return;
    const label = KEY_MAP[e.key.toLowerCase()];
    if (!label) return;
    e.preventDefault();
    decrement(label);
  });

  render();
</script>
</body>
</html>
