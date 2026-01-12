<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
<meta name="theme-color" content="#1e1e1e">
<title>Sing on Pitch! (Fixed)</title>
<style>
  :root {
    --bg-color: #1e1e1e;
    --panel-bg: #2d2d2d;
    --primary: #4caf50;
    --primary-hover: #43a047;
    --accent: #ffd700;
    --text: #f0f0f0;
    --danger: #e57373;
  }

  * { box-sizing: border-box; touch-action: manipulation; -webkit-tap-highlight-color: transparent; }
  
  html, body {
    height: 100%; margin: 0; padding: 0; overflow: hidden;
    background: var(--bg-color);
    color: var(--text);
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
  }

  body {
    display: flex; justify-content: center; align-items: center;
    height: 100dvh; 
  }

  /* --- UI Containers --- */
  .container {
    width: 95%; max-width: 500px;
    text-align: center;
    display: flex; flex-direction: column; align-items: center;
    max-height: 100dvh; overflow-y: auto;
  }

  h1 { margin: 10px 0; font-weight: 300; letter-spacing: 1px; color: var(--primary); }
  p { color: #aaa; margin: 10px 0; font-size: 0.95rem; }

  /* --- Controls --- */
  .panel {
    background: var(--panel-bg);
    border-radius: 12px;
    padding: 15px;
    width: 100%;
    margin-bottom: 15px;
    box-shadow: 0 4px 6px rgba(0,0,0,0.3);
    border: 1px solid #444;
  }

  button {
    background: var(--panel-bg);
    border: 1px solid #555;
    color: #eee;
    padding: 12px 16px; /* Larger touch target */
    font-size: 1rem;
    border-radius: 8px;
    margin: 4px;
    cursor: pointer;
    transition: all 0.2s active;
    min-height: 48px; 
  }

  button:active { transform: scale(0.96); background: #444; }

  .btn-primary { background: var(--primary); border-color: var(--primary); color: white; font-weight: 600; width: 80%; margin: 8px auto; display: block; }
  .btn-danger { background: var(--danger); border-color: var(--danger); color: white; }

  /* --- Radio Toggle --- */
  .toggle-group { display: flex; justify-content: center; background: #222; border-radius: 20px; padding: 4px; margin: 10px auto; width: fit-content; }
  .toggle-group input { display: none; }
  .toggle-group label {
    padding: 8px 16px; border-radius: 16px; font-size: 0.85rem; cursor: pointer; color: #888; transition: 0.2s;
  }
  .toggle-group input:checked + label { background: var(--primary); color: white; font-weight: 600; }

  /* --- Game View --- */
  #gameContainer {
    position: fixed; top: 0; left: 0; width: 100%; height: 100dvh;
    background: #111; z-index: 100;
    display: none; justify-content: center; align-items: center;
  }

  canvas {
    background: #222;
    box-shadow: 0 0 20px rgba(0,0,0,0.5);
    max-width: 100%; max-height: 100%;
  }

  /* --- HUD --- */
  #hud, #debug {
    position: absolute; pointer-events: none; user-select: none;
    text-shadow: 0 1px 2px black;
  }
  #hud { top: 15px; left: 15px; font-size: 1.1rem; font-weight: bold; color: white; z-index: 10; }
  #debug { top: 15px; right: 15px; font-size: 0.9rem; color: #aaa; text-align: right; font-family: monospace; }
  
  #gameControls { 
    position: absolute; bottom: 20px; left: 0; width: 100%; 
    text-align: center; pointer-events: auto; z-index: 20; 
  }
  
  .feedback-float {
    position: absolute; font-weight: 900; font-size: 1.5rem;
    pointer-events: none; z-index: 20;
    animation: floatUp 0.8s ease-out forwards;
    text-shadow: 2px 2px 0 #000;
  }

  @keyframes floatUp {
    0% { opacity: 1; transform: translateY(0) scale(0.8); }
    50% { transform: translateY(-20px) scale(1.2); }
    100% { opacity: 0; transform: translateY(-40px) scale(1); }
  }

  /* --- Console Log for Mobile --- */
  #mobileConsole {
    position: fixed; bottom: 0; left: 0; width: 100%; height: 100px;
    background: rgba(0,0,0,0.8); color: #0f0; font-family: monospace;
    font-size: 10px; overflow-y: scroll; padding: 5px; z-index: 999;
    border-top: 1px solid #333; pointer-events: none;
    display: none; /* Hidden by default unless error */
  }

  /* --- Overlays --- */
  .overlay {
    position: fixed; top: 0; left: 0; width: 100%; height: 100%;
    background: rgba(0,0,0,0.85);
    display: flex; justify-content: center; align-items: center;
    z-index: 200; backdrop-filter: blur(5px);
  }
  .overlay-content {
    background: var(--panel-bg); padding: 30px; border-radius: 15px;
    text-align: center; border: 1px solid #555; width: 85%; max-width: 400px;
  }
