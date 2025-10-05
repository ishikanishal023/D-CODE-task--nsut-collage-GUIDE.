<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>NSUT Campus Guide - Dark Theme</title>
<style>
  /* styles */
  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }

  body {
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    line-height: 1.6;
    background: #0d1117;
    color: #E0E1DD;
    overflow-x: hidden;
  }

  :root {
    --primary-color: #4E9CAF;
    --accent-color: #F4A261;
    --highlight-color: #9AE3D4;
    --background-card: #1f2c36;
    --text-light: #E0E1DD;
  }

  /* Animated background gradient */
  .animated-background {
    position: fixed; inset: 0;
    background: linear-gradient(270deg, #0d1117, #1f2c36, #0d1117);
    background-size: 600% 600%;
    animation: gradientShift 30s ease infinite;
    z-index: -1;
  }
  @keyframes gradientShift {
    0% { background-position: 0% 50%; }
    50% { background-position: 100% 50%; }
    100% { background-position: 0% 50%; }
  }

  /* Nav bar */
  nav {
    position: sticky;
    top: 0;
    background: rgba(13, 17, 23, 0.95);
    backdrop-filter: blur(8px);
    padding: 1rem 2rem;
    display: flex;
    justify-content: center;
    flex-wrap: wrap;
    box-shadow: 0 4px 12px rgba(0, 0, 0, 0.3);
    z-index: 999;
  }
  nav ul {
    list-style: none;
    display: flex;
    flex-wrap: wrap;
    gap: 1.5rem;
  }
  nav a {
    color: var(--text-light);
    text-decoration: none;
    font-weight: 600;
    padding: 0.5rem 1rem;
    border-radius: 20px;
    transition: background 0.3s, transform 0.2s;
    cursor: pointer;
  }
  nav a:hover {
    background-color: var(--highlight-color);
    color: #fff;
    transform: translateY(-2px);
  }

  /* Hero section */
  .hero {
    position: relative;
    padding: 6rem 2rem;
    text-align: center;
  }
  .hero h1 {
    font-size: 3rem;
    color: var(--highlight-color);
    margin-bottom: 1rem;
    animation: pulseText 2s infinite alternate;
  }
  @keyframes pulseText {
    0% { text-shadow: 0 0 8px rgba(78, 158, 172, 0.7); }
    100% { text-shadow: 0 0 16px rgba(78, 158, 172, 1); }
  }
  .hero p {
    max-width: 700px;
    margin: 0 auto 2rem;
    font-size: 1.2rem;
    color: #ccc;
    line-height: 1.6;
  }
  .hero-badge {
    display: inline-block;
    background-color: #F4A261;
    padding: 0.6rem 1.5rem;
    border-radius: 25px;
    font-weight: 600;
    color: #fff;
    font-size: 1rem;
    box-shadow: 0 4px 12px rgba(78, 158, 172, 0.3);
    animation: bounceBadge 2s infinite;
  }
  @keyframes bounceBadge {
    0%, 100% { transform: translateY(0); }
    50% { transform: translateY(-5px); }
  }
  /* Scroll indicator */
  .scroll-indicator {
    margin: 2rem auto;
    width: 30px; height: 50px;
    border: 3px solid #ccc;
    border-radius: 15px;
    position: relative;
    animation: bounce 2s infinite;
  }
  .scroll-indicator::after {
    content: "";
    position: absolute;
    top: 10px; left: 50%;
    width: 6px; height: 6px;
    background-color: #ccc;
    border-radius: 50%;
    transform: translateX(-50%);
    animation: moveDot 2s ease-in-out infinite;
  }
  @keyframes moveDot {
    0% { top: 10px; opacity: 1; }
    50% { top: 30px; opacity: 0.5; }
    100% { top: 10px; opacity: 1; }
  }
  @keyframes bounce {
    0%, 100% { transform: translateY(0); }
    50% { transform: translateY(-10px); }
  }

  /* Container styles */
  .container {
    max-width: 1200px;
    margin: -50px auto 4rem; /* Adjusted for overlap with hero */
    padding: 3rem 2rem;
    background-color: var(--background-card);
    border-radius: 15px;
    box-shadow: 0 8px 20px rgba(0, 0, 0, 0.3);
    animation: fadeInUp 1s ease forwards;
  }
  @keyframes fadeInUp {
    from { opacity: 0; transform: translateY(20px); }
    to { opacity: 1; transform: translateY(0); }
  }
  /* Section titles */
  .section-title {
    font-size: 2.5rem;
    text-align: center;
    margin-bottom: 1rem;
    background: linear-gradient(135deg, #4E9CAF, #F4A261);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    font-weight: bold;
    text-shadow: 0 2px 4px rgba(0, 0, 0, 0.3);
    animation: slideIn 1s ease forwards;
  }
  @keyframes slideIn {
    from { opacity: 0; transform: translateX(-50px); }
    to { opacity: 1; transform: translateX(0); }
  }
  .section-subtitle {
    text-align: center;
    color: #bbb;
    font-size: 1.1rem;
    margin-bottom: 3rem;
  }

  /* Grid for campus hangouts and events */
  .places-grid {
    display: grid;
    gap: 1.5rem;
    grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
  }

  /* boxes under campus hangout and events styling */
  .place-card {
    background-color: #2c3e50;
    border-radius: 15px;
    overflow: hidden;
    box-shadow: 0 4px 15px rgba(0,0,0,0.2);
    cursor: pointer;
    display: flex;
    flex-direction: column;
    transition: transform 0.3s, box-shadow 0.3s;
    height: 250px; /* uniform height */
  }
  .place-card:hover {
    transform: translateY(-5px);
    box-shadow: 0 8px 20px rgba(0,0,0,0.3);
  }

  .place-image {
    background: linear-gradient(135deg, #2c3e50, #4ca1af);
    height: 140px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 3rem;
    color: #fff;
    position: relative;
  }
  /*  background change */
  .place-image:hover {
    background: linear-gradient(135deg, #4ca1af, #2c3e50);
  }
 

  .place-content {
    padding: 1rem;
    flex: 1;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
  }

  .place-tag {
    display: inline-block;
    background-color: var(--highlight-color);
    padding: 0.4rem 1rem;
    border-radius: 20px;
    font-size: 0.75rem;
    font-weight: 600;
    color: #fff;
    margin-bottom: 0.8rem;
    align-self: flex-start;
    animation: pulse 2s infinite alternate;
  }
  @keyframes pulse {
    0% { background-color: var(--highlight-color); }
    100% { background-color: #fff; color: #000; }
  }

  /* Title hover underline effect */
  .place-content h3 {
    font-size: 1.4rem;
    margin-bottom: 0.5rem;
    color: #f0f0f0;
    position: relative;
    cursor: pointer;
  }
  .place-content h3::after {
    content: "";
    position: absolute;
    width: 0;
    height: 2px;
    bottom: -2px;
    left: 0;
    background: linear-gradient(90deg, #4E9CAF, #F4A261);
    transition: width 0.4s;
  }
  .place-content h3:hover::after {
    width: 100%;
  }

  /* Stats section with animated background */
  .stats-section {
    margin-top: 4rem;
    display: grid;
    gap: 1.5rem;
    grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
    padding: 2rem;
    background-color: var(--background-card);
    border-radius: 15px;
    position: relative;
  }
  .stats-section::before {
    content: "";
    position: absolute;
    inset: -50px;
    width: 150px;
    height: 150px;
    background: radial-gradient(circle, rgba(78, 158, 172, 0.1), transparent);
    border-radius: 50%;
    animation: orbMove 15s ease-in-out infinite;
    z-index: -1;
  }
  @keyframes orbMove {
    0% { transform: translate(0,0); }
    50% { transform: translate(50px, -50px); }
    100% { transform: translate(0,0); }
  }
  .stat-card {
    background-color: #2c3e50;
    padding: 1rem;
    border-radius: 12px;
    text-align: center;
    box-shadow: 0 4px 15px rgba(0,0,0,0.2);
    transition: transform 0.3s, box-shadow 0.3s;
  }
  .stat-card:hover {
    transform: translateY(-5px);
    box-shadow: 0 8px 20px rgba(0,0,0,0.3);
  }
  .stat-number {
    font-size: 2rem;
    font-weight: bold;
    background: linear-gradient(135deg, #4E9CAF, #F4A261);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
  }
  .stat-label {
    margin-top: 0.5rem;
    font-size: 1rem;
    color: #bbb;
  }

  /* Footer styles */
  footer {
    background-color: #111;
    padding: 4rem 2rem;
    text-align: center;
    position: relative;
    overflow: hidden; /* To prevent extra space from unwanted elements */
  }
  footer::before {
    content: "";
    position: absolute;
    inset: -50%;
    width: 200%;
    height: 200%;
    background: radial-gradient(circle, rgba(78, 158, 172, 0.05), transparent);
    animation: moveBackground 25s linear infinite;
    z-index: -1;
  }
  .footer-content {
    position: relative;
    z-index: 1;
  }
  footer p {
    color: #ccc;
    margin: 0.5rem 0;
  }
  .social-links {
    margin-top: 1.5rem;
    display: flex;
    justify-content: center;
    gap: 1.5rem;
  }
  .social-icon {
    width: 50px; height: 50px;
    background-color: rgba(78, 158, 172, 0.2);
    display: flex;
    align-items: center;
    justify-content: center;
    border-radius: 50%;
    font-size: 1.5rem;
    color: #f0f0f0;
    cursor: pointer;
    transition: all 0.3s;
  }
  .social-icon:hover {
    background-color: var(--highlight-color);
    transform: translateY(-5px) scale(1.1);
  }

  /* Loader for initial load */
  .loading-overlay {
    position: fixed;
    inset: 0;
    background-color: #0d1117;
    display: flex;
    align-items: center;
    justify-content: center;
    z-index: 9999;
  }
  .loader {
    border: 6px solid #ccc;
    border-top: 6px solid var(--primary-color);
    border-radius: 50%;
    width: 50px; height: 50px;
    animation: spin 1s linear infinite;
  }
  @keyframes spin {
    0% { transform: rotate(0deg);}
    100% { transform: rotate(360deg);}
  }

  /* Responsive adjustments */
  @media(max-width: 768px) {
    body { font-size: 14px; }
    .hero h1 { font-size: 2rem; }
  }
</style>
</head>
<body>

<!-- Loading overlay -->
<div class="loading-overlay" id="loadingOverlay">
  <div class="loader"></div>
</div>

<!-- Background animated gradient -->
<div class="animated-background"></div>

<!-- Navigation Bar with Event -->
<nav>
  <ul>
    <li><a href="#home">🏠 Home</a></li>
    <li><a href="#places">⛳ Top Spots</a></li>
    <li><a href="#events">🎉 Events</a></li>
    <li><a href="#stats">📚 Campus Stats</a></li>
    <li><a href="#contact">☎️ Contact</a></li>
  </ul>
</nav>

<!-- Hero Section -->
<div class="hero" id="home">
  <h1> NSUT CAMPUS GUIDE </h1>
  <p> Your complete guide to explore NSUT campus,hangout spots. Whether you are here for studies or fun with friends, this guide helps you navigate and enjoy every moment!!!</p>
  <div class="hero-badge"><a href="https://maps.app.goo.gl/s27e3ukNzF3mfc1h7" style="text-decoration:none; color:white;"> DWARKA, SOUTH-WEST DELHI </a></div>
</div>

<!-- Main Content -->
<div class="container">

  <!-- Campus Hangouts -->
  <h2 class="section-title" id="places">Campus Hangouts</h2>
  <p class="section-subtitle">Places in campus where you can study and chill with your friends</p>
  <div class="places-grid">
    <!-- box for canteen and SC -->
    <div class="place-card" onclick="window.open('https://maps.app.goo.gl/BMSwzd8igtRbFp548','_blank')">
      <div class="place-image">🍽️</div>
      <div class="place-content">
        <div class="place-tag">Food, Chill & Study</div>
        <h3>Canteen & SC</h3>
        <p>“If you want cheap food, free Wi-Fi, AC, and a side of nonstop noise – welcome to our canteen</p>
      </div>
    </div>
    <!-- box for safal and mother dairy -->
    <div class="place-card" onclick="window.open('https://maps.app.goo.gl/pwAt4BU9vzPvCEgs9','_blank')">
      <div class="place-image">🍞</div>
      <div class="place-content">
        <div class="place-tag">Dairy & Essentials</div>
        <h3>Safal & Mother Dairy</h3>
        <p>Fresh dairy products and daily essentials. The only survival for Hostelers </p>
      </div>
    </div>
    <!-- box for nescafé -->
    <div class="place-card" onclick="window.open('https://maps.app.goo.gl/r2cE92jRpcYNLxuk9','_blank')">
      <div class="place-image">☕</div>
      <div class="place-content">
        <div class="place-tag">Coffee Spot</div>
        <h3>Nescafé</h3>
        <p>Popular for expensive coffee, badiya watermelon ice tea, and instant maggie.</p>
      </div>
    </div>
    <!-- box for nescii lawn -->
    <div class="place-card" onclick="window.open('https://maps.app.goo.gl/SH9TCJZT4Hy1Zd3x7','_blank')">
      <div class="place-image">🌿</div>
      <div class="place-content">
        <div class="place-tag">Lawn & Relax</div>
        <h3>Nescii Lawn</h3>
        <p>Perfect for outdoor gatherings and relaxing near Admin block.</p>
      </div>
    <!-- box for music room -->
    </div>
    <div class="place-card" onclick="window.open('https://maps.app.goo.gl/i32AkhXq52sBFfFj9','_blank')">
      <div class="place-image">🎶</div>
      <div class="place-content">
        <div class="place-tag">Music & Arts</div>
        <h3>Music Room</h3>
        <p>Practice, jam sessions, and music events.</p>
      </div>
    </div>
    <!-- box for NSUT Front Lawns -->
    <div class="place-card" onclick="window.open('https://maps.app.goo.gl/sXVwQEZ8hx6sLeA27', '_blank')">
      <div class="place-image">🌳</div>
      <div class="place-content">
        <div class="place-tag">Nature & Recreation</div>
        <h3>NSUT Front Lawns</h3>
        <p>Outdoor space for leisure and fun.</p>
      </div>
    </div>
    <!-- box for sports complex -->
    <div class="place-card" onclick="window.open('https://maps.app.goo.gl/j9gTeAQsGH5d4WNL9','_blank')">
      <div class="place-image">🤸️ </div>
      <div class="place-content">
        <div class="place-tag">Sports & Fitness</div>
        <h3>Sports Complex</h3>
        <p>Cricket, vollyball, football ground and basketball area.Moreover a peaceful area to chill and relax.</p>
      </div>
    </div>
    <!-- box for nsut lake -->
    <div class="place-card" onclick="window.open('https://maps.app.goo.gl/FQ3gwMw3Us69BJM89','_blank')">
      <div class="place-image">🏞️</div>
      <div class="place-content">
        <div class="place-tag">Nature & Peace</div>
        <h3>NSUT Lake</h3>
        <p>Restrickted area but jugad krke ja sakte ho.</p>
      </div>
    </div>
  </div>

  <!-- Campus Events -->
  <h2 class="section-title" id="events" style="margin-top:4rem;">Campus Events</h2>
  <p class="section-subtitle">Join the buzz! Upcoming events in MAIN CAMPUS:</p>
  <div class="places-grid">
    <!-- Event: Resonance -->
    <div class="place-card" onclick="window.open('https://www.instagram.com/resonanznsut?utm_source=ig_web_button_share_sheet&igsh=ZDNlZDc0MzIxNw==','_blank')">
      <div class="place-image">🎤</div>
      <div class="place-content">
        <div class="place-tag">only for NSUT students</div>
        <h3>Resonance</h3>
        <p>Annual cultural fest with concerts, competitions, and more.</p>
      </div>
    </div>
    <!-- Event: Innovision -->
    <div class="place-card" onclick="window.open('https://www.instagram.com/innovisionnsut?utm_source=ig_web_button_share_sheet&igsh=ZDNlZDc0MzIxNw==','_blank')">
      <div class="place-image">💡</div>
      <div class="place-content">
        <div class="place-tag">tech fest of NSUT</div>
        <h3>Innovision</h3>
        <p>Tech and innovation hackathon with industry experts.</p>
         </div>
    </div>
    
    <!-- Event: Moksha -->
    <div class="place-card" onclick="window.open('https://www.instagram.com/mokshansut?utm_source=ig_web_button_share_sheet&igsh=ZDNlZDc0MzIxNw==','_blank')">
    <div class="place-image">🎶</div>
      <div class="place-content">
        <div class="place-tag">Largest fest</div>
        <h3>Moksha</h3>
        <p>Music and arts festival showcasing student talent.</p>
      </div>
    </div>
    <!-- More events -->
  </div>

  <!-- Campus Stats -->
  <h2 class="section-title" id="stats" style="margin-top:4rem;">Campus Status</h2>
  <div class="stats-section">
    <div class="stat-card">
      <div class="stat-number">145</div>
      <div class="stat-label">Area - Acres</div>
    </div>
    <div class="stat-card">
      <div class="stat-number">DWARKA SOUTH-WEST DELHI</div>
      <div class="stat-label">Location</div>
    </div>
    <div class="stat-card">
      <div class="stat-number">7220+</div>
      <div class="stat-label">Students</div>
    </div>
    <div class="stat-card">
      <div class="stat-number">32+</div>
      <div class="stat-label">Societies</div>
    </div>
  </div>

</div>

<!-- Contact -->
<div id="contact" style="padding:4rem 2rem; background-color:#111; text-align:center;">
  <h2 style="color:#F4A261;">Contact Us</h2>
  <p style="color:#ccc;">Email: info@nsut.ac.in | Phone: +91 01125000268 </p>
</div>

<!-- Footer -->
<footer>
  <div class="footer-content">
    <p style="font-size:1.3rem;">💙 Made with Love for NSUT Community</p>
    <p>Netaji Subhas University of Technology</p>
    <p>Sector 3, Dwarka, New Delhi - 110078</p>
    <p style="margin-top:1rem;">📧 info@nsut.ac.in | 📞 +91-11-25099022</p>
    <div class="social-links" style="margin-top:1.5rem;">
      <div class="social-icon" onclick="window.open('https://www.instagram.com/nsut.official?utm_source=ig_web_button_share_sheet&igsh=ZDNlZDc0MzIxNw==','_blank')">📱</div>
      <div class="social-icon" onclick="window.open('https://nsut.ac.in/,_blank')">🌐</div>
      <div class="social-icon" oneclick="window.open('https://nsut.ac.in/en/about-campus','_blank')">🏫	</div></div>
    <p style="margin-top:2rem; opacity:0.7;">Lets go! NSUT campus guide. Keep Exploring! 🚀</p>
  </div>
</footer>

<!-- Scripts for loader -->
<script>
  // Hide loader after load
  window.addEventListener('load', () => {
    document.getElementById('loadingOverlay').style.display = 'none';
  });
</script>
</body>
</html>
