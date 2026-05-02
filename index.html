<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>ESP32 Motor Control</title>
<style>
  @import url('https://fonts.googleapis.com/css2?family=Share+Tech+Mono&family=Barlow+Condensed:wght@300;600;800&display=swap');

  :root {
    --bg:        #0a0c10;
    --panel:     #111318;
    --border:    #1e2230;
    --accent-a:  #00e5ff;
    --accent-b:  #ff3d71;
    --green:     #39ff14;
    --dim:       #3a3f52;
    --text:      #c8d0e8;
    --text-dim:  #555c78;
    --radius:    6px;
    --font-mono: 'Share Tech Mono', monospace;
    --font-ui:   'Barlow Condensed', sans-serif;
  }

  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: var(--font-ui);
    min-height: 100vh;
    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 32px 16px 48px;
    background-image:
      repeating-linear-gradient(0deg,   transparent, transparent 39px, #ffffff04 39px, #ffffff04 40px),
      repeating-linear-gradient(90deg,  transparent, transparent 39px, #ffffff04 39px, #ffffff04 40px);
  }

  /* ── Header ── */
  header {
    width: 100%;
    max-width: 640px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    margin-bottom: 36px;
  }
  .logo {
    font-size: 11px;
    font-family: var(--font-mono);
    color: var(--text-dim);
    letter-spacing: 3px;
    text-transform: uppercase;
  }
  .logo span { color: var(--accent-a); }

  /* ── Status pill ── */
  #status-pill {
    display: flex;
    align-items: center;
    gap: 8px;
    padding: 6px 14px;
    border: 1px solid var(--border);
    border-radius: 100px;
    font-family: var(--font-mono);
    font-size: 11px;
    letter-spacing: 1px;
    transition: border-color .3s, color .3s;
  }
  #status-dot {
    width: 7px; height: 7px;
    border-radius: 50%;
    background: var(--dim);
    transition: background .3s, box-shadow .3s;
  }
  #status-pill.connected   { border-color: var(--green); color: var(--green); }
  #status-pill.connected #status-dot {
    background: var(--green);
    box-shadow: 0 0 8px var(--green);
    animation: pulse 1.8s ease-in-out infinite;
  }
  #status-pill.error { border-color: var(--accent-b); color: var(--accent-b); }
  #status-pill.error #status-dot { background: var(--accent-b); }

  @keyframes pulse {
    0%,100% { box-shadow: 0 0 4px var(--green); }
    50%      { box-shadow: 0 0 14px var(--green); }
  }

  /* ── Connect button ── */
  #btn-connect {
    width: 100%;
    max-width: 640px;
    padding: 18px;
    margin-bottom: 32px;
    border: 1px solid var(--accent-a);
    border-radius: var(--radius);
    background: transparent;
    color: var(--accent-a);
    font-family: var(--font-ui);
    font-size: 18px;
    font-weight: 600;
    letter-spacing: 4px;
    text-transform: uppercase;
    cursor: pointer;
    position: relative;
    overflow: hidden;
    transition: background .25s, color .25s, box-shadow .25s;
  }
  #btn-connect::before {
    content: '';
    position: absolute;
    inset: 0;
    background: var(--accent-a);
    transform: scaleX(0);
    transform-origin: left;
    transition: transform .25s ease;
    z-index: 0;
  }
  #btn-connect:hover::before { transform: scaleX(1); }
  #btn-connect:hover { color: var(--bg); box-shadow: 0 0 24px #00e5ff44; }
  #btn-connect span { position: relative; z-index: 1; }
  #btn-connect:disabled {
    border-color: var(--dim); color: var(--dim); cursor: not-allowed;
  }
  #btn-connect:disabled::before { display: none; }

  /* ── Motor panels ── */
  .motors-grid {
    width: 100%;
    max-width: 640px;
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 16px;
  }

  .motor-card {
    background: var(--panel);
    border: 1px solid var(--border);
    border-radius: var(--radius);
    padding: 24px 20px 20px;
    display: flex;
    flex-direction: column;
    gap: 14px;
    transition: border-color .3s;
  }
  .motor-card.active-fwd { border-color: var(--accent-a); box-shadow: 0 0 20px #00e5ff18; }
  .motor-card.active-bck { border-color: var(--accent-b); box-shadow: 0 0 20px #ff3d7118; }

  .motor-label {
    display: flex;
    align-items: baseline;
    gap: 10px;
  }
  .motor-letter {
    font-size: 42px;
    font-weight: 800;
    line-height: 1;
    color: var(--text-dim);
    transition: color .2s;
  }
  .motor-card.active-fwd .motor-letter { color: var(--accent-a); }
  .motor-card.active-bck .motor-letter { color: var(--accent-b); }

  .motor-name {
    font-size: 11px;
    font-family: var(--font-mono);
    color: var(--text-dim);
    letter-spacing: 2px;
  }

  /* ── Motor state indicator ── */
  .motor-state {
    font-family: var(--font-mono);
    font-size: 12px;
    letter-spacing: 2px;
    color: var(--text-dim);
    min-height: 16px;
    transition: color .2s;
  }
  .motor-card.active-fwd .motor-state { color: var(--accent-a); }
  .motor-card.active-bck .motor-state { color: var(--accent-b); }

  /* ── Directional buttons ── */
  .btn-row {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 8px;
  }

  .btn-motor {
    padding: 14px 8px;
    border-radius: var(--radius);
    border: 1px solid var(--border);
    background: transparent;
    color: var(--text-dim);
    font-family: var(--font-ui);
    font-size: 13px;
    font-weight: 600;
    letter-spacing: 2px;
    text-transform: uppercase;
    cursor: pointer;
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 6px;
    transition: all .2s;
    -webkit-user-select: none;
    user-select: none;
  }
  .btn-motor svg { transition: transform .2s; }
  .btn-motor:disabled { opacity: .25; cursor: not-allowed; }

  /* FWD button */
  .btn-fwd { border-color: #00e5ff33; }
  .btn-fwd:not(:disabled):hover,
  .btn-fwd.pressed {
    background: #00e5ff18;
    border-color: var(--accent-a);
    color: var(--accent-a);
    box-shadow: 0 0 12px #00e5ff33;
  }
  .btn-fwd.pressed svg { transform: translateY(-3px); }

  /* BCK button */
  .btn-bck { border-color: #ff3d7133; }
  .btn-bck:not(:disabled):hover,
  .btn-bck.pressed {
    background: #ff3d7118;
    border-color: var(--accent-b);
    color: var(--accent-b);
    box-shadow: 0 0 12px #ff3d7133;
  }
  .btn-bck.pressed svg { transform: translateY(3px); }

  /* ── Log ── */
  #log-wrap {
    width: 100%;
    max-width: 640px;
    margin-top: 28px;
  }
  .log-title {
    font-family: var(--font-mono);
    font-size: 10px;
    letter-spacing: 3px;
    color: var(--text-dim);
    text-transform: uppercase;
    margin-bottom: 8px;
  }
  #log {
    background: var(--panel);
    border: 1px solid var(--border);
    border-radius: var(--radius);
    padding: 12px 14px;
    height: 120px;
    overflow-y: auto;
    font-family: var(--font-mono);
    font-size: 11px;
    line-height: 1.8;
    color: var(--text-dim);
  }
  #log .entry { display: flex; gap: 10px; }
  #log .ts  { color: #2a2f42; flex-shrink: 0; }
  #log .msg-ok  { color: var(--green); }
  #log .msg-err { color: var(--accent-b); }
  #log .msg-info { color: var(--accent-a); }

  /* ── Disconnect btn ── */
  #btn-disconnect {
    display: none;
    width: 100%;
    max-width: 640px;
    margin-top: 12px;
    padding: 12px;
    border: 1px solid #ff3d7166;
    border-radius: var(--radius);
    background: transparent;
    color: #ff3d7188;
    font-family: var(--font-ui);
    font-size: 13px;
    font-weight: 600;
    letter-spacing: 3px;
    text-transform: uppercase;
    cursor: pointer;
    transition: all .2s;
  }
  #btn-disconnect:hover {
    border-color: var(--accent-b);
    color: var(--accent-b);
    background: #ff3d7110;
  }
