<style>
        :root {
            --gh-bg: #0d1117;
            --gh-border: #30363d;
            --hustle-accent: #238636;
            --text-gray: #8b949e;
        }

        /* 1. Slim Top Overlay Banner */
        .mini-hustle-card {
            position: fixed;
            top: 10px; /* Positioned at the top */
            left: 50%;
            transform: translateX(-50%);
            width: 90%;
            max-width: 450px; /* Narrower for a cleaner look */
            background: var(--gh-bg);
            border: 1px solid var(--gh-border);
            border-radius: 8px; /* Slightly sharper professional corners */
            padding: 10px 15px;
            cursor: pointer;
            box-shadow: 0 4px 20px rgba(0,0,0,0.6);
            z-index: 1000;
            overflow: hidden;
            display: flex;
            align-items: center;
            gap: 12px;
            animation: borderPulse 4s infinite;
        }

        @keyframes borderPulse {
            0% { border-color: var(--gh-border); }
            50% { border-color: var(--hustle-accent); box-shadow: 0 0 10px rgba(35, 134, 54, 0.2); }
            100% { border-color: var(--gh-border); }
        }

        /* 2. Compact Auto-Slide Content */
        .slide-container {
            flex-grow: 1;
        }

        .slide-text {
            display: none;
            font-size: 0.8rem; /* Smaller font for top overlay */
            line-height: 1.2;
            color: white;
            animation: fadeSlide 0.5s ease;
        }

        .slide-text.active { display: block; }

        @keyframes fadeSlide {
            from { opacity: 0; transform: translateY(-5px); }
            to { opacity: 1; transform: translateY(0); }
        }

        .hustle-tag {
            background: var(--hustle-accent);
            color: white;
            font-size: 0.65rem;
            font-weight: bold;
            padding: 2px 6px;
            border-radius: 4px;
            text-transform: uppercase;
            white-space: nowrap;
        }

        /* 3. Full-Screen Iframe Overlay */
        #iframe-overlay {
            position: fixed;
            top: 0; left: 0; 
            width: 100%; height: 100%;
            background: rgba(0,0,0,0.9);
            display: none;
            justify-content: center;
            align-items: center;
            z-index: 9999;
            backdrop-filter: blur(8px);
        }

        .iframe-container {
            width: 95%; /* Wider for GitHub Page tools */
            max-width: 1200px;
            height: 90vh;
            background: #ffffff;
            border-radius: 12px;
            position: relative;
            overflow: hidden;
            box-shadow: 0 0 50px rgba(0,0,0,0.5);
        }

        .close-iframe {
            position: absolute;
            top: 10px;
            right: 15px;
            background: #f85149;
            color: white;
            border: none;
            padding: 8px 15px;
            border-radius: 5px;
            cursor: pointer;
            z-index: 10001;
            font-weight: bold;
            font-size: 0.8rem;
        }

        iframe {
            width: 100%;
            height: 100%;
            border: none;
        }
    </style>



    <div class="mini-hustle-card" onclick="openHustleKit()">
        <span class="hustle-tag">NEW</span>
        
        <div class="slide-container">
            <div class="slide-text active">
                <strong>Side Hustle Tools:</strong> Launch your digital business today.
            </div>
            
            <div class="slide-text">
                <strong>Entrepreneur Ideas:</strong> Thrive in the digital economy.
            </div>

            <div class="slide-text">
                <strong>One-Stop Place:</strong> Everything you need online.
            </div>
        </div>

        <span style="color: var(--text-gray); font-size: 1rem;">›</span>
    </div>

    <div id="iframe-overlay" onclick="closeHustleKit(event)">
        <div class="iframe-container" onclick="event.stopPropagation()">
            <button class="close-iframe" onclick="closeHustleKit(event)">CLOSE [X]</button>
            <iframe src="https://msha.ke/debeatzgh" title="Side Hustle Starter Kit"></iframe>
        </div>
    </div>

    <script>
        // Auto-Slide Logic
        let currentSlide = 0;
        const slides = document.querySelectorAll('.slide-text');
        
        function rotateSlides() {
            slides[currentSlide].classList.remove('active');
            currentSlide = (currentSlide + 1) % slides.length;
            slides[currentSlide].classList.add('active');
        }

        setInterval(rotateSlides, 3500); 

        // Iframe Open/Close Logic
        function openHustleKit() {
            document.getElementById('iframe-overlay').style.display = 'flex';
            document.body.style.overflow = 'hidden'; // Prevent background scroll
        }

        function closeHustleKit(event) {
            document.getElementById('iframe-overlay').style.display = 'none';
            document.body.style.overflow = 'auto'; // Restore scroll
        }
    </script>



