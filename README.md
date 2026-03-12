# 💎 Digital Ecosystem Hub

**A High-Performance Software Developer Portal & AI Strategy Command Center.**

This UI hosts the **DeBeatzGH Digital Hub**, a unified interface designed to bridge the gap between software development, AI automation, and digital content strategy. Built with a "SaaS-first" aesthetic, it utilizes modern web technologies to provide a seamless, app-like experience on GitHub Pages.

---

## 🚀 Premium Features & Engineering

### ⚡ Smart UI/UX Systems

* **Sticky-Hide Navigation:** An intelligent floating header that tracks scroll direction. It hides when scrolling down to provide a focused reading experience and reappears instantly on scroll-up for quick navigation.
* **Real-time Progress Tracker:** A dynamic reading bar integrated into the slim-nav that indicates the user's current position within the ecosystem.
* **Dynamic Theme Engine:** A custom-coded toggle between **Cyber Dark** and **Studio Light** modes with `localStorage` persistence to remember user preferences across sessions.

### 🛡️ Portal Architecture (Node Loading)

* **Lazy-Loaded Iframe System:** To maintain peak performance, external nodes (AppDateGH, Decode AI, G-Dev) are only initialized upon user request, significantly reducing initial page load weight.
* **Secure Portal Modal:** A branded overlay that allows users to interact with external tools and services without ever leaving the primary hub.

### 🎨 Aesthetic & Performance

* **Ambient Particle Engine:** A high-performance HTML5 Canvas background that generates a tech-focused atmosphere with zero impact on scroll performance.
* **Bento-Grid Layout:** A responsive, glassmorphic card system designed using Tailwind CSS for clean, professional service presentation.
* **AOS Integration:** Smooth "Animate On Scroll" entrance effects to guide the user's eye toward key service nodes.

---

## 🛠️ Technical Stack

