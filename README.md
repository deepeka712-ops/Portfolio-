<!DOCTYPE html><html lang="en" data-theme="dark">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Student Portfolio — Future of Space Exploration</title>
  <meta name="description" content="A sleek, responsive student portfolio themed around the future of space exploration. Built with HTML, CSS, and JavaScript." />
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Outfit:wght@300;400;500;600;700;800&display=swap" rel="stylesheet">
  <style>
    :root{
      --bg: #0b1020;          /* Deep space */
      --bg-soft:#0f1630;
      --text:#e6e8f2;         /* Starlight */
      --muted:#a9b0d0;        /* Moon dust */
      --brand:#77e6ff;        /* Neon cyan */
      --brand-2:#a78bfa;      /* Nebula violet */
      --accent:#20f1b4;       /* Aurora green */
      --card:#121935;
      --border:rgba(255,255,255,.08);
      --shadow: 0 10px 30px rgba(0,0,0,.4);
    }
    [data-theme="light"]{
      --bg:#f6f8ff; --bg-soft:#ffffff; --text:#0f1222; --muted:#3b3f59;
      --brand:#0ea5e9; --brand-2:#7c3aed; --accent:#059669; --card:#ffffff; --border:rgba(0,0,0,.1);
      --shadow: 0 8px 26px rgba(0,0,0,.08);
    }
    *{box-sizing:border-box}
    html,body{height:100%}
    body{
      margin:0; font-family:'Outfit',system-ui,Segoe UI,Roboto,Helvetica,Arial,sans-serif;
      background:radial-gradient(1200px 800px at 10% -10%, rgba(119,230,255,.08), transparent 60%),
                 radial-gradient(1000px 700px at 110% 20%, rgba(167,139,250,.10), transparent 60%),
                 var(--bg);
      color:var(--text); line-height:1.6; letter-spacing:.2px;
    }
    a{color:var(--brand); text-decoration:none}
    a:hover{text-decoration:underline}
    .container{width:min(1200px, 92%); margin-inline:auto}
    header{
      position:sticky; top:0; z-index:50; backdrop-filter:saturate(140%) blur(8px);
      background:linear-gradient(to bottom, rgba(10,15,30,.85), rgba(10,15,30,.55));
      border-bottom:1px solid var(--border);
    }
    .nav{display:flex; align-items:center; justify-content:space-between; padding:14px 0}
    .brand{display:flex; gap:12px; align-items:center; font-weight:700; letter-spacing:.5px}
    .logo{width:34px; height:34px; border-radius:50%;
      background: conic-gradient(from 210deg, var(--brand), var(--brand-2), var(--accent), var(--brand));
      box-shadow:0 0 0 2px rgba(255,255,255,.06), inset 0 0 18px rgba(255,255,255,.15);
    }
    .nav a{padding:8px 10px; border-radius:12px}
    .nav a:hover{background:rgba(255,255,255,.06)}
    .controls{display:flex; gap:10px; align-items:center}
    .btn{border:1px solid var(--border); background:linear-gradient(180deg, var(--bg-soft), var(--card));
      color:var(--text); padding:10px 14px; border-radius:14px; cursor:pointer; box-shadow:var(--shadow);
      transition:transform .18s ease, background .2s ease, border-color .2s ease; font-weight:600;
    }
    .btn:hover{transform:translateY(-1px); border-color:rgba(255,255,255,.16)}
    .btn.primary{background:linear-gradient(135deg, rgba(119,230,255,.22), rgba(167,139,250,.18)); border-color:transparent}/* Hero */
.hero{display:grid; grid-template-columns:1.2fr .8fr; gap:28px; align-items:center; padding:60px 0 40px}
.hero h1{font-size:clamp(30px, 3.2vw, 56px); line-height:1.1; margin:0 0 12px}
.hero p{color:var(--muted); max-width:62ch}
.tags{display:flex; flex-wrap:wrap; gap:8px; margin-top:14px}
.tag{font-size:12px; padding:6px 10px; border-radius:999px; border:1px solid var(--border); color:var(--muted)}
.scene{
  aspect-ratio:1.2/1; border-radius:22px; position:relative; overflow:hidden; border:1px solid var(--border);
  background: radial-gradient(120px 120px at 70% 40%, rgba(119,230,255,.35), transparent 60%),
              linear-gradient(160deg, var(--card), transparent 50%),
              radial-gradient(700px 300px at -10% 120%, rgba(167,139,250,.14), transparent 60%), var(--bg-soft);
  box-shadow: var(--shadow);
}
/* star field */
.stars, .stars:before, .stars:after{content:""; position:absolute; inset:0; background-repeat:repeat;}
.stars{background-image: radial-gradient(1px 1px at 20px 30px, rgba(255,255,255,.8), transparent 2px),
                           radial-gradient(1px 1px at 80px 120px, rgba(255,255,255,.7), transparent 2px),
                           radial-gradient(1px 1px at 200px 60px, rgba(255,255,255,.9), transparent 2px);
       animation: drift 80s linear infinite; opacity:.85}