<!-- =========================================================
 FAQ + RESOURCE HUB
 GitHub Pages + Blogger Compatible
 Modern reusable widget with:
 ✔ Premium glassmorphism UI
 ✔ Floating quick actions
 ✔ Search engine
 ✔ Lazy-load FAQ system
 ✔ Inline iframe preview modal
 ✔ Toast popups
 ✔ Animated counters
 ✔ Auto reveal animations
 ✔ Reusable cards
 ✔ Mobile optimized
 ✔ GitHub Pages ready
========================================================= -->

<div id="dbz-premium-hub">

<style>
:root{
  --dbz-bg:#050816;
  --dbz-panel:rgba(15,23,42,.72);
  --dbz-border:rgba(255,255,255,.08);
  --dbz-text:#f8fafc;
  --dbz-muted:#94a3b8;
  --dbz-accent:#d946ef;
  --dbz-blue:#3b82f6;
  --dbz-green:#06b6d4;
  --dbz-radius:22px;
  --dbz-shadow:0 20px 60px rgba(0,0,0,.45);
}

#dbz-premium-hub *{
  box-sizing:border-box;
}

#dbz-premium-hub{
  background:
    radial-gradient(circle at top right, rgba(217,70,239,.12), transparent 30%),
    radial-gradient(circle at bottom left, rgba(59,130,246,.15), transparent 30%),
    var(--dbz-bg);
  color:var(--dbz-text);
  padding:28px 16px 90px;
  border-radius:30px;
  font-family:Inter,Segoe UI,Roboto,sans-serif;
  max-width:1200px;
  margin:auto;
  overflow:hidden;
  position:relative;
}

/* HERO */
.dbz-hero{
  position:relative;
  overflow:hidden;
  border:1px solid var(--dbz-border);
  background:linear-gradient(135deg, rgba(255,255,255,.05), rgba(255,255,255,.02));
  backdrop-filter:blur(14px);
  padding:30px;
  border-radius:28px;
  margin-bottom:24px;
  box-shadow:var(--dbz-shadow);
}

.dbz-badge{
  display:inline-flex;
  align-items:center;
  gap:8px;
  background:rgba(255,255,255,.06);
  border:1px solid rgba(255,255,255,.08);
  color:#fff;
  padding:8px 14px;
  border-radius:999px;
  font-size:.8rem;
  font-weight:700;
  margin-bottom:16px;
}

.dbz-live-dot{
  width:8px;
  height:8px;
  border-radius:50%;
  background:#22c55e;
  animation:pulse 1.6s infinite;
}

@keyframes pulse{
  0%,100%{transform:scale(1);opacity:1;}
  50%{transform:scale(1.4);opacity:.4;}
}

.dbz-title{
  font-size:clamp(2rem,5vw,4rem);
  font-weight:900;
  line-height:1;
  margin-bottom:14px;
  letter-spacing:-2px;
}

.dbz-gradient{
  background:linear-gradient(90deg,var(--dbz-accent),var(--dbz-blue));
  -webkit-background-clip:text;
  -webkit-text-fill-color:transparent;
}

.dbz-desc{
  max-width:780px;
  color:var(--dbz-muted);
  line-height:1.7;
  font-size:1rem;
}

