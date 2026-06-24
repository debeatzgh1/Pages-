<!-- DeBeatzGH Multi-Form Launcher Console -->
<div id="debeatzgh-launcher-system">
    <!-- Floating Trigger Node -->
    <button id="portal-floating-trigger" onclick="openFormPortal()" title="Launch Form Portal">
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round">
            <path d="M14 2H6a2 2 0 0 0-2 2v16a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V8z"></path>
            <polyline points="14 2 14 8 20 8"></polyline>
            <line x1="16" y1="13" x2="8" y2="13"></line>
            <line x1="16" y1="17" x2="8" y2="17"></line>
            <polyline points="10 9 9 9 8 9"></polyline>
        </svg>
    </button>

    <!-- Modal Backdrop Overlay -->
    <div id="portal-modal-overlay" onclick="triggerBlockShake()">
        <!-- Interactive Panel Base -->
        <div id="portal-console-card" onclick="event.stopPropagation()">
            <div class="console-title-row">
                <div class="console-brand-meta">
                    <span class="brand-glow-dot"></span>
                    <h6>DeBeatzGH Centralized Intake</h6>
                </div>
                <button class="console-close-btn" onclick="closeFormPortal()" title="Close Portal">✕</button>
            </div>
            
            <p class="console-instructions">Select your required data profile channel below. Fill out and submit your production fields completely inside the frame before dismissing the panel view.</p>
            
            <!-- Tab Selection Rail -->
            <div class="console-tab-rail">
                <button class="console-tab active" onclick="switchFormChannel(this, 0)">Channel 1</button>
                <button class="console-tab" onclick="switchFormChannel(this, 1)">Channel 2</button>
                <button class="console-tab" onclick="switchFormChannel(this, 2)">Channel 3</button>
            </div>

            <!-- Frame Container Core -->
            <div class="console-frame-container">
                <div class="frame-loading-overlay" id="frameLoader">Compiling Form Data Stream...</div>
                <iframe id="portalIntakeFrame" src="" onload="hideFrameLoader()"></iframe>
            </div>
        </div>
    </div>
</div>

<style>
    /* Floating Launcher Element with Heartbeat Engine */
    #portal-floating-trigger {
        position: fixed;
        bottom: 24px;
        right: 24px;
        width: 60px;
        height: 60px;
        border-radius: 50%;
        background: linear-gradient(135deg, #bc6cff, #58a6ff);
        border: 1px solid rgba(250, 251, 252, 0.25);
        color: #ffffff;
        cursor: pointer;
        display: flex;
        justify-content: center;
        align-items: center;
        box-shadow: 0 8px 24px rgba(188, 108, 255, 0.4);
        z-index: 999998;
        transition: transform 0.2s, box-shadow 0.2s;
        animation: triggerHeartbeat 2.4s infinite ease-in-out;
    }

    #portal-floating-trigger:hover {
        animation-play-state: paused;
        transform: scale(1.08);
        box-shadow: 0 10px 28px rgba(188, 108, 255, 0.6);
    }

    #portal-floating-trigger svg {
        width: 24px;
        height: 24px;
    }

    @keyframes triggerHeartbeat {
        0% { transform: scale(1); box-shadow: 0 8px 24px rgba(188, 108, 255, 0.4); }
        14% { transform: scale(1.06); box-shadow: 0 10px 28px rgba(188, 108, 255, 0.5); }
        28% { transform: scale(1); box-shadow: 0 8px 24px rgba(188, 108, 255, 0.4); }
        42% { transform: scale(1.06); box-shadow: 0 10px 28px rgba(188, 108, 255, 0.5); }
        70% { transform: scale(1); box-shadow: 0 8px 24px rgba(188, 108, 255, 0.4); }
    }

    /* Modal Backdrop Configuration */
    #portal-modal-overlay {
        position: fixed;
        top: 0;
        left: 0;
        width: 100vw;
        height: 100vh;
        background: rgba(4, 7, 12, 0.85);
        backdrop-filter: blur(10px);
        -webkit-backdrop-filter: blur(10px);
        z-index: 999999;
        display: none;
        justify-content: center;
        align-items: center;
        padding: 20px;
    }

    /* Glassmorphic Panel Core Card with Scale Animation */
    #portal-console-card {
        background: rgba(22, 27, 34, 0.65);
        backdrop-filter: blur(20px);
        -webkit-backdrop-filter: blur(20px);
        border: 1px solid rgba(88, 166, 255, 0.2);
        border-radius: 16px;
        width: 100%;
        max-width: 760px;
        height: 85vh;
        max-height: 800px;
        display: flex;
        flex-direction: column;
        padding: 24px;
        box-shadow: 0 30px 70px rgba(0, 0, 0, 0.8);
        transform: scale(0.92);
        opacity: 0;
        transition: transform 0.3s cubic-bezier(0.34, 1.56, 0.64, 1), opacity 0.3s ease;
    }

    #portal-modal-overlay.portal-active #portal-console-card {
        transform: scale(1);
        opacity: 1;
    }

    /* Attention Mechanics: Shake Keyframes */
    @keyframes panelShake {
        0%, 100% { transform: translateX(0); }
        20%, 60% { transform: translateX(-6px); }
        40%, 80% { transform: translateX(6px); }
    }

    #portal-console-card.shake-attention {
        animation: panelShake 0.4s ease-in-out;
    }

    /* Header Design Styles */
    .console-title-row {
        display: flex;
        justify-content: space-between;
        align-items: center;
        margin-bottom: 8px;
    }

    .console-brand-meta {
        display: flex;
        align-items: center;
        gap: 10px;
    }

    .brand-glow-dot {
        width: 10px;
        height: 10px;
        background: #3fb950;
        border-radius: 50%;
        box-shadow: 0 0 10px #3fb950;
    }

    .console-brand-meta h6 {
        font-size: 16px;
        color: #ffffff;
        font-weight: 600;
        margin: 0;
    }

    .console-close-btn {
        background: transparent;
        border: none;
        color: #8b949e;
        font-size: 18px;
        cursor: pointer;
        transition: color 0.2s;
    }

    .console-close-btn:hover {
        color: #ff7b72;
    }

    .console-instructions {
        font-size: 13px;
        color: #8b949e;
        line-height: 1.5;
        margin-bottom: 20px;
    }

    /* Tab Layout Rail */
    .console-tab-rail {
        display: grid;
        grid-template-columns: repeat(3, 1fr);
        gap: 8px;
        margin-bottom: 16px;
    }

    .console-tab {
        background: rgba(33, 38, 45, 0.5);
        color: #c9d1d9;
        border: 1px solid rgba(240, 246, 252, 0.1);
        padding: 10px;
        border-radius: 8px;
        font-size: 12.5px;
        font-weight: 600;
        cursor: pointer;
        transition: all 0.2s ease;
    }

    .console-tab:hover, .console-tab.active {
        background: #21262d;
        border-color: #58a6ff;
        color: #ffffff;
    }

    /* Content Containment Frame */
    .console-frame-container {
        flex-grow: 1;
        position: relative;
        background: #0d1117;
        border: 1px solid rgba(240, 246, 252, 0.08);
        border-radius: 10px;
        overflow: hidden;
    }

    .frame-loading-overlay {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background: #0d1117;
        color: #8b949e;
        display: flex;
        justify-content: center;
        align-items: center;
        font-size: 13px;
        font-family: monospace;
        z-index: 2;
    }

    #portalIntakeFrame {
        width: 100%;
        height: 100%;
        border: none;
        position: absolute;
        top: 0;
        left: 0;
        z-index: 1;
    }
</style>

