[ecotrack.html](https://github.com/user-attachments/files/26794695/ecotrack.html)
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>EcoTrack – Smart Plastic Waste Management</title>
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;600;700;800&family=DM+Sans:ital,wght@0,300;0,400;0,500;0,600;1,400&display=swap" rel="stylesheet"/>
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css"/>

<style>
/* ============================================================
   CSS VARIABLES & RESET
============================================================ */
:root {
  --bg-deep:      #030f07;
  --bg-mid:       #061a0e;
  --bg-panel:     #0a2614;
  --green-900:    #0d4f3c;
  --green-700:    #1a7a5a;
  --green-500:    #22c47e;
  --green-400:    #34e896;
  --green-neon:   #00ff87;
  --cyan:         #00e5c8;
  --cyan-light:   #7fffd4;
  --gold:         #f5c842;
  --coral:        #ff6b6b;
  --white:        #ffffff;
  --white-80:     rgba(255,255,255,0.80);
  --white-60:     rgba(255,255,255,0.60);
  --white-30:     rgba(255,255,255,0.30);
  --white-10:     rgba(255,255,255,0.10);
  --white-06:     rgba(255,255,255,0.06);
  --glass-bg:     rgba(255,255,255,0.055);
  --glass-border: rgba(0,255,135,0.18);
  --glass-shadow: 0 8px 40px rgba(0,0,0,0.45);
  --glow-green:   0 0 40px rgba(0,255,135,0.25);
  --glow-cyan:    0 0 40px rgba(0,229,200,0.20);
  --radius-sm:    10px;
  --radius-md:    18px;
  --radius-lg:    28px;
  --radius-xl:    40px;
  --font-head:    'Syne', sans-serif;
  --font-body:    'DM Sans', sans-serif;
  --transition:   all 0.35s cubic-bezier(0.4,0,0.2,1);
}
*, *::before, *::after { margin:0; padding:0; box-sizing:border-box; }
html { scroll-behavior:smooth; font-size:16px; }
body {
  background-color: var(--bg-deep);
  color: var(--white-80);
  font-family: var(--font-body);
  line-height:1.65;
  overflow-x:hidden;
}
a { color:inherit; text-decoration:none; }
img { max-width:100%; }

/* ── Scrollbar ── */
::-webkit-scrollbar { width:6px; }
::-webkit-scrollbar-track { background:var(--bg-deep); }
::-webkit-scrollbar-thumb { background:var(--green-700); border-radius:3px; }

/* ============================================================
   UTILITY CLASSES
============================================================ */
.container { max-width:1200px; margin:0 auto; padding:0 28px; }
.section-tag {
  display:inline-block;
  font-family:var(--font-body);
  font-size:.75rem;
  font-weight:600;
  letter-spacing:.18em;
  text-transform:uppercase;
  color:var(--green-neon);
  background:rgba(0,255,135,.08);
  border:1px solid rgba(0,255,135,.22);
  padding:5px 18px;
  border-radius:99px;
  margin-bottom:18px;
}
.section-title {
  font-family:var(--font-head);
  font-size:clamp(2rem,4vw,3rem);
  font-weight:800;
  color:var(--white);
  line-height:1.15;
  margin-bottom:16px;
}
.section-sub {
  font-size:1.05rem;
  color:var(--white-60);
  max-width:580px;
  margin:0 auto 56px;
}
.text-center { text-align:center; }
.gradient-text {
  background: linear-gradient(135deg, var(--green-neon), var(--cyan));
  -webkit-background-clip:text;
  -webkit-text-fill-color:transparent;
  background-clip:text;
}

/* ── Glass Card ── */
.glass-card {
  background: var(--glass-bg);
  border: 1px solid var(--glass-border);
  border-radius: var(--radius-md);
  backdrop-filter: blur(20px);
  -webkit-backdrop-filter: blur(20px);
  box-shadow: var(--glass-shadow);
  transition: var(--transition);
}
.glass-card:hover {
  border-color: rgba(0,255,135,0.38);
  box-shadow: var(--glow-green), var(--glass-shadow);
  transform: translateY(-4px);
}

/* ── Buttons ── */
.btn {
  display:inline-flex; align-items:center; gap:8px;
  padding:13px 30px;
  font-family:var(--font-head);
  font-size:.95rem; font-weight:700;
  border-radius:99px;
  cursor:pointer;
  border:none;
  transition:var(--transition);
}
.btn-primary {
  background: linear-gradient(135deg, var(--green-neon), var(--cyan));
  color: var(--bg-deep);
  box-shadow: 0 4px 24px rgba(0,255,135,.35);
}
.btn-primary:hover {
  transform:translateY(-2px) scale(1.03);
  box-shadow: 0 8px 40px rgba(0,255,135,.55);
}
.btn-ghost {
  background: var(--white-10);
  color: var(--white);
  border: 1px solid var(--white-30);
}
.btn-ghost:hover {
  background: var(--white-06);
  border-color: var(--green-neon);
  color: var(--green-neon);
}
.btn-sm { padding:9px 22px; font-size:.85rem; }

/* ── Noise Overlay ── */
body::before {
  content:''; position:fixed; inset:0; z-index:0; pointer-events:none;
  background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 200 200' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.85' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='0.045'/%3E%3C/svg%3E");
  opacity:.5;
}

/* ============================================================
   NAV
============================================================ */
#navbar {
  position:fixed; top:0; left:0; right:0; z-index:1000;
  padding:18px 0;
  transition:var(--transition);
}
#navbar.scrolled {
  background:rgba(3,15,7,.85);
  backdrop-filter:blur(20px);
  border-bottom:1px solid var(--glass-border);
  padding:12px 0;
}
.nav-inner {
  display:flex; align-items:center; justify-content:space-between;
}
.nav-logo {
  font-family:var(--font-head);
  font-size:1.45rem; font-weight:800;
  display:flex; align-items:center; gap:10px;
}
.nav-logo .logo-icon {
  width:38px; height:38px;
  background: linear-gradient(135deg, var(--green-neon), var(--cyan));
  border-radius:10px;
  display:flex; align-items:center; justify-content:center;
  font-size:1.1rem; color:var(--bg-deep);
}
.nav-logo span { background: linear-gradient(135deg, var(--green-neon), var(--cyan));
  -webkit-background-clip:text; -webkit-text-fill-color:transparent; background-clip:text; }
.nav-links { display:flex; align-items:center; gap:32px; }
.nav-links a {
  font-size:.9rem; font-weight:500; color:var(--white-60);
  transition:var(--transition); position:relative;
}
.nav-links a::after {
  content:''; position:absolute; bottom:-4px; left:0; width:0; height:2px;
  background:var(--green-neon); border-radius:1px; transition:width .3s;
}
.nav-links a:hover { color:var(--white); }
.nav-links a:hover::after { width:100%; }
.nav-cta { display:flex; align-items:center; gap:12px; }
.hamburger { display:none; flex-direction:column; gap:5px; cursor:pointer; }
.hamburger span { width:24px; height:2px; background:var(--white-60); border-radius:1px; }

/* ============================================================
   HERO SECTION
============================================================ */
#hero {
  position:relative; min-height:100vh;
  display:flex; align-items:center;
  padding:120px 0 80px;
  overflow:hidden;
}
/* Animated background orbs */
.orb {
  position:absolute; border-radius:50%; filter:blur(80px); pointer-events:none;
}
.orb-1 {
  width:600px; height:600px;
  background: radial-gradient(circle, rgba(0,255,135,.15), transparent 70%);
  top:-100px; right:-100px;
  animation: floatOrb 8s ease-in-out infinite alternate;
}
.orb-2 {
  width:400px; height:400px;
  background: radial-gradient(circle, rgba(0,229,200,.12), transparent 70%);
  bottom:-80px; left:-80px;
  animation: floatOrb 10s ease-in-out infinite alternate-reverse;
}
.orb-3 {
  width:300px; height:300px;
  background: radial-gradient(circle, rgba(34,196,126,.1), transparent 70%);
  top:40%; left:40%;
  animation: floatOrb 12s ease-in-out infinite alternate;
}
@keyframes floatOrb {
  0%   { transform: translate(0,0) scale(1); }
  100% { transform: translate(30px,20px) scale(1.08); }
}

/* Grid lines */
.grid-bg {
  position:absolute; inset:0; pointer-events:none;
  background-image:
    linear-gradient(rgba(0,255,135,.04) 1px, transparent 1px),
    linear-gradient(90deg, rgba(0,255,135,.04) 1px, transparent 1px);
  background-size:60px 60px;
}

.hero-inner {
  display:grid; grid-template-columns:1fr 1fr; gap:60px; align-items:center;
  position:relative; z-index:2;
}
.hero-badge {
  display:inline-flex; align-items:center; gap:8px;
  background:rgba(0,255,135,.08); border:1px solid rgba(0,255,135,.25);
  color:var(--green-neon); font-size:.8rem; font-weight:600;
  padding:6px 16px; border-radius:99px; margin-bottom:24px;
  animation: fadeInUp .6s ease both;
}
.hero-badge .dot { width:7px; height:7px; background:var(--green-neon); border-radius:50%; animation:pulse 1.5s infinite; }
@keyframes pulse { 0%,100%{opacity:1;} 50%{opacity:.3;} }

.hero-title {
  font-family:var(--font-head); font-size:clamp(2.5rem,5.5vw,4.2rem);
  font-weight:800; line-height:1.08; color:var(--white);
  margin-bottom:22px;
  animation: fadeInUp .7s .1s ease both;
}
.hero-desc {
  font-size:1.1rem; color:var(--white-60); max-width:500px;
  margin-bottom:36px; line-height:1.75;
  animation: fadeInUp .7s .2s ease both;
}
.hero-btns {
  display:flex; gap:14px; flex-wrap:wrap;
  animation: fadeInUp .7s .3s ease both;
}
.hero-stats {
  display:flex; gap:32px; margin-top:48px;
  animation: fadeInUp .7s .4s ease both;
}
.stat-item .stat-num {
  font-family:var(--font-head); font-size:1.8rem; font-weight:800;
  background:linear-gradient(135deg,var(--green-neon),var(--cyan));
  -webkit-background-clip:text;-webkit-text-fill-color:transparent;background-clip:text;
}
.stat-item .stat-label { font-size:.8rem; color:var(--white-60); }

/* Hero Visual */
.hero-visual {
  position:relative; display:flex; justify-content:center; align-items:center;
  animation: fadeInRight .9s .2s ease both;
}
.phone-mockup {
  width:280px; height:540px;
  background: linear-gradient(160deg, rgba(255,255,255,.1), rgba(255,255,255,.03));
  border:1px solid rgba(255,255,255,.18);
  border-radius:40px;
  padding:18px;
  backdrop-filter:blur(12px);
  position:relative;
  box-shadow: 0 30px 80px rgba(0,0,0,.5), var(--glow-green);
  animation: float 6s ease-in-out infinite;
}
@keyframes float { 0%,100%{transform:translateY(0);} 50%{transform:translateY(-16px);} }
.phone-notch {
  width:80px; height:10px; background:rgba(255,255,255,.15);
  border-radius:99px; margin:0 auto 16px;
}
.phone-screen {
  background:var(--bg-mid);
  border-radius:26px; height:100%;
  display:flex; flex-direction:column; gap:10px;
  padding:14px; overflow:hidden;
}
.phone-screen .ps-header {
  display:flex; justify-content:space-between; align-items:center;
  font-size:.65rem; font-weight:600; color:var(--green-neon);
  font-family:var(--font-head);
}
.ps-score-card {
  background: linear-gradient(135deg, var(--green-900), #0a3d28);
  border-radius:14px; padding:14px; border:1px solid rgba(0,255,135,.2);
}
.ps-score-card .score-label { font-size:.6rem; color:var(--white-60); }
.ps-score-card .score-val {
  font-family:var(--font-head); font-size:1.5rem; font-weight:800;
  color:var(--green-neon);
}
.ps-mini-cards { display:grid; grid-template-columns:1fr 1fr; gap:8px; }
.ps-mini-card {
  background:rgba(255,255,255,.05); border-radius:10px;
  padding:10px; border:1px solid rgba(255,255,255,.08);
}
.ps-mini-card .mc-icon { font-size:.9rem; margin-bottom:4px; }
.ps-mini-card .mc-val { font-size:.75rem; font-weight:700; font-family:var(--font-head); color:var(--white); }
.ps-mini-card .mc-label { font-size:.55rem; color:var(--white-60); }
.ps-bar-section { flex:1; }
.ps-bar-section .bar-title { font-size:.6rem; color:var(--white-60); margin-bottom:8px; }
.bar-row { display:flex; align-items:center; gap:6px; margin-bottom:6px; }
.bar-row span { font-size:.5rem; color:var(--white-60); width:16px; }
.bar-track { flex:1; height:5px; background:rgba(255,255,255,.08); border-radius:3px; overflow:hidden; }
.bar-fill { height:100%; border-radius:3px; background:linear-gradient(90deg,var(--green-neon),var(--cyan)); }
.floating-badges {
  position:absolute;
}
.fbadge {
  background: rgba(3,15,7,.9);
  border:1px solid var(--glass-border);
  border-radius:12px; padding:10px 14px;
  backdrop-filter:blur(12px);
  display:flex; align-items:center; gap:8px;
  font-size:.75rem; font-weight:600;
  white-space:nowrap;
  box-shadow: var(--glass-shadow);
}
.fbadge-1 { top:40px; left:-80px; animation:float 5s ease-in-out infinite; }
.fbadge-2 { bottom:80px; right:-70px; animation:float 6s 1s ease-in-out infinite; }
.fbadge .fbi { font-size:1.2rem; }

@keyframes fadeInUp {
  from { opacity:0; transform:translateY(30px); }
  to   { opacity:1; transform:translateY(0); }
}
@keyframes fadeInRight {
  from { opacity:0; transform:translateX(40px); }
  to   { opacity:1; transform:translateX(0); }
}

/* ============================================================
   ABOUT SECTION
============================================================ */
#about {
  padding:100px 0;
  position:relative;
}
.about-inner {
  display:grid; grid-template-columns:1fr 1fr; gap:70px; align-items:center;
}
.about-vis {
  position:relative;
}
.about-main-card {
  background: linear-gradient(135deg, var(--bg-panel), rgba(13,79,60,.4));
  border:1px solid var(--glass-border);
  border-radius:var(--radius-lg);
  padding:36px;
  position:relative; overflow:hidden;
}
.about-main-card::before {
  content:''; position:absolute; top:0; left:0; right:0; height:3px;
  background:linear-gradient(90deg, var(--green-neon), var(--cyan));
}
.about-big-num {
  font-family:var(--font-head); font-size:5rem; font-weight:800;
  line-height:1; color:transparent;
  -webkit-text-stroke:2px rgba(0,255,135,.25);
  margin-bottom:8px;
}
.about-big-label { font-size:1rem; color:var(--white-60); margin-bottom:28px; }
.about-progress-item { margin-bottom:20px; }
.apm-top { display:flex; justify-content:space-between; font-size:.82rem; color:var(--white-80); margin-bottom:6px; }
.apm-bar { height:7px; background:rgba(255,255,255,.08); border-radius:3px; overflow:hidden; }
.apm-fill {
  height:100%; border-radius:3px;
  background:linear-gradient(90deg, var(--green-neon), var(--cyan));
  animation: barGrow 1.5s ease both;
}
@keyframes barGrow { from{width:0;} }
.about-side-cards {
  position:absolute; right:-30px; bottom:-30px;
  display:grid; gap:12px; width:200px;
}
.asc { background:rgba(255,255,255,.06); border:1px solid rgba(255,255,255,.1); border-radius:var(--radius-sm); padding:14px; }
.asc-icon { font-size:1.3rem; margin-bottom:6px; }
.asc-val { font-family:var(--font-head); font-size:1.1rem; font-weight:800; color:var(--green-neon); }
.asc-label { font-size:.7rem; color:var(--white-60); }

