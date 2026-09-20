<!DOCTYPE html>
<html lang="en" class="scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Wahab Qadeer | AI & Software Architecture</title>
    
    <!-- Premium Fonts: Inter for high-legibility body, Space Grotesk for sharp headings -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Fira+Code:wght@400;500;600&family=Inter:wght@300;400;500;600;700&family=Space+Grotesk:wght@400;500;600;700;800&display=swap" rel="stylesheet">
    
    <!-- FontAwesome -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    
    <!-- Chart.js -->
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    
    <script>
        tailwind.config = {
            darkMode: 'class',
            theme: {
                extend: {
                    fontFamily: {
                        heading: ['"Space Grotesk"', 'sans-serif'],
                        body: ['Inter', 'sans-serif'],
                        code: ['"Fira Code"', 'monospace'],
                    },
                    colors: {
                        system: {
                            950: '#020806',
                            900: '#03120f',
                            800: '#06241e',
                            700: '#09362d',
                            600: '#0d4f42'
                        },
                        neon: {
                            emerald: '#10b981',
                            teal: '#14b8a6',
                            lime: '#a3e635',
                            cyan: '#06b6d4'
                        }
                    },
                    animation: {
                        'float-smooth': 'floatSmooth 6s ease-in-out infinite',
                        'pulse-glow': 'pulseGlow 4s ease-in-out infinite alternate',
                        'spin-slow': 'spin 12s linear infinite',
                    },
                    keyframes: {
                        floatSmooth: {
                            '0%, 100%': { transform: 'translateY(0) scale(1)' },
                            '50%': { transform: 'translateY(-15px) scale(1.01)' },
                        },
                        pulseGlow: {
                            '0%': { opacity: 0.4, transform: 'scale(1)' },
                            '100%': { opacity: 0.8, transform: 'scale(1.1)' },
                        }
                    }
                }
            }
        }
    </script>

    <style>
        /* Base Reset & Smooth Typography */
        body {
            background-color: #020806;
            color: #e2e8f0;
            font-family: 'Inter', sans-serif;
            overflow-x: hidden;
            -webkit-font-smoothing: antialiased;
            -moz-osx-font-smoothing: grayscale;
        }

        h1, h2, h3, h4, h5, h6, .font-heading {
            font-family: 'Space Grotesk', sans-serif;
            letter-spacing: -0.02em;
        }

        /* Ambient Background Canvas */
        #ambient-canvas {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -10;
            pointer-events: none;
            opacity: 0.6;
        }

        /* Glassmorphism Panels (Clean & Elegant) */
        .glass-card {
            background: rgba(6, 36, 30, 0.4);
            backdrop-filter: blur(16px);
            -webkit-backdrop-filter: blur(16px);
            border: 1px solid rgba(20, 184, 166, 0.15);
            box-shadow: 0 4px 30px rgba(0, 0, 0, 0.3);
            transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
        }

        .glass-card:hover {
            background: rgba(9, 54, 45, 0.6);
            border-color: rgba(16, 185, 129, 0.4);
            box-shadow: 0 10px 40px rgba(16, 185, 129, 0.15);
            transform: translateY(-4px);
        }

        /* Image Container (Left Side, Non-Circular, Elegant) */
        .image-showcase {
            position: relative;
            width: 100%;
            max-width: 400px; /* Constrains width so text always has room */
            margin: 0 auto;
            border-radius: 1.5rem;
            padding: 8px;
            background: linear-gradient(145deg, rgba(20,184,166,0.3), rgba(3,18,15,0.8));
            box-shadow: 0 20px 50px rgba(0,0,0,0.5), inset 0 0 20px rgba(16,185,129,0.2);
            z-index: 10;
        }

        .image-showcase img {
            width: 100%;
            height: auto;
            border-radius: 1rem;
            object-fit: cover;
            box-shadow: 0 10px 30px rgba(0,0,0,0.8);
            filter: contrast(1.02) brightness(0.98);
            transition: transform 0.6s ease, filter 0.6s ease;
        }

        .image-showcase:hover img {
            transform: scale(1.03);
            filter: contrast(1.05) brightness(1.02);
        }

        /* Background Glows for Image */
        .image-glow {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            width: 120%;
            height: 120%;
            background: radial-gradient(circle, rgba(16,185,129,0.15) 0%, rgba(0,0,0,0) 70%);
            filter: blur(40px);
            z-index: 1;
            pointer-events: none;
        }

        /* Text Gradients */
        .text-gradient {
            background: linear-gradient(135deg, #10b981 0%, #14b8a6 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }
        
        .text-gradient-lime {
            background: linear-gradient(135deg, #10b981 0%, #a3e635 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        /* Clean Reveal Animations */
        .reveal-up {
            opacity: 0;
            transform: translateY(40px);
            transition: opacity 0.8s ease-out, transform 0.8s cubic-bezier(0.16, 1, 0.3, 1);
        }
        
        .reveal-up.active {
            opacity: 1;
            transform: translateY(0);
        }

        /* Typing Effect Caret */
        .type-caret::after {
            content: '';
            display: inline-block;
            width: 3px;
            height: 1em;
            background-color: #10b981;
            margin-left: 4px;
            vertical-align: middle;
            animation: blink 1s step-end infinite;
        }
        @keyframes blink { 50% { opacity: 0; } }

        /* Chart Containers - Enforces exact constraints so layout never breaks */
        .chart-container {
            position: relative;
            width: 100%;
            height: 300px;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        /* Modals */
        .modal-overlay {
            position: fixed; inset: 0;
            background: rgba(2, 8, 6, 0.9);
            backdrop-filter: blur(10px);
            z-index: 100;
            display: flex; align-items: center; justify-content: center;
            opacity: 0; pointer-events: none;
            transition: opacity 0.4s ease;
        }
        .modal-overlay.active { opacity: 1; pointer-events: all; }
        
        .modal-box {
            background: #03120f;
            border: 1px solid rgba(20, 184, 166, 0.3);
            border-radius: 1.5rem;
            width: 90%; max-width: 800px; max-height: 85vh;
            overflow-y: auto;
            transform: translateY(30px);
            transition: transform 0.4s cubic-bezier(0.16, 1, 0.3, 1);
            box-shadow: 0 25px 50px rgba(0,0,0,0.5);
            padding: 2.5rem;
        }
        .modal-overlay.active .modal-box { transform: translateY(0); }

        /* Custom Scrollbar */
        ::-webkit-scrollbar { width: 8px; }
        ::-webkit-scrollbar-track { background: #020806; }
        ::-webkit-scrollbar-thumb { background: #09362d; border-radius: 4px; }
        ::-webkit-scrollbar-thumb:hover { background: #10b981; }
    </style>
</head>
<body class="selection:bg-neon-emerald selection:text-system-950">

    <!-- Ambient Elegant Canvas Background -->
    <canvas id="ambient-canvas"></canvas>

    <!-- Header Navigation -->
    <header class="fixed top-0 left-0 w-full z-50 px-6 py-4 transition-all duration-300" id="header">
        <div class="max-w-7xl mx-auto">
            <div class="glass-card rounded-2xl px-8 py-4 flex items-center justify-between">
                
                <a href="#" class="font-heading font-bold text-2xl text-white flex items-center gap-3 group">
                    <div class="w-10 h-10 rounded-lg bg-gradient-to-br from-neon-emerald to-neon-teal flex items-center justify-center text-system-950 font-black shadow-[0_0_15px_rgba(16,185,129,0.4)] group-hover:rotate-12 transition-transform">
                        WQ
                    </div>
                    <span class="tracking-wide">Wahab<span class="text-neon-emerald">.ai</span></span>
                </a>

                <nav class="hidden md:flex items-center space-x-10 text-sm font-medium text-slate-300">
                    <a href="#about" class="hover:text-neon-emerald transition-colors">Profile</a>
                    <a href="#analytics" class="hover:text-neon-emerald transition-colors">Analytics</a>
                    <a href="#projects" class="hover:text-neon-emerald transition-colors">Systems</a>
                    <a href="#connect" class="px-5 py-2 rounded-lg bg-neon-emerald/10 border border-neon-emerald/30 text-neon-emerald hover:bg-neon-emerald hover:text-system-950 transition-all font-bold">
                        Initialize Connection
                    </a>
                </nav>
            </div>
        </div>
    </header>

    <main class="relative pt-32 pb-20">

        <!-- HERO SECTION: Perfectly Arranged Text & Image -->
        <section id="about" class="min-h-[85vh] flex items-center justify-center px-6 lg:px-8 py-12">
            <div class="max-w-7xl mx-auto w-full">
                
                <!-- 
                  Layout Logic: 
                  lg:flex-row makes it side-by-side on desktop.
                  gap-16 ensures massive breathing room between image and text. 
                  items-center keeps them perfectly vertically aligned.
                -->
                <div class="flex flex-col lg:flex-row items-center gap-16 lg:gap-20">
                    
                    <!-- LEFT SIDE: Profile Picture (Non-Circular, Elegant) -->
                    <div class="w-full lg:w-5/12 flex justify-center reveal-up">
                        <div class="relative w-full max-w-sm animate-float-smooth">
                            <!-- Soft glow behind image -->
                            <div class="image-glow"></div>
                            
                            <div class="image-showcase">
                                <img 
                                    src="WhatsApp Image 2026-08-13 at 1.09.24 PM.jpeg" 
                                    alt="Wahab Qadeer" 
                                    onerror="this.src='https://placehold.co/600x800/06241e/10b981?text=Wahab+Qadeer'"
                                >
                            </div>
                            
                            <!-- Floating Info Tag -->
                            <div class="absolute -bottom-6 -right-6 glass-card px-6 py-3 rounded-xl border border-neon-emerald/40 text-sm font-code font-bold text-white shadow-xl z-20 flex items-center gap-3">
                                <span class="relative flex h-3 w-3">
                                  <span class="animate-ping absolute inline-flex h-full w-full rounded-full bg-neon-emerald opacity-75"></span>
                                  <span class="relative inline-flex rounded-full h-3 w-3 bg-neon-emerald"></span>
                                </span>
                                System Online
                            </div>
                        </div>
                    </div>

                    <!-- RIGHT SIDE: Well-Managed, Breathable Text -->
                    <div class="w-full lg:w-7/12 flex flex-col items-center lg:items-start text-center lg:text-left reveal-up" style="transition-delay: 200ms;">
                        
                        <!-- Top Label -->
                        <div class="inline-block px-4 py-1.5 rounded-full bg-system-800 border border-neon-teal/30 text-neon-teal text-xs font-code uppercase tracking-widest mb-6">
                            <i class="fa-solid fa-microchip mr-2"></i> BS(AI) Candidate @ BIIT
                        </div>

                        <!-- Main Headline -->
                        <h1 class="text-5xl sm:text-6xl lg:text-7xl font-extrabold tracking-tight text-white leading-tight mb-6">
                            Architecting <br class="hidden sm:block">
                            <span class="text-gradient">Intelligent</span> Systems.
                        </h1>

                        <!-- Dynamic Typing Row -->
                        <div class="text-xl sm:text-2xl font-medium text-slate-300 mb-6 flex items-center justify-center lg:justify-start h-8">
                            <span class="mr-2">I specialize in</span>
                            <span id="typing-text" class="font-code text-neon-emerald font-bold type-caret"></span>
                        </div>

                        <!-- Highly Legible Bio Paragraph -->
                        <p class="text-slate-400 text-lg leading-loose max-w-2xl mx-auto lg:mx-0 font-light mb-10">
                            Computer Science undergraduate focused on Artificial Intelligence. I bridge the gap between raw data sets, complex algorithmic logic, and robust object-oriented software architectures to solve practical, real-world problems.
                        </p>

                        <!-- Call to Actions & Metrics -->
                        <div class="flex flex-col sm:flex-row items-center gap-8 w-full justify-center lg:justify-start">
                            
                            <a href="#analytics" class="px-8 py-4 rounded-xl bg-neon-emerald text-system-950 font-bold text-base hover:bg-neon-lime hover:shadow-[0_0_30px_rgba(16,185,129,0.4)] transition-all flex items-center gap-3">
                                <i class="fa-solid fa-chart-line"></i> View Analytics
                            </a>
                            
                            <!-- Clean Data Points -->
                            <div class="flex items-center gap-6 px-6 py-3 rounded-xl bg-system-900 border border-system-800">
                                <div class="text-left">
                                    <span class="block text-2xl font-black text-white counter" data-target="15">0</span>
                                    <span class="text-[10px] text-neon-teal uppercase tracking-widest font-bold">Projects Built</span>
                                </div>
                                <div class="w-px h-10 bg-system-700"></div>
                                <div class="text-left">
                                    <span class="block text-2xl font-black text-white counter" data-target="98">0</span>
                                    <span class="text-[10px] text-neon-lime uppercase tracking-widest font-bold">Efficiency %</span>
                                </div>
                            </div>
                        </div>

                    </div>
                </div>
            </div>
        </section>

        <!-- ANALYTICS DASHBOARD: Chart.js Graphs (Well Arranged Grid) -->
        <section id="analytics" class="py-24 px-6 lg:px-8 border-t border-system-800 bg-system-950/50">
            <div class="max-w-7xl mx-auto">
                
                <div class="text-center mb-16 reveal-up">
                    <span class="text-xs font-code text-neon-teal uppercase tracking-widest block mb-3 font-bold">Telemetry</span>
                    <h2 class="text-4xl font-extrabold text-white">Live <span class="text-gradient">Growth Dashboard</span></h2>
                    <p class="text-slate-400 mt-4 max-w-2xl mx-auto text-base leading-relaxed">
                        Data-driven visualization of my technical stack, algorithmic proficiencies, and learning velocity over time.
                    </p>
                </div>

                <!-- Grid Layout for Charts: 2 columns on desktop, 1 on mobile -->
                <div class="grid grid-cols-1 lg:grid-cols-2 gap-8 reveal-up" style="transition-delay: 200ms;">
                    
                    <!-- Chart 1: Skill Distribution (Doughnut) -->
                    <div class="glass-card p-8 rounded-3xl flex flex-col">
                        <div class="mb-6">
                            <h3 class="text-xl font-bold text-white flex items-center gap-3">
                                <i class="fa-solid fa-chart-pie text-neon-emerald"></i> Skill Distribution
                            </h3>
                            <p class="text-xs text-slate-500 font-code uppercase tracking-wider mt-1">Resource Allocation</p>
                        </div>
                        <div class="chart-container">
                            <canvas id="chartDoughnut"></canvas>
                        </div>
                    </div>

                    <!-- Chart 2: Competency (Radar) -->
                    <div class="glass-card p-8 rounded-3xl flex flex-col">
                        <div class="mb-6">
                            <h3 class="text-xl font-bold text-white flex items-center gap-3">
                                <i class="fa-solid fa-bullseye text-neon-teal"></i> Core Competencies
                            </h3>
                            <p class="text-xs text-slate-500 font-code uppercase tracking-wider mt-1">Vector Analysis Matrix</p>
                        </div>
                        <div class="chart-container">
                            <canvas id="chartRadar"></canvas>
                        </div>
                    </div>

                    <!-- Chart 3: Tech Languages (Polar Area) -->
                    <div class="glass-card p-8 rounded-3xl flex flex-col">
                        <div class="mb-6">
                            <h3 class="text-xl font-bold text-white flex items-center gap-3">
                                <i class="fa-solid fa-layer-group text-neon-lime"></i> Language Mastery
                            </h3>
                            <p class="text-xs text-slate-500 font-code uppercase tracking-wider mt-1">Syntax & Frameworks</p>
                        </div>
                        <div class="chart-container">
                            <canvas id="chartPolar"></canvas>
                        </div>
                    </div>

                    <!-- Chart 4: Learning Velocity (Mixed Bar/Line) -->
                    <div class="glass-card p-8 rounded-3xl flex flex-col">
                        <div class="mb-6">
                            <h3 class="text-xl font-bold text-white flex items-center gap-3">
                                <i class="fa-solid fa-chart-line text-neon-cyan"></i> Learning Velocity
                            </h3>
                            <p class="text-xs text-slate-500 font-code uppercase tracking-wider mt-1">12-Month Progression Trend</p>
                        </div>
                        <div class="chart-container">
                            <canvas id="chartMixed"></canvas>
                        </div>
                    </div>

                </div>
            </div>
        </section>

        <!-- PROJECTS / SYSTEMS SECTION -->
        <section id="projects" class="py-24 px-6 lg:px-8 border-t border-system-800">
            <div class="max-w-7xl mx-auto">
                
                <div class="flex flex-col md:flex-row justify-between items-end mb-16 gap-6 reveal-up">
                    <div>
                        <span class="text-xs font-code text-neon-lime uppercase tracking-widest block mb-3 font-bold">Deployment</span>
                        <h2 class="text-4xl font-extrabold text-white">Engineered <span class="text-gradient-lime">Systems</span></h2>
                    </div>
                    <p class="text-slate-400 max-w-md text-base leading-relaxed md:text-right">
                        Click on any architecture node to view detailed implementation logic and software features.
                    </p>
                </div>

                <!-- Clean Grid for Projects -->
                <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
                    
                    <!-- Project 1 -->
                    <div class="glass-card p-10 rounded-[2rem] group cursor-pointer reveal-up flex flex-col justify-between" onclick="openModal('modal-1')">
                        <div>
                            <div class="w-16 h-16 rounded-2xl bg-system-800 border border-neon-emerald/30 flex items-center justify-center text-neon-emerald text-3xl mb-8 group-hover:scale-110 group-hover:bg-neon-emerald/20 transition-all duration-300">
                                <i class="fa-solid fa-hospital-user"></i>
                            </div>
                            <h3 class="text-2xl font-bold text-white mb-4 group-hover:text-neon-emerald transition-colors">Smart Hospital Core</h3>
                            <p class="text-slate-400 text-base leading-relaxed mb-8">
                                Enterprise desktop application enforcing strict Object-Oriented paradigms (Java) connected to a relational database to manage complex medical logistics.
                            </p>
                        </div>
                        <div class="flex items-center justify-between border-t border-white/10 pt-6">
                            <div class="flex gap-3">
                                <span class="px-3 py-1.5 rounded-lg bg-system-900 text-neon-emerald font-code text-[11px] font-bold border border-neon-emerald/20">Java OOP</span>
                                <span class="px-3 py-1.5 rounded-lg bg-system-900 text-neon-teal font-code text-[11px] font-bold border border-neon-teal/20">SQL DB</span>
                            </div>
                            <span class="text-xs font-code text-white font-bold uppercase group-hover:text-neon-emerald transition-colors">
                                View Data <i class="fa-solid fa-arrow-right ml-1 group-hover:translate-x-1 transition-transform"></i>
                            </span>
                        </div>
                    </div>

                    <!-- Project 2 -->
                    <div class="glass-card p-10 rounded-[2rem] group cursor-pointer reveal-up flex flex-col justify-between" style="transition-delay: 150ms;" onclick="openModal('modal-2')">
                        <div>
                            <div class="w-16 h-16 rounded-2xl bg-system-800 border border-neon-teal/30 flex items-center justify-center text-neon-teal text-3xl mb-8 group-hover:scale-110 group-hover:bg-neon-teal/20 transition-all duration-300">
                                <i class="fa-solid fa-plane-up"></i>
                            </div>
                            <h3 class="text-2xl font-bold text-white mb-4 group-hover:text-neon-teal transition-colors">Aero-Reserve DBMS</h3>
                            <p class="text-slate-400 text-base leading-relaxed mb-8">
                                Complex relational schema design demonstrating normalized tables, high-performance JOINs, indexing, and transactional integrity for flight systems.
                            </p>
                        </div>
                        <div class="flex items-center justify-between border-t border-white/10 pt-6">
                            <div class="flex gap-3">
                                <span class="px-3 py-1.5 rounded-lg bg-system-900 text-neon-teal font-code text-[11px] font-bold border border-neon-teal/20">SQL Schema</span>
                                <span class="px-3 py-1.5 rounded-lg bg-system-900 text-white font-code text-[11px] font-bold border border-white/20">ER Diagrams</span>
                            </div>
                            <span class="text-xs font-code text-white font-bold uppercase group-hover:text-neon-teal transition-colors">
                                View Data <i class="fa-solid fa-arrow-right ml-1 group-hover:translate-x-1 transition-transform"></i>
                            </span>
                        </div>
                    </div>

                    <!-- Project 3 -->
                    <div class="glass-card p-10 rounded-[2rem] group cursor-pointer reveal-up flex flex-col justify-between" onclick="openModal('modal-3')">
                        <div>
                            <div class="w-16 h-16 rounded-2xl bg-system-800 border border-neon-lime/30 flex items-center justify-center text-neon-lime text-3xl mb-8 group-hover:scale-110 group-hover:bg-neon-lime/20 transition-all duration-300">
                                <i class="fa-solid fa-droplet"></i>
                            </div>
                            <h3 class="text-2xl font-bold text-white mb-4 group-hover:text-neon-lime transition-colors">Automated Irrigation Engine</h3>
                            <p class="text-slate-400 text-base leading-relaxed mb-8">
                                C++ logical simulation managing resource constraints, automated sensor triggering, and algorithmic water conservation schedules.
                            </p>
                        </div>
                        <div class="flex items-center justify-between border-t border-white/10 pt-6">
                            <div class="flex gap-3">
                                <span class="px-3 py-1.5 rounded-lg bg-system-900 text-neon-lime font-code text-[11px] font-bold border border-neon-lime/20">C++ Logic</span>
                                <span class="px-3 py-1.5 rounded-lg bg-system-900 text-neon-emerald font-code text-[11px] font-bold border border-neon-emerald/20">Algorithms</span>
                            </div>
                            <span class="text-xs font-code text-white font-bold uppercase group-hover:text-neon-lime transition-colors">
                                View Data <i class="fa-solid fa-arrow-right ml-1 group-hover:translate-x-1 transition-transform"></i>
                            </span>
                        </div>
                    </div>

                    <!-- Project 4 -->
                    <div class="glass-card p-10 rounded-[2rem] group cursor-pointer reveal-up flex flex-col justify-between" style="transition-delay: 150ms;" onclick="openModal('modal-4')">
                        <div>
                            <div class="w-16 h-16 rounded-2xl bg-system-800 border border-[#ef4444]/30 flex items-center justify-center text-[#ef4444] text-3xl mb-8 group-hover:scale-110 group-hover:bg-[#ef4444]/20 transition-all duration-300">
                                <i class="fa-solid fa-fire-flame-curved"></i>
                            </div>
                            <h3 class="text-2xl font-bold text-white mb-4 group-hover:text-[#ef4444] transition-colors">Hardware: Auto Fire Brigade</h3>
                            <p class="text-slate-400 text-base leading-relaxed mb-8">
                                Embedded systems engineering combining Arduino microcontrollers, flame detection logic, motor drivers, and real-time physical actuation.
                            </p>
                        </div>
                        <div class="flex items-center justify-between border-t border-white/10 pt-6">
                            <div class="flex gap-3">
                                <span class="px-3 py-1.5 rounded-lg bg-system-900 text-[#ef4444] font-code text-[11px] font-bold border border-[#ef4444]/20">Arduino</span>
                                <span class="px-3 py-1.5 rounded-lg bg-system-900 text-[#ef4444] font-code text-[11px] font-bold border border-[#ef4444]/20">Sensors</span>
                            </div>
                            <span class="text-xs font-code text-white font-bold uppercase group-hover:text-[#ef4444] transition-colors">
                                View Data <i class="fa-solid fa-arrow-right ml-1 group-hover:translate-x-1 transition-transform"></i>
                            </span>
                        </div>
                    </div>

                </div>
            </div>
        </section>

        <!-- TERMINAL / CONTACT SECTION -->
        <section id="connect" class="py-24 px-6 lg:px-8 bg-system-900/50 border-t border-system-800">
            <div class="max-w-5xl mx-auto">
                <div class="glass-card rounded-[2.5rem] p-8 md:p-14 reveal-up">
                    <div class="grid grid-cols-1 lg:grid-cols-2 gap-16">
                        
                        <!-- Left Side: Links -->
                        <div class="flex flex-col justify-center">
                            <div class="mb-10">
                                <h2 class="text-4xl font-extrabold text-white mb-4">Initialize <span class="text-gradient">Connection</span></h2>
                                <p class="text-slate-400 text-base leading-relaxed">
                                    Ready to compile ideas into reality. Open to collaboration on AI research, software engineering projects, or technical discussions.
                                </p>
                            </div>

                            <div class="space-y-4">
                                <a href="mailto:realwahabqadeer@gmail.com" class="flex items-center gap-5 p-5 rounded-2xl bg-system-800/50 border border-system-700 hover:border-neon-emerald/50 group transition-all">
                                    <div class="w-12 h-12 rounded-xl bg-system-950 flex items-center justify-center text-neon-emerald text-xl group-hover:bg-neon-emerald group-hover:text-system-950 transition-colors">
                                        <i class="fa-solid fa-envelope"></i>
                                    </div>
                                    <div>
                                        <span class="text-[10px] font-code text-slate-500 uppercase tracking-widest block mb-1">Email</span>
                                        <span class="text-sm font-bold text-white group-hover:text-neon-emerald transition-colors">realwahabqadeer@gmail.com</span>
                                    </div>
                                </a>
                                <a href="https://www.linkedin.com/in/wahab-qadeer/" target="_blank" class="flex items-center gap-5 p-5 rounded-2xl bg-system-800/50 border border-system-700 hover:border-blue-500/50 group transition-all">
                                    <div class="w-12 h-12 rounded-xl bg-system-950 flex items-center justify-center text-blue-500 text-xl group-hover:bg-blue-500 group-hover:text-white transition-colors">
                                        <i class="fa-brands fa-linkedin-in"></i>
                                    </div>
                                    <div>
                                        <span class="text-[10px] font-code text-slate-500 uppercase tracking-widest block mb-1">LinkedIn</span>
                                        <span class="text-sm font-bold text-white group-hover:text-blue-500 transition-colors">linkedin.com/in/wahab-qadeer</span>
                                    </div>
                                </a>
                                <a href="https://github.com/wahab-qadeer" target="_blank" class="flex items-center gap-5 p-5 rounded-2xl bg-system-800/50 border border-system-700 hover:border-white/50 group transition-all">
                                    <div class="w-12 h-12 rounded-xl bg-system-950 flex items-center justify-center text-white text-xl group-hover:bg-white group-hover:text-system-950 transition-colors">
                                        <i class="fa-brands fa-github"></i>
                                    </div>
                                    <div>
                                        <span class="text-[10px] font-code text-slate-500 uppercase tracking-widest block mb-1">GitHub</span>
                                        <span class="text-sm font-bold text-white group-hover:text-white transition-colors">github.com/wahab-qadeer</span>
                                    </div>
                                </a>
                            </div>
                        </div>

                        <!-- Right Side: Terminal Form -->
                        <div class="bg-[#010403] rounded-3xl p-8 border border-system-800 shadow-inner">
                            <div class="flex gap-2 mb-8 border-b border-system-800 pb-4">
                                <div class="w-3 h-3 rounded-full bg-red-500"></div>
                                <div class="w-3 h-3 rounded-full bg-yellow-500"></div>
                                <div class="w-3 h-3 rounded-full bg-neon-emerald"></div>
                            </div>
                            <form id="contact-form" class="space-y-6">
                                <div>
                                    <label class="block text-xs font-code font-bold text-neon-emerald mb-2 uppercase tracking-widest">>> Name</label>
                                    <input type="text" required id="form-name" class="w-full bg-transparent border-b border-system-700 text-white px-0 py-2 focus:outline-none focus:border-neon-emerald transition-colors font-code text-sm">
                                </div>
                                <div>
                                    <label class="block text-xs font-code font-bold text-neon-emerald mb-2 uppercase tracking-widest">>> Email</label>
                                    <input type="email" required id="form-email" class="w-full bg-transparent border-b border-system-700 text-white px-0 py-2 focus:outline-none focus:border-neon-emerald transition-colors font-code text-sm">
                                </div>
                                <div>
                                    <label class="block text-xs font-code font-bold text-neon-emerald mb-2 uppercase tracking-widest">>> Message</label>
                                    <textarea rows="3" required id="form-message" class="w-full bg-transparent border-b border-system-700 text-white px-0 py-2 focus:outline-none focus:border-neon-emerald transition-colors font-code text-sm resize-none"></textarea>
                                </div>
                                <button type="submit" class="w-full py-4 rounded-xl bg-neon-emerald text-system-950 font-bold text-sm uppercase tracking-widest hover:bg-neon-lime transition-all mt-4">
                                    Send Transmission
                                </button>
                            </form>
                        </div>
                        
                    </div>
                </div>
            </div>
        </section>
    </main>

    <!-- FOOTER -->
    <footer class="border-t border-system-800 py-12 px-6 bg-system-950 relative z-10 text-center">
        <div class="max-w-7xl mx-auto flex flex-col items-center gap-6">
            <div class="w-12 h-12 rounded-xl bg-gradient-to-br from-neon-emerald to-neon-teal flex items-center justify-center text-system-950 font-black text-xl">WQ</div>
            <p class="text-slate-500 font-code text-sm leading-relaxed">
                System architecture compiled by <span class="text-neon-emerald font-bold">Wahab Qadeer</span> © <span id="current-year"></span>.<br>
                BS Artificial Intelligence @ BIIT.
            </p>
        </div>
    </footer>

    <!-- MODALS -->
    <!-- Modal 1 -->
    <div id="modal-1" class="modal-overlay" onclick="closeModal(event, 'modal-1')">
        <div class="modal-box" onclick="event.stopPropagation()">
            <div class="flex justify-between items-start mb-8 border-b border-system-800 pb-6">
                <div>
                    <span class="text-neon-emerald font-code text-xs uppercase tracking-widest font-bold block mb-2">Enterprise Software</span>
                    <h2 class="text-3xl font-extrabold text-white">Smart Hospital System</h2>
                </div>
                <button onclick="closeModal(null, 'modal-1')" class="w-10 h-10 rounded-full bg-system-800 text-slate-400 hover:text-white hover:bg-red-500/20 transition-all"><i class="fa-solid fa-xmark text-lg"></i></button>
            </div>
            <div class="text-slate-300 text-base leading-relaxed space-y-4">
                <p>A comprehensive desktop application designed to streamline healthcare administration, built using strict Object-Oriented Programming (OOP) paradigms in Java.</p>
                <ul class="list-disc pl-5 space-y-2 text-sm mt-4 text-slate-400">
                    <li><strong>Encapsulation & Inheritance:</strong> Clean class hierarchies for Patients, Doctors, and Staff.</li>
                    <li><strong>Database Connectivity:</strong> Integrated via JDBC to handle persistent storage of appointments and billing.</li>
                    <li><strong>UI/UX:</strong> Intuitive dashboards for administrative staff to retrieve critical data.</li>
                </ul>
            </div>
        </div>
    </div>

    <!-- Modal 2 -->
    <div id="modal-2" class="modal-overlay" onclick="closeModal(event, 'modal-2')">
        <div class="modal-box" onclick="event.stopPropagation()">
            <div class="flex justify-between items-start mb-8 border-b border-system-800 pb-6">
                <div>
                    <span class="text-neon-teal font-code text-xs uppercase tracking-widest font-bold block mb-2">Database Engineering</span>
                    <h2 class="text-3xl font-extrabold text-white">Aero-Reserve DBMS</h2>
                </div>
                <button onclick="closeModal(null, 'modal-2')" class="w-10 h-10 rounded-full bg-system-800 text-slate-400 hover:text-white hover:bg-red-500/20 transition-all"><i class="fa-solid fa-xmark text-lg"></i></button>
            </div>
            <div class="text-slate-300 text-base leading-relaxed space-y-4">
                <p>A highly normalized relational database project engineered to simulate the backend of an international airline booking system.</p>
                <ul class="list-disc pl-5 space-y-2 text-sm mt-4 text-slate-400">
                    <li><strong>Normalization:</strong> Entities reduced to BCNF to eliminate data redundancy.</li>
                    <li><strong>Complex Queries:</strong> Multi-table JOINs, subqueries, and aggregate functions.</li>
                    <li><strong>Constraints:</strong> Strict physical database tables defining cardinalities and foreign key constraints.</li>
                </ul>
            </div>
        </div>
    </div>

    <!-- Modal 3 -->
    <div id="modal-3" class="modal-overlay" onclick="closeModal(event, 'modal-3')">
        <div class="modal-box" onclick="event.stopPropagation()">
            <div class="flex justify-between items-start mb-8 border-b border-system-800 pb-6">
                <div>
                    <span class="text-neon-lime font-code text-xs uppercase tracking-widest font-bold block mb-2">Algorithmic Logic</span>
                    <h2 class="text-3xl font-extrabold text-white">Smart Irrigation Engine</h2>
                </div>
                <button onclick="closeModal(null, 'modal-3')" class="w-10 h-10 rounded-full bg-system-800 text-slate-400 hover:text-white hover:bg-red-500/20 transition-all"><i class="fa-solid fa-xmark text-lg"></i></button>
            </div>
            <div class="text-slate-300 text-base leading-relaxed">
                <p>A console-based logic simulation built purely in C++ without external libraries. It models intelligent water distribution based on variable environmental factors, utilizing complex conditional structures and looping logic to simulate resource conservation dynamically.</p>
            </div>
        </div>
    </div>

    <!-- Modal 4 -->
    <div id="modal-4" class="modal-overlay" onclick="closeModal(event, 'modal-4')">
        <div class="modal-box" onclick="event.stopPropagation()">
            <div class="flex justify-between items-start mb-8 border-b border-system-800 pb-6">
                <div>
                    <span class="text-[#ef4444] font-code text-xs uppercase tracking-widest font-bold block mb-2">Embedded Systems</span>
                    <h2 class="text-3xl font-extrabold text-white">Auto Fire Brigade</h2>
                </div>
                <button onclick="closeModal(null, 'modal-4')" class="w-10 h-10 rounded-full bg-system-800 text-slate-400 hover:text-white hover:bg-red-500/20 transition-all"><i class="fa-solid fa-xmark text-lg"></i></button>
            </div>
            <div class="text-slate-300 text-base leading-relaxed">
                <p>Hardware and software synergy. Designed and programmed an autonomous robot utilizing physical flame sensors and Arduino microcontrollers. The logic connects sensor inputs to motor driver outputs to detect and maneuver toward fires dynamically in real-time.</p>
            </div>
        </div>
    </div>

    <!-- Toast -->
    <div id="toast" class="fixed bottom-8 right-8 z-50 transform translate-y-32 opacity-0 transition-all duration-500 glass-card px-6 py-4 rounded-xl flex items-center gap-4 text-white">
        <i class="fa-solid fa-circle-check text-neon-emerald text-2xl"></i>
        <span class="text-sm font-code">Message transmitted successfully.</span>
    </div>

    <!-- SCRIPTS -->
    <script>
        // Set Year
        document.getElementById('current-year').textContent = new Date().getFullYear();

        // 1. Elegant Typing Effect
        const phrases = ["Machine Learning Models.", "Object-Oriented Logic.", "Relational Databases.", "Embedded IoT Systems."];
        let pIdx = 0, cIdx = 0, isDel = false;
        const typeEl = document.getElementById('typing-text');
        
        function typeWriter() {
            const current = phrases[pIdx];
            if (isDel) {
                typeEl.textContent = current.substring(0, cIdx - 1);
                cIdx--;
            } else {
                typeEl.textContent = current.substring(0, cIdx + 1);
                cIdx++;
            }
            let speed = isDel ? 30 : 70;
            if (!isDel && cIdx === current.length) { speed = 2500; isDel = true; } 
            else if (isDel && cIdx === 0) { isDel = false; pIdx = (pIdx + 1) % phrases.length; speed = 500; }
            setTimeout(typeWriter, speed);
        }
        setTimeout(typeWriter, 1000);

        // 2. Smooth Reveal & Number Counters
        const revealElements = document.querySelectorAll('.reveal-up');
        const counters = document.querySelectorAll('.counter');
        let hasCounted = false;

        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.classList.add('active');
                    
                    if(entry.target.querySelector('.counter') && !hasCounted) {
                        hasCounted = true;
                        counters.forEach(counter => {
                            const target = +counter.getAttribute('data-target');
                            const increment = target / 100; 
                            let current = 0;
                            const updateCounter = () => {
                                current += increment;
                                if(current < target) {
                                    counter.innerText = Math.ceil(current);
                                    requestAnimationFrame(updateCounter);
                                } else {
                                    counter.innerText = target + (target > 50 ? '%' : '+');
                                }
                            };
                            updateCounter();
                        });
                    }
                }
            });
        }, { threshold: 0.1 });
        revealElements.forEach(el => observer.observe(el));

        // 3. Modals & Form
        function openModal(id) {
            document.body.style.overflow = 'hidden';
            document.getElementById(id).classList.add('active');
        }
        function closeModal(e, id) {
            if(e && e.target !== e.currentTarget) return;
            document.body.style.overflow = 'auto';
            document.getElementById(id).classList.remove('active');
        }

        document.getElementById('contact-form').addEventListener('submit', (e) => {
            e.preventDefault();
            const toast = document.getElementById('toast');
            toast.classList.remove('translate-y-32', 'opacity-0');
            toast.classList.add('translate-y-0', 'opacity-100');
            e.target.reset();
            setTimeout(() => {
                toast.classList.remove('translate-y-0', 'opacity-100');
                toast.classList.add('translate-y-32', 'opacity-0');
            }, 4000);
        });

        // 4. CHART.JS (Perfectly Constrained and Styled)
        document.addEventListener("DOMContentLoaded", function() {
            Chart.defaults.color = '#64748b'; // slate-500
            Chart.defaults.font.family = "'Fira Code', monospace";
            
            const tooltipStyle = {
                backgroundColor: 'rgba(3, 18, 15, 0.95)',
                titleColor: '#10b981',
                bodyColor: '#fff',
                borderColor: '#10b981',
                borderWidth: 1,
                padding: 12
            };

            // Doughnut Chart
            new Chart(document.getElementById('chartDoughnut').getContext('2d'), {
                type: 'doughnut',
                data: {
                    labels: ['Algorithms', 'Architecture', 'Databases', 'Hardware'],
                    datasets: [{
                        data: [35, 25, 25, 15],
                        backgroundColor: ['#10b981', '#14b8a6', '#06b6d4', '#a3e635'],
                        borderColor: '#06241e',
                        borderWidth: 4
                    }]
                },
                options: {
                    responsive: true, maintainAspectRatio: false, cutout: '75%',
                    plugins: { legend: { position: 'bottom' }, tooltip: tooltipStyle }
                }
            });

            // Radar Chart
            new Chart(document.getElementById('chartRadar').getContext('2d'), {
                type: 'radar',
                data: {
                    labels: ['OOP', 'SQL', 'C++', 'Data Structures', 'Embedded'],
                    datasets: [{
                        label: 'Skill Level',
                        data: [95, 90, 85, 88, 80],
                        backgroundColor: 'rgba(20, 184, 166, 0.2)',
                        borderColor: '#14b8a6',
                        pointBackgroundColor: '#fff',
                        pointBorderColor: '#14b8a6',
                        borderWidth: 2
                    }]
                },
                options: {
                    responsive: true, maintainAspectRatio: false,
                    scales: {
                        r: {
                            angleLines: { color: 'rgba(255,255,255,0.05)' },
                            grid: { color: 'rgba(255,255,255,0.05)' },
                            pointLabels: { color: '#6ee7b7', font: {size: 10} },
                            ticks: { display: false, max: 100 }
                        }
                    },
                    plugins: { legend: { display: false }, tooltip: tooltipStyle }
                }
            });

            // Polar Area Chart
            new Chart(document.getElementById('chartPolar').getContext('2d'), {
                type: 'polarArea',
                data: {
                    labels: ['Java', 'SQL', 'HTML/CSS', 'Kotlin', 'Arduino'],
                    datasets: [{
                        data: [90, 85, 70, 50, 80],
                        backgroundColor: [
                            'rgba(16, 185, 129, 0.6)', 'rgba(6, 182, 212, 0.6)',
                            'rgba(59, 130, 246, 0.6)', 'rgba(139, 92, 246, 0.6)', 'rgba(239, 68, 68, 0.6)'
                        ],
                        borderColor: '#06241e',
                        borderWidth: 2
                    }]
                },
                options: {
                    responsive: true, maintainAspectRatio: false,
                    scales: { r: { grid: { color: 'rgba(255,255,255,0.05)' }, ticks: {display: false} } },
                    plugins: { legend: { position: 'right' }, tooltip: tooltipStyle }
                }
            });

            // Mixed Line/Bar Chart
            const ctxMixed = document.getElementById('chartMixed').getContext('2d');
            const gradBar = ctxMixed.createLinearGradient(0, 0, 0, 300);
            gradBar.addColorStop(0, 'rgba(6, 182, 212, 0.8)');
            gradBar.addColorStop(1, 'rgba(6, 182, 212, 0.1)');

            new Chart(ctxMixed, {
                type: 'bar',
                data: {
                    labels: ['Jan', 'Mar', 'May', 'Jul', 'Sep', 'Nov'],
                    datasets: [
                        {
                            type: 'line', label: 'Expected',
                            data: [10, 25, 45, 65, 75, 95],
                            borderColor: '#a3e635', borderWidth: 2, borderDash: [5, 5],
                            pointBackgroundColor: '#fff', pointBorderColor: '#a3e635',
                            tension: 0.4
                        },
                        {
                            type: 'bar', label: 'Actual',
                            data: [12, 22, 42, 60, 80, 92],
                            backgroundColor: gradBar, borderRadius: 4, barPercentage: 0.5
                        }
                    ]
                },
                options: {
                    responsive: true, maintainAspectRatio: false,
                    scales: {
                        x: { grid: { display: false } },
                        y: { grid: { color: 'rgba(255,255,255,0.05)' }, max: 100 }
                    },
                    plugins: { legend: { display: false }, tooltip: tooltipStyle }
                }
            });
        });

        // 5. Elegant, Optimized Single Canvas Background (Neural Network)
        const canvas = document.getElementById('ambient-canvas');
        const ctx = canvas.getContext('2d');
        
        let width, height;
        function resize() {
            width = window.innerWidth;
            height = window.innerHeight;
            canvas.width = width;
            canvas.height = height;
        }
        window.addEventListener('resize', resize);
        resize();

        class Particle {
            constructor() {
                this.x = Math.random() * width;
                this.y = Math.random() * height;
                this.vx = (Math.random() - 0.5) * 0.5;
                this.vy = (Math.random() - 0.5) * 0.5;
                this.radius = Math.random() * 1.5 + 0.5;
            }
            update() {
                this.x += this.vx;
                this.y += this.vy;
                if (this.x < 0 || this.x > width) this.vx *= -1;
                if (this.y < 0 || this.y > height) this.vy *= -1;
            }
            draw() {
                ctx.beginPath();
                ctx.arc(this.x, this.y, this.radius, 0, Math.PI * 2);
                ctx.fillStyle = '#10b981';
                ctx.fill();
            }
        }

        const particleCount = Math.min(Math.floor((window.innerWidth * window.innerHeight) / 15000), 100);
        const particles = Array.from({length: particleCount}, () => new Particle());

        function animateCanvas() {
            ctx.clearRect(0, 0, width, height);
            
            for (let i = 0; i < particles.length; i++) {
                particles[i].update();
                particles[i].draw();
                
                for (let j = i + 1; j < particles.length; j++) {
                    const dx = particles[i].x - particles[j].x;
                    const dy = particles[i].y - particles[j].y;
                    const dist = Math.sqrt(dx*dx + dy*dy);
                    
                    if (dist < 150) {
                        ctx.beginPath();
                        ctx.moveTo(particles[i].x, particles[i].y);
                        ctx.lineTo(particles[j].x, particles[j].y);
                        ctx.strokeStyle = `rgba(16, 185, 129, ${0.2 * (1 - dist/150)})`;
                        ctx.lineWidth = 1;
                        ctx.stroke();
                    }
                }
            }
            requestAnimationFrame(animateCanvas);
        }
        animateCanvas();
    </script>
</body>
</html>