.dbz-hero-actions{
  display:flex;
  flex-wrap:wrap;
  gap:12px;
  margin-top:24px;
}

.dbz-btn{
  border:none;
  cursor:pointer;
  padding:13px 20px;
  border-radius:16px;
  font-weight:800;
  transition:.3s ease;
  text-decoration:none;
  display:inline-flex;
  align-items:center;
  gap:10px;
  font-size:.92rem;
}

.dbz-btn-primary{
  background:linear-gradient(135deg,var(--dbz-accent),var(--dbz-blue));
  color:#fff;
  box-shadow:0 10px 30px rgba(217,70,239,.25);
}

.dbz-btn-secondary{
  background:rgba(255,255,255,.05);
  color:#fff;
  border:1px solid rgba(255,255,255,.08);
}

.dbz-btn:hover{
  transform:translateY(-3px) scale(1.01);
}

/* STATS */
.dbz-stats{
  display:grid;
  grid-template-columns:repeat(auto-fit,minmax(180px,1fr));
  gap:16px;
  margin:24px 0;
}

.dbz-stat{
  background:var(--dbz-panel);
  border:1px solid var(--dbz-border);
  border-radius:20px;
  padding:20px;
  backdrop-filter:blur(10px);
}

.dbz-stat h3{
  font-size:2rem;
  margin:0;
}

.dbz-stat p{
  color:var(--dbz-muted);
  margin-top:8px;
}

/* SEARCH */
.dbz-search-wrap{
  margin:26px 0;
  position:relative;
}

.dbz-search{
  width:100%;
  padding:16px 20px;
  border-radius:18px;
  border:1px solid var(--dbz-border);
  background:rgba(255,255,255,.05);
  color:#fff;
  outline:none;
  font-size:1rem;
}

.dbz-search::placeholder{
  color:#94a3b8;
}

/* CATEGORY */
.dbz-cats{
  display:flex;
  gap:12px;
  overflow-x:auto;
  padding-bottom:10px;
  margin-bottom:24px;
  scrollbar-width:none;
}

.dbz-cats::-webkit-scrollbar{
  display:none;
}

.dbz-cat{
  flex:0 0 auto;
  border:none;
  padding:12px 18px;
  border-radius:999px;
  background:rgba(255,255,255,.05);
  color:var(--dbz-muted);
  font-weight:700;
  cursor:pointer;
  transition:.25s;
}

.dbz-cat.active{
  background:linear-gradient(135deg,var(--dbz-accent),var(--dbz-blue));
  color:#fff;
  box-shadow:0 8px 30px rgba(217,70,239,.3);
}

/* GRID */
.dbz-grid{
  display:grid;
  grid-template-columns:repeat(auto-fit,minmax(280px,1fr));
  gap:18px;
}

.dbz-card{
  background:var(--dbz-panel);
  border:1px solid var(--dbz-border);
  border-radius:24px;
  overflow:hidden;
  backdrop-filter:blur(10px);
  transition:.35s;
  position:relative;
}

.dbz-card:hover{
  transform:translateY(-6px);
  border-color:rgba(217,70,239,.35);
}

.dbz-thumb{
  height:170px;
  width:100%;
  object-fit:cover;
  display:block;
}

.dbz-card-body{
  padding:18px;
}

.dbz-card-title{
  font-size:1.1rem;
  font-weight:800;
  margin-bottom:10px;
}

.dbz-card-text{
  color:var(--dbz-muted);
  line-height:1.6;
  font-size:.92rem;
  margin-bottom:16px;
}

.dbz-card-actions{
  display:flex;
  gap:10px;
}

.dbz-mini-btn{
  flex:1;
  border:none;
  cursor:pointer;
  padding:11px;
  border-radius:14px;
  font-weight:700;
  transition:.25s;
}

.dbz-preview{
  background:linear-gradient(135deg,var(--dbz-blue),var(--dbz-green));
  color:#fff;
}

