
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@400;600;800&display=swap');

        :root {
            --accent: #00f2ff;
            --g-blue: #8ab4f8;
            --dark-glass: rgba(15, 15, 15, 0.7);
        }

        body {
            background: radial-gradient(circle at top right, #1a1a1a, #050505);
            font-family: 'Plus Jakarta Sans', sans-serif;
            color: #fff;
            overflow-x: hidden;
        }

        /* 1. MOVING BACKGROUND PARTICLES */
        #bg-canvas { position: fixed; inset: 0; z-index: -1; opacity: 0.3; }

        /* 2. GLASS CARDS */
        .hub-card {
            background: var(--dark-glass);
            backdrop-filter: blur(20px);
            border: 1px solid rgba(255, 255, 255, 0.05);
            border-radius: 24px;
            transition: all 0.5s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            cursor: pointer;
        }

        .hub-card:hover {
            transform: translateY(-12px) scale(1.02);
            border-color: var(--accent);
            box-shadow: 0 25px 50px rgba(0, 242, 255, 0.15);
        }

        /* 3. PORTAL MODAL */
        #portal-overlay {
            position: fixed; inset: 0; background: rgba(0,0,0,0.9);
            backdrop-filter: blur(30px); display: none; z-index: 10000;
            padding: 20px; transition: 0.4s;
        }

        .portal-content {
            width: 100%; max-width: 1200px; height: 90vh;
            background: #000; border-radius: 30px;
            border: 1px solid rgba(255,255,255,0.1); overflow: hidden;
            display: flex; flex-direction: column; position: relative;
        }

        iframe { width: 100%; height: 100%; border: none; background: #fff; }

        /* 4. ANIMATED STATUS INDICATOR */
        .status-pulse {
            width: 8px; height: 8px; background: #34A853; border-radius: 50%;
            display: inline-block; margin-right: 8px;
            box-shadow: 0 0 10px #34A853; animation: pulse 2s infinite;
        }

        @keyframes pulse { 0% { opacity: 1; } 50% { opacity: 0.3; } 100% { opacity: 1; } }

        /* 5. FLOATING HIRE BUTTON */
        .hire-float {
            position: fixed; bottom: 30px; right: 30px;
            background: #25D366; color: white; padding: 12px 25px;
            border-radius: 50px; font-weight: 800; font-size: 14px;
            box-shadow: 0 10px 30px rgba(37, 211, 102, 0.4);
            z-index: 999; transition: 0.3s;
        }
        .hire-float:hover { transform: scale(1.1); }
    </style>
</head>
<body>

    <main class="max-w-6xl mx-auto px-6 py-20">
        <header class="mb-16 text-center" data-aos="fade-down">
            <h1 class="text-5xl font-extrabold tracking-tight mb-4">
                DEBEATZ<span class="text-cyan-400">GH</span>
            </h1>
            <div class="flex items-center justify-center gap-4 text-xs uppercase tracking-widest text-gray-500 font-bold">
                <span><span class="status-pulse"></span> Systems Active</span>
                <span class="h-1 w-1 bg-gray-700 rounded-full"></span>
                <span>Software Developer</span>
            </div>
        </header>

        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
            
            <div class="hub-card p-8" data-aos="fade-up" data-aos-delay="100" onclick="openPortal('https://debeatzgh1.github.io/appdategh/')">
                <i class="fab fa-android text-4xl text-cyan-400 mb-6"></i>
                <h3 class="text-xl font-bold mb-2">AppDateGH</h3>
                <p class="text-gray-400 text-sm">Entertainment & App Repository ecosystem.</p>
            </div>

            <div class="hub-card p-8" data-aos="fade-up" data-aos-delay="200" onclick="openPortal('https://beatzde4.blogspot.com')">
                <i class="fas fa-brain text-4xl text-purple-400 mb-6"></i>
                <h3 class="text-xl font-bold mb-2">Decode AI</h3>
                <p class="text-gray-400 text-sm">Automating business solutions & content.</p>
            </div>

            <div class="hub-card p-8" data-aos="fade-up" data-aos-delay="300" onclick="openPortal('https://debeatzgh1.github.io/1')">
                <i class="fab fa-google text-4xl text-blue-400 mb-6"></i>
                <h3 class="text-xl font-bold mb-2">G-Dev Node</h3>
                <p class="text-gray-400 text-sm">Verified Developer credentials & badges.</p>
            </div>

            <div class="hub-card p-8" data-aos="fade-up" data-aos-delay="400" onclick="openPortal('https://debeatzgh1.github.io/blogs')">
                <i class="fas fa-briefcase text-4xl text-yellow-400 mb-6"></i>
                <h3 class="text-xl font-bold mb-2">Dkonsult</h3>
                <p class="text-gray-400 text-sm">Premium client services & technical support.</p>
            </div>

            <div class="hub-card p-8" data-aos="fade-up" data-aos-delay="500" onclick="window.open('https://github.com/debeatzgh1', '_blank')">
                <i class="fab fa-github text-4xl text-white mb-6"></i>
                <h3 class="text-xl font-bold mb-2">Source Code</h3>
                <p class="text-gray-400 text-sm">Exploration of open-source projects.</p>
            </div>

            <div class="hub-card p-8 border-dashed border-cyan-900/50" data-aos="fade-up" data-aos-delay="600" onclick="scrollToCollab()">
                <i class="fas fa-paper-plane text-4xl text-red-500 mb-6"></i>
                <h3 class="text-xl font-bold mb-2">Collab Space</h3>
                <p class="text-gray-400 text-sm">Direct line for project inquiries.</p>
            </div>
        </div>
    </main>

    <div id="portal-overlay" onclick="closePortal(event)">
        <div class="portal-content mx-auto mt-4">
            <div class="p-4 bg-black flex justify-between items-center border-b border-white/10">
                <span id="portal-title" class="text-xs font-bold uppercase tracking-widest text-cyan-400">Loading Node...</span>
                <button onclick="togglePortal()" class="text-white hover:text-red-500"><i class="fas fa-times"></i></button>
            </div>
            <iframe id="portal-frame" src=""></iframe>
        </div>
    </div>

    <a href="https://wa.me/233270201181?text=Hi%20DeBeatz,%20I'm%20at%20your%20Hub%20and%20want%20to%20hire%20you." target="_blank" class="hire-float">
        <i class="fab fa-whatsapp"></i> contact 
    </a>

    <script src="https://unpkg.com/aos@2.3.1/dist/aos.js"></script>
    <script>
        AOS.init({ duration: 1000, once: true });

        const overlay = document.getElementById('portal-overlay');
        const frame = document.getElementById('portal-frame');
        const title = document.getElementById('portal-title');

        function openPortal(url) {
            overlay.style.display = 'block';
            frame.src = url;
            title.innerText = "Connecting to Secure Node: " + url.split('/')[2];
            document.body.style.overflow = 'hidden';
        }

        function togglePortal() {
            overlay.style.display = 'none';
            frame.src = "";
            document.body.style.overflow = 'auto';
        }

        function closePortal(e) { if (e.target === overlay) togglePortal(); }

        // 45 SECOND AUTO-POPUP (G-Dev Profile)
        setInterval(() => {
            if (overlay.style.display !== 'block') {
                openPortal('https://g.dev/debeatzgh');
            }
        }, 45000);

        function scrollToCollab() {
            alert("Email: debeatz4@gmail.com\nWhatsApp: 0549757544");
        }
    </script>
</body>
</html>







<nav id="slim-nav" class="slim-nav-container">
    <div class="nav-left">
        <button class="theme-toggle" onclick="toggleTheme()" title="Switch Theme">
            <i id="theme-icon" class="fas fa-moon"></i>
        </button>
        <div class="nav-divider"></div>
        <span class="nav-inscription" onclick="openForm()">
            Browse modern UI layout and pages <i class="fas fa-external-link-alt ml-1 opacity-40"></i>
        </span>
    </div>

    <div class="nav-right">
        <button onclick="scrollToTop()" class="nav-ctrl" title="Scroll to Top">
            <i class="fas fa-chevron-up"></i>
        </button>
        <button onclick="scrollToBottom()" class="nav-ctrl" title="Scroll to Bottom">
            <i class="fas fa-chevron-down"></i>
        </button>
    </div>
</nav>

<style>
    /* 1. THEME & TRANSITION LOGIC */
    :root {
        --nav-bg: rgba(10, 10, 12, 0.85);
        --nav-text: #f0f6fc;
        --nav-accent: #00f2ff;
        --nav-border: rgba(0, 242, 255, 0.15);
        --page-bg: #030712;
    }

    body[data-theme="light"] {
        --nav-bg: rgba(255, 255, 255, 0.9);
        --nav-text: #0f172a;
        --nav-accent: #2563eb;
        --nav-border: rgba(0, 0, 0, 0.08);
        --page-bg: #f8fafc;
    }

    body {
        background-color: var(--page-bg);
        transition: background-color 0.4s ease, color 0.4s ease;
    }

    /* 2. STICKY-HIDE ANIMATION */
    .slim-nav-container {
        position: fixed;
        top: 15px;
        left: 50%;
        transform: translateX(-50%);
        width: 92%;
        max-width: 750px;
        height: 44px;
        background: var(--nav-bg);
        backdrop-filter: blur(15px);
        -webkit-backdrop-filter: blur(15px);
        border: 1px solid var(--nav-border);
        border-radius: 14px;
        display: flex;
        align-items: center;
        justify-content: space-between;
        padding: 0 12px;
        z-index: 10000;
        box-shadow: 0 10px 30px -10px rgba(0, 0, 0, 0.5);
        transition: transform 0.4s cubic-bezier(0.16, 1, 0.3, 1), 
                    top 0.4s ease, 
                    background 0.3s ease;
    }

    /* The 'Hidden' State */
    .nav-up {
        transform: translateX(-50%) translateY(-100px);
    }

    /* 3. COMPONENT STYLING */
    .nav-left, .nav-right { display: flex; align-items: center; gap: 8px; }

    .nav-inscription {
        font-size: 11px;
        font-weight: 800;
        letter-spacing: 0.3px;
        color: var(--nav-text);
        cursor: pointer;
        transition: 0.2s;
        text-transform: uppercase;
    }

    .nav-inscription:hover { color: var(--nav-accent); }

    .nav-divider { width: 1px; height: 16px; background: var(--nav-border); margin: 0 4px; }

    .theme-toggle, .nav-ctrl {
        width: 32px; height: 32px;
        border-radius: 10px;
        display: flex; align-items: center; justify-content: center;
        cursor: pointer; color: var(--nav-text);
        transition: 0.2s; border: none; background: transparent;
    }

    .theme-toggle:hover, .nav-ctrl:hover {
        background: rgba(255, 255, 255, 0.08);
        color: var(--nav-accent);
    }

    body[data-theme="light"] .theme-toggle:hover,
    body[data-theme="light"] .nav-ctrl:hover {
        background: rgba(0, 0, 0, 0.05);
    }

    @media (max-width: 480px) {
        .nav-inscription { font-size: 9px; max-width: 180px; }
        .slim-nav-container { width: 96%; }
    }
</style>

<script>
    // --- 1. STICKY HIDE LOGIC ---
    let lastScrollY = window.scrollY;
    const nav = document.getElementById('slim-nav');

    window.addEventListener('scroll', () => {
        const currentScrollY = window.scrollY;

        if (currentScrollY > lastScrollY && currentScrollY > 100) {
            // Scrolling Down - Hide Nav
            nav.classList.add('nav-up');
        } else {
            // Scrolling Up - Show Nav
            nav.classList.remove('nav-up');
        }
        lastScrollY = currentScrollY;
    });

    // --- 2. EXTERNAL REDIRECT ---
    function openForm() {
        window.open('https://debeatzgh1.github.io/Pages-/', '_blank');
    }

    // --- 3. THEME ENGINE ---
    function toggleTheme() {
        const body = document.body;
        const icon = document.getElementById('theme-icon');
        const isLight = body.getAttribute('data-theme') === 'light';
        
        if (isLight) {
            body.removeAttribute('data-theme');
            icon.className = 'fas fa-moon';
            localStorage.setItem('debeatz_theme', 'dark');
        } else {
            body.setAttribute('data-theme', 'light');
            icon.className = 'fas fa-sun';
            localStorage.setItem('debeatz_theme', 'light');
        }
    }

    // --- 4. NAVIGATION ---
    function scrollToTop() { window.scrollTo({ top: 0, behavior: 'smooth' }); }
    function scrollToBottom() { window.scrollTo({ top: document.body.scrollHeight, behavior: 'smooth' }); }

    // Init Theme on Load
    if (localStorage.getItem('debeatz_theme') === 'light') toggleTheme();
</script>
