```html
<!DOCTYPE html>
<html lang="en" class="scroll-smooth">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Abdullah Shafi | Cyber Security Expert, Scout & Pro FC Mobile Gamer</title>
  <!-- Tailwind CSS -->
  <script src="https://cdn.tailwindcss.com"></script>
  <!-- Google Fonts: Inter & Orbitron for Cyber-Tech feel -->
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800&family=Orbitron:wght@500;700;900&display=swap" rel="stylesheet">
  <!-- Font Awesome Icons -->
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/css/all.min.css" />
  <!-- Tone.js for Retro Arcade Sound Effects -->
  <script src="https://cdnjs.cloudflare.com/ajax/libs/tone/14.8.49/Tone.js"></script>
  <!-- Leaflet CSS for Interactive Bangladesh Map -->
  <link rel="stylesheet" href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css" />
  <script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js"></script>

  <script>
    tailwind.config = {
      theme: {
        extend: {
          fontFamily: {
            sans: ['Inter', 'sans-serif'],
            cyber: ['Orbitron', 'sans-serif'],
          },
          colors: {
            cyberbg: '#070b14',
            cybercard: '#0e1628',
            cybercyan: '#00f0ff',
            argblue: '#75aadb',
            goldaccent: '#ffd700',
          }
        }
      }
    }
  </script>

  <style>
    body {
      background-color: #070b14;
      color: #e2e8f0;
      overflow-x: hidden;
    }

    /* Cyber Grid Background */
    .cyber-grid {
      background-image: 
        linear-gradient(to right, rgba(0, 240, 255, 0.05) 1px, transparent 1px),
        linear-gradient(to bottom, rgba(0, 240, 255, 0.05) 1px, transparent 1px);
      background-size: 40px 40px;
    }

    /* Glowing borders & text */
    .glow-cyan {
      box-shadow: 0 0 20px rgba(0, 240, 255, 0.25);
    }
    .glow-gold {
      box-shadow: 0 0 22px rgba(255, 215, 0, 0.3);
    }
    .glow-arg {
      box-shadow: 0 0 22px rgba(117, 170, 219, 0.35);
    }

    /* FC Mobile Card Styling */
    .fc-card {
      background: linear-gradient(145deg, #1e293b 0%, #0f172a 55%, #1e1b4b 100%);
      border: 2px solid #ffd700;
      clip-path: polygon(12% 0%, 88% 0%, 100% 14%, 100% 84%, 50% 100%, 0% 84%, 0% 14%);
      transition: transform 0.25s ease, box-shadow 0.25s ease;
    }
    .fc-card:hover {
      transform: translateY(-6px) scale(1.06);
      z-index: 30;
    }
    .fc-card-icon {
      background: linear-gradient(145deg, #fefce8 0%, #fde047 35%, #ca8a04 100%);
      color: #1e1b4b;
      border: 2px solid #ffffff;
    }
    .fc-card-utoty {
      background: linear-gradient(145deg, #0c4a6e 0%, #1d4ed8 45%, #312e81 100%);
      border: 2px solid #38bdf8;
    }

    /* Football Pitch Stripes */
    .pitch-bg {
      background: repeating-linear-gradient(
        0deg,
        #14532d,
        #14532d 42px,
        #166534 42px,
        #166534 84px
      );
    }

    /* Custom Scrollbar */
    ::-webkit-scrollbar {
      width: 8px;
    }
    ::-webkit-scrollbar-track {
      background: #070b14;
    }
    ::-webkit-scrollbar-thumb {
      background: #1e293b;
      border-radius: 9999px;
    }
    ::-webkit-scrollbar-thumb:hover {
      background: #00f0ff;
    }

    /* Pulsing Map Marker */
    @keyframes pulseRing {
      0% { transform: scale(0.8); opacity: 0.9; }
      100% { transform: scale(2.4); opacity: 0; }
    }
    .map-pulse {
      animation: pulseRing 1.8s infinite ease-out;
    }

    /* Leaflet dark theme override */
    .leaflet-container {
      background: #0b1324 !important;
      border-radius: 1rem;
      z-index: 10;
    }
  </style>
</head>
<body class="cyber-grid font-sans antialiased selection:bg-cyan-400 selection:text-slate-950">

  <!-- Top Navigation Bar -->
  <header class="sticky top-0 z-50 backdrop-blur-md bg-[#070b14]/85 border-b border-cyan-500/20">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="flex items-center justify-between h-16">
        <!-- Brand Logo -->
        <a href="#home" class="flex items-center gap-2.5 group">
          <div class="w-10 h-10 rounded-xl bg-gradient-to-br from-cyan-400 to-blue-600 flex items-center justify-center text-slate-950 font-cyber font-black text-lg shadow-lg group-hover:scale-105 transition">
            AS
          </div>
          <div>
            <span class="font-cyber font-bold text-white tracking-wider text-sm sm:text-base block leading-none">ABDULLAH SHAFI</span>
            <span class="text-[11px] text-cyan-400 font-medium tracking-widest uppercase">Cyber • Scout • FC Pro</span>
          </div>
        </a>

        <!-- Desktop Menu -->
        <nav class="hidden lg:flex items-center gap-6 text-sm font-medium text-slate-300">
          <a href="#skills" class="hover:text-cyan-400 transition">Skills & Certs</a>
          <a href="#scouting" class="hover:text-amber-400 transition">Scouting</a>
          <a href="#argentina" class="hover:text-sky-300 transition">Argentina Drills</a>
          <a href="#fcmobile" class="hover:text-yellow-400 transition">FC Mobile 4-3-3</a>
          <a href="#arcade" class="hover:text-emerald-400 transition">12 Games Arcade</a>
          <a href="#tools" class="hover:text-purple-400 transition">Smart Tools</a>
          <a href="#location" class="hover:text-rose-400 transition">Narsingdi Map</a>
        </nav>

        <!-- Mobile Menu Toggle -->
        <button id="mobileMenuBtn" class="lg:hidden p-2.5 rounded-xl bg-slate-800/80 text-cyan-400 border border-cyan-500/30 hover:bg-slate-700">
          <i class="fa-solid fa-bars text-lg"></i>
        </button>
      </div>
    </div>

    <!-- Mobile Dropdown -->
    <div id="mobileMenu" class="hidden lg:hidden bg-[#0b1222] border-b border-cyan-500/20 px-4 pt-2 pb-4 space-y-2">
      <a href="#skills" class="block py-2 px-3 rounded-lg hover:bg-slate-800 text-slate-200">Skills & Certificates</a>
      <a href="#scouting" class="block py-2 px-3 rounded-lg hover:bg-slate-800 text-amber-300">Scouting & President's Award</a>
      <a href="#argentina" class="block py-2 px-3 rounded-lg hover:bg-slate-800 text-sky-300">Argentina Exercises</a>
      <a href="#fcmobile" class="block py-2 px-3 rounded-lg hover:bg-slate-800 text-yellow-300">FC Mobile 4-3-3 Squad</a>
      <a href="#arcade" class="block py-2 px-3 rounded-lg hover:bg-slate-800 text-emerald-300">12 Playable Games Arcade</a>
      <a href="#tools" class="block py-2 px-3 rounded-lg hover:bg-slate-800 text-purple-300">Smart Detectors Lab</a>
      <a href="#location" class="block py-2 px-3 rounded-lg hover:bg-slate-800 text-rose-300">Bangladesh Map (Narsingdi)</a>
    </div>
  </header>

  <!-- 1. HERO & CYBER-TECH PROFILE SECTION -->
  <section id="home" class="relative pt-10 pb-16 sm:pt-16 sm:pb-24 overflow-hidden">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 relative z-10">
      <div class="grid grid-cols-1 lg:grid-cols-12 gap-10 items-center">
        <!-- Left Content -->
        <div class="lg:col-span-7 space-y-6">
          <div class="inline-flex items-center gap-2 px-3.5 py-1.5 rounded-full bg-cyan-500/10 border border-cyan-400/30 text-cyan-300 text-xs sm:text-sm font-semibold">
            <span class="w-2 h-2 rounded-full bg-cyan-400 animate-ping"></span>
            Class 8 Student • Nasima Kadir Molla High School & Homes
          </div>

          <h1 class="text-4xl sm:text-5xl lg:text-6xl font-cyber font-black text-white leading-tight">
            Assalamu Alaikum, I'm <br/>
            <span class="bg-gradient-to-r from-cyan-400 via-sky-300 to-amber-300 bg-clip-text text-transparent">
              Abdullah Shafi
            </span>
          </h1>

          <p class="text-slate-300 text-base sm:text-lg leading-relaxed max-w-2xl">
            From <span class="text-cyan-400 font-semibold">Balanagar, Narsingdi, Bangladesh</span> — I am a passionate 
            <span class="text-white font-semibold">Cyber Security Expert</span>, Full-Stack Web Builder, PC Hardware Architect, Robotics Maker, 
            <span class="text-amber-400 font-semibold">Patrol Leader & President's Scout Award</span> achiever, die-hard <span class="text-sky-300 font-semibold">Argentina ⭐⭐⭐</span> supporter, and Pro <span class="text-yellow-400 font-semibold">FC Mobile</span> tactician!
          </p>

          <!-- Role Pills -->
          <div class="flex flex-wrap gap-2.5 pt-1">
            <span class="px-3 py-1.5 rounded-xl bg-slate-800/90 border border-cyan-500/30 text-cyan-300 text-xs font-semibold flex items-center gap-1.5">
              <i class="fa-solid fa-shield-halved"></i> Cyber Security Expert
            </span>
            <span class="px-3 py-1.5 rounded-xl bg-slate-800/90 border border-blue-500/30 text-blue-300 text-xs font-semibold flex items-center gap-1.5">
              <i class="fa-solid fa-code"></i> Web & Software Dev
            </span>
            <span class="px-3 py-1.5 rounded-xl bg-slate-800/90 border border-purple-500/30 text-purple-300 text-xs font-semibold flex items-center gap-1.5">
              <i class="fa-solid fa-microchip"></i> PC Builder & Robotics
            </span>
            <span class="px-3 py-1.5 rounded-xl bg-slate-800/90 border border-amber-500/30 text-amber-300 text-xs font-semibold flex items-center gap-1.5">
              <i class="fa-solid fa-award"></i> President's Scout Award
            </span>
            <span class="px-3 py-1.5 rounded-xl bg-slate-800/90 border border-yellow-500/30 text-yellow-300 text-xs font-semibold flex items-center gap-1.5">
              <i class="fa-solid fa-gamepad"></i> FC Mobile Pro (4-3-3)
            </span>
          </div>

          <!-- Action Buttons -->
          <div class="flex flex-wrap gap-4 pt-2">
            <a href="#arcade" class="px-6 py-3.5 rounded-2xl bg-gradient-to-r from-cyan-500 to-blue-600 hover:from-cyan-400 hover:to-blue-500 text-slate-950 font-bold text-sm sm:text-base shadow-lg shadow-cyan-500/25 transition flex items-center gap-2">
              <i class="fa-solid fa-joystick"></i> Play 12 Arcade Games
            </a>
            <a href="#fcmobile" class="px-6 py-3.5 rounded-2xl bg-slate-800/90 hover:bg-slate-700 text-yellow-300 border border-yellow-500/40 font-bold text-sm sm:text-base transition flex items-center gap-2">
              <i class="fa-solid fa-futbol"></i> Inspect FC Mobile Squad
            </a>
          </div>
        </div>

        <!-- Right Cyber ID Card -->
        <div class="lg:col-span-5">
          <div class="rounded-3xl bg-[#0e1628]/95 border border-cyan-500/30 p-6 sm:p-8 glow-cyan relative overflow-hidden">
            <div class="absolute top-0 right-0 w-36 h-36 bg-cyan-500/10 rounded-full blur-2xl"></div>
            <div class="flex items-center justify-between border-b border-slate-700/80 pb-4 mb-5">
              <div class="flex items-center gap-3">
                <div class="w-14 h-14 rounded-2xl bg-gradient-to-tr from-cyan-400 via-sky-400 to-amber-300 p-0.5">
                  <div class="w-full h-full rounded-2xl bg-slate-950 flex items-center justify-center">
                    <i class="fa-solid fa-user-secret text-2xl text-cyan-400"></i>
                  </div>
                </div>
                <div>
                  <h2 class="font-cyber font-bold text-lg text-white">OPERATIVE ID: #BD-08</h2>
                  <p class="text-xs text-emerald-400 font-mono"><i class="fa-solid fa-circle text-[8px] mr-1"></i> STATUS: ONLINE • NARSINGDI</p>
                </div>
              </div>
              <span class="px-2.5 py-1 rounded-lg bg-amber-500/20 text-amber-300 border border-amber-400/30 text-xs font-bold">
                LVL 99
              </span>
            </div>

            <div class="space-y-3.5 text-sm">
              <div class="flex justify-between items-center bg-slate-900/70 px-4 py-2.5 rounded-xl border border-slate-800">
                <span class="text-slate-400"><i class="fa-solid fa-school text-cyan-400 mr-2"></i>School</span>
                <span class="text-white font-semibold text-right">Nasima Kadir Molla High School & Homes</span>
              </div>
              <div class="flex justify-between items-center bg-slate-900/70 px-4 py-2.5 rounded-xl border border-slate-800">
                <span class="text-slate-400"><i class="fa-solid fa-graduation-cap text-cyan-400 mr-2"></i>Class</span>
                <span class="text-white font-semibold">Class Eight (8)</span>
              </div>
              <div class="flex justify-between items-center bg-slate-900/70 px-4 py-2.5 rounded-xl border border-slate-800">
                <span class="text-slate-400"><i class="fa-solid fa-location-dot text-rose-400 mr-2"></i>Hometown</span>
                <span class="text-white font-semibold">Balanagar, Narsingdi, Bangladesh</span>
              </div>
              <div class="flex justify-between items-center bg-slate-900/70 px-4 py-2.5 rounded-xl border border-slate-800">
                <span class="text-slate-400"><i class="fa-solid fa-compass text-amber-400 mr-2"></i>Scout Rank</span>
                <span class="text-amber-300 font-semibold">Patrol Leader (President's Award)</span>
              </div>
              <div class="flex justify-between items-center bg-slate-900/70 px-4 py-2.5 rounded-xl border border-slate-800">
                <span class="text-slate-400"><i class="fa-solid fa-trophy text-sky-400 mr-2"></i>Fav Team</span>
                <span class="text-sky-300 font-semibold">Argentina ⭐⭐⭐</span>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- TECH STACK, HARDWARE, ROBOTICS & CERTIFICATES VAULT -->
  <section id="skills" class="py-16 bg-[#090f1d] border-y border-slate-800/80">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="text-center max-w-3xl mx-auto mb-12">
        <span class="text-cyan-400 font-cyber text-xs tracking-widest uppercase">Arsenal & Credentials</span>
        <h2 class="text-3xl sm:text-4xl font-cyber font-bold text-white mt-2">Tech Skills, Robotics & Certificates</h2>
        <p class="text-slate-400 mt-3 text-sm sm:text-base">
          Mastering code, cyber defense, custom computer hardware assembly, robotics engineering, and certified achievements.
        </p>
      </div>

      <!-- Skills Grid -->
      <div class="grid grid-cols-2 sm:grid-cols-3 lg:grid-cols-5 gap-4 mb-12">
        <div class="p-5 rounded-2xl bg-[#0e1628] border border-slate-800 hover:border-cyan-400/60 transition group text-center">
          <i class="fa-solid fa-user-shield text-3xl text-cyan-400 mb-3 group-hover:scale-110 transition"></i>
          <h3 class="font-bold text-white text-sm sm:text-base">Cyber Security</h3>
          <p class="text-xs text-slate-400 mt-1">Ethical Defense & Network Safety</p>
        </div>
        <div class="p-5 rounded-2xl bg-[#0e1628] border border-slate-800 hover:border-orange-400/60 transition group text-center">
          <i class="fa-brands fa-html5 text-3xl text-orange-500 mb-3 group-hover:scale-110 transition"></i>
          <h3 class="font-bold text-white text-sm sm:text-base">HTML5 & CSS3</h3>
          <p class="text-xs text-slate-400 mt-1">Modern Responsive Web UI</p>
        </div>
        <div class="p-5 rounded-2xl bg-[#0e1628] border border-slate-800 hover:border-yellow-400/60 transition group text-center">
          <i class="fa-brands fa-js text-3xl text-yellow-400 mb-3 group-hover:scale-110 transition"></i>
          <h3 class="font-bold text-white text-sm sm:text-base">JavaScript</h3>
          <p class="text-xs text-slate-400 mt-1">Interactive Apps & Game Logic</p>
        </div>
        <div class="p-5 rounded-2xl bg-[#0e1628] border border-slate-800 hover:border-blue-400/60 transition group text-center">
          <i class="fa-brands fa-python text-3xl text-blue-400 mb-3 group-hover:scale-110 transition"></i>
          <h3 class="font-bold text-white text-sm sm:text-base">Python</h3>
          <p class="text-xs text-slate-400 mt-1">Scripting, Automation & Security</p>
        </div>
        <div class="p-5 rounded-2xl bg-[#0e1628] border border-slate-800 hover:border-indigo-400/60 transition group text-center">
          <i class="fa-solid fa-terminal text-3xl text-indigo-400 mb-3 group-hover:scale-110 transition"></i>
          <h3 class="font-bold text-white text-sm sm:text-base">C & C++</h3>
          <p class="text-xs text-slate-400 mt-1">Algorithms & Embedded Logic</p>
        </div>
        <div class="p-5 rounded-2xl bg-[#0e1628] border border-slate-800 hover:border-emerald-400/60 transition group text-center">
          <i class="fa-solid fa-globe text-3xl text-emerald-400 mb-3 group-hover:scale-110 transition"></i>
          <h3 class="font-bold text-white text-sm sm:text-base">Website Building</h3>
          <p class="text-xs text-slate-400 mt-1">End-to-End Site Deployment</p>
        </div>
        <div class="p-5 rounded-2xl bg-[#0e1628] border border-slate-800 hover:border-rose-400/60 transition group text-center">
          <i class="fa-solid fa-desktop text-3xl text-rose-400 mb-3 group-hover:scale-110 transition"></i>
          <h3 class="font-bold text-white text-sm sm:text-base">PC Building</h3>
          <p class="text-xs text-slate-400 mt-1">Custom Rig Assembly & Tuning</p>
        </div>
        <div class="p-5 rounded-2xl bg-[#0e1628] border border-slate-800 hover:border-purple-400/60 transition group text-center">
          <i class="fa-solid fa-memory text-3xl text-purple-400 mb-3 group-hover:scale-110 transition"></i>
          <h3 class="font-bold text-white text-sm sm:text-base">Computer Parts</h3>
          <p class="text-xs text-slate-400 mt-1">CPU, GPU, RAM & Motherboard Diagnostics</p>
        </div>
        <div class="p-5 rounded-2xl bg-[#0e1628] border border-slate-800 hover:border-teal-400/60 transition group text-center">
          <i class="fa-solid fa-robot text-3xl text-teal-400 mb-3 group-hover:scale-110 transition"></i>
          <h3 class="font-bold text-white text-sm sm:text-base">Robotics Making</h3>
          <p class="text-xs text-slate-400 mt-1">Sensors, Microcontrollers & Bots</p>
        </div>
        <div class="p-5 rounded-2xl bg-[#0e1628] border border-amber-500/40 hover:border-amber-400 transition group text-center">
          <i class="fa-solid fa-certificate text-3xl text-amber-400 mb-3 group-hover:scale-110 transition"></i>
          <h3 class="font-bold text-white text-sm sm:text-base">Certified Pro</h3>
          <p class="text-xs text-amber-300 mt-1">Multiple Verified Honors</p>
        </div>
      </div>

      <!-- Verified Certificates Vault -->
      <div class="rounded-3xl bg-[#0e1628] border border-cyan-500/25 p-6 sm:p-8">
        <div class="flex flex-col sm:flex-row sm:items-center justify-between gap-4 mb-6">
          <div>
            <h3 class="font-cyber font-bold text-xl text-white flex items-center gap-2">
              <i class="fa-solid fa-vault text-cyan-400"></i> Verified Certificates Vault
            </h3>
            <p class="text-xs sm:text-sm text-slate-400">Click any certificate to inspect Abdullah Shafi's credential details</p>
          </div>
          <span class="px-3 py-1 rounded-full bg-cyan-500/10 text-cyan-300 border border-cyan-500/30 text-xs font-semibold self-start sm:self-auto">
            6 Official Credentials
          </span>
        </div>

        <div id="certGrid" class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-4">
          <!-- Populated cleanly via JS -->
        </div>
      </div>
    </div>
  </section>

  <!-- 2. SCOUTING & LEADERSHIP HONOR SECTION -->
  <section id="scouting" class="py-16 relative">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="rounded-3xl bg-gradient-to-br from-[#0f1f18] via-[#0e1628] to-[#1c1917] border border-amber-50# Al-shafi.github.io