</style>
</head>
<body>

<div id="mobileConsole"></div>

<div id="menu" class="container">
  <h1>Sing on Pitch!</h1>
  
  <div class="panel">
    <p>Range: <span id="octaveDisplay" style="color:white; font-weight:bold">C3 - C4</span></p>
    <div style="display:flex; justify-content:center; flex-wrap:wrap;">
      <button id="octaveDownBtn">Oct -</button>
      <button id="noteDownBtn">Note -</button>
      <button id="noteUpBtn">Note +</button>
      <button id="octaveUpBtn">Oct +</button>
    </div>

    <p style="margin-top:15px">Scale Type:</p>
    <div class="toggle-group">
      <input type="radio" id="sMaj" name="scale" value="major" checked><label for="sMaj">Major</label>
      <input type="radio" id="sMin" name="scale" value="minor"><label for="sMin">Minor</label>
      <input type="radio" id="sChr" name="scale" value="chromatic"><label for="sChr">Chrom</label>
    </div>
  </div>

  <p>Select Difficulty:</p>
  <button class="btn-primary" id="btnSingle">1-Note Challenge</button>
  <button class="btn-primary" id="btnDouble">2-Note Challenge</button>
  <button class="btn-primary" id="btnTriple">3-Note Challenge</button>
  
  <p id="statusMsg" style="color: #e57373; font-weight: bold;"></p>
</div>

<div id="gameContainer">
  <canvas id="gameCanvas"></canvas>
  <div id="hud">Score: <span id="scoreVal">0</span></div>
  <div id="debug">Init...</div>
  <div id="gameControls">
    <button class="btn-danger" id="quitBtn">Stop</button>
  </div>
</div>

<script>
// --- DEBUGGER ---
function log(msg) {
  console.log(msg);
  const c = document.getElementById('mobileConsole');
  c.style.display = 'block';
  c.innerHTML += `> ${msg}<br>`;
  c.scrollTop = c.scrollHeight;
}

window.onerror = function(msg, url, line) {
  log(`ERROR: ${msg} line ${line}`);
  alert(`Error: ${msg}`);
};

// --- CONSTANTS ---
const AUDIO_CTX_OPTS = { latencyHint: 'interactive' };
const YIN_THRESHOLD = 0.15;
const SMOOTHING = 0.15;
const PARTICLE_COUNT = 6;
const COIN_SPEED_BASE = 280;

// --- GLOBALS ---
let audioCtx, analyser, microphone, buffer;
let isAudioInit = false;
let animationId;
let lastTime = 0;
let gameRunning = false;
let mode = 'single';
let rootMidi = 48; // C3
let notes = [];
let currentFreq = 0;
let smoothedFreq = 0;
let playerY = 0;
let score = 0;
let coinList = [];
let particles = [];
let trail = [];

// --- ELEMENTS ---
const canvas = document.getElementById('gameCanvas');
const ctx = canvas.getContext('2d', { alpha: false });
const bgCanvas = document.createElement('canvas');
const bgCtx = bgCanvas.getContext('2d');
const elScore = document.getElementById('scoreVal');
const elDebug = document.getElementById('debug');
const elOctave = document.getElementById('octaveDisplay');

