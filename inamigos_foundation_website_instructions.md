# 🌟 InAmigos Foundation — Awareness Website: Development Instructions

> **Purpose:** A richly animated, visually bold awareness webpage for **InAmigos Foundation** — a Section 8 non-profit NGO based in Chhattisgarh, India. Built with pure **HTML & CSS** (with vanilla JS for interactivity), this page should feel alive: vibrant, compassionate, and community-driven.

---

## 📁 File Structure

```
inamigos-awareness/
│
├── index.html          ← Main webpage (single-page)
├── style.css           ← All styles, animations, scroll effects
├── assets/
│   ├── images/         ← Downloaded/placeholder images
│   └── icons/          ← SVG icons or Font Awesome
└── README.md
```

---

## 🎨 Design Direction & Aesthetic

### Theme: **"Warm Earth + Vibrant Humanity"**

| Property | Value |
|---|---|
| **Primary Color** | `#E85D26` (Burnt Orange — energy, compassion) |
| **Secondary Color** | `#2C6E49` (Forest Green — nature, growth) |
| **Accent Color** | `#F9C74F` (Sunflower Yellow — hope, warmth) |
| **Dark Base** | `#1A1A2E` (Deep Navy — contrast, trust) |
| **Light BG** | `#FFF8F0` (Warm Cream — softness) |
| **Text Dark** | `#2B2B2B` |
| **Text Light** | `#FFFFFF` |

### Fonts (Google Fonts)

```html
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@700;900&family=Nunito:wght@400;600;800&display=swap" rel="stylesheet">
```

- **Display / Headings:** `Playfair Display` — editorial, dignified
- **Body / UI:** `Nunito` — friendly, readable, human

### CSS Variables (define in `:root`)

```css
:root {
  --orange:    #E85D26;
  --green:     #2C6E49;
  --yellow:    #F9C74F;
  --navy:      #1A1A2E;
  --cream:     #FFF8F0;
  --white:     #FFFFFF;
  --text-dark: #2B2B2B;

  --shadow-soft: 0 8px 32px rgba(232, 93, 38, 0.15);
  --shadow-card: 0 4px 20px rgba(0,0,0,0.12);
  --radius-lg:   20px;
  --radius-pill: 50px;

  --transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
}
```

---

## 🏗️ Page Sections (in order)

