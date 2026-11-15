```html
<!DOCTYPE html>
<html lang="en" class="scroll-smooth">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Techbuilder | Learn Computers</title>
<meta name="description" content="Learn computer basics, hardware, software, PC building and troubleshooting with Techbuilder">
<script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
<style>
*{box-sizing:border-box;margin:0;padding:0}
body{font-family:Arial,sans-serif;background:#fff;color:#17243a;line-height:1.6}
header{height:78px;border-top:4px solid #1769e0;border-bottom:1px solid #e7ebf0;display:flex;align-items:center;justify-content:space-between;padding:0 8%;position:sticky;top:0;background:rgba(255,255,255,.96);backdrop-filter:blur(8px);z-index:20}
.logo{display:inline-flex;align-items:center;gap:10px;font-size:24px;font-weight:800;color:#17243a;text-decoration:none;letter-spacing:-0.4px}
.logo-mark{display:inline-flex;align-items:center;justify-content:center;width:36px;height:36px;border-radius:10px;background:linear-gradient(135deg,#1769e0 0%,#0ea5e9 100%);box-shadow:0 6px 14px rgba(23,105,224,.28)}
.logo-text span{color:#1769e0}
nav a{color:#344054;text-decoration:none;margin-left:23px;font-size:14px;font-weight:600}
nav a:hover,nav a.active-nav{color:#1769e0}
nav a.active-nav{border-bottom:2px solid #1769e0;padding-bottom:4px}
.page-section{display:none}
.page-section.active-section{display:block}
.hero{padding:75px 8%;background:#f7faff;text-align:center}
.hero h1{font-size:clamp(32px,5vw,54px);line-height:1.15;max-width:750px;margin:auto}
.hero p{color:#667085;max-width:620px;margin:18px auto}
.search{max-width:550px;margin:28px auto;display:flex;background:white;border:1px solid #dce3ed;border-radius:10px;overflow:hidden}
.search input{flex:1;min-width:0;padding:15px;border:0;outline:0;font-size:15px}
.search button,.btn{background:#1769e0;color:white;border:0;padding:14px 22px;cursor:pointer;text-decoration:none;border-radius:8px;font-weight:600;font-size:14px;display:inline-block}
.btn-outline{background:#fff;color:#1769e0;border:1px solid #1769e0;padding:11px 18px;border-radius:8px;cursor:pointer;font-weight:600;font-size:13px}
.btn-outline:hover{background:#f0f6ff}
.container{max-width:1150px;margin:auto;padding:65px 22px}
.heading{text-align:center;margin-bottom:35px}
.heading h2{font-size:30px}
.heading p{color:#667085;margin-top:8px}
.grid{display:grid;grid-template-columns:repeat(3,1fr);gap:20px}
.card{border:1px solid #e7ebf0;border-radius:12px;padding:25px;transition:.2s;background:#fff}
.card:hover{transform:translateY(-4px);box-shadow:0 8px 25px #17243a10}
.card .icon{font-size:32px;margin-bottom:12px}
.card h3{font-size:19px;margin-bottom:8px}
.card p{font-size:14px;color:#667085;margin-bottom:16px}
.card a{color:#1769e0;text-decoration:none;font-weight:bold;font-size:14px;cursor:pointer}
.feature{background:#f7faff;border-radius:16px;padding:35px;display:flex;align-items:center;justify-content:space-between;gap:20px}
.feature p{color:#667085;margin:10px 0 20px}
footer{background:#101d32;color:white;padding:35px 8%;text-align:center}
footer p{color:#bdc8d8;font-size:13px;margin-top:8px}
#noResults{text-align:center;color:#667085;padding:25px;display:none}

/* Interactive 3D Lab & Weekly Guide Panels */
.lab-wrap{display:grid;grid-template-columns:1.15fr 1fr;gap:24px;align-items:stretch}
.canvas-box{position:relative;background:radial-gradient(circle at 55% 40%,#eef5ff,#dce8fb 80%);border:1px solid #dce3ed;border-radius:16px;min-height:380px;overflow:hidden}
.canvas-box canvas{display:block;width:100%;height:100%;cursor:grab;touch-action:none}
.canvas-box canvas:active{cursor:grabbing}
.hud-top{position:absolute;top:14px;left:14px;background:rgba(255,255,255,.92);border:1px solid #dce3ed;padding:6px 12px;border-radius:999px;font-size:12px;font-weight:700;color:#17243a;pointer-events:none}
.hud-bottom{position:absolute;bottom:14px;left:14px;right:14px;display:flex;flex-wrap:wrap;gap:8px;justify-content:space-between}
.hud-btn{background:rgba(255,255,255,.94);border:1px solid #cfd9e8;color:#17243a;padding:7px 13px;border-radius:999px;font-size:12px;font-weight:600;cursor:pointer}
.hud-btn.active{background:#1769e0;color:#fff;border-color:#1769e0}
.info-panel{border:1px solid #e7ebf0;border-radius:16px;padding:24px;background:#fff;display:flex;flex-direction:column;justify-content:space-between;gap:16px}
.part-tabs{display:flex;flex-wrap:wrap;gap:8px;margin-bottom:20px;justify-content:center}
.part-tab{border:1px solid #dce3ed;background:#fff;color:#344054;padding:8px 14px;border-radius:999px;font-size:13px;font-weight:600;cursor:pointer}
.part-tab.active{background:#1769e0;color:#fff;border-color:#1769e0}
.pill-list{display:flex;flex-wrap:wrap;gap:6px;margin-top:8px}
.pill{background:#f0f6ff;border:1px solid #d4e4fc;color:#1769e0;padding:4px 10px;border-radius:999px;font-size:12px;font-weight:600}
.guide-card{border:1px solid #e7ebf0;border-radius:16px;padding:30px;background:#fff}
.guide-meta{font-size:12px;color:#667085;background:#f7faff;border:1px solid #e7ebf0;padding:10px 14px;border-radius:8px;margin-bottom:18px}
.guide-section{margin-top:20px}
.guide-section h4{font-size:17px;color:#17243a;margin-bottom:8px}
.guide-section ul,.guide-section ol{padding-left:20px;color:#344054;font-size:14px}
.guide-section li{margin-bottom:6px}
.quiz-box{margin-top:22px;background:#f7faff;border:1px solid #dce3ed;border-radius:12px;padding:20px}
.quiz-opt{display:block;width:100%;text-align:left;margin-top:8px;padding:10px 14px;border-radius:8px;border:1px solid #dce3ed;background:#fff;cursor:pointer;font-size:14px;color:#17243a}
.quiz-opt:hover{border-color:#1769e0}
.quiz-opt.correct{background:#ecfdf3;border-color:#12b76a;color:#027a48;font-weight:600}
.quiz-opt.wrong{background:#fef3f2;border-color:#f04438;color:#b42318}
.book-reader{background:#f7faff;border:1px solid #dce3ed;border-radius:14px;padding:22px;margin-top:16px;font-size:14.5px;line-height:1.7;color:#1e293b}
.book-grid{display:grid;grid-template-columns:repeat(2,minmax(0,1fr));gap:16px;margin-top:14px}
.book-rect{background:#fff;border:1px solid #dce3ed;border-radius:12px;padding:18px;box-shadow:0 2px 10px rgba(15,23,42,.03)}
.book-wide{grid-column:1 / -1}
@media(max-width:780px){.book-grid{grid-template-columns:1fr}}
.book-reader h3{font-size:24px;color:#1769e0;border-bottom:2px solid #eef5ff;padding-bottom:10px;margin-bottom:16px}
.book-reader h4{font-size:19px;color:#17243a;margin:24px 0 10px}
.book-reader h5{font-size:16px;color:#1769e0;margin:18px 0 8px}
.book-reader p{margin-bottom:14px}
.book-fig{background:#f7faff;border:1px dashed #93c5fd;border-radius:10px;padding:12px 16px;margin:14px 0;font-size:13.5px;color:#1e40af}
.book-cmd{background:#0f172a;color:#e2e8f0;font-family:monospace;font-size:13px;line-height:1.6;padding:14px 16px;border-radius:10px;margin:12px 0;overflow-x:auto;white-space:pre}
@media(max-width:600px){.book-reader{padding:18px;font-size:14.5px}}
.course-badge{display:inline-block;background:#eef5ff;color:#1769e0;font-size:11px;font-weight:700;padding:3px 9px;border-radius:999px;margin-bottom:10px}
.playground{display:grid;grid-template-columns:1fr 1fr;gap:16px;margin-top:16px}
.code-editor{width:100%;min-height:170px;font-family:monospace;font-size:13px;padding:12px;border:1px solid #dce3ed;border-radius:10px;background:#0f172a;color:#e2e8f0;resize:vertical}
.code-preview{border:1px solid #dce3ed;border-radius:10px;padding:14px;background:#fff;min-height:170px}
@media(max-width:750px){.playground{grid-template-columns:1fr}}

@media(max-width:850px){.lab-wrap{grid-template-columns:1fr}}
@media(max-width:750px){
header{padding:0 5%;height:auto;min-height:70px;flex-wrap:wrap}
nav{width:100%;padding:10px 0 15px;display:flex;gap:17px;overflow-x:auto}
nav a{margin:0;white-space:nowrap}
.grid{grid-template-columns:repeat(2,1fr)}
.feature{display:block}
}
@media(max-width:480px){.grid{grid-template-columns:1fr}.hero{padding:55px 5%}}
</style>
</head>
<body>

<header>
  <a href="#sec-home" class="logo section-jump" data-target="sec-home">
    <span class="logo-mark" aria-hidden="true">
      <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="#ffffff" stroke-width="2.2" stroke-linecap="round" stroke-linejoin="round">
        <path d="M12 2L2 7l10 5 10-5-10-5z"/>
        <path d="M2 17l10 5 10-5"/>
        <path d="M2 12l10 5 10-5"/>
      </svg>
    </span>
    <span class="logo-text">Tech<span>builder</span></span>
  </a>
  <nav id="mainNav">
    <a href="#sec-home" class="nav-tab active-nav" data-target="sec-home">Home</a>
    <a href="#sec-topics" class="nav-tab" data-target="sec-topics">Topics</a>
    <a href="#sec-hardware" class="nav-tab" data-target="sec-hardware">3D Hardware</a>
    <a href="#sec-courses" class="nav-tab" data-target="sec-courses">Courses</a>
    <a href="#sec-builder" class="nav-tab" data-target="sec-builder">Builder</a>
    <a href="#sec-basics" class="nav-tab" data-target="sec-basics">Guides</a>
    <a href="#sec-about" class="nav-tab" data-target="sec-about">About</a>
  </nav>
</header>

<section class="hero page-section active-section" id="sec-home">
  <div style="display:inline-block;background:linear-gradient(135deg,#e0f2fe 0%,#dbeafe 100%);border:1px solid #7dd3fc;color:#0369a1;font-size:13.5px;font-weight:700;padding:9px 20px;border-radius:999px;margin-bottom:20px;box-shadow:0 6px 18px rgba(14,165,233,0.18)">
    Thanks for visiting Techbuilder! Your curiosity for learning computers &amp; coding makes you unstoppable.
  </div>
  <h1>Understand Computers.<br>Build Your Knowledge.</h1>
  <p>Your beginner-friendly destination to learn computer hardware in 3D, software, PC building, and troubleshooting.</p>
  <div class="search" style="margin-bottom:10px">
    <input id="searchInput" type="search" placeholder="Live search anything: CPU, RTX 4060, SEBA, PAN/LAN, HTML, Python...">
    <button type="button" id="searchBtn">Search</button>
  </div>
  <div id="liveSearchResults" style="display:none;max-width:550px;margin:0 auto 22px;background:#fff;border:1px solid #dce3ed;border-radius:12px;text-align:left;box-shadow:0 12px 30px rgba(15,23,42,.1);max-height:290px;overflow-y:auto"></div>
  <a href="#sec-hardware" class="btn section-jump" data-target="sec-hardware">Explore 3D PC →</a>
</section>

<section class="container page-section" id="sec-topics" style="padding-top:35px">
  <div class="heading">
    <h2>Explore Computer Topics</h2>
    <p>Everything you need to know about computers in one place.</p>
  </div>

  <div class="grid" id="topicGrid">
    <article class="card" data-search="computer basics beginner introduction ipos input output">
      <div class="icon">💻</div>
      <h3>Computer Basics</h3>
      <p>Understand computers, their functions, types and how data flows from click to screen.</p>
      <a href="#sec-basics" class="section-jump" data-target="sec-basics" data-guide="basics">Learn More →</a>
    </article>

    <article class="card" data-search="hardware cpu ram gpu motherboard ssd psu ryzen rtx 4060 samsung 990 pro">
      <div class="icon">⚙️</div>
      <h3>Computer Hardware</h3>
      <p>Discover CPU, RAM, GPU, motherboard, storage and real product names in 3D.</p>
      <a href="#sec-hardware" class="section-jump" data-target="sec-hardware">Explore 3D →</a>
    </article>

    <article class="card" data-search="software windows linux macos applications os">
      <div class="icon">🖥️</div>
      <h3>Software &amp; OS</h3>
      <p>Learn about operating systems, applications and how software talks to hardware.</p>
      <a href="#sec-basics" data-topic="software" data-target="sec-basics" class="topic-jump section-jump">Learn More →</a>
    </article>

    <article class="card" data-search="pc build gaming computer budget components">
      <div class="icon">🔧</div>
      <h3>PC Building</h3>
      <p>Understand compatible computer components and beginner-to-pro PC configurations.</p>
      <a href="#sec-hardware" class="section-jump" data-target="sec-hardware">Inspect Parts →</a>
    </article>

    <article class="card" data-search="troubleshooting repair problems overheating slow">
      <div class="icon">🛠️</div>
      <h3>Troubleshooting</h3>
      <p>Understand common computer issues, thermal throttling, and quick fixes.</p>
      <a href="#sec-basics" data-topic="troubleshooting" data-target="sec-basics" class="topic-jump section-jump">Learn More →</a>
    </article>

    <article class="card" data-search="technology internet networking wifi router">
      <div class="icon">🌐</div>
      <h3>Technology</h3>
      <p>Explore the internet, networking, Wi-Fi, and modern computing.</p>
      <a href="#sec-basics" data-topic="technology" data-target="sec-basics" class="topic-jump section-jump">Learn More →</a>
    </article>
  </div>
  <p id="noResults">No matching topics found. Try another search.</p>
</section>

<!-- INTERACTIVE 3D HARDWARE SECTION -->
<section class="container page-section" id="sec-hardware" style="padding-top:35px">
  <div class="heading">
    <h2>Interactive 3D Computer Hardware</h2>
    <p>Rotate the 3D PC, explode the case, or click any component to see what it does and real product names.</p>
  </div>

  <div class="part-tabs" id="partTabs"></div>

  <div class="lab-wrap">
    <div class="canvas-box" id="pcCanvasWrap">
      <div class="hud-top" id="hudLabel">Full Desktop PC — Drag to Rotate</div>
      <div class="hud-bottom">
        <div style="display:flex;gap:8px;flex-wrap:wrap">
          <button type="button" class="hud-btn active" id="viewModeBtn">Mode: Mini-Parts 3D</button>
          <button type="button" class="hud-btn" id="explodeBtn">Explode Mini-Parts</button>
          <button type="button" class="hud-btn active" id="spinBtn">Auto-Spin: ON</button>
        </div>
        <button type="button" class="hud-btn" id="resetCamBtn">Reset Angle</button>
      </div>
    </div>

    <div class="info-panel">
      <div>
        <span style="font-size:12px;font-weight:700;color:#1769e0;text-transform:uppercase" id="partCat">Core Processing</span>
        <h3 style="font-size:24px;margin-top:4px" id="partTitle">CPU (Processor)</h3>
        <p style="font-size:14px;font-weight:600;color:#344054;margin-top:4px" id="partAnalogy"></p>
        <p style="font-size:14px;color:#667085;margin-top:12px" id="partDesc"></p>

        <div style="margin-top:16px">
          <strong style="font-size:12px;color:#344054;text-transform:uppercase">Popular Real-World Product Names</strong>
          <div class="pill-list" id="partProducts"></div>
        </div>
      </div>

      <div style="margin-top:4px">
        <strong style="font-size:12px;color:#344054;text-transform:uppercase">Small Mini-Parts Inside (Click any in 3D or below)</strong>
        <div class="pill-list" id="miniPartsList"></div>
        <div id="miniPartDetail" style="margin-top:10px;background:#eef5ff;border:1px solid #cfe0fc;border-radius:10px;padding:12px;font-size:13px;color:#17243a"></div>
      </div>

      <div style="background:#f7faff;border:1px solid #e7ebf0;border-radius:10px;padding:14px">
        <strong style="font-size:12px;color:#17243a">Where It Connects:</strong>
        <p style="font-size:13px;color:#667085;margin-top:4px" id="partConnect"></p>
      </div>
    </div>
  </div>
</section>

<!-- CODING & TECH COURSES SECTION -->
<section class="container page-section" id="sec-courses" style="padding-top:35px">
  <div class="heading">
    <h2>Beginner Coding &amp; Tech Courses</h2>
    <p>Learn HTML, CSS, JavaScript, Python, Git &amp; GitHub, and SQL—step by step with live practice.</p>
  </div>

  <div class="grid" id="courseGrid">
    <article class="card" style="border:2px solid #1769e0;background:#f7faff" data-search="how to make a website full expert course build deploy seo html css js">
      <div class="course-badge" style="background:#1769e0;color:#fff">Full Expert Course • 7 Modules</div>
      <div class="icon">🚀</div>
      <h3>How to Make a Website</h3>
      <p>Complete step-by-step expert masterclass: Planning, Semantic HTML5, CSS Grid/Flexbox, JS, SEO, Speed, &amp; Going Live.</p>
      <a href="#coursePlayer" class="course-open" data-course="webdev">Open Expert Course →</a>
    </article>

    <article class="card" style="border:2px solid #059669;background:#f0fdf4" data-search="class 10 computer science seba board assam hslc c programming mysql networks oop">
      <div class="course-badge" style="background:#059669;color:#fff">SEBA Board • Class 10</div>
      <div class="icon">📘</div>
      <h3>Class 10 Computer Science (SEBA)</h3>
      <p>Complete Assam SEBA Class X syllabus: Networks, HTML/CSS3, MySQL, C Loops/Arrays/Functions, OOP &amp; Practicals.</p>
      <a href="#coursePlayer" class="course-open" data-course="seba10">Open SEBA Class 10 →</a>
    </article>

    <article class="card" data-search="html web structure tags elements headings links">
      <div class="course-badge">Web Foundation</div>
      <div class="icon">🧱</div>
      <h3>HTML5 Basics</h3>
      <p>Build the structure of any webpage using headings, paragraphs, links, images, and forms.</p>
      <a href="#coursePlayer" class="course-open" data-course="html">Start HTML Course →</a>
    </article>

    <article class="card" data-search="css styling colors flexbox grid responsive design">
      <div class="course-badge">Web Design</div>
      <div class="icon">🎨</div>
      <h3>CSS3 Styling</h3>
      <p>Style websites with colors, fonts, spacing, Flexbox, Grid, and mobile-friendly layouts.</p>
      <a href="#coursePlayer" class="course-open" data-course="css">Start CSS Course →</a>
    </article>

    <article class="card" data-search="javascript js programming interactivity dom events">
      <div class="course-badge">Interactivity</div>
      <div class="icon">⚡</div>
      <h3>JavaScript Essentials</h3>
      <p>Make pages interactive with variables, functions, button clicks, and live DOM updates.</p>
      <a href="#coursePlayer" class="course-open" data-course="js">Start JS Course →</a>
    </article>

    <article class="card" data-search="java oop android programming classes objects beginner">
      <div class="course-badge">OOP &amp; Apps</div>
      <div class="icon">☕</div>
      <h3>Java Programming</h3>
      <p>Learn object-oriented programming, classes, loops, and how Java powers Android apps &amp; enterprise software.</p>
      <a href="#coursePlayer" class="course-open" data-course="java">Start Java Course →</a>
    </article>

    <article class="card" data-search="python coding beginner logic loops functions">
      <div class="course-badge">Programming</div>
      <div class="icon">🐍</div>
      <h3>Python for Beginners</h3>
      <p>Learn clean, readable programming from variables and loops to simple automation scripts.</p>
      <a href="#coursePlayer" class="course-open" data-course="python">Start Python Course →</a>
    </article>

    <article class="card" data-search="git github version control commits repositories">
      <div class="course-badge">Workflow</div>
      <div class="icon">🌿</div>
      <h3>Git &amp; GitHub</h3>
      <p>Save code versions, collaborate with classmates, and publish your projects online.</p>
      <a href="#coursePlayer" class="course-open" data-course="git">Start Git Course →</a>
    </article>

    <article class="card" data-search="sql database tables queries data storage">
      <div class="course-badge">Data</div>
      <div class="icon">🗄️</div>
      <h3>Databases &amp; SQL</h3>
      <p>Organize information in tables and fetch exact records using simple SQL queries.</p>
      <a href="#coursePlayer" class="course-open" data-course="sql">Start SQL Course →</a>
    </article>
  </div>

  <!-- Interactive Course Lesson & Live Playground -->
  <div class="guide-card" id="coursePlayer" style="margin-top:24px">
    <div style="display:flex;flex-wrap:wrap