// ==========================================
// AUDIO SYSTEM
// ==========================================
async function initAudio() {
  if (isAudioInit) return true;
  
  log("Initializing Audio...");
  
  // 1. Check Secure Context
  if (window.location.protocol === 'file:') {
    alert("ERROR: This game cannot run from a local file. You must run it on a server (localhost or https).");
    return false;
  }

  try {
    const AudioContext = window.AudioContext || window.webkitAudioContext;
    if (!AudioContext) { alert("Web Audio API not supported"); return false; }
    
    audioCtx = new AudioContext(AUDIO_CTX_OPTS);
    
    // Resume context (needed for mobile Safari/Chrome)
    if (audioCtx.state === 'suspended') {
      await audioCtx.resume();
    }

    log("Requesting Mic...");
    const stream = await navigator.mediaDevices.getUserMedia({ 
      audio: { 
        echoCancellation: false, 
        noiseSuppression: true, 
        autoGainControl: false 
      } 
    });
    
    microphone = audioCtx.createMediaStreamSource(stream);
    analyser = audioCtx.createAnalyser();
    analyser.fftSize = 2048; 
    microphone.connect(analyser);
    buffer = new Float32Array(analyser.fftSize);
    isAudioInit = true;
    log("Audio Ready!");
    return true;
  } catch (e) {
    log("Audio Error: " + e.message);
    alert("Microphone Error: " + e.message + "\nCheck browser permissions.");
    return false;
  }
}

// YIN Pitch Detection
function getPitch() {
  analyser.getFloatTimeDomainData(buffer);
  const ns = buffer.length;
  const tauBuffer = new Float32Array(ns / 2);
  
  for (let tau = 0; tau < ns / 2; tau++) {
    tauBuffer[tau] = 0;
    for (let i = 0; i < ns / 2; i++) {
      const delta = buffer[i] - buffer[i + tau];
      tauBuffer[tau] += delta * delta;
    }
  }

  tauBuffer[0] = 1;
  let runningSum = 0;
  for (let tau = 1; tau < ns / 2; tau++) {
    runningSum += tauBuffer[tau];
    tauBuffer[tau] *= tau / (runningSum || 1);
  }

  let tauEstimate = -1;
  for (let tau = 1; tau < ns / 2; tau++) {
    if (tauBuffer[tau] < YIN_THRESHOLD) {
      while (tau + 1 < ns / 2 && tauBuffer[tau + 1] < tauBuffer[tau]) tau++;
      tauEstimate = tau;
      break;
    }
  }

  if (tauEstimate === -1) return null;

  const x0 = tauEstimate < 1 ? tauEstimate : tauEstimate - 1;
  const x2 = tauEstimate + 1 < ns / 2 ? tauEstimate + 1 : tauEstimate;
  if (x0 === tauEstimate || x2 === tauEstimate) return audioCtx.sampleRate / tauEstimate;
  
  const s0 = tauBuffer[x0];
  const s1 = tauBuffer[tauEstimate];
  const s2 = tauBuffer[x2];
  let betterTau = tauEstimate + (s2 - s0) / (2 * (2 * s1 - s2 - s0));
  return audioCtx.sampleRate / betterTau;
}

// ==========================================
// UTILS
// ==========================================
const NOTE_NAMES = ['C','C#','D','D#','E','F','F#','G','G#','A','A#','B'];
function midiToFreq(m) { return 440 * Math.pow(2, (m - 69) / 12); }
function freqToMidi(f) { return Math.round(12 * Math.log2(f / 440) + 69); }
function getNoteName(m) { return NOTE_NAMES[m % 12] + (Math.floor(m / 12) - 1); }

function getScaleNotes(root, type) {
  const intervals = type === 'major' ? [0,2,4,5,7,9,11,12] 
                  : type === 'minor' ? [0,2,3,5,7,8,10,12]
                  : [0,1,2,3,4,5,6,7,8,9,10,11,12];
  return intervals.map(i => {
    const m = root + i;
    return { midi: m, freq: midiToFreq(m), name: getNoteName(m) };
  });
}

// ==========================================
// GRAPHICS
// ==========================================
function resize() {
  canvas.width = window.innerWidth;
  canvas.height = window.innerHeight;
  bgCanvas.width = canvas.width;
  bgCanvas.height = canvas.height;
  if(notes.length > 0) renderStaticBackground();
}
window.addEventListener('resize', resize);

function renderStaticBackground() {
  bgCtx.fillStyle = '#111';
  bgCtx.fillRect(0, 0, bgCanvas.width, bgCanvas.height);
  
  const minF = notes[0].freq;
  const maxF = notes[notes.length-1].freq;
  const logMin = Math.log2(minF);
  const logMax = Math.log2(maxF);

  bgCtx.lineWidth = 1;
  bgCtx.font = '12px sans-serif';
  bgCtx.textBaseline = 'middle';

  notes.forEach(note => {
    const norm = (Math.log2(note.freq) - logMin) / (logMax - logMin);
    const y = bgCanvas.height - (bgCanvas.height * 0.1) - (norm * (bgCanvas.height * 0.8));
    
    // FIX: Using actual HEX color instead of invalid string
    const isRoot = note.midi % 12 === rootMidi % 12;
    bgCtx.strokeStyle = isRoot ? '#444' : '#2a2a2a';
    bgCtx.beginPath();
    bgCtx.moveTo(0, y);
    bgCtx.lineTo(bgCanvas.width, y);
    bgCtx.stroke();

    bgCtx.fillStyle = isRoot ? '#4caf50' : '#555';
    bgCtx.fillText(note.name, 5, y - 8);
  });
}

