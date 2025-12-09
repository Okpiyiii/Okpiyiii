<!--
  index.html
  Personal repository front page: visitor badge + typing animation + skills showcase
  INSTRUCTIONS: Replace USERNAME and REPO in the visitor badge URL (line with src for visitor badge).
  Save this file to your repo root or docs/ then enable GitHub Pages (if you want it live).
-->

<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Soumyadeep — Dev Playground</title>
  <style>
    :root{--bg:#0f1724;--card:#0b1220;--accent:#7c3aed;--muted:#9aa4b2;--glass:rgba(255,255,255,0.04)}
    *{box-sizing:border-box}
    body{font-family:Inter,system-ui,Segoe UI,Roboto,Helvetica,Arial,sans-serif;margin:0;background:linear-gradient(180deg,#071022 0%, #071a2a 100%);color:#e6eef6;display:flex;align-items:center;justify-content:center;min-height:100vh;padding:24px}
    .card{width:100%;max-width:880px;background:linear-gradient(180deg,rgba(255,255,255,0.02),transparent);border:1px solid rgba(255,255,255,0.04);padding:28px;border-radius:14px;box-shadow:0 8px 30px rgba(2,6,23,0.6)}
    header{display:flex;align-items:center;gap:18px}
    .avatar{width:84px;height:84px;border-radius:12px;background:linear-gradient(135deg,var(--accent),#06b6d4);display:flex;align-items:center;justify-content:center;font-weight:700;font-size:34px;color:white}
    h1{margin:0;font-size:20px}
    p.lead{margin:6px 0 0;color:var(--muted)}
    .badges{margin-left:auto;display:flex;gap:8px;align-items:center}
    .badge img{height:26px}

    /* Typing animation */
    .typing-wrap{margin-top:20px;display:flex;gap:12px;align-items:center}
    .cursor{width:2px;height:1.2em;background:var(--accent);animation:blink 1s steps(2) infinite}
    @keyframes blink{50%{opacity:0}}
    .typing{font-family:monospace,ui-monospace,Menlo,Monaco,Consolas,"Liberation Mono";font-size:18px;background:linear-gradient(90deg,#e6eef6, #b6d4ff);-webkit-background-clip:text;background-clip:text;color:transparent}

    /* Skills */
    .skills{display:flex;flex-wrap:wrap;gap:10px;margin-top:18px}
    .chip{background:var(--glass);padding:8px 12px;border-radius:999px;color:#dfe9f8;font-weight:600;font-size:13px;border:1px solid rgba(255,255,255,0.03)}

    /* Progress bars */
    .skill-list{margin-top:18px;display:grid;gap:10px}
    .skill{display:flex;align-items:center;gap:12px}
    .skill-name{width:140px;color:var(--muted);font-size:14px}
    .progress{flex:1;background:rgba(255,255,255,0.03);border-radius:999px;height:10px;overflow:hidden}
    .progress > span{display:block;height:100%;background:linear-gradient(90deg,var(--accent),#06b6d4);border-radius:999px}

    footer{margin-top:20px;color:var(--muted);display:flex;justify-content:space-between;align-items:center}
    a.link{color:#cfe9ff;text-decoration:none}

    /* Responsive */
    @media (max-width:600px){header{flex-direction:column;align-items:flex-start}.badges{margin-left:0;width:100%;justify-content:flex-start}}
  </style>
</head>
<body>
  <main class="card" role="main">
    <header>
      <div class="avatar">SP</div>
      <div>
        <h1>Hi, I’m <strong>Soumyadeep</strong> 👋</h1>
        <p class="lead">ECE student • ML & AI • Data enthusiast — I build models that tell stories.</p>

        <div class="typing-wrap">
          <div class="typing" id="typing"></div>
          <div class="cursor" aria-hidden="true"></div>
        </div>

        <div class="skills" aria-label="skills">
          <div class="chip">Python 🐍</div>
          <div class="chip">Machine Learning 🤖</div>
          <div class="chip">Data Viz 📊</div>
          <div class="chip">Pandas • NumPy</div>
          <div class="chip">Git • GitHub</div>
        </div>

      </div>

      <div class="badges" aria-hidden="true">
        <!-- Replace USERNAME and REPO with your GitHub username and repository name -->
        <div class="badge">
          <img alt="visitor badge" src="https://visitor-badge.laobi.works/badge?page_id=USERNAME.REPO">
        </div>
        <!-- Optional: GitHub stars/last-commit badges from shields.io -->
        <div class="badge">
          <img alt="repo stars" src="https://img.shields.io/github/stars/USERNAME/REPO?style=for-the-badge&label=Stars&logo=github">
        </div>
      </div>
    </header>

    <section class="skill-list" aria-labelledby="skills-heading">
      <div class="skill"><div class="skill-name">Python</div><div class="progress" title="Python 90%"><span style="width:90%"></span></div></div>
      <div class="skill"><div class="skill-name">Machine Learning</div><div class="progress" title="ML 80%"><span style="width:80%"></span></div></div>
      <div class="skill"><div class="skill-name">Data Visualization</div><div class="progress" title="Viz 75%"><span style="width:75%"></span></div></div>
      <div class="skill"><div class="skill-name">Web / HTML</div><div class="progress" title="HTML 70%"><span style="width:70%"></span></div></div>
    </section>

    <footer>
      <div>🔭 Currently: Predictive models & anomaly detection</div>
      <div><a class="link" href="#">Say hi 👋</a></div>
    </footer>
  </main>

  <script>
    // Typing animation — list of phrases to rotate
    const phrases = [
      'Building ML models.',
      'Visualizing data beautifully.',
      'Experimenting with predictive analytics.',
      'Open to collaborations!'
    ];

    const typingEl = document.getElementById('typing');
    let phraseIndex = 0, charIndex = 0, deleting = false;

    function tick(){
      const current = phrases[phraseIndex];
      if(!deleting){
        charIndex++;
        typingEl.textContent = current.slice(0,charIndex);
        if(charIndex === current.length){
          deleting = true;
          setTimeout(tick,1200);
          return;
        }
      } else {
        charIndex--;
        typingEl.textContent = current.slice(0,charIndex);
        if(charIndex === 0){
          deleting = false;
          phraseIndex = (phraseIndex+1) % phrases.length;
        }
      }
      setTimeout(tick, deleting ? 60 : 90);
    }
    // Start after short delay
    setTimeout(tick, 600);
  </script>
</body>
</html>