.about-content .section-title { text-align:left; }
.about-content .section-sub { text-align:left; margin:0 0 40px; }
.about-points { display:grid; gap:20px; }
.about-point {
  display:flex; gap:18px; align-items:flex-start;
  background:var(--glass-bg); border:1px solid var(--glass-border);
  border-radius:var(--radius-sm); padding:20px;
  transition:var(--transition);
}
.about-point:hover { border-color:rgba(0,255,135,.4); transform:translateX(6px); }
.ap-icon {
  width:44px; height:44px; border-radius:10px; flex-shrink:0;
  background:linear-gradient(135deg, rgba(0,255,135,.15), rgba(0,229,200,.1));
  border:1px solid rgba(0,255,135,.25);
  display:flex; align-items:center; justify-content:center; font-size:1.2rem;
}
.ap-title { font-family:var(--font-head); font-weight:700; color:var(--white); margin-bottom:4px; }
.ap-desc { font-size:.88rem; color:var(--white-60); }

/* ============================================================
   FEATURES SECTION
============================================================ */
#features {
  padding:100px 0;
  background: linear-gradient(180deg, transparent, rgba(13,79,60,.12), transparent);
  position:relative;
}
.features-grid {
  display:grid; grid-template-columns:repeat(3,1fr); gap:24px;
}
.feat-card {
  background:var(--glass-bg);
  border:1px solid var(--glass-border);
  border-radius:var(--radius-md);
  padding:32px 28px;
  transition:var(--transition);
  position:relative; overflow:hidden;
  cursor:default;
}
.feat-card::before {
  content:''; position:absolute; inset:0;
  background:linear-gradient(135deg, rgba(0,255,135,.05), transparent);
  opacity:0; transition:opacity .4s;
}
.feat-card:hover::before { opacity:1; }
.feat-card:hover { border-color:rgba(0,255,135,.4); transform:translateY(-6px); box-shadow:var(--glow-green); }
.feat-card.featured {
  grid-column:span 1;
  background:linear-gradient(135deg, rgba(0,255,135,.1), rgba(0,229,200,.06));
  border-color:rgba(0,255,135,.35);
}
.fc-num {
  font-family:var(--font-head); font-size:3.5rem; font-weight:800;
  color:rgba(0,255,135,.08); line-height:1; margin-bottom:-10px;
}
.fc-icon {
  width:52px; height:52px; border-radius:14px;
  background:linear-gradient(135deg, rgba(0,255,135,.18), rgba(0,229,200,.1));
  border:1px solid rgba(0,255,135,.3);
  display:flex; align-items:center; justify-content:center; font-size:1.45rem;
  margin-bottom:18px;
}
.fc-title {
  font-family:var(--font-head); font-size:1.1rem; font-weight:700;
  color:var(--white); margin-bottom:10px;
}
.fc-desc { font-size:.88rem; color:var(--white-60); line-height:1.65; margin-bottom:18px; }
.fc-tag {
  display:inline-block; font-size:.72rem; font-weight:600; letter-spacing:.1em;
  padding:3px 12px; border-radius:99px;
  background:rgba(0,255,135,.1); color:var(--green-neon);
  border:1px solid rgba(0,255,135,.2);
}