</style>
</head>
<body>

<header>
  <div class="logo"><span>//</span> ESP32-C3 · L298N</div>
  <div id="status-pill">
    <div id="status-dot"></div>
    <span id="status-text">DESCONECTADO</span>
  </div>
</header>

<button id="btn-connect"><span>⬡ Conectar via Bluetooth</span></button>

<div class="motors-grid">

  <!-- Motor A -->
  <div class="motor-card" id="card-a">
    <div class="motor-label">
      <div class="motor-letter">A</div>
      <div class="motor-name">MOTOR A</div>
    </div>
    <div class="motor-state" id="state-a">PARADO</div>
    <div class="btn-row">
      <button class="btn-motor btn-fwd" id="btn-a-fwd" disabled data-motor="a" data-dir="fwd">
        <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round">
          <polyline points="18 15 12 9 6 15"/>
        </svg>
        AVANCE
      </button>
      <button class="btn-motor btn-bck" id="btn-a-bck" disabled data-motor="a" data-dir="bck">
        <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round">
          <polyline points="6 9 12 15 18 9"/>
        </svg>
        RETRO
      </button>
    </div>
  </div>

  <!-- Motor B -->
  <div class="motor-card" id="card-b">
    <div class="motor-label">
      <div class="motor-letter">B</div>
      <div class="motor-name">MOTOR B</div>
    </div>
    <div class="motor-state" id="state-b">PARADO</div>
    <div class="btn-row">
      <button class="btn-motor btn-fwd" id="btn-b-fwd" disabled data-motor="b" data-dir="fwd">
        <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round">
          <polyline points="18 15 12 9 6 15"/>
        </svg>
        AVANCE
      </button>
      <button class="btn-motor btn-bck" id="btn-b-bck" disabled data-motor="b" data-dir="bck">
        <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round">
          <polyline points="6 9 12 15 18 9"/>
        </svg>
        RETRO
      </button>
    </div>
  </div>

