<style>
  /* 🌟 Fade Slide Animation */
  @keyframes fadeSlideUp {
    0% { opacity: 0; transform: translateY(0) translateX(20px); }
    100% { opacity: 1; transform: translateY(0) translateX(0); }
  }

  /* ❤️ Heartbeat Animation */
  @keyframes heartbeat {
    0% { transform: scale(1); }
    25% { transform: scale(1.08); }
    50% { transform: scale(1); }
    75% { transform: scale(1.08); }
    100% { transform: scale(1); }
  }

  .floating-btn-group {
    animation: fadeSlideUp 0.6s ease-out;
  }

  /* Iframe Modal Styles */
  #iframe-modal {
    display: none;
    position: fixed;
    z-index: 9999;
    left: 0;
    top: 0;
    width: 100%;
    height: 115%;
    background: rgba(0,0,0,0.6);
    backdrop-filter: blur(4px);
  }

  .modal-content {
    position: relative;
    margin: 2% auto;
    background: #fff;
    border-radius: 16px;
    width: 95%;
    height: 90%;
    box-shadow: 0 8px 24px rgba(0,0,0,0.3);
    overflow: hidden;
    animation: fadeIn 0.3s ease;
  }

  #modal-iframe {
    width: 100%;
    height: 105%;
    border: none;
  }

  .close-btn {
    position: absolute;
    top: 10px;
    right: 18px;
    font-size: 30px;
    color: #333;
    cursor: pointer;
    transition: color 0.2s;
    z-index: 10;
  }

  .close-btn:hover {
    color: #e11d48;
  }

  @keyframes fadeIn {
    from {opacity: 0; transform: translateY(-10px);}
    to {opacity: 1; transform: translateY(0);}
  }
</style>

<script>
document.addEventListener("DOMContentLoaded", function () {

  // 🔹 Floating Button at TOP-LEFT
  const btnGroup = document.createElement("div");
  btnGroup.className = "floating-btn-group";
  Object.assign(btnGroup.style, {
    position: "fixed",
    top: "20px",          // Top-left positioning
    left: "20px",
    zIndex: "9999",
    animation: "heartbeat 2.5s infinite ease-in-out, fadeSlideUp 0.6s ease-out forwards"
  });

  // -------------------------------------------------------
  // 📌 Updates Button
  // -------------------------------------------------------
  const button = document.createElement("a");
  button.href = "#";
  button.innerText = "📌 Updates";
  Object.assign(button.style, {
    background: "#16a34a",
    color: "#fff",
    padding: "12px 24px",
    borderRadius: "30px",
    textDecoration: "none",
    fontSize: "15px",
    fontWeight: "700",
    boxShadow: "0 4px 10px rgba(0,0,0,0.25)",
    whiteSpace: "nowrap",
  });

  // 🔹 Iframe Modal
  const modal = document.createElement("div");
  modal.id = "iframe-modal";
  modal.innerHTML = `
    <div class="modal-content">
      <span class="close-btn">&times;</span>
      <iframe id="modal-iframe" src="" loading="lazy"></iframe>
    </div>
  `;

  document.body.appendChild(modal);

  // 🔹 Open Iframe on click
  button.addEventListener("click", function (e) {
    e.preventDefault();
    document.getElementById("modal-iframe").src = "https://debeatzgh1.github.io/Digital-Creator-s-Essential-Guides-Tools/";
    modal.style.display = "block";
  });

  btnGroup.appendChild(button);
  document.body.appendChild(btnGroup);

  // 🔹 Close Modal
  document.addEventListener("click", function (e) {
    if (e.target.classList.contains("close-btn") || e.target.id === "iframe-modal") {
      modal.style.display = "none";
      document.getElementById("modal-iframe").src = "";
    }
  });

  // 🔹 Auto-open external ads in a new tab
  document.getElementById("modal-iframe").addEventListener("load", function () {
    try {
      const links = this.contentDocument.querySelectorAll("a");
      links.forEach(link => {
        if (!link.href.includes("debeatzgh.wordpress.com")) {
          link.setAttribute("target", "_blank");
          link.setAttribute("rel", "noopener");
        }
      });
    } catch (err) {
      console.warn("External site - cannot rewrite links");
    }
  });

});
</script>