/* ============================================================
   DASHBOARD SECTION
============================================================ */
#dashboard {
  padding:100px 0;
  position:relative;
}
.dashboard-wrapper {
  background:var(--bg-mid);
  border:1px solid var(--glass-border);
  border-radius:var(--radius-xl);
  overflow:hidden;
  box-shadow:0 40px 100px rgba(0,0,0,.5), var(--glow-green);
}
/* Dashboard Top Bar */
.db-topbar {
  background: linear-gradient(90deg, var(--bg-panel), rgba(13,79,60,.6));
  border-bottom:1px solid var(--glass-border);
  padding:16px 28px;
  display:flex; align-items:center; justify-content:space-between;
}
.db-topbar-title { font-family:var(--font-head); font-size:1rem; font-weight:700; color:var(--white); display:flex; align-items:center; gap:10px; }
.db-topbar-title .dot { width:8px; height:8px; background:var(--green-neon); border-radius:50%; }
.db-topbar-right { display:flex; align-items:center; gap:16px; font-size:.82rem; color:var(--white-60); }
.db-notif { width:34px; height:34px; border-radius:10px; background:rgba(255,255,255,.06); border:1px solid rgba(255,255,255,.1); display:flex; align-items:center; justify-content:center; position:relative; }
.db-notif::after { content:'3'; position:absolute; top:-5px; right:-5px; width:16px; height:16px; background:var(--coral); border-radius:50%; font-size:.6rem; font-weight:700; color:#fff; display:flex; align-items:center; justify-content:center; }
.db-avatar { width:34px; height:34px; border-radius:50%; background:linear-gradient(135deg,var(--green-neon),var(--cyan)); display:flex; align-items:center; justify-content:center; font-size:.75rem; font-weight:800; color:var(--bg-deep); }
/* Dashboard layout */
.db-body {
  display:grid; grid-template-columns:220px 1fr; min-height:540px;
}
.db-sidebar {
  background:rgba(0,0,0,.25); border-right:1px solid var(--glass-border); padding:24px 16px;
}
.db-sidebar-user { text-align:center; padding-bottom:22px; border-bottom:1px solid var(--glass-border); margin-bottom:20px; }
.db-user-ava { width:64px; height:64px; background:linear-gradient(135deg,var(--green-900),var(--green-500)); border-radius:50%; margin:0 auto 10px; display:flex; align-items:center; justify-content:center; font-size:1.5rem; font-weight:800; color:#fff; border:3px solid var(--green-neon); }
.db-user-name { font-family:var(--font-head); font-size:.9rem; font-weight:700; color:var(--white); }
.db-user-level { font-size:.72rem; color:var(--green-neon); background:rgba(0,255,135,.1); padding:2px 10px; border-radius:99px; display:inline-block; margin-top:4px; }
.db-nav-item { display:flex; align-items:center; gap:10px; padding:10px 14px; border-radius:10px; font-size:.85rem; color:var(--white-60); cursor:pointer; transition:var(--transition); margin-bottom:4px; }
.db-nav-item:hover, .db-nav-item.active { background:rgba(0,255,135,.1); color:var(--green-neon); border:1px solid rgba(0,255,135,.2); }
.db-nav-item.active { border-color:rgba(0,255,135,.3); }
.db-nav-item i { width:16px; text-align:center; }
/* Dashboard main */
.db-main { padding:28px; display:flex; flex-direction:column; gap:24px; }
.db-kpis { display:grid; grid-template-columns:repeat(4,1fr); gap:14px; }
.kpi-card {
  background:var(--glass-bg); border:1px solid var(--glass-border);
  border-radius:var(--radius-sm); padding:18px; position:relative; overflow:hidden;
}
.kpi-card::after {
  content:''; position:absolute; bottom:0; left:0; right:0; height:3px;
}
.kpi-card.kpi-green::after { background:linear-gradient(90deg,var(--green-neon),var(--cyan)); }
.kpi-card.kpi-gold::after { background:linear-gradient(90deg,var(--gold),#ffaa00); }
.kpi-card.kpi-coral::after { background:linear-gradient(90deg,var(--coral),#ff9a6b); }
.kpi-card.kpi-cyan::after { background:linear-gradient(90deg,var(--cyan),#00b4d8); }
.kpi-icon { font-size:1.2rem; margin-bottom:8px; }
.kpi-val { font-family:var(--font-head); font-size:1.5rem; font-weight:800; color:var(--white); }
.kpi-label { font-size:.72rem; color:var(--white-60); margin-top:2px; }
.kpi-delta { font-size:.7rem; color:var(--green-neon); margin-top:4px; }
/* DB charts row */
.db-charts { display:grid; grid-template-columns:1.5fr 1fr; gap:16px; }
.db-chart-card { background:var(--glass-bg); border:1px solid var(--glass-border); border-radius:var(--radius-sm); padding:20px; }
.dcc-title { font-family:var(--font-head); font-size:.85rem; font-weight:700; color:var(--white); margin-bottom:16px; display:flex; justify-content:space-between; align-items:center; }
.dcc-badge { font-size:.65rem; padding:3px 10px; border-radius:99px; background:rgba(0,255,135,.1); color:var(--green-neon); }
/* SVG Chart */
.chart-svg { width:100%; }
/* Quick actions */
.db-actions { display:flex; gap:12px; }
.qa-btn {
  flex:1; background:var(--glass-bg); border:1px solid var(--glass-border);
  border-radius:var(--radius-sm); padding:14px;
  display:flex; flex-direction:column; align-items:center; gap:6px;
  cursor:pointer; transition:var(--transition); text-align:center;
}
.qa-btn:hover { border-color:rgba(0,255,135,.4); background:rgba(0,255,135,.06); }
.qa-btn i { font-size:1.2rem; color:var(--green-neon); }
.qa-btn span { font-size:.75rem; color:var(--white-60); }

/* ============================================================
   SCAN PAGE
============================================================ */
#scan {
  padding:100px 0;
  background:linear-gradient(180deg, rgba(0,255,135,.04), transparent);
}
.scan-inner {
  display:grid; grid-template-columns:1fr 1fr; gap:60px; align-items:center;
}
.scan-device {
  position:relative; display:flex; justify-content:center;
}
.scan-frame {
  width:320px; height:380px;
  background: linear-gradient(160deg, rgba(0,255,135,.08), rgba(0,229,200,.04));
  border:2px solid rgba(0,255,135,.3);
  border-radius:var(--radius-lg);
  position:relative; overflow:hidden;
  display:flex; align-items:center; justify-content:center;
}
.scan-corners span {
  position:absolute; width:24px; height:24px;
  border-color:var(--green-neon); border-style:solid;
}
.scan-corners span:nth-child(1) { top:12px; left:12px; border-width:3px 0 0 3px; border-radius:4px 0 0 0; }
.scan-corners span:nth-child(2) { top:12px; right:12px; border-width:3px 3px 0 0; border-radius:0 4px 0 0; }
.scan-corners span:nth-child(3) { bottom:12px; left:12px; border-width:0 0 3px 3px; border-radius:0 0 0 4px; }
.scan-corners span:nth-child(4) { bottom:12px; right:12px; border-width:0 3px 3px 0; border-radius:0 0 4px 0; }
.scan-laser {
  position:absolute; top:0; left:0; right:0; height:2px;
  background:linear-gradient(90deg, transparent, var(--green-neon), transparent);
  box-shadow:0 0 20px var(--green-neon);
  animation:scanLine 2.5s ease-in-out infinite;
}
@keyframes scanLine {
  0%   { top:15%; }
  50%  { top:85%; }
  100% { top:15%; }
}
.scan-object {
  font-size:5rem; filter:drop-shadow(0 0 30px rgba(0,255,135,.5));
  animation:pulse 2s infinite;
}
.scan-result-overlay {
  position:absolute; bottom:16px; left:16px; right:16px;
  background:rgba(3,15,7,.9); border:1px solid var(--green-neon);
  border-radius:12px; padding:14px;
  animation:resultSlide .6s ease;
}
@keyframes resultSlide { from{transform:translateY(20px);opacity:0;} to{transform:translateY(0);opacity:1;} }
.sro-tag { font-size:.65rem; color:var(--green-neon); font-weight:600; letter-spacing:.1em; margin-bottom:4px; }
.sro-name { font-family:var(--font-head); font-size:.95rem; font-weight:700; color:var(--white); }
.sro-pts { font-size:.75rem; color:var(--cyan); }

.scan-content .section-title { text-align:left; }
.scan-content .section-sub { text-align:left; margin:0 0 36px; }
.scan-steps { display:grid; gap:16px; }
.scan-step {
  display:flex; gap:16px; align-items:flex-start;
  background:var(--glass-bg); border:1px solid var(--glass-border);
  border-radius:var(--radius-sm); padding:18px;
}
.ss-num {
  width:32px; height:32px; border-radius:50%; flex-shrink:0;
  background:linear-gradient(135deg,var(--green-neon),var(--cyan));
  color:var(--bg-deep); font-family:var(--font-head); font-size:.8rem; font-weight:800;
  display:flex; align-items:center; justify-content:center;
}
.ss-title { font-family:var(--font-head); font-weight:700; color:var(--white); font-size:.9rem; margin-bottom:4px; }
.ss-desc { font-size:.82rem; color:var(--white-60); }
/* AI types */
.ai-types { display:flex; gap:8px; flex-wrap:wrap; margin-top:24px; }
.ai-type-tag {
  background:rgba(0,255,135,.07); border:1px solid rgba(0,255,135,.2);
  color:var(--green-neon); font-size:.75rem; padding:5px 14px; border-radius:99px;
}

/* ============================================================
   REWARDS SECTION
============================================================ */
#rewards {
  padding:100px 0;
  background:linear-gradient(180deg, transparent, rgba(0,229,200,.04), transparent);
}
.rewards-inner { display:grid; grid-template-columns:1fr 1fr; gap:60px; align-items:start; }
.wallet-card {
  background: linear-gradient(135deg, #0d4f3c, #094028);
  border:1px solid rgba(0,255,135,.35);
  border-radius:var(--radius-lg);
  padding:32px;
  position:relative; overflow:hidden;
  box-shadow:var(--glow-green);
}
.wallet-card::before {
  content:''; position:absolute; top:-60px; right:-60px;
  width:200px; height:200px; border-radius:50%;
  background:rgba(0,255,135,.07); border:1px solid rgba(0,255,135,.1);
}
.wc-label { font-size:.75rem; color:var(--green-neon); letter-spacing:.1em; font-weight:600; margin-bottom:8px; }
.wc-balance { font-family:var(--font-head); font-size:3rem; font-weight:800; color:var(--white); display:flex; align-items:baseline; gap:8px; }
.wc-currency { font-size:1.2rem; color:var(--green-neon); }
.wc-sub { font-size:.85rem; color:var(--white-60); margin-top:6px; margin-bottom:28px; }
.wc-actions { display:flex; gap:12px; }
.wca { flex:1; background:rgba(255,255,255,.1); border:1px solid rgba(255,255,255,.15); border-radius:12px; padding:12px; text-align:center; cursor:pointer; transition:var(--transition); }
.wca:hover { background:rgba(0,255,135,.15); border-color:rgba(0,255,135,.4); }
.wca i { font-size:1.1rem; color:var(--green-neon); display:block; margin-bottom:6px; }
.wca span { font-size:.75rem; color:var(--white-80); }
.wc-history { margin-top:24px; }
.wch-title { font-size:.75rem; color:var(--white-60); margin-bottom:12px; font-weight:600; }
.wch-item { display:flex; justify-content:space-between; align-items:center; padding:10px 0; border-bottom:1px solid rgba(255,255,255,.05); font-size:.82rem; }
.wch-item .wch-label { color:var(--white-80); }
.wch-item .wch-val.green { color:var(--green-neon); }
.wch-item .wch-val.coral { color:var(--coral); }

.redeem-section .section-title { text-align:left; }
.redeem-grid { display:grid; grid-template-columns:1fr 1fr; gap:14px; margin-top:28px; }
.redeem-card {
  background:var(--glass-bg); border:1px solid var(--glass-border);
  border-radius:var(--radius-md); padding:20px; transition:var(--transition); cursor:pointer;
}
.redeem-card:hover { border-color:rgba(0,255,135,.4); transform:translateY(-4px); }
.rc-icon { font-size:2rem; margin-bottom:12px; }
.rc-title { font-family:var(--font-head); font-size:.9rem; font-weight:700; color:var(--white); margin-bottom:6px; }
.rc-pts { font-size:.78rem; color:var(--green-neon); margin-bottom:10px; }
.rc-desc { font-size:.77rem; color:var(--white-60); }

/* ============================================================
   MAP SECTION
============================================================ */
#map-section {
  padding:100px 0;
}
.map-wrapper {
  display:grid; grid-template-columns:1fr 280px; gap:24px;
}
.map-area {
  background:var(--bg-panel);
  border:1px solid var(--glass-border);
  border-radius:var(--radius-lg);
  position:relative; overflow:hidden; min-height:400px;
  display:flex; align-items:center; justify-content:center;
}
.map-grid {
  position:absolute; inset:0;
  background-image:
    linear-gradient(rgba(0,255,135,.06) 1px, transparent 1px),
    linear-gradient(90deg, rgba(0,255,135,.06) 1px, transparent 1px);
  background-size:40px 40px;
}
.map-center-dot {
  position:absolute; width:16px; height:16px; background:var(--green-neon);
  border-radius:50%; border:3px solid var(--bg-deep);
  box-shadow: 0 0 0 10px rgba(0,255,135,.15), 0 0 0 20px rgba(0,255,135,.08);
  animation:mapPulse 2s infinite;
}
@keyframes mapPulse {
  0%,100% { box-shadow:0 0 0 10px rgba(0,255,135,.15),0 0 0 20px rgba(0,255,135,.08); }
  50%      { box-shadow:0 0 0 16px rgba(0,255,135,.08),0 0 0 28px rgba(0,255,135,.04); }
}
.map-pin {
  position:absolute;
  display:flex; flex-direction:column; align-items:center; gap:0; cursor:pointer;
}
.map-pin .pin-icon {
  width:32px; height:32px; border-radius:50% 50% 50% 0; transform:rotate(-45deg);
  background:linear-gradient(135deg,var(--green-neon),var(--cyan));
  display:flex; align-items:center; justify-content:center;
}
.map-pin .pin-icon span { transform:rotate(45deg); font-size:.85rem; }
.map-pin .pin-label {
  background:rgba(3,15,7,.9); border:1px solid var(--glass-border);
  border-radius:6px; padding:4px 10px; font-size:.65rem; color:var(--white-80);
  white-space:nowrap; margin-top:6px;
}
.map-overlay {
  position:absolute; top:20px; left:20px;
  background:rgba(3,15,7,.85); border:1px solid var(--glass-border);
  border-radius:12px; padding:12px 16px; backdrop-filter:blur(10px);
}
.mo-title { font-family:var(--font-head); font-size:.8rem; font-weight:700; color:var(--white); margin-bottom:4px; }
.mo-stat { font-size:.7rem; color:var(--green-neon); }
.map-sidebar { display:flex; flex-direction:column; gap:14px; }
.map-center-card {
  background:var(--glass-bg); border:1px solid var(--glass-border);
  border-radius:var(--radius-md); padding:18px;
}
.mcc-header { display:flex; align-items:center; gap:10px; margin-bottom:12px; }
.mcc-icon { width:36px; height:36px; border-radius:10px; background:linear-gradient(135deg,rgba(0,255,135,.15),rgba(0,229,200,.1)); display:flex; align-items:center; justify-content:center; font-size:1rem; }
.mcc-name { font-family:var(--font-head); font-size:.88rem; font-weight:700; color:var(--white); }
.mcc-dist { font-size:.7rem; color:var(--green-neon); }
.mcc-tags { display:flex; gap:6px; flex-wrap:wrap; margin-bottom:12px; }
.mcc-tag { font-size:.65rem; padding:2px 8px; border-radius:99px; background:rgba(0,255,135,.08); color:var(--green-neon); border:1px solid rgba(0,255,135,.2); }
.mcc-btn { width:100%; padding:8px; background:linear-gradient(135deg,var(--green-neon),var(--cyan)); color:var(--bg-deep); border:none; border-radius:8px; font-family:var(--font-head); font-weight:700; font-size:.78rem; cursor:pointer; }

/* ============================================================
   SMART DUSTBIN
============================================================ */
#dustbin {
  padding:100px 0;
  background:linear-gradient(180deg, transparent, rgba(13,79,60,.12), transparent);
}
.dustbin-inner { display:grid; grid-template-columns:1fr 1fr; gap:60px; align-items:center; }
.dustbin-visual { display:flex; justify-content:center; }
.dustbin-unit {
  width:260px; position:relative; text-align:center;
}
.du-bin {
  width:200px; height:240px; margin:0 auto 20px;
  background: linear-gradient(160deg, rgba(0,255,135,.12), rgba(0,229,200,.05));
  border:2px solid rgba(0,255,135,.3);
  border-radius:16px 16px 28px 28px;
  position:relative; overflow:hidden; cursor:pointer;
  transition:var(--transition);
  box-shadow:var(--glow-green);
}
.du-bin:hover { box-shadow:0 0 60px rgba(0,255,135,.4); border-color:var(--green-neon); }
.du-bin-top {
  height:28px;
  background:linear-gradient(135deg, rgba(0,255,135,.25), rgba(0,229,200,.15));
  border-bottom:1px solid rgba(0,255,135,.3);
  display:flex; align-items:center; justify-content:center;
  font-size:.7rem; color:var(--green-neon); font-weight:600; letter-spacing:.08em;
}
.du-fill-track {
  margin:16px; height:160px; background:rgba(0,0,0,.3);
  border-radius:8px; position:relative; overflow:hidden;
}
.du-fill-bar {
  position:absolute; bottom:0; left:0; right:0; height:68%;
  background:linear-gradient(0deg, var(--green-900), var(--green-500));
  border-radius:8px;
  display:flex; align-items:flex-end; justify-content:center; padding-bottom:8px;
  animation:fillRise 1.5s ease both;
}
@keyframes fillRise { from{height:0;} }
.du-fill-bar span { font-size:.7rem; color:rgba(255,255,255,.7); font-weight:700; }
.du-level-marks { position:absolute; top:0; left:0; right:0; height:100%; display:flex; flex-direction:column; justify-content:space-around; padding:4px 0; }
.du-level-marks span { font-size:.55rem; color:rgba(255,255,255,.2); text-align:right; padding-right:6px; border-top:1px dashed rgba(255,255,255,.1); }
.du-status {
  display:flex; align-items:center; justify-content:center; gap:8px;
  font-size:.8rem; color:var(--green-neon); font-weight:600;
}
.du-status .ds-dot { width:8px; height:8px; background:var(--green-neon); border-radius:50%; animation:pulse 1.5s infinite; }
.du-signals {
  position:absolute; top:-20px; left:-20px; right:-20px; bottom:-20px;
  pointer-events:none;
}
.du-signals::before, .du-signals::after {
  content:''; position:absolute; inset:20px; border-radius:50%;
  border:1px solid rgba(0,255,135,.15);
  animation:signalExpand 2s ease infinite;
}
.du-signals::after { animation-delay:1s; }
@keyframes signalExpand { 0%{transform:scale(.8);opacity:.5;} 100%{transform:scale(1.3);opacity:0;} }
.dustbin-content .section-title { text-align:left; }
.dustbin-content .section-sub { text-align:left; margin:0 0 36px; }
.db-stats-grid { display:grid; grid-template-columns:1fr 1fr; gap:14px; margin-bottom:28px; }
.db-stat-card {
  background:var(--glass-bg); border:1px solid var(--glass-border);
  border-radius:var(--radius-sm); padding:18px; text-align:center;
}
.dbs-icon { font-size:1.5rem; margin-bottom:8px; }
.dbs-val { font-family:var(--font-head); font-size:1.3rem; font-weight:800; color:var(--white); }
.dbs-label { font-size:.72rem; color:var(--white-60); }
.iot-tags { display:flex; gap:8px; flex-wrap:wrap; }
.iot-tag { display:flex; align-items:center; gap:6px; font-size:.78rem; color:var(--white-60); background:var(--glass-bg); border:1px solid var(--glass-border); padding:7px 14px; border-radius:99px; }
.iot-tag i { color:var(--green-neon); }

/* ============================================================
   LEADERBOARD
============================================================ */
#leaderboard {
  padding:100px 0;
}
.leaderboard-inner { display:grid; grid-template-columns:1.2fr 1fr; gap:40px; }
.lb-table {
  background:var(--glass-bg); border:1px solid var(--glass-border);
  border-radius:var(--radius-lg); overflow:hidden;
}
.lb-header {
  background:linear-gradient(90deg, rgba(0,255,135,.1), rgba(0,229,200,.06));
  padding:18px 24px; display:grid; grid-template-columns:50px 1fr 100px 80px;
  font-size:.72rem; font-weight:600; color:var(--white-60); letter-spacing:.1em; text-transform:uppercase;
}
.lb-row {
  padding:14px 24px; display:grid; grid-template-columns:50px 1fr 100px 80px;
  align-items:center; border-top:1px solid rgba(255,255,255,.05);
  transition:var(--transition); cursor:pointer;
}
.lb-row:hover { background:rgba(0,255,135,.04); }
.lb-row.top1 { background:linear-gradient(90deg, rgba(245,200,66,.05), transparent); }
.lb-row.top2 { background:linear-gradient(90deg, rgba(180,180,180,.04), transparent); }
.lb-row.top3 { background:linear-gradient(90deg, rgba(205,127,50,.04), transparent); }
.lb-rank { font-family:var(--font-head); font-size:1rem; font-weight:800; }
.rank-1 { color:var(--gold); }
.rank-2 { color:#c0c0c0; }
.rank-3 { color:#cd7f32; }
.lb-user { display:flex; align-items:center; gap:12px; }
.lb-ava { width:36px; height:36px; border-radius:50%; display:flex; align-items:center; justify-content:center; font-size:.8rem; font-weight:700; color:#fff; }
.lb-user-name { font-weight:600; font-size:.88rem; color:var(--white); }
.lb-user-loc { font-size:.7rem; color:var(--white-60); }
.lb-pts { font-family:var(--font-head); font-size:.9rem; font-weight:700; color:var(--green-neon); }
.lb-badge-img { font-size:1.2rem; }

.badges-section .section-title { text-align:left; }
.badges-grid { display:grid; grid-template-columns:repeat(2,1fr); gap:14px; margin-top:24px; }
.badge-card {
  background:var(--glass-bg); border:1px solid var(--glass-border);
  border-radius:var(--radius-md); padding:20px; text-align:center;
  transition:var(--transition);
}
.badge-card:hover { border-color:rgba(245,200,66,.4); transform:scale(1.04); }
.badge-card.locked { opacity:.45; }
.bc-icon { font-size:2.2rem; margin-bottom:8px; }
.bc-name { font-family:var(--font-head); font-size:.85rem; font-weight:700; color:var(--white); margin-bottom:4px; }
.bc-desc { font-size:.72rem; color:var(--white-60); }
.bc-progress { margin-top:10px; height:4px; background:rgba(255,255,255,.08); border-radius:2px; overflow:hidden; }
.bc-progress-fill { height:100%; background:linear-gradient(90deg,var(--gold),#ffaa00); border-radius:2px; }

/* ============================================================
   PROFILE
============================================================ */
#profile {
  padding:100px 0;
  background:linear-gradient(180deg, rgba(0,255,135,.04), transparent);
}
.profile-inner { display:grid; grid-template-columns:320px 1fr; gap:32px; }
.profile-card {
  background:var(--glass-bg); border:1px solid var(--glass-border);
  border-radius:var(--radius-lg); padding:32px; text-align:center;
}
.pc-avatar {
  width:90px; height:90px;
  background:linear-gradient(135deg,var(--green-900),var(--green-500));
  border-radius:50%; margin:0 auto 16px;
  display:flex; align-items:center; justify-content:center;
  font-size:2rem; font-weight:800; color:#fff;
  border:4px solid var(--green-neon);
  box-shadow:var(--glow-green);
}
.pc-name { font-family:var(--font-head); font-size:1.3rem; font-weight:800; color:var(--white); }
.pc-tagline { font-size:.82rem; color:var(--green-neon); margin:4px 0 20px; }
.eco-score-ring {
  width:120px; height:120px; margin:0 auto 20px; position:relative;
}
.eco-score-ring svg { transform:rotate(-90deg); }
.eco-score-ring .ring-bg { fill:none; stroke:rgba(255,255,255,.08); stroke-width:8; }
.eco-score-ring .ring-fill {
  fill:none; stroke:url(#scoreGrad); stroke-width:8;
  stroke-linecap:round;
  stroke-dasharray:283; stroke-dashoffset:57;
  transition:stroke-dashoffset 1.5s ease;
}
.eco-score-num {
  position:absolute; inset:0;
  display:flex; flex-direction:column; align-items:center; justify-content:center;
}
.eco-score-num .esn-val { font-family:var(--font-head); font-size:1.6rem; font-weight:800; color:var(--white); }
.eco-score-num .esn-label { font-size:.6rem; color:var(--green-neon); }
.pc-stats { display:grid; grid-template-columns:1fr 1fr; gap:10px; margin-bottom:20px; }
.pcs { background:rgba(255,255,255,.05); border:1px solid rgba(255,255,255,.08); border-radius:10px; padding:12px; }
.pcs-val { font-family:var(--font-head); font-size:1rem; font-weight:800; color:var(--white); }
.pcs-label { font-size:.65rem; color:var(--white-60); }
.profile-badges { display:flex; gap:8px; flex-wrap:wrap; justify-content:center; }
.pb { width:36px; height:36px; border-radius:50%; background:rgba(255,255,255,.08); display:flex; align-items:center; justify-content:center; font-size:1.1rem; border:1px solid rgba(255,255,255,.12); cursor:pointer; transition:var(--transition); }
.pb:hover { border-color:var(--gold); transform:scale(1.15); }

.profile-activity { display:flex; flex-direction:column; gap:20px; }
.pa-section {
  background:var(--glass-bg); border:1px solid var(--glass-border);
  border-radius:var(--radius-md); padding:24px;
}
.pas-title { font-family:var(--font-head); font-size:.9rem; font-weight:700; color:var(--white); margin-bottom:16px; display:flex; align-items:center; gap:8px; }
.pas-title i { color:var(--green-neon); }
.timeline { display:flex; flex-direction:column; gap:0; }
.tl-item { display:flex; gap:16px; padding-bottom:20px; position:relative; }
.tl-item::before { content:''; position:absolute; left:15px; top:28px; width:1px; height:calc(100% - 8px); background:rgba(255,255,255,.08); }
.tl-item:last-child::before { display:none; }
.tl-dot { width:30px; height:30px; border-radius:50%; flex-shrink:0; display:flex; align-items:center; justify-content:center; font-size:.8rem; }
.tl-dot.green { background:rgba(0,255,135,.15); border:1px solid rgba(0,255,135,.3); }
.tl-dot.cyan  { background:rgba(0,229,200,.12); border:1px solid rgba(0,229,200,.3); }
.tl-dot.gold  { background:rgba(245,200,66,.12); border:1px solid rgba(245,200,66,.3); }
.tl-content .tlc-title { font-size:.88rem; font-weight:600; color:var(--white); }
.tl-content .tlc-sub   { font-size:.75rem; color:var(--white-60); }
.tl-content .tlc-pts   { font-size:.75rem; color:var(--green-neon); margin-top:2px; }

/* Achievements list */
.ach-list { display:flex; flex-direction:column; gap:10px; }
.ach-item { display:flex; align-items:center; gap:14px; }
.ach-icon { font-size:1.4rem; width:40px; text-align:center; }
.ach-info .ai-title { font-size:.88rem; font-weight:600; color:var(--white); }
.ach-info .ai-desc { font-size:.75rem; color:var(--white-60); }
.ach-pts { margin-left:auto; font-family:var(--font-head); font-size:.9rem; font-weight:800; color:var(--gold); }

/* ============================================================
   PLASTIC CREDIT ECONOMY (UNIQUE FEATURE)
============================================================ */
#economy {
  padding:100px 0;
  background:linear-gradient(180deg, transparent, rgba(0,229,200,.04), transparent);
}
.economy-inner { display:grid; grid-template-columns:1fr 1fr; gap:60px; align-items:center; }
.economy-content .section-title { text-align:left; }
.economy-content .section-sub { text-align:left; margin:0 0 36px; }
.economy-flow { display:flex; flex-direction:column; gap:0; }
.ef-step {
  display:flex; align-items:flex-start; gap:18px; padding-bottom:24px; position:relative;
}
.ef-step::before { content:''; position:absolute; left:23px; top:46px; width:2px; height:calc(100% - 26px); background:linear-gradient(180deg,var(--green-neon),transparent); }
.ef-step:last-child::before { display:none; }
.ef-icon {
  width:46px; height:46px; border-radius:50%; flex-shrink:0;
  background:linear-gradient(135deg,var(--green-neon),var(--cyan));
  color:var(--bg-deep); display:flex; align-items:center; justify-content:center;
  font-size:1.1rem; font-weight:800;
}
.ef-title { font-family:var(--font-head); font-weight:700; color:var(--white); margin-bottom:4px; }
.ef-desc { font-size:.85rem; color:var(--white-60); }
.economy-vis { position:relative; }
.eco-card-stack { position:relative; height:340px; }
.ecc {
  position:absolute; width:280px;
  background: linear-gradient(135deg, var(--bg-panel), rgba(0,79,60,.6));
  border:1px solid rgba(0,255,135,.25);
  border-radius:var(--radius-md); padding:24px;
  transition:var(--transition);
}
.ecc-1 { top:0; left:0; transform:rotate(-6deg); }
.ecc-2 { top:20px; left:20px; transform:rotate(-2deg); }
.ecc-3 { top:40px; left:40px; transform:rotate(0deg); box-shadow:var(--glow-green); }
.ecc:hover { transform:rotate(0) translateY(-8px) !important; z-index:10; }
.ecc-header { display:flex; justify-content:space-between; align-items:center; margin-bottom:20px; }
.ecc-logo { font-family:var(--font-head); font-size:.8rem; font-weight:800; color:var(--green-neon); }
.ecc-type { font-size:.65rem; color:var(--white-60); }
.ecc-num { font-family:var(--font-head); font-size:1.1rem; font-weight:700; letter-spacing:.15em; color:var(--white); margin-bottom:20px; }
.ecc-bottom { display:flex; justify-content:space-between; align-items:flex-end; }
.ecc-bal-label { font-size:.6rem; color:var(--white-60); }
.ecc-bal { font-family:var(--font-head); font-size:1.2rem; font-weight:800; color:var(--green-neon); }
.ecc-chip { width:32px; height:24px; background:linear-gradient(135deg,var(--gold),#ffaa00); border-radius:4px; }

/* ============================================================
   CONTACT & FOOTER
============================================================ */
#contact { padding:100px 0 0; }
.contact-inner { display:grid; grid-template-columns:1fr 1fr; gap:60px; }
.contact-info .section-title { text-align:left; }
.contact-info .section-sub { text-align:left; margin:0 0 36px; }
.contact-items { display:flex; flex-direction:column; gap:18px; margin-bottom:36px; }
.ci-item { display:flex; align-items:center; gap:16px; }
.ci-icon { width:44px; height:44px; border-radius:12px; background:linear-gradient(135deg,rgba(0,255,135,.12),rgba(0,229,200,.08)); border:1px solid rgba(0,255,135,.2); display:flex; align-items:center; justify-content:center; font-size:1.1rem; color:var(--green-neon); flex-shrink:0; }
.ci-text .cit-label { font-size:.75rem; color:var(--white-60); }
.ci-text .cit-val { font-size:.9rem; font-weight:600; color:var(--white); }
.social-links { display:flex; gap:12px; }
.sl { width:42px; height:42px; border-radius:12px; background:var(--glass-bg); border:1px solid var(--glass-border); display:flex; align-items:center; justify-content:center; font-size:1rem; color:var(--white-60); transition:var(--transition); cursor:pointer; }
.sl:hover { background:rgba(0,255,135,.1); border-color:rgba(0,255,135,.35); color:var(--green-neon); transform:translateY(-3px); }
/* Contact Form */
.contact-form-wrap {
  background:var(--glass-bg); border:1px solid var(--glass-border);
  border-radius:var(--radius-lg); padding:36px;
}
.cf-title { font-family:var(--font-head); font-size:1.2rem; font-weight:700; color:var(--white); margin-bottom:24px; }
.cf-grid { display:grid; grid-template-columns:1fr 1fr; gap:16px; margin-bottom:16px; }
.cf-field { display:flex; flex-direction:column; gap:7px; margin-bottom:16px; }
.cf-field label { font-size:.78rem; color:var(--white-60); font-weight:600; }
.cf-field input, .cf-field textarea, .cf-field select {
  background:rgba(255,255,255,.05); border:1px solid rgba(255,255,255,.12);
  border-radius:10px; padding:12px 16px;
  color:var(--white); font-family:var(--font-body); font-size:.88rem;
  outline:none; transition:var(--transition);
  resize:none;
}
.cf-field input:focus, .cf-field textarea:focus, .cf-field select:focus {
  border-color:rgba(0,255,135,.5); box-shadow:0 0 0 3px rgba(0,255,135,.1);
}
.cf-field textarea { min-height:110px; }
.cf-grid .cf-field { margin-bottom:0; }
/* Footer */
footer {
  margin-top:80px;
  border-top:1px solid var(--glass-border);
  padding:60px 0 32px;
}
.footer-inner {
  display:grid; grid-template-columns:2fr 1fr 1fr 1fr; gap:40px;
  margin-bottom:40px;
}
.footer-brand .nav-logo { margin-bottom:14px; }
.footer-brand p { font-size:.85rem; color:var(--white-60); max-width:260px; line-height:1.7; }
.footer-col-title { font-family:var(--font-head); font-size:.85rem; font-weight:700; color:var(--white); margin-bottom:14px; }
.footer-links { display:flex; flex-direction:column; gap:10px; }
.footer-links a { font-size:.82rem; color:var(--white-60); transition:var(--transition); }
.footer-links a:hover { color:var(--green-neon); }
.footer-bottom {
  border-top:1px solid rgba(255,255,255,.06);
  padding-top:24px; display:flex; justify-content:space-between; align-items:center;
  font-size:.78rem; color:var(--white-60);
}
.footer-bottom span { color:var(--green-neon); }

/* ============================================================
   ECO MSG TICKER
============================================================ */
.eco-ticker {
  background:linear-gradient(90deg, rgba(0,255,135,.08), rgba(0,229,200,.05));
  border-top:1px solid rgba(0,255,135,.12);
  border-bottom:1px solid rgba(0,255,135,.12);
  padding:10px 0; overflow:hidden; white-space:nowrap;
}
.eco-ticker-inner {
  display:inline-flex; gap:48px;
  animation:ticker 30s linear infinite;
}
@keyframes ticker { 0%{transform:translateX(0);} 100%{transform:translateX(-50%);} }
.eco-ticker-item {
  display:inline-flex; align-items:center; gap:8px;
  font-size:.78rem; color:var(--green-neon); font-weight:600;
}
.eco-ticker-item i { opacity:.7; }

/* ============================================================
   RESPONSIVE
============================================================ */
@media(max-width:1024px) {
  .hero-inner, .about-inner, .scan-inner, .rewards-inner, .dustbin-inner, .economy-inner, .contact-inner { grid-template-columns:1fr; gap:50px; }
  .features-grid { grid-template-columns:1fr 1fr; }
  .db-body { grid-template-columns:1fr; }
  .db-sidebar { display:none; }
  .leaderboard-inner, .profile-inner { grid-template-columns:1fr; }
  .footer-inner { grid-template-columns:1fr 1fr; }
  .hero-visual { display:none; }
  .about-side-cards { display:none; }
}
@media(max-width:768px) {
  .nav-links, .nav-cta { display:none; }
  .hamburger { display:flex; }
  .features-grid { grid-template-columns:1fr; }
  .db-kpis { grid-template-columns:1fr 1fr; }
  .db-charts { grid-template-columns:1fr; }
  .map-wrapper { grid-template-columns:1fr; }
  .map-sidebar { flex-direction:row; overflow-x:auto; }
  .footer-inner { grid-template-columns:1fr; }
  .hero-stats { flex-wrap:wrap; gap:20px; }
  .about-inner { gap:30px; }
}

/* ============================================================
   PAGE SECTION ANIMATIONS (Intersection Observer)
============================================================ */
.reveal { opacity:0; transform:translateY(40px); transition:opacity .7s ease, transform .7s ease; }
.reveal.visible { opacity:1; transform:translateY(0); }
.reveal-left { opacity:0; transform:translateX(-40px); transition:opacity .7s ease, transform .7s ease; }
.reveal-left.visible { opacity:1; transform:translateX(0); }
.reveal-right { opacity:0; transform:translateX(40px); transition:opacity .7s ease, transform .7s ease; }
.reveal-right.visible { opacity:1; transform:translateX(0); }
</style>
</head>

<body>

<!-- ============================================================
     NAVBAR
============================================================ -->
<nav id="navbar">
  <div class="container">
    <div class="nav-inner">
      <div class="nav-logo">
        <div class="logo-icon">♻</div>
        <span>EcoTrack</span>
      </div>
      <div class="nav-links">
        <a href="#about">About</a>
        <a href="#features">Features</a>
        <a href="#dashboard">Dashboard</a>
        <a href="#rewards">Rewards</a>
        <a href="#leaderboard">Leaderboard</a>
        <a href="#contact">Contact</a>
      </div>
      <div class="nav-cta">
        <a class="btn btn-ghost btn-sm" href="#dashboard">Login</a>
        <a class="btn btn-primary btn-sm" href="#scan">Scan Plastic</a>
      </div>
      <div class="hamburger">
        <span></span><span></span><span></span>
      </div>
    </div>
  </div>
</nav>

<!-- ============================================================
     ECO TICKER
============================================================ -->
<div class="eco-ticker" style="margin-top:70px;">
  <div class="eco-ticker-inner">
    <span class="eco-ticker-item"><i class="fas fa-leaf"></i> 380 million tonnes of plastic produced every year</span>
    <span class="eco-ticker-item"><i class="fas fa-recycle"></i> Only 9% of all plastic ever made has been recycled</span>
    <span class="eco-ticker-item"><i class="fas fa-fish"></i> 8 million tonnes enter our oceans annually</span>
    <span class="eco-ticker-item"><i class="fas fa-award"></i> EcoTrack: Turning waste into rewards since 2024</span>
    <span class="eco-ticker-item"><i class="fas fa-bolt"></i> 1 PET bottle = 10 EcoCredits — Start scanning!</span>
    <span class="eco-ticker-item"><i class="fas fa-leaf"></i> 380 million tonnes of plastic produced every year</span>
    <span class="eco-ticker-item"><i class="fas fa-recycle"></i> Only 9% of all plastic ever made has been recycled</span>
    <span class="eco-ticker-item"><i class="fas fa-fish"></i> 8 million tonnes enter our oceans annually</span>
    <span class="eco-ticker-item"><i class="fas fa-award"></i> EcoTrack: Turning waste into rewards since 2024</span>
    <span class="eco-ticker-item"><i class="fas fa-bolt"></i> 1 PET bottle = 10 EcoCredits — Start scanning!</span>
  </div>
</div>

<!-- ============================================================
     HERO
============================================================ -->
<section id="hero">
  <div class="grid-bg"></div>
  <div class="orb orb-1"></div>
  <div class="orb orb-2"></div>
  <div class="orb orb-3"></div>
  <div class="container">
    <div class="hero-inner">
      <!-- Left -->
      <div class="hero-text">
        <div class="hero-badge">
          <span class="dot"></span>
          AI + IoT Powered · Live Now
        </div>
        <h1 class="hero-title">
          Turn Plastic Waste<br>
          into <span class="gradient-text">Smart Rewards</span>
        </h1>
        <p class="hero-desc">
          EcoTrack uses AI-powered plastic detection, IoT smart dustbins, and a blockchain-backed credit economy to transform how you interact with plastic — scan, deposit, earn, and make Earth cleaner.
        </p>
        <div class="hero-btns">
          <a href="#dashboard" class="btn btn-primary"><i class="fas fa-rocket"></i> Get Started</a>
          <a href="#scan" class="btn btn-ghost"><i class="fas fa-camera"></i> Scan Plastic</a>
        </div>
        <div class="hero-stats">
          <div class="stat-item">
            <div class="stat-num">2.4M+</div>
            <div class="stat-label">Items Scanned</div>
          </div>
          <div class="stat-item">
            <div class="stat-num">18K+</div>
            <div class="stat-label">Active Users</div>
          </div>
          <div class="stat-item">
            <div class="stat-num">340T</div>
            <div class="stat-label">Plastic Recycled</div>
          </div>
        </div>
      </div>
      <!-- Right: Phone Mockup -->
      <div class="hero-visual">
        <div class="phone-mockup">
          <div class="phone-notch"></div>
          <div class="phone-screen">
            <div class="ps-header">
              <span>ECOTRACK</span>
              <span>9:41 ●●●</span>
            </div>
            <div class="ps-score-card">
              <div class="score-label">YOUR ECO SCORE</div>
              <div class="score-val">842 pts</div>
              <div style="font-size:.6rem;color:rgba(0,255,135,.7);margin-top:2px;">↑ +24 today</div>
            </div>
            <div class="ps-mini-cards">
              <div class="ps-mini-card">
                <div class="mc-icon">♻️</div>
                <div class="mc-val">34</div>
                <div class="mc-label">Items this week</div>
              </div>
              <div class="ps-mini-card">
                <div class="mc-icon">💰</div>
                <div class="mc-val">₹420</div>
                <div class="mc-label">Credit balance</div>
              </div>
              <div class="ps-mini-card">
                <div class="mc-icon">🌍</div>
                <div class="mc-val">1.2 kg</div>
                <div class="mc-label">CO₂ saved</div>
              </div>
              <div class="ps-mini-card">
                <div class="mc-icon">🏆</div>
                <div class="mc-val">#7</div>
                <div class="mc-label">City rank</div>
              </div>
            </div>
            <div class="ps-bar-section">
              <div class="bar-title">WEEKLY ACTIVITY</div>
              <div class="bar-row"><span>M</span><div class="bar-track"><div class="bar-fill" style="width:70%"></div></div></div>
              <div class="bar-row"><span>T</span><div class="bar-track"><div class="bar-fill" style="width:45%"></div></div></div>
              <div class="bar-row"><span>W</span><div class="bar-track"><div class="bar-fill" style="width:90%"></div></div></div>
              <div class="bar-row"><span>T</span><div class="bar-track"><div class="bar-fill" style="width:55%"></div></div></div>
              <div class="bar-row"><span>F</span><div class="bar-track"><div class="bar-fill" style="width:80%"></div></div></div>
            </div>
          </div>
        </div>
        <!-- Floating badges -->
        <div class="floating-badges">
          <div class="fbadge fbadge-1">
            <span class="fbi">🤖</span>
            <div>
              <div style="font-size:.6rem;color:var(--green-neon);font-weight:700;">AI DETECTED</div>
              <div style="font-size:.7rem;color:#fff;">PET Bottle</div>
            </div>
          </div>
          <div class="fbadge fbadge-2">
            <span class="fbi">⚡</span>
            <div>
              <div style="font-size:.6rem;color:var(--gold);font-weight:700;">+10 CREDITS</div>
              <div style="font-size:.7rem;color:#fff;">Earned!</div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- ============================================================
     ABOUT
============================================================ -->
<section id="about">
  <div class="container">
    <div class="about-inner">
      <!-- Visual Card -->
      <div class="about-vis reveal-left">
        <div class="about-main-card">
          <div class="about-big-num">8M</div>
          <div class="about-big-label">Tonnes of plastic enter oceans <em>every year</em></div>
          <div class="about-progress-item">
            <div class="apm-top"><span>Plastic Produced Annually</span><span>380 MT</span></div>
            <div class="apm-bar"><div class="apm-fill" style="width:95%"></div></div>
          </div>
          <div class="about-progress-item">
            <div class="apm-top"><span>Actually Recycled</span><span>9%</span></div>
            <div class="apm-bar"><div class="apm-fill" style="width:9%;background:linear-gradient(90deg,var(--coral),#ff9a6b);"></div></div>
          </div>
          <div class="about-progress-item">
            <div class="apm-top"><span>EcoTrack Target by 2026</span><span>35%</span></div>
            <div class="apm-bar"><div class="apm-fill" style="width:35%;background:linear-gradient(90deg,var(--cyan),#00b4d8);"></div></div>
          </div>
          <div style="margin-top:24px;font-size:.82rem;color:var(--white-60);line-height:1.7;border-top:1px solid rgba(255,255,255,.06);padding-top:18px;">
            💡 <strong style="color:var(--green-neon);">Did you know?</strong> A plastic bottle takes <strong style="color:var(--white);">450 years</strong> to decompose. EcoTrack gives it a purpose in seconds.
          </div>
        </div>
      </div>
      <!-- Content -->
      <div class="about-content reveal-right">
        <span class="section-tag">About EcoTrack</span>
        <h2 class="section-title">Solving a <span class="gradient-text">Global Crisis</span><br>with Smart Technology</h2>
        <p class="section-sub">Plastic pollution is one of the most severe environmental challenges of our time. EcoTrack bridges the gap between awareness and action through AI, IoT, and a rewarding credit economy.</p>
        <div class="about-points">
          <div class="about-point">
            <div class="ap-icon">🤖</div>
            <div>
              <div class="ap-title">AI-Powered Detection</div>
              <div class="ap-desc">Our computer vision model identifies plastic type (PET, HDPE, PVC, LDPE, PP, PS) in real-time with 96.4% accuracy.</div>
            </div>
          </div>
          <div class="about-point">
            <div class="ap-icon">📡</div>
            <div>
              <div class="ap-title">IoT Smart Dustbins</div>
              <div class="ap-desc">Connected smart bins auto-identify deposited plastic, update fill levels, and instantly credit your wallet.</div>
            </div>
          </div>
          <div class="about-point">
            <div class="ap-icon">💎</div>
            <div>
              <div class="ap-title">Plastic Credit Economy</div>
              <div class="ap-desc">Every gram recycled earns EcoCredits — redeemable for mobile recharges, coupons, and marketplace rewards.</div>
            </div>
          </div>
          <div class="about-point">
            <div class="ap-icon">🗺️</div>
            <div>
              <div class="ap-title">Recycling Infrastructure</div>
              <div class="ap-desc">Live map of 2,400+ verified recycling centers with navigation, operating hours, and accepted plastic types.</div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- ============================================================
     FEATURES
============================================================ -->
<section id="features">
  <div class="container">
    <div class="text-center reveal">
      <span class="section-tag">Core Features</span>
      <h2 class="section-title">Everything You Need to<br><span class="gradient-text">Recycle Smarter</span></h2>
      <p class="section-sub">Six powerful tools working in harmony to close the loop on plastic waste — from detection to disposal to reward.</p>
    </div>
    <div class="features-grid">
      <!-- Feature 1 -->
      <div class="feat-card featured reveal">
        <div class="fc-num">01</div>
        <div class="fc-icon">🤖</div>
        <div class="fc-title">AI Plastic Detection</div>
        <div class="fc-desc">Point your camera at any plastic item. Our on-device TensorFlow Lite model identifies the plastic resin code, estimated weight, recyclability score, and environmental impact — all in under 1.2 seconds.</div>
        <span class="fc-tag">Computer Vision · ML</span>
      </div>
      <!-- Feature 2 -->
      <div class="feat-card reveal">
        <div class="fc-num">02</div>
        <div class="fc-icon">💰</div>
        <div class="fc-title">Plastic Credit System</div>
        <div class="fc-desc">Earn EcoCredits for every item scanned and deposited. Credits are tracked on a transparent ledger and redeemable for real-world rewards.</div>
        <span class="fc-tag">Blockchain · Wallet</span>
      </div>
      <!-- Feature 3 -->
      <div class="feat-card reveal">
        <div class="fc-num">03</div>
        <div class="fc-icon">📡</div>
        <div class="fc-title">Smart Dustbin Integration</div>
        <div class="fc-desc">IoT-enabled bins with load sensors, fill-level monitoring, and RFID readers. Auto-crediting upon deposit — no manual scanning needed.</div>
        <span class="fc-tag">IoT · RFID · Sensors</span>
      </div>
      <!-- Feature 4 -->
      <div class="feat-card reveal">
        <div class="fc-num">04</div>
        <div class="fc-icon">📊</div>
        <div class="fc-title">Plastic Footprint Tracker</div>
        <div class="fc-desc">Daily, weekly, and monthly breakdowns of your plastic usage vs. recycling. Compare with city averages and set personal reduction goals.</div>
        <span class="fc-tag">Analytics · Dashboard</span>
      </div>
      <!-- Feature 5 -->
      <div class="feat-card reveal">
        <div class="fc-num">05</div>
        <div class="fc-icon">🎁</div>
        <div class="fc-title">Rewards & Redemption</div>
        <div class="fc-desc">Mobile recharges, food coupons, eco-products, and gift cards — all within the app. Partner with 200+ brands making sustainability rewarding.</div>
        <span class="fc-tag">Rewards · Partners</span>
      </div>
      <!-- Feature 6 -->
      <div class="feat-card reveal">
        <div class="fc-num">06</div>
        <div class="fc-icon">🗺️</div>
        <div class="fc-title">Nearby Recycling Centers</div>
        <div class="fc-desc">Real-time GPS-based map showing verified collection centers, accepted plastic types, operating hours, and user reviews. One-tap navigation.</div>
        <span class="fc-tag">Maps · GPS · Live Data</span>
      </div>
    </div>
  </div>
</section>

<!-- ============================================================
     DASHBOARD
============================================================ -->
<section id="dashboard">
  <div class="container">
    <div class="text-center reveal" style="margin-bottom:40px;">
      <span class="section-tag">User Dashboard</span>
      <h2 class="section-title">Your <span class="gradient-text">Eco Control Center</span></h2>
      <p class="section-sub">Monitor your impact, track earnings, and take quick actions from a single, beautiful panel.</p>
    </div>
    <div class="dashboard-wrapper reveal">
      <!-- Top bar -->
      <div class="db-topbar">
        <div class="db-topbar-title"><span class="dot"></span> EcoTrack Dashboard</div>
        <div class="db-topbar-right">
          <span>Thu, Apr 16, 2026</span>
          <div class="db-notif"><i class="fas fa-bell" style="font-size:.8rem;"></i></div>
          <div class="db-avatar">AK</div>
        </div>
      </div>
      <!-- Body -->
      <div class="db-body">
        <!-- Sidebar -->
        <div class="db-sidebar">
          <div class="db-sidebar-user">
            <div class="db-user-ava">AK</div>
            <div class="db-user-name">Aryan Kumar</div>
            <div class="db-user-level">🌿 Eco Champion</div>
          </div>
          <div class="db-nav-item active"><i class="fas fa-home"></i> Overview</div>
          <div class="db-nav-item"><i class="fas fa-camera"></i> Scan Plastic</div>
          <div class="db-nav-item"><i class="fas fa-wallet"></i> Rewards</div>
          <div class="db-nav-item"><i class="fas fa-map-marker-alt"></i> Nearby Map</div>
          <div class="db-nav-item"><i class="fas fa-trash-alt"></i> Smart Dustbin</div>
          <div class="db-nav-item"><i class="fas fa-trophy"></i> Leaderboard</div>
          <div class="db-nav-item"><i class="fas fa-user"></i> Profile</div>
          <div class="db-nav-item" style="margin-top:24px;"><i class="fas fa-cog"></i> Settings</div>
        </div>
        <!-- Main -->
        <div class="db-main">
          <!-- KPIs -->
          <div class="db-kpis">
            <div class="kpi-card kpi-green">
              <div class="kpi-icon">🌱</div>
              <div class="kpi-val">842</div>
              <div class="kpi-label">Eco Score</div>
              <div class="kpi-delta">↑ +24 today</div>
            </div>
            <div class="kpi-card kpi-gold">
              <div class="kpi-icon">💰</div>
              <div class="kpi-val">₹1,240</div>
              <div class="kpi-label">Credit Balance</div>
              <div class="kpi-delta">↑ +₹80 today</div>
            </div>
            <div class="kpi-card kpi-coral">
              <div class="kpi-icon">♻️</div>
              <div class="kpi-val">3.4 kg</div>
              <div class="kpi-label">Plastic This Month</div>
              <div class="kpi-delta" style="color:var(--coral);">↓ -12% vs last</div>
            </div>
            <div class="kpi-card kpi-cyan">
              <div class="kpi-icon">🏆</div>
              <div class="kpi-val">#7</div>
              <div class="kpi-label">City Ranking</div>
              <div class="kpi-delta">↑ +3 places</div>
            </div>
          </div>
          <!-- Charts -->
          <div class="db-charts">
            <!-- Bar chart -->
            <div class="db-chart-card">
              <div class="dcc-title">Weekly Recycling Activity <span class="dcc-badge">Last 7 days</span></div>
              <svg class="chart-svg" viewBox="0 0 360 120" xmlns="http://www.w3.org/2000/svg">
                <defs>
                  <linearGradient id="barGrad" x1="0" y1="0" x2="0" y2="1">
                    <stop offset="0%" stop-color="#00ff87"/>
                    <stop offset="100%" stop-color="#00e5c8"/>
                  </linearGradient>
                </defs>
                <!-- Gridlines -->
                <line x1="0" y1="100" x2="360" y2="100" stroke="rgba(255,255,255,.06)" stroke-width="1"/>
                <line x1="0" y1="75"  x2="360" y2="75"  stroke="rgba(255,255,255,.06)" stroke-width="1"/>
                <line x1="0" y1="50"  x2="360" y2="50"  stroke="rgba(255,255,255,.06)" stroke-width="1"/>
                <line x1="0" y1="25"  x2="360" y2="25"  stroke="rgba(255,255,255,.06)" stroke-width="1"/>
                <!-- Bars -->
                <rect x="10"  y="55" width="34" height="45" rx="4" fill="url(#barGrad)" opacity=".7"/>
                <rect x="62"  y="70" width="34" height="30" rx="4" fill="url(#barGrad)" opacity=".7"/>
                <rect x="114" y="35" width="34" height="65" rx="4" fill="url(#barGrad)"/>
                <rect x="166" y="60" width="34" height="40" rx="4" fill="url(#barGrad)" opacity=".7"/>
                <rect x="218" y="45" width="34" height="55" rx="4" fill="url(#barGrad)"/>
                <rect x="270" y="40" width="34" height="60" rx="4" fill="url(#barGrad)"/>
                <rect x="322" y="25" width="34" height="75" rx="4" fill="url(#barGrad)"/>
                <!-- Labels -->
                <text x="27"  y="114" fill="rgba(255,255,255,.4)" font-size="9" text-anchor="middle" font-family="DM Sans">Mon</text>
                <text x="79"  y="114" fill="rgba(255,255,255,.4)" font-size="9" text-anchor="middle" font-family="DM Sans">Tue</text>
                <text x="131" y="114" fill="rgba(255,255,255,.4)" font-size="9" text-anchor="middle" font-family="DM Sans">Wed</text>
                <text x="183" y="114" fill="rgba(255,255,255,.4)" font-size="9" text-anchor="middle" font-family="DM Sans">Thu</text>
                <text x="235" y="114" fill="rgba(255,255,255,.4)" font-size="9" text-anchor="middle" font-family="DM Sans">Fri</text>
                <text x="287" y="114" fill="rgba(255,255,255,.4)" font-size="9" text-anchor="middle" font-family="DM Sans">Sat</text>
                <text x="339" y="114" fill="rgba(255,255,255,.4)" font-size="9" text-anchor="middle" font-family="DM Sans">Sun</text>
              </svg>
            </div>
            <!-- Donut chart -->
            <div class="db-chart-card">
              <div class="dcc-title">Plastic Types Scanned</div>
              <svg viewBox="0 0 120 120" style="width:120px;margin:0 auto;display:block;">
                <defs>
                  <linearGradient id="scoreGrad" x1="0" y1="0" x2="1" y2="0">
                    <stop offset="0%" stop-color="#00ff87"/>
                    <stop offset="100%" stop-color="#00e5c8"/>
                  </linearGradient>
                </defs>
                <circle cx="60" cy="60" r="45" fill="none" stroke="rgba(255,255,255,.05)" stroke-width="18"/>
                <circle cx="60" cy="60" r="45" fill="none" stroke="#00ff87" stroke-width="18" stroke-dasharray="113 170" stroke-dashoffset="0" stroke-linecap="round" transform="rotate(-90 60 60)"/>
                <circle cx="60" cy="60" r="45" fill="none" stroke="#00e5c8" stroke-width="18" stroke-dasharray="68 215" stroke-dashoffset="-113" stroke-linecap="round" transform="rotate(-90 60 60)"/>
                <circle cx="60" cy="60" r="45" fill="none" stroke="#f5c842" stroke-width="18" stroke-dasharray="45 238" stroke-dashoffset="-181" stroke-linecap="round" transform="rotate(-90 60 60)"/>
                <circle cx="60" cy="60" r="45" fill="none" stroke="#ff6b6b" stroke-width="18" stroke-dasharray="27 256" stroke-dashoffset="-226" stroke-linecap="round" transform="rotate(-90 60 60)"/>
                <text x="60" y="56" fill="white" font-size="14" font-weight="800" text-anchor="middle" font-family="Syne">148</text>
                <text x="60" y="68" fill="rgba(255,255,255,.5)" font-size="7" text-anchor="middle" font-family="DM Sans">items</text>
              </svg>
              <div style="display:grid;grid-template-columns:1fr 1fr;gap:6px;margin-top:14px;">
                <div style="display:flex;align-items:center;gap:6px;font-size:.7rem;color:rgba(255,255,255,.6);">
                  <span style="width:8px;height:8px;border-radius:2px;background:#00ff87;flex-shrink:0;"></span>PET (40%)
                </div>
                <div style="display:flex;align-items:center;gap:6px;font-size:.7rem;color:rgba(255,255,255,.6);">
                  <span style="width:8px;height:8px;border-radius:2px;background:#00e5c8;flex-shrink:0;"></span>HDPE (25%)
                </div>
                <div style="display:flex;align-items:center;gap:6px;font-size:.7rem;color:rgba(255,255,255,.6);">
                  <span style="width:8px;height:8px;border-radius:2px;background:#f5c842;flex-shrink:0;"></span>PP (17%)
                </div>
                <div style="display:flex;align-items:center;gap:6px;font-size:.7rem;color:rgba(255,255,255,.6);">
                  <span style="width:8px;height:8px;border-radius:2px;background:#ff6b6b;flex-shrink:0;"></span>Other (18%)
                </div>
              </div>
            </div>
          </div>
          <!-- Quick Actions -->
          <div class="db-actions">
            <div class="qa-btn"><i class="fas fa-camera"></i><span>Scan Plastic</span></div>
            <div class="qa-btn"><i class="fas fa-gift"></i><span>Redeem Rewards</span></div>
            <div class="qa-btn"><i class="fas fa-map-marker-alt"></i><span>Find Centers</span></div>
            <div class="qa-btn"><i class="fas fa-trash-alt"></i><span>Smart Dustbin</span></div>
            <div class="qa-btn"><i class="fas fa-users"></i><span>Leaderboard</span></div>
          </div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- ============================================================
     SCAN PLASTIC
============================================================ -->
<section id="scan">
  <div class="container">
    <div class="scan-inner">
      <!-- Scan Device -->
      <div class="scan-device reveal-left">
        <div class="scan-frame">
          <div class="scan-corners">
            <span></span><span></span><span></span><span></span>
          </div>
          <div class="scan-laser"></div>
          <div class="scan-object">🧴</div>
          <div class="scan-result-overlay">
            <div class="sro-tag">✓ AI DETECTED · 96.4% CONFIDENCE</div>
            <div class="sro-name">HDPE Bottle (Shampoo)</div>
            <div class="sro-pts">+8 EcoCredits · Recyclable ✓ · ~180g</div>
          </div>
        </div>
      </div>
      <!-- Content -->
      <div class="scan-content reveal-right">
        <span class="section-tag">AI Scan</span>
        <h2 class="section-title">Instant <span class="gradient-text">Plastic ID</span><br>in 1.2 Seconds</h2>
        <p class="section-sub">Our on-device ML model, trained on 1.2 million plastic images, identifies type, grade, weight, and recyclability — no internet needed.</p>
        <div class="scan-steps">
          <div class="scan-step">
            <div class="ss-num">1</div>
            <div>
              <div class="ss-title">Point Camera</div>
              <div class="ss-desc">Open the scanner and aim at any plastic item — bottle, bag, container, wrapper.</div>
            </div>
          </div>
          <div class="scan-step">
            <div class="ss-num">2</div>
            <div>
              <div class="ss-title">AI Identifies</div>
              <div class="ss-desc">Real-time detection of plastic resin code, weight estimate, and recyclability grade (A–F).</div>
            </div>
          </div>
          <div class="scan-step">
            <div class="ss-num">3</div>
            <div>
              <div class="ss-title">Earn Credits</div>
              <div class="ss-desc">Deposit to a Smart Dustbin or verified center to auto-earn EcoCredits to your wallet.</div>
            </div>
          </div>
        </div>
        <div class="ai-types">
          <span class="ai-type-tag">PET #1</span>
          <span class="ai-type-tag">HDPE #2</span>
          <span class="ai-type-tag">PVC #3</span>
          <span class="ai-type-tag">LDPE #4</span>
          <span class="ai-type-tag">PP #5</span>
          <span class="ai-type-tag">PS #6</span>
          <span class="ai-type-tag">Other #7</span>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- ============================================================
     REWARDS
============================================================ -->
<section id="rewards">
  <div class="container">
    <div class="text-center reveal" style="margin-bottom:50px;">
      <span class="section-tag">Rewards System</span>
      <h2 class="section-title">Recycle. Earn. <span class="gradient-text">Redeem.</span></h2>
      <p class="section-sub">Your eco actions have real monetary value. Turn plastic credits into mobile recharges, coupons, and eco-products.</p>
    </div>
    <div class="rewards-inner">
      <!-- Wallet -->
      <div class="reveal-left">
        <div class="wallet-card">
          <div class="wc-label">ECOCREDIT WALLET</div>
          <div class="wc-balance"><span class="wc-currency">₹</span>1,240</div>
          <div class="wc-sub">≈ 1,240 EcoCredits · Earned from recycling</div>
          <div class="wc-actions">
            <div class="wca"><i class="fas fa-exchange-alt"></i><span>Transfer</span></div>
            <div class="wca"><i class="fas fa-gift"></i><span>Redeem</span></div>
            <div class="wca"><i class="fas fa-history"></i><span>History</span></div>
          </div>
          <div class="wc-history">
            <div class="wch-title">RECENT TRANSACTIONS</div>
            <div class="wch-item"><span class="wch-label">PET Bottle × 3</span><span class="wch-val green">+30 EC</span></div>
            <div class="wch-item"><span class="wch-label">Mobile Recharge ₹49</span><span class="wch-val coral">-49 EC</span></div>
            <div class="wch-item"><span class="wch-label">Smart Dustbin Deposit</span><span class="wch-val green">+25 EC</span></div>
            <div class="wch-item"><span class="wch-label">Eco Bonus – Monday</span><span class="wch-val green">+15 EC</span></div>
            <div class="wch-item"><span class="wch-label">Zomato Coupon</span><span class="wch-val coral">-100 EC</span></div>
          </div>
        </div>
      </div>
      <!-- Redeem Options -->
      <div class="redeem-section reveal-right">
        <span class="section-tag">Redeem Options</span>
        <h3 class="section-title" style="font-size:1.8rem;">What will you<br><span class="gradient-text">spend credits on?</span></h3>
        <div class="redeem-grid">
          <div class="redeem-card">
            <div class="rc-icon">📱</div>
            <div class="rc-title">Mobile Recharge</div>
            <div class="rc-pts">From 49 EC</div>
            <div class="rc-desc">Recharge any network — Jio, Airtel, Vi, BSNL.</div>
          </div>
          <div class="redeem-card">
            <div class="rc-icon">🍕</div>
            <div class="rc-title">Food Coupons</div>
            <div class="rc-pts">From 100 EC</div>
            <div class="rc-desc">Swiggy, Zomato, and 50+ restaurant partners.</div>
          </div>
          <div class="redeem-card">
            <div class="rc-icon">🌿</div>
            <div class="rc-title">Eco Products</div>
            <div class="rc-pts">From 200 EC</div>
            <div class="rc-desc">Bamboo toothbrushes, reusable bags, planters.</div>
          </div>
          <div class="redeem-card">
            <div class="rc-icon">🎁</div>
            <div class="rc-title">Gift Cards</div>
            <div class="rc-pts">From 500 EC</div>
            <div class="rc-desc">Amazon, Flipkart, Myntra, and more.</div>
          </div>
          <div class="redeem-card">
            <div class="rc-icon">🌱</div>
            <div class="rc-title">Plant a Tree</div>
            <div class="rc-pts">50 EC</div>
            <div class="rc-desc">We plant a real tree in your name via NGO partners.</div>
          </div>
          <div class="redeem-card">
            <div class="rc-icon">💳</div>
            <div class="rc-title">Bank Transfer</div>
            <div class="rc-pts">Min. 1000 EC</div>
            <div class="rc-desc">Direct UPI/bank transfer at ₹1 per EcoCredit.</div>
          </div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- ============================================================
     MAP SECTION
============================================================ -->
<section id="map-section">
  <div class="container">
    <div class="text-center reveal" style="margin-bottom:40px;">
      <span class="section-tag">Recycling Map</span>
      <h2 class="section-title">Find Centers <span class="gradient-text">Near You</span></h2>
      <p class="section-sub">Live map of 2,400+ verified recycling centers, smart bins, and drop-off points across India.</p>
    </div>
    <div class="map-wrapper reveal">
      <div class="map-area">
        <div class="map-grid"></div>
        <!-- Animated center dot -->
        <div class="map-center-dot"></div>
        <!-- Pins -->
        <div class="map-pin" style="top:35%;left:48%;">
          <div class="pin-icon"><span>♻</span></div>
          <div class="pin-label">EcoCenter Jaipur</div>
        </div>
        <div class="map-pin" style="top:55%;left:60%;">
          <div class="pin-icon" style="background:linear-gradient(135deg,var(--cyan),#00b4d8);"><span>📡</span></div>
          <div class="pin-label">Smart Bin #42</div>
        </div>
        <div class="map-pin" style="top:25%;left:65%;">
          <div class="pin-icon" style="background:linear-gradient(135deg,var(--gold),#ffaa00);"><span>🏭</span></div>
          <div class="pin-label">Recycling Hub</div>
        </div>
        <div class="map-pin" style="top:65%;left:35%;">
          <div class="pin-icon"><span>♻</span></div>
          <div class="pin-label">Collection Point</div>
        </div>
        <div class="map-pin" style="top:45%;left:28%;">
          <div class="pin-icon" style="background:linear-gradient(135deg,var(--coral),#ff9a6b);"><span>🗑</span></div>
          <div class="pin-label">Smart Bin #18</div>
        </div>
        <!-- Overlay -->
        <div class="map-overlay">
          <div class="mo-title">📍 Jaipur, Rajasthan</div>
          <div class="mo-stat">12 centers within 5 km</div>
        </div>
        <!-- Nav button -->
        <div style="position:absolute;bottom:20px;right:20px;">
          <a class="btn btn-primary btn-sm" href="#"><i class="fas fa-navigation"></i> Navigate</a>
        </div>
      </div>
      <!-- Sidebar -->
      <div class="map-sidebar">
        <div class="map-center-card">
          <div class="mcc-header">
            <div class="mcc-icon">♻</div>
            <div>
              <div class="mcc-name">EcoCenter Jaipur</div>
              <div class="mcc-dist">0.8 km · Open Now</div>
            </div>
          </div>
          <div class="mcc-tags">
            <span class="mcc-tag">PET</span><span class="mcc-tag">HDPE</span><span class="mcc-tag">PP</span>
          </div>
          <button class="mcc-btn">Get Directions</button>
        </div>
        <div class="map-center-card">
          <div class="mcc-header">
            <div class="mcc-icon">📡</div>
            <div>
              <div class="mcc-name">Smart Bin #42</div>
              <div class="mcc-dist">1.2 km · 68% Full</div>
            </div>
          </div>
          <div class="mcc-tags">
            <span class="mcc-tag">PET</span><span class="mcc-tag">All Types</span>
          </div>
          <button class="mcc-btn">Get Directions</button>
        </div>
        <div class="map-center-card">
          <div class="mcc-header">
            <div class="mcc-icon">🏭</div>
            <div>
              <div class="mcc-name">GreenHub Recycling</div>
              <div class="mcc-dist">2.1 km · Open Now</div>
            </div>
          </div>
          <div class="mcc-tags">
            <span class="mcc-tag">All Types</span><span class="mcc-tag">Bulk</span>
          </div>
          <button class="mcc-btn">Get Directions</button>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- ============================================================
     SMART DUSTBIN
============================================================ -->
<section id="dustbin">
  <div class="container">
    <div class="dustbin-inner">
      <!-- Visual -->
      <div class="dustbin-visual reveal-left">
        <div class="dustbin-unit">
          <div style="position:relative;">
            <div class="du-signals"></div>
            <div class="du-bin" id="smartBin">
              <div class="du-bin-top">ECOTRACK BIN v2</div>
              <div class="du-fill-track">
                <div class="du-level-marks">
                  <span>100%</span><span>75%</span><span>50%</span><span>25%</span>
                </div>
                <div class="du-fill-bar"><span>68%</span></div>
              </div>
            </div>
          </div>
          <div class="du-status"><span class="ds-dot"></span> Connected · BIN-JA-042</div>
          <div style="margin-top:12px;display:flex;gap:8px;justify-content:center;flex-wrap:wrap;">
            <span style="font-size:.7rem;background:rgba(0,255,135,.1);color:var(--green-neon);padding:4px 12px;border-radius:99px;border:1px solid rgba(0,255,135,.2);">📶 WiFi OK</span>
            <span style="font-size:.7rem;background:rgba(0,229,200,.1);color:var(--cyan);padding:4px 12px;border-radius:99px;border:1px solid rgba(0,229,200,.2);">⚡ 87% Battery</span>
          </div>
        </div>
      </div>
      <!-- Content -->
      <div class="dustbin-content reveal-right">
        <span class="section-tag">Smart Dustbin</span>
        <h2 class="section-title">IoT Bins That <span class="gradient-text">Auto-Reward</span><br>Every Deposit</h2>
        <p class="section-sub">Our WiFi+BLE smart bins use load cells, RFID, and computer vision to identify, weigh, and auto-credit your wallet the moment you deposit plastic.</p>
        <div class="db-stats-grid">
          <div class="db-stat-card">
            <div class="dbs-icon">🗑️</div>
            <div class="dbs-val">2,400+</div>
            <div class="dbs-label">Smart Bins Deployed</div>
          </div>
          <div class="db-stat-card">
            <div class="dbs-icon">⚡</div>
            <div class="dbs-val">~1.2s</div>
            <div class="dbs-label">Auto-Credit Speed</div>
          </div>
          <div class="db-stat-card">
            <div class="dbs-icon">📡</div>
            <div class="dbs-val">99.4%</div>
            <div class="dbs-label">Uptime SLA</div>
          </div>
          <div class="db-stat-card">
            <div class="dbs-icon">🔋</div>
            <div class="dbs-val">Solar</div>
            <div class="dbs-label">Powered by Solar</div>
          </div>
        </div>
        <div class="iot-tags">
          <span class="iot-tag"><i class="fas fa-wifi"></i> WiFi 6</span>
          <span class="iot-tag"><i class="fas fa-bluetooth"></i> BLE 5.0</span>
          <span class="iot-tag"><i class="fas fa-microchip"></i> ESP32 + Pi</span>
          <span class="iot-tag"><i class="fas fa-weight-hanging"></i> Load Cell</span>
          <span class="iot-tag"><i class="fas fa-id-card"></i> RFID Reader</span>
          <span class="iot-tag"><i class="fas fa-solar-panel"></i> Solar</span>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- ============================================================
     LEADERBOARD
============================================================ -->
<section id="leaderboard">
  <div class="container">
    <div class="text-center reveal" style="margin-bottom:50px;">
      <span class="section-tag">Gamification</span>
      <h2 class="section-title">The <span class="gradient-text">Eco Champions</span><br>Leaderboard</h2>
      <p class="section-sub">Compete with your city, earn badges, unlock achievements. Making recycling a game changes everything.</p>
    </div>
    <div class="leaderboard-inner">
      <!-- Table -->
      <div class="reveal-left">
        <div class="lb-table">
          <div class="lb-header">
            <div>#</div><div>User</div><div>EcoCredits</div><div>Badge</div>
          </div>
          <div class="lb-row top1">
            <div class="lb-rank rank-1">🥇</div>
            <div class="lb-user"><div class="lb-ava" style="background:linear-gradient(135deg,#f5c842,#ff9a00);">PP</div><div><div class="lb-user-name">Priya Patel</div><div class="lb-user-loc">Mumbai</div></div></div>
            <div class="lb-pts">4,820 EC</div>
            <div class="lb-badge-img">🌟</div>
          </div>
          <div class="lb-row top2">
            <div class="lb-rank rank-2">🥈</div>
            <div class="lb-user"><div class="lb-ava" style="background:linear-gradient(135deg,#c0c0c0,#a0a0a0);">RS</div><div><div class="lb-user-name">Ravi Sharma</div><div class="lb-user-loc">Delhi</div></div></div>
            <div class="lb-pts">4,210 EC</div>
            <div class="lb-badge-img">🌿</div>
          </div>
          <div class="lb-row top3">
            <div class="lb-rank rank-3">🥉</div>
            <div class="lb-user"><div class="lb-ava" style="background:linear-gradient(135deg,#cd7f32,#a0522d);">AK</div><div><div class="lb-user-name">Aryan Kumar</div><div class="lb-user-loc">Jaipur</div></div></div>
            <div class="lb-pts">3,940 EC</div>
            <div class="lb-badge-img">♻️</div>
          </div>
          <div class="lb-row">
            <div class="lb-rank" style="color:rgba(255,255,255,.4);">4</div>
            <div class="lb-user"><div class="lb-ava" style="background:linear-gradient(135deg,#22c47e,#0a3d28);">SN</div><div><div class="lb-user-name">Sneha Nair</div><div class="lb-user-loc">Bangalore</div></div></div>
            <div class="lb-pts">3,720 EC</div>
            <div class="lb-badge-img">🌱</div>
          </div>
          <div class="lb-row">
            <div class="lb-rank" style="color:rgba(255,255,255,.4);">5</div>
            <div class="lb-user"><div class="lb-ava" style="background:linear-gradient(135deg,#00e5c8,#0a3d28);">KM</div><div><div class="lb-user-name">Kiran Mehta</div><div class="lb-user-loc">Pune</div></div></div>
            <div class="lb-pts">3,450 EC</div>
            <div class="lb-badge-img">🍃</div>
          </div>
          <div class="lb-row">
            <div class="lb-rank" style="color:rgba(255,255,255,.4);">6</div>
            <div class="lb-user"><div class="lb-ava" style="background:linear-gradient(135deg,#7fffd4,#0a3d28);">VR</div><div><div class="lb-user-name">Vikram Rao</div><div class="lb-user-loc">Hyderabad</div></div></div>
            <div class="lb-pts">3,200 EC</div>
            <div class="lb-badge-img">🌍</div>
          </div>
          <div class="lb-row" style="background:rgba(0,255,135,.04);border:1px solid rgba(0,255,135,.12);">
            <div class="lb-rank" style="color:var(--green-neon);">7</div>
            <div class="lb-user"><div class="lb-ava" style="background:linear-gradient(135deg,#22c47e,#0f5c3a);border:2px solid var(--green-neon);">You</div><div><div class="lb-user-name">Aryan Kumar</div><div class="lb-user-loc">Jaipur · You</div></div></div>
            <div class="lb-pts" style="color:var(--green-neon);">842 EC</div>
            <div class="lb-badge-img">🏅</div>
          </div>
        </div>
      </div>
      <!-- Badges -->
      <div class="badges-section reveal-right">
        <span class="section-tag">Achievements</span>
        <h3 class="section-title" style="font-size:1.6rem;text-align:left;">Earn <span class="gradient-text">Badges</span></h3>
        <div class="badges-grid">
          <div class="badge-card">
            <div class="bc-icon">🌱</div>
            <div class="bc-name">First Steps</div>
            <div class="bc-desc">Recycled first 10 items</div>
            <div class="bc-progress"><div class="bc-progress-fill" style="width:100%"></div></div>
          </div>
          <div class="badge-card">
            <div class="bc-icon">🔥</div>
            <div class="bc-name">7-Day Streak</div>
            <div class="bc-desc">Recycled 7 days in a row</div>
            <div class="bc-progress"><div class="bc-progress-fill" style="width:100%"></div></div>
          </div>
          <div class="badge-card">
            <div class="bc-icon">🌍</div>
            <div class="bc-name">Planet Saver</div>
            <div class="bc-desc">Recycled 10 kg total</div>
            <div class="bc-progress"><div class="bc-progress-fill" style="width:65%"></div></div>
          </div>
          <div class="badge-card locked">
            <div class="bc-icon">🏆</div>
            <div class="bc-name">Eco Legend</div>
            <div class="bc-desc">Top 10 in City</div>
            <div class="bc-progress"><div class="bc-progress-fill" style="width:30%"></div></div>
          </div>
          <div class="badge-card locked">
            <div class="bc-icon">💎</div>
            <div class="bc-name">Diamond Recycler</div>
            <div class="bc-desc">50 kg recycled</div>
            <div class="bc-progress"><div class="bc-progress-fill" style="width:12%"></div></div>
          </div>
          <div class="badge-card locked">
            <div class="bc-icon">🌊</div>
            <div class="bc-name">Ocean Guardian</div>
            <div class="bc-desc">Prevent 100 ocean-bound</div>
            <div class="bc-progress"><div class="bc-progress-fill" style="width:8%"></div></div>
          </div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- ============================================================
     PROFILE
============================================================ -->
<section id="profile">
  <div class="container">
    <div class="text-center reveal" style="margin-bottom:50px;">
      <span class="section-tag">User Profile</span>
      <h2 class="section-title">Your <span class="gradient-text">Eco Journey</span></h2>
    </div>
    <div class="profile-inner reveal">
      <!-- Profile Card -->
      <div class="profile-card">
        <div class="pc-avatar">AK</div>
        <div class="pc-name">Aryan Kumar</div>
        <div class="pc-tagline">🌿 Eco Champion · Level 8</div>
        <div class="eco-score-ring" style="margin-bottom:20px;">
          <svg viewBox="0 0 100 100" width="120" height="120">
            <defs>
              <linearGradient id="scoreGrad2" x1="0" y1="0" x2="1" y2="0">
                <stop offset="0%" stop-color="#00ff87"/>
                <stop offset="100%" stop-color="#00e5c8"/>
              </linearGradient>
            </defs>
            <circle class="ring-bg" cx="50" cy="50" r="45" fill="none" stroke="rgba(255,255,255,.08)" stroke-width="8"/>
            <circle cx="50" cy="50" r="45" fill="none" stroke="url(#scoreGrad2)" stroke-width="8"
              stroke-linecap="round" stroke-dasharray="283" stroke-dashoffset="57"
              transform="rotate(-90 50 50)"/>
          </svg>
          <div class="eco-score-num" style="position:absolute;inset:0;display:flex;flex-direction:column;align-items:center;justify-content:center;">
            <div class="esn-val">842</div>
            <div class="esn-label">ECO SCORE</div>
          </div>
        </div>
        <div class="pc-stats">
          <div class="pcs"><div class="pcs-val">34.2 kg</div><div class="pcs-label">Plastic Recycled</div></div>
          <div class="pcs"><div class="pcs-val">842</div><div class="pcs-label">Total Credits</div></div>
          <div class="pcs"><div class="pcs-val">47</div><div class="pcs-label">Days Streak</div></div>
          <div class="pcs"><div class="pcs-val">8</div><div class="pcs-label">Badges Earned</div></div>
        </div>
        <div class="profile-badges">
          <div class="pb" title="First Steps">🌱</div>
          <div class="pb" title="7-Day Streak">🔥</div>
          <div class="pb" title="100 Items">♻️</div>
          <div class="pb" title="Eco Starter">🌿</div>
          <div class="pb" title="Scan Pro">📷</div>
          <div class="pb" title="Community">👥</div>
        </div>
      </div>
      <!-- Activity -->
      <div class="profile-activity">
        <div class="pa-section">
          <div class="pas-title"><i class="fas fa-history"></i> Recent Activity</div>
          <div class="timeline">
            <div class="tl-item">
              <div class="tl-dot green">♻</div>
              <div class="tl-content">
                <div class="tlc-title">Scanned HDPE Bottle</div>
                <div class="tlc-sub">Today, 9:32 AM · Smart Bin #42</div>
                <div class="tlc-pts">+8 EcoCredits</div>
              </div>
            </div>
            <div class="tl-item">
              <div class="tl-dot gold">🏅</div>
              <div class="tl-content">
                <div class="tlc-title">Badge Unlocked: 7-Day Streak</div>
                <div class="tlc-sub">Yesterday, 11:00 PM</div>
                <div class="tlc-pts">+50 Bonus Credits</div>
              </div>
            </div>
            <div class="tl-item">
              <div class="tl-dot cyan">💳</div>
              <div class="tl-content">
                <div class="tlc-title">Redeemed Mobile Recharge</div>
                <div class="tlc-sub">Apr 14, 2026 · ₹49 Airtel</div>
                <div class="tlc-pts" style="color:var(--coral);">-49 EcoCredits</div>
              </div>
            </div>
            <div class="tl-item">
              <div class="tl-dot green">📡</div>
              <div class="tl-content">
                <div class="tlc-title">Smart Dustbin Deposit</div>
                <div class="tlc-sub">Apr 13, 2026 · 5 PET bottles</div>
                <div class="tlc-pts">+50 EcoCredits</div>
              </div>
            </div>
          </div>
        </div>
        <div class="pa-section">
          <div class="pas-title"><i class="fas fa-star"></i> Achievements</div>
          <div class="ach-list">
            <div class="ach-item">
              <div class="ach-icon">🌱</div>
              <div class="ach-info"><div class="ai-title">First Steps</div><div class="ai-desc">Recycled your first 10 items</div></div>
              <div class="ach-pts">+100 EC</div>
            </div>
            <div class="ach-item">
              <div class="ach-icon">🔥</div>
              <div class="ach-info"><div class="ai-title">7-Day Streak</div><div class="ai-desc">Recycled 7 consecutive days</div></div>
              <div class="ach-pts">+50 EC</div>
            </div>
            <div class="ach-item">
              <div class="ach-icon">🏙️</div>
              <div class="ach-info"><div class="ai-title">City Explorer</div><div class="ai-desc">Used 5 different recycling centers</div></div>
              <div class="ach-pts">+75 EC</div>
            </div>
            <div class="ach-item">
              <div class="ach-icon">📷</div>
              <div class="ach-info"><div class="ai-title">Scan Maestro</div><div class="ai-desc">Scanned 100+ items</div></div>
              <div class="ach-pts">+80 EC</div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- ============================================================
     PLASTIC CREDIT ECONOMY (UNIQUE FEATURE)
============================================================ -->
<section id="economy">
  <div class="container">
    <div class="economy-inner">
      <div class="economy-content reveal-left">
        <span class="section-tag">Unique Feature</span>
        <h2 class="section-title">The <span class="gradient-text">Plastic Credit</span><br>Economy</h2>
        <p class="section-sub">A self-sustaining economic loop where plastic waste becomes currency — incentivizing recycling at scale through behavioral economics.</p>
        <div class="economy-flow">
          <div class="ef-step">
            <div class="ef-icon">🧴</div>
            <div>
              <div class="ef-title">You Collect Plastic</div>
              <div class="ef-desc">Gather plastic waste from your home, office, or community. Every gram counts.</div>
            </div>
          </div>
          <div class="ef-step">
            <div class="ef-icon">📱</div>
            <div>
              <div class="ef-title">Scan or Deposit</div>
              <div class="ef-desc">Use AI scan or deposit to a Smart Bin — the system identifies, weighs, and valuates instantly.</div>
            </div>
          </div>
          <div class="ef-step">
            <div class="ef-icon">💰</div>
            <div>
              <div class="ef-title">Earn EcoCredits</div>
              <div class="ef-desc">Credits are minted and added to your wallet. Value scales with plastic grade and rarity.</div>
            </div>
          </div>
          <div class="ef-step">
            <div class="ef-icon">🎁</div>
            <div>
              <div class="ef-title">Spend & Grow</div>
              <div class="ef-desc">Redeem for real rewards. Brands buy plastic credits to offset their footprint, funding the ecosystem.</div>
            </div>
          </div>
        </div>
      </div>
      <div class="economy-vis reveal-right">
        <div class="eco-card-stack">
          <div class="ecc ecc-1">
            <div class="ecc-header">
              <div class="ecc-logo">ECOCREDIT</div>
              <div class="ecc-type">Standard</div>
            </div>
            <div class="ecc-num">EC •• •• 3021</div>
            <div class="ecc-bottom">
              <div><div class="ecc-bal-label">BALANCE</div><div class="ecc-bal">482 EC</div></div>
              <div class="ecc-chip"></div>
            </div>
          </div>
          <div class="ecc ecc-2">
            <div class="ecc-header">
              <div class="ecc-logo">ECOCREDIT</div>
              <div class="ecc-type">Green+</div>
            </div>
            <div class="ecc-num">EC •• •• 7814</div>
            <div class="ecc-bottom">
              <div><div class="ecc-bal-label">BALANCE</div><div class="ecc-bal">756 EC</div></div>
              <div class="ecc-chip"></div>
            </div>
          </div>
          <div class="ecc ecc-3">
            <div class="ecc-header">
              <div class="ecc-logo">ECOCREDIT</div>
              <div class="ecc-type">Champion</div>
            </div>
            <div class="ecc-num">EC •• •• 1240</div>
            <div class="ecc-bottom">
              <div><div class="ecc-bal-label">BALANCE</div><div class="ecc-bal">1,240 EC</div></div>
              <div class="ecc-chip"></div>
            </div>
          </div>
        </div>
        <div style="margin-top:24px;display:grid;grid-template-columns:1fr 1fr 1fr;gap:12px;">
          <div class="glass-card" style="padding:16px;text-align:center;">
            <div style="font-size:1.4rem;margin-bottom:4px;">🌿</div>
            <div style="font-family:var(--font-head);font-size:.85rem;font-weight:700;color:var(--green-neon);">1:1</div>
            <div style="font-size:.7rem;color:var(--white-60);">EC = ₹1</div>
          </div>
          <div class="glass-card" style="padding:16px;text-align:center;">
            <div style="font-size:1.4rem;margin-bottom:4px;">♻️</div>
            <div style="font-family:var(--font-head);font-size:.85rem;font-weight:700;color:var(--cyan);">10g</div>
            <div style="font-size:.7rem;color:var(--white-60);">= 1 EC (PET)</div>
          </div>
          <div class="glass-card" style="padding:16px;text-align:center;">
            <div style="font-size:1.4rem;margin-bottom:4px;">🏭</div>
            <div style="font-family:var(--font-head);font-size:.85rem;font-weight:700;color:var(--gold);">B2B</div>
            <div style="font-size:.7rem;color:var(--white-60);">Corp credits</div>
          </div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- ============================================================
     CONTACT & FOOTER
============================================================ -->
<section id="contact">
  <div class="container">
    <div class="contact-inner">
      <div class="contact-info reveal-left">
        <span class="section-tag">Get In Touch</span>
        <h2 class="section-title">Let's Build a<br><span class="gradient-text">Cleaner Future</span><br>Together</h2>
        <p class="section-sub" style="text-align:left;margin:0 0 36px;">Have questions, want to partner, or interested in deploying Smart Bins in your city? We'd love to hear from you.</p>
        <div class="contact-items">
          <div class="ci-item">
            <div class="ci-icon"><i class="fas fa-envelope"></i></div>
            <div class="ci-text"><div class="cit-label">Email</div><div class="cit-val">hello@ecotrack.in</div></div>
          </div>
          <div class="ci-item">
            <div class="ci-icon"><i class="fas fa-phone"></i></div>
            <div class="ci-text"><div class="cit-label">Phone</div><div class="cit-val">+91 98765 43210</div></div>
          </div>
          <div class="ci-item">
            <div class="ci-icon"><i class="fas fa-map-marker-alt"></i></div>
            <div class="ci-text"><div class="cit-label">Office</div><div class="cit-val">Jaipur, Rajasthan, India 302001</div></div>
          </div>
        </div>
        <div class="social-links">
          <div class="sl"><i class="fab fa-twitter"></i></div>
          <div class="sl"><i class="fab fa-instagram"></i></div>
          <div class="sl"><i class="fab fa-linkedin"></i></div>
          <div class="sl"><i class="fab fa-github"></i></div>
          <div class="sl"><i class="fab fa-youtube"></i></div>
        </div>
      </div>
      <div class="reveal-right">
        <div class="contact-form-wrap">
          <div class="cf-title">Send us a message 💬</div>
          <div class="cf-grid">
            <div class="cf-field"><label>First Name</label><input type="text" placeholder="Aryan"/></div>
            <div class="cf-field"><label>Last Name</label><input type="text" placeholder="Kumar"/></div>
          </div>
          <div class="cf-field"><label>Email Address</label><input type="email" placeholder="aryan@example.com"/></div>
          <div class="cf-field">
            <label>Subject</label>
            <select>
              <option>General Inquiry</option>
              <option>Smart Bin Deployment</option>
              <option>Partnership</option>
              <option>College/Research Collaboration</option>
              <option>Media & Press</option>
            </select>
          </div>
          <div class="cf-field"><label>Message</label><textarea placeholder="Tell us how we can help build a cleaner future..."></textarea></div>
          <button class="btn btn-primary" style="width:100%;justify-content:center;" onclick="this.innerHTML='<i class=\'fas fa-check\'></i> Message Sent!';this.style.background='linear-gradient(135deg,#00c87e,#00b4a0)';">
            <i class="fas fa-paper-plane"></i> Send Message
          </button>
        </div>
      </div>
    </div>
  </div>

  <!-- FOOTER -->
  <footer>
    <div class="container">
      <div class="footer-inner">
        <div class="footer-brand">
          <div class="nav-logo">
            <div class="logo-icon">♻</div>
            <span>EcoTrack</span>
          </div>
          <p>Turning plastic waste into smart rewards through AI, IoT, and a sustainable credit economy. Making Earth cleaner, one scan at a time.</p>
          <div class="social-links" style="margin-top:18px;">
            <div class="sl"><i class="fab fa-twitter"></i></div>
            <div class="sl"><i class="fab fa-instagram"></i></div>
            <div class="sl"><i class="fab fa-linkedin"></i></div>
          </div>
        </div>
        <div>
          <div class="footer-col-title">Product</div>
          <div class="footer-links">
            <a href="#features">Features</a>
            <a href="#dashboard">Dashboard</a>
            <a href="#scan">AI Scanner</a>
            <a href="#rewards">Rewards</a>
            <a href="#map-section">Recycling Map</a>
          </div>
        </div>
        <div>
          <div class="footer-col-title">Company</div>
          <div class="footer-links">
            <a href="#about">About Us</a>
            <a href="#">Blog</a>
            <a href="#">Careers</a>
            <a href="#">Press Kit</a>
            <a href="#contact">Contact</a>
          </div>
        </div>
        <div>
          <div class="footer-col-title">Legal</div>
          <div class="footer-links">
            <a href="#">Privacy Policy</a>
            <a href="#">Terms of Service</a>
            <a href="#">Cookie Policy</a>
            <a href="#">Data Security</a>
          </div>
        </div>
      </div>
      <div class="footer-bottom">
        <span>© 2026 EcoTrack. Made with <span style="color:var(--coral);">♥</span> for <span>Planet Earth</span></span>
        <span style="color:var(--white-60);font-size:.75rem;">♻ Every plastic recycled makes a difference.</span>
      </div>
    </div>
  </footer>
</section>

<!-- ============================================================
     JAVASCRIPT
============================================================ -->
<script>
// ── Navbar scroll effect ──
const navbar = document.getElementById('navbar');
window.addEventListener('scroll', () => {
  navbar.classList.toggle('scrolled', window.scrollY > 50);
});

// ── Intersection Observer for reveal animations ──
const revealElements = document.querySelectorAll('.reveal, .reveal-left, .reveal-right');
const revealObserver = new IntersectionObserver((entries) => {
  entries.forEach(entry => {
    if (entry.isIntersecting) {
      // Stagger children if parent
      entry.target.classList.add('visible');
    }
  });
}, { threshold: 0.12, rootMargin: '0px 0px -60px 0px' });

revealElements.forEach(el => revealObserver.observe(el));

// ── Stagger feature cards ──
const featCards = document.querySelectorAll('.feat-card');
featCards.forEach((card, i) => {
  card.style.transitionDelay = `${i * 0.08}s`;
});
const kpiCards = document.querySelectorAll('.kpi-card');
kpiCards.forEach((card, i) => {
  card.style.transitionDelay = `${i * 0.06}s`;
});

// ── Active nav link on scroll ──
const sections = document.querySelectorAll('section[id]');
const navLinks = document.querySelectorAll('.nav-links a');
const sectionObserver = new IntersectionObserver((entries) => {
  entries.forEach(entry => {
    if (entry.isIntersecting) {
      navLinks.forEach(link => {
        link.style.color = link.getAttribute('href') === '#' + entry.target.id
          ? 'var(--green-neon)' : '';
      });
    }
  });
}, { threshold: 0.4 });
sections.forEach(s => sectionObserver.observe(s));

// ── Smart Bin click interaction ──
const smartBin = document.getElementById('smartBin');
if (smartBin) {
  smartBin.addEventListener('click', () => {
    smartBin.style.boxShadow = '0 0 80px rgba(0,255,135,.6)';
    smartBin.style.borderColor = 'var(--green-neon)';
    
    // Show toast
    const toast = document.createElement('div');
    toast.style.cssText = `
      position:fixed;bottom:30px;right:30px;z-index:9999;
      background:rgba(3,15,7,.95);border:1px solid var(--green-neon);
      border-radius:14px;padding:16px 24px;
      font-family:var(--font-body);font-size:.88rem;color:var(--white);
      box-shadow:0 8px 40px rgba(0,0,0,.5),0 0 30px rgba(0,255,135,.2);
      animation:slideToast .4s ease;
    `;
    toast.innerHTML = `
      <div style="color:var(--green-neon);font-weight:700;margin-bottom:4px;">⚡ Smart Bin Activated!</div>
      <div style="color:rgba(255,255,255,.6);font-size:.8rem;">+25 EcoCredits deposited to wallet</div>
    `;
    document.body.appendChild(toast);
    setTimeout(() => {
      toast.style.opacity='0'; toast.style.transform='translateY(10px)';
      toast.style.transition='all .4s';
      setTimeout(() => toast.remove(), 400);
    }, 3000);
    setTimeout(() => { smartBin.style.boxShadow=''; smartBin.style.borderColor=''; }, 3000);
  });
}

// ── Redeem card click ──
document.querySelectorAll('.redeem-card').forEach(card => {
  card.addEventListener('click', () => {
    card.style.borderColor = 'rgba(0,255,135,.7)';
    card.style.background = 'rgba(0,255,135,.06)';
    setTimeout(() => { card.style.borderColor=''; card.style.background=''; }, 600);
  });
});

// ── Dashboard nav items (toggle active) ──
document.querySelectorAll('.db-nav-item').forEach(item => {
  item.addEventListener('click', () => {
    document.querySelectorAll('.db-nav-item').forEach(i => i.classList.remove('active'));
    item.classList.add('active');
  });
});

// ── Counter animation for stats ──
function animateCounter(el, target, suffix='') {
  let current = 0;
  const step = target / 60;
  const timer = setInterval(() => {
    current += step;
    if (current >= target) { current = target; clearInterval(timer); }
    el.textContent = Math.floor(current).toLocaleString() + suffix;
  }, 25);
}

const statObserver = new IntersectionObserver((entries) => {
  entries.forEach(entry => {
    if (entry.isIntersecting) {
      const statNums = entry.target.querySelectorAll('.stat-num');
      statNums.forEach(el => {
        const text = el.textContent;
        if (text.includes('2.4M')) animateCounter(el, 2400000, '+').toString().replace(/\d+/,'2.4M');
        if (text.includes('18K')) { el.textContent='0+'; animateCounter(el,18000,'+'); }
        if (text.includes('340T')) { el.textContent='0T'; }
      });
      statObserver.unobserve(entry.target);
    }
  });
}, { threshold: 0.5 });
const heroStats = document.querySelector('.hero-stats');
if (heroStats) statObserver.observe(heroStats);

// ── Toast animation keyframe ──
const style = document.createElement('style');
style.textContent = '@keyframes slideToast{from{transform:translateY(20px);opacity:0;}to{transform:translateY(0);opacity:1;}}';
document.head.appendChild(style);

// ── Map pin hover tooltips ──
document.querySelectorAll('.map-pin').forEach(pin => {
  pin.addEventListener('mouseenter', () => {
    pin.querySelector('.pin-icon').style.transform = 'scale(1.2) rotate(-45deg)';
  });
  pin.addEventListener('mouseleave', () => {
    pin.querySelector('.pin-icon').style.transform = '';
  });
});

// ── Scan object cycling ──
const scanObjects = ['🧴','🍶','🫙','🧃','🥤','🛢️'];
let scanIdx = 0;
const scanObj = document.querySelector('.scan-object');
if (scanObj) {
  setInterval(() => {
    scanObj.style.opacity = '0';
    scanObj.style.transform = 'scale(0.5)';
    setTimeout(() => {
      scanIdx = (scanIdx + 1) % scanObjects.length;
      scanObj.textContent = scanObjects[scanIdx];
      scanObj.style.opacity = '1';
      scanObj.style.transform = 'scale(1)';
    }, 300);
  }, 2500);
  scanObj.style.transition = 'opacity .3s, transform .3s';
}

// ── Parallax subtle on hero ──
document.addEventListener('mousemove', (e) => {
  const orbs = document.querySelectorAll('.orb');
  const x = (e.clientX / window.innerWidth - 0.5) * 20;
  const y = (e.clientY / window.innerHeight - 0.5) * 20;
  orbs.forEach((orb, i) => {
    const factor = (i + 1) * 0.4;
    orb.style.transform = `translate(${x * factor}px, ${y * factor}px)`;
  });
});
</script>
</body>
</html>