</div>

<button id="btn-disconnect">✕ Desconectar</button>

<div id="log-wrap">
  <div class="log-title">// consola</div>
  <div id="log"></div>
</div>

<script>
  // ── UUIDs (deben coincidir con el sketch) ──────────────────
  const SERVICE_UUID     = '12345678-1234-1234-1234-123456789abc';
  const CHAR_UUIDS = {
    'a-fwd': 'aaaaaaaa-0000-1000-8000-00805f9b34fb',
    'a-bck': 'aaaaaaab-0000-1000-8000-00805f9b34fb',
    'b-fwd': 'aaaaaaac-0000-1000-8000-00805f9b34fb',
    'b-bck': 'aaaaaaad-0000-1000-8000-00805f9b34fb',
  };

  // ── Estado ─────────────────────────────────────────────────
  let device = null;
  let server = null;
  let chars  = {};   // { 'a-fwd': BLECharacteristic, ... }

  // Estado activo por motor: null | 'fwd' | 'bck'
  const motorState = { a: null, b: null };

  // ── DOM refs ───────────────────────────────────────────────
  const btnConnect    = document.getElementById('btn-connect');
  const btnDisconnect = document.getElementById('btn-disconnect');
  const statusPill    = document.getElementById('status-pill');
  const statusText    = document.getElementById('status-text');
  const logEl         = document.getElementById('log');

  const motorBtns = document.querySelectorAll('.btn-motor');

  // ── Log helper ─────────────────────────────────────────────
  function log(msg, type = 'info') {
    const ts   = new Date().toLocaleTimeString('es', { hour12: false });
    const div  = document.createElement('div');
    div.className = 'entry';
    div.innerHTML = `<span class="ts">${ts}</span><span class="msg-${type}">${msg}</span>`;
    logEl.appendChild(div);
    logEl.scrollTop = logEl.scrollHeight;
  }

  // ── UI helpers ─────────────────────────────────────────────
  function setStatus(state, text) {
    statusPill.className = state;
    statusText.textContent = text;
  }

  function setMotorUI(motor, dir) {
    // dir: 'fwd' | 'bck' | null
    motorState[motor] = dir;
    const card  = document.getElementById(`card-${motor}`);
    const state = document.getElementById(`state-${motor}`);
    const fwdBtn = document.getElementById(`btn-${motor}-fwd`);
    const bckBtn = document.getElementById(`btn-${motor}-bck`);

    card.classList.remove('active-fwd', 'active-bck');
    fwdBtn.classList.remove('pressed');
    bckBtn.classList.remove('pressed');

    if (dir === 'fwd') {
      card.classList.add('active-fwd');
      fwdBtn.classList.add('pressed');
      state.textContent = '▲ AVANZANDO';
    } else if (dir === 'bck') {
      card.classList.add('active-bck');
      bckBtn.classList.add('pressed');
      state.textContent = '▼ RETROCEDIENDO';
    } else {
      state.textContent = 'PARADO';
    }
  }

  function enableButtons(enabled) {
    motorBtns.forEach(b => b.disabled = !enabled);
    btnDisconnect.style.display = enabled ? 'block' : 'none';
    btnConnect.style.display    = enabled ? 'none'  : 'block';
  }

  // ── Enviar valor a una característica ─────────────────────
  async function writeChar(key, value) {
    if (!chars[key]) { log(`Característica ${key} no disponible`, 'err'); return; }
    const encoder = new TextEncoder();
    await chars[key].writeValueWithoutResponse(encoder.encode(value));
  }

  // ── Lógica de botón ────────────────────────────────────────
  async function handleMotorBtn(motor, dir) {
    const isActive = motorState[motor] === dir;

    // Parar siempre primero (enviamos "0" a la característica activa)
    if (motorState[motor]) {
      await writeChar(`${motor}-${motorState[motor]}`, '0');
    }

    if (isActive) {
      // Era toggle: apagar
      setMotorUI(motor, null);
      log(`Motor ${motor.toUpperCase()} → STOP`, 'ok');
    } else {
      // Activar nueva dirección
      await writeChar(`${motor}-${dir}`, '1');
      setMotorUI(motor, dir);
      const label = dir === 'fwd' ? 'AVANCE' : 'RETROCESO';
      log(`Motor ${motor.toUpperCase()} → ${label}`, 'ok');
    }
  }

  // ── Conectar BLE ───────────────────────────────────────────
  btnConnect.addEventListener('click', async () => {
    if (!navigator.bluetooth) {
      log('Web Bluetooth no soportado. Usa Chrome/Edge en escritorio.', 'err');
      return;
    }
    try {
      log('Buscando dispositivo BLE...', 'info');
      setStatus('', 'BUSCANDO...');
      btnConnect.disabled = true;

      device = await navigator.bluetooth.requestDevice({
        filters: [{ name: 'ESP32-Motores' }],
        optionalServices: [SERVICE_UUID]
      });

      log(`Dispositivo: ${device.name}`, 'info');
      device.addEventListener('gattserverdisconnected', onDisconnected);

      server = await device.gatt.connect();
      log('GATT conectado', 'ok');

      const service = await server.getPrimaryService(SERVICE_UUID);
      log('Servicio BLE encontrado', 'ok');

      // Obtener las 4 características
      for (const [key, uuid] of Object.entries(CHAR_UUIDS)) {
        chars[key] = await service.getCharacteristic(uuid);
        log(`Característica ${key} lista`, 'ok');
      }

      setStatus('connected', 'CONECTADO');
      enableButtons(true);
      log('¡Listo para controlar los motores!', 'ok');

    } catch (err) {
      log(`Error: ${err.message}`, 'err');
      setStatus('error', 'ERROR');
      btnConnect.disabled = false;
    }
  });

  // ── Desconectar ────────────────────────────────────────────
  btnDisconnect.addEventListener('click', async () => {
    // Parar todos los motores antes de desconectar
    for (const key of Object.keys(chars)) {
      try { await writeChar(key, '0'); } catch(_) {}
    }
    if (device && device.gatt.connected) device.gatt.disconnect();
  });

  function onDisconnected() {
    chars = {};
    setStatus('error', 'DESCONECTADO');
    enableButtons(false);
    setMotorUI('a', null);
    setMotorUI('b', null);
    log('Dispositivo desconectado', 'err');
    btnConnect.disabled = false;
  }

  // ── Eventos de botones ────────────────────────────────────
  motorBtns.forEach(btn => {
    btn.addEventListener('click', () => {
      const motor = btn.dataset.motor;
      const dir   = btn.dataset.dir;
      handleMotorBtn(motor, dir).catch(err => log(`Error BLE: ${err.message}`, 'err'));
    });
  });

  // ── Init log ───────────────────────────────────────────────
  log('Página lista. Pulsa "Conectar" para empezar.', 'info');
  if (!navigator.bluetooth) {
    log('⚠ Web Bluetooth no detectado. Necesitas Chrome o Edge.', 'err');
  }
</script>
</body>
</html>
