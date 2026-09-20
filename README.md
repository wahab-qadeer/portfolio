<!DOCTYPE html>
<html lang="en" class="scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Wahab Qadeer | AI & Software Architecture</title>
    
    <!-- Premium Fonts: Inter for high-legibility body, Space Grotesk for sharp headings -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Fira+Code:wght@400;500;600;700&family=Inter:wght@300;400;500;600;700&family=Space+Grotesk:wght@400;500;600;700;800&display=swap" rel="stylesheet">
    
    <!-- FontAwesome for crisp vector icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    
    <!-- Chart.js for Advanced Data Visualization -->
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    
    <!-- Tailwind CSS Engine -->
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
                            800: '#05211c',
                            700: '#08332a',
                            600: '#0b473b'
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
                        'pulse-glow': 'pulseGlow 3s ease-in-out infinite alternate',
                    },
                    keyframes: {
                        floatSmooth: {
                            '0%, 100%': { transform: 'translateY(0)' },
                            '50%': { transform: 'translateY(-12px)' },
                        },
                        pulseGlow: {
                            '0%': { opacity: 0.5, transform: 'scale(1)' },
                            '100%': { opacity: 1, transform: 'scale(1.05)' },
                        }
                    }
                }
            }
        }
    </script>

    <style>
        /* =========================================
           CORE TYPOGRAPHY & RESET
           ========================================= */
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

        /* =========================================
           BACKGROUND CANVAS SYSTEM
           ========================================= */
        #ambient-canvas {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -10;
            pointer-events: none;
            opacity: 0.7;
        }

        .glow-orb {
            position: absolute;
            border-radius: 50%;
            filter: blur(100px);
            z-index: -9;
            opacity: 0.15;
            pointer-events: none;
        }
        .orb-1 { top: -10%; left: -10%; width: 50vw; height: 50vw; background: #10b981; }
        .orb-2 { bottom: 10%; right: -5%; width: 40vw; height: 40vw; background: #14b8a6; }

        /* =========================================
           GLASSMORPHISM UI PANELS
           ========================================= */
        .glass-card {
            background: rgba(5, 33, 28, 0.4);
            backdrop-filter: blur(20px);
            -webkit-backdrop-filter: blur(20px);
            border: 1px solid rgba(20, 184, 166, 0.15);
            box-shadow: 0 10px 40px rgba(0, 0, 0, 0.4);
            transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
        }

        .glass-card:hover {
            background: rgba(8, 51, 42, 0.6);
            border-color: rgba(16, 185, 129, 0.35);
            box-shadow: 0 15px 50px rgba(16, 185, 129, 0.15);
            transform: translateY(-4px);
        }

        .glass-solid {
            background: #03120f;
            border: 1px solid rgba(20, 184, 166, 0.2);
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.6);
        }

        /* =========================================
           HERO IMAGE SHOWCASE
           ========================================= */
        .image-showcase {
            position: relative;
            width: 100%;
            max-width: 420px;
            margin: 0 auto;
            border-radius: 2rem;
            padding: 10px;
            background: linear-gradient(145deg, rgba(20,184,166,0.2), rgba(3,18,15,0.9));
            box-shadow: 0 25px 60px rgba(0,0,0,0.7), inset 0 0 20px rgba(16,185,129,0.1);
            z-index: 10;
        }

        .image-showcase img {
            width: 100%;
            height: auto;
            border-radius: 1.5rem;
            object-fit: cover;
            box-shadow: 0 15px 40px rgba(0,0,0,0.8);
            filter: contrast(1.05) brightness(0.95);
            transition: transform 0.6s ease, filter 0.6s ease;
        }

        .image-showcase:hover img {
            transform: scale(1.04);
            filter: contrast(1.1) brightness(1.02);
        }

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

        /* =========================================
           TYPOGRAPHY GRADIENTS & EFFECTS
           ========================================= */
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

        .text-gradient-cyan {
            background: linear-gradient(135deg, #06b6d4 0%, #14b8a6 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .type-caret::after {
            content: '';
            display: inline-block;
            width: 3px;
            height: 1em;
            background-color: #10b981;
            margin-left: 6px;
            vertical-align: middle;
            animation: blink 1s step-end infinite;
        }
        @keyframes blink { 50% { opacity: 0; } }

        /* =========================================
           CHART CONTAINERS
           ========================================= */
        .chart-container {
            position: relative;
            width: 100%;
            height: 320px;
            display: flex;
            align-items: center;
            justify-content: center;
        }
        .chart-container-wide {
            position: relative;
            width: 100%;
            height: 400px;
        }

        /* =========================================
           UTILITIES & ANIMATIONS
           ========================================= */
        .reveal-up {
            opacity: 0;
            transform: translateY(40px);
            transition: opacity 0.8s ease-out, transform 0.8s cubic-bezier(0.16, 1, 0.3, 1);
        }
        
        .reveal-up.active {
            opacity: 1;
            transform: translateY(0);
        }

        ::-webkit-scrollbar { width: 10px; }
        ::-webkit-scrollbar-track { background: #020806; }
        ::-webkit-scrollbar-thumb { background: #08332a; border-radius: 5px; border: 2px solid #020806; }
        ::-webkit-scrollbar-thumb:hover { background: #10b981; }

        .modal-overlay {
            position: fixed; inset: 0;
            background: rgba(2, 8, 6, 0.95);
            backdrop-filter: blur(15px);
            z-index: 100;
            display: flex; align-items: center; justify-content: center;
            opacity: 0; pointer-events: none;
            transition: opacity 0.4s ease;
        }
        .modal-overlay.active { opacity: 1; pointer-events: all; }
        
        .modal-box {
            background: #03120f;
            border: 1px solid rgba(20, 184, 166, 0.3);
            border-radius: 2rem;
            width: 90%; max-width: 850px; max-height: 85vh;
            overflow-y: auto;
            transform: translateY(30px);
            transition: transform 0.4s cubic-bezier(0.16, 1, 0.3, 1);
            box-shadow: 0 30px 60px rgba(0,0,0,0.8), 0 0 40px rgba(16, 185, 129, 0.1);
            padding: 3rem;
        }
        .modal-overlay.active .modal-box { transform: translateY(0); }
    </style>
</head>
<body class="selection:bg-neon-emerald selection:text-system-950">

    <canvas id="ambient-canvas"></canvas>
    <div class="glow-orb orb-1"></div>
    <div class="glow-orb orb-2"></div>

    <!-- =========================================
         HEADER NAVIGATION
         ========================================= -->
    <header class="fixed top-0 left-0 w-full z-50 px-4 sm:px-8 py-5 transition-all duration-300" id="header">
        <div class="max-w-[1400px] mx-auto">
            <div class="glass-card rounded-2xl px-6 md:px-10 py-4 flex items-center justify-between">
                
                <a href="#" class="font-heading font-bold text-2xl text-white flex items-center gap-4 group">
                    <div class="w-12 h-12 rounded-xl bg-gradient-to-br from-neon-emerald to-neon-teal flex items-center justify-center text-system-950 font-black text-xl shadow-[0_0_20px_rgba(16,185,129,0.4)] group-hover:rotate-12 transition-transform duration-300">
                        WQ
                    </div>
                    <div class="flex flex-col">
                        <span class="leading-none tracking-wide group-hover:text-neon-emerald transition-colors">Wahab<span class="text-neon-emerald">.ai</span></span>
                        <span class="text-[10px] text-slate-400 font-code tracking-widest uppercase mt-1">System Architecture</span>
                    </div>
                </a>

                <nav class="hidden lg:flex items-center space-x-8 xl:space-x-10 text-sm font-medium text-slate-300">
                    <a href="#about" class="hover:text-neon-emerald transition-colors duration-300">Profile</a>
                    <a href="#analytics" class="hover:text-neon-emerald transition-colors duration-300">Analytics</a>
                    <a href="#projects" class="hover:text-neon-emerald transition-colors duration-300">Systems</a>
                    <a href="#focus" class="hover:text-neon-emerald transition-colors duration-300">Next Focus</a>
                    <a href="#connect" class="px-6 py-2.5 rounded-xl bg-neon-emerald text-system-950 hover:bg-neon-lime hover:shadow-[0_0_20px_rgba(163,230,53,0.5)] transition-all font-bold uppercase tracking-widest text-xs">
                        Initialize
                    </a>
                </nav>
            </div>
        </div>
    </header>

    <main class="relative pt-36 pb-20">

        <!-- =========================================
             HERO SECTION
             ========================================= -->
        <section id="about" class="min-h-[85vh] flex items-center justify-center px-6 lg:px-8 py-12">
            <div class="max-w-[1400px] mx-auto w-full">
                
                <div class="flex flex-col lg:flex-row items-center justify-between gap-16 lg:gap-24">
                    
                    <div class="w-full lg:w-5/12 flex justify-center lg:justify-start order-2 lg:order-1 reveal-up">
                        <div class="relative w-full max-w-md animate-float-smooth">
                            <div class="image-showcase">
                                <!-- Replace with your actual image path -->
                                <img 
                                    src="WhatsApp Image 2026-08-13 at 1.09.24 PM_2.jpeg" 
                                    alt="Wahab Qadeer" 
                                    onerror="this.src='https://placehold.co/600x800/05211c/10b981?text=Wahab+Qadeer'"
                                >
                            </div>
                            <div class="absolute -bottom-6 -right-4 md:-right-8 glass-card px-6 py-3.5 rounded-xl border border-neon-emerald/40 text-sm font-code font-bold text-white shadow-2xl z-20 flex items-center gap-3">
                                <span class="relative flex h-3 w-3">
                                  <span class="animate-ping absolute inline-flex h-full w-full rounded-full bg-neon-emerald opacity-75"></span>
                                  <span class="relative inline-flex rounded-full h-3 w-3 bg-neon-emerald"></span>
                                </span>
                                System Online
                            </div>
                        </div>
                    </div>

                    <div class="w-full lg:w-7/12 flex flex-col items-center lg:items-start text-center lg:text-left order-1 lg:order-2 reveal-up" style="transition-delay: 150ms;">
                        
                        <div class="inline-flex items-center gap-2 px-5 py-2 rounded-full bg-system-800 border border-neon-teal/30 text-neon-teal text-xs font-code uppercase tracking-widest mb-8 shadow-lg">
                            <i class="fa-solid fa-microchip"></i> BS(AI) Candidate @ BIIT
                        </div>

                        <h1 class="text-5xl sm:text-6xl lg:text-[5rem] font-extrabold tracking-tight text-white leading-[1.1] mb-6">
                            Architecting <br class="hidden sm:block">
                            <span class="text-gradient">Intelligent</span> Systems.
                        </h1>

                        <div class="flex flex-row items-center justify-center lg:justify-start text-xl sm:text-2xl lg:text-3xl font-medium text-slate-300 mb-8 h-10 w-full overflow-hidden">
                            <span class="mr-3 whitespace-nowrap">I build</span>
                            <span id="typing-text" class="font-code text-neon-emerald font-bold type-caret whitespace-nowrap border-b-2 border-neon-emerald/30 pb-1"></span>
                        </div>

                        <p class="text-slate-400 text-lg sm:text-xl leading-loose max-w-2xl mx-auto lg:mx-0 font-light mb-12">
                            Computer Science undergraduate specializing in Artificial Intelligence. I bridge the gap between raw data, complex algorithmic logic, and robust object-oriented software architectures to solve real-world problems.
                        </p>

                        <div class="flex flex-col sm:flex-row items-center gap-8 w-full justify-center lg:justify-start">
                            <a href="#analytics" class="px-8 py-4 rounded-xl bg-neon-emerald text-system-950 font-black text-base hover:bg-neon-lime hover:shadow-[0_0_30px_rgba(163,230,53,0.5)] transition-all flex items-center gap-3 shrink-0">
                                Explore Analytics <i class="fa-solid fa-arrow-right"></i>
                            </a>
                            
                            <div class="flex items-center gap-6 px-6 py-3 rounded-2xl bg-system-900/50 border border-system-800 shrink-0">
                                <div class="text-left">
                                    <span class="block text-3xl font-black text-white counter" data-target="15">0</span>
                                    <span class="text-[10px] text-neon-teal uppercase tracking-widest font-bold block mt-1">Projects Built</span>
                                </div>
                                <div class="w-px h-12 bg-system-700"></div>
                                <div class="text-left">
                                    <span class="block text-3xl font-black text-white counter" data-target="98">0</span>
                                    <span class="text-[10px] text-neon-lime uppercase tracking-widest font-bold block mt-1">Code Efficiency %</span>
                                </div>
                            </div>
                        </div>

                    </div>
                </div>
            </div>
        </section>

        <!-- =========================================
             ANALYTICS DASHBOARD
             ========================================= -->
        <section id="analytics" class="py-28 px-4 sm:px-6 lg:px-8 border-t border-system-800 bg-system-900/30 relative z-10">
            <div class="max-w-[1400px] mx-auto">
                
                <div class="text-center mb-20 reveal-up">
                    <span class="text-sm font-code text-neon-teal uppercase tracking-widest block mb-4 font-bold flex items-center justify-center gap-3">
                        <i class="fa-solid fa-radar text-neon-lime animate-spin-slow"></i> Telemetry Data
                    </span>
                    <h2 class="text-4xl sm:text-5xl font-extrabold text-white">Live <span class="text-gradient">Growth Dashboard</span></h2>
                    <p class="text-slate-400 mt-6 max-w-3xl mx-auto text-lg leading-relaxed">
                        Data-driven visualization of my technological stack, core architectural competencies, and historical learning velocity.
                    </p>
                </div>

                <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8 reveal-up" style="transition-delay: 200ms;">
                    
                    <div class="glass-solid p-8 rounded-[2rem] flex flex-col relative overflow-hidden">
                        <div class="mb-8 relative z-10">
                            <h3 class="text-2xl font-bold text-white flex items-center gap-3">
                                <i class="fa-solid fa-chart-pie text-neon-emerald"></i> Distribution
                            </h3>
                            <p class="text-xs text-slate-500 font-code uppercase tracking-wider mt-2">Resource Allocation %</p>
                        </div>
                        <div class="chart-container relative z-10">
                            <canvas id="chartDoughnut"></canvas>
                        </div>
                        <div class="absolute -right-10 -bottom-10 w-40 h-40 bg-neon-emerald/10 blur-3xl rounded-full"></div>
                    </div>

                    <div class="glass-solid p-8 rounded-[2rem] flex flex-col relative overflow-hidden">
                        <div class="mb-8 relative z-10">
                            <h3 class="text-2xl font-bold text-white flex items-center gap-3">
                                <i class="fa-solid fa-bullseye text-neon-teal"></i> Competencies
                            </h3>
                            <p class="text-xs text-slate-500 font-code uppercase tracking-wider mt-2">Vector Analysis Matrix</p>
                        </div>
                        <div class="chart-container relative z-10">
                            <canvas id="chartRadar"></canvas>
                        </div>
                        <div class="absolute -left-10 -bottom-10 w-40 h-40 bg-neon-teal/10 blur-3xl rounded-full"></div>
                    </div>

                    <div class="glass-solid p-8 rounded-[2rem] flex flex-col relative overflow-hidden md:col-span-2 lg:col-span-1">
                        <div class="mb-8 relative z-10">
                            <h3 class="text-2xl font-bold text-white flex items-center gap-3">
                                <i class="fa-solid fa-layer-group text-neon-lime"></i> Tech Stack
                            </h3>
                            <p class="text-xs text-slate-500 font-code uppercase tracking-wider mt-2">Syntax & Frameworks</p>
                        </div>
                        <div class="chart-container relative z-10">
                            <canvas id="chartPolar"></canvas>
                        </div>
                        <div class="absolute top-1/2 right-1/2 w-40 h-40 bg-neon-lime/5 blur-3xl rounded-full transform translate-x-1/2 -translate-y-1/2"></div>
                    </div>

                    <div class="glass-solid p-8 md:p-12 rounded-[2rem] flex flex-col lg:col-span-3 relative overflow-hidden">
                        <div class="flex flex-col sm:flex-row sm:items-center justify-between mb-10 gap-6 relative z-10">
                            <div>
                                <h3 class="text-2xl font-bold text-white flex items-center gap-3">
                                    <i class="fa-solid fa-chart-line text-neon-cyan"></i> Learning Velocity
                                </h3>
                                <p class="text-xs text-slate-500 font-code uppercase tracking-wider mt-2">12-Month Progression Trend</p>
                            </div>
                            <div class="flex items-center gap-6 bg-system-950 p-4 rounded-xl border border-white/5">
                                <div class="flex items-center gap-2">
                                    <div class="w-4 h-4 rounded bg-neon-cyan/50 border border-neon-cyan"></div>
                                    <span class="text-xs text-slate-300 font-code">Actual Units</span>
                                </div>
                                <div class="flex items-center gap-2">
                                    <div class="w-6 h-0.5 bg-neon-lime"></div>
                                    <span class="text-xs text-slate-300 font-code">Trajectory</span>
                                </div>
                            </div>
                        </div>
                        <div class="chart-container-wide relative z-10">
                            <canvas id="chartMixed"></canvas>
                        </div>
                    </div>

                </div>
            </div>
        </section>

        <!-- =========================================
             PROJECTS SECTION
             ========================================= -->
        <section id="projects" class="py-28 px-4 sm:px-6 lg:px-8 border-t border-system-800">
            <div class="max-w-[1400px] mx-auto">
                
                <div class="flex flex-col md:flex-row justify-between items-end mb-20 gap-8 reveal-up">
                    <div>
                        <span class="text-sm font-code text-neon-lime uppercase tracking-widest block mb-4 font-bold">Deployment Phase</span>
                        <h2 class="text-4xl sm:text-5xl font-extrabold text-white">Engineered <span class="text-gradient-lime">Systems</span></h2>
                    </div>
                    <p class="text-slate-400 max-w-lg text-lg leading-relaxed md:text-right">
                        Click on any architecture node to open a full diagnostic overlay detailing source logic, database schemas, and implementation features.
                    </p>
                </div>

                <div class="grid grid-cols-1 md:grid-cols-2 gap-10">
                    
                    <div class="glass-card p-10 lg:p-12 rounded-[2.5rem] group cursor-pointer reveal-up flex flex-col justify-between" onclick="openModal('modal-1')">
                        <div>
                            <div class="w-20 h-20 rounded-2xl bg-system-800 border border-neon-emerald/30 flex items-center justify-center text-neon-emerald text-4xl mb-8 group-hover:scale-110 group-hover:bg-neon-emerald/10 transition-all duration-300 shadow-[0_0_20px_rgba(16,185,129,0.1)] group-hover:shadow-[0_0_30px_rgba(16,185,129,0.3)]">
                                <i class="fa-solid fa-hospital-user"></i>
                            </div>
                            <h3 class="text-3xl font-extrabold text-white mb-4 group-hover:text-neon-emerald transition-colors tracking-tight">Smart Hospital Core</h3>
                            <p class="text-slate-400 text-lg leading-loose mb-10 pr-4">
                                Enterprise desktop application enforcing strict Object-Oriented paradigms (Java) connected to a relational database to manage complex medical logistics and patient scheduling.
                            </p>
                        </div>
                        <div class="flex flex-wrap items-center justify-between border-t border-white/10 pt-8 gap-4">
                            <div class="flex flex-wrap gap-3">
                                <span class="px-4 py-2 rounded-xl bg-system-900 text-neon-emerald font-code text-xs font-bold border border-neon-emerald/20">Java OOP</span>
                                <span class="px-4 py-2 rounded-xl bg-system-900 text-neon-teal font-code text-xs font-bold border border-neon-teal/20">SQL DB</span>
                            </div>
                            <span class="text-sm font-code text-white font-bold uppercase group-hover:text-neon-emerald transition-colors flex items-center">
                                View Data <i class="fa-solid fa-arrow-right-long ml-3 group-hover:translate-x-2 transition-transform"></i>
                            </span>
                        </div>
                    </div>

                    <div class="glass-card p-10 lg:p-12 rounded-[2.5rem] group cursor-pointer reveal-up flex flex-col justify-between" style="transition-delay: 150ms;" onclick="openModal('modal-2')">
                        <div>
                            <div class="w-20 h-20 rounded-2xl bg-system-800 border border-neon-teal/30 flex items-center justify-center text-neon-teal text-4xl mb-8 group-hover:scale-110 group-hover:bg-neon-teal/10 transition-all duration-300 shadow-[0_0_20px_rgba(20,184,166,0.1)] group-hover:shadow-[0_0_30px_rgba(20,184,166,0.3)]">
                                <i class="fa-solid fa-plane-up"></i>
                            </div>
                            <h3 class="text-3xl font-extrabold text-white mb-4 group-hover:text-neon-teal transition-colors tracking-tight">Aero-Reserve DBMS</h3>
                            <p class="text-slate-400 text-lg leading-loose mb-10 pr-4">
                                Complex relational schema design demonstrating highly normalized tables, high-performance JOINs, indexing, and strict transactional integrity for airline flight systems.
                            </p>
                        </div>
                        <div class="flex flex-wrap items-center justify-between border-t border-white/10 pt-8 gap-4">
                            <div class="flex flex-wrap gap-3">
                                <span class="px-4 py-2 rounded-xl bg-system-900 text-neon-teal font-code text-xs font-bold border border-neon-teal/20">SQL Schema</span>
                                <span class="px-4 py-2 rounded-xl bg-system-900 text-neon-cyan font-code text-xs font-bold border border-neon-cyan/20">ER Diagrams</span>
                            </div>
                            <span class="text-sm font-code text-white font-bold uppercase group-hover:text-neon-teal transition-colors flex items-center">
                                View Data <i class="fa-solid fa-arrow-right-long ml-3 group-hover:translate-x-2 transition-transform"></i>
                            </span>
                        </div>
                    </div>

                    <div class="glass-card p-10 lg:p-12 rounded-[2.5rem] group cursor-pointer reveal-up flex flex-col justify-between" onclick="openModal('modal-3')">
                        <div>
                            <div class="w-20 h-20 rounded-2xl bg-system-800 border border-neon-lime/30 flex items-center justify-center text-neon-lime text-4xl mb-8 group-hover:scale-110 group-hover:bg-neon-lime/10 transition-all duration-300 shadow-[0_0_20px_rgba(163,230,53,0.1)] group-hover:shadow-[0_0_30px_rgba(163,230,53,0.3)]">
                                <i class="fa-solid fa-droplet"></i>
                            </div>
                            <h3 class="text-3xl font-extrabold text-white mb-4 group-hover:text-neon-lime transition-colors tracking-tight">Automated Irrigation Engine</h3>
                            <p class="text-slate-400 text-lg leading-loose mb-10 pr-4">
                                Pure C++ logical simulation managing intelligent resource constraints, automated sensor triggering algorithms, and dynamic water conservation schedules without external libraries.
                            </p>
                        </div>
                        <div class="flex flex-wrap items-center justify-between border-t border-white/10 pt-8 gap-4">
                            <div class="flex flex-wrap gap-3">
                                <span class="px-4 py-2 rounded-xl bg-system-900 text-neon-lime font-code text-xs font-bold border border-neon-lime/20">C++ Logic</span>
                                <span class="px-4 py-2 rounded-xl bg-system-900 text-neon-emerald font-code text-xs font-bold border border-neon-emerald/20">Algorithms</span>
                            </div>
                            <span class="text-sm font-code text-white font-bold uppercase group-hover:text-neon-lime transition-colors flex items-center">
                                View Data <i class="fa-solid fa-arrow-right-long ml-3 group-hover:translate-x-2 transition-transform"></i>
                            </span>
                        </div>
                    </div>

                    <div class="glass-card p-10 lg:p-12 rounded-[2.5rem] group cursor-pointer reveal-up flex flex-col justify-between" style="transition-delay: 150ms;" onclick="openModal('modal-4')">
                        <div>
                            <div class="w-20 h-20 rounded-2xl bg-system-800 border border-[#ef4444]/30 flex items-center justify-center text-[#ef4444] text-4xl mb-8 group-hover:scale-110 group-hover:bg-[#ef4444]/10 transition-all duration-300 shadow-[0_0_20px_rgba(239,68,68,0.1)] group-hover:shadow-[0_0_30px_rgba(239,68,68,0.3)]">
                                <i class="fa-solid fa-fire-flame-curved"></i>
                            </div>
                            <h3 class="text-3xl font-extrabold text-white mb-4 group-hover:text-[#ef4444] transition-colors tracking-tight">Hardware: Auto Fire Brigade</h3>
                            <p class="text-slate-400 text-lg leading-loose mb-10 pr-4">
                                Embedded systems engineering combining Arduino microcontrollers, physical flame detection sensors, motor drivers, and real-time logic for autonomous fire response robots.
                            </p>
                        </div>
                        <div class="flex flex-wrap items-center justify-between border-t border-white/10 pt-8 gap-4">
                            <div class="flex flex-wrap gap-3">
                                <span class="px-4 py-2 rounded-xl bg-system-900 text-[#ef4444] font-code text-xs font-bold border border-[#ef4444]/20">Arduino</span>
                                <span class="px-4 py-2 rounded-xl bg-system-900 text-neon-amber font-code text-xs font-bold border border-neon-amber/20">Embedded C</span>
                            </div>
                            <span class="text-sm font-code text-white font-bold uppercase group-hover:text-[#ef4444] transition-colors flex items-center">
                                View Data <i class="fa-solid fa-arrow-right-long ml-3 group-hover:translate-x-2 transition-transform"></i>
                            </span>
                        </div>
                    </div>

                </div>
            </div>
        </section>

        <!-- =========================================
             FUTURE TRAJECTORY / NEXT FOCUS
             ========================================= -->
        <section id="focus" class="py-28 px-4 sm:px-6 lg:px-8 border-t border-system-800 bg-system-900/40 relative z-10">
            <div class="max-w-[1400px] mx-auto">
                
                <div class="text-center mb-20 reveal-up">
                    <span class="text-sm font-code text-neon-cyan uppercase tracking-widest block mb-4 font-bold">Evolutionary Path</span>
                    <h2 class="text-4xl sm:text-5xl font-extrabold text-white">Future <span class="text-gradient-cyan">Trajectory</span></h2>
                    <p class="text-slate-400 mt-6 max-w-3xl mx-auto text-lg leading-relaxed">
                        Continuously expanding my architectural expertise. Here is the core technical trifecta I am mastering for the next phase of my professional development.
                    </p>
                </div>

                <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
                    
                    <div class="glass-card p-10 rounded-[2rem] reveal-up group">
                        <div class="w-16 h-16 rounded-2xl bg-system-800 border border-neon-teal/30 flex items-center justify-center text-neon-teal text-3xl mb-8 group-hover:scale-110 group-hover:bg-neon-teal/10 transition-all duration-300">
                            <i class="fa-solid fa-brain"></i>
                        </div>
                        <h3 class="text-2xl font-bold text-white mb-4 group-hover:text-neon-teal transition-colors">AI & Machine Learning</h3>
                        <p class="text-slate-400 text-base leading-relaxed">
                            Deepening my knowledge in Neural Networks, Deep Learning, and Predictive Analytics. Building models capable of processing complex datasets to derive actionable, intelligent insights.
                        </p>
                    </div>

                    <div class="glass-card p-10 rounded-[2rem] reveal-up group" style="transition-delay: 150ms;">
                        <div class="w-16 h-16 rounded-2xl bg-system-800 border border-neon-lime/30 flex items-center justify-center text-neon-lime text-3xl mb-8 group-hover:scale-110 group-hover:bg-neon-lime/10 transition-all duration-300">
                            <i class="fa-solid fa-network-wired"></i>
                        </div>
                        <h3 class="text-2xl font-bold text-white mb-4 group-hover:text-neon-lime transition-colors">Data Structures & Algorithms</h3>
                        <p class="text-slate-400 text-base leading-relaxed">
                            Mastering advanced data structures, graph theory, and algorithm optimization to write highly efficient, scalable, and computationally robust code for complex problem-solving.
                        </p>
                    </div>

                    <div class="glass-card p-10 rounded-[2rem] reveal-up group" style="transition-delay: 300ms;">
                        <div class="w-16 h-16 rounded-2xl bg-system-800 border border-neon-cyan/30 flex items-center justify-center text-neon-cyan text-3xl mb-8 group-hover:scale-110 group-hover:bg-neon-cyan/10 transition-all duration-300">
                            <i class="fa-solid fa-code-branch"></i>
                        </div>
                        <h3 class="text-2xl font-bold text-white mb-4 group-hover:text-neon-cyan transition-colors">Software Engineering</h3>
                        <p class="text-slate-400 text-base leading-relaxed">
                            Mastering advanced design patterns, microservices architecture, and system integration strategies to build highly scalable, maintainable, and fault-tolerant enterprise applications.
                        </p>
                    </div>

                </div>
            </div>
        </section>

        <!-- =========================================
             CONTACT / TERMINAL SECTION (Pristine layout)
             ========================================= -->
        <section id="connect" class="py-28 px-4 sm:px-6 lg:px-8 border-t border-system-800 bg-system-900/60 relative z-10">
            <div class="max-w-[1300px] mx-auto">
                
                <div class="glass-solid rounded-[3rem] p-8 sm:p-12 lg:p-16 border border-neon-emerald/20 shadow-[0_30px_70px_rgba(0,0,0,0.6),0_0_50px_rgba(16,185,129,0.1)] reveal-up">
                    
                    <div class="grid grid-cols-1 lg:grid-cols-2 gap-16 lg:gap-20 items-start">
                        
                        <!-- LEFT SIDE: Text and Links -->
                        <div class="flex flex-col w-full">
                            <div class="mb-12">
                                <span class="text-sm font-code text-neon-emerald uppercase tracking-widest block mb-4 font-bold flex items-center gap-3">
                                    <span class="w-3 h-3 rounded-full bg-neon-emerald animate-ping inline-block"></span> Establishing Handshake
                                </span>
                                <h2 class="text-4xl sm:text-5xl font-extrabold text-white mb-6 leading-tight">Initialize <br> <span class="text-gradient">Connection</span></h2>
                                <p class="text-slate-400 text-lg leading-loose pr-4">
                                    Ready to compile ideas into reality. Open to collaboration on Artificial Intelligence research, software engineering architectures, or advanced technical discussions.
                                </p>
                            </div>

                            <div class="space-y-6 w-full">
                                <a href="mailto:realwahabqadeer@gmail.com" class="flex items-center gap-6 p-6 rounded-2xl bg-system-950/50 border border-system-800 hover:border-neon-emerald/60 hover:bg-system-900 group transition-all duration-300 w-full">
                                    <div class="w-16 h-16 shrink-0 rounded-xl bg-system-900 flex items-center justify-center text-neon-emerald text-2xl group-hover:bg-neon-emerald group-hover:text-system-950 transition-colors shadow-inner">
                                        <i class="fa-solid fa-envelope"></i>
                                    </div>
                                    <div class="flex flex-col overflow-hidden">
                                        <span class="text-xs font-code text-slate-500 uppercase tracking-widest block mb-2">Direct Protocol</span>
                                        <span class="text-lg font-bold text-white group-hover:text-neon-emerald transition-colors truncate">realwahabqadeer@gmail.com</span>
                                    </div>
                                </a>

                                <a href="https://www.linkedin.com/in/wahab-qadeer/" target="_blank" class="flex items-center gap-6 p-6 rounded-2xl bg-system-950/50 border border-system-800 hover:border-blue-500/60 hover:bg-system-900 group transition-all duration-300 w-full">
                                    <div class="w-16 h-16 shrink-0 rounded-xl bg-system-900 flex items-center justify-center text-blue-500 text-2xl group-hover:bg-blue-500 group-hover:text-white transition-colors shadow-inner">
                                        <i class="fa-brands fa-linkedin-in"></i>
                                    </div>
                                    <div class="flex flex-col overflow-hidden">
                                        <span class="text-xs font-code text-slate-500 uppercase tracking-widest block mb-2">Professional Network</span>
                                        <span class="text-lg font-bold text-white group-hover:text-blue-500 transition-colors truncate">linkedin.com/in/wahab-qadeer</span>
                                    </div>
                                </a>
                            </div>
                        </div>

                        <!-- RIGHT SIDE: Enclosed Terminal Form -->
                        <div class="bg-[#000504] rounded-3xl border border-system-700 shadow-2xl w-full flex flex-col overflow-hidden">
                            
                            <!-- Terminal Top Bar -->
                            <div class="bg-system-900 px-6 py-4 flex items-center gap-3 border-b border-system-700">
                                <div class="w-3.5 h-3.5 rounded-full bg-red-500"></div>
                                <div class="w-3.5 h-3.5 rounded-full bg-yellow-500"></div>
                                <div class="w-3.5 h-3.5 rounded-full bg-neon-emerald"></div>
                                <span class="ml-4 text-xs font-code text-slate-400">bash: ~/transmit_payload.sh</span>
                            </div>

                            <!-- Terminal Body -->
                            <div class="p-8 sm:p-10">
                                <form id="contact-form" class="space-y-6">
                                    <div>
                                        <label class="block text-xs font-code font-bold text-neon-emerald mb-2 uppercase tracking-widest">>> String: Identity</label>
                                        <input type="text" required id="form-name" class="w-full bg-system-900/50 border border-system-700 rounded-xl text-white px-5 py-4 focus:outline-none focus:border-neon-emerald focus:ring-1 focus:ring-neon-emerald transition-all font-code text-sm placeholder-slate-600" placeholder="Enter your name">
                                    </div>
                                    <div>
                                        <label class="block text-xs font-code font-bold text-neon-emerald mb-2 uppercase tracking-widest">>> Protocol: Address</label>
                                        <input type="email" required id="form-email" class="w-full bg-system-900/50 border border-system-700 rounded-xl text-white px-5 py-4 focus:outline-none focus:border-neon-emerald focus:ring-1 focus:ring-neon-emerald transition-all font-code text-sm placeholder-slate-600" placeholder="Enter your email">
                                    </div>
                                    <div>
                                        <label class="block text-xs font-code font-bold text-neon-emerald mb-2 uppercase tracking-widest">>> Data: Payload</label>
                                        <textarea rows="4" required id="form-message" class="w-full bg-system-900/50 border border-system-700 rounded-xl text-white px-5 py-4 focus:outline-none focus:border-neon-emerald focus:ring-1 focus:ring-neon-emerald transition-all font-code text-sm placeholder-slate-600 resize-none leading-relaxed" placeholder="Write logic here..."></textarea>
                                    </div>
                                    
                                    <button type="submit" class="w-full py-5 rounded-xl bg-neon-emerald text-system-950 font-black text-base uppercase tracking-widest hover:bg-neon-lime hover:shadow-[0_0_30px_rgba(163,230,53,0.5)] transition-all flex items-center justify-center gap-4 mt-6">
                                        Execute Transmission <i class="fa-solid fa-paper-plane text-xl"></i>
                                    </button>
                                </form>
                            </div>
                        </div>
                        
                    </div>
                </div>
            </div>
        </section>
    </main>

    <!-- FOOTER -->
    <footer class="border-t border-system-800 py-16 px-6 bg-system-950 relative z-10 text-center">
        <div class="max-w-7xl mx-auto flex flex-col items-center gap-8">
            <div class="w-16 h-16 rounded-2xl bg-gradient-to-br from-neon-emerald to-neon-teal flex items-center justify-center text-system-950 font-black text-2xl shadow-[0_0_20px_rgba(16,185,129,0.2)]">WQ</div>
            <p class="text-slate-500 font-code text-base leading-loose">
                System architecture compiled by <span class="text-neon-emerald font-bold">Wahab Qadeer</span> © <span id="current-year"></span>.<br>
                <span class="text-sm opacity-75">BS Artificial Intelligence @ Barani Institute of Information Technology.</span>
            </p>
        </div>
    </footer>

    <!-- =========================================
         FULL SCREEN MODAL SYSTEM (For deep dives)
         ========================================= -->
    
    <div id="modal-1" class="modal-overlay" onclick="closeModal(event, 'modal-1')">
        <div class="modal-box" onclick="event.stopPropagation()">
            <div class="flex justify-between items-start mb-10 border-b border-system-800 pb-8">
                <div>
                    <span class="text-neon-emerald font-code text-sm uppercase tracking-widest font-bold block mb-3">Enterprise Software / OOP</span>
                    <h2 class="text-4xl sm:text-5xl font-extrabold text-white leading-tight">Smart Hospital <br>Management System</h2>
                </div>
                <button onclick="closeModal(null, 'modal-1')" class="w-14 h-14 rounded-full bg-system-800 text-slate-400 hover:text-white hover:bg-red-500/20 border border-transparent hover:border-red-500/50 transition-all flex items-center justify-center shrink-0">
                    <i class="fa-solid fa-xmark text-2xl"></i>
                </button>
            </div>
            
            <div class="grid grid-cols-1 md:grid-cols-3 gap-12 text-slate-300">
                <div class="md:col-span-2 space-y-8">
                    <p class="text-lg leading-loose">A comprehensive desktop application designed to streamline healthcare administration. Built from the ground up using strict Object-Oriented Programming paradigms in Java to ensure maintainability and scalability.</p>
                    
                    <div>
                        <h4 class="text-2xl font-bold text-white mb-6 border-l-4 border-neon-emerald pl-4">Architectural Highlights</h4>
                        <ul class="space-y-5 text-base leading-relaxed">
                            <li class="flex items-start gap-4">
                                <i class="fa-solid fa-check text-neon-emerald mt-1.5 text-lg"></i>
                                <span><strong>Encapsulation & Inheritance:</strong> Implemented clean class hierarchies for Patients, Doctors, and Administrators ensuring data security and modularity.</span>
                            </li>
                            <li class="flex items-start gap-4">
                                <i class="fa-solid fa-check text-neon-emerald mt-1.5 text-lg"></i>
                                <span><strong>Database Connectivity:</strong> Integrated seamlessly with a relational database via JDBC to handle persistent storage of appointments and billing infrastructure.</span>
                            </li>
                            <li class="flex items-start gap-4">
                                <i class="fa-solid fa-check text-neon-emerald mt-1.5 text-lg"></i>
                                <span><strong>Graphical Interface:</strong> Designed intuitive dashboards for administrative staff to quickly input and retrieve critical patient data in emergency situations.</span>
                            </li>
                        </ul>
                    </div>
                </div>
                
                <div class="bg-system-900 rounded-3xl p-8 border border-system-800 h-fit">
                    <h5 class="text-white font-bold mb-6 text-lg uppercase tracking-wider font-code">Tech Stack</h5>
                    <div class="flex flex-col gap-4">
                        <div class="flex items-center gap-5 bg-system-950 p-5 rounded-2xl border border-neon-emerald/20">
                            <i class="fa-brands fa-java text-4xl text-neon-emerald"></i>
                            <div>
                                <span class="block text-white font-bold text-lg">Java</span>
                                <span class="text-xs text-slate-500 font-code uppercase">Core Logic & OOP</span>
                            </div>
                        </div>
                        <div class="flex items-center gap-5 bg-system-950 p-5 rounded-2xl border border-neon-teal/20">
                            <i class="fa-solid fa-database text-4xl text-neon-teal"></i>
                            <div>
                                <span class="block text-white font-bold text-lg">JDBC / SQL</span>
                                <span class="text-xs text-slate-500 font-code uppercase">Database Layer</span>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <!-- Modals 2, 3, 4 -->
    <div id="modal-2" class="modal-overlay" onclick="closeModal(event, 'modal-2')"><div class="modal-box" onclick="event.stopPropagation()"><div class="flex justify-between items-start mb-10 border-b border-system-800 pb-8"><div><span class="text-neon-teal font-code text-sm uppercase tracking-widest font-bold block mb-3">Database Engineering</span><h2 class="text-4xl sm:text-5xl font-extrabold text-white leading-tight">Aero-Reserve DBMS</h2></div><button onclick="closeModal(null, 'modal-2')" class="w-14 h-14 rounded-full bg-system-800 text-slate-400 hover:text-white transition-all flex items-center justify-center shrink-0"><i class="fa-solid fa-xmark text-2xl"></i></button></div><div class="text-slate-300 text-lg leading-loose"><p>A highly normalized relational database project engineered to simulate the backend of an international airline booking system. Includes complex Entity-Relationship modeling translated into strict physical database schemas with foreign key constraints, high-performance JOIN queries, and data normalization ensuring zero insertion anomalies.</p></div></div></div>
    
    <div id="modal-3" class="modal-overlay" onclick="closeModal(event, 'modal-3')"><div class="modal-box" onclick="event.stopPropagation()"><div class="flex justify-between items-start mb-10 border-b border-system-800 pb-8"><div><span class="text-neon-lime font-code text-sm uppercase tracking-widest font-bold block mb-3">Algorithmic Logic</span><h2 class="text-4xl sm:text-5xl font-extrabold text-white leading-tight">Smart Irrigation Engine</h2></div><button onclick="closeModal(null, 'modal-3')" class="w-14 h-14 rounded-full bg-system-800 text-slate-400 hover:text-white transition-all flex items-center justify-center shrink-0"><i class="fa-solid fa-xmark text-2xl"></i></button></div><div class="text-slate-300 text-lg leading-loose"><p>A console-based logic simulation built purely in C++ without external libraries. It models intelligent water distribution based on variable environmental factors, utilizing complex conditional structures and looping logic to simulate resource conservation dynamically.</p></div></div></div>
    
    <div id="modal-4" class="modal-overlay" onclick="closeModal(event, 'modal-4')"><div class="modal-box" onclick="event.stopPropagation()"><div class="flex justify-between items-start mb-10 border-b border-system-800 pb-8"><div><span class="text-[#ef4444] font-code text-sm uppercase tracking-widest font-bold block mb-3">Embedded Systems</span><h2 class="text-4xl sm:text-5xl font-extrabold text-white leading-tight">Auto Fire Brigade</h2></div><button onclick="closeModal(null, 'modal-4')" class="w-14 h-14 rounded-full bg-system-800 text-slate-400 hover:text-white transition-all flex items-center justify-center shrink-0"><i class="fa-solid fa-xmark text-2xl"></i></button></div><div class="text-slate-300 text-lg leading-loose"><p>Hardware and software synergy. Designed and programmed an autonomous robot utilizing physical flame sensors and Arduino microcontrollers. The logic connects sensor inputs to motor driver outputs to detect and maneuver toward fires dynamically in real-time.</p></div></div></div>

    <!-- TOAST NOTIFICATION -->
    <div id="toast" class="fixed bottom-10 right-10 z-50 transform translate-y-40 opacity-0 transition-all duration-500 glass-card px-8 py-6 rounded-2xl flex items-center gap-5 text-white shadow-2xl">
        <i class="fa-solid fa-circle-check text-neon-emerald text-4xl"></i>
        <div>
            <strong class="block text-neon-emerald font-bold text-lg mb-1 tracking-wide">Success 200</strong>
            <span class="text-sm font-code text-slate-300">Payload transmitted successfully.</span>
        </div>
    </div>

    <!-- =========================================
         MASTER JAVASCRIPT ENGINE
         ========================================= -->
    <script>
        document.getElementById('current-year').textContent = new Date().getFullYear();

        const phrases = ["AI & Machine Learning.", "Data Structures & Algorithms.", "Software Engineering."];
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
            let speed = isDel ? 30 : 80;
            if (!isDel && cIdx === current.length) { speed = 3000; isDel = true; } 
            else if (isDel && cIdx === 0) { isDel = false; pIdx = (pIdx + 1) % phrases.length; speed = 500; }
            setTimeout(typeWriter, speed);
        }
        setTimeout(typeWriter, 1200);

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
        }, { threshold: 0.15 });
        revealElements.forEach(el => observer.observe(el));

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
            toast.classList.remove('translate-y-40', 'opacity-0');
            toast.classList.add('translate-y-0', 'opacity-100');
            e.target.reset();
            setTimeout(() => {
                toast.classList.remove('translate-y-0', 'opacity-100');
                toast.classList.add('translate-y-40', 'opacity-0');
            }, 5000); 
        });

        document.addEventListener("DOMContentLoaded", function() {
            Chart.defaults.color = '#64748b'; 
            Chart.defaults.font.family = "'Fira Code', monospace";
            Chart.defaults.font.size = 12;
            
            const tooltipConfig = {
                backgroundColor: 'rgba(3, 18, 15, 0.95)',
                titleColor: '#10b981',
                bodyColor: '#fff',
                borderColor: '#10b981',
                borderWidth: 1,
                padding: 16,
                cornerRadius: 12,
                titleFont: { size: 14, family: "'Inter', sans-serif", weight: 'bold' },
                bodyFont: { size: 13, family: "'Fira Code', monospace" }
            };

            new Chart(document.getElementById('chartDoughnut').getContext('2d'), {
                type: 'doughnut',
                data: {
                    labels: ['Logic & Algorithms', 'System Architecture', 'Database Design', 'Hardware IoT'],
                    datasets: [{
                        data: [35, 25, 25, 15],
                        backgroundColor: ['#10b981', '#14b8a6', '#06b6d4', '#a3e635'],
                        borderColor: '#03120f',
                        borderWidth: 6,
                        hoverOffset: 12
                    }]
                },
                options: {
                    responsive: true, maintainAspectRatio: false, cutout: '72%',
                    plugins: { 
                        legend: { position: 'bottom', labels: { padding: 25, usePointStyle: true } },
                        tooltip: tooltipConfig
                    },
                    animation: { animateScale: true, animateRotate: true, duration: 2000, easing: 'easeOutQuart' }
                }
            });

            new Chart(document.getElementById('chartRadar').getContext('2d'), {
                type: 'radar',
                data: {
                    labels: ['OOP Paradigms', 'SQL Scripting', 'C++ Logic', 'Data Structures', 'Embedded', 'Frontend UI'],
                    datasets: [{
                        label: 'Proficiency Score',
                        data: [95, 90, 85, 88, 80, 75],
                        backgroundColor: 'rgba(20, 184, 166, 0.25)',
                        borderColor: '#14b8a6',
                        pointBackgroundColor: '#fff',
                        pointBorderColor: '#14b8a6',
                        borderWidth: 3, pointRadius: 4, pointHoverRadius: 8
                    }]
                },
                options: {
                    responsive: true, maintainAspectRatio: false,
                    scales: {
                        r: {
                            angleLines: { color: 'rgba(255,255,255,0.08)' },
                            grid: { color: 'rgba(255,255,255,0.08)' },
                            pointLabels: { color: '#6ee7b7', font: {size: 11, family: "'Inter', sans-serif"} },
                            ticks: { display: false, max: 100, min: 0 }
                        }
                    },
                    plugins: { legend: { display: false }, tooltip: tooltipConfig },
                    animation: { duration: 2500 }
                }
            });

            new Chart(document.getElementById('chartPolar').getContext('2d'), {
                type: 'polarArea',
                data: {
                    labels: ['Java OOP', 'SQL DBs', 'HTML/CSS', 'Kotlin App', 'Arduino C'],
                    datasets: [{
                        data: [90, 85, 70, 50, 80],
                        backgroundColor: [
                            'rgba(16, 185, 129, 0.7)', 'rgba(6, 182, 212, 0.7)',
                            'rgba(59, 130, 246, 0.7)', 'rgba(139, 92, 246, 0.7)', 'rgba(239, 68, 68, 0.7)'
                        ],
                        borderColor: '#03120f', borderWidth: 4
                    }]
                },
                options: {
                    responsive: true, maintainAspectRatio: false,
                    scales: { r: { grid: { color: 'rgba(255,255,255,0.08)' }, ticks: {display: false} } },
                    plugins: { 
                        legend: { position: 'right', labels: { padding: 20, usePointStyle: true } },
                        tooltip: tooltipConfig
                    },
                    animation: { duration: 2500 }
                }
            });

            const ctxMixed = document.getElementById('chartMixed').getContext('2d');
            const gradBar = ctxMixed.createLinearGradient(0, 0, 0, 400);
            gradBar.addColorStop(0, 'rgba(6, 182, 212, 0.9)');
            gradBar.addColorStop(1, 'rgba(6, 182, 212, 0.1)');

            new Chart(ctxMixed, {
                type: 'bar',
                data: {
                    labels: ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 'Jul', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec'],
                    datasets: [
                        {
                            type: 'line', label: 'Expected Trajectory',
                            data: [10, 15, 25, 30, 45, 50, 65, 70, 75, 80, 90, 98],
                            borderColor: '#a3e635', borderWidth: 3, borderDash: [6, 6],
                            pointBackgroundColor: '#020806', pointBorderColor: '#a3e635', pointRadius: 6,
                            tension: 0.4
                        },
                        {
                            type: 'bar', label: 'Actual Knowledge Units',
                            data: [12, 18, 22, 35, 42, 55, 60, 68, 80, 85, 88, 95],
                            backgroundColor: gradBar, borderRadius: 6, barPercentage: 0.5
                        }
                    ]
                },
                options: {
                    responsive: true, maintainAspectRatio: false,
                    interaction: { mode: 'index', intersect: false },
                    scales: {
                        x: { grid: { display: false }, ticks: { padding: 12, font: {size: 12} } },
                        y: { 
                            grid: { color: 'rgba(255,255,255,0.05)' }, 
                            max: 100, 
                            ticks: { padding: 15, stepSize: 25, font: {size: 12} } 
                        }
                    },
                    plugins: { legend: { display: false }, tooltip: tooltipConfig },
                    animation: { duration: 3000, delay: (context) => context.dataIndex * 80 } 
                }
            });
        });

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
                this.vx = (Math.random() - 0.5) * 0.4;
                this.vy = (Math.random() - 0.5) * 0.4;
                this.radius = Math.random() * 2 + 0.5;
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

        const particleCount = Math.min(Math.floor((window.innerWidth * window.innerHeight) / 12000), 120);
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
                        ctx.strokeStyle = `rgba(16, 185, 129, ${0.15 * (1 - dist/150)})`;
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
