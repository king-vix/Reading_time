
html = r'''<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<meta name="theme-color" content="#10251f">
<title>King-Vix Study Zone</title>
<style>
:root{--bg:#0b1513;--panel:#14231f;--panel2:#1b302a;--text:#f3f7f4;--muted:#b2c3bb;--green:#7ee0ad;--line:#2d4940;--gold:#f5d78e}
*{box-sizing:border-box}body{margin:0;background:radial-gradient(ellipse at top,#1c3930 0%,var(--bg) 55%);color:var(--text);font-family:system-ui,-apple-system,Segoe UI,Roboto,sans-serif;line-height:1.5}
.wrap{max-width:1050px;margin:auto;padding:22px 16px 48px}.top{display:flex;justify-content:space-between;align-items:center;gap:12px;flex-wrap:wrap}.brand{font-weight:800;letter-spacing:.4px}.pill{border:1px solid var(--line);border-radius:999px;padding:7px 12px;color:var(--green);font-size:.85rem}
h1{font-size:clamp(2rem,6vw,3.6rem);line-height:1.04;margin:24px 0 12px;letter-spacing:-1.5px}.accent{color:var(--green)}.intro{color:var(--muted);max-width:650px;margin-bottom:24px}
.grid{display:grid;grid-template-columns:1.15fr .85fr;gap:16px}.panel{background:linear-gradient(145deg,rgba(27,48,42,.96),rgba(17,32,28,.97));border:1px solid var(--line);border-radius:22px;padding:20px;box-shadow:0 12px 35px #0002}
.panel h2{margin:0 0 14px;font-size:1.15rem}.timer{font-size:clamp(3rem,10vw,5rem);font-weight:800;letter-spacing:-2px;text-align:center;font-variant-numeric:tabular-nums;margin:12px 0 0}.phase{text-align:center;color:var(--green);font-weight:700}.sub{text-align:center;color:var(--muted);font-size:.9rem}
.progress{height:8px;background:#0b1713;border-radius:99px;overflow:hidden;margin:18px 0}.progress span{display:block;height:100%;width:0;background:linear-gradient(90deg,#56b985,#a5f2c6);transition:width .25s}
.row{display:flex;gap:9px;flex-wrap:wrap;align-items:center}.row.center{justify-content:center}.btn{border:0;border-radius:12px;padding:11px 15px;font-weight:750;cursor:pointer;background:var(--green);color:#10251d}.btn.secondary{background:var(--panel2);color:var(--text);border:1px solid var(--line)}.btn:focus-visible,input:focus-visible,select:focus-visible{outline:3px solid var(--gold);outline-offset:2px}
select,input[type=range]{accent-color:var(--green)}select{background:#0d1b17;color:var(--text);border:1px solid var(--line);border-radius:10px;padding:9px;max-width:100%}
.music-status{color:var(--muted);font-size:.9rem;margin:10px 0 14px}.visualizer{display:flex;gap:5px;align-items:end;justify-content:center;height:45px;margin:12px 0}.bar{width:7px;border-radius:5px;background:var(--green);height:9px;opacity:.7}.playing .bar{animation:bounce .8s ease-in-out infinite alternate}.bar:nth-child(2n){animation-delay:.2s}.bar:nth-child(3n){animation-delay:.4s}@keyframes bounce{to{height:38px;opacity:1}}
.tasks{display:grid;gap:10px}.task{display:flex;gap:11px;align-items:flex-start;padding:12px;border:1px solid var(--line);border-radius:13px;background:#10201b}.task input{margin-top:5px;transform:scale(1.2);accent-color:var(--green)}.task strong{display:block}.task small{color:var(--muted)}.task.done{opacity:.62}.task.done strong{text-decoration:line-through}
.schedule{display:grid;gap:8px}.slot{display:grid;grid-template-columns:110px 1fr;gap:10px;padding:11px;border-radius:12px;background:#10201b;border:1px solid var(--line)}.slot time{color:var(--green);font-weight:750;font-variant-numeric:tabular-nums}.slot small{display:block;color:var(--muted)}
.tip{border-left:3px solid var(--gold);padding:10px 13px;background:#302c1d66;border-radius:0 10px 10px 0;color:#f4e7c3;font-size:.92rem;margin-top:15px}
footer{text-align:center;color:var(--muted);font-size:.85rem;margin-top:22px}
@media(max-width:760px){.grid{grid-template-columns:1fr}.wrap{padding:16px 12px 32px}.panel{padding:17px}.slot{grid-template-columns:95px 1fr}}
</style>
</head>
<body>
<div class="wrap">
  <div class="top"><div class="brand">👑 KING-VIX <span class="accent">STUDY ZONE</span></div><div class="pill">IJMB • FOCUS MODE</div></div>
  <h1>Your goals.<br><span class="accent">One focused night.</span></h1>
  <p class="intro">A little structure, steady practice, and calm background sound. Built for your IJMB subjects: Mathematics, Physics and Chemistry. Your progress stays saved in this browser on this device.</p>

  <div class="grid">
    <section class="panel">
      <h2>⏱️ Focus timer</h2>
      <div class="phase" id="phase">Ready when you are</div>
      <div class="timer" id="timer">50:00</div>
      <div class="sub" id="timerNote">Study for 50 minutes, then take a break.</div>
      <div class="progress"><span id="timerProgress"></span></div>
      <div class="row center">
        <button class="btn" id="startBtn">▶ Start focus</button>
        <button class="btn secondary" id="pauseBtn">Ⅱ Pause</button>
        <button class="btn secondary" id="resetBtn">↻ Reset</button>
      </div>
      <div class="row center" style="margin-top:14px">
        <label for="session">Session:</label>
        <select id="session">
          <option value="50">Study • 50 min</option>
          <option value="10">Short break • 10 min</option>
          <option value="15">Long break • 15 min</option>
          <option value="40">Revision • 40 min</option>
        </select>
      </div>
      <div class="tip">Tiny rule: put your phone on Do Not Disturb, keep only your notes and calculator nearby, and start with one specific task.</div>
    </section>

    <section class="panel">
      <h2>🎧 Focus sound</h2>
      <p style="color:var(--muted);margin-top:-5px">Gentle ambient tones generated by this page. No song downloads or internet needed.</p>
      <div class="visualizer" id="visualizer" aria-hidden="true"></div>
      <div class="row">
        <button class="btn" id="musicBtn">▶ Play focus sound</button>
        <button class="btn secondary" id="musicStop">■ Stop</button>
      </div>
      <div class="music-status" id="musicStatus">Sound is off. Tap Play to begin.</div>
      <div class="row" style="justify-content:space-between">
        <label for="volume">Volume</label><span id="volumeText">20%</span>
      </div>
      <input id="volume" type="range" min="0" max="50" value="20" style="width:100%">
      <p class="sub" style="text-align:left;margin-top:12px">Tip: keep it quiet enough that the music doesn't compete with your thinking.</p>
    </section>
  </div>

  <section class="panel" style="margin-top:16px">
    <h2>✅ Tonight's checklist</h2>
    <p style="color:var(--muted);margin-top:-5px">Tick each task as you finish it. Your ticks are saved automatically.</p>
    <div class="progress"><span id="taskProgress"></span></div>
    <div id="taskCount" class="sub" style="text-align:left;margin-bottom:12px">0 of 7 tasks complete</div>
    <div class="tasks" id="tasks">
      <label class="task"><input type="checkbox" data-task="recall"><span><strong>Recall today's lectures</strong><small>Write what you remember before opening your notes.</small></span></label>
      <label class="task"><input type="checkbox" data-task="math"><span><strong>Mathematics practice</strong><small>Understand one topic and solve questions yourself.</small></span></label>
      <label class="task"><input type="checkbox" data-task="physics"><span><strong>Physics concepts and calculations</strong><small>Explain the idea, then practise using the formulas.</small></span></label>
      <label class="task"><input type="checkbox" data-task="chem"><span><strong>Chemistry review</strong><small>Work on equations, theory or calculations from lectures.</small></span></label>
      <label class="task"><input type="checkbox" data-task="questions"><span><strong>Answer exam-style questions</strong><small>Try without notes before checking answers.</small></span></label>
      <label class="task"><input type="checkbox" data-task="mistakes"><span><strong>Correct mistakes</strong><small>Record what went wrong and redo one question.</small></span></label>
      <label class="task"><input type="checkbox" data-task="tomorrow"><span><strong>Prepare for tomorrow</strong><small>Choose the first topic you'll study next time.</small></span></label>
    </div>
    <div class="row" style="margin-top:14px"><button class="btn secondary" id="clearTasks">Reset tonight's checklist</button></div>
  </section>

  <section class="panel" style="margin-top:16px">
    <h2>🗓️ Your night plan • 8 PM–12 AM</h2>
    <div class="schedule">
      <div class="slot"><time>8:00–8:20</time><div><strong>Lecture recall</strong><small>Review today's notes and list questions you still have.</small></div></div>
      <div class="slot"><time>8:20–9:10</time><div><strong>Main subject</strong><small>Learn one difficult topic deeply.</small></div></div>
      <div class="slot"><time>9:10–9:20</time><div><strong>Break</strong><small>Stand up, stretch, drink water.</small></div></div>
      <div class="slot"><time>9:20–10:10</time><div><strong>Second subject</strong><small>Work through examples, then try one alone.</small></div></div>
      <div class="slot"><time>10:10–10:25</time><div><strong>Long break</strong><small>Snack and rest your eyes.</small></div></div>
      <div class="slot"><time>10:25–11:10</time><div><strong>Practice questions</strong><small>Use IJMB-style questions and mark your work.</small></div></div>
      <div class="slot"><time>11:10–11:20</time><div><strong>Break</strong><small>Reset before the final session.</small></div></div>
      <div class="slot"><time>11:20–12:00</time><div><strong>Third subject + wrap-up</strong><small>Recall key ideas, correct mistakes, plan tomorrow.</small></div></div>
    </div>
    <div class="tip">Subject rotation: Monday Maths + Physics; Tuesday Chemistry + Maths; Wednesday Physics + Chemistry; Thursday Maths + Physics; Friday Chemistry + weakest subject; Saturday timed questions; Sunday lighter revision.</div>
  </section>
  <footer>Made for steady progress, not perfection. Save this file and open it in your browser whenever you study. 🌱</footer>
</div>
<script>
const $ = id => document.getElementById(id);
let total = 50*60, remaining = total, interval = null, endAt = null;
function fmt(s){const m=Math.floor(Math.max(0,s)/60), sec=Math.max(0,s)%60;return String(m).padStart(2,'0')+':'+String(sec).padStart(2,'0')}
function updateTimer(){
  $('timer').textContent=fmt(remaining);
  $('timerProgress').style.width=((total-remaining)/total*100)+'%';
}
function stopTimer(){if(interval){clearInterval(interval);interval=null}endAt=null}
function tick(){
  if(endAt!==null) remaining=Math.max(0,Math.ceil((endAt-Date.now())/1000));
  updateTimer();
  if(remaining<=0){stopTimer();$('phase').textContent='Session complete!';$('timerNote').textContent='Take a break, or choose your next session.';try{beep()}catch(e){}}
}
function beep(){if(!audioCtx)return;const o=audioCtx.createOscillator(),g=audioCtx.createGain();o.frequency.value=660;g.gain.value=.08;o.connect(g);g.connect(audioCtx.destination);o.start();o.stop(audioCtx.currentTime+.22)}
$('startBtn').onclick=()=>{if(interval)return; if(remaining<=0)remaining=total;endAt=Date.now()+remaining*1000;$('phase').textContent='Focus in progress';$('timerNote').textContent='Stay with one task until the timer ends.';interval=setInterval(tick,250);tick()};
$('pauseBtn').onclick=()=>{if(interval){remaining=Math.max(0,Math.ceil((endAt-Date.now())/1000));stopTimer();$('phase').textContent='Paused';tick()}};
$('resetBtn').onclick=()=>{stopTimer();total=Number($('session').value)*60;remaining=total;$('phase').textContent='Ready when you are';$('timerNote').textContent='Study for the selected time, then take a break.';updateTimer()};
$('session').onchange=()=>{stopTimer();total=Number($('session').value)*60;remaining=total;$('phase').textContent='Ready when you are';updateTimer()};

let audioCtx=null, master=null, oscillators=[], musicOn=false;
function setupAudio(){
  const AC=window.AudioContext||window.webkitAudioContext;
  if(!AC){$('musicStatus').textContent='This browser does not support generated audio.';return false}
  if(!audioCtx){audioCtx=new AC();master=audioCtx.createGain();master.gain.value=Number($('volume').value)/100;master.connect(audioCtx.destination);
    // Soft, low-volume ambient chord. No recording or external track.
    [110,164.81,220,329.63].forEach((freq,i)=>{const osc=audioCtx.createOscillator(),gain=audioCtx.createGain(),filter=audioCtx.createBiquadFilter();osc.type=i===1?'triangle':'sine';osc.frequency.value=freq;gain.gain.value=[.20,.10,.07,.035][i];filter.type='lowpass';filter.frequency.value=700;osc.connect(filter);filter.connect(gain);gain.connect(master);osc.start();oscillators.push({osc,gain,base:[.20,.10,.07,.035][i]})});
  }return true
}
$('musicBtn').onclick=async()=>{if(!setupAudio())return;await audioCtx.resume();musicOn=true;master.gain.setTargetAtTime(Number($('volume').value)/100,audioCtx.currentTime,.15);$('musicStatus').textContent='Focus sound is playing. Keep the volume gentle.';$('musicBtn').textContent='♫ Sound playing';$('visualizer').classList.add('playing')};
$('musicStop').onclick=async()=>{musicOn=false;if(audioCtx&&master){master.gain.setTargetAtTime(0,audioCtx.currentTime,.15)}$('musicStatus').textContent='Sound is off.';$('musicBtn').textContent='▶ Play focus sound';$('visualizer').classList.remove('playing')};
$('volume').oninput=()=>{$('volumeText').textContent=$('volume').value+'%';if(audioCtx&&master&&musicOn)master.gain.setTargetAtTime(Number($('volume').value)/100,audioCtx.currentTime,.1)};
for(let i=0;i<13;i++){const b=document.createElement('span');b.className='bar';$('visualizer').appendChild(b)}
const taskBoxes=[...document.querySelectorAll('[data-task]')];
function loadTasks(){let saved={};try{saved=JSON.parse(localStorage.getItem('kv-study-tasks')||'{}')}catch(e){}taskBoxes.forEach(box=>{box.checked=!!saved[box.dataset.task];box.closest('.task').classList.toggle('done',box.checked)});updateTasks()}
function updateTasks(){const count=taskBoxes.filter(x=>x.checked).length;$('taskCount').textContent=count+' of '+taskBoxes.length+' tasks complete';$('taskProgress').style.width=(count/taskBoxes.length*100)+'%';const saved={};taskBoxes.forEach(box=>saved[box.dataset.task]=box.checked);try{localStorage.setItem('kv-study-tasks',JSON.stringify(saved))}catch(e){}}
taskBoxes.forEach(box=>box.addEventListener('change',()=>{box.closest('.task').classList.toggle('done',box.checked);updateTasks()}));
$('clearTasks').onclick=()=>{taskBoxes.forEach(box=>{box.checked=false;box.closest('.task').classList.remove('done')});updateTasks()};
loadTasks();updateTimer();
</script>
</body>
</html>'''
path = Path("/mnt/data/king_vix_study_zone.html")
path.write_text(html, encoding="utf-8")
print(f"Created: {path}")
