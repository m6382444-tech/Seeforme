<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>SeeForMe — AI visual assistance</title>
<style>
:root{
  --bg:#0a1a2f; --surface:#12294a; --ink:#ffffff; --muted:#b9c8de;
  --accent:#ffd400; --accent-ink:#0a1a2f; --danger:#ff6b5e; --line:#2f4a75;
  --r:20px;
}
@media (prefers-color-scheme: light){
  :root.auto{--bg:#fffdf2;--surface:#ffffff;--ink:#0a1a2f;--muted:#33465f;--accent:#0a1a2f;--accent-ink:#ffd400;--line:#0a1a2f}
}
:root.contrast{--bg:#000;--surface:#000;--ink:#fff;--muted:#fff;--line:#fff;--accent:#ffd400;--accent-ink:#000}
*{box-sizing:border-box}
html{font-size:calc(18px * var(--scale,1))}
body{margin:0;background:var(--bg);color:var(--ink);font-family:"Atkinson Hyperlegible","Segoe UI",system-ui,sans-serif;line-height:1.5;
  padding:env(safe-area-inset-top,0) 16px env(safe-area-inset-bottom,0)}
main{max-width:760px;margin:0 auto;padding:16px 0 40px;display:grid;gap:16px}
h1{font-size:1.6rem;margin:0}
h2{font-size:1.15rem;margin:0 0 8px}
header{display:flex;justify-content:space-between;align-items:center;gap:12px}
.tag{color:var(--muted);margin:0}
:focus-visible{outline:4px solid var(--accent);outline-offset:3px}
button{font:inherit;cursor:pointer}
.stage{position:relative;border:3px solid var(--line);border-radius:var(--r);overflow:hidden;background:#000;aspect-ratio:4/3}
video,canvas#snap,.stage img{width:100%;height:100%;object-fit:cover;display:block}
canvas#snap{display:none}
.placeholder{position:absolute;inset:0;display:grid;place-items:center;text-align:center;padding:24px;color:#fff}
.modes{display:grid;grid-template-columns:repeat(auto-fit,minmax(140px,1fr));gap:10px}
.mode{background:var(--surface);color:var(--ink);border:3px solid var(--line);border-radius:var(--r);padding:16px 10px;font-weight:700;min-height:72px}
.mode[aria-pressed="true"]{background:var(--accent);color:var(--accent-ink);border-color:var(--accent)}
.big{width:100%;min-height:104px;font-size:1.5rem;font-weight:800;border:0;border-radius:var(--r);background:var(--accent);color:var(--accent-ink)}
.row{display:grid;grid-template-columns:1fr 1fr;gap:10px}
.sec{min-height:64px;background:var(--surface);color:var(--ink);border:3px solid var(--line);border-radius:var(--r);font-weight:700}
.sec.listening{background:var(--danger);color:#000;border-color:var(--danger)}
.card{background:var(--surface);border:3px solid var(--line);border-radius:var(--r);padding:16px}
#result{font-size:1.25rem;min-height:3.5em;margin:0}
ul#history{list-style:none;margin:0;padding:0;display:grid;gap:8px}
ul#history li{border-top:2px solid var(--line);padding-top:8px}
ul#history time{color:var(--muted);font-size:.85rem;display:block}
label{display:flex;justify-content:space-between;align-items:center;gap:12px;margin:10px 0}
input[type=range]{width:55%;height:36px;accent-color:var(--accent)}
.sw{display:flex;gap:10px;align-items:center}
input[type=checkbox]{width:28px;height:28px;accent-color:var(--accent)}
.sr{position:absolute;width:1px;height:1px;overflow:hidden;clip:rect(0 0 0 0)}
.busy{animation:pulse 1s infinite alternate}
@media (prefers-reduced-motion: reduce){.busy{animation:none}}
@keyframes pulse{to{opacity:.6}}
</style>
</head>
<body>
<a class="sr" href="#main">Skip to main content</a>
<main id="main">
  <header>
    <div>
      <h1>SeeForMe</h1>
      <p class="tag">Point your camera. Hear what is around you.</p>
    </div>
    <button class="sec" id="repeat" style="width:auto;padding:0 18px" aria-label="Repeat last description">Repeat</button>
  </header>

  <section class="stage" aria-label="Camera view">
    <video id="video" autoplay playsinline muted aria-hidden="true"></video>
    <canvas id="snap"></canvas>
    <div class="placeholder" id="placeholder">
      <div><strong>Camera is off</strong><br>Press “Start camera” to begin.</div>
    </div>
  </section>

  <div class="row">
    <button class="sec" id="camBtn">Start camera</button>
    <button class="sec" id="voiceBtn" aria-pressed="false">Speak a command</button>
  </div>

  <section aria-labelledby="mh">
    <h2 id="mh">What do you need?</h2>
    <div class="modes" role="group" aria-label="Choose a mode">
      <button class="mode" data-mode="scene" aria-pressed="true">Describe scene</button>
      <button class="mode" data-mode="text" aria-pressed="false">Read text</button>
      <button class="mode" data-mode="obstacle" aria-pressed="false">Check my path</button>
      <button class="mode" data-mode="money" aria-pressed="false">Identify money</button>
    </div>
  </section>

  <button class="big" id="go">Describe now</button>

  <section class="card" aria-labelledby="rh">
    <h2 id="rh">Result</h2>
    <p id="result" role="status" aria-live="polite">Nothing described yet.</p>
  </section>

  <section class="card" aria-labelledby="hh">
    <h2 id="hh">Earlier results</h2>
    <ul id="history"><li>No history yet.</li></ul>
  </section>

  <section class="card" aria-labelledby="sh">
    <h2 id="sh">Settings</h2>
    <label>Voice speed
      <input type="range" id="rate" min="0.6" max="1.8" step="0.1" value="1" aria-label="Voice speed">
    </label>
    <label>Text size
      <input type="range" id="scale" min="1" max="1.6" step="0.1" value="1" aria-label="Text size">
    </label>
    <label class="sw"><span>High contrast</span><input type="checkbox" id="hc"></label>
    <label class="sw"><span>Vibrate on result</span><input type="checkbox" id="vib" checked></label>
    <label>Backend URL (leave empty for demo)
      <input id="api" type="url" placeholder="https://your-server/describe" style="width:55%;min-height:44px;font:inherit">
    </label>
  </section>
</main>

<script>
/* ===== SeeForMe front end =====
   Backend contract (POST JSON): { image: "<base64 jpeg>", mode: "scene|text|obstacle|money" }
   Response JSON: { description: "..." }
   Your server should call a vision model (e.g. Claude) with a mode-specific prompt. */

const $ = s => document.querySelector(s);
const video = $('#video'), snap = $('#snap'), result = $('#result');
let stream = null, mode = 'scene', last = '', busy = false;

const LABELS = {scene:'Describe now', text:'Read text now', obstacle:'Check my path', money:'Identify money'};
const DEMO = {
  scene:'Demo: You are in a bright room. A wooden table is ahead, with a laptop and a white mug on it. A door is to your left.',
  text:'Demo: The sign reads “Pharmacy, open 9 a.m. to 6 p.m.”',
  obstacle:'Demo: Path is clear for about three meters. A chair is slightly to your right.',
  money:'Demo: This looks like a 500 rupee note.'
};

/* ---- speech out ---- */
function speak(text){
  if(!('speechSynthesis' in window)) return;
  speechSynthesis.cancel();
  const u = new SpeechSynthesisUtterance(text);
  u.rate = +$('#rate').value;
  speechSynthesis.speak(u);
}
function announce(text, save=true){
  result.textContent = text; last = text; speak(text);
  if($('#vib').checked && navigator.vibrate) navigator.vibrate(120);
  if(save) addHistory(text);
}
function addHistory(t){
  const ul = $('#history');
  if(ul.firstElementChild && ul.firstElementChild.textContent==='No history yet.') ul.innerHTML='';
  const li = document.createElement('li');
  li.innerHTML = '<time></time><span></span>';
  li.querySelector('time').textContent = new Date().toLocaleTimeString([], {hour:'2-digit',minute:'2-digit'}) + ' · ' + mode;
  li.querySelector('span').textContent = t;
  ul.prepend(li);
}

/* ---- camera ---- */
async function toggleCamera(){
  if(stream){
    stream.getTracks().forEach(t=>t.stop()); stream=null; video.srcObject=null;
    $('#placeholder').style.display='grid'; $('#camBtn').textContent='Start camera';
    speak('Camera off'); return;
  }
  try{
    stream = await navigator.mediaDevices.getUserMedia({video:{facingMode:'environment'},audio:false});
    video.srcObject = stream; $('#placeholder').style.display='none';
    $('#camBtn').textContent='Stop camera'; speak('Camera on. Ready.');
  }catch(e){
    announce('Camera unavailable. Allow camera access in your browser settings, then try again.', false);
  }
}

/* ---- describe ---- */
async function describe(){
  if(busy) return;
  if(!stream){ announce('Start the camera first.', false); return; }
  busy = true; $('#go').classList.add('busy'); $('#go').disabled = true;
  speak('Looking.');
  snap.width = video.videoWidth || 640; snap.height = video.videoHeight || 480;
  snap.getContext('2d').drawImage(video,0,0,snap.width,snap.height);
  const image = snap.toDataURL('image/jpeg',0.8).split(',')[1];
  const url = $('#api').value.trim();
  try{
    let text;
    if(!url){ await new Promise(r=>setTimeout(r,900)); text = DEMO[mode]; }
    else{
      const res = await fetch(url,{method:'POST',headers:{'Content-Type':'application/json'},body:JSON.stringify({image,mode})});
      if(!res.ok) throw new Error(res.status);
      text = (await res.json()).description;
    }
    announce(text);
  }catch(e){
    announce('I could not reach the service. Check your connection and try again.', false);
  }finally{
    busy = false; $('#go').classList.remove('busy'); $('#go').disabled = false;
  }
}

/* ---- modes ---- */
function setMode(m){
  mode = m;
  document.querySelectorAll('.mode').forEach(b=>b.setAttribute('aria-pressed', b.dataset.mode===m));
  $('#go').textContent = LABELS[m];
  speak(LABELS[m].replace(' now','') + ' mode');
}
document.querySelectorAll('.mode').forEach(b=>b.addEventListener('click',()=>setMode(b.dataset.mode)));

/* ---- voice commands ---- */
const SR = window.SpeechRecognition || window.webkitSpeechRecognition;
function listen(){
  const btn = $('#voiceBtn');
  if(!SR){ announce('Voice commands are not supported in this browser.', false); return; }
  const rec = new SR(); rec.lang = navigator.language || 'en-US';
  btn.classList.add('listening'); btn.setAttribute('aria-pressed','true'); btn.textContent='Listening…';
  rec.onresult = e => handleCommand(e.results[0][0].transcript.toLowerCase());
  rec.onerror = () => announce('I did not catch that. Try again.', false);
  rec.onend = () => { btn.classList.remove('listening'); btn.setAttribute('aria-pressed','false'); btn.textContent='Speak a command'; };
  rec.start();
}
function handleCommand(t){
  if(/read|text|sign/.test(t)) setMode('text');
  else if(/path|obstacle|walk|safe/.test(t)) setMode('obstacle');
  else if(/money|note|cash|currency/.test(t)) setMode('money');
  else if(/describe|scene|around|what/.test(t)) setMode('scene');
  else if(/repeat|again/.test(t)) return speak(last||'Nothing to repeat.');
  else if(/start camera|camera on/.test(t)) return stream||toggleCamera();
  else if(/stop camera|camera off/.test(t)) return stream&&toggleCamera();
  else return announce('Command not recognised. Say describe, read, path, or money.', false);
  setTimeout(describe, 700);
}

/* ---- settings & events ---- */
$('#camBtn').onclick = toggleCamera;
$('#go').onclick = describe;
$('#voiceBtn').onclick = listen;
$('#repeat').onclick = () => speak(last || 'Nothing to repeat.');
$('#hc').onchange = e => document.documentElement.classList.toggle('contrast', e.target.checked);
$('#scale').oninput = e => document.documentElement.style.setProperty('--scale', e.target.value);
document.documentElement.classList.add('auto');
addEventListener('keydown', e => {           // keyboard shortcuts: Space = describe, V = voice
  if(['INPUT','BUTTON'].includes(document.activeElement.tagName)) return;
  if(e.code==='Space'){ e.preventDefault(); describe(); }
  if(e.key==='v') listen();
});
</script>
</body>
</html>