<!doctype html>




Debeatzgh Iframe Carousel
<style>
  body { margin:0; font-family: Arial, sans-serif; background:#f5f5f5; }

  @keyframes heartbeat {0%{transform:translateX(-50%) scale(1);}25%{transform:translateX(-50%) scale(1.08);}50%{transform:translateX(-50%) scale(1);}75%{transform:translateX(-50%) scale(1.08);}100%{transform:translateX(-50%) scale(1);}}

  #floating-btn {
    position: fixed; center: 20px; left: 50%; transform: translateX(-50%);
    width: 60px; height: 60px; background:#007bff; color:#fff;
    font-size:28px; display:flex; align-items:center; justify-content:center;
    cursor:pointer; border-radius:50%; box-shadow:0 4px 12px rgba(0,0,0,0.3);
    opacity:0; animation:heartbeat 2.5s infinite ease-in-out; transition:opacity 0.8s; z-index:9999;
  }

  #carousel-modal { display:none; position:fixed; top:0; left:0; width:100%; height:100%; background:rgba(0,0,0,0.8); backdrop-filter:blur(4px); z-index:9998; }
  .carousel-content { position:relative; width:100%; height:100%; padding:50px 0; box-sizing:border-box; }
  .carousel-slide { display:none; width:100%; height:100%; text-align:center; }
  .carousel-slide.active { display:block; }
  .carousel-thumb { width:200px; border-radius:12px; margin-bottom:12px; }
  .carousel-title { font-size:20px; font-weight:700; color:#fff; margin-bottom:8px; }
  .carousel-desc { font-size:14px; color:#eee; margin-bottom:12px; }
  .carousel-btn { padding:10px 20px; background:#16a34a; color:#fff; border:none; border-radius:8px; cursor:pointer; font-weight:700; }
  .close-btn { position:absolute; top:15px; right:20px; font-size:32px; color:#fff; cursor:pointer; z-index:10; }
  .carousel-nav { position:absolute; bottom:40px; left:50%; transform:translateX(-50%); display:flex; gap:15px; }
  .nav-btn { background:#fff; border:none; padding:10px 16px; border-radius:10px; font-weight:700; cursor:pointer; }
</style>



<div id="floating-btn">+</div>

<div id="carousel-modal">
  <div class="carousel-content">
    <span class="close-btn">×</span>

    <div class="carousel-slide active" data-url="https://msha.ke/debeatzgh">
      <img class="carousel-thumb" src="https://debeatzgh.wordpress.com/wp-content/uploads/2025/08/designadigitalproductse-commerceonlinedeals3545265155247625100.jpg" />
      <div class="carousel-title">Website</div>
      <div class="carousel-desc">Check out our main website for digital products and deals.</div>
      <button class="carousel-btn" onclick="openIframe('https://msha.ke/debeatzgh')">Open Website</button>
    </div>

    <div class="carousel-slide" data-url="https://debeatzgh.wordpress.com/">
      <img class="carousel-thumb" src="https://debeatzgh.wordpress.com/wp-content/uploads/2025/12/1763148379311_1619032177476517720.jpg" />
      <div class="carousel-title">Blog</div>
      <div class="carousel-desc">Visit our blog for latest updates, guides, and news.</div>
      <button class="carousel-btn" onclick="openIframe('https://debeatzgh.wordpress.com/')">Open Blog</button>
    </div>

    <div class="carousel-slide" data-url="https://github.com/apps/dkonsult">
      <img class="carousel-thumb" src="https://debeatzgh.wordpress.com/wp-content/uploads/2025/08/wp-17550753355015215823208011315422.jpg" />
      <div class="carousel-title">Sign Up</div>
      <div class="carousel-desc">Sign up for the GitHub app directly in a new tab.</div>
      <button class="carousel-btn" onclick="window.open('https://github.com/apps/dkonsult','_blank')">Sign Up (New Tab)</button>
    </div>

    <div class="carousel-nav">
      <button class="nav-btn" id="prev">Prev</button>
      <button class="nav-btn" id="next">Next</button>
    </div>
  </div>
</div>

<script>
// Show floating button after 3 seconds
setTimeout(()=>{document.getElementById('floating-btn').style.opacity='1';},3000);

const btn = document.getElementById('floating-btn');
const modal = document.getElementById('carousel-modal');
const slides = modal.querySelectorAll('.carousel-slide');
let current=0;

btn.onclick=()=>{ modal.style.display='block'; showSlide(current); };

function showSlide(index){
  slides.forEach((slide,i)=>{
    slide.classList.toggle('active',i===index);
    if(i===2) slide.querySelector('button').onclick=()=>{ window.open('https://github.com/apps/dkonsult','_blank'); };
  });
}

document.getElementById('prev').onclick=()=>{ current=(current-1+slides.length)%slides.length; showSlide(current); };
document.getElementById('next').onclick=()=>{ current=(current+1)%slides.length; showSlide(current); };

modal.querySelector('.close-btn').onclick=()=>{ modal.style.display='none'; };
modal.onclick=e=>{ if(e.target===modal) modal.style.display='none'; };

function openIframe(url){
  const iframe = document.createElement('iframe');
  iframe.src=url;
  iframe.style.width='100%'; iframe.style.height='100%'; iframe.style.border='none';
  const content = modal.querySelector('.carousel-content');
  content.innerHTML=''; content.appendChild(iframe);
}

// Open external ads in new tab inside iframe (if same origin)
</script>


</!doctype>
  <h1>🚀 Debeatzgh GitHub Pages Product Showcase</h1> <a href="https://beatzde4.blogspot.com/p/blog-page_16.html" target="_blank">
  <img src="https://img.shields.io/badge/-PAGES%20DOCS-0A66C2?style=for-the-badge&logo=google-docs&logoColor=white">
  </a>
  <p>Explore premium, modern web pages built for creators, startups, and digital entrepreneurs.

  Click below to preview or order your own custom page.</p>
</header>

<section class="products-container">

  <!-- Homepage -->
  <div class="product-card">
    <div class="thumbnail">
      <img src="https://i.postimg.cc/nhyJpmYF/homepage-thumbnail.jpg" alt="Homepage Thumbnail">
    </div>
    <div class="product-content">
      <h3>🏠 Homepage</h3>
      <p>A visually appealing homepage perfect for creators or brands looking for an engaging first impression.</p>
      <div class="buttons">
        <a href="https://debeatzgh1.github.io/Home-/" class="btn btn-view" target="_self">View Page</a>
        <a href="https://docs.google.com/forms/d/e/1FAIpQLSec8llbmfgq_2cVxpdk0M9zi2BtNUT4_IjqFVkbM1RCApV3Gw/viewform?usp=header" class="btn btn-order" target="_self">Order Now</a>
      </div>
    </div>
  </div>

  <!-- Quizzes -->
  <div class="product-card">
    <div class="thumbnail">
      <img src="https://i.postimg.cc/vZfFh7qS/quiz-thumbnail.jpg" alt="Interactive Quizzes">
    </div>
    <div class="product-content">
      <h3>🧠 Interactive Knowledge Quizzes</h3>
      <p>Boost user engagement with auto-grading quizzes designed to educate and entertain your audience.</p>
      <div class="buttons">
        <a href="https://debeatzgh1.github.io/-Interactive-Knowledge-Quizzes/" class="btn btn-view" target="_self">View Page</a>
        <a href="https://docs.google.com/forms/d/e/1FAIpQLSec8llbmfgq_2cVxpdk0M9zi2BtNUT4_IjqFVkbM1RCApV3Gw/viewform?usp=header" class="btn btn-order" target="_self">Order Now</a>
      </div>
    </div>
  </div>

  <!-- Portfolio -->
  <div class="product-card">
    <div class="thumbnail">
      <img src="https://i.postimg.cc/SNHm0VJp/portfolio-thumbnail.jpg" alt="Portfolio Thumbnail">
    </div>
    <div class="product-content">
      <h3>💼 Personal Portfolio</h3>
      <p>Showcase your work, skills, and achievements in a sleek portfolio with smooth animations and responsive layout.</p>
      <div class="buttons">
        <a href="https://debeatzgh1.github.io/Personal-Portfolio-site-/" class="btn btn-view" target="_self">View Page</a>
        <a href="https://docs.google.com/forms/d/e/1FAIpQLSec8llbmfgq_2cVxpdk0M9zi2BtNUT4_IjqFVkbM1RCApV3Gw/viewform?usp=header" class="btn btn-order" target="_self">Order Now</a>
      </div>
    </div>
  </div>

  <!-- Shop -->
  <div class="product-card">
    <div class="thumbnail">
      <img src="https://i.postimg.cc/ht4kGh0C/shop-thumbnail.jpg" alt="Digital Shop Thumbnail">
    </div>
    <div class="product-content">
      <h3>🛍️ Digital Product Shop</h3>
      <p>Launch your digital storefront fast — ideal for selling templates, eBooks, music, or affiliate offers.</p>
      <div class="buttons">
        <a href="https://debeatzgh1.github.io/-My-Brand-Online-Digital-Products-Affiliate-Shop/" class="btn btn-view" target="_self">View Page</a>
        <a href="https://docs.google.com/forms/d/e/1FAIpQLSec8llbmfgq_2cVxpdk0M9zi2BtNUT4_IjqFVkbM1RCApV3Gw/viewform?usp=header" class="btn btn-order" target="_self">Order Now</a>
      </div>
    </div>
  </div>

  <!-- Newsletter Widget -->
  <div class="product-card">
    <div class="thumbnail">
      <img src="https://i.postimg.cc/tCZ9DHzS/newsletter-thumbnail.jpg" alt="Newsletter Widget Thumbnail">
    </div>
    <div class="product-content">
      <h3>📩 Newsletter Widget</h3>
      <p>Grow your email list fast using this stylish, animated sliding newsletter widget with smooth pulse effects.</p>
      <div class="buttons">
        <a href="https://debeatzgh1.github.io/Sliding-Newsletter-Signup-Widget-with-Pulse-Animation/" class="btn btn-view" target="_self">View Page</a>
        <a href="https://docs.google.com/forms/d/e/1FAIpQLSec8llbmfgq_2cVxpdk0M9zi2BtNUT4_IjqFVkbM1RCApV3Gw/viewform?usp=header" class="btn btn-order" target="_self">Order Now</a>
      </div>
    </div>
  </div>

  <!-- Tech & AI Hub -->
  <div class="product-card">
    <div class="thumbnail">
      <img src="https://i.postimg.cc/9FzFybWm/techai-thumbnail.jpg" alt="Tech & AI Hub Thumbnail">
    </div>
    <div class="product-content">
      <h3>🤖 Tech and AI Hub</h3>
      <p>Discover powerful AI tools and ideas for automation, content creation, and digital business growth.</p>
      <div class="buttons">
        <a href="https://debeatzgh1.github.io/Tech-and-AI-Hub-/" class="btn btn-view" target="_self">View Page</a>
        <a href="https://docs.google.com/forms/d/e/1FAIpQLSec8llbmfgq_2cVxpdk0M9zi2BtNUT4_IjqFVkbM1RCApV3Gw/viewform?usp=header" class="btn btn-order" target="_self">Order Now</a>
      </div>
    </div>
  </div>

  <!-- Blogger Theme -->
  <div class="product-card">
    <div class="thumbnail">
      <img src="https://i.postimg.cc/FKCH9kMw/blogger-theme-thumbnail.jpg" alt="Blogger Theme Thumbnail">
    </div>
    <div class="product-content">
      <h3>🎨 Blogger Theme</h3>
      <p>Customize your Blogger site with a dynamic, fast-loading theme including branding, logos, and post animations.</p>
      <div class="buttons">
        <a href="https://debeatzgh1.github.io/Custom-Blogger-Theme-for-with-Dynamic-Post-Loading-and-Logo-/" class="btn btn-view" target="_self">View Page</a>
        <a href="https://docs.google.com/forms/d/e/1FAIpQLSec8llbmfgq_2cVxpdk0M9zi2BtNUT4_IjqFVkbM1RCApV3Gw/viewform?usp=header" class="btn btn-order" target="_self">Order Now</a>
      </div>
    </div>
  </div>

</section>

<footer>
  © 2025 Debeatzgh — Crafted for digital creators, startups & innovators 🌐
</footer>
</body>
</html>