// ==========================================
// GAME LOOP
// ==========================================
function startGame(selectedMode) {
  log("Starting Game Mode: " + selectedMode);
  initAudio().then(ready => {
    if(!ready) return;
    
    mode = selectedMode;
    const sType = document.querySelector('input[name="scale"]:checked').value;
    notes = getScaleNotes(rootMidi, sType);
    
    score = 0; coinList = []; particles = []; trail = [];
    elScore.innerText = '0';
    
    resize();
    renderStaticBackground();
    
    document.getElementById('menu').style.display = 'none';
    document.getElementById('gameContainer').style.display = 'flex';
    
    gameRunning = true;
    lastTime = performance.now();
    scheduleMelody();
    loop();
  });
}

function scheduleMelody() {
  if(!gameRunning) return;
  const delay = 1000;
  const count = mode === 'single' ? 1 : mode === 'double' ? 2 : 3;
  
  setTimeout(() => {
    if(!gameRunning) return;
    for(let i=0; i<count; i++) {
      const note = notes[Math.floor(Math.random() * notes.length)];
      const logMin = Math.log2(notes[0].freq);
      const logMax = Math.log2(notes[notes.length-1].freq);
      const norm = (Math.log2(note.freq) - logMin) / (logMax - logMin);
      const y = canvas.height - (canvas.height * 0.1) - (norm * (canvas.height * 0.8));

      coinList.push({
        x: canvas.width + (i * 200),
        y: y,
        note: note,
        collected: false,
        r: 18
      });
      playTone(note.freq, i * 0.4);
    }
  }, delay);
}

function playTone(freq, delaySec) {
  const o = audioCtx.createOscillator();
  const g = audioCtx.createGain();
  o.connect(g); g.connect(audioCtx.destination);
  o.type = 'sine';
  o.frequency.value = freq;
  const now = audioCtx.currentTime + delaySec;
  g.gain.setValueAtTime(0, now);
  g.gain.linearRampToValueAtTime(0.1, now + 0.05);
  g.gain.exponentialRampToValueAtTime(0.001, now + 0.4);
  o.start(now);
  o.stop(now + 0.5);
}