.stars:before{background-image: radial-gradient(1px 1px at 40px 50px, rgba(255,255,255,.6), transparent 2px),
                              radial-gradient(1px 1px at 100px 200px, rgba(255,255,255,.65), transparent 2px);
              animation: drift 120s linear infinite reverse; opacity:.6}
.stars:after{background-image: radial-gradient(1px 1px at 10px 90px, rgba(255,255,255,.55), transparent 2px),
                             radial-gradient(1px 1px at 160px 20px, rgba(255,255,255,.5), transparent 2px);
             animation: drift 200s linear infinite; opacity:.45}
@keyframes drift{from{transform:translateY(0)} to{transform:translateY(-600px)}}

/* Sections */
section{padding:60px 0; border-top:1px solid var(--border)}
h2{font-size:clamp(22px, 2.4vw, 34px); margin:0 0 18px}
.grid{display:grid; gap:18px}
.grid.projects{grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));}
.card{background:linear-gradient(180deg, var(--bg-soft), var(--card)); border:1px solid var(--border);
      border-radius:20px; padding:16px; box-shadow:var(--shadow)}
.card h3{margin:4px 0 8px}
.meta{font-size:13px; color:var(--muted)}
.chip{display:inline-block; font-size:12px; padding:6px 10px; border:1px solid var(--border); border-radius:999px; margin:4px 6px 0 0; color:var(--muted)}

.filters{display:flex; gap:8px; flex-wrap:wrap; margin-bottom:14px}
.filters button{font-size:13px}

/* Timeline */
.timeline{position:relative; padding-left:22px}
.timeline:before{content:""; position:absolute; top:6px; bottom:6px; left:8px; width:2px; background:linear-gradient(180deg, var(--brand), transparent)}
.event{position:relative; margin-bottom:14px}
.event:before{content:""; position:absolute; left:-1px; top:8px; width:10px; height:10px; border-radius:50%; background:var(--brand); box-shadow:0 0 0 3px rgba(119,230,255,.18)}

/* Gallery */
.gallery{display:grid; grid-template-columns:repeat(auto-fit,minmax(160px,1fr)); gap:12px}
.thumb{aspect-ratio:1.4/1; border-radius:16px; overflow:hidden; border:1px solid var(--border); background:linear-gradient(135deg, rgba(119,230,255,.2), rgba(167,139,250,.2));}

/* Footer */
footer{padding:40px 0 60px; text-align:center; color:var(--muted)}

/* Responsive tweaks */
@media (max-width: 900px){ .hero{grid-template-columns:1fr; gap:18px; padding-top:30px} }

/* Print-friendly resume export */
@media print{ header,.controls{display:none!important} body{background:white; color:black} .card, .scene{box-shadow:none} }

  </style>
</head>
<body>
  <header>
    <div class="container nav">
      <div class="brand" aria-label="Site brand">
        <div class="logo" aria-hidden="true"></div>
        <span>Future of Space Exploration — Portfolio</span>
      </div>
      <nav class="controls" aria-label="Primary">
        <a href="#projects">Projects</a>
        <a href="#skills">Skills</a>
        <a href="#timeline">Timeline</a>
        <a href="#contact">Contact</a>
        <button class="btn" id="themeToggle" aria-pressed="true" title="Toggle light/dark">Toggle Theme</button>
        <button class="btn primary" id="printBtn" title="Export as PDF">Export</button>
      </nav>
    </div>
  </header>  <main class="container">
    <!-- HERO -->
    <section class="hero" aria-labelledby="intro-title">
      <div>
        <h1 id="intro-title">Hi, I'm <span style="color:var(--brand)">[Your Name]</span> — aspiring space technologist</h1>
        <p>
          I design, prototype, and communicate ideas for humanity's future among the stars — from
          reusable launch systems to AI-driven deep space exploration. This portfolio showcases my
          projects, research, and public outreach.
        </p>
        <div class="tags" aria-label="Focus tags">
          <span class="tag">Reusable Rockets</span>
          <span class="tag">Lunar Habitats</span>
          <span class="tag">Mars ISRU</span>
          <span class="tag">AI Robotics</span>
          <span class="tag">Space Policy</span>
        </div>
        <div class="controls" style="margin-top:16px">
          <a class="btn primary" href="#projects">See Projects</a>
          <a class="btn" href="#contact">Get in touch</a>
        </div>
      </div>
      <div class="scene" role="img" aria-label="Stylized space scene with stars and gradients">
        <div class="stars"></div>
      </div>
    </section><!-- PROJECTS -->