1. [Sticky Navigation Bar](#1-sticky-navigation-bar)
2. [Hero Section — Full-Screen Banner](#2-hero-section)
3. [About InAmigos Foundation](#3-about-section)
4. [Stats Counter Strip](#4-stats-counter-strip)
5. [Our Projects — Horizontal Scroll Cards](#5-projects-horizontal-scroll)
6. [Social Impact — Alternating Layout](#6-social-impact-section)
7. [Gallery — Masonry/Grid with Hover Zoom](#7-gallery-section)
8. [Events Timeline](#8-events-timeline)
9. [Testimonials / Volunteer Voices](#9-testimonials)
10. [Call-to-Action — Full-Width Band](#10-call-to-action)
11. [Footer](#11-footer)

---

## 1. Sticky Navigation Bar

### HTML

```html
<nav class="navbar" id="navbar">
  <div class="nav-container">
    <a href="#" class="nav-logo">
      <img src="https://inamigosfoundation.org.in/public/storage/settings/174421468011.jpg"
           alt="InAmigos Foundation Logo" class="logo-img">
      <span class="logo-text">InAmigos Foundation</span>
    </a>
    <button class="hamburger" id="hamburger" aria-label="Toggle menu">
      <span></span><span></span><span></span>
    </button>
    <ul class="nav-links" id="navLinks">
      <li><a href="#about">About</a></li>
      <li><a href="#projects">Projects</a></li>
      <li><a href="#impact">Impact</a></li>
      <li><a href="#gallery">Gallery</a></li>
      <li><a href="#events">Events</a></li>
      <li><a href="#cta" class="nav-donate-btn">Donate ❤️</a></li>
    </ul>
  </div>
</nav>
```

### CSS

```css
.navbar {
  position: fixed;
  top: 0; left: 0; right: 0;
  z-index: 1000;
  background: rgba(255, 248, 240, 0.95);
  backdrop-filter: blur(12px);
  -webkit-backdrop-filter: blur(12px);
  border-bottom: 2px solid transparent;
  transition: var(--transition);
  padding: 0.8rem 0;
}

.navbar.scrolled {
  border-bottom-color: var(--orange);
  box-shadow: 0 4px 24px rgba(232,93,38,0.12);
}

.nav-container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 2rem;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.nav-logo {
  display: flex;
  align-items: center;
  gap: 0.75rem;
  text-decoration: none;
}

.logo-img {
  height: 48px;
  width: 48px;
  border-radius: 50%;
  object-fit: cover;
  border: 2px solid var(--orange);
}

.logo-text {
  font-family: 'Playfair Display', serif;
  font-weight: 700;
  font-size: 1.15rem;
  color: var(--orange);
}

.nav-links {
  list-style: none;
  display: flex;
  align-items: center;
  gap: 2rem;
  margin: 0; padding: 0;
}

.nav-links a {
  text-decoration: none;
  font-family: 'Nunito', sans-serif;
  font-weight: 600;
  color: var(--text-dark);
  position: relative;
  padding-bottom: 4px;
  transition: color 0.3s;
}

.nav-links a::after {
  content: '';
  position: absolute;
  bottom: 0; left: 0;
  width: 0; height: 2px;
  background: var(--orange);
  transition: width 0.35s ease;
}

.nav-links a:hover { color: var(--orange); }
.nav-links a:hover::after { width: 100%; }

.nav-donate-btn {
  background: var(--orange) !important;
  color: var(--white) !important;
  padding: 0.5rem 1.4rem !important;
  border-radius: var(--radius-pill);
  font-weight: 800 !important;
  box-shadow: 0 4px 16px rgba(232,93,38,0.35);
  transition: var(--transition) !important;
}

.nav-donate-btn:hover {
  background: #c84d18 !important;
  transform: translateY(-2px);
  box-shadow: 0 8px 24px rgba(232,93,38,0.4) !important;
}

.nav-donate-btn::after { display: none !important; }

/* Hamburger */
.hamburger {
  display: none;
  flex-direction: column;
  gap: 5px;
  background: none;
  border: none;
  cursor: pointer;
  padding: 4px;
}
.hamburger span {
  display: block;
  width: 26px;
  height: 3px;
  background: var(--orange);
  border-radius: 2px;
  transition: var(--transition);
}

@media (max-width: 768px) {
  .hamburger { display: flex; }
  .nav-links {
    position: fixed;
    top: 70px; left: 0; right: 0;
    background: var(--cream);
    flex-direction: column;
    padding: 2rem;
    gap: 1.5rem;
    transform: translateX(-100%);
    transition: transform 0.4s ease;
    box-shadow: 4px 0 20px rgba(0,0,0,0.1);
  }
  .nav-links.open { transform: translateX(0); }
}
```

### JavaScript (add at bottom of `index.html` in `<script>`)

```js
// Sticky navbar shadow
window.addEventListener('scroll', () => {
  document.getElementById('navbar')
    .classList.toggle('scrolled', window.scrollY > 50);
});

// Mobile menu toggle
document.getElementById('hamburger').addEventListener('click', () => {
  document.getElementById('navLinks').classList.toggle('open');
});
```

---

## 2. Hero Section

### HTML

```html
<section class="hero" id="hero">
  <!-- Animated background particles -->
  <div class="hero-particles">
    <div class="particle"></div>
    <div class="particle"></div>
    <div class="particle"></div>
    <div class="particle"></div>
    <div class="particle"></div>
    <div class="particle"></div>
  </div>

  <div class="hero-content">
    <div class="hero-badge">🌱 #InAmigos | Making India Better</div>
    <h1 class="hero-title">
      <span class="line-reveal">Together,</span>
      <span class="line-reveal delay-1">We Build</span>
      <span class="line-reveal delay-2 highlight-word">Brighter Futures</span>
    </h1>
    <p class="hero-subtitle">
      InAmigos Foundation — a Section 8 certified non-profit empowering communities
      across India through education, food, women's rights, animal welfare, and
      environmental sustainability.
    </p>
    <div class="hero-cta-group">
      <!-- 🔗 PLACEHOLDER: Replace # with your actual links -->
      <a href="#" class="btn btn-primary pulse-btn">❤️ Donate Now</a>
      <a href="#" class="btn btn-outline">🤝 Volunteer With Us</a>
    </div>
    <div class="hero-scroll-hint">
      <span>Scroll to explore</span>
      <div class="scroll-arrow"></div>
    </div>
  </div>

  <div class="hero-visual">
    <!-- Uses a gradient overlay on a meaningful image -->
    <img
      src="https://inamigosfoundation.org.in/public/storage/gallery/1743051485.jpg"
      alt="InAmigos Foundation volunteers in action"
      class="hero-img">
    <div class="hero-img-overlay"></div>
  </div>
</section>
```

### CSS

```css
.hero {
  min-height: 100vh;
  display: grid;
  grid-template-columns: 1fr 1fr;
  align-items: center;
  background: var(--navy);
  padding: 7rem 4rem 4rem;
  position: relative;
  overflow: hidden;
  gap: 3rem;
}

/* Animated background blobs */
.hero::before {
  content: '';
  position: absolute;
  top: -20%;
  left: -10%;
  width: 600px;
  height: 600px;
  background: radial-gradient(circle, rgba(232,93,38,0.2) 0%, transparent 70%);
  animation: blobFloat 8s ease-in-out infinite alternate;
  pointer-events: none;
}
.hero::after {
  content: '';
  position: absolute;
  bottom: -20%;
  right: -5%;
  width: 500px;
  height: 500px;
  background: radial-gradient(circle, rgba(44,110,73,0.25) 0%, transparent 70%);
  animation: blobFloat 10s ease-in-out infinite alternate-reverse;
  pointer-events: none;
}

@keyframes blobFloat {
  0%   { transform: translate(0, 0) scale(1); }
  100% { transform: translate(40px, -40px) scale(1.1); }
}

/* Floating particles */
.hero-particles { position: absolute; inset: 0; pointer-events: none; }
.particle {
  position: absolute;
  border-radius: 50%;
  opacity: 0.4;
  animation: particleDrift linear infinite;
}
.particle:nth-child(1) { width:12px; height:12px; background:var(--orange); top:20%; left:15%; animation-duration:12s; }
.particle:nth-child(2) { width:8px; height:8px; background:var(--yellow); top:60%; left:5%; animation-duration:9s; animation-delay:1s; }
.particle:nth-child(3) { width:16px; height:16px; background:var(--green); top:80%; left:25%; animation-duration:14s; animation-delay:2s; }
.particle:nth-child(4) { width:10px; height:10px; background:var(--orange); top:30%; right:20%; animation-duration:11s; animation-delay:0.5s; }
.particle:nth-child(5) { width:14px; height:14px; background:var(--yellow); top:70%; right:10%; animation-duration:10s; animation-delay:3s; }
.particle:nth-child(6) { width:6px; height:6px; background:var(--green); top:10%; right:35%; animation-duration:8s; animation-delay:1.5s; }

@keyframes particleDrift {
  0%   { transform: translateY(0) rotate(0deg); }
  100% { transform: translateY(-80px) rotate(360deg); }
}

/* Hero Content */
.hero-content { position: relative; z-index: 2; }

.hero-badge {
  display: inline-block;
  background: rgba(249,199,79,0.15);
  color: var(--yellow);
  border: 1px solid rgba(249,199,79,0.4);
  padding: 0.4rem 1.2rem;
  border-radius: var(--radius-pill);
  font-family: 'Nunito', sans-serif;
  font-size: 0.85rem;
  font-weight: 700;
  letter-spacing: 0.05em;
  margin-bottom: 1.5rem;
  animation: fadeSlideUp 0.8s ease both;
}

.hero-title {
  font-family: 'Playfair Display', serif;
  font-size: clamp(2.8rem, 5vw, 4.2rem);
  font-weight: 900;
  color: var(--white);
  line-height: 1.15;
  margin-bottom: 1.5rem;
  display: flex;
  flex-direction: column;
}

.line-reveal {
  display: block;
  animation: fadeSlideUp 0.9s ease both;
}
.delay-1 { animation-delay: 0.2s; }
.delay-2 { animation-delay: 0.4s; }

.highlight-word {
  color: var(--orange);
  -webkit-text-stroke: 1px var(--orange);
}

@keyframes fadeSlideUp {
  from { opacity: 0; transform: translateY(30px); }
  to   { opacity: 1; transform: translateY(0); }
}

.hero-subtitle {
  font-family: 'Nunito', sans-serif;
  color: rgba(255,255,255,0.75);
  font-size: 1.1rem;
  line-height: 1.7;
  max-width: 520px;
  margin-bottom: 2.5rem;
  animation: fadeSlideUp 1s ease 0.5s both;
}

/* CTA Buttons */
.hero-cta-group {
  display: flex;
  gap: 1rem;
  flex-wrap: wrap;
  animation: fadeSlideUp 1s ease 0.7s both;
}

.btn {
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  padding: 0.9rem 2rem;
  border-radius: var(--radius-pill);
  font-family: 'Nunito', sans-serif;
  font-weight: 800;
  font-size: 1rem;
  text-decoration: none;
  cursor: pointer;
  transition: var(--transition);
  position: relative;
  overflow: hidden;
}

.btn-primary {
  background: var(--orange);
  color: var(--white);
  box-shadow: 0 6px 24px rgba(232,93,38,0.45);
}
.btn-primary:hover {
  background: #c84d18;
  transform: translateY(-3px);
  box-shadow: 0 12px 32px rgba(232,93,38,0.5);
}

.btn-outline {
  background: transparent;
  color: var(--white);
  border: 2px solid rgba(255,255,255,0.5);
}
.btn-outline:hover {
  background: rgba(255,255,255,0.1);
  border-color: var(--white);
  transform: translateY(-3px);
}

/* Pulse animation for primary CTA */
.pulse-btn::after {
  content: '';
  position: absolute;
  inset: 0;
  border-radius: var(--radius-pill);
  background: var(--orange);
  animation: pulse-ring 2.5s ease-out infinite;
  z-index: -1;
}
@keyframes pulse-ring {
  0%   { transform: scale(1); opacity: 0.7; }
  100% { transform: scale(1.5); opacity: 0; }
}

/* Scroll hint */
.hero-scroll-hint {
  display: flex;
  align-items: center;
  gap: 0.75rem;
  margin-top: 3rem;
  color: rgba(255,255,255,0.45);
  font-family: 'Nunito', sans-serif;
  font-size: 0.85rem;
  animation: fadeSlideUp 1s ease 1s both;
}
.scroll-arrow {
  width: 20px;
  height: 20px;
  border-right: 2px solid rgba(255,255,255,0.4);
  border-bottom: 2px solid rgba(255,255,255,0.4);
  transform: rotate(45deg);
  animation: arrowBounce 1.5s ease-in-out infinite;
}
@keyframes arrowBounce {
  0%, 100% { transform: rotate(45deg) translateY(0); }
  50%       { transform: rotate(45deg) translateY(6px); }
}

/* Hero Image Panel */
.hero-visual {
  position: relative;
  height: 520px;
  border-radius: 24px;
  overflow: hidden;
  animation: fadeSlideUp 1s ease 0.3s both;
}

.hero-img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 6s ease;
}
.hero-visual:hover .hero-img {
  transform: scale(1.06);
}

.hero-img-overlay {
  position: absolute;
  inset: 0;
  background: linear-gradient(
    135deg,
    rgba(232,93,38,0.3) 0%,
    rgba(44,110,73,0.25) 100%
  );
}

/* Responsive */
@media (max-width: 900px) {
  .hero {
    grid-template-columns: 1fr;
    padding: 6rem 2rem 3rem;
    text-align: center;
  }
  .hero-visual { height: 300px; }
  .hero-subtitle { margin: 0 auto 2rem; }
  .hero-cta-group { justify-content: center; }
  .hero-scroll-hint { justify-content: center; }
}
```

---

## 3. About Section

### HTML

```html
<section class="about-section" id="about">
  <div class="container">
    <div class="section-label">🏛️ Who We Are</div>
    <div class="about-grid">
      <div class="about-text fade-in-left">
        <h2 class="section-title">InAmigos Foundation</h2>
        <p class="about-lead">
          Founded on <strong>September 23, 2020</strong> by
          <strong>Mr. Govind Shukla (Founder & CEO)</strong>, InAmigos Foundation
          is a <strong>Section 8 registered non-profit organization</strong>
          licensed by the Central Government — committed to creating
          lasting social impact across India.
        </p>
        <p class="about-body">
          Based in Chhattisgarh, we operate through a strong network of dedicated
          professionals and volunteers spanning <strong>28 states</strong>.
          Our operations are backed by <strong>80G & 12A certifications</strong>,
          ensuring transparency, accountability, and tax-exempt benefits for donors.
          We are also <strong>CSR-1 registered</strong>,
          <strong>NITI Aayog registered</strong>, and hold the prestigious
          <strong>IAF ISO 9001:2015 certification</strong>.
        </p>
        <div class="about-tags">
          <span class="tag">🏛️ Section 8 Registered</span>
          <span class="tag">📋 NITI Aayog</span>
          <span class="tag">💰 80G & 12A Certified</span>
          <span class="tag">🤝 CSR-1 Registered</span>
          <span class="tag">✅ ISO 9001:2015</span>
        </div>
        <!-- 🔗 PLACEHOLDER: Replace # with actual About Us page link -->
        <a href="#" class="btn btn-secondary mt-2">Learn More About Us →</a>
      </div>

      <div class="about-image-stack fade-in-right">
        <img src="https://inamigosfoundation.org.in/public/storage/gallery/1743051466.jpg"
             alt="InAmigos Foundation team" class="stack-img stack-back">
        <img src="https://inamigosfoundation.org.in/public/storage/gallery/1743051438.jpg"
             alt="InAmigos Foundation volunteers" class="stack-img stack-front">
        <div class="stack-badge">
          <div class="badge-number">50,000+</div>
          <div class="badge-label">Beneficiaries Reached</div>
        </div>
      </div>
    </div>
  </div>
</section>
```

### CSS

```css
.about-section {
  background: var(--cream);
  padding: 7rem 2rem;
  position: relative;
  overflow: hidden;
}

.about-section::before {
  content: '';
  position: absolute;
  top: -100px; right: -100px;
  width: 400px; height: 400px;
  background: radial-gradient(circle, rgba(232,93,38,0.07), transparent 70%);
  pointer-events: none;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
}

.section-label {
  font-family: 'Nunito', sans-serif;
  font-size: 0.85rem;
  font-weight: 800;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  color: var(--orange);
  margin-bottom: 0.75rem;
}

.section-title {
  font-family: 'Playfair Display', serif;
  font-size: clamp(2rem, 4vw, 3.2rem);
  font-weight: 900;
  color: var(--navy);
  line-height: 1.2;
  margin-bottom: 1.5rem;
}

.about-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 5rem;
  align-items: center;
  margin-top: 2rem;
}

.about-lead {
  font-family: 'Nunito', sans-serif;
  font-size: 1.15rem;
  line-height: 1.7;
  color: var(--text-dark);
  margin-bottom: 1.25rem;
}

.about-body {
  font-family: 'Nunito', sans-serif;
  font-size: 1rem;
  line-height: 1.75;
  color: #555;
  margin-bottom: 1.5rem;
}

.about-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 0.65rem;
  margin-bottom: 2rem;
}

.tag {
  background: white;
  border: 1.5px solid rgba(232,93,38,0.25);
  color: var(--orange);
  padding: 0.35rem 0.9rem;
  border-radius: var(--radius-pill);
  font-family: 'Nunito', sans-serif;
  font-size: 0.82rem;
  font-weight: 700;
  transition: var(--transition);
}
.tag:hover {
  background: var(--orange);
  color: white;
  border-color: var(--orange);
  transform: translateY(-2px);
}

.btn-secondary {
  display: inline-block;
  background: var(--green);
  color: white;
  padding: 0.85rem 2rem;
  border-radius: var(--radius-pill);
  font-family: 'Nunito', sans-serif;
  font-weight: 800;
  font-size: 1rem;
  text-decoration: none;
  transition: var(--transition);
  box-shadow: 0 6px 20px rgba(44,110,73,0.3);
}
.btn-secondary:hover {
  background: #1e4d34;
  transform: translateY(-3px);
}

/* Stacked images */
.about-image-stack {
  position: relative;
  height: 420px;
}

.stack-img {
  position: absolute;
  border-radius: 20px;
  object-fit: cover;
  box-shadow: var(--shadow-card);
  transition: var(--transition);
}

.stack-back {
  width: 75%;
  height: 80%;
  top: 0; right: 0;
  filter: brightness(0.85);
}

.stack-front {
  width: 65%;
  height: 70%;
  bottom: 0; left: 0;
  border: 4px solid white;
  z-index: 2;
}

.about-image-stack:hover .stack-front { transform: rotate(-2deg) scale(1.03); }
.about-image-stack:hover .stack-back  { transform: rotate(2deg) scale(1.02); }

.stack-badge {
  position: absolute;
  bottom: 20px;
  right: 20px;
  background: var(--orange);
  color: white;
  padding: 1rem 1.5rem;
  border-radius: 16px;
  text-align: center;
  z-index: 3;
  box-shadow: 0 8px 24px rgba(232,93,38,0.4);
  animation: badgePop 3s ease-in-out infinite alternate;
}
.badge-number {
  font-family: 'Playfair Display', serif;
  font-size: 1.8rem;
  font-weight: 900;
  line-height: 1;
}
.badge-label {
  font-family: 'Nunito', sans-serif;
  font-size: 0.72rem;
  font-weight: 700;
  opacity: 0.9;
  margin-top: 4px;
}

@keyframes badgePop {
  0%   { transform: translateY(0); }
  100% { transform: translateY(-8px); }
}

/* Scroll fade-in utility */
.fade-in-left, .fade-in-right, .fade-in-up {
  opacity: 0;
  transition: opacity 0.8s ease, transform 0.8s ease;
}
.fade-in-left  { transform: translateX(-40px); }
.fade-in-right { transform: translateX(40px); }
.fade-in-up    { transform: translateY(40px); }

.fade-in-left.visible,
.fade-in-right.visible,
.fade-in-up.visible {
  opacity: 1;
  transform: none;
}

.mt-2 { margin-top: 1rem; }

@media (max-width: 900px) {
  .about-grid { grid-template-columns: 1fr; gap: 3rem; }
  .about-image-stack { height: 300px; }
}
```

---

## 4. Stats Counter Strip

### HTML

```html
<section class="stats-strip">
  <div class="stats-container">
    <div class="stat-item">
      <div class="stat-number" data-target="200">0</div>
      <div class="stat-plus">+</div>
      <div class="stat-label">Volunteers Nationwide</div>
    </div>
    <div class="stat-divider"></div>
    <div class="stat-item">
      <div class="stat-number" data-target="28">0</div>
      <div class="stat-label">States Covered</div>
    </div>
    <div class="stat-divider"></div>
    <div class="stat-item">
      <div class="stat-number" data-target="50000">0</div>
      <div class="stat-plus">+</div>
      <div class="stat-label">Beneficiaries Helped</div>
    </div>
    <div class="stat-divider"></div>
    <div class="stat-item">
      <div class="stat-number" data-target="6">0</div>
      <div class="stat-label">Active Projects</div>
    </div>
    <div class="stat-divider"></div>
    <div class="stat-item">
      <div class="stat-number" data-target="30000">0</div>
      <div class="stat-plus">+</div>
      <div class="stat-label">Interns Trained (4 Years)</div>
    </div>
  </div>
</section>
```

### CSS

```css
.stats-strip {
  background: linear-gradient(135deg, var(--navy) 0%, #2a1a40 100%);
  padding: 4rem 2rem;
  position: relative;
  overflow: hidden;
}

.stats-strip::before {
  content: '';
  position: absolute;
  inset: 0;
  background: repeating-linear-gradient(
    45deg,
    transparent,
    transparent 40px,
    rgba(255,255,255,0.02) 40px,
    rgba(255,255,255,0.02) 80px
  );
}

.stats-container {
  max-width: 1200px;
  margin: 0 auto;
  display: flex;
  align-items: center;
  justify-content: space-around;
  flex-wrap: wrap;
  gap: 2rem;
  position: relative;
}

.stat-item {
  text-align: center;
  position: relative;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.stat-number {
  font-family: 'Playfair Display', serif;
  font-size: clamp(2.5rem, 5vw, 3.8rem);
  font-weight: 900;
  color: var(--orange);
  line-height: 1;
  display: inline-block;
}

.stat-plus {
  font-family: 'Playfair Display', serif;
  font-size: 2rem;
  color: var(--yellow);
  line-height: 1;
  margin-top: -0.5rem;
}

.stat-label {
  font-family: 'Nunito', sans-serif;
  font-size: 0.9rem;
  color: rgba(255,255,255,0.65);
  font-weight: 600;
  margin-top: 0.5rem;
  max-width: 120px;
  line-height: 1.3;
}

.stat-divider {
  width: 1px;
  height: 60px;
  background: rgba(255,255,255,0.12);
}

@media (max-width: 700px) {
  .stat-divider { display: none; }
  .stats-container { justify-content: center; gap: 2.5rem; }
}
```

### JavaScript (counter animation)

```js
// Animated counter on scroll
const counters = document.querySelectorAll('.stat-number');
const counterObserver = new IntersectionObserver((entries) => {
  entries.forEach(entry => {
    if (entry.isIntersecting) {
      const el = entry.target;
      const target = parseInt(el.getAttribute('data-target'));
      const duration = 2000;
      const step = target / (duration / 16);
      let current = 0;
      const timer = setInterval(() => {
        current += step;
        if (current >= target) {
          el.textContent = target.toLocaleString();
          clearInterval(timer);
        } else {
          el.textContent = Math.floor(current).toLocaleString();
        }
      }, 16);
      counterObserver.unobserve(el);
    }
  });
}, { threshold: 0.5 });

counters.forEach(c => counterObserver.observe(c));
```

---

## 5. Projects — Horizontal Scroll Cards

### HTML

```html
<section class="projects-section" id="projects">
  <div class="container">
    <div class="section-label">💡 Our Initiatives</div>
    <h2 class="section-title">Six Pillars of Change</h2>
    <p class="projects-intro">
      Each project under InAmigos Foundation targets a specific dimension of
      social upliftment — from feeding the hungry to empowering women and
      protecting nature.
    </p>
  </div>

  <!-- Horizontal scrolling track -->
  <div class="projects-scroll-wrapper">
    <div class="projects-track">

      <div class="project-card" style="--card-color: #E85D26;">
        <div class="project-icon">📚</div>
        <div class="project-tag">Education</div>
        <h3 class="project-name">BachpanShala</h3>
        <p class="project-desc">
          Bridging the education gap for underprivileged children through
          basic digital literacy, life skills, and school education support.
          Nurturing young minds to build bright futures.
        </p>
        <div class="project-impact">👧 Children Empowered</div>
        <!-- 🔗 PLACEHOLDER: Replace # with project page link -->
        <a href="#" class="project-link">Explore →</a>
      </div>

      <div class="project-card" style="--card-color: #2C6E49;">
        <div class="project-icon">🍽️</div>
        <div class="project-tag">Humanitarian</div>
        <h3 class="project-name">Project Seva</h3>
        <p class="project-desc">
          Over <strong>50,000+ meals and clothing items</strong> distributed
          to underprivileged families across India. Serving humanity with
          compassion, one meal at a time.
        </p>
        <div class="project-impact">🤲 50,000+ Meals Given</div>
        <!-- 🔗 PLACEHOLDER: Replace # with project page link -->
        <a href="#" class="project-link">Explore →</a>
      </div>

      <div class="project-card" style="--card-color: #9B5DE5;">
        <div class="project-icon">👩</div>
        <div class="project-tag">Women Empowerment</div>
        <h3 class="project-name">Project Udaan</h3>
        <p class="project-desc">
          Soaring towards a brighter future — empowering women through
          self-help groups, skill development, financial independence, and
          menstrual hygiene awareness in rural communities.
        </p>
        <div class="project-impact">🌸 Rural Women Uplifted</div>
        <!-- 🔗 PLACEHOLDER: Replace # with project page link -->
        <a href="#" class="project-link">Explore →</a>
      </div>

      <div class="project-card" style="--card-color: #F77F00;">
        <div class="project-icon">🐾</div>
        <div class="project-tag">Animal Welfare</div>
        <h3 class="project-name">Project Jeev</h3>
        <p class="project-desc">
          Empowering lives and spreading compassion — feeding <strong>50+
          stray animals daily</strong>, rescue operations, and protection
          drives through our volunteer network.
        </p>
        <div class="project-impact">🐕 50+ Animals Fed Daily</div>
        <!-- 🔗 PLACEHOLDER: Replace # with project page link -->
        <a href="#" class="project-link">Explore →</a>
      </div>

      <div class="project-card" style="--card-color: #2C6E49;">
        <div class="project-icon">🌿</div>
        <div class="project-tag">Environment</div>
        <h3 class="project-name">Project Prakriti</h3>
        <p class="project-desc">
          Plant for a better tomorrow — <strong>20,000+ saplings planted</strong>,
          advocacy for sustainable farming, environmental conservation, and
          eco-friendly agricultural practices.
        </p>
        <div class="project-impact">🌳 20,000+ Trees Planted</div>
        <!-- 🔗 PLACEHOLDER: Replace # with project page link -->
        <a href="#" class="project-link">Explore →</a>
      </div>

      <div class="project-card" style="--card-color: #E85D26;">
        <div class="project-icon">💼</div>
        <div class="project-tag">Skill Development</div>
        <h3 class="project-name">Project Vikas</h3>
        <p class="project-desc">
          Enhancing employability through internships in data operations,
          finance, research, content writing, digital marketing, and social
          work. <strong>30,000+ interns trained</strong> in four years.
        </p>
        <div class="project-impact">🎓 30,000+ Interns Trained</div>
        <!-- 🔗 PLACEHOLDER: Replace # with project page link -->
        <a href="#" class="project-link">Explore →</a>
      </div>

    </div><!-- .projects-track -->
  </div><!-- .projects-scroll-wrapper -->

  <!-- Scroll indicator -->
  <div class="scroll-hint-row">
    <span>← Scroll horizontally to see all projects →</span>
  </div>
</section>
```

### CSS

```css
.projects-section {
  background: var(--cream);
  padding: 7rem 0 5rem;
  overflow: hidden;
}

.projects-section .container { padding: 0 2rem; margin-bottom: 3rem; }

.projects-intro {
  font-family: 'Nunito', sans-serif;
  font-size: 1.05rem;
  color: #666;
  max-width: 600px;
  line-height: 1.7;
  margin-top: 0.75rem;
}

/* Horizontal scroll wrapper */
.projects-scroll-wrapper {
  overflow-x: auto;
  padding: 1rem 2rem 2rem;
  scrollbar-width: thin;
  scrollbar-color: var(--orange) rgba(232,93,38,0.1);
  cursor: grab;
}
.projects-scroll-wrapper::-webkit-scrollbar { height: 6px; }
.projects-scroll-wrapper::-webkit-scrollbar-track { background: rgba(232,93,38,0.08); border-radius: 3px; }
.projects-scroll-wrapper::-webkit-scrollbar-thumb { background: var(--orange); border-radius: 3px; }

.projects-track {
  display: flex;
  gap: 1.5rem;
  width: max-content;
  padding-bottom: 0.5rem;
}

/* Project cards */
.project-card {
  width: 320px;
  flex-shrink: 0;
  background: white;
  border-radius: var(--radius-lg);
  padding: 2rem 1.75rem 1.75rem;
  box-shadow: var(--shadow-card);
  position: relative;
  overflow: hidden;
  transition: var(--transition);
  border-top: 4px solid var(--card-color, var(--orange));
}

.project-card::before {
  content: '';
  position: absolute;
  bottom: 0; right: 0;
  width: 140px; height: 140px;
  background: var(--card-color, var(--orange));
  opacity: 0.06;
  border-radius: 50%;
  transform: translate(40%, 40%);
  transition: var(--transition);
}

.project-card:hover {
  transform: translateY(-8px);
  box-shadow: 0 20px 50px rgba(0,0,0,0.15);
}
.project-card:hover::before { opacity: 0.12; transform: translate(30%, 30%) scale(1.2); }

.project-icon {
  font-size: 2.5rem;
  margin-bottom: 0.75rem;
  display: block;
}

.project-tag {
  display: inline-block;
  font-family: 'Nunito', sans-serif;
  font-size: 0.72rem;
  font-weight: 800;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  color: var(--card-color, var(--orange));
  background: color-mix(in srgb, var(--card-color, var(--orange)) 10%, transparent);
  padding: 0.3rem 0.8rem;
  border-radius: var(--radius-pill);
  margin-bottom: 0.75rem;
}

.project-name {
  font-family: 'Playfair Display', serif;
  font-size: 1.5rem;
  font-weight: 900;
  color: var(--navy);
  margin-bottom: 0.85rem;
}

.project-desc {
  font-family: 'Nunito', sans-serif;
  font-size: 0.93rem;
  color: #666;
  line-height: 1.65;
  margin-bottom: 1.25rem;
}

.project-impact {
  display: flex;
  align-items: center;
  gap: 0.4rem;
  font-family: 'Nunito', sans-serif;
  font-size: 0.88rem;
  font-weight: 700;
  color: var(--card-color, var(--orange));
  margin-bottom: 1.25rem;
  padding: 0.5rem 0;
  border-top: 1px solid rgba(0,0,0,0.06);
  border-bottom: 1px solid rgba(0,0,0,0.06);
}

.project-link {
  display: inline-block;
  font-family: 'Nunito', sans-serif;
  font-weight: 800;
  font-size: 0.95rem;
  color: var(--card-color, var(--orange));
  text-decoration: none;
  transition: var(--transition);
  padding-bottom: 2px;
  border-bottom: 2px solid transparent;
}
.project-link:hover { border-bottom-color: var(--card-color, var(--orange)); letter-spacing: 0.02em; }

/* Drag-to-scroll JS hook */
.projects-scroll-wrapper.grabbing { cursor: grabbing; }

.scroll-hint-row {
  text-align: center;
  font-family: 'Nunito', sans-serif;
  font-size: 0.85rem;
  color: rgba(0,0,0,0.35);
  margin-top: 0.5rem;
  letter-spacing: 0.05em;
}
```

### JavaScript (drag-to-scroll)

```js
// Drag to scroll projects track
const slider = document.querySelector('.projects-scroll-wrapper');
let isDown = false, startX, scrollLeft;

slider.addEventListener('mousedown', e => {
  isDown = true;
  slider.classList.add('grabbing');
  startX = e.pageX - slider.offsetLeft;
  scrollLeft = slider.scrollLeft;
});
slider.addEventListener('mouseleave', () => { isDown = false; slider.classList.remove('grabbing'); });
slider.addEventListener('mouseup',    () => { isDown = false; slider.classList.remove('grabbing'); });
slider.addEventListener('mousemove',  e => {
  if (!isDown) return;
  e.preventDefault();
  const x = e.pageX - slider.offsetLeft;
  slider.scrollLeft = scrollLeft - (x - startX) * 1.5;
});
```

---

## 6. Social Impact Section

### HTML

```html
<section class="impact-section" id="impact">
  <div class="container">
    <div class="section-label">💛 Why It Matters</div>
    <h2 class="section-title center">The Change We Drive</h2>
  </div>

  <!-- Alternating impact items -->
  <div class="impact-list">

    <div class="impact-item fade-in-left">
      <div class="impact-visual">
        <img src="https://inamigosfoundation.org.in/public/storage/gallery/1743051449.jpg"
             alt="Education impact" class="impact-img">
        <div class="impact-number-badge">01</div>
      </div>
      <div class="impact-content">
        <span class="impact-emoji">📚</span>
        <h3>Closing the Education Gap</h3>
        <p>
          Millions of children in India grow up without access to quality education.
          Through <strong>BachpanShala</strong>, we run learning centres that
          provide school support, digital literacy, and life-skills training —
          because education is the most powerful tool to break the cycle of poverty.
        </p>
        <ul class="impact-bullets">
          <li>✔ Digital literacy for underprivileged children</li>
          <li>✔ After-school tutoring centres</li>
          <li>✔ Life skills and vocational awareness</li>
        </ul>
      </div>
    </div>

    <div class="impact-item reverse fade-in-right">
      <div class="impact-visual">
        <img src="https://inamigosfoundation.org.in/public/storage/gallery/1743051438.jpg"
             alt="Women empowerment" class="impact-img">
        <div class="impact-number-badge">02</div>
      </div>
      <div class="impact-content">
        <span class="impact-emoji">👩</span>
        <h3>Empowering Women, Strengthening Families</h3>
        <p>
          <strong>Project Udaan</strong> works with self-help groups in
          rural India to promote financial independence, entrepreneurship,
          and awareness around health and hygiene. When women rise,
          entire communities rise with them.
        </p>
        <ul class="impact-bullets">
          <li>✔ Self-help group collaborations in rural areas</li>
          <li>✔ Skill development & micro-entrepreneurship</li>
          <li>✔ Menstrual hygiene and health awareness drives</li>
        </ul>
      </div>
    </div>

    <div class="impact-item fade-in-left">
      <div class="impact-visual">
        <img src="https://inamigosfoundation.org.in/public/storage/gallery/1743051485.jpg"
             alt="Environment" class="impact-img">
        <div class="impact-number-badge">03</div>
      </div>
      <div class="impact-content">
        <span class="impact-emoji">🌿</span>
        <h3>Protecting Our Planet</h3>
        <p>
          Climate change is an urgent threat. <strong>Project Prakriti</strong>
          leads tree-plantation drives, promotes eco-friendly farming, and
          educates communities on sustainability — because a healthy planet
          is the foundation for all human progress.
        </p>
        <ul class="impact-bullets">
          <li>✔ 20,000+ saplings planted across India</li>
          <li>✔ Eco-agriculture awareness campaigns</li>
          <li>✔ World Environment Day & Water Day events</li>
        </ul>
      </div>
    </div>

  </div>
</section>
```

### CSS

```css
.impact-section {
  background: white;
  padding: 7rem 2rem;
}

.center { text-align: center; margin: 0 auto; }

.impact-list {
  max-width: 1200px;
  margin: 4rem auto 0;
  display: flex;
  flex-direction: column;
  gap: 6rem;
}

.impact-item {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 5rem;
  align-items: center;
}

.impact-item.reverse {
  direction: rtl;
}
.impact-item.reverse > * {
  direction: ltr;
}

.impact-visual {
  position: relative;
  border-radius: var(--radius-lg);
  overflow: visible;
}

.impact-img {
  width: 100%;
  height: 380px;
  object-fit: cover;
  border-radius: var(--radius-lg);
  box-shadow: var(--shadow-card);
  transition: transform 0.6s ease;
}
.impact-item:hover .impact-img { transform: scale(1.03) rotate(-1deg); }

.impact-number-badge {
  position: absolute;
  top: -20px;
  left: -20px;
  width: 64px; height: 64px;
  background: var(--orange);
  color: white;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-family: 'Playfair Display', serif;
  font-size: 1.4rem;
  font-weight: 900;
  box-shadow: 0 6px 20px rgba(232,93,38,0.35);
}

.impact-emoji {
  font-size: 2.5rem;
  display: block;
  margin-bottom: 0.75rem;
}

.impact-content h3 {
  font-family: 'Playfair Display', serif;
  font-size: clamp(1.5rem, 3vw, 2.2rem);
  font-weight: 900;
  color: var(--navy);
  margin-bottom: 1rem;
  line-height: 1.2;
}

.impact-content p {
  font-family: 'Nunito', sans-serif;
  font-size: 1rem;
  color: #555;
  line-height: 1.75;
  margin-bottom: 1.25rem;
}

.impact-bullets {
  list-style: none;
  padding: 0;
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}
.impact-bullets li {
  font-family: 'Nunito', sans-serif;
  font-size: 0.95rem;
  color: var(--green);
  font-weight: 700;
}

@media (max-width: 900px) {
  .impact-item,
  .impact-item.reverse {
    grid-template-columns: 1fr;
    direction: ltr;
    gap: 2rem;
  }
  .impact-img { height: 260px; }
}
```

---

## 7. Gallery Section

### HTML

```html
<section class="gallery-section" id="gallery">
  <div class="container">
    <div class="section-label">📸 Our Work in Pictures</div>
    <h2 class="section-title">Gallery</h2>
    <p class="projects-intro">A glimpse into the lives we touch and the communities we serve.</p>
  </div>

  <div class="gallery-grid container">
    <div class="gallery-item tall fade-in-up">
      <img src="https://inamigosfoundation.org.in/public/storage/gallery/1743051485.jpg"
           alt="InAmigos volunteers" loading="lazy">
      <div class="gallery-overlay">
        <span>Volunteer Drive 2024</span>
      </div>
    </div>
    <div class="gallery-item fade-in-up" style="animation-delay:0.1s;">
      <img src="https://inamigosfoundation.org.in/public/storage/gallery/1743051466.jpg"
           alt="InAmigos community" loading="lazy">
      <div class="gallery-overlay">
        <span>Community Outreach</span>
      </div>
    </div>
    <div class="gallery-item fade-in-up" style="animation-delay:0.2s;">
      <img src="https://inamigosfoundation.org.in/public/storage/gallery/1743051449.jpg"
           alt="BachpanShala" loading="lazy">
      <div class="gallery-overlay">
        <span>BachpanShala Sessions</span>
      </div>
    </div>
    <div class="gallery-item wide fade-in-up" style="animation-delay:0.3s;">
      <img src="https://inamigosfoundation.org.in/public/storage/gallery/1743051438.jpg"
           alt="InAmigos event" loading="lazy">
      <div class="gallery-overlay">
        <span>Seva Food Distribution</span>
      </div>
    </div>
    <!-- Add more gallery items here with actual images -->
  </div>

  <!-- 🔗 PLACEHOLDER: Replace # with gallery page link -->
  <div style="text-align:center; margin-top:3rem;">
    <a href="#" class="btn btn-primary" style="display:inline-flex;">📷 View Full Gallery</a>
  </div>
</section>
```

### CSS

```css
.gallery-section {
  background: var(--cream);
  padding: 7rem 2rem;
}

.gallery-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-template-rows: 250px 250px;
  gap: 1rem;
  margin-top: 3rem;
}

.gallery-item {
  position: relative;
  border-radius: 16px;
  overflow: hidden;
  cursor: pointer;
}

.gallery-item.tall { grid-row: span 2; }
.gallery-item.wide { grid-column: span 2; }

.gallery-item img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.6s ease;
  display: block;
}

.gallery-overlay {
  position: absolute;
  inset: 0;
  background: linear-gradient(
    to top,
    rgba(26,26,46,0.85) 0%,
    transparent 60%
  );
  display: flex;
  align-items: flex-end;
  padding: 1.25rem;
  opacity: 0;
  transition: opacity 0.4s ease;
}

.gallery-overlay span {
  font-family: 'Nunito', sans-serif;
  font-size: 0.95rem;
  font-weight: 700;
  color: white;
  letter-spacing: 0.03em;
}

.gallery-item:hover img        { transform: scale(1.08); }
.gallery-item:hover .gallery-overlay { opacity: 1; }

@media (max-width: 768px) {
  .gallery-grid {
    grid-template-columns: 1fr 1fr;
    grid-template-rows: auto;
  }
  .gallery-item.tall { grid-row: span 1; }
  .gallery-item.wide { grid-column: span 1; }
}
```

---

## 8. Events Timeline

### HTML

```html
<section class="events-section" id="events">
  <div class="container">
    <div class="section-label">📅 Recent Events</div>
    <h2 class="section-title">Milestones & Activities</h2>

    <div class="timeline">

      <div class="timeline-item fade-in-up">
        <div class="timeline-date">22 March 2025</div>
        <div class="timeline-dot"></div>
        <div class="timeline-card">
          <span class="timeline-tag">Community</span>
          <h4>World Water Day 2025</h4>
          <p>Highlighted the importance of water conservation and collective action to ensure clean water for all communities across India.</p>
          <!-- 🔗 PLACEHOLDER -->
          <a href="#" class="timeline-link">Read More →</a>
        </div>
      </div>

      <div class="timeline-item fade-in-up">
        <div class="timeline-date">20 March 2025</div>
        <div class="timeline-dot"></div>
        <div class="timeline-card">
          <span class="timeline-tag">Happiness</span>
          <h4>International Day of Happiness 2025</h4>
          <p>Spreading joy, positivity, and well-being through engaging activities, workshops, and inspiring community discussions.</p>
          <!-- 🔗 PLACEHOLDER -->
          <a href="#" class="timeline-link">Read More →</a>
        </div>
      </div>

      <div class="timeline-item fade-in-up">
        <div class="timeline-date">11 Feb 2025</div>
        <div class="timeline-dot"></div>
        <div class="timeline-card">
          <span class="timeline-tag">Education</span>
          <h4>Women and Girls in Science Day</h4>
          <p>Celebrated and encouraged women and girls to pursue careers in science, technology, engineering, and mathematics across our outreach zones.</p>
          <!-- 🔗 PLACEHOLDER -->
          <a href="#" class="timeline-link">Read More →</a>
        </div>
      </div>

    </div>

    <!-- 🔗 PLACEHOLDER -->
    <div style="text-align:center; margin-top:3rem;">
      <a href="#" class="btn btn-secondary" style="display:inline-flex;">See All Events</a>
    </div>
  </div>
</section>
```

### CSS

```css
.events-section {
  background: white;
  padding: 7rem 2rem;
}

.timeline {
  position: relative;
  margin-top: 3rem;
  padding-left: 2rem;
}

.timeline::before {
  content: '';
  position: absolute;
  left: 0;
  top: 0; bottom: 0;
  width: 3px;
  background: linear-gradient(to bottom, var(--orange), var(--green));
  border-radius: 2px;
}

.timeline-item {
  position: relative;
  display: grid;
  grid-template-columns: 140px 20px 1fr;
  gap: 1.5rem;
  align-items: start;
  margin-bottom: 3rem;
}

.timeline-date {
  font-family: 'Nunito', sans-serif;
  font-size: 0.85rem;
  font-weight: 800;
  color: var(--orange);
  text-align: right;
  padding-top: 0.3rem;
}

.timeline-dot {
  width: 20px;
  height: 20px;
  background: var(--orange);
  border: 3px solid white;
  border-radius: 50%;
  box-shadow: 0 0 0 3px var(--orange);
  margin-top: 0.15rem;
  transition: var(--transition);
}

.timeline-item:hover .timeline-dot {
  background: var(--green);
  box-shadow: 0 0 0 3px var(--green);
  transform: scale(1.3);
}

.timeline-card {
  background: var(--cream);
  border-radius: 16px;
  padding: 1.5rem 1.75rem;
  border-left: 4px solid var(--orange);
  transition: var(--transition);
}
.timeline-card:hover {
  transform: translateX(6px);
  box-shadow: var(--shadow-soft);
}

.timeline-tag {
  display: inline-block;
  font-family: 'Nunito', sans-serif;
  font-size: 0.72rem;
  font-weight: 800;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  color: var(--green);
  background: rgba(44,110,73,0.1);
  padding: 0.25rem 0.75rem;
  border-radius: var(--radius-pill);
  margin-bottom: 0.6rem;
}

.timeline-card h4 {
  font-family: 'Playfair Display', serif;
  font-size: 1.2rem;
  font-weight: 700;
  color: var(--navy);
  margin-bottom: 0.5rem;
}

.timeline-card p {
  font-family: 'Nunito', sans-serif;
  font-size: 0.93rem;
  color: #666;
  line-height: 1.6;
  margin-bottom: 0.75rem;
}

.timeline-link {
  font-family: 'Nunito', sans-serif;
  font-weight: 800;
  font-size: 0.88rem;
  color: var(--orange);
  text-decoration: none;
  transition: letter-spacing 0.3s;
}
.timeline-link:hover { letter-spacing: 0.04em; }

@media (max-width: 700px) {
  .timeline-item { grid-template-columns: 1fr; gap: 0.5rem; }
  .timeline-date { text-align: left; }
  .timeline-dot  { display: none; }
}
```

---

## 9. Testimonials / Volunteer Voices

### HTML

```html
<section class="testimonials-section" id="testimonials">
  <div class="container">
    <div class="section-label">🗣️ Volunteer Voices</div>
    <h2 class="section-title center">Stories of Change</h2>

    <div class="testimonials-grid">

      <div class="testimonial-card fade-in-up">
        <div class="quote-mark">"</div>
        <p class="testimonial-text">
          Volunteering with InAmigos has been the most fulfilling experience of my life.
          The BachpanShala project changed how I look at education — it's not just about
          books, it's about giving children the confidence to dream.
        </p>
        <div class="testimonial-author">
          <div class="author-avatar">FK</div>
          <div>
            <div class="author-name">Faiz Khan</div>
            <div class="author-role">Volunteer Supervisor, Uttar Pradesh</div>
          </div>
        </div>
      </div>

      <div class="testimonial-card fade-in-up" style="animation-delay:0.15s;">
        <div class="quote-mark">"</div>
        <p class="testimonial-text">
          The warmth and dedication of the InAmigos team is unmatched. Being part of
          Project Seva taught me that even a small act — sharing a meal — can restore
          a person's dignity and hope.
        </p>
        <div class="testimonial-author">
          <div class="author-avatar" style="background:var(--green);">MJ</div>
          <div>
            <div class="author-name">Manavi Jaiswal</div>
            <div class="author-role">Junior Volunteer Associate</div>
          </div>
        </div>
      </div>

      <div class="testimonial-card fade-in-up" style="animation-delay:0.3s;">
        <div class="quote-mark">"</div>
        <p class="testimonial-text">
          Project Vikas gave me real-world experience I couldn't get anywhere else.
          InAmigos doesn't just train interns — they nurture future changemakers
          who go on to make a difference in every sector.
        </p>
        <div class="testimonial-author">
          <div class="author-avatar" style="background:var(--yellow); color:var(--navy);">A</div>
          <div>
            <div class="author-name">Akash</div>
            <div class="author-role">Volunteer Associate</div>
          </div>
        </div>
      </div>

    </div>
  </div>
</section>
```

### CSS

```css
.testimonials-section {
  background: linear-gradient(135deg, var(--navy) 0%, #2a1a40 100%);
  padding: 7rem 2rem;
}

.testimonials-section .section-label { color: var(--yellow); }
.testimonials-section .section-title { color: white; }

.testimonials-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 1.75rem;
  margin-top: 3rem;
}

.testimonial-card {
  background: rgba(255,255,255,0.05);
  border: 1px solid rgba(255,255,255,0.1);
  border-radius: var(--radius-lg);
  padding: 2rem;
  backdrop-filter: blur(8px);
  transition: var(--transition);
  position: relative;
}
.testimonial-card:hover {
  background: rgba(255,255,255,0.1);
  transform: translateY(-6px);
  box-shadow: 0 20px 48px rgba(0,0,0,0.3);
}

.quote-mark {
  font-family: 'Playfair Display', serif;
  font-size: 5rem;
  color: var(--orange);
  line-height: 0.6;
  margin-bottom: 1rem;
  opacity: 0.6;
}

.testimonial-text {
  font-family: 'Nunito', sans-serif;
  font-size: 0.97rem;
  color: rgba(255,255,255,0.8);
  line-height: 1.75;
  margin-bottom: 1.5rem;
  font-style: italic;
}

.testimonial-author {
  display: flex;
  align-items: center;
  gap: 0.85rem;
}

.author-avatar {
  width: 46px; height: 46px;
  border-radius: 50%;
  background: var(--orange);
  color: white;
  display: flex;
  align-items: center;
  justify-content: center;
  font-family: 'Playfair Display', serif;
  font-weight: 900;
  font-size: 1rem;
  flex-shrink: 0;
}

.author-name {
  font-family: 'Nunito', sans-serif;
  font-weight: 800;
  color: white;
  font-size: 0.95rem;
}
.author-role {
  font-family: 'Nunito', sans-serif;
  font-size: 0.78rem;
  color: rgba(255,255,255,0.5);
  margin-top: 2px;
}

@media (max-width: 900px) {
  .testimonials-grid { grid-template-columns: 1fr; }
}
```

---

## 10. Call-to-Action Section

### HTML

```html
<section class="cta-section" id="cta">
  <div class="cta-bg-pattern"></div>
  <div class="container cta-container">
    <div class="cta-text fade-in-up">
      <div class="section-label" style="color:var(--yellow);">✨ Join the Movement</div>
      <h2 class="cta-title">Be the Change India Needs</h2>
      <p class="cta-subtitle">
        Whether you donate, volunteer, or simply spread the word —
        every action creates ripples of change. Together, let's build
        a more compassionate and inclusive India. <strong>#InAmigos</strong>
      </p>
    </div>

    <div class="cta-cards fade-in-up" style="animation-delay:0.2s;">

      <div class="cta-card">
        <div class="cta-card-icon">❤️</div>
        <h3>Donate</h3>
        <p>Your contribution — big or small — directly funds our projects on the ground.</p>
        <!-- 🔗 PLACEHOLDER: Replace # with donation link (e.g. Razorpay) -->
        <a href="#" class="btn btn-primary" style="width:100%; justify-content:center;">Donate Now</a>
      </div>

      <div class="cta-card featured">
        <div class="cta-card-icon">🤝</div>
        <h3>Volunteer</h3>
        <p>Join our growing community of 200+ volunteers making a real difference across 28 states.</p>
        <!-- 🔗 PLACEHOLDER: Replace # with volunteer form link -->
        <a href="#" class="btn btn-primary" style="width:100%; justify-content:center;">Become a Volunteer</a>
      </div>

      <div class="cta-card">
        <div class="cta-card-icon">🌐</div>
        <h3>Partner With Us</h3>
        <p>CSR partnerships, corporate collaborations, or NGO alliances — let's amplify impact together.</p>
        <!-- 🔗 PLACEHOLDER: Replace # with contact/partnership link -->
        <a href="#" class="btn btn-primary" style="width:100%; justify-content:center;">Contact Us</a>
      </div>

    </div>

    <!-- Social media icons row -->
    <div class="social-row fade-in-up" style="animation-delay:0.4s;">
      <span>Follow us:</span>
      <!-- 🔗 PLACEHOLDER: Replace # with actual social links -->
      <a href="https://www.instagram.com/inamigos/" class="social-icon" target="_blank" aria-label="Instagram">📷</a>
      <a href="https://www.facebook.com/inamigos.inamigos" class="social-icon" target="_blank" aria-label="Facebook">📘</a>
      <a href="#" class="social-icon" aria-label="Twitter/X">🐦</a>
      <a href="#" class="social-icon" aria-label="LinkedIn">💼</a>
      <a href="#" class="social-icon" aria-label="YouTube">▶️</a>
    </div>
  </div>
</section>
```

### CSS

```css
.cta-section {
  background: var(--orange);
  padding: 7rem 2rem;
  position: relative;
  overflow: hidden;
}

.cta-bg-pattern {
  position: absolute;
  inset: 0;
  background: repeating-linear-gradient(
    -45deg,
    transparent,
    transparent 30px,
    rgba(255,255,255,0.04) 30px,
    rgba(255,255,255,0.04) 60px
  );
  pointer-events: none;
}

.cta-container {
  position: relative;
  z-index: 2;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 3.5rem;
}

.cta-text { text-align: center; max-width: 680px; }

.cta-title {
  font-family: 'Playfair Display', serif;
  font-size: clamp(2.2rem, 5vw, 3.5rem);
  font-weight: 900;
  color: white;
  line-height: 1.15;
  margin-bottom: 1rem;
}

.cta-subtitle {
  font-family: 'Nunito', sans-serif;
  font-size: 1.1rem;
  color: rgba(255,255,255,0.85);
  line-height: 1.7;
}

.cta-cards {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 1.5rem;
  width: 100%;
  max-width: 960px;
}

.cta-card {
  background: white;
  border-radius: var(--radius-lg);
  padding: 2rem 1.75rem;
  text-align: center;
  transition: var(--transition);
}
.cta-card:hover {
  transform: translateY(-8px);
  box-shadow: 0 20px 50px rgba(0,0,0,0.2);
}
.cta-card.featured {
  background: var(--navy);
  color: white;
  transform: scale(1.05);
}
.cta-card.featured:hover { transform: scale(1.05) translateY(-8px); }

.cta-card-icon { font-size: 2.5rem; margin-bottom: 0.75rem; }

.cta-card h3 {
  font-family: 'Playfair Display', serif;
  font-size: 1.4rem;
  font-weight: 900;
  color: var(--navy);
  margin-bottom: 0.6rem;
}
.cta-card.featured h3 { color: white; }

.cta-card p {
  font-family: 'Nunito', sans-serif;
  font-size: 0.9rem;
  color: #666;
  line-height: 1.6;
  margin-bottom: 1.5rem;
}
.cta-card.featured p { color: rgba(255,255,255,0.7); }

/* Social row */
.social-row {
  display: flex;
  align-items: center;
  gap: 1rem;
  font-family: 'Nunito', sans-serif;
  font-weight: 700;
  color: rgba(255,255,255,0.8);
  font-size: 0.95rem;
}
.social-icon {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 46px; height: 46px;
  background: rgba(255,255,255,0.15);
  border-radius: 50%;
  font-size: 1.3rem;
  text-decoration: none;
  transition: var(--transition);
  border: 2px solid rgba(255,255,255,0.25);
}
.social-icon:hover {
  background: white;
  transform: translateY(-4px) scale(1.1);
  box-shadow: 0 8px 24px rgba(0,0,0,0.2);
}

@media (max-width: 768px) {
  .cta-cards { grid-template-columns: 1fr; }
  .cta-card.featured { transform: scale(1); }
}
```

---

## 11. Footer

### HTML

```html
<footer class="footer">
  <div class="footer-wave">
    <svg viewBox="0 0 1440 80" xmlns="http://www.w3.org/2000/svg" preserveAspectRatio="none">
      <path d="M0,40 C360,80 1080,0 1440,40 L1440,80 L0,80 Z" fill="#1A1A2E"/>
    </svg>
  </div>

  <div class="footer-body">
    <div class="footer-grid">

      <div class="footer-brand">
        <img src="https://inamigosfoundation.org.in/public/storage/settings/174421468011.jpg"
             alt="InAmigos Foundation" class="footer-logo">
        <p>
          InAmigos Foundation — a Section 8 certified, NITI Aayog registered
          non-profit working to uplift communities across India through education,
          food, women empowerment, animal welfare, and sustainability.
        </p>
        <p class="footer-reg">📋 Reg. No.: Section 8 | 80G & 12A | ISO 9001:2015</p>
      </div>

      <div class="footer-links">
        <h4>Quick Links</h4>
        <ul>
          <!-- 🔗 PLACEHOLDERS: Update all href values -->
          <li><a href="#">Home</a></li>
          <li><a href="#">About Us</a></li>
          <li><a href="#">Our Projects</a></li>
          <li><a href="#">Gallery</a></li>
          <li><a href="#">Events</a></li>
          <li><a href="#">Blog</a></li>
          <li><a href="#">Contact</a></li>
        </ul>
      </div>

      <div class="footer-links">
        <h4>Our Projects</h4>
        <ul>
          <!-- 🔗 PLACEHOLDERS -->
          <li><a href="#">📚 BachpanShala</a></li>
          <li><a href="#">🍽️ Project Seva</a></li>
          <li><a href="#">👩 Project Udaan</a></li>
          <li><a href="#">🐾 Project Jeev</a></li>
          <li><a href="#">🌿 Project Prakriti</a></li>
          <li><a href="#">💼 Project Vikas</a></li>
        </ul>
      </div>

      <div class="footer-contact">
        <h4>Contact Us</h4>
        <p>📍 Ward No. 5, Gram Post, Sipat Ujwal Nagar,<br>
           Bilaspur, Chhattisgarh — 495555</p>
        <p>📧 <a href="mailto:inamigosfoundation@gmail.com">inamigosfoundation@gmail.com</a></p>
        <p>📞 <a href="tel:+916267309902">+91 626 730 9902</a></p>
        <p>🌐 <a href="https://inamigosfoundation.org.in" target="_blank">inamigosfoundation.org.in</a></p>
      </div>

    </div>

    <div class="footer-bottom">
      <p>© 2024 InAmigos Foundation. All Rights Reserved.</p>
      <p>Designed with ❤️ for a better India | #InAmigos</p>
    </div>
  </div>
</footer>
```

### CSS

```css
.footer {
  background: var(--navy);
  position: relative;
  color: rgba(255,255,255,0.7);
}

.footer-wave {
  margin-bottom: -4px;
  line-height: 0;
}
.footer-wave svg { width: 100%; display: block; }

.footer-body { padding: 4rem 2rem 2rem; max-width: 1200px; margin: 0 auto; }

.footer-grid {
  display: grid;
  grid-template-columns: 2fr 1fr 1fr 1.5fr;
  gap: 3rem;
  margin-bottom: 3rem;
}

.footer-logo {
  height: 60px;
  width: 60px;
  border-radius: 50%;
  object-fit: cover;
  border: 2px solid var(--orange);
  margin-bottom: 1rem;
}

.footer-brand p {
  font-family: 'Nunito', sans-serif;
  font-size: 0.9rem;
  line-height: 1.7;
  margin-bottom: 0.75rem;
}
.footer-reg {
  font-size: 0.8rem !important;
  color: rgba(255,255,255,0.4) !important;
}

.footer-links h4,
.footer-contact h4 {
  font-family: 'Playfair Display', serif;
  font-size: 1.1rem;
  color: white;
  margin-bottom: 1.25rem;
  position: relative;
  padding-bottom: 0.5rem;
}
.footer-links h4::after,
.footer-contact h4::after {
  content: '';
  position: absolute;
  bottom: 0; left: 0;
  width: 30px; height: 2px;
  background: var(--orange);
}

.footer-links ul {
  list-style: none;
  padding: 0;
  display: flex;
  flex-direction: column;
  gap: 0.6rem;
}
.footer-links ul a {
  font-family: 'Nunito', sans-serif;
  color: rgba(255,255,255,0.6);
  text-decoration: none;
  font-size: 0.93rem;
  transition: color 0.3s, padding-left 0.3s;
}
.footer-links ul a:hover { color: var(--orange); padding-left: 6px; }

.footer-contact p {
  font-family: 'Nunito', sans-serif;
  font-size: 0.9rem;
  line-height: 1.6;
  margin-bottom: 0.75rem;
}
.footer-contact a {
  color: rgba(255,255,255,0.6);
  text-decoration: none;
  transition: color 0.3s;
}
.footer-contact a:hover { color: var(--orange); }

.footer-bottom {
  border-top: 1px solid rgba(255,255,255,0.08);
  padding-top: 1.5rem;
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
  gap: 0.5rem;
  font-family: 'Nunito', sans-serif;
  font-size: 0.85rem;
  color: rgba(255,255,255,0.35);
}

@media (max-width: 900px) {
  .footer-grid { grid-template-columns: 1fr 1fr; }
}
@media (max-width: 500px) {
  .footer-grid { grid-template-columns: 1fr; }
  .footer-bottom { flex-direction: column; }
}
```

---

## 🔁 Scroll-Triggered Animation JavaScript

Add this to your `<script>` block — it makes all `.fade-in-*` elements animate when scrolled into view:

```js
// Intersection Observer for scroll animations
const animatedEls = document.querySelectorAll(
  '.fade-in-left, .fade-in-right, .fade-in-up'
);
const scrollObserver = new IntersectionObserver((entries) => {
  entries.forEach(entry => {
    if (entry.isIntersecting) {
      entry.target.classList.add('visible');
      scrollObserver.unobserve(entry.target);
    }
  });
}, { threshold: 0.15 });

animatedEls.forEach(el => scrollObserver.observe(el));
```

---

## 📄 Complete `index.html` Skeleton

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta name="description"
    content="InAmigos Foundation — a Section 8 non-profit spreading education, food, women empowerment, animal welfare & sustainability across India. Join us. #InAmigos">
  <meta property="og:title" content="InAmigos Foundation | Making India Better">
  <meta property="og:description" content="Empowering communities across 28 states through 6 impactful projects.">
  <meta property="og:image"
    content="https://inamigosfoundation.org.in/public/storage/settings/174421468011.jpg">
  <title>InAmigos Foundation — Awareness Page</title>

  <!-- Google Fonts -->
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@700;900&family=Nunito:wght@400;600;700;800&display=swap" rel="stylesheet">

  <link rel="stylesheet" href="style.css">
</head>
<body>

  <!-- 1. Navbar -->
  <!-- (paste navbar HTML here) -->

  <!-- 2. Hero -->
  <!-- (paste hero HTML here) -->

  <!-- 3. About -->
  <!-- (paste about HTML here) -->

  <!-- 4. Stats -->
  <!-- (paste stats HTML here) -->

  <!-- 5. Projects -->
  <!-- (paste projects HTML here) -->

  <!-- 6. Impact -->
  <!-- (paste impact HTML here) -->

  <!-- 7. Gallery -->
  <!-- (paste gallery HTML here) -->

  <!-- 8. Events -->
  <!-- (paste events HTML here) -->

  <!-- 9. Testimonials -->
  <!-- (paste testimonials HTML here) -->

  <!-- 10. CTA -->
  <!-- (paste cta HTML here) -->

  <!-- 11. Footer -->
  <!-- (paste footer HTML here) -->

  <script>
    /* === Paste all JavaScript sections here === */

    // 1. Sticky navbar
    window.addEventListener('scroll', () => {
      document.getElementById('navbar')
        .classList.toggle('scrolled', window.scrollY > 50);
    });

    // 2. Mobile menu
    document.getElementById('hamburger').addEventListener('click', () => {
      document.getElementById('navLinks').classList.toggle('open');
    });

    // 3. Counter animation
    const counters = document.querySelectorAll('.stat-number');
    const counterObserver = new IntersectionObserver((entries) => {
      entries.forEach(entry => {
        if (entry.isIntersecting) {
          const el = entry.target;
          const target = parseInt(el.getAttribute('data-target'));
          const duration = 2000;
          const step = target / (duration / 16);
          let current = 0;
          const timer = setInterval(() => {
            current += step;
            if (current >= target) {
              el.textContent = target.toLocaleString();
              clearInterval(timer);
            } else {
              el.textContent = Math.floor(current).toLocaleString();
            }
          }, 16);
          counterObserver.unobserve(el);
        }
      });
    }, { threshold: 0.5 });
    counters.forEach(c => counterObserver.observe(c));

    // 4. Drag-to-scroll projects track
    const slider = document.querySelector('.projects-scroll-wrapper');
    let isDown = false, startX, scrollLeft;
    slider.addEventListener('mousedown', e => {
      isDown = true;
      slider.classList.add('grabbing');
      startX = e.pageX - slider.offsetLeft;
      scrollLeft = slider.scrollLeft;
    });
    slider.addEventListener('mouseleave', () => { isDown = false; slider.classList.remove('grabbing'); });
    slider.addEventListener('mouseup',    () => { isDown = false; slider.classList.remove('grabbing'); });
    slider.addEventListener('mousemove', e => {
      if (!isDown) return;
      e.preventDefault();
      const x = e.pageX - slider.offsetLeft;
      slider.scrollLeft = scrollLeft - (x - startX) * 1.5;
    });

    // 5. Scroll-triggered fade-in animations
    const animatedEls = document.querySelectorAll('.fade-in-left, .fade-in-right, .fade-in-up');
    const scrollObserver = new IntersectionObserver((entries) => {
      entries.forEach(entry => {
        if (entry.isIntersecting) {
          entry.target.classList.add('visible');
          scrollObserver.unobserve(entry.target);
        }
      });
    }, { threshold: 0.15 });
    animatedEls.forEach(el => scrollObserver.observe(el));

  </script>
</body>
</html>
```

---

## 🔗 Placeholder Link Summary

All call-to-action links are marked with `<!-- 🔗 PLACEHOLDER -->`. Here's a quick reference:

| Button / Link | Where to Replace | Suggested Destination |
|---|---|---|
| **Donate Now** | Hero + CTA + Navbar | Razorpay / payment link |
| **Volunteer** | Hero + CTA | Google Form / volunteer page |
| **Join Us** | Navbar | Volunteer registration page |
| **Learn More About Us** | About section | `/page/About-Us` |
| **Explore →** (each project) | Project cards | Respective cause page |
| **View Full Gallery** | Gallery | `/gallery` |
| **See All Events** | Events | `/events` |
| **Contact Us** | CTA card | `/contact` |
| **Facebook** | Social icons | `facebook.com/inamigos.inamigos` |
| **Instagram** | Social icons | `instagram.com/inamigos/` |
| **Twitter/X, LinkedIn, YouTube** | Social icons | Official profiles |

---

## ✅ Final Checklist Before Submission

- [ ] All 11 sections are present and render correctly
- [ ] Google Fonts load (check internet connection or embed via `@import`)
- [ ] Navbar scrolls and highlights correctly on desktop and mobile
- [ ] Hamburger menu works on mobile viewport (< 768px)
- [ ] Stats counter animates when section comes into view
- [ ] Projects section scrolls horizontally (drag + scroll wheel)
- [ ] Gallery hover effects reveal captions
- [ ] Scroll-triggered animations fire for all `.fade-in-*` elements
- [ ] All `href="#"` placeholders are noted / replaced with real links
- [ ] `index.html` passes basic HTML validation (`validator.w3.org`)
- [ ] Page looks good on mobile (375px), tablet (768px), desktop (1280px)
- [ ] Alt text on all images is descriptive
- [ ] `<meta>` description and OG tags are accurate

---

## 🎯 Evaluation Tips

| Criterion | How to Score High |
|---|---|
| **Content Accuracy** | Use exact data from the official site — founding date, founder name, project names, certifications |
| **Design & Structure** | Follow the color system, font pairing, and section order above |
| **Creativity** | Add smooth animations, hover effects, and the horizontal scroll — these set your page apart |
| **Use of Sources** | Cite hashtag `#InAmigos` content ideas; reference official site sections (About, Causes, Events) |

---

*Built for InAmigos Foundation Awareness Campaign | #InAmigos | inamigosfoundation.org.in*