<script>
    // Clean View Route URLs Array
    const formEndpoints = [
        "https://docs.google.com/forms/d/e/1FAIpQLScyB-p-xY_XyB979S-hbyNreL638EAsD-2Ew_29u1fQ-u57QA/viewform",
        "https://docs.google.com/forms/d/e/1FAIpQLSfp63UonT3_9u4WclgT7Lp7Ew69f0R5vB_6_XU_68wU82B0rA/viewform",
        "https://docs.google.com/forms/d/e/1FAIpQLScsXy8xO5E6vB982G-89R1u_yH896u2_vY_U_28u88y66vO9A/viewform"
    ];

    let initializedChannel = 0;

    function openFormPortal() {
        const overlay = document.getElementById('portal-modal-overlay');
        document.body.style.overflow = 'hidden'; // Lock base screen navigation
        overlay.style.display = 'flex';
        
        // Force rendering paint cycle before adding animation classes
        setTimeout(() => {
            overlay.classList.add('portal-active');
            loadActiveChannel();
        }, 20);
    }

    function closeFormPortal() {
        const overlay = document.getElementById('portal-modal-overlay');
        overlay.classList.remove('portal-active');
        
        setTimeout(() => {
            overlay.style.display = 'none';
            document.body.style.overflow = ''; // Release parent track focus
            document.getElementById('portalIntakeFrame').src = "";
        }, 300);
    }

    function loadActiveChannel() {
        document.getElementById('frameLoader').style.display = 'flex';
        document.getElementById('portalIntakeFrame').src = formEndpoints[initializedChannel];
    }

    function switchFormChannel(tabElement, channelIndex) {
        if(channelIndex === initializedChannel) return;
        
        document.querySelectorAll('.console-tab').forEach(tab => tab.classList.remove('active'));
        tabElement.classList.add('active');
        
        initializedChannel = channelIndex;
        loadActiveChannel();
    }

    function hideFrameLoader() {
        document.getElementById('frameLoader').style.display = 'none';
    }

    // Attention Safeguard Trigger Mechanics
    function triggerBlockShake() {
        const panel = document.getElementById('portal-console-card');
        panel.classList.remove('shake-attention');
        
        // Forces DOM reflow engine validation to reset runtime keyframes
        void panel.offsetWidth; 
        
        panel.classList.add('shake-attention');
    }
</script>



<div id="dbz-faq-hub">
    <style>
        #dbz-faq-hub {
            --dbz-space-bg: #090d16;
            --dbz-panel-bg: rgba(15, 23, 42, 0.65);
            --dbz-card-border: rgba(255, 255, 255, 0.06);
            --dbz-text-main: #f8fafc;
            --dbz-text-muted: #94a3b8;
            --dbz-accent-neon: #d946ef; /* Ehub / DeBeatzGH Accent Magenta */
            --dbz-accent-blue: #3b82f6;
            
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Helvetica, sans-serif;
            background: var(--dbz-space-bg);
            color: var(--dbz-text-main);
            padding: 40px 16px;
            max-width: 768px;
            margin: 0 auto;
            border-radius: 24px;
        }

        #dbz-faq-hub h2 {
            text-align: center;
            font-size: 1.75rem;
            font-weight: 900;
            margin-bottom: 24px;
            background: linear-gradient(45deg, var(--dbz-text-main), var(--dbz-text-muted));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            letter-spacing: -0.5px;
        }

        /* Swipeable Mobile Category Bar */
        #dbz-faq-hub .category-slider {
            display: flex;
            gap: 10px;
            overflow-x: auto;
            scroll-snap-type: x mandatory;
            scrollbar-width: none; /* Hide scrollbar for Firefox */
            -webkit-overflow-scrolling: touch;
            padding-bottom: 16px;
            margin-bottom: 20px;
            border-bottom: 1px solid var(--dbz-card-border);
        }

        #dbz-faq-hub .category-slider::-webkit-scrollbar {
            display: none; /* Hide scrollbar for Chrome/Safari */
        }

        #dbz-faq-hub .cat-btn {
            flex: 0 0 auto;
            scroll-snap-align: start;
            background: rgba(255, 255, 255, 0.03);
            border: 1px solid var(--dbz-card-border);
            color: var(--dbz-text-muted);
            padding: 8px 18px;
            border-radius: 20px;
            font-size: 0.85rem;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.25s cubic-bezier(0.4, 0, 0.2, 1);
        }

        #dbz-faq-hub .cat-btn.active {
            background: linear-gradient(135deg, var(--dbz-accent-neon) 0%, var(--dbz-accent-blue) 100%);
            color: #ffffff;
            border-color: transparent;
            box-shadow: 0 4px 15px rgba(217, 70, 239, 0.25);
        }

        /* Lazy Load Accordion Layout */
        #dbz-faq-hub .faq-wrapper {
            display: none;
            flex-direction: column;
            gap: 12px;
        }

        #dbz-faq-hub .faq-wrapper.active {
            display: flex;
            animation: dbzFadeIn 0.35s ease;
        }

        #dbz-faq-hub .faq-item {
            background: var(--dbz-panel-bg);
            border: 1px solid var(--dbz-card-border);
            border-radius: 14px;
            overflow: hidden;
            transition: border-color 0.2s ease;
        }

        #dbz-faq-hub .faq-trigger {
            width: 100%;
            padding: 16px 20px;
            text-align: left;
            background: transparent;
            border: none;
            color: var(--dbz-text-main);
            font-size: 0.95rem;
            font-weight: 700;
            cursor: pointer;
            display: flex;
            justify-content: space-between;
            align-items: center;
            gap: 15px;
        }

        #dbz-faq-hub .faq-icon {
            font-size: 0.75rem;
            color: var(--dbz-text-muted);
            transition: transform 0.3s cubic-bezier(0.4, 0, 0.2, 1);
            flex-shrink: 0;
        }

        #dbz-faq-hub .faq-item.open {
            border-color: rgba(217, 70, 239, 0.25);
        }

        #dbz-faq-hub .faq-item.open .faq-icon {
            transform: rotate(180deg);
            color: var(--dbz-accent-neon);
        }

        #dbz-faq-hub .faq-content {
            max-height: 0;
            overflow: hidden;
            transition: max-height 0.3s cubic-bezier(0.4, 0, 0.2, 1);
            background: rgba(0, 0, 0, 0.15);
        }

        #dbz-faq-hub .faq-content-inner {
            padding: 16px 20px;
            font-size: 0.88rem;
            line-height: 1.5;
            color: var(--dbz-text-muted);
            border-top: 1px solid rgba(255, 255, 255, 0.02);
        }

        @keyframes dbzFadeIn {
            from { opacity: 0; transform: translateY(6px); }
            to { opacity: 1; transform: translateY(0); }
        }
    </style>

    <h2>Frequently Asked Questions</h2>

    <div class="category-slider" id="dbz-faq-cats">
        <button class="cat-btn active" onclick="switchFaqCategory('general')">General Portal</button>
        <button class="cat-btn" onclick="switchFaqCategory('ehub')">Ehub Streaming</button>
        <button class="cat-btn" onclick="switchFaqCategory('resources')">Creative Assets</button>
    </div>

    <div class="faq-wrapper active" id="faq-general">
        <div class="faq-item">
            <button class="faq-trigger" onclick="toggleFaqAccordion(this, 'What is the DeBeatzGH workspace hub?')">
                <span>What is the DeBeatzGH workspace hub?</span>
                <span class="faq-icon">▼</span>
            </button>
            <div class="faq-content"><div class="faq-content-inner"></div></div>
        </div>
        <div class="faq-item">
            <button class="faq-trigger" onclick="toggleFaqAccordion(this, 'How do I submit forms via GitHub pages safely?')">
                <span>How do I submit forms via GitHub pages safely?</span>
                <span class="faq-icon">▼</span>
            </button>
            <div class="faq-content"><div class="faq-content-inner"></div></div>
        </div>
    </div>

    <div class="faq-wrapper" id="faq-ehub">
        <div class="faq-item">
            <button class="faq-trigger" onclick="toggleFaqAccordion(this, 'Where can I find the official music countdown charts?')">
                <span>Where can I find the official music countdown charts?</span>
                <span class="faq-icon">▼</span>
            </button>
            <div class="faq-content"><div class="faq-content-inner"></div></div>
        </div>
        <div class="faq-item">
            <button class="faq-trigger" onclick="toggleFaqAccordion(this, 'Can I integrate the floating Ehub widget into my blog?')">
                <span>Can I integrate the floating Ehub widget into my blog?</span>
                <span class="faq-icon">▼</span>
            </button>
            <div class="faq-content"><div class="faq-content-inner"></div></div>
        </div>
    </div>

    <div class="faq-wrapper" id="faq-resources">
        <div class="faq-item">
            <button class="faq-trigger" onclick="toggleFaqAccordion(this, 'Are the blogger templates free to modify?')">
                <span>Are the blogger templates free to modify?</span>
                <span class="faq-icon">▼</span>
            </button>
            <div class="faq-content"><div class="faq-content-inner"></div></div>
        </div>
    </div>

    <script>
        // Tab Switch Engine
        function switchFaqCategory(catId) {
            // Deactivate existing layouts
            document.querySelectorAll('#dbz-faq-hub .faq-wrapper').forEach(wrapper => {
                wrapper.classList.remove('active');
            });
            document.querySelectorAll('#dbz-faq-hub .cat-btn').forEach(btn => {
                btn.classList.remove('active');
            });

            // Set current target view
            document.getElementById(`faq-${catId}`).classList.add('active');
            
            // Highlight target tab element dynamically
            const activeBtn = Array.from(document.querySelectorAll('#dbz-faq-hub .cat-btn')).find(btn => {
                return btn.getAttribute('onclick').includes(catId);
            });
            if (activeBtn) {
                activeBtn.classList.add('active');
                activeBtn.scrollIntoView({ behavior: 'smooth', block: 'nearest', inline: 'center' });
            }
        }

        // Lazy-Loading Accordion Logic Engine
        function toggleFaqAccordion(triggerElement, questionText) {
            const faqItem = triggerElement.parentElement;
            const contentPane = faqItem.querySelector('.faq-content');
            const innerTextNode = faqItem.querySelector('.faq-content-inner');

            // CRITICAL: Lazy Content Allocation Injection Guard
            if (!innerTextNode.innerHTML || innerTextNode.innerHTML.trim() === "") {
                innerTextNode.innerHTML = fetchLazyFaqData(questionText);
            }

            // Close other sibling items in the active view block
            const currentWrapper = faqItem.parentElement;
            currentWrapper.querySelectorAll('.faq-item').forEach(item => {
                if (item !== faqItem) {
                    item.classList.remove('open');
                    item.querySelector('.faq-content').style.maxHeight = null;
                }
            });

            // Toggle target element
            if (faqItem.classList.contains('open')) {
                faqItem.classList.remove('open');
                contentPane.style.maxHeight = null;
            } else {
                faqItem.classList.add('open');
                contentPane.style.maxHeight = contentPane.scrollHeight + "px";
            }
        }

        // Mock Data Dictionary Repository (Simulates secure API thread processing)
        function fetchLazyFaqData(question) {
            const dictionary = {
                "What is the DeBeatzGH workspace hub?": "The DeBeatzGH workspace hub is a unified dashboard designed to catalog tools, widgets, entertainment pipelines, and custom API interfaces for creators, developers, and platform managers.",
                "How do I submit forms via GitHub pages safely?": "Our system integrates lightweight sandboxed oembed environments. Your form fields render lazily inside designated sandboxes, bypassing raw infrastructure processing for maximum data compliance.",
                "Where can I find the official music countdown charts?": "All digital entertainment updates are broadcast live inside the Ehub portal stream. Simply deploy the layout toggle widget or launch our system carousel overlays to view updated ranks.",
                "Can I integrate the floating Ehub widget into my blog?": "Yes. The modular architecture is designed precisely to deploy inside standard GitHub project directories or Blogger static layouts with full theme styling isolation properties.",
                "Are the blogger templates free to modify?": "Absolutely. All layout templates, UI scripts, and asset tools generated across the DeBeatzGH ecosystem are distributed as completely customizable blueprints to scale up your platforms."
            };
            return dictionary[question] || "System parameter updated. Documentation log file is processing verification lines.";
        }

        // SWIPE GESTURE CONTROLS (Enables horizontal category swipe parsing for touch panels)
        (function() {
            const slider = document.getElementById('dbz-faq-cats');
            let isDown = false;
            let startX, scrollLeft;

            slider.addEventListener('mousedown', (e) => {
                isDown = true;
                startX = e.pageX - slider.offsetLeft;
                scrollLeft = slider.scrollLeft;
            });
            slider.addEventListener('mouseleave', () => isDown = false);
            slider.addEventListener('mouseup', () => isDown = false);
            slider.addEventListener('mousemove', (e) => {
                if(!isDown) return;
                e.preventDefault();
                const x = e.pageX - slider.offsetLeft;
                const walk = (x - startX) * 2;
                slider.scrollLeft = scrollLeft - walk;
            });
        })();
    </script>