<section id="projects" aria-labelledby="projects-title">
  <h2 id="projects-title">Featured Projects</h2>
  <p class="meta">Filter projects by track (all items are placeholders — replace with your own!)</p>
  <div class="filters" role="tablist" aria-label="Project filters">
    <button class="btn" data-filter="all" role="tab" aria-selected="true">All</button>
    <button class="btn" data-filter="engineering" role="tab">Engineering</button>
    <button class="btn" data-filter="research" role="tab">Research</button>
    <button class="btn" data-filter="software" role="tab">Software</button>
    <button class="btn" data-filter="outreach" role="tab">Outreach</button>
  </div>
  <div class="grid projects" id="projectGrid" aria-live="polite"></div>
</section>

<!-- SKILLS -->
<section id="skills" aria-labelledby="skills-title">
  <h2 id="skills-title">Skills & Tools</h2>
  <div class="grid" style="grid-template-columns:repeat(auto-fit,minmax(260px,1fr))">
    <div class="card">
      <h3>Engineering</h3>
      <p class="meta">Systems thinking · CAD · Rapid prototyping · Testing</p>
      <div>
        <span class="chip">Fusion 360</span>
        <span class="chip">SolidWorks</span>
        <span class="chip">MATLAB</span>
        <span class="chip">Simulink</span>
      </div>
    </div>
    <div class="card">
      <h3>Software</h3>
      <p class="meta">Full‑stack web · Python for data · Embedded</p>
      <div>
        <span class="chip">HTML</span>
        <span class="chip">CSS</span>
        <span class="chip">JavaScript</span>
        <span class="chip">Python</span>
        <span class="chip">C/C++</span>
      </div>
    </div>
    <div class="card">
      <h3>Space Domain</h3>
      <p class="meta">Mission design · Orbital mechanics · Space policy</p>
      <div>
        <span class="chip">STK (AGI)</span>
        <span class="chip">GMAT</span>
        <span class="chip">CubeSat</span>
        <span class="chip">ISRU</span>
      </div>
    </div>
  </div>
</section>

<!-- TIMELINE -->
<section id="timeline" aria-labelledby="timeline-title">
  <h2 id="timeline-title">Journey</h2>
  <div class="timeline">
    <div class="event">
      <div class="card">
        <strong>2025 — Mars Rover Mini</strong>
        <p class="meta">Built a 4‑wheel rover prototype with autonomous navigation using AprilTags.</p>
      </div>
    </div>
    <div class="event">
      <div class="card">
        <strong>2024 — Lunar Habitat Design Sprint</strong>
        <p class="meta">Led a 4‑person team to design a 3D‑printed regolith dome with thermal control.</p>
      </div>
    </div>
    <div class="event">
      <div class="card">
        <strong>2023 — Satellite Data Visualizer</strong>
        <p class="meta">Web app to visualize TLE orbits and ground tracks in the browser.</p>
      </div>
    </div>
  </div>
</section>

<!-- GALLERY -->
<section aria-labelledby="gallery-title">
  <h2 id="gallery-title">Gallery</h2>
  <div class="gallery">
    <div class="thumb" role="img" aria-label="Concept render: lunar base"></div>
    <div class="thumb" role="img" aria-label="Concept render: Mars greenhouse"></div>
    <div class="thumb" role="img" aria-label="Concept render: Starship landing"></div>
    <div class="thumb" role="img" aria-label="Concept render: CubeSat"></div>
  </div>
</section>

<!-- CONTACT -->
<section id="contact" aria-labelledby="contact-title">
  <h2 id="contact-title">Contact</h2>
  <div class="grid" style="grid-template-columns:1.2fr .8fr">
    <form class="card" id="contactForm" aria-label="Contact form">
      <label for="name">Name</label>
      <input id="name" name="name" class="input" required placeholder="Your full name" />

      <label for="email">Email</label>
      <input id="email" name="email" type="email" class="input" required placeholder="you@example.com" />

      <label for="message">Message</label>
      <textarea id="message" name="message" class="input" rows="5" required placeholder="Say hello…"></textarea>

      <div class="controls" style="margin-top:10px">
        <button class="btn primary" type="submit">Send</button>
        <button class="btn" type="reset">Reset</button>
      </div>
    </form>
    <div class="card">
      <h3>Links</h3>
      <p class="meta">Add your profiles here</p>
      <ul>
        <li>GitHub: <a href="#">github.com/yourname</a></li>
        <li>LinkedIn: <a href="#">linkedin.com/in/yourname</a></li>
        <li>Orcid / Google Scholar: <a href="#">your-id</a></li>
      </ul>
    </div>
  </div>