.dbz-open{
  background:rgba(255,255,255,.05);
  color:#fff;
}

.dbz-mini-btn:hover{
  transform:translateY(-2px);
}

/* FAQ */
.dbz-faq-wrap{
  margin-top:40px;
}

.dbz-faq-item{
  margin-bottom:14px;
  border-radius:18px;
  overflow:hidden;
  background:var(--dbz-panel);
  border:1px solid var(--dbz-border);
}

.dbz-faq-btn{
  width:100%;
  border:none;
  background:none;
  color:#fff;
  text-align:left;
  padding:18px;
  cursor:pointer;
  display:flex;
  justify-content:space-between;
  align-items:center;
  font-weight:800;
}

.dbz-faq-content{
  max-height:0;
  overflow:hidden;
  transition:max-height .35s ease;
}

.dbz-faq-inner{
  padding:0 18px 18px;
  color:var(--dbz-muted);
  line-height:1.7;
}

/* MODAL */
.dbz-modal{
  position:fixed;
  inset:0;
  background:rgba(0,0,0,.8);
  display:none;
  align-items:center;
  justify-content:center;
  z-index:999999;
  backdrop-filter:blur(6px);
}

.dbz-modal.active{
  display:flex;
}

.dbz-modal-box{
  width:min(1200px,95vw);
  height:min(85vh,800px);
  background:#000;
  border-radius:24px;
  overflow:hidden;
  border:1px solid rgba(255,255,255,.08);
  animation:fadeUp .35s ease;
}

@keyframes fadeUp{
  from{
    transform:translateY(30px);
    opacity:0;
  }
  to{
    transform:translateY(0);
    opacity:1;
  }
}

.dbz-modal-head{
  padding:14px 16px;
  background:#050816;
  display:flex;
  align-items:center;
  justify-content:space-between;
}

.dbz-modal-actions{
  display:flex;
  gap:10px;
}

.dbz-frame{
  width:100%;
  height:calc(100% - 60px);
  border:none;
}

/* FLOAT BUTTON */
.dbz-float{
  position:fixed;
  bottom:24px;
  right:24px;
  width:58px;
  height:58px;
  border-radius:50%;
  background:linear-gradient(135deg,var(--dbz-accent),var(--dbz-blue));
  display:flex;
  align-items:center;
  justify-content:center;
  color:#fff;
  cursor:pointer;
  z-index:99999;
  box-shadow:0 15px 35px rgba(217,70,239,.35);
  animation:floatPulse 2s infinite;
}

@keyframes floatPulse{
  0%,100%{
    transform:scale(1);
  }
  50%{
    transform:scale(1.08);
  }
}

/* TOAST */
.dbz-toast{
  position:fixed;
  top:24px;
  right:24px;
  background:#111827;
  color:#fff;
  padding:14px 18px;
  border-radius:14px;
  border:1px solid rgba(255,255,255,.08);
  z-index:999999;
  opacity:0;
  transform:translateY(-10px);
  transition:.35s;
}

.dbz-toast.show{
  opacity:1;
  transform:translateY(0);
}

@media(max-width:768px){

  .dbz-title{
    font-size:2.3rem;
  }

  .dbz-card-actions{
    flex-direction:column;
  }

  .dbz-hero{
    padding:22px;
  }
}
</style>

<!-- HERO -->
<section class="dbz-hero">
  <div class="dbz-badge">
    <span class="dbz-live-dot"></span>
    Premium GitHub Pages Interface
  </div>

  <h1 class="dbz-title">
    UI <span class="dbz-gradient">Resource Hub</span>
  </h1>

  <p class="dbz-desc">
    Professional reusable widget system for GitHub Pages and Blogger. 
    Launch previews, explore templates, deploy tools, load FAQs lazily, 
    and deliver premium creator experiences with modern UI components.
  </p>

  <div class="dbz-hero-actions">
    <a class="dbz-btn dbz-btn-primary"
       href="https://debeatzgh1.github.io/Home-/"
       target="_blank">
       🚀 Open Main Hub
    </a>

    <button class="dbz-btn dbz-btn-secondary"
      onclick="dbzToast('System initialized successfully')">
      ✨ Launch Experience
    </button>
  </div>
