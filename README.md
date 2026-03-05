

<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>DeBeatzGH | Unified Hub</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">
    <link href="https://unpkg.com/aos@2.3.1/dist/aos.css" rel="stylesheet">
    
    <script src="https://cdn.jotfor.ms/s/static/latest/static/feedback2.js"></script>
    <script>
      var componentID = new JotformFeedback({
        type: 0, width: 700, height: 500, fontColor: "#FFFFFF", background: "#bd10e0",
        isCardForm: false, formId: "241335470278053", buttonText: "Sign in",
        buttonSide: "top", buttonAlign: "right", base: "https://form.jotform.com/",
      }).componentID;
    </script>

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

            <div class="hub-card p-8" data-aos="fade-up" data-aos-delay="300" onclick="openPortal('https://g.dev/debeatzgh')">
                <i class="fab fa-google text-4xl text-blue-400 mb-6"></i>
                <h3 class="text-xl font-bold mb-2">G-Dev Node</h3>
                <p class="text-gray-400 text-sm">Verified Developer credentials & badges.</p>
            </div>

            <div class="hub-card p-8" data-aos="fade-up" data-aos-delay="400" onclick="openPortal('https://debeatz4.wixsite.com/debeatz')">
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

    <a href="https://wa.me/233549757544?text=Hi%20DeBeatz,%20I'm%20at%20your%20Hub%20and%20want%20to%20hire%20you." target="_blank" class="hire-float">
        <i class="fab fa-whatsapp"></i> Hire 0549757544
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


<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Debeatzgh Ecosystem Hub</title>
    <style>
        :root {
            --bg: #0d1117;
            --card: #161b22;
            --border: #30363d;
            --accent: #58a6ff;
            --text: #c9d1d9;
            --glass: rgba(22, 27, 34, 0.8);
        }

        body {
            margin: 0;
            padding: 0;
            font-family: -apple-system, system-ui, sans-serif;
            background-color: var(--bg);
            color: var(--text);
            overflow-x: hidden;
        }

        /* --- FLOATING TOP BANNER --- */
        .top-banner {
            position: fixed;
            top: 10px;
            left: 50%;
            transform: translateX(-50%);
            width: 90%;
            max-width: 800px;
            background: var(--glass);
            border: 1px solid var(--border);
            backdrop-filter: blur(10px);
            border-radius: 50px;
            padding: 8px 20px;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 15px;
            z-index: 1000;
            box-shadow: 0 4px 20px rgba(0,0,0,0.5);
        }

        .ai-bot-icon {
            font-size: 20px;
            animation: pulse-bot 2s infinite;
        }

        .banner-text {
            font-size: 0.85rem;
            font-weight: 500;
            letter-spacing: 0.5px;
        }

        @keyframes pulse-bot {
            0% { transform: scale(1); filter: drop-shadow(0 0 0px var(--accent)); }
            50% { transform: scale(1.1); filter: drop-shadow(0 0 8px var(--accent)); }
            100% { transform: scale(1); filter: drop-shadow(0 0 0px var(--accent)); }
        }

        /* --- SECTION 1: AUTO-SLIDE CAROUSEL (IFRAME) --- */
        .section-header { text-align: center; margin: 80px 0 20px; color: var(--accent); font-size: 0.9rem; letter-spacing: 2px; text-transform: uppercase; }

        .carousel-container {
            width: 100%;
            overflow: hidden;
            background: var(--card);
            padding: 40px 0;
            border-top: 1px solid var(--border);
            border-bottom: 1px solid var(--border);
        }

        .carousel-track {
            display: flex;
            width: max-content;
            animation: scroll-carousel 40s linear infinite;
        }

        .carousel-item {
            width: 300px;
            margin: 0 15px;
            background: var(--bg);
            border: 1px solid var(--border);
            border-radius: 12px;
            padding: 20px;
            text-align: center;
        }

        .btn-launch {
            background: var(--accent);
            color: white;
            border: none;
            padding: 8px 16px;
            border-radius: 6px;
            cursor: pointer;
            font-weight: bold;
            margin-top: 10px;
        }

        /* --- SECTION 2: ICON LAUNCHERS --- */
        .icon-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(80px, 1fr));
            gap: 25px;
            padding: 40px 10%;
            max-width: 1200px;
            margin: 0 auto;
        }

        .icon-launcher {
            display: flex;
            flex-direction: column;
            align-items: center;
            cursor: pointer;
            transition: transform 0.3s;
        }

        .icon-launcher:hover { transform: translateY(-5px); }

        .icon-circle {
            width: 60px;
            height: 60px;
            background: var(--card);
            border: 1px solid var(--border);
            border-radius: 18px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 24px;
            margin-bottom: 8px;
            color: var(--accent);
        }

        .icon-label { font-size: 0.7rem; text-align: center; opacity: 0.8; }

        /* --- SECTION 3: SPLASH LINKS --- */
        .splash-track {
            height: 100px;
            display: flex;
            align-items: center;
            background: #000;
            overflow: hidden;
        }

        .splash-item {
            white-space: nowrap;
            padding: 0 40px;
            display: flex;
            align-items: center;
            gap: 10px;
            text-decoration: none;
            color: var(--text);
        }

        .badge { background: var(--accent); color: white; padding: 2px 8px; border-radius: 4px; font-size: 0.6rem; font-weight: bold; }
        .tag { color: var(--accent); font-family: monospace; }

        /* --- IFRAME MODAL --- */
        #iframe-overlay {
            position: fixed;
            inset: 0;
            background: rgba(0,0,0,0.9);
            display: none;
            flex-direction: column;
            z-index: 2000;
        }

        .iframe-header {
            height: 50px;
            background: var(--card);
            display: flex;
            align-items: center;
            padding: 0 20px;
            justify-content: space-between;
        }

        #main-iframe { flex-grow: 1; border: none; width: 100%; }

        @keyframes scroll-carousel {
            0% { transform: translateX(0); }
            100% { transform: translateX(-50%); }
        }
    </style>