</div>

<!--
  Blogger Product Catalog Carousel — GitHub Pages Iframer
  Author: debeatzgh + ChatGPT
  How to use in Blogger:
  1) Create a new HTML/JavaScript gadget (Layout ➜ Add a Gadget ➜ HTML/JavaScript) OR paste into a post in HTML mode.
  2) Paste this entire snippet. No external libraries needed.
  3) Edit the DATA section to add/remove items.
  Notes:
  - "Preview" opens the site inside a modal iframe (same page).
  - "Open" navigates to the GitHub Page in the same tab.
  - Fully responsive, keyboard accessible, and touch-friendly.
-->

<style>
  /* --- Reset-ish --- */
  .bdz * { box-sizing: border-box; }
  .bdz { font-family: system-ui, -apple-system, Segoe UI, Roboto, Inter, Arial, sans-serif; color: #0f172a; }

  /* --- Theme Tokens --- */
  :root {
    --bdz-bg: #f8fafc;           /* slate-50 */
    --bdz-card: #ffffff;         /* white */
    --bdz-ink: #0f172a;          /* slate-900 */
    --bdz-sub: #475569;          /* slate-600 */
    --bdz-brand: #2563eb;        /* blue-600 */
    --bdz-accent: #f59e0b;       /* amber-500 */
    --bdz-ring: rgba(37, 99, 235, 0.25);
    --bdz-shadow: 0 10px 25px rgba(15, 23, 42, 0.08);
    --bdz-radius: 16px;
  }

  /* --- Section Wrapper --- */
  .bdz-catalog { background: var(--bdz-bg); padding: 28px 16px; border-radius: var(--bdz-radius); position: relative; overflow: hidden; }
  .bdz-heading { display: flex; align-items: center; justify-content: space-between; gap: 16px; margin: 0 0 16px; }
  .bdz-title { font-size: clamp(1.1rem, 2vw, 1.6rem); font-weight: 800; letter-spacing: -0.02em; margin: 0; }
  .bdz-subtitle { font-size: 0.95rem; color: var(--bdz-sub); margin: 4px 0 0 0; }

  /* --- CTA banner --- */
  .bdz-cta { display: flex; flex-wrap: wrap; align-items: center; gap: 12px; margin: 16px 0 10px; }
  .bdz-cta-btn { appearance: none; border: none; padding: 10px 14px; border-radius: 999px; font-weight: 500; cursor: pointer; background: var(--bdz-brand); color: #fff; box-shadow: var(--bdz-shadow); transition: transform .15s ease, box-shadow .2s ease; }
  .bdz-cta-btn:hover { transform: translateY(-1px); }
  .bdz-cta-btn:focus { outline: 3px solid var(--bdz-ring); outline-offset: 2px; }
  .bdz-cta-btn.pulse { animation: bdzPulse 2.2s infinite; }
  @keyframes bdzPulse { 0% { box-shadow: 0 0 0 0 rgba(37,99,235,0.45);} 70% { box-shadow: 0 0 0 16px rgba(37,99,235,0);} 100% { box-shadow: 0 0 0 0 rgba(37,99,235,0);} }

  /* --- Carousel --- */
  .bdz-carousel { position: relative; }
  .bdz-track { display: flex; gap: 14px; overflow-x: auto; scroll-snap-type: x mandatory; -webkit-overflow-scrolling: touch; padding: 12px 4px 18px; scroll-behavior: smooth; }
  .bdz-card { min-width: clamp(160px, 32vw, 260px); background: var(--bdz-card); border-radius: var(--bdz-radius); box-shadow: var(--bdz-shadow); scroll-snap-align: start; overflow: hidden; position: relative; transition: transform .2s ease, box-shadow .2s ease; }
  .bdz-card:hover { transform: translateY(-2px); box-shadow: 0 16px 40px rgba(15,23,42,.12); }

  .bdz-thumb-wrap { position: relative; aspect-ratio: 16/9; background: #e2e8f0; overflow: hidden; }
  .bdz-thumb { width: 80%; height: 80%; object-fit: cover; display: block; }
  .bdz-chip { position: absolute; top: 10px; left: 10px; background: rgba(255,255,255,.85); color: var(--bdz-ink); font-size: 12px; padding: 4px 8px; border-radius: 999px; backdrop-filter: blur(6px); }

  .bdz-body { padding: 14px; }
  .bdz-item-title { font-size: 1.05rem; font-weight: 600; margin: 0 0 6px; letter-spacing: -0.015em; }
  .bdz-desc { color: var(--bdz-sub); font-size: .92rem; line-height: 1.35rem; min-height: 2.7rem; margin: 0 0 10px; }

  .bdz-actions { display: flex; gap: 10px; }
  .bdz-btn { flex: 1; appearance: none; border: none; padding: 10px 12px; border-radius: 10px; font-weight: 500; cursor: pointer; background: #eef2ff; color: #1e293b; transition: transform .12s ease, background .12s ease; }
  .bdz-btn:hover { transform: translateY(-1px); }
  .bdz-btn.primary { background: var(--bdz-brand); color: #fff; }
  .bdz-btn.secondary { background: #f1f5f9; }
  .bdz-btn.ghost { background: transparent; border: 1px dashed #cbd5e1; }

  /* --- Carousel Controls --- */
  .bdz-nav { position: absolute; inset: 0; pointer-events: none; }
  .bdz-arrow { position: absolute; top: 40%; transform: translateY(-50%); pointer-events: auto; border: none; background: rgba(15,23,42,.75); color: #fff; width: 40px; height: 40px; border-radius: 999px; cursor: pointer; display: grid; place-items: center; box-shadow: var(--bdz-shadow); }
  .bdz-arrow:hover { background: rgba(15,23,42,.95); }
  .bdz-prev { left: 6px; }
  .bdz-next { right: 6px; }

  .bdz-dots { display: flex; gap: 6px; justify-content: center; margin-top: 8px; }
  .bdz-dot { width: 8px; height: 8px; border-radius: 999px; background: #cbd5e1; border: none; }
  .bdz-dot.active { background: var(--bdz-ink); }

  /* --- Modal Iframe --- */
  .bdz-modal { position: fixed; inset: 0; display: none; align-items: center; justify-content: center; background: rgba(2,6,23,.65); backdrop-filter: blur(3px); z-index: 99999; }
  .bdz-modal.open { display: flex; animation: bdzFade .18s ease; }
  @keyframes bdzFade { from { opacity: 0 } to { opacity: 1 } }
  .bdz-modal-card { width: min(1200px, 95vw); height: min(85vh, 720px); background: var(--bdz-card); border-radius: 14px; box-shadow: 0 25px 80px rgba(0,0,0,.35); overflow: hidden; position: relative; }
  .bdz-modal-head { display: flex; align-items: center; justify-content: space-between; padding: 10px 12px; border-bottom: 1px solid #e2e8f0; }
  .bdz-modal-title { font-weight: 600; font-size: 0.98rem; }
  .bdz-modal-actions { display: flex; gap: 8px; }
  .bdz-close, .bdz-open-page { border: none; border-radius: 8px; padding: 8px 10px; font-weight: 500; cursor: pointer; }
  .bdz-open-page { background: #0ea5e9; color: #fff; }
  .bdz-close { background: #e2e8f0; }
  .bdz-iframe-wrap { position: relative; height: calc(80% - 36px); }
  .bdz-iframe { position: absolute; inset: 0; width: 100%; height: 90%; border: 0; }
  .bdz-skeleton { position: absolute; inset: 0; background: linear-gradient(120deg, #f1f5f9 20%, #e2e8f0 38%, #f1f5f9 61%); background-size: 200% 100%; animation: bdzShimmer 1.3s infinite; }
  @keyframes bdzShimmer { 0% { background-position: 180% 0 } 100% { background-position: -20% 0 } }

  /* --- No-JS fallback --- */
  .bdz-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(260px, 1fr)); gap: 14px; }

  /* --- Small helpers --- */
  .sr-only { position: absolute; width: 1px; height: 1px; padding: 0; margin: -1px; overflow: hidden; clip: rect(0,0,0,0); white-space: nowrap; border: 0; }
</style>

<section class="bdz bdz-catalog" role="region" aria-label="Product Catalog Carousel">
  <header class="bdz-heading">
    <div>
      <h2 class="bdz-title">Frontend Scripts & Widgets — GitHub Pages</h2>
      <p class="bdz-subtitle">Tap a card to preview instantly. Everything opens inline with an iframe or in the same tab.</p>
    </div>
    <div class="bdz-cta">
      <button class="bdz-cta-btn pulse" data-bdz-more></button>
    </div>
  </header>

  <div class="bdz-carousel" id="bdzCarousel" aria-roledescription="carousel">
    <div class="bdz-track" id="bdzTrack"></div>
    <div class="bdz-nav" aria-hidden="false">
      <button class="bdz-arrow bdz-prev" aria-label="Previous">
        <span aria-hidden="true">&#10094;</span>
      </button>
      <button class="bdz-arrow bdz-next" aria-label="Next">
        <span aria-hidden="true">&#10095;</span>
      </button>
    </div>
  </div>
  <div class="bdz-dots" id="bdzDots" aria-label="Carousel pagination"></div>

  <noscript>
    <div class="bdz-grid">
      <!-- Static fallback if JS is disabled (edit as needed) -->
      <a href="https://beatzde4.blogspot.com/p/firebase-curated-front-end-components.html" style="text-decoration:none;">
        <div class="bdz-card">
          <div class="bdz-thumb-wrap"></div>
          <div class="bdz-body">
            <h3 class="bdz-item-title">Browse More Scripts</h3>
            <p class="bdz-desc">Open the full catalog of reusable front-end components and Blogger widgets.</p>
          </div>
        </div>
      </a>
    </div>
  </noscript>
</section>

<!-- Modal viewer -->
<div class="bdz-modal" id="bdzModal" role="dialog" aria-modal="true" aria-labelledby="bdzModalTitle">
  <div class="bdz-modal-card">
    <div class="bdz-modal-head">
      <div class="bdz-modal-title" id="bdzModalTitle">Preview</div>
      <div class="bdz-modal-actions">
        <button class="bdz-open-page" id="bdzOpenFull">Open</button>
        <button class="bdz-close" id="bdzClose">Close</button>
      </div>
    </div>
    <div class="bdz-iframe-wrap">
      <div class="bdz-skeleton" id="bdzSkeleton"></div>
      <iframe class="bdz-iframe" id="bdzIframe" title="Inline Preview"></iframe>
    </div>
  </div>
</div>

<script>
(function(){
  // ===== 1) DATA: Add or edit catalog items here =====
  const BDZ_DATA = [
    {
      url: "https://debeatzgh1.github.io/Custom-Blogger-Theme-for-with-Dynamic-Post-Loading-and-Logo-/",
      title: "Custom Blogger Theme (Dynamic Loading + Logo)",
      desc: "Mobile-first Blogger template featuring infinite/dynamic post loading, sticky header with logo, and clean modern UI.",
      thumb: "https://debeatzgh.wordpress.com/wp-content/uploads/2025/08/generateamobile-firstresponsivebloggertemplatewithcustomizablecolorsfontsandsections1576324612066211977.jpg",
      tag: "Theme"
    },
    {
      url: "https://debeatzgh1.github.io/popup-html-page-generator-blogger/",
      title: "Popup HTML Page Generator (Blogger)",
      desc: "Generate clean popup pages/embeds for Blogger posts with thumbnail, title, and Read More — perfect for cross-blog promotion.",
      thumb: "https://debeatzgh.wordpress.com/wp-content/uploads/2025/08/createatoolthatgeneratesiframeorcard-styleembedsforindividualbloggerpostscompletewiththumbnailtitleandreadmorebuttonforcross-blogpromotion754077096311972631.jpg",
      tag: "Tool"
    },
    {
      url: "https://debeatzgh1.github.io/Sliding-Newsletter-Signup-Widget-with-Pulse-Animation/",
      title: "Sliding Newsletter Signup (Pulse)",
      desc: "Attention-grabbing email opt-in with slide-in panel and subtle pulse glow to boost signups.",
      thumb: "https://debeatzgh.wordpress.com/wp-content/uploads/2025/08/amodernflat-styleillustrationofanotificationbellwithglowinghighlightssurroundedbyabstractshapespaperenvelopesanddigitalicons28emailmessageupdate293314991682681990671.jpg",
      tag: "Widget"
    },
    {
      url: "https://debeatzgh1.github.io/Blogger-Product-Carousel-with-WhatsApp-Floating-Button/",
      title: "Product Carousel + WhatsApp Button",
      desc: "Showcase products with a slick carousel and instant WhatsApp chat — great for affiliate shops.",
      thumb: "https://debeatzgh.wordpress.com/wp-content/uploads/2025/08/designacleanmodernthumbnailforabloggerproductscarouseltool1711994558720457535.jpg",
      tag: "Carousel"
    },
    {
      url: "https://debeatzgh1.github.io/-Floating-Dock-Smart-Iframe-Modal/",
      title: "Floating Dock + Smart Iframe Modal",
      desc: "Modern floating dock of round icons (Patreon, Blogger, GitHub, etc.) with on-page iframe modal previews.",
      thumb: "https://debeatzgh.wordpress.com/wp-content/uploads/2025/08/amodernminimallayoutwithafloatingdockofcolorfulroundicons28patreonbloggergithub29ontherightsideofacleanwebpagemockup6676994054500999142.jpg",
      tag: "UI"
    },
    {
      url: "https://debeatzgh1.github.io/Modern-homepage-styling-with-TailwindCSS-/",
      title: "Modern Homepage Styling (Tailwind)",
      desc: "Starter homepage template: hero, features, and CTA styled like a SaaS landing page.",
      thumb: "https://debeatzgh.wordpress.com/wp-content/uploads/2025/08/createamodernandcleanthumbnailforawebdevelopmentproducttitledmodernhomepagestylingtemplatewithtailwindcss3420170625469385526.jpg",
      tag: "Template"
    },
    {
      url: "https://debeatzgh1.github.io/TechAdapt-Solutions-Strategies-for-Modern-Startups-and-Individuals/",
      title: "TechAdapt Strategies (Guide)",
      desc: "Actionable strategies and starter components tailored for startups and solo builders.",
      thumb: "https://debeatzgh.wordpress.com/wp-content/uploads/2025/08/wp-17550417188267308669484942620808.jpg",
      tag: "Guide"
    }
  ];

  const MORE_URL = "https://beatzde4.blogspot.com/p/firebase-curated-front-end-components.html";

  // ===== 2) DOM refs =====
  const track = document.getElementById('bdzTrack');
  const dots = document.getElementById('bdzDots');
  const carousel = document.getElementById('bdzCarousel');
  const prevBtn = carousel.querySelector('.bdz-prev');
  const nextBtn = carousel.querySelector('.bdz-next');
  const ctaMore = document.querySelector('[data-bdz-more]');

  const modal = document.getElementById('bdzModal');
  const iframe = document.getElementById('bdzIframe');
  const modalTitle = document.getElementById('bdzModalTitle');
  const openFull = document.getElementById('bdzOpenFull');
  const closeBtn = document.getElementById('bdzClose');
  const skeleton = document.getElementById('bdzSkeleton');

  // ===== 3) Build Cards =====
  const frag = document.createDocumentFragment();
  BDZ_DATA.forEach((item, idx) => {
    const card = document.createElement('article');
    card.className = 'bdz-card';
    card.setAttribute('tabindex', '0');
    card.setAttribute('aria-label', item.title);

    card.innerHTML = `
      <div class="bdz-thumb-wrap">
        <img class="bdz-thumb" loading="lazy" referrerpolicy="no-referrer" alt="${item.title} thumbnail" src="${item.thumb}">
        <span class="bdz-chip">${item.tag || 'Script'}</span>
      </div>
      <div class="bdz-body">
        <h3 class="bdz-item-title">${item.title}</h3>
        <p class="bdz-desc">${item.desc}</p>
        <div class="bdz-actions">
          <button class="bdz-btn primary" data-preview data-url="${item.url}" data-title="${item.title}">Preview</button>
          <button class="bdz-btn secondary" data-open data-url="${item.url}" aria-label="Open ${item.title}">Open</button>
        </div>
      </div>
    `;

    // Click on card image or body also previews
    card.querySelector('.bdz-thumb-wrap').addEventListener('click', () => openModal(item.url, item.title));
    card.querySelector('.bdz-body').addEventListener('click', (e) => {
      const isButton = e.target.closest('button');
      if (!isButton) openModal(item.url, item.title);
    });

    // Buttons
    card.querySelector('[data-preview]').addEventListener('click', (e) => {
      e.stopPropagation();
      openModal(item.url, item.title);
    });
    card.querySelector('[data-open]').addEventListener('click', (e) => {
      e.stopPropagation();
      window.location.href = item.url; // same tab
    });

    frag.appendChild(card);
  });
  track.appendChild(frag);

  // ===== 4) Dots =====
  const pageSize = () => {
    // Estimate cards per view
    const card = track.querySelector('.bdz-card');
    if (!card) return 1;
    const vw = track.clientWidth;
    const cw = card.clientWidth + 14; // card + gap
    return Math.max(1, Math.round(vw / cw));
  };

  const pageCount = () => Math.max(1, Math.ceil(BDZ_DATA.length / pageSize()));

  function buildDots(){
    dots.innerHTML = '';
    const pages = pageCount();
    for (let i=0; i<pages; i++){
      const dot = document.createElement('button');
      dot.className = 'bdz-dot' + (i===0 ? ' active' : '');
      dot.setAttribute('aria-label', 'Go to slide '+(i+1));
      dot.addEventListener('click', () => goToPage(i));
      dots.appendChild(dot);
    }
  }
  buildDots();
  window.addEventListener('resize', () => { buildDots(); });

  function goToPage(i){
    const ps = pageSize();
    const card = track.querySelector('.bdz-card');
    if (!card) return;
    const cw = card.clientWidth + 14;
    track.scrollTo({ left: i * cw * ps, behavior: 'smooth' });
  }

  function updateDots(){
    const ps = pageSize();
    const card = track.querySelector('.bdz-card');
    if (!card) return;
    const cw = card.clientWidth + 14;
    const idx = Math.round(track.scrollLeft / (cw * ps));
    const all = dots.querySelectorAll('.bdz-dot');
    all.forEach((d,i)=> d.classList.toggle('active', i===idx));
  }
  track.addEventListener('scroll', () => { updateDots(); });

  // ===== 5) Navigation & Autoplay =====
  prevBtn.addEventListener('click', () => { goRel(-1); });
  nextBtn.addEventListener('click', () => { goRel(1); });

  function goRel(delta){
    const ps = pageSize();
    const card = track.querySelector('.bdz-card');
    if (!card) return;
    const cw = card.clientWidth + 14;
    const cur = Math.round(track.scrollLeft / (cw * ps));
    const next = Math.max(0, Math.min(pageCount()-1, cur + delta));
    goToPage(next);
  }

  let autoTimer = setInterval(()=>{ goRel(1); if (dots.querySelectorAll('.bdz-dot.active').length && dots.lastChild.classList.contains('active')) goToPage(0); }, 5000);
  [track, carousel].forEach(el=>{
    el.addEventListener('mouseenter', ()=> clearInterval(autoTimer));
    el.addEventListener('mouseleave', ()=> autoTimer = setInterval(()=>{ goRel(1); if (dots.lastChild.classList.contains('active')) goToPage(0); }, 5000));
  });
  // Keyboard
  carousel.addEventListener('keydown', (e)=>{ if (e.key==='ArrowLeft') goRel(-1); if (e.key==='ArrowRight') goRel(1); });

  // ===== 6) Modal Iframe Logic =====
  function openModal(url, title){
    modal.classList.add('open');
    document.body.style.overflow = 'hidden';
    modalTitle.textContent = title || 'Preview';
    iframe.src = '';
    skeleton.style.display = 'block';
    setTimeout(()=>{ iframe.src = url; }, 60);
    openFull.onclick = () => { window.location.href = url; };
  }
  function closeModal(){
    modal.classList.remove('open');
    document.body.style.overflow = '';
    iframe.src = '';
  }
  closeBtn.addEventListener('click', closeModal);
  modal.addEventListener('click', (e)=>{ if (e.target === modal) closeModal(); });
  document.addEventListener('keydown', (e)=>{ if (e.key === 'Escape') closeModal(); });
  iframe.addEventListener('load', ()=>{ skeleton.style.display = 'none'; });

  // ===== 7) CTA: View More Scripts =====
  ctaMore.addEventListener('click', ()=> { window.location.href = MORE_URL; });

  // ===== 8) Progressive image loading (optional nicety) =====
  const imgs = track.querySelectorAll('img[loading="lazy"]');
  const io = ('IntersectionObserver' in window) ? new IntersectionObserver((entries)=>{
    entries.forEach(entry=>{
      if (entry.isIntersecting){
        const img = entry.target; img.src = img.getAttribute('src'); io.unobserve(img);
      }
    })
  }, { root: track, rootMargin: '100px' }) : null;
  if (io) imgs.forEach(img=> io.observe(img));
})();
</script>

<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>DeBeatzGH | Smart Overlay</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">
    <style>
        :root {
            --accent: #00f2ff;
            --glass: rgba(15, 15, 20, 0.8);
            --border: rgba(255, 255, 255, 0.1);
        }

        body { background: #050507; font-family: 'Plus Jakarta Sans', sans-serif; height: 200vh; }

        /* --- 1. TRANSPARENT FLOATING BUTTON --- */
        #home-trigger {
            position: fixed; bottom: 30px; left: 30px;
            width: 55px; height: 55px;
            background: rgba(255, 255, 255, 0.05);
            backdrop-filter: blur(10px);
            border: 1px solid var(--border);
            border-radius: 50%;
            display: flex; align-items: center; justify-content: center;
            cursor: pointer; z-index: 10000;
            transition: 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
        }

        #home-trigger:hover { border-color: var(--accent); background: rgba(0, 242, 255, 0.1); transform: scale(1.1); }

        /* --- 2. SCROLL INDICATOR ICONS --- */
        .scroll-icon {
            position: fixed; bottom: 95px; left: 47px;
            font-size: 10px; color: var(--accent);
            opacity: 0; transition: 0.3s; pointer-events: none;
        }
        .scroll-icon.active { opacity: 1; transform: translateY(-5px); }

        /* --- 3. OVERLAY CONTAINER --- */
        #home-overlay {
            position: fixed; inset: 0;
            background: rgba(0,0,0,0.9);
            backdrop-filter: blur(15px);
            display: none; z-index: 10001;
            padding: 20px; flex-direction: column;
            animation: fadeIn 0.4s ease;
        }

        .iframe-shell {
            width: 100%; height: 100%;
            border: 1px solid var(--border);
            border-radius: 24px; overflow: hidden;
            background: #fff; box-shadow: 0 0 50px rgba(0,0,0,0.5);
            position: relative;
        }

        /* --- 4. SMART PROMPT --- */
        #stay-prompt {
            position: fixed; top: 50%; left: 50%;
            transform: translate(-50%, -50%);
            width: 320px; background: #111; border: 1px solid var(--accent);
            border-radius: 20px; padding: 25px;
            display: none; z-index: 10005; text-align: center;
            box-shadow: 0 0 40px rgba(0, 242, 255, 0.2);
        }

        @keyframes fadeIn { from { opacity: 0; } to { opacity: 1; } }
        @keyframes bounce { 0%, 100% { transform: translateY(0); } 50% { transform: translateY(-10px); } }
        .auto-pulse { animation: bounce 1s infinite; border-color: var(--accent) !important; }

    </style>
</head>
<body>

    <i id="scroll-up" class="fas fa-chevron-up scroll-icon"></i>
    <i id="scroll-down" class="fas fa-chevron-down scroll-icon"></i>

    <div id="home-trigger" onclick="toggleHome()">
        <i class="fas fa-home text-white/50 text-sm" id="main-icon"></i>
    </div>

    <div id="home-overlay">
        <div class="flex justify-between items-center mb-4 px-4">
            <span class="text-[10px] font-black tracking-widest text-cyan-400">DEBEATZGH_HOME // LIVE_VIEW</span>
            <button onclick="toggleHome()" class="text-gray-500 hover:text-white text-xs font-bold uppercase">
               <i class="fas fa-times mr-1"></i> Close
            </button>
        </div>
        <div class="iframe-shell">
            <iframe id="home-frame" src="" class="w-full h-full border-none"></iframe>
        </div>
    </div>

    <div id="stay-prompt">
        <h3 class="text-white font-bold mb-2">Session Sync</h3>
        <p class="text-gray-500 text-[11px] mb-6">You've been active for 1 minute. How would you like to continue?</p>
        <div class="flex flex-col gap-2">
            <button onclick="handlePrompt('stay')" class="bg-cyan-500 text-black py-3 rounded-xl text-[10px] font-black uppercase">Stay on Page</button>
            <button onclick="handlePrompt('new')" class="border border-white/10 text-white py-3 rounded-xl text-[10px] font-bold uppercase hover:bg-white/5">Open New Tab</button>
        </div>
    </div>

    <script>
        const homeUrl = "https://debeatzgh1.github.io/Home-/";
        let lastScrollTop = 0;

        // --- 1. AUTO-POPUP LOGIC (Every 6s) ---
        setInterval(() => {
            const btn = document.getElementById('home-trigger');
            btn.classList.add('auto-pulse');
            setTimeout(() => btn.classList.remove('auto-pulse'), 2000);
        }, 6000);

        // --- 2. SCROLL DIRECTION LOGIC ---
        window.addEventListener("scroll", () => {
            let st = window.pageYOffset || document.documentElement.scrollTop;
            const up = document.getElementById('scroll-up');
            const down = document.getElementById('scroll-down');

            if (st > lastScrollTop) {
                down.classList.add('active');
                up.classList.remove('active');
            } else {
                up.classList.add('active');
                down.classList.remove('active');
            }
            lastScrollTop = st <= 0 ? 0 : st;
            
            // Auto hide after 1.5s stillness
            clearTimeout(window.scrollTimer);
            window.scrollTimer = setTimeout(() => {
                up.classList.remove('active');
                down.classList.remove('active');
            }, 1500);
        });

        // --- 3. OVERLAY TOGGLE ---
        function toggleHome() {
            const overlay = document.getElementById('home-overlay');
            const frame = document.getElementById('home-frame');
            const isVisible = overlay.style.display === 'flex';

            if (!isVisible) {
                frame.src = homeUrl;
                overlay.style.display = 'flex';
                document.body.style.overflow = 'hidden';
            } else {
                overlay.style.display = 'none';
                frame.src = "";
                document.body.style.overflow = 'auto';
            }
        }

        // --- 4. ONE MINUTE PROMPT LOGIC ---
        setTimeout(() => {
            document.getElementById('stay-prompt').style.display = 'block';
        }, 60000);

        function handlePrompt(choice) {
            const prompt = document.getElementById('stay-prompt');
            prompt.style.display = 'none';

            if (choice === 'stay') {
                // If on same page, ensure UI is minimized/closed if open
                console.log("User chose to stay.");
            } else {
                // Open in new tab without leaving current
                window.open(homeUrl, '_blank');
            }
        }
    </script>
</body>
</html>





<iframe src="https://msha.ke/debeatzgh#about-4" width="100%" height="400" frameborder="0" allowfullscreen></iframe>



<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">
    <style>
        :root {
            --bg-color: #0d1117;
            --text-color: #ffffff;
            --dock-bg: rgba(15, 15, 20, 0.95);
            --dock-border: rgba(255, 255, 255, 0.12);
            --accent: #FF1493;
            --scroll-bg: #30363d;
            --dev-green: #2ea44f;
        }

        body.light-mode {
            --bg-color: #f0f2f5;
            --text-color: #1c1e21;
            --dock-bg: rgba(255, 255, 255, 0.95);
            --dock-border: rgba(0, 0, 0, 0.1);
            --scroll-bg: #e1e4e8;
        }

        body { 
            background-color: var(--bg-color); 
            color: var(--text-color); 
            transition: background 0.5s ease;
            margin: 0;
            min-height: 200vh;
            scroll-behavior: smooth;
        }

        /* --- SOCIAL DOCK --- */
        .social-dock {
            position: fixed;
            right: 25px;
            bottom: 30px;
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 10px;
            background: var(--dock-bg);
            padding: 12px 10px;
            border-radius: 50px;
            border: 1px solid var(--dock-border);
            backdrop-filter: blur(15px);
            box-shadow: 0 15px 40px rgba(0,0,0,0.4);
            z-index: 10002;
            opacity: 0;
            transform: translateY(30px);
            transition: all 0.6s cubic-bezier(0.175, 0.885, 0.32, 1.275);
        }

        .social-dock.show, .social-dock.is-locked { opacity: 1 !important; transform: translateY(0) !important; }
        .social-dock.is-locked { border-color: var(--accent); }

        /* --- DEV STATUS --- */
        .dev-status {
            font-size: 7px;
            text-transform: uppercase;
            font-weight: 900;
            color: var(--dev-green);
            letter-spacing: 0.5px;
            text-align: center;
            line-height: 1;
            margin-bottom: 2px;
        }

        #commit-date { color: var(--text-color); opacity: 0.6; display: block; margin-top: 2px; }

        .theme-btn {
            width: 36px; height: 36px; border-radius: 50%;
            display: flex; align-items: center; justify-content: center;
            color: #FFD700; cursor: pointer; transition: 0.3s;
        }

        /* --- ICONS --- */
        .social-icon {
            width: 40px; height: 40px;
            display: flex; align-items: center; justify-content: center;
            border-radius: 50%; color: var(--text-color);
            text-decoration: none; font-size: 1.1rem;
            transition: 0.3s; position: relative;
        }
        .social-icon:hover { transform: scale(1.15); color: var(--accent); }

        #backToTop {
            width: 36px; height: 36px; background: var(--scroll-bg);
            border-radius: 50%; display: flex; align-items: center; justify-content: center;
            cursor: pointer; font-size: 0.8rem; opacity: 0; visibility: hidden;
            transition: 0.4s; margin-top: 5px;
        }
        #backToTop.visible { opacity: 1; visibility: visible; }

        .share-toast {
            position: absolute; right: 55px; background: var(--accent);
            color: #fff; padding: 4px 10px; border-radius: 4px;
            font-size: 10px; font-weight: 800; opacity: 0;
            transition: 0.3s; white-space: nowrap;
        }

        .sep { width: 18px; height: 1px; background: var(--dock-border); margin: 4px 0; }
    </style>
</head>
<body id="top">

    <div class="social-dock" id="socialDock">
        <div class="dev-status">
            Updated
            <span id="commit-date">Loading...</span>
        </div>

        <div class="theme-btn" onclick="toggleThemeAndLock()" title="Theme & Lock">
            <i class="fas fa-sun" id="themeIcon"></i>
        </div>
        
        <a href="https://www.instagram.com/debeatzgh" target="_blank" class="social-icon"><i class="fab fa-instagram"></i></a>
        <a href="https://www.facebook.com/Debeatzgh" target="_blank" class="social-icon"><i class="fab fa-facebook-f"></i></a>
        <a href="https://debeatzgh1.github.io/Pages-/" target="_blank" class="social-icon"><i class="fas fa-layer-group"></i></a>
        <a href="https://debeatzgh1.github.io/blogs/" target="_blank" class="social-icon"><i class="fas fa-rss"></i></a>

        <div class="sep"></div>

        <div class="social-icon" onclick="copySiteLink()" style="cursor: pointer;">
            <i class="fas fa-share-alt"></i>
            <div class="share-toast" id="shareToast">Copied!</div>
        </div>

        <div id="backToTop" onclick="scrollToTop()" title="Back to Top">
            <i class="fas fa-chevron-up"></i>
        </div>
    </div>

    <script>
        const body = document.body;
        const dock = document.getElementById('socialDock');
        const themeIcon = document.getElementById('themeIcon');
        const bttBtn = document.getElementById('backToTop');
        const toast = document.getElementById('shareToast');
        let isLocked = false;
        let breatheInterval;

        // --- FETCH GITHUB DATA ---
        async function fetchLastCommit() {
            try {
                const response = await fetch('https://api.github.com/repos/debeatzgh1/debeatzgh/commits/main');
                const data = await response.json();
                const date = new Date(data.commit.author.date);
                const options = { month: 'short', day: 'numeric' };
                document.getElementById('commit-date').innerText = date.toLocaleDateString('en-US', options);
            } catch (error) {
                document.getElementById('commit-date').innerText = "Recent";
            }
        }

        function toggleThemeAndLock() {
            body.classList.toggle('light-mode');
            const isLight = body.classList.contains('light-mode');
            themeIcon.className = isLight ? 'fas fa-moon' : 'fas fa-sun';
            isLocked = true;
            dock.classList.add('is-locked');
            clearInterval(breatheInterval);
        }

        window.onscroll = () => {
            if (window.scrollY > 300) bttBtn.classList.add('visible');
            else bttBtn.classList.remove('visible');
        };

        function scrollToTop() { window.scrollTo({ top: 0, behavior: 'smooth' }); }

        async function copySiteLink() {
            await navigator.clipboard.writeText(window.location.href);
            toast.style.opacity = "1";
            setTimeout(() => { toast.style.opacity = "0"; }, 2000);
        }

        function runBreathe() {
            if (isLocked) return;
            dock.classList.add('show');
            setTimeout(() => { if (!isLocked) dock.classList.remove('show'); }, 4000);
        }

        function startBreatheCycle() {
            clearInterval(breatheInterval);
            runBreathe();
            breatheInterval = setInterval(runBreathe, 8000);
        }

        // INIT
        fetchLastCommit();
        setTimeout(startBreatheCycle, 1000);
    </script>
</body>
</html>






<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>G-Dev Portfolio | Hiring Portal</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Google+Sans:wght@400;500;700&display=swap');

        :root {
            --g-blue: #8ab4f8;
            --g-green: #34A853;
            --dark-bg: #1a1c1e;
            --dark-card: #2d2f31;
            --glass-border: rgba(255, 255, 255, 0.08);
        }

        body { font-family: 'Google Sans', sans-serif; background: #121212; margin: 0; }

        /* 1. LAUNCHER */
        #gdev-launcher {
            position: fixed; left: 20px; top: 50%; transform: translateY(-50%);
            display: flex; align-items: center; gap: 12px;
            background: var(--dark-card); padding: 8px 18px 8px 8px;
            border-radius: 40px; cursor: pointer; z-index: 9999;
            box-shadow: 0 10px 40px rgba(0,0,0,0.5);
            transition: 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            border: 1px solid var(--glass-border);
        }

        #gdev-launcher:hover { transform: translateY(-50%) scale(1.08) translateX(5px); border-color: var(--g-blue); }

        .dev-avatar {
            width: 30px; height: 30px; background: #121212; border-radius: 50%;
            display: flex; align-items: center; justify-content: center;
            border: 2px solid var(--g-blue); color: var(--g-blue); position: relative;
        }

        .status-dot {
            position: absolute; bottom: 2px; right: 2px; width: 10px; height: 10px;
            background: var(--g-green); border-radius: 50%; border: 2px solid var(--dark-card);
        }

        .status-glow {
            position: absolute; inset: 0; background: var(--g-green);
            border-radius: 50%; animation: status-pulse 2s infinite;
        }

        @keyframes status-pulse { 0% { transform: scale(1); opacity: 0.8; } 100% { transform: scale(2.5); opacity: 0; } }

        /* 2. OVERLAY MODAL */
        #gdev-overlay {
            position: fixed; inset: 0; background: rgba(0,0,0,0.85);
            backdrop-filter: blur(12px); display: none; z-index: 10000;
            justify-content: center; align-items: center; padding: 20px;
            opacity: 0; transition: opacity 0.4s ease;
        }

        #gdev-overlay.active { display: flex; opacity: 1; }

        .gdev-modal {
            width: 100%; max-width: 950px; height: 92vh;
            background: var(--dark-bg); border-radius: 28px;
            display: flex; flex-direction: column; overflow: hidden;
            border: 1px solid var(--glass-border); position: relative;
        }

        /* 3. IFRAME & FOOTER */
        #gdev-frame { flex-grow: 1; width: 100%; border: none; background: #fff; }

        .close-gdev {
            position: absolute; top: 20px; right: 25px; width: 40px; height: 30px;
            background: var(--dark-card); border-radius: 50%;
            display: flex; align-items: center; justify-content: center;
            cursor: pointer; color: #fff; z-index: 20;
        }

        /* CONTACT ME BUTTON STYLE */
        .hire-btn {
            background: var(--g-green);
            color: white;
            padding: 8px 18px;
            border-radius: 20px;
            font-size: 11px;
            font-weight: 800;
            text-transform: uppercase;
            letter-spacing: 1px;
            display: flex;
            align-items: center;
            gap: 8px;
            transition: 0.3s;
            box-shadow: 0 4px 15px rgba(52, 168, 83, 0.3);
        }
        .hire-btn:hover { transform: translateY(-2px); box-shadow: 0 6px 20px rgba(52, 168, 83, 0.4); background: #2e964a; }

        @media (max-width: 768px) {
            .gdev-modal { height: 100vh; border-radius: 0; }
            .footer-controls { flex-direction: column; gap: 10px; padding: 15px; }
        }
    </style>
</head>
<body>

    <div id="gdev-launcher" onclick="toggleGDev()">
        <div class="dev-avatar">
            <i class="fab fa-google"></i>
            <div class="status-dot"><div class="status-glow"></div></div>
        </div>
        <div class="hidden sm:block">
            <div class="flex items-center gap-2">
                <span class="text-[9px] text-[#34A853] font-bold uppercase tracking-widest">Active</span>
            </div>
            <p class="text-[14px] font-medium text-gray-200">@debeatzgh</p>
        </div>
    </div>

    <div id="gdev-overlay">
        <div class="gdev-modal">
            <div class="close-gdev" onclick="toggleGDev()"><i class="fas fa-times"></i></div>
            
            <iframe id="gdev-frame" src=""></iframe>

            <div class="footer-controls p-4 bg-[#1a1c1e] border-t border-white/5 flex justify-between items-center px-8">
                <span class="text-[9px] text-gray-600 font-bold uppercase tracking-[2px]">G-Dev Protocol v4.0</span>
                
                <div class="flex items-center gap-3">
                    <button id="copy-btn" class="text-[11px] text-[#8ab4f8] font-bold px-4 py-2 hover:text-white transition" onclick="copyProfileLink()">
                        Copy Profile
                    </button>
                    <a href="https://wa.me/233549757544?text=Hi%20DeBeatz,%20I%20saw%20your%20Google%20Dev%20profile%20and%20would%20like%20to%20discuss%20a%20project." 
                       target="_blank" class="hire-btn">
                        <i class="fas fa-briefcase"></i> Contact Me
                    </a>
                </div>
            </div>
        </div>
    </div>

    <script>
        const overlay = document.getElementById('gdev-overlay');
        const frame = document.getElementById('gdev-frame');
        const profileUrl = "https://docs.google.com/forms/d/e/1FAIpQLSdipVP7tU1hjTjECfWUdnhzWN-PROdQp19ng25EUDJk5-8JzA/viewform?usp=header";

        function toggleGDev() {
            if (overlay.style.display === 'flex') {
                overlay.classList.remove('active');
                setTimeout(() => { overlay.style.display = 'none'; frame.src = ""; }, 400);
                document.body.style.overflow = 'auto';
            } else {
                overlay.style.display = 'flex';
                setTimeout(() => overlay.classList.add('active'), 10);
                frame.src = profileUrl;
                document.body.style.overflow = 'hidden';
            }
        }

        async function copyProfileLink() {
            await navigator.clipboard.writeText(profileUrl);
            const btn = document.getElementById('copy-btn');
            btn.innerText = "Copied!";
            setTimeout(() => { btn.innerText = "Copy Profile"; }, 2000);
        }

        overlay.onclick = (e) => { if (e.target === overlay) toggleGDev(); };
    </script>
</body>
</html>








# 💎 Digital Ecosystem Hub

**A High-Performance Software Developer Portal & AI Strategy Command Center.**

This UI hosts the **your Digital Hub**, a unified interface designed to bridge the gap between software development, AI automation, and digital content strategy. Built with a "SaaS-first" aesthetic, it utilizes modern web technologies to provide a seamless, app-like experience on GitHub Pages.

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
        <i class="fab fa-whatsapp text-lg"></i> contact 
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