</section>

<!-- STATS -->
<div class="dbz-stats">
  <div class="dbz-stat">
    <h3>50+</h3>
    <p>Reusable UI layouts</p>
  </div>

  <div class="dbz-stat">
    <h3>100%</h3>
    <p>GitHub Pages compatible</p>
  </div>

  <div class="dbz-stat">
    <h3>24/7</h3>
    <p>Interactive experience</p>
  </div>
</div>

<!-- SEARCH -->
<div class="dbz-search-wrap">
  <input type="text"
         class="dbz-search"
         id="dbzSearch"
         placeholder="Search templates, FAQs, widgets, scripts...">
</div>

<!-- CATEGORY -->
<div class="dbz-cats">
  <button class="dbz-cat active">All</button>
  <button class="dbz-cat">Templates</button>
  <button class="dbz-cat">AI Tools</button>
  <button class="dbz-cat">Widgets</button>
  <button class="dbz-cat">Resources</button>
</div>

<!-- CARDS -->
<div class="dbz-grid" id="dbzGrid">

  <div class="dbz-card">
    <img class="dbz-thumb"
    loading="lazy"
    src="https://debeatzgh.wordpress.com/wp-content/uploads/2025/08/createamodernandcleanthumbnailforawebdevelopmentproducttitledmodernhomepagestylingtemplatewithtailwindcss3420170625469385526.jpg">

    <div class="dbz-card-body">
      <div class="dbz-card-title">Premium Homepage UI</div>

      <div class="dbz-card-text">
        Modern landing page templates optimized for GitHub Pages, startups, creators, and portfolios.
      </div>

      <div class="dbz-card-actions">
        <button class="dbz-mini-btn dbz-preview"
        onclick="openDBZModal('https://debeatzgh1.github.io/Home-/')">
        Preview
        </button>

        <button class="dbz-mini-btn dbz-open"
        onclick="window.open('https://debeatzgh1.github.io/Home-/','_blank')">
        Open
        </button>
      </div>
    </div>
  </div>

  <div class="dbz-card">
    <img class="dbz-thumb"
    loading="lazy"
    src="https://debeatzgh.wordpress.com/wp-content/uploads/2025/08/designadigitalproductse-commerceonlinedeals3545265155247625100.jpg">

    <div class="dbz-card-body">
      <div class="dbz-card-title">Digital Product Hub</div>

      <div class="dbz-card-text">
        Explore online business systems, monetization kits, side hustles, and digital product tools.
      </div>

      <div class="dbz-card-actions">
        <button class="dbz-mini-btn dbz-preview"
        onclick="openDBZModal('https://debeatzgh1.github.io/-My-Brand-Online-Digital-Products-Affiliate-Shop/')">
        Preview
        </button>

        <button class="dbz-mini-btn dbz-open"
        onclick="window.open('https://debeatzgh1.github.io/-My-Brand-Online-Digital-Products-Affiliate-Shop/','_blank')">
        Open
        </button>
      </div>
    </div>
  </div>

  <div class="dbz-card">
    <img class="dbz-thumb"
    loading="lazy"
    src="https://debeatzgh.wordpress.com/wp-content/uploads/2025/08/createavibranteye-catchingyoutubeblogthumbnailfeaturingafloatingquizpop-upicononadigitalblogpage5084708667809205788.jpg">

    <div class="dbz-card-body">
      <div class="dbz-card-title">AI Assistant Portal</div>

      <div class="dbz-card-text">
        Interactive AI dashboards, chatbot systems, creator widgets, and automation interfaces.
      </div>

      <div class="dbz-card-actions">
        <button class="dbz-mini-btn dbz-preview"
        onclick="openDBZModal('https://debeatzgh1.github.io/1/')">
        Preview
        </button>

        <button class="dbz-mini-btn dbz-open"
        onclick="window.open('https://debeatzgh1.github.io/1/','_blank')">
        Open
        </button>
      </div>
    </div>
  </div>