</head>
<body>

    <div class="top-banner">
        <span class="ai-bot-icon">🤖</span>
        <span class="banner-text">Your lifestyle productivity tools and ideas All in one place!</span>
    </div>

    <div class="section-header">Interactive Quick-Launch</div>
    <div class="carousel-container">
        <div class="carousel-track" id="carousel-track">
            </div>
    </div>

    <div class="section-header">Resource Dashboard</div>
    <div class="icon-grid" id="icon-grid">
        </div>

    <div class="section-header">Ecosystem Feed</div>
    <div class="splash-track">
        <div class="carousel-track" style="animation-duration: 60s;" id="splash-track">
            </div>
    </div>

    <div id="iframe-overlay">
        <div class="iframe-header">
            <span id="modal-title" style="font-weight: bold;">Loading...</span>
            <button onclick="closeModal()" style="background:red; color:white; border:none; padding:5px 15px; border-radius:4px; cursor:pointer;">Close</button>
        </div>
        <iframe id="main-iframe"></iframe>
    </div>

    <script>
        const urls = [
            { name: "Master Hub", url: "https://debeatzgh1.github.io/1/", icon: "📂", tag: "CORE" },
            { name: "AI Chat", url: "https://debeatzgh1.github.io/ai-chat/", icon: "🤖", tag: "AI" },
            { name: "Global Posts", url: "https://debeatzgh1.github.io/posts/", icon: "📝", tag: "NEWS" },
            { name: "Portfolio", url: "https://debeatzgh1.github.io/Personal-Portfolio-site-/", icon: "👤", tag: "ME" },
            { name: "Collaborators", url: "https://debeatzgh1.github.io/Debeatzgh-Collaborators-Hub/", icon: "🤝", tag: "COMMUNITY" },
            { name: "AI Starter Kit", url: "https://debeatzgh1.github.io/Decode-AI-starter-kit-/", icon: "🚀", tag: "LEARN" },
            { name: "Side Hustle Guide", url: "https://debeatzgh1.github.io/The-Ultimate-Guide-to-Side-Hustle/", icon: "💰", tag: "GROWTH" },
            { name: "Frontend Components", url: "https://debeatzgh1.github.io/firebase-front-end-components/", icon: "🧩", tag: "DEV" },
            { name: "Sales Portal", url: "https://debeatzgh1.github.io/sales/", icon: "📈", tag: "PRO" },
            { name: "About Me", url: "https://debeatzgh1.github.io/me-/", icon: "🆔", tag: "BIO" },
            { name: "Debeatzgh", url: "https://debeatzgh1.github.io/debeatzgh/", icon: "🌐", tag: "ROOT" },
            { name: "Hustle Kit", url: "https://debeatzgh1.github.io/Side-hustle-starter-kit-/", icon: "⚒️", tag: "TOOLS" },
            { name: "Business Kit", url: "https://debeatzgh1.github.io/Online-business-kit/", icon: "🏢", tag: "biz" },
            { name: "Tailwind Styling", url: "https://debeatzgh1.github.io/Modern-homepage-styling-with-TailwindCSS-/", icon: "🎨", tag: "CSS" },
            { name: "Menu Widget", url: "https://debeatzgh1.github.io/menu-widget-/", icon: "🖱️", tag: "UI" },
            { name: "MB Online", url: "https://debeatzgh1.github.io/MB--online-/", icon: "📱", tag: "MOBILE" },
            { name: "Popup Gen", url: "https://debeatzgh1.github.io/popup-html-page-generator-blogger/", icon: "⚡", tag: "GEN" },
            { name: "Floating Dock", url: "https://debeatzgh1.github.io/-Floating-Dock-Smart-Iframe-Modal/#/", icon: "⚓", tag: "SYSTEM" }
        ];

        // 1. Populate Carousel
        const carouselTrack = document.getElementById('carousel-track');
        [...urls, ...urls].forEach(item => {
            const div = document.createElement('div');
            div.className = 'carousel-item';
            div.innerHTML = `
                <div style="font-size:40px">${item.icon}</div>
                <h3>${item.name}</h3>
                <button class="btn-launch" onclick="openModal('${item.url}', '${item.name}')">Launch Preview</button>
            `;
            carouselTrack.appendChild(div);
        });

        // 2. Populate Grid
        const grid = document.getElementById('icon-grid');
        urls.forEach(item => {
            const div = document.createElement('div');
            div.className = 'icon-launcher';
            div.onclick = () => openModal(item.url, item.name);
            div.innerHTML = `
                <div class="icon-circle">${item.icon}</div>
                <div class="icon-label">${item.name}</div>
            `;
            grid.appendChild(div);
        });

        // 3. Populate Splash Marquee
        const splashTrack = document.getElementById('splash-track');
        [...urls, ...urls].forEach(item => {
            const a = document.createElement('a');
            a.className = 'splash-item';
            a.href = item.url;
            a.target = "_blank";
            a.innerHTML = `
                <span class="tag">#${item.tag}</span>
                <strong>${item.name}</strong>
                <span class="badge">OPEN LINK</span>
            `;
            splashTrack.appendChild(a);
        });

        function openModal(url, name) {
            document.getElementById('modal-title').innerText = name;
            document.getElementById('main-iframe').src = url;
            document.getElementById('iframe-overlay').style.display = 'flex';
            document.body.style.overflow = 'hidden';
        }

        function closeModal() {
            document.getElementById('iframe-overlay').style.display = 'none';
            document.getElementById('main-iframe').src = '';
            document.body.style.overflow = 'auto';
        }
    </script>
</body>
</html>