</section>

  </main>  <footer>
    <div class="container">
      <p>© <span id="year"></span> Your Name — Built with HTML • CSS • JS · Theme: <span id="themeLabel">Dark</span></p>
    </div>
  </footer>  <style>
    /* Minimal form/input styles */
    label{display:block; font-weight:600; margin:8px 0 6px}
    .input{width:100%; padding:12px 14px; border-radius:14px; border:1px solid var(--border); background:var(--bg-soft); color:var(--text)}
    .input:focus{outline:2px solid var(--brand); border-color:transparent}
  </style>  <script>
    // ===== Content you can customize quickly =====
    const PROJECTS = [
      {
        title: "Starship Reuse Study",
        track: "engineering",
        blurb: "Reducing turnaround time via heat-shield swap modules.",
        tech: ["CAD", "Materials", "Testing"],
        link: "#"
      },
      {
        title: "Lunar ISRU Simulator",
        track: "software",
        blurb: "Python + JS simulator for regolith-to-oxygen pipelines.",
        tech: ["Python", "WebGL", "Three.js"],
        link: "#"
      },
      {
        title: "Mars Greenhouse Paper",
        track: "research",
        blurb: "Closed-loop life support analysis with algae bioreactors.",
        tech: ["LaTeX", "CFD", "Biology"],
        link: "#"
      },
      {
        title: "Space Outreach Camp",
        track: "outreach",
        blurb: "Taught 60+ school students orbital mechanics basics.",
        tech: ["Education", "Workshops"],
        link: "#"
      },
      {
        title: "CubeSat ADCS",
        track: "engineering",
        blurb: "Reaction wheel control and sun-sensor fusion (EKF).",
        tech: ["C++", "MATLAB", "Control"],
        link: "#"
      }
    ];

    // ===== Helper functions =====
    const $ = (q, c=document) => c.querySelector(q);
    const $$ = (q, c=document) => [...c.querySelectorAll(q)];

    function renderProjects(filter="all"){ 
      const grid = $('#projectGrid');
      grid.innerHTML = '';
      const items = PROJECTS.filter(p => filter==='all' ? true : p.track===filter);
      if(items.length===0){
        grid.innerHTML = `<p class="meta">No projects yet for "${filter}".</p>`;
        return;
      }
      for(const p of items){
        const el = document.createElement('article');
        el.className = 'card';
        el.innerHTML = `
          <div class="meta">${p.track.toUpperCase()}</div>
          <h3>${p.title}</h3>
          <p>${p.blurb}</p>
          <div>${p.tech.map(t=>`<span class='chip'>${t}</span>`).join('')}</div>
          <div class="controls" style="margin-top:10px">
            <a class="btn" href="${p.link}">View</a>
          </div>
        `;
        grid.appendChild(el);
      }
    }

    // ===== Theme Toggle =====
    const themeToggle = $('#themeToggle');
    const themeLabel = $('#themeLabel');
    const pref = localStorage.getItem('theme') || 'dark';
    document.documentElement.setAttribute('data-theme', pref);
    themeLabel.textContent = pref === 'dark' ? 'Dark' : 'Light';

    themeToggle.addEventListener('click', () => {
      const current = document.documentElement.getAttribute('data-theme');
      const next = current === 'dark' ? 'light' : 'dark';
      document.documentElement.setAttribute('data-theme', next);
      localStorage.setItem('theme', next);
      themeLabel.textContent = next === 'dark' ? 'Dark' : 'Light';
    });

    // ===== Filters =====
    $$('.filters [data-filter]').forEach(btn=>{
      btn.addEventListener('click', () =>{
        $$('.filters [role="tab"]').forEach(b=>b.setAttribute('aria-selected', 'false'));
        btn.setAttribute('aria-selected','true');
        renderProjects(btn.dataset.filter);
      });
    })

    // ===== Contact (demo only) =====
    $('#contactForm').addEventListener('submit', (e)=>{
      e.preventDefault();
      const name = $('#name').value.trim();
      const email = $('#email').value.trim();
      const msg = $('#message').value.trim();
      alert(`Thanks, ${name}! I'll reply to ${email}.\n\nMessage:\n${msg}`);
      e.target.reset();
    });

    // ===== Print / Export =====
    $('#printBtn').addEventListener('click', ()=> window.print());

    // ===== Init =====
    renderProjects('all');
    $('#year').textContent = new Date().getFullYear();
  </script></body>
</html>