</div>

<!-- FAQ -->
<div class="dbz-faq-wrap">

  <div class="dbz-faq-item">
    <button class="dbz-faq-btn">
      What is this platform about?
      <span>⌄</span>
    </button>

    <div class="dbz-faq-content">
      <div class="dbz-faq-inner">
        This platform delivers reusable GitHub Pages and Blogger-ready interfaces for creators, developers, startups, and AI enthusiasts.
      </div>
    </div>
  </div>

  <div class="dbz-faq-item">
    <button class="dbz-faq-btn">
      Can I customize the templates?
      <span>⌄</span>
    </button>

    <div class="dbz-faq-content">
      <div class="dbz-faq-inner">
        Yes. All layouts can be edited, rebranded, expanded, and embedded into Blogger, WordPress, or GitHub Pages projects.
      </div>
    </div>
  </div>

  <div class="dbz-faq-item">
    <button class="dbz-faq-btn">
      Does this support lazy loading?
      <span>⌄</span>
    </button>

    <div class="dbz-faq-content">
      <div class="dbz-faq-inner">
        Absolutely. Images and iframe previews are loaded only when triggered for maximum performance optimization.
      </div>
    </div>
  </div>

</div>

<!-- FLOAT BUTTON -->
<div class="dbz-float"
onclick="window.scrollTo({top:0,behavior:'smooth'})">
⬆
</div>

<!-- MODAL -->
<div class="dbz-modal" id="dbzModal">
  <div class="dbz-modal-box">

    <div class="dbz-modal-head">
      <strong>Live Preview Environment</strong>

      <div class="dbz-modal-actions">
        <button class="dbz-btn dbz-btn-secondary"
        onclick="window.open(document.getElementById('dbzFrame').src,'_blank')">
        Open
        </button>

        <button class="dbz-btn dbz-btn-primary"
        onclick="closeDBZModal()">
        Close
        </button>
      </div>
    </div>

    <iframe class="dbz-frame"
    id="dbzFrame"
    loading="lazy"></iframe>

  </div>
</div>

<!-- TOAST -->
<div class="dbz-toast" id="dbzToast"></div>

<script>

/* MODAL */
function openDBZModal(url){
  document.getElementById('dbzModal').classList.add('active');
  document.getElementById('dbzFrame').src = url;
}

function closeDBZModal(){
  document.getElementById('dbzModal').classList.remove('active');
  document.getElementById('dbzFrame').src = '';
}

/* TOAST */
function dbzToast(message){
  const toast = document.getElementById('dbzToast');
  toast.innerText = message;
  toast.classList.add('show');

  setTimeout(()=>{
    toast.classList.remove('show');
  },3000);
}

/* FAQ */
document.querySelectorAll('.dbz-faq-btn').forEach(btn=>{
  btn.addEventListener('click',()=>{

    const content = btn.nextElementSibling;

    if(content.style.maxHeight){
      content.style.maxHeight = null;
    }else{

      document.querySelectorAll('.dbz-faq-content').forEach(c=>{
        c.style.maxHeight = null;
      });

      content.style.maxHeight = content.scrollHeight + 'px';
    }
  });
});

/* SEARCH */
document.getElementById('dbzSearch').addEventListener('keyup', function(){

  const value = this.value.toLowerCase();

  document.querySelectorAll('.dbz-card').forEach(card=>{

    const text = card.innerText.toLowerCase();

    card.style.display = text.includes(value)
      ? 'block'
      : 'none';
  });

});

/* AUTO POPUP */
setTimeout(()=>{
  dbzToast('Premium interface loaded successfully');
},2000);

</script>