| Category | Technology |
| --- | --- |
| **Framework** | [Tailwind CSS](https://tailwindcss.com/) |
| **Animation** | [AOS (Animate On Scroll)](https://michalsnik.github.io/aos/) |
| **Icons** | [FontAwesome 6.4](https://fontawesome.com/) |
| **Fonts** | Plus Jakarta Sans (Main), JetBrains Mono (System) |
| **Core Logic** | Vanilla JavaScript (ES6+) |
| **Background** | HTML5 Canvas API |

---

## 📂 Project Structure

```bash
├── index.html          # Main Entry Point (The Hub)
├── README.md           # Documentation & Tech Specs
└── assets/             # Project assets (Images, JSON data)

```

---

## 🔧 Installation & Deployment

1. **Fork the Repository:** Create your own copy of the hub.
2. **Customize Content:** Update the `openPortal('URL')` targets in the HTML to point to your specific sub-projects.
3. **Deploy:** * Go to **Settings** > **Pages**.
* Set **Branch** to `main`.
* Your hub will be live at `https://debeatzgh1.github.io/`.



---

## ⚖️ License & Credits

**Built by DeBeatzGH.** Engineered for creators, entrepreneurs, and modern hustlers.

* **Email:** debeatz4@gmail.com
* **WhatsApp:** [+233 27 020 1181](https://www.google.com/search?q=https://wa.me/233270201181)

---



<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>DEBEATZGH | Software Ecosystem</title>
    
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link href="https://unpkg.com/aos@2.3.1/dist/aos.css" rel="stylesheet">
    
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@400;600;800&family=JetBrains+Mono&display=swap');

        :root {
            --accent: #00f2ff;
            --page-bg: #030712;
            --card-bg: rgba(15, 15, 18, 0.6);
            --nav-bg: rgba(10, 10, 12, 0.8);
            --text: #f0f6fc;
            --border: rgba(255, 255, 255, 0.08);
        }

        body[data-theme="light"] {
            --page-bg: #f8fafc;
            --card-bg: rgba(255, 255, 255, 0.8);
            --nav-bg: rgba(255, 255, 255, 0.9);
            --text: #0f172a;
            --accent: #2563eb;
            --border: rgba(0, 0, 0, 0.08);
        }

        body {
            background-color: var(--page-bg);
            color: var(--text);
            font-family: 'Plus Jakarta Sans', sans-serif;
            transition: background 0.4s ease;
            overflow-x: hidden;
        }

        /* 1. PROGRESS BAR & SLIM NAV */
        .progress-container { position: absolute; bottom: 0; left: 0; width: 100%; height: 2px; background: transparent; overflow: hidden; border-radius: 0 0 12px 12px; }
        .progress-bar { height: 100%; width: 0%; background: var(--accent); transition: width 0.1s ease; box-shadow: 0 0 10px var(--accent); }

        .slim-nav-container {
            position: fixed; top: 15px; left: 50%; transform: translateX(-50%);
            width: 92%; max-width: 800px; height: 46px;
            background: var(--nav-bg); backdrop-filter: blur(20px); -webkit-backdrop-filter: blur(20px);
            border: 1px solid var(--border); border-radius: 14px;
            display: flex; align-items: center; justify-content: space-between;
            padding: 0 12px; z-index: 10000; transition: transform 0.4s cubic-bezier(0.16, 1, 0.3, 1);
        }
        .nav-up { transform: translateX(-50%) translateY(-100px); }

        /* 2. PREMIUM CARD STYLING */
        .hub-card {
            background: var(--card-bg); backdrop-filter: blur(16px);
            border: 1px solid var(--border); border-radius: 28px;
            transition: all 0.5s cubic-bezier(0.23, 1, 0.32, 1);
            position: relative; overflow: hidden;
        }
        .hub-card:hover {
            transform: translateY(-10px); border-color: var(--accent);
            box-shadow: 0 20px 40px rgba(0,0,0,0.3);
        }
        .hub-card::after {
            content: ''; position: absolute; top: 0; left: -100%; width: 100%; height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255,255,255,0.05), transparent);
            transition: 0.5s;
        }
        .hub-card:hover::after { left: 100%; }

        /* 3. PARTICLE CANVAS */
        #bg-canvas { position: fixed; inset: 0; z-index: -1; opacity: 0.4; pointer-events: none; }

        /* 4. MODAL PORTAL */
        #portal-overlay {
            position: fixed; inset: 0; background: rgba(0,0,0,0.95);
            backdrop-filter: blur(20px); display: none; z-index: 20000; align-items: center; justify-content: center;
        }
        .portal-content { width: 95%; height: 90vh; background: #000; border-radius: 24px; overflow: hidden; border: 1px solid var(--border); }
        
        /* 5. STATUS PULSE */
        .status-pulse { width: 10px; height: 10px; background: #22c55e; border-radius: 50%; display: inline-block; box-shadow: 0 0 10px #22c55e; animation: pulse 2s infinite; }
        @keyframes pulse { 0%, 100% { opacity: 1; transform: scale(1); } 50% { opacity: 0.5; transform: scale(1.2); } }
    </style>
</head>
<body data-theme="dark">

    <canvas id="bg-canvas"></canvas>

    <nav id="slim-nav" class="slim-nav-container">
        <div class="flex items-center gap-3">
            <button class="w-8 h-8 rounded-lg flex items-center justify-center text-current hover:bg-white/10 transition" onclick="toggleTheme()">
                <i id="theme-icon" class="fas fa-moon"></i>
            </button>
            <div class="h-4 w-px bg-white/10 mx-1"></div>
            <span class="text-[10px] font-black uppercase tracking-widest cursor-pointer hover:text-cyan-400" onclick="window.open('https://debeatzgh1.github.io/sales/', '_blank')">
                Browse UI Layouts <i class="fas fa-arrow-right ml-1"></i>
            </span>
        </div>
        <div class="flex items-center gap-2">
            <button onclick="scrollToTop()" class="w-8 h-8 text-[10px]"><i class="fas fa-chevron-up"></i></button>
            <button onclick="scrollToBottom()" class="w-8 h-8 text-[10px]"><i class="fas fa-chevron-down"></i></button>
        </div>
        <div class="progress-container"><div id="scroll-bar" class="progress-bar"></div></div>
    </nav>

    <main class="max-w-6xl mx-auto px-6 pt-32 pb-20">
        <header class="mb-20 text-center" data-aos="fade-down">
            <h1 class="text-6xl font-black tracking-tighter mb-4">DEBEATZ<span class="text-cyan-400">GH</span></h1>
            <div class="flex items-center justify-center gap-6 font-mono text-[10px] uppercase tracking-widest opacity-60">
                <span><span class="status-pulse mr-2"></span>Systems Online</span>
                <span class="h-1 w-1 bg-white/20 rounded-full"></span>
                <span>Software Developer</span>
                <span class="h-1 w-1 bg-white/20 rounded-full"></span>
                <span>AI Strategist</span>
            </div>
        </header>

        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
            <div class="hub-card p-8 group" onclick="openPortal('https://debeatzgh1.github.io/appdategh/')">
                <div class="w-12 h-12 bg-cyan-500/10 rounded-2xl flex items-center justify-center text-cyan-400 mb-6 group-hover:scale-110 transition">
                    <i class="fab fa-android text-2xl"></i>
                </div>
                <h3 class="text-xl font-bold mb-2 tracking-tight">AppDateGH</h3>
                <p class="text-sm opacity-50 leading-relaxed">Cross-platform entertainment repository & ecosystem.</p>
            </div>

            <div class="hub-card p-8 group" onclick="openPortal('https://beatzde4.blogspot.com')">
                <div class="w-12 h-12 bg-purple-500/10 rounded-2xl flex items-center justify-center text-purple-400 mb-6 group-hover:scale-110 transition">
                    <i class="fas fa-brain text-2xl"></i>
                </div>
                <h3 class="text-xl font-bold mb-2 tracking-tight">Decode AI</h3>
                <p class="text-sm opacity-50 leading-relaxed">Automating business logic & generative content workflows.</p>
            </div>

            <div class="hub-card p-8 group" onclick="openPortal('https://debeatzgh1.github.io/1')">
                <div class="w-12 h-12 bg-blue-500/10 rounded-2xl flex items-center justify-center text-blue-400 mb-6 group-hover:scale-110 transition">
                    <i class="fab fa-google text-2xl"></i>
                </div>
                <h3 class="text-xl font-bold mb-2 tracking-tight">G-Dev Node</h3>
                <p class="text-sm opacity-50 leading-relaxed">Google Developer credentials and verified cloud badges.</p>
            </div>

            <div class="hub-card p-8 group" onclick="openPortal('https://debeatzgh1.github.io/blogs')">
                <div class="w-12 h-12 bg-yellow-500/10 rounded-2xl flex items-center justify-center text-yellow-400 mb-6 group-hover:scale-110 transition">
                    <i class="fas fa-briefcase text-2xl"></i>
                </div>
                <h3 class="text-xl font-bold mb-2 tracking-tight">Dkonsult</h3>
                <p class="text-sm opacity-50 leading-relaxed">Strategic technical consulting & premium software services.</p>
            </div>

            <div class="hub-card p-8 group" onclick="window.open('https://github.com/debeatzgh1', '_blank')">
                <div class="w-12 h-12 bg-white/10 rounded-2xl flex items-center justify-center text-white mb-6 group-hover:scale-110 transition">
                    <i class="fab fa-github text-2xl"></i>
                </div>
                <h3 class="text-xl font-bold mb-2 tracking-tight">Source Code</h3>
                <p class="text-sm opacity-50 leading-relaxed">Open-source contributions and development repositories.</p>
            </div>

            <div class="hub-card p-8 border-dashed border-cyan-500/30 group" onclick="openContact()">
                <div class="w-12 h-12 bg-red-500/10 rounded-2xl flex items-center justify-center text-red-500 mb-6 group-hover:scale-110 transition">
                    <i class="fas fa-paper-plane text-2xl"></i>
                </div>
                <h3 class="text-xl font-bold mb-2 tracking-tight">Collab Space</h3>
                <p class="text-sm opacity-50 leading-relaxed">Ready to build? Send your project brief directly.</p>
            </div>
        </div>
    </main>

    <div id="portal-overlay">
        <div class="portal-content">
            <div class="px-6 py-4 bg-black/80 flex justify-between items-center border-b border-white/10">
                <span id="portal-title" class="text-[10px] font-mono uppercase text-cyan-400 tracking-widest">Node Initialized</span>
                <button onclick="closePortal()" class="w-8 h-8 rounded-full hover:bg-red-500/20 text-red-500 transition"><i class="fas fa-times"></i></button>
            </div>
            <iframe id="portal-frame" src="" class="w-full h-full"></iframe>
        </div>
    </div>

    <a href="https://wa.me/233270201181?text=Project%20Inquiry" target="_blank" class="fixed bottom-6 right-6 flex items-center gap-3 bg-[#25D366] text-white px-6 py-3 rounded-2xl font-black text-xs uppercase tracking-tighter shadow-2xl hover:scale-105 transition-all z-[500]">
        <i class="fab fa-whatsapp text-lg"></i> Hire Me
    </a>

    <script src="https://unpkg.com/aos@2.3.1/dist/aos.js"></script>
    <script>
        AOS.init({ duration: 800, once: true });

        // --- THEME ENGINE ---
        function toggleTheme() {
            const b = document.body;
            const icon = document.getElementById('theme-icon');
            if(b.getAttribute('data-theme') === 'dark') {
                b.setAttribute('data-theme', 'light');
                icon.className = 'fas fa-sun';
                localStorage.setItem('theme', 'light');
            } else {
                b.setAttribute('data-theme', 'dark');
                icon.className = 'fas fa-moon';
                localStorage.setItem('theme', 'dark');
            }
        }
        if(localStorage.getItem('theme') === 'light') toggleTheme();

        // --- STICKY NAV & PROGRESS BAR ---
        let lastScroll = 0;
        window.addEventListener('scroll', () => {
            const nav = document.getElementById('slim-nav');
            const bar = document.getElementById('scroll-bar');
            const currentScroll = window.scrollY;
            
            // Progress Logic
            const winScroll = document.body.scrollTop || document.documentElement.scrollTop;
            const height = document.documentElement.scrollHeight - document.documentElement.clientHeight;
            const scrolled = (winScroll / height) * 100;
            bar.style.width = scrolled + "%";

            // Hide/Show Logic
            if (currentScroll > lastScroll && currentScroll > 100) nav.classList.add('nav-up');
            else nav.classList.remove('nav-up');
            lastScroll = currentScroll;
        });

        // --- PORTAL LOGIC ---
        function openPortal(url) {
            const overlay = document.getElementById('portal-overlay');
            document.getElementById('portal-frame').src = url;
            document.getElementById('portal-title').innerText = "Accessing: " + url;
            overlay.style.display = 'flex';
            document.body.style.overflow = 'hidden';
        }

        function closePortal() {
            document.getElementById('portal-overlay').style.display = 'none';
            document.getElementById('portal-frame').src = "";
            document.body.style.overflow = 'auto';
        }

        function scrollToTop() { window.scrollTo({top: 0, behavior: 'smooth'}); }
        function scrollToBottom() { window.scrollTo({top: document.body.scrollHeight, behavior: 'smooth'}); }
        
        function openContact() {
            alert("Official Contact Details:\nEmail: debeatz4@gmail.com\nWhatsApp: +233 27 020 1181");
        }

        // --- BACKGROUND PARTICLES ---
        const canvas = document.getElementById('bg-canvas');
        const ctx = canvas.getContext('2d');
        let particles = [];
        function initCanvas() {
            canvas.width = window.innerWidth;
            canvas.height = window.innerHeight;
        }
        class Particle {
            constructor() {
                this.x = Math.random() * canvas.width;
                this.y = Math.random() * canvas.height;
                this.size = Math.random() * 2;
                this.speedX = Math.random() * 0.5 - 0.25;
                this.speedY = Math.random() * 0.5 - 0.25;
            }
            update() {
                this.x += this.speedX;
                this.y += this.speedY;
                if (this.x > canvas.width) this.x = 0;
                if (this.x < 0) this.x = canvas.width;
                if (this.y > canvas.height) this.y = 0;
                if (this.y < 0) this.y = canvas.height;
            }
            draw() {
                ctx.fillStyle = document.body.getAttribute('data-theme') === 'light' ? '#cbd5e1' : '#1e293b';
                ctx.beginPath();
                ctx.arc(this.x, this.y, this.size, 0, Math.PI * 2);
                ctx.fill();
            }
        }
        for (let i = 0; i < 80; i++) particles.push(new Particle());
        function animate() {
            ctx.clearRect(0, 0, canvas.width, canvas.height);
            particles.forEach(p => { p.update(); p.draw(); });
            requestAnimationFrame(animate);
        }
        window.addEventListener('resize', initCanvas);
        initCanvas();
        animate();
    </script>
</body>
</html>