function loop() {
  if (!gameRunning) return;
  animationId = requestAnimationFrame(loop);

  const now = performance.now();
  const dt = (now - lastTime) / 1000;
  lastTime = now;

  // Pitch Logic
  const detected = getPitch();
  const minF = notes[0].freq;
  const maxF = notes[notes.length-1].freq;
  let hasPitch = false;

  if (detected) {
    let f = detected;
    // Octave folding
    while (f < minF / 1.5 && f > 10) f *= 2;
    while (f > maxF * 1.5 && f > 10) f /= 2;
    
    if (smoothedFreq === 0) smoothedFreq = f;
    else smoothedFreq = smoothedFreq + (f - smoothedFreq) * SMOOTHING;
    currentFreq = f;
    hasPitch = true;
    elDebug.innerText = `${Math.round(currentFreq)}Hz ${getNoteName(freqToMidi(currentFreq))}`;
  } else {
    elDebug.innerText = "Sing!";
  }

  // Player Position
  const logMin = Math.log2(minF);
  const logMax = Math.log2(maxF);
  let targetY = canvas.height / 2;
  
  if (currentFreq > 10) {
    const norm = (Math.log2(smoothedFreq) - logMin) / (logMax - logMin);
    targetY = canvas.height - (canvas.height * 0.1) - (norm * (canvas.height * 0.8));
  }
  playerY = playerY + (targetY - playerY) * 0.1;

  // Trail
  if(hasPitch) trail.push({x: 100, y: playerY});
  trail.forEach(t => t.x -= COIN_SPEED_BASE * dt);
  trail = trail.filter(t => t.x > 0);

  // Draw
  ctx.drawImage(bgCanvas, 0, 0);

  // Draw Trail
  if(trail.length > 1) {
    ctx.strokeStyle = 'rgba(76, 175, 80, 0.5)';
    ctx.lineWidth = 4;
    ctx.beginPath();
    ctx.moveTo(trail[0].x, trail[0].y);
    for(let i=1; i<trail.length; i++) ctx.lineTo(trail[i].x, trail[i].y);
    ctx.stroke();
  }

  // Draw Coins & Collision
  const pX = 100;
  let allGone = coinList.length === 0;
  
  for (let i = coinList.length - 1; i >= 0; i--) {
    let c = coinList[i];
    c.x -= COIN_SPEED_BASE * dt;

    ctx.fillStyle = '#ffd700';
    ctx.beginPath();
    ctx.arc(c.x, c.y, c.r, 0, Math.PI*2);
    ctx.fill();
    ctx.fillStyle = '#000';
    ctx.font = '10px monospace';
    ctx.textAlign = 'center';
    ctx.fillText(c.note.name, c.x, c.y+3);

    // Collision
    if (!c.collected && Math.abs(c.x - pX) < 20) {
      if (Math.abs(c.y - playerY) < 30) {
        c.collected = true;
        score += 50;
        elScore.innerText = score;
        spawnParticles(c.x, c.y, '#00ff00');
        spawnFeedback("HIT!", c.x, c.y, '#00ff00');
        coinList.splice(i, 1);
      }
    } else if (c.x < -20) {
      coinList.splice(i, 1);
    }
  }

  // Draw Player
  ctx.fillStyle = hasPitch ? '#4caf50' : '#555';
  ctx.beginPath();
  ctx.arc(pX, playerY, 15, 0, Math.PI*2);
  ctx.fill();

  // Particles
  updateParticles(dt);

  // Next Round Logic
  if (coinList.length === 0 && !allGone) {
    // Just cleared coins
    scheduleMelody();
  } else if (coinList.length === 0 && allGone) {
      // Logic handled in scheduleMelody
      if(!waitFlag) {
          waitFlag = true;
          setTimeout(()=> { scheduleMelody(); waitFlag = false; }, 500);
      }
  }
}
let waitFlag = false;

// --- VFX ---
function spawnParticles(x, y, color) {
  for(let i=0; i<PARTICLE_COUNT; i++) {
    particles.push({x:x, y:y, vx:(Math.random()-0.5)*200, vy:(Math.random()-0.5)*200, life:1.0, color:color});
  }
}
function updateParticles(dt) {
  for(let i=particles.length-1; i>=0; i--) {
    let p = particles[i];
    p.x += p.vx*dt; p.y += p.vy*dt; p.life -= dt*2;
    if(p.life <= 0) { particles.splice(i,1); continue; }
    ctx.fillStyle = p.color;
    ctx.globalAlpha = p.life;
    ctx.fillRect(p.x, p.y, 4, 4);
    ctx.globalAlpha = 1.0;
  }
}
function spawnFeedback(text, x, y, color) {
  const el = document.createElement('div');
  el.className = 'feedback-float';
  el.innerText = text; el.style.color = color; el.style.left = x+'px'; el.style.top = y+'px';
  document.body.appendChild(el);
  setTimeout(()=>el.remove(), 800);
}

// --- CONTROLS ---
function updateMenuDisplay() {
  const s = getNoteName(rootMidi);
  const e = getNoteName(rootMidi + 12);
  elOctave.innerText = `${s} - ${e}`;
}

document.getElementById('btnSingle').addEventListener('click', () => startGame('single'));
document.getElementById('btnDouble').addEventListener('click', () => startGame('double'));
document.getElementById('btnTriple').addEventListener('click', () => startGame('triple'));

document.getElementById('octaveUpBtn').onclick = () => { if(rootMidi < 84) rootMidi+=12; updateMenuDisplay(); };
document.getElementById('octaveDownBtn').onclick = () => { if(rootMidi > 24) rootMidi-=12; updateMenuDisplay(); };
document.getElementById('noteUpBtn').onclick = () => { if(rootMidi < 90) rootMidi++; updateMenuDisplay(); };
document.getElementById('noteDownBtn').onclick = () => { if(rootMidi > 21) rootMidi--; updateMenuDisplay(); };
document.getElementById('quitBtn').onclick = () => location.reload();

updateMenuDisplay();
</script>
</body>
</html>
