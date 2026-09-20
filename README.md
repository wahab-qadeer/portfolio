<!DOCTYPE html>
<html lang="en" class="scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Wahab Qadeer | Advanced AI & Software Architect</title>
    
    <!-- Google Fonts: Optimized for Readability and Tech Aesthetic -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Fira+Code:wght@300;400;500;600;700&family=Inter:wght@300;400;500;600;700;800&family=Space+Grotesk:wght@300;400;500;600;700;800&display=swap" rel="stylesheet">
    
    <!-- FontAwesome Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    
    <!-- Chart.js for Advanced Data Visualization -->
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    
    <!-- Tailwind CSS Engine -->
    <script src="https://cdn.tailwindcss.com"></script>
    
    <!-- Tailwind Extended Configuration -->
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
                        void: {
                            950: '#000504',
                            900: '#010f0c',
                            800: '#021a15',
                            700: '#032b23',
                            600: '#054236'
                        },
                        neon: {
                            emerald: '#10b981',
                            lime: '#a3e635',
                            teal: '#14b8a6',
                            mint: '#6ee7b7',
                            cyan: '#06b6d4',
                            amber: '#f59e0b'
                        }
                    },
                    animation: {
                        'spin-slow': 'spin 15s linear infinite',
                        'float': 'float 7s ease-in-out infinite',
                        'float-delayed': 'float 7s ease-in-out 3.5s infinite',
                        'pulse-glow': 'pulseGlow 4s infinite alternate',
                        'morph': 'morph 10s ease-in-out infinite',
                        'scanline': 'scanline 8s linear infinite',
                    },
                    keyframes: {
                        float: {
                            '0%, 100%': { transform: 'translateY(0px)' },
                            '50%': { transform: 'translateY(-20px)' },
                        },
                        pulseGlow: {
                            '0%': { boxShadow: '0 0 15px rgba(16, 185, 129, 0.1)' },
                            '100%': { boxShadow: '0 0 45px rgba(163, 230, 53, 0.4)' },
                        },
                        morph: {
                            '0%': { borderRadius: '60% 40% 30% 70%/60% 30% 70% 40%' },
                            '50%': { borderRadius: '30% 60% 70% 40%/50% 60% 30% 60%' },
                            '100%': { borderRadius: '60% 40% 30% 70%/60% 30% 70% 40%' }
                        },
                        scanline: {
                            '0%': { transform: 'translateY(-100%)' },
                            '100%': { transform: 'translateY(100%)' }
                        }
                    }
                }
            }
        }
    </script>

    <style>
        /* =========================================
           CORE TYPOGRAPHY & BODY STYLES
           ========================================= */
        body {
            background-color: #000504;
            color: #f8fafc;
            font-family: 'Inter', sans-serif;
            overflow-x: hidden;
            -webkit-font-smoothing: antialiased;
            -moz-osx-font-smoothing: grayscale;
            line-height: 1.6;
        }

        h1, h2, h3, h4, h5, h6, .font-heading {
            font-family: 'Space Grotesk', sans-serif;
            letter-spacing: -0.03em;
        }

        /* Highly Legible Paragraphs */
        p {
            line-height: 1.8;
            letter-spacing: 0.01em;
        }

        /* =========================================
           BACKGROUND CANVAS SYSTEM (TRIPLE LAYER)
           ========================================= */
        #matrix-canvas {
            position: fixed; top: 0; left: 0; width: 100%; height: 100%;
            z-index: -11; pointer-events: none; opacity: 0.15;
        }
        #neural-canvas {
            position: fixed; top: 0; left: 0; width: 100%; height: 100%;
            z-index: -10; pointer-events: none; opacity: 0.3;
        }
        #interaction-canvas {
            position: fixed; top: 0; left: 0; width: 100%; height: 100%;
            z-index: -9; pointer-events: none;
        }

        /* Abstract Ambient Lighting Blobs */
        .ambient-blob {
            position: absolute; filter: blur(90px); z-index: -8; opacity: 0.12;
            pointer-events: none; animation: morph 20s ease-in-out infinite;
        }
        .blob-1 { top: -10%; left: -5%; width: 50vw; height: 50vw; background: linear-gradient(135deg, #10b981, #14b8a6); }
        .blob-2 { bottom: -10%; right: -5%; width: 40vw; height: 40vw; background: linear-gradient(135deg, #14b8a6, #06b6d4); animation-delay: -5s; }
        .blob-3 { top: 30%; left: 30%; width: 30vw; height: 30vw; background: linear-gradient(135deg, #a3e635, #10b981); animation-delay: -10s; }

        /* =========================================
           GLASSMORPHISM & UI PANELS
           ========================================= */
        .glass-panel {
            background: rgba(3, 43, 35, 0.25);
            backdrop-filter: blur(24px);
            -webkit-backdrop-filter: blur(24px);
            border: 1px solid rgba(255, 255, 255, 0.06);
            box-shadow: 0 20px 40px -10px rgba(0, 0, 0, 0.8);
            transition: all 0.5s cubic-bezier(0.4, 0, 0.2, 1);
        }
        
        .glass-panel:hover {
            background: rgba(3, 43, 35, 0.45);
            border-color: rgba(16, 185, 129, 0.3);
            box-shadow: 0 30px 60px -15px rgba(16, 185, 129, 0.2);
            transform: translateY(-4px);
        }

        .glass-panel-solid {
            background: linear-gradient(145deg, rgba(5, 66, 54, 0.9), rgba(2, 26, 21, 0.95));
            border: 1px solid rgba(20, 184, 166, 0.3);
            box-shadow: 0 0 30px rgba(16, 185, 129, 0.1);
        }

        /* =========================================
           INTERACTIVE 3D PROFILE PICTURE (NOT CIRCULAR)
           ========================================= */
        .dp-container {
            perspective: 1200px;
            width: 100%;
            max-width: 420px;
            margin: 0 auto;
        }

        .dp-card {
            width: 100%;
            height: 520px;
            position: relative;
            transform-style: preserve-3d;
            border-radius: 2rem;
            background: rgba(3, 43, 35, 0.4);
            border: 2px solid rgba(16, 185, 129, 0.4);
            box-shadow: 0 25px 50px rgba(0,0,0,0.5), inset 0 0 30px rgba(16,185,129,0.2);
            transition: transform 0.1s ease-out; /* JS controlled for smooth 3D */
            overflow: visible;
        }

        .dp-image-wrapper {
            position: absolute;
            inset: 12px;
            border-radius: 1.5rem;
            overflow: hidden;
            transform: translateZ(30px); /* Pops out of the card */
            box-shadow: 0 15px 35px rgba(0,0,0,0.6);
        }

        .dp-image-wrapper img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            filter: contrast(1.05) brightness(0.95) saturate(1.1);
            transition: transform 0.8s ease;
        }

        .dp-container:hover .dp-image-wrapper img {
            transform: scale(1.08);
            filter: contrast(1.1) brightness(1.05) saturate(1.2);
        }

        /* 3D Floating Badges */
        .dp-badge {
            position: absolute;
            transform: translateZ(60px);
            backdrop-filter: blur(12px);
            background: rgba(3, 43, 35, 0.85);
            border: 1px solid rgba(16, 185, 129, 0.5);
            border-radius: 1rem;
            padding: 0.75rem 1.25rem;
            color: #fff;
            font-family: 'Fira Code', monospace;
            font-size: 0.75rem;
            font-weight: 700;
            box-shadow: 0 10px 20px rgba(0,0,0,0.5);
            display: flex;
            align-items: center;
            gap: 0.5rem;
            transition: all 0.3s ease;
        }
        
        .badge-1 { bottom: -20px; right: -20px; }
        .badge-2 { top: 40px; left: -30px; }

        /* =========================================
           TYPOGRAPHY & GRADIENTS
           ========================================= */
        .text-gradient-primary {
            background: linear-gradient(135deg, #10b981 0%, #a3e635 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }
        
        .text-gradient-secondary {
            background: linear-gradient(135deg, #14b8a6 0%, #6ee7b7 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .typing-caret::after {
            content: '█';
            animation: blink 1s step-end infinite;
            color: #10b981;
            margin-left: 6px;
        }
        @keyframes blink { 0%, 100% { opacity: 1; } 50% { opacity: 0; } }

        /* =========================================
           DATA HEATMAP SYSTEM (SPACIOUS)
           ========================================= */
        .heatmap-wrapper {
            width: 100%;
            overflow-x: auto;
            padding: 10px 0;
        }
        .heatmap-grid {
            display: grid;
            grid-template-columns: repeat(52, 1fr);
            gap: 6px; /* Increased gap for better arrangement */
            min-width: 800px; /* Forces scroll on small screens, prevents cramping */
        }
        .heatmap-cell {
            width: 14px;
            height: 14px;
            border-radius: 3px;
            background-color: #032b23;
            transition: all 0.2s ease;
            position: relative;
        }
        .heatmap-cell:hover {
            transform: scale(1.6);
            box-shadow: 0 0 12px #10b981;
            z-index: 10;
            border: 1px solid #fff;
        }
        .level-0 { background-color: #021a15; }
        .level-1 { background-color: #054236; }
        .level-2 { background-color: #0b8066; }
        .level-3 { background-color: #10b981; }
        .level-4 { background-color: #a3e635; }

        /* =========================================
           UTILITIES & ANIMATIONS
           ========================================= */
        .reveal {
            opacity: 0;
            transform: translateY(50px);
            transition: all 1.2s cubic-bezier(0.16, 1, 0.3, 1);
        }
        .reveal.active {
            opacity: 1;
            transform: translateY(0);
        }

        .stagger-1 { transition-delay: 100ms; }
        .stagger-2 { transition-delay: 200ms; }
        .stagger-3 { transition-delay: 300ms; }

        /* Scrollbars */
        ::-webkit-scrollbar { width: 12px; height: 12px; }
        ::-webkit-scrollbar-track { background: #000504; }
        ::-webkit-scrollbar-thumb { background: #032b23; border-radius: 6px; border: 3px solid #000504; }
        ::-webkit-scrollbar-thumb:hover { background: #10b981; }

        /* Modal Overlay */
        .modal-backdrop {
            position: fixed; inset: 0;
            background: rgba(0, 5, 4, 0.9);
            backdrop-filter: blur(20px);
            z-index: 100;
            display: flex; align-items: center; justify-content: center;
            opacity: 0; pointer-events: none;
            transition: all 0.4s ease;
            padding: 1rem;
        }
        .modal-backdrop.active { opacity: 1; pointer-events: all; }
        
        .modal-window {
            background: #010f0c;
            border: 1px solid rgba(20, 184, 166, 0.4);
            border-radius: 2rem;
            width: 100%; max-width: 900px;
            max-height: 90vh; overflow-y: auto;
            transform: scale(0.95) translateY(30px);
            transition: all 0.5s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            box-shadow: 0 30px 60px rgba(0,0,0,0.9), 0 0 50px rgba(16, 185, 129, 0.15);
        }
        .modal-backdrop.active .modal-window { transform: scale(1) translateY(0); }
    </style>
</head>
<body class="selection:bg-neon-emerald selection:text-void-950">

    <!-- =========================================
         BACKGROUND CANVAS SYSTEM
         ========================================= -->
    <canvas id="matrix-canvas"></canvas>
    <canvas id="neural-canvas"></canvas>
    <canvas id="interaction-canvas"></canvas>
    
    <!-- Ambient Lighting -->
    <div class="ambient-blob blob-1"></div>
    <div class="ambient-blob blob-2"></div>
    <div class="ambient-blob blob-3"></div>

    <!-- =========================================
         HEADER / NAVIGATION
         ========================================= -->
    <header class="fixed top-0 left-0 w-full z-50 transition-all duration-500 px-4 sm:px-8 py-5" id="main-header">
        <div class="max-w-[1400px] mx-auto">
            <div class="glass-panel rounded-2xl px-6 md:px-10 py-4 flex items-center justify-between">
                
                <!-- Logo -->
                <a href="#" class="font-heading font-bold text-2xl tracking-wide text-white flex items-center gap-4 group">
                    <div class="w-12 h-12 rounded-xl bg-gradient-to-br from-neon-emerald to-neon-teal flex items-center justify-center text-void-950 font-black text-xl shadow-[0_0_20px_rgba(16,185,129,0.5)] transform group-hover:rotate-12 transition-all duration-300">
                        WQ
                    </div>
                    <div class="flex flex-col">
                        <span class="leading-none group-hover:text-neon-emerald transition-colors">Wahab<span class="text-neon-emerald">.ai</span></span>
                        <span class="text-[10px] text-slate-400 font-code tracking-widest uppercase mt-1">Portfolio System</span>
                    </div>
                </a>

                <!-- Desktop Nav (Extremely spacious) -->
                <nav class="hidden lg:flex items-center space-x-12 text-sm font-semibold text-slate-300">
                    <a href="#about" class="hover:text-neon-emerald hover:-translate-y-1 transition-all duration-300">01. Architecture</a>
                    <a href="#dashboard" class="hover:text-neon-emerald hover:-translate-y-1 transition-all duration-300">02. Analytics</a>
                    <a href="#projects" class="hover:text-neon-emerald hover:-translate-y-1 transition-all duration-300">03. Systems Built</a>
                    <a href="#timeline" class="hover:text-neon-emerald hover:-translate-y-1 transition-all duration-300">04. Timeline</a>
                </nav>

                <!-- Action Button -->
                <a href="#connect" class="hidden md:flex px-8 py-3 rounded-xl bg-neon-emerald text-void-950 font-bold text-sm uppercase tracking-widest hover:bg-neon-lime transition-all shadow-[0_0_20px_rgba(16,185,129,0.4)] hover:shadow-[0_0_35px_rgba(163,230,53,0.6)] items-center gap-3 transform hover:scale-105">
                    <i class="fa-solid fa-terminal"></i> Initialize
                </a>

                <!-- Mobile Menu Button -->
                <button class="lg:hidden text-white text-2xl hover:text-neon-emerald transition-colors">
                    <i class="fa-solid fa-bars-staggered"></i>
                </button>
            </div>
        </div>
    </header>

    <main class="relative pt-36 pb-20">

        <!-- =========================================
             HERO SECTION (LEFT-ALIGNED 3D IMAGE, SPACIOUS TEXT)
             ========================================= -->
        <section class="min-h-[85vh] flex items-center justify-center px-4 sm:px-6 lg:px-8 py-12 relative overflow-hidden">
            <div class="max-w-[1400px] mx-auto w-full">
                
                <!-- Flex container: Image Left, Text Right on Desktop -->
                <div class="flex flex-col lg:flex-row items-center justify-between gap-16 lg:gap-20">
                    
                    <!-- LEFT COLUMN: 3D Interactive Profile Card -->
                    <div class="w-full lg:w-5/12 flex justify-center order-2 lg:order-1 reveal">
                        <div class="dp-container" id="dp-container">
                            <div class="dp-card" id="dp-card">
                                
                                <!-- Floating 3D Badges -->
                                <div class="dp-badge badge-1 animate-float">
                                    <span class="w-2 h-2 rounded-full bg-neon-lime animate-ping"></span>
                                    Status: Online
                                </div>
                                <div class="dp-badge badge-2 animate-float-delayed">
                                    <i class="fa-solid fa-microchip text-neon-teal"></i>
                                    BS(AI) Candidate
                                </div>

                                <div class="dp-image-wrapper">
                                    <!-- User Image -->
                                    <img 
                                        src="WhatsApp Image 2026-08-13 at 1.09.24 PM_2.jpeg" 
                                        alt="Wahab Qadeer Portfolio Identity" 
                                        onerror="this.src='https://placehold.co/600x800/032b23/10b981?text=Wahab+Qadeer'"
                                    >
                                </div>
                            </div>
                        </div>
                    </div>

                    <!-- RIGHT COLUMN: Well-Arranged Typography -->
                    <div class="w-full lg:w-7/12 flex flex-col items-center lg:items-start text-center lg:text-left order-1 lg:order-2 reveal stagger-1">
                        
                        <!-- System Status -->
                        <div class="inline-flex items-center gap-3 px-6 py-2.5 rounded-full glass-panel border-neon-emerald/30 text-neon-emerald text-xs sm:text-sm font-code uppercase tracking-widest shadow-[0_0_20px_rgba(16,185,129,0.1)] mb-8">
                            <i class="fa-solid fa-shield-check text-base"></i>
                            BIIT Artificial Intelligence Department
                        </div>

                        <!-- Massive, Breathable Headlines -->
                        <h1 class="text-5xl sm:text-6xl lg:text-[5rem] font-extrabold tracking-tighter text-white leading-[1.05] mb-6">
                            Architecting <br>
                            <span class="text-gradient-primary">Intelligent</span> Systems.
                        </h1>

                        <!-- Dynamic Typing with ample height to prevent layout shifts -->
                        <div class="text-xl sm:text-2xl lg:text-3xl font-medium text-slate-300 h-16 flex items-center justify-center lg:justify-start mb-4">
                            <span>I build </span>
                            <span id="typing-text" class="typing-caret font-code text-neon-teal font-bold ml-3 border-b-2 border-neon-teal/30 pb-1"></span>
                        </div>

                        <!-- Highly readable, well-spaced body text -->
                        <p class="text-slate-400 text-lg sm:text-xl leading-relaxed max-w-2xl mx-auto lg:mx-0 font-light mb-12">
                            Computer Science undergraduate specializing in Artificial Intelligence. Bridging the gap between raw data, complex algorithmic logic, and robust object-oriented software architectures to solve real-world problems.
                        </p>

                        <!-- Action Buttons & KPI Metrics spaced perfectly -->
                        <div class="flex flex-col sm:flex-row items-center gap-10 justify-center lg:justify-start w-full">
                            
                            <a href="#dashboard" class="px-8 py-4 rounded-xl bg-gradient-to-r from-neon-emerald to-neon-teal text-void-950 font-black text-base tracking-wide hover:shadow-[0_0_40px_rgba(16,185,129,0.6)] transition-all flex items-center gap-3 transform hover:-translate-y-1">
                                <i class="fa-solid fa-chart-network"></i> Explore Analytics
                            </a>
                            
                            <!-- KPI Metrics separated by borders -->
                            <div class="flex gap-8 items-center bg-void-900/50 p-4 rounded-2xl border border-white/5">
                                <div class="text-left px-2">
                                    <span class="block text-3xl font-black text-white counter" data-target="15">0</span>
                                    <span class="text-[10px] text-neon-teal uppercase tracking-widest font-bold">Projects Built</span>
                                </div>
                                <div class="w-px h-12 bg-white/10"></div>
                                <div class="text-left px-2">
                                    <span class="block text-3xl font-black text-white counter" data-target="98">0</span>
                                    <span class="text-[10px] text-neon-lime uppercase tracking-widest font-bold">Code Efficiency %</span>
                                </div>
                            </div>
                        </div>

                    </div>
                </div>
            </div>
        </section>

        <!-- =========================================
             BENTO-BOX ANALYTICS DASHBOARD (EXPANDED & SPACIOUS)
             ========================================= -->
        <section id="dashboard" class="py-28 px-4 sm:px-6 lg:px-8 relative z-10 border-t border-void-800 bg-void-950/80">
            <div class="max-w-[1400px] mx-auto">
                
                <!-- Section Header with wide margins -->
                <div class="text-center mb-20 reveal">
                    <span class="text-sm font-code text-neon-teal uppercase tracking-widest block mb-4 font-bold flex items-center justify-center gap-3">
                        <i class="fa-solid fa-radar text-neon-lime animate-spin-slow text-lg"></i> Telemetry & Metrics
                    </span>
                    <h2 class="text-4xl sm:text-5xl lg:text-6xl font-extrabold text-white mb-6">Live <span class="text-gradient-primary">Growth Dashboard</span></h2>
                    <p class="text-slate-400 max-w-3xl mx-auto text-lg leading-relaxed">
                        A real-time visualization of my skill acquisition, technological proficiencies, and architectural competencies represented through interactive data nodes.
                    </p>
                </div>

                <!-- BENTO GRID SYSTEM: 
                     Using grid-cols-12 to perfectly manage space.
                     Top Row: 4 + 4 + 4
                     Middle Row: 12 (Wide chart)
                     Bottom Row: 12 (Heatmap) -->
                <div class="grid grid-cols-1 lg:grid-cols-12 gap-8 reveal">
                    
                    <!-- WIDGET 1: Skill Distribution (Doughnut Chart) -->
                    <div class="glass-panel-solid p-10 rounded-3xl flex flex-col h-full relative overflow-hidden lg:col-span-4">
                        <div class="absolute -right-10 -top-10 w-48 h-48 bg-neon-emerald/20 blur-3xl rounded-full pointer-events-none"></div>
                        
                        <div class="mb-8">
                            <h3 class="text-2xl font-bold text-white mb-2 flex items-center gap-3">
                                <i class="fa-solid fa-chart-pie text-neon-emerald"></i> Resource Allocation
                            </h3>
                            <p class="text-sm text-slate-400 font-code uppercase tracking-wider">Depth Distribution %</p>
                        </div>
                        
                        <div class="relative flex-grow min-h-[280px] w-full flex items-center justify-center">
                            <canvas id="chartDoughnut"></canvas>
                        </div>
                    </div>

                    <!-- WIDGET 2: Core Competencies (Radar Chart) -->
                    <div class="glass-panel-solid p-10 rounded-3xl flex flex-col h-full relative overflow-hidden lg:col-span-4">
                        <div class="absolute -left-10 -bottom-10 w-48 h-48 bg-neon-teal/20 blur-3xl rounded-full pointer-events-none"></div>
                        
                        <div class="mb-8">
                            <h3 class="text-2xl font-bold text-white mb-2 flex items-center gap-3">
                                <i class="fa-solid fa-bullseye text-neon-teal"></i> Vector Analysis
                            </h3>
                            <p class="text-sm text-slate-400 font-code uppercase tracking-wider">Competency Radar Matrix</p>
                        </div>

                        <div class="relative flex-grow min-h-[280px] w-full flex items-center justify-center">
                            <canvas id="chartRadar"></canvas>
                        </div>
                    </div>

                    <!-- WIDGET 3: Tech Stack Mastery (Polar Area Chart) -->
                    <div class="glass-panel-solid p-10 rounded-3xl flex flex-col h-full relative overflow-hidden lg:col-span-4">
                        <div class="absolute right-1/2 top-1/2 w-48 h-48 bg-neon-lime/10 blur-3xl rounded-full transform translate-x-1/2 -translate-y-1/2 pointer-events-none"></div>
                        
                        <div class="mb-8">
                            <h3 class="text-2xl font-bold text-white mb-2 flex items-center gap-3">
                                <i class="fa-solid fa-layer-group text-neon-lime"></i> Tech Stack Mastery
                            </h3>
                            <p class="text-sm text-slate-400 font-code uppercase tracking-wider">Syntax & Frameworks</p>
                        </div>

                        <div class="relative flex-grow min-h-[280px] w-full flex items-center justify-center">
                            <canvas id="chartPolar"></canvas>
                        </div>
                    </div>

                    <!-- WIDGET 4: Learning Velocity (Wide Bar/Line Combo Chart) -->
                    <div class="glass-panel-solid p-10 rounded-3xl lg:col-span-12 flex flex-col relative overflow-hidden">
                        <div class="absolute top-0 right-0 w-full h-1 bg-gradient-to-r from-transparent via-neon-cyan to-transparent"></div>
                        
                        <div class="flex flex-col md:flex-row md:items-center justify-between mb-10 gap-6">
                            <div>
                                <h3 class="text-2xl font-bold text-white mb-2 flex items-center gap-3">
                                    <i class="fa-solid fa-chart-line text-neon-cyan"></i> Learning Velocity
                                </h3>
                                <p class="text-sm text-slate-400 font-code uppercase tracking-wider">12-Month Knowledge Progression Trend</p>
                            </div>
                            
                            <!-- Custom Chart Legend -->
                            <div class="flex gap-6 bg-void-900/60 p-4 rounded-xl border border-white/5">
                                <div class="flex items-center gap-2">
                                    <div class="w-4 h-4 rounded-sm bg-neon-cyan/50 border border-neon-cyan"></div>
                                    <span class="text-xs text-slate-300 font-code">Actual Units</span>
                                </div>
                                <div class="flex items-center gap-2">
                                    <div class="w-6 h-1 bg-neon-lime border-t border-dashed border-void-950"></div>
                                    <span class="text-xs text-slate-300 font-code">Expected Trajectory</span>
                                </div>
                            </div>
                        </div>

                        <div class="relative h-[350px] w-full">
                            <canvas id="chartMixed"></canvas>
                        </div>
                    </div>

                    <!-- WIDGET 5: GitHub Style Activity Heatmap (Ultra Spacious) -->
                    <div class="glass-panel-solid p-10 rounded-3xl lg:col-span-12 flex flex-col">
                        
                        <div class="flex flex-col md:flex-row md:items-center justify-between mb-8 gap-6">
                            <div>
                                <h3 class="text-2xl font-bold text-white mb-2 flex items-center gap-3">
                                    <i class="fa-solid fa-calendar-days text-neon-emerald"></i> Compilation Matrix
                                </h3>
                                <p class="text-sm text-slate-400 font-code uppercase tracking-wider">365-Day Code Activity Density</p>
                            </div>
                            <div class="flex items-center gap-3 text-xs text-slate-400 font-code uppercase font-bold tracking-widest bg-void-900/60 p-4 rounded-xl border border-white/5">
                                <span>Less</span>
                                <div class="flex gap-2">
                                    <div class="w-4 h-4 rounded-sm bg-[#021a15]"></div>
                                    <div class="w-4 h-4 rounded-sm bg-[#054236]"></div>
                                    <div class="w-4 h-4 rounded-sm bg-[#0b8066]"></div>
                                    <div class="w-4 h-4 rounded-sm bg-[#10b981]"></div>
                                    <div class="w-4 h-4 rounded-sm bg-[#a3e635]"></div>
                                </div>
                                <span>More</span>
                            </div>
                        </div>
                        
                        <!-- Heatmap Container -->
                        <div class="bg-void-900/50 p-8 rounded-2xl border border-void-700 overflow-hidden shadow-inner heatmap-wrapper">
                            <div class="heatmap-grid" id="heatmap-container"></div>
                        </div>
                        
                    </div>

                </div>
            </div>
        </section>

        <!-- =========================================
             PROJECTS / SYSTEMS BUILT SECTION
             ========================================= -->
        <section id="projects" class="py-28 px-4 sm:px-6 lg:px-8 bg-void-900/30 border-y border-void-800 relative z-10">
            <div class="max-w-[1400px] mx-auto">
                
                <!-- Highly spaced Header -->
                <div class="flex flex-col md:flex-row justify-between items-end mb-20 reveal gap-8">
                    <div>
                        <span class="text-sm font-code text-neon-lime uppercase tracking-widest block mb-4 font-bold">Execution & Deployment</span>
                        <h2 class="text-4xl sm:text-5xl lg:text-6xl font-extrabold text-white">Engineered <span class="text-gradient-secondary">Systems</span></h2>
                    </div>
                    <p class="text-slate-400 max-w-xl text-lg leading-relaxed text-left md:text-right">
                        Click on any architecture node below to open a full-screen diagnostic overlay detailing source logic, database schemas, and implementation features.
                    </p>
                </div>

                <!-- Projects Grid: Enormous space for text to breathe -->
                <div class="grid grid-cols-1 md:grid-cols-2 gap-10">
                    
                    <!-- Project 1 -->
                    <div class="glass-panel p-10 lg:p-12 rounded-[2rem] group cursor-pointer reveal project-card flex flex-col justify-between" onclick="openModal('modal-1')">
                        <div>
                            <div class="w-20 h-20 rounded-[1.5rem] bg-void-800 border border-neon-emerald/30 flex items-center justify-center text-neon-emerald text-4xl mb-8 group-hover:scale-110 group-hover:bg-neon-emerald/10 transition-all duration-500 shadow-[0_0_20px_rgba(16,185,129,0.1)] group-hover:shadow-[0_0_35px_rgba(16,185,129,0.3)]">
                                <i class="fa-solid fa-hospital-user"></i>
                            </div>
                            <h3 class="text-3xl font-extrabold text-white mb-4 tracking-tight group-hover:text-neon-emerald transition-colors">Smart Hospital Core</h3>
                            <p class="text-slate-400 text-base leading-loose mb-10 pr-4">
                                An enterprise-level desktop application enforcing strict Object-Oriented paradigms (Java) connected to a relational database to manage complex medical logistics, patient records, and doctor scheduling.
                            </p>
                        </div>
                        <div class="flex items-center justify-between border-t border-white/10 pt-6">
                            <div class="flex flex-wrap gap-3">
                                <span class="px-4 py-2 rounded-lg bg-void-900 text-neon-emerald font-code text-xs font-bold border border-neon-emerald/20">Java OOP</span>
                                <span class="px-4 py-2 rounded-lg bg-void-900 text-neon-teal font-code text-xs font-bold border border-neon-teal/20">SQL DB</span>
                            </div>
                            <span class="text-sm font-code text-neon-emerald font-bold tracking-widest uppercase flex items-center gap-3 group-hover:translate-x-3 transition-transform duration-300">
                                Analyze <i class="fa-solid fa-arrow-right-long"></i>
                            </span>
                        </div>
                    </div>

                    <!-- Project 2 -->
                    <div class="glass-panel p-10 lg:p-12 rounded-[2rem] group cursor-pointer reveal project-card flex flex-col justify-between stagger-1" onclick="openModal('modal-2')">
                        <div>
                            <div class="w-20 h-20 rounded-[1.5rem] bg-void-800 border border-neon-teal/30 flex items-center justify-center text-neon-teal text-4xl mb-8 group-hover:scale-110 group-hover:bg-neon-teal/10 transition-all duration-500 shadow-[0_0_20px_rgba(20,184,166,0.1)] group-hover:shadow-[0_0_35px_rgba(20,184,166,0.3)]">
                                <i class="fa-solid fa-plane-up"></i>
                            </div>
                            <h3 class="text-3xl font-extrabold text-white mb-4 tracking-tight group-hover:text-neon-teal transition-colors">Aero-Reserve RDBMS</h3>
                            <p class="text-slate-400 text-base leading-loose mb-10 pr-4">
                                A complex relational schema design demonstrating highly normalized tables, high-performance JOINs, indexing strategies, and strict transactional integrity for airline booking systems.
                            </p>
                        </div>
                        <div class="flex items-center justify-between border-t border-white/10 pt-6">
                            <div class="flex flex-wrap gap-3">
                                <span class="px-4 py-2 rounded-lg bg-void-900 text-neon-teal font-code text-xs font-bold border border-neon-teal/20">SQL Server</span>
                                <span class="px-4 py-2 rounded-lg bg-void-900 text-neon-cyan font-code text-xs font-bold border border-neon-cyan/20">ER Modeling</span>
                            </div>
                            <span class="text-sm font-code text-neon-teal font-bold tracking-widest uppercase flex items-center gap-3 group-hover:translate-x-3 transition-transform duration-300">
                                Analyze <i class="fa-solid fa-arrow-right-long"></i>
                            </span>
                        </div>
                    </div>

                    <!-- Project 3 -->
                    <div class="glass-panel p-10 lg:p-12 rounded-[2rem] group cursor-pointer reveal project-card flex flex-col justify-between" onclick="openModal('modal-3')">
                        <div>
                            <div class="w-20 h-20 rounded-[1.5rem] bg-void-800 border border-neon-lime/30 flex items-center justify-center text-neon-lime text-4xl mb-8 group-hover:scale-110 group-hover:bg-neon-lime/10 transition-all duration-500 shadow-[0_0_20px_rgba(163,230,53,0.1)] group-hover:shadow-[0_0_35px_rgba(163,230,53,0.3)]">
                                <i class="fa-solid fa-droplet"></i>
                            </div>
                            <h3 class="text-3xl font-extrabold text-white mb-4 tracking-tight group-hover:text-neon-lime transition-colors">Automated Irrigation Engine</h3>
                            <p class="text-slate-400 text-base leading-loose mb-10 pr-4">
                                A pure C++ logical simulation engineering smart resource constraints, automated sensor triggering algorithms, and dynamic water conservation scheduling without external libraries.
                            </p>
                        </div>
                        <div class="flex items-center justify-between border-t border-white/10 pt-6">
                            <div class="flex flex-wrap gap-3">
                                <span class="px-4 py-2 rounded-lg bg-void-900 text-neon-lime font-code text-xs font-bold border border-neon-lime/20">C++ Logic</span>
                                <span class="px-4 py-2 rounded-lg bg-void-900 text-neon-emerald font-code text-xs font-bold border border-neon-emerald/20">Algorithms</span>
                            </div>
                            <span class="text-sm font-code text-neon-lime font-bold tracking-widest uppercase flex items-center gap-3 group-hover:translate-x-3 transition-transform duration-300">
                                Analyze <i class="fa-solid fa-arrow-right-long"></i>
                            </span>
                        </div>
                    </div>

                    <!-- Project 4 (Hardware) -->
                    <div class="glass-panel p-10 lg:p-12 rounded-[2rem] group cursor-pointer reveal project-card flex flex-col justify-between stagger-1" onclick="openModal('modal-4')">
                        <div>
                            <div class="w-20 h-20 rounded-[1.5rem] bg-void-800 border border-[#ef4444]/30 flex items-center justify-center text-[#ef4444] text-4xl mb-8 group-hover:scale-110 group-hover:bg-[#ef4444]/10 transition-all duration-500 shadow-[0_0_20px_rgba(239,68,68,0.1)] group-hover:shadow-[0_0_35px_rgba(239,68,68,0.3)]">
                                <i class="fa-solid fa-fire-flame-curved"></i>
                            </div>
                            <h3 class="text-3xl font-extrabold text-white mb-4 tracking-tight group-hover:text-[#ef4444] transition-colors">Hardware: Auto Fire Brigade</h3>
                            <p class="text-slate-400 text-base leading-loose mb-10 pr-4">
                                Embedded systems engineering combining Arduino microcontrollers, physical flame detection sensors, motor drivers, and real-time actuation logic for autonomous fire response.
                            </p>
                        </div>
                        <div class="flex items-center justify-between border-t border-white/10 pt-6">
                            <div class="flex flex-wrap gap-3">
                                <span class="px-4 py-2 rounded-lg bg-void-900 text-[#ef4444] font-code text-xs font-bold border border-[#ef4444]/20">Arduino</span>
                                <span class="px-4 py-2 rounded-lg bg-void-900 text-neon-amber font-code text-xs font-bold border border-neon-amber/20">Embedded C</span>
                            </div>
                            <span class="text-sm font-code text-[#ef4444] font-bold tracking-widest uppercase flex items-center gap-3 group-hover:translate-x-3 transition-transform duration-300">
                                Analyze <i class="fa-solid fa-arrow-right-long"></i>
                            </span>
                        </div>
                    </div>

                </div>
            </div>
        </section>

        <!-- =========================================
             TERMINAL / CONTACT SECTION (WELL MANAGED)
             ========================================= -->
        <section id="connect" class="py-28 px-4 sm:px-6 lg:px-8 bg-void-900/80 border-t border-void-800 relative z-10">
            <div class="max-w-[1200px] mx-auto">
                
                <div class="glass-panel-solid rounded-[3rem] p-10 md:p-16 lg:p-20 border border-neon-emerald/30 shadow-[0_40px_80px_-20px_rgba(0,0,0,0.9),0_0_60px_rgba(16,185,129,0.15)] reveal">
                    
                    <div class="grid grid-cols-1 lg:grid-cols-2 gap-20">
                        
                        <!-- Left: Info & Spaced Links -->
                        <div class="flex flex-col justify-between">
                            <div class="mb-12">
                                <span class="text-sm font-code text-neon-emerald uppercase tracking-widest block mb-4 font-bold flex items-center gap-3">
                                    <span class="w-3 h-3 rounded-full bg-neon-emerald animate-ping inline-block"></span> Establishing Handshake
                                </span>
                                <h2 class="text-4xl sm:text-5xl font-extrabold text-white mb-6">Initialize <span class="text-gradient-primary">Connection</span></h2>
                                <p class="text-slate-400 text-lg leading-loose pr-4">
                                    Ready to compile ideas into reality. Open to collaboration on Artificial Intelligence research, software engineering architectures, or advanced technical discussions.
                                </p>
                            </div>

                            <div class="space-y-6">
                                <a href="mailto:realwahabqadeer@gmail.com" class="flex items-center gap-6 p-6 rounded-2xl bg-void-800/50 border border-void-700 hover:border-neon-emerald/50 group transition-all duration-300 transform hover:translate-x-3 hover:bg-void-800">
                                    <div class="w-16 h-16 rounded-xl bg-void-950 flex items-center justify-center text-neon-emerald text-2xl group-hover:bg-neon-emerald group-hover:text-void-950 transition-colors shadow-inner">
                                        <i class="fa-solid fa-envelope"></i>
                                    </div>
                                    <div>
                                        <span class="text-xs font-code text-slate-500 uppercase tracking-widest block mb-2">Direct Protocol</span>
                                        <span class="text-lg font-bold text-white group-hover:text-neon-emerald transition-colors">realwahabqadeer@gmail.com</span>
                                    </div>
                                </a>

                                <a href="https://www.linkedin.com/in/wahab-qadeer/" target="_blank" class="flex items-center gap-6 p-6 rounded-2xl bg-void-800/50 border border-void-700 hover:border-neon-cyan/50 group transition-all duration-300 transform hover:translate-x-3 hover:bg-void-800">
                                    <div class="w-16 h-16 rounded-xl bg-void-950 flex items-center justify-center text-neon-cyan text-2xl group-hover:bg-neon-cyan group-hover:text-void-950 transition-colors shadow-inner">
                                        <i class="fa-brands fa-linkedin-in"></i>
                                    </div>
                                    <div>
                                        <span class="text-xs font-code text-slate-500 uppercase tracking-widest block mb-2">Professional Network</span>
                                        <span class="text-lg font-bold text-white group-hover:text-neon-cyan transition-colors">linkedin.com/in/wahab-qadeer</span>
                                    </div>
                                </a>
                            </div>
                        </div>

                        <!-- Right: Terminal Form -->
                        <div class="bg-[#030908] rounded-[2rem] p-10 border border-void-700 shadow-inner relative overflow-hidden flex flex-col justify-center">
                            
                            <!-- Terminal Mac-style header -->
                            <div class="flex gap-3 mb-10 border-b border-void-800 pb-5">
                                <div class="w-4 h-4 rounded-full bg-red-500"></div>
                                <div class="w-4 h-4 rounded-full bg-yellow-500"></div>
                                <div class="w-4 h-4 rounded-full bg-neon-emerald"></div>
                                <span class="ml-4 text-sm font-code text-slate-500">bash: ./transmit_payload.sh</span>
                            </div>

                            <form id="contact-form" class="space-y-8">
                                <div class="group">
                                    <label class="block text-sm font-code font-bold text-neon-emerald mb-3 uppercase tracking-widest">>> String: Identity</label>
                                    <input type="text" required id="form-name" class="w-full bg-transparent border-b-2 border-void-700 text-white text-lg px-0 py-3 focus:outline-none focus:border-neon-emerald transition-colors font-code placeholder-slate-700" placeholder="Enter name">
                                </div>
                                <div class="group">
                                    <label class="block text-sm font-code font-bold text-neon-emerald mb-3 uppercase tracking-widest">>> Protocol: Address</label>
                                    <input type="email" required id="form-email" class="w-full bg-transparent border-b-2 border-void-700 text-white text-lg px-0 py-3 focus:outline-none focus:border-neon-emerald transition-colors font-code placeholder-slate-700" placeholder="Enter email">
                                </div>
                                <div class="group">
                                    <label class="block text-sm font-code font-bold text-neon-emerald mb-3 uppercase tracking-widest">>> Data: Payload</label>
                                    <textarea rows="4" required id="form-message" class="w-full bg-transparent border-b-2 border-void-700 text-white text-lg px-0 py-3 focus:outline-none focus:border-neon-emerald transition-colors font-code placeholder-slate-700 resize-none leading-relaxed" placeholder="Write logic here..."></textarea>
                                </div>
                                <button type="submit" class="w-full py-5 rounded-xl bg-neon-emerald text-void-950 font-black text-base uppercase tracking-widest hover:bg-neon-lime hover:shadow-[0_0_30px_rgba(163,230,53,0.5)] transition-all flex items-center justify-center gap-4 mt-4">
                                    Execute Transmission <i class="fa-solid fa-paper-plane text-xl"></i>
                                </button>
                            </form>
                        </div>
                        
                    </div>
                </div>
            </div>
        </section>
    </main>

    <!-- FOOTER -->
    <footer class="border-t border-void-800 py-16 px-4 bg-void-950 relative z-10 text-center">
        <div class="max-w-7xl mx-auto flex flex-col items-center gap-8">
            <div class="w-16 h-16 rounded-2xl bg-gradient-to-br from-neon-emerald to-neon-teal flex items-center justify-center text-void-950 font-black text-2xl shadow-[0_0_20px_rgba(16,185,129,0.2)]">WQ</div>
            <p class="text-slate-500 font-code text-base leading-loose">
                System architecture compiled by <span class="text-neon-emerald font-bold">Wahab Qadeer</span> © <span id="current-year"></span>. <br>
                <span class="text-sm opacity-75">BS Artificial Intelligence @ Barani Institute of Information Technology.</span>
            </p>
        </div>
    </footer>

    <!-- =========================================
         FULL SCREEN MODAL SYSTEM (DEEP DIVES)
         ========================================= -->
    
    <!-- Modal 1 -->
    <div id="modal-1" class="modal-backdrop" onclick="closeModal(event, 'modal-1')">
        <div class="modal-window p-10 md:p-16" onclick="event.stopPropagation()">
            <div class="flex justify-between items-start mb-10 border-b border-void-800 pb-8">
                <div>
                    <span class="text-neon-emerald font-code text-sm uppercase tracking-widest font-bold block mb-3">Enterprise Software / OOP</span>
                    <h2 class="text-4xl md:text-5xl font-extrabold text-white leading-tight">Smart Hospital <br>Management System</h2>
                </div>
                <button onclick="closeModal(null, 'modal-1')" class="w-12 h-12 rounded-full bg-void-800 text-slate-400 hover:text-white hover:bg-red-500/20 hover:border-red-500/50 border border-transparent transition-all flex items-center justify-center flex-shrink-0">
                    <i class="fa-solid fa-xmark text-2xl"></i>
                </button>
            </div>
            
            <div class="grid grid-cols-1 md:grid-cols-3 gap-12 text-slate-300">
                <div class="md:col-span-2 space-y-8">
                    <p class="text-lg leading-loose">A comprehensive desktop application designed to completely streamline healthcare administration. Built from the ground up using strict Object-Oriented Programming paradigms in Java to ensure maintainability and scalability.</p>
                    
                    <div>
                        <h4 class="text-2xl font-bold text-white mb-6 border-l-4 border-neon-emerald pl-4">Architectural Highlights</h4>
                        <ul class="space-y-4 text-base leading-relaxed">
                            <li class="flex items-start gap-4">
                                <i class="fa-solid fa-check text-neon-emerald mt-1"></i>
                                <span><strong>Encapsulation & Inheritance:</strong> Implemented clean class hierarchies for Patients, Doctors, and Administrators ensuring data security and modularity across the system.</span>
                            </li>
                            <li class="flex items-start gap-4">
                                <i class="fa-solid fa-check text-neon-emerald mt-1"></i>
                                <span><strong>Database Connectivity:</strong> Integrated seamlessly with a relational database via JDBC to handle persistent storage of appointments, medical records, and billing infrastructure.</span>
                            </li>
                            <li class="flex items-start gap-4">
                                <i class="fa-solid fa-check text-neon-emerald mt-1"></i>
                                <span><strong>Graphical Interface:</strong> Designed intuitive dashboards for administrative staff to quickly input and retrieve critical patient data in emergency situations.</span>
                            </li>
                        </ul>
                    </div>
                </div>
                
                <div class="bg-void-900 rounded-2xl p-8 border border-void-800 h-fit">
                    <h5 class="text-white font-bold mb-6 text-lg uppercase tracking-wider font-code">Tech Stack</h5>
                    <div class="flex flex-col gap-4">
                        <div class="flex items-center gap-4 bg-void-950 p-4 rounded-xl border border-neon-emerald/20">
                            <i class="fa-brands fa-java text-3xl text-neon-emerald"></i>
                            <div>
                                <span class="block text-white font-bold">Java</span>
                                <span class="text-xs text-slate-500">Core Logic & OOP</span>
                            </div>
                        </div>
                        <div class="flex items-center gap-4 bg-void-950 p-4 rounded-xl border border-neon-teal/20">
                            <i class="fa-solid fa-database text-3xl text-neon-teal"></i>
                            <div>
                                <span class="block text-white font-bold">JDBC / SQL</span>
                                <span class="text-xs text-slate-500">Database Layer</span>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <!-- Modals 2, 3, 4 follow identical spacious structure. 
         (Truncated slightly in HTML to save redundant lines, but functional using same classes) -->
    <div id="modal-2" class="modal-backdrop" onclick="closeModal(event, 'modal-2')"><div class="modal-window p-10 md:p-16" onclick="event.stopPropagation()"><div class="flex justify-between items-start mb-10 border-b border-void-800 pb-8"><div><span class="text-neon-teal font-code text-sm uppercase tracking-widest font-bold block mb-3">Database Engineering</span><h2 class="text-4xl md:text-5xl font-extrabold text-white leading-tight">Aero-Reserve DBMS</h2></div><button onclick="closeModal(null, 'modal-2')" class="w-12 h-12 rounded-full bg-void-800 text-slate-400 hover:text-white transition-all flex items-center justify-center"><i class="fa-solid fa-xmark text-2xl"></i></button></div><div class="text-slate-300 text-lg leading-loose"><p>A highly normalized relational database project engineered to simulate the backend of an international airline booking system. Includes complex Entity-Relationship modeling translated into strict physical database schemas with foreign key constraints, high-performance JOIN queries, and data normalization ensuring zero insertion anomalies.</p></div></div></div>
    
    <div id="modal-3" class="modal-backdrop" onclick="closeModal(event, 'modal-3')"><div class="modal-window p-10 md:p-16" onclick="event.stopPropagation()"><div class="flex justify-between items-start mb-10 border-b border-void-800 pb-8"><div><span class="text-neon-lime font-code text-sm uppercase tracking-widest font-bold block mb-3">Algorithmic Logic</span><h2 class="text-4xl md:text-5xl font-extrabold text-white leading-tight">Smart Irrigation</h2></div><button onclick="closeModal(null, 'modal-3')" class="w-12 h-12 rounded-full bg-void-800 text-slate-400 hover:text-white transition-all flex items-center justify-center"><i class="fa-solid fa-xmark text-2xl"></i></button></div><div class="text-slate-300 text-lg leading-loose"><p>A console-based logic simulation built purely in C++ without external libraries. It models intelligent water distribution based on variable environmental factors, utilizing complex conditional structures and looping logic to simulate resource conservation.</p></div></div></div>
    
    <div id="modal-4" class="modal-backdrop" onclick="closeModal(event, 'modal-4')"><div class="modal-window p-10 md:p-16" onclick="event.stopPropagation()"><div class="flex justify-between items-start mb-10 border-b border-void-800 pb-8"><div><span class="text-[#ef4444] font-code text-sm uppercase tracking-widest font-bold block mb-3">Embedded Systems</span><h2 class="text-4xl md:text-5xl font-extrabold text-white leading-tight">Auto Fire Brigade</h2></div><button onclick="closeModal(null, 'modal-4')" class="w-12 h-12 rounded-full bg-void-800 text-slate-400 hover:text-white transition-all flex items-center justify-center"><i class="fa-solid fa-xmark text-2xl"></i></button></div><div class="text-slate-300 text-lg leading-loose"><p>Hardware and software synergy. Designed and programmed an autonomous robot utilizing physical flame sensors and Arduino microcontrollers. The logic connects sensor inputs to motor driver outputs to detect and maneuver toward fires dynamically in real-time.</p></div></div></div>

    <!-- TOAST NOTIFICATION -->
    <div id="toast" class="fixed bottom-10 right-10 z-50 transform translate-y-40 opacity-0 transition-all duration-500 pointer-events-none glass-panel px-8 py-6 rounded-2xl border border-neon-emerald flex items-center gap-6 text-white font-code text-sm">
        <i class="fa-solid fa-circle-check text-neon-emerald text-4xl shadow-[0_0_15px_rgba(16,185,129,0.5)] rounded-full"></i>
        <div>
            <strong class="block text-neon-emerald uppercase text-base mb-1 tracking-widest">Success 200</strong> 
            <span class="text-slate-300">Payload transmitted successfully.</span>
        </div>
    </div>

    <!-- =========================================
         MASTER JAVASCRIPT ENGINE
         ========================================= -->
    <script>
        // 1. Basic Utilities
        document.getElementById('current-year').textContent = new Date().getFullYear();

        // 2. Interactive 3D Tilt Effect on Profile Picture
        const dpContainer = document.getElementById('dp-container');
        const dpCard = document.getElementById('dp-card');
        
        dpContainer.addEventListener('mousemove', (e) => {
            const rect = dpContainer.getBoundingClientRect();
            const x = e.clientX - rect.left;
            const y = e.clientY - rect.top;
            
            // Calculate rotation based on mouse position (center is 0,0)
            const centerX = rect.width / 2;
            const centerY = rect.height / 2;
            
            const rotateX = ((y - centerY) / centerY) * -15; // Max rotation 15deg
            const rotateY = ((x - centerX) / centerX) * 15;
            
            dpCard.style.transform = `perspective(1200px) rotateX(${rotateX}deg) rotateY(${rotateY}deg) scale3d(1.02, 1.02, 1.02)`;
        });

        dpContainer.addEventListener('mouseleave', () => {
            dpCard.style.transform = `perspective(1200px) rotateX(0deg) rotateY(0deg) scale3d(1, 1, 1)`;
            dpCard.style.transition = 'transform 0.5s ease-out';
        });
        
        dpContainer.addEventListener('mouseenter', () => {
            dpCard.style.transition = 'none'; // Remove transition for instant tracking
        });

        // 3. Scroll Reveal & Number Counter
        const revealElements = document.querySelectorAll('.reveal');
        const counters = document.querySelectorAll('.counter');
        let hasCounted = false;

        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.classList.add('active');
                    
                    // Counter Logic
                    if(entry.target.querySelector('.counter') && !hasCounted) {
                        hasCounted = true;
                        counters.forEach(counter => {
                            const target = +counter.getAttribute('data-target');
                            const duration = 2500; 
                            const increment = target / (duration / 16); 
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

        // 4. Typing Effect Logic
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
            let speed = isDel ? 40 : 80;
            if (!isDel && cIdx === current.length) { speed = 3000; isDel = true; } 
            else if (isDel && cIdx === 0) { isDel = false; pIdx = (pIdx + 1) % phrases.length; speed = 500; }
            setTimeout(typeWriter, speed);
        }
        setTimeout(typeWriter, 1500);

        // 5. Modal Engine
        function openModal(id) {
            document.body.style.overflow = 'hidden'; // Prevent background scrolling
            document.getElementById(id).classList.add('active');
        }
        function closeModal(e, id) {
            // Close only if clicking the background overlay or the close button
            if(e && e.target !== e.currentTarget) return;
            document.body.style.overflow = 'auto';
            document.getElementById(id).classList.remove('active');
        }

        // 6. Contact Form Transmission Logic
        document.getElementById('contact-form').addEventListener('submit', (e) => {
            e.preventDefault();
            const toast = document.getElementById('toast');
            toast.classList.remove('translate-y-40', 'opacity-0');
            toast.classList.add('translate-y-0', 'opacity-100');
            e.target.reset();
            setTimeout(() => {
                toast.classList.remove('translate-y-0', 'opacity-100');
                toast.classList.add('translate-y-40', 'opacity-0');
            }, 5000); // Show toast for 5 seconds
        });

        // 7. Advanced Heatmap Generation (Ultra Spacious layout)
        const heatmapContainer = document.getElementById('heatmap-container');
        const cellsNeeded = 52 * 7; // Full year representation
        for(let i=0; i<cellsNeeded; i++) {
            const cell = document.createElement('div');
            let level = 0;
            const rand = Math.random();
            // Assign probability distribution for realistic commit activity
            if(rand > 0.92) level = 4;
            else if(rand > 0.80) level = 3;
            else if(rand > 0.60) level = 2;
            else if(rand > 0.35) level = 1;
            
            cell.className = `heatmap-cell level-${level}`;
            heatmapContainer.appendChild(cell);
        }

        // 8. CHART.JS - ADVANCED ANALYTICS RENDERER
        document.addEventListener("DOMContentLoaded", function() {
            
            // Global Chart Defaults
            Chart.defaults.color = '#94a3b8';
            Chart.defaults.font.family = "'Fira Code', monospace";
            Chart.defaults.font.size = 12;
            
            // Reusable Tooltip config
            const tooltipConfig = {
                backgroundColor: 'rgba(1, 15, 12, 0.95)',
                titleColor: '#10b981',
                bodyColor: '#fff',
                borderColor: '#10b981',
                borderWidth: 1,
                padding: 16,
                cornerRadius: 8,
                titleFont: { size: 14, family: "'Inter', sans-serif", weight: 'bold' },
                bodyFont: { size: 13, family: "'Fira Code', monospace" }
            };

            // Chart 1: Doughnut (Skill Depth)
            new Chart(document.getElementById('chartDoughnut').getContext('2d'), {
                type: 'doughnut',
                data: {
                    labels: ['Logic & Algorithms', 'System Architecture', 'Database Design', 'Hardware IoT'],
                    datasets: [{
                        data: [35, 25, 25, 15],
                        backgroundColor: ['#10b981', '#14b8a6', '#06b6d4', '#a3e635'],
                        borderColor: '#021a15',
                        borderWidth: 6,
                        hoverOffset: 15
                    }]
                },
                options: {
                    responsive: true, maintainAspectRatio: false, cutout: '72%',
                    plugins: { 
                        legend: { position: 'bottom', labels: { padding: 30, usePointStyle: true, pointStyle: 'circle' } },
                        tooltip: tooltipConfig
                    },
                    animation: { animateScale: true, animateRotate: true, duration: 2500, easing: 'easeOutQuart' }
                }
            });

            // Chart 2: Radar (Core Competencies)
            new Chart(document.getElementById('chartRadar').getContext('2d'), {
                type: 'radar',
                data: {
                    labels: ['OOP Paradigms', 'SQL Scripting', 'C++ Logic', 'Data Structures', 'Embedded Systems', 'Frontend UI'],
                    datasets: [{
                        label: 'Proficiency Score',
                        data: [95, 90, 85, 88, 80, 75],
                        backgroundColor: 'rgba(20, 184, 166, 0.25)',
                        borderColor: '#14b8a6',
                        pointBackgroundColor: '#fff',
                        pointBorderColor: '#14b8a6',
                        pointHoverBackgroundColor: '#14b8a6',
                        pointHoverBorderColor: '#fff',
                        borderWidth: 3,
                        pointRadius: 5,
                        pointHoverRadius: 8
                    }]
                },
                options: {
                    responsive: true, maintainAspectRatio: false,
                    scales: {
                        r: {
                            angleLines: { color: 'rgba(255,255,255,0.1)', lineWidth: 1 },
                            grid: { color: 'rgba(255,255,255,0.1)', lineWidth: 1 },
                            pointLabels: { color: '#6ee7b7', font: {size: 11, family: "'Inter', sans-serif"} },
                            ticks: { display: false, max: 100, min: 0 }
                        }
                    },
                    plugins: { legend: { display: false }, tooltip: tooltipConfig },
                    animation: { duration: 3000, easing: 'easeOutElastic' }
                }
            });

            // Chart 3: Polar Area (Tech Stack Mastery)
            new Chart(document.getElementById('chartPolar').getContext('2d'), {
                type: 'polarArea',
                data: {
                    labels: ['Java Enterprise', 'SQL / RDBMS', 'HTML5 / CSS3', 'Kotlin / Mobile', 'Arduino / C'],
                    datasets: [{
                        data: [90, 85, 70, 50, 80],
                        backgroundColor: [
                            'rgba(16, 185, 129, 0.7)',
                            'rgba(6, 182, 212, 0.7)',
                            'rgba(59, 130, 246, 0.7)',
                            'rgba(139, 92, 246, 0.7)',
                            'rgba(239, 68, 68, 0.7)'
                        ],
                        borderColor: '#021a15',
                        borderWidth: 4
                    }]
                },
                options: {
                    responsive: true, maintainAspectRatio: false,
                    scales: { r: { grid: { color: 'rgba(255,255,255,0.1)' }, ticks: {display: false, backdropColor: 'transparent'} } },
                    plugins: { 
                        legend: { position: 'right', labels: { padding: 20, usePointStyle: true, font: {size: 12} } },
                        tooltip: tooltipConfig
                    },
                    animation: { duration: 2500 }
                }
            });

            // Chart 4: Mixed (Learning Velocity - Massive Chart)
            const ctxMixed = document.getElementById('chartMixed').getContext('2d');
            const gradBar = ctxMixed.createLinearGradient(0, 0, 0, 400);
            gradBar.addColorStop(0, 'rgba(6, 182, 212, 0.9)');
            gradBar.addColorStop(1, 'rgba(6, 182, 212, 0.05)');

            new Chart(ctxMixed, {
                type: 'bar',
                data: {
                    labels: ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 'Jul', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec'],
                    datasets: [
                        {
                            type: 'line', label: 'Expected Trajectory',
                            data: [10, 15, 25, 30, 45, 50, 65, 70, 75, 80, 90, 98],
                            borderColor: '#a3e635', borderWidth: 3, borderDash: [6, 6],
                            pointBackgroundColor: '#010f0c', pointBorderColor: '#a3e635', pointRadius: 6,
                            pointHoverRadius: 8, pointHoverBackgroundColor: '#a3e635',
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
                        x: { grid: { display: false }, ticks: { padding: 10, font: {size: 13} } },
                        y: { 
                            grid: { color: 'rgba(255,255,255,0.05)', drawBorder: false }, 
                            max: 100, 
                            ticks: { padding: 15, stepSize: 25, font: {size: 12} } 
                        }
                    },
                    plugins: { legend: { display: false }, tooltip: tooltipConfig },
                    animation: { duration: 3000, delay: (context) => context.dataIndex * 80 } // Staggered load
                }
            });
        });

        // 9. TRIPLE LAYER CANVAS SYSTEM (Neural + Matrix Rain + Interactivity)
        const canvasMatrix = document.getElementById('matrix-canvas');
        const ctxM = canvasMatrix.getContext('2d');
        const canvasNeural = document.getElementById('neural-canvas');
        const ctxN = canvasNeural.getContext('2d');
        const canvasInteract = document.getElementById('interaction-canvas');
        const ctxI = canvasInteract.getContext('2d');
        
        let width, height;
        let mouse = { x: null, y: null, radius: 200 }; // Larger interaction radius

        window.addEventListener('mousemove', (e) => {
            mouse.x = e.clientX;
            mouse.y = e.clientY;
        });

        function resize() {
            width = window.innerWidth;
            height = window.innerHeight;
            canvasMatrix.width = width; canvasMatrix.height = height;
            canvasNeural.width = width; canvasNeural.height = height;
            canvasInteract.width = width; canvasInteract.height = height;
        }
        window.addEventListener('resize', resize);
        resize();

        // --- Matrix Rain Logic (Background Layer) ---
        const chars = '01ABCDEFGHIJKLMNOPQRSTUVWXYZ'.split('');
        const fontSize = 14;
        const columns = Math.floor(window.innerWidth / fontSize) + 1; // Recalculated dynamically
        const drops = [];
        for(let x = 0; x < columns; x++) drops[x] = 1;

        function drawMatrix() {
            ctxM.fillStyle = 'rgba(0, 5, 4, 0.05)'; // Fades trailing chars
            ctxM.fillRect(0, 0, canvasMatrix.width, canvasMatrix.height);
            ctxM.fillStyle = '#10b981';
            ctxM.font = fontSize + 'px monospace';
            
            for(let i = 0; i < drops.length; i++) {
                const text = chars[Math.floor(Math.random() * chars.length)];
                ctxM.fillText(text, i * fontSize, drops[i] * fontSize);
                if(drops[i] * fontSize > canvasMatrix.height && Math.random() > 0.975) drops[i] = 0;
                drops[i]++;
            }
        }
        setInterval(drawMatrix, 50); // Run matrix separately

        // --- Neural Network Logic (Middle & Top Layers) ---
        class Node {
            constructor(isInteractive) {
                this.x = Math.random() * width;
                this.y = Math.random() * height;
                this.vx = (Math.random() - 0.5) * (isInteractive ? 1.2 : 0.4);
                this.vy = (Math.random() - 0.5) * (isInteractive ? 1.2 : 0.4);
                this.radius = Math.random() * 2.5 + 1;
                this.isInteractive = isInteractive;
                this.baseX = this.x;
                this.baseY = this.y;
            }
            update() {
                // Interactive nodes scatter from mouse
                if(this.isInteractive && mouse.x != null) {
                    let dx = mouse.x - this.x;
                    let dy = mouse.y - this.y;
                    let distance = Math.sqrt(dx*dx + dy*dy);
                    let force = (mouse.radius - distance) / mouse.radius;
                    
                    if(distance < mouse.radius) {
                        this.x -= dx * force * 0.05;
                        this.y -= dy * force * 0.05;
                    } else {
                        // Return to base path smoothly
                        if(this.x !== this.baseX) this.x -= (this.x - this.baseX) * 0.02;
                        if(this.y !== this.baseY) this.y -= (this.y - this.baseY) * 0.02;
                    }
                }
                
                this.x += this.vx; this.y += this.vy;
                this.baseX += this.vx; this.baseY += this.vy;

                // Bounce off edges
                if (this.x < 0 || this.x > width) { this.vx *= -1; this.baseX = this.x; }
                if (this.y < 0 || this.y > height) { this.vy *= -1; this.baseY = this.y; }
            }
            draw(ctx, color) {
                ctx.beginPath();
                ctx.arc(this.x, this.y, this.radius, 0, Math.PI * 2);
                ctx.fillStyle = color;
                ctx.fill();
            }
        }

        // Adjust node count based on screen size for performance
        const nodeDensity = width < 768 ? 8000 : 15000;
        const neuralNodes = Array.from({length: Math.floor((width*height)/nodeDensity)}, () => new Node(false));
        const interactNodes = Array.from({length: Math.floor((width*height)/nodeDensity)}, () => new Node(true));

        function animateNeuralCanvas() {
            ctxN.clearRect(0, 0, width, height);
            ctxI.clearRect(0, 0, width, height);

            // Draw Static Background Neural Layer
            neuralNodes.forEach((n, i) => {
                n.update(); 
                n.draw(ctxN, '#054236');
                for(let j=i+1; j<neuralNodes.length; j++) {
                    let dx = n.x - neuralNodes[j].x, dy = n.y - neuralNodes[j].y;
                    let dist = Math.sqrt(dx*dx + dy*dy);
                    if(dist < 160) { // Connection threshold
                        ctxN.beginPath(); ctxN.moveTo(n.x, n.y); ctxN.lineTo(neuralNodes[j].x, neuralNodes[j].y);
                        ctxN.strokeStyle = `rgba(5, 66, 54, ${1 - dist/160})`; 
                        ctxN.lineWidth = 0.8;
                        ctxN.stroke();
                    }
                }
            });

            // Draw Top Interactive Layer
            interactNodes.forEach((n, i) => {
                n.update(); 
                n.draw(ctxI, '#10b981');
                for(let j=i+1; j<interactNodes.length; j++) {
                    let dx = n.x - interactNodes[j].x, dy = n.y - interactNodes[j].y;
                    let dist = Math.sqrt(dx*dx + dy*dy);
                    if(dist < 130) {
                        ctxI.beginPath(); ctxI.moveTo(n.x, n.y); ctxI.lineTo(interactNodes[j].x, interactNodes[j].y);
                        ctxI.strokeStyle = `rgba(20, 184, 166, ${1 - dist/130})`; 
                        ctxI.lineWidth = 1;
                        ctxI.stroke();
                    }
                }
            });

            requestAnimationFrame(animateNeuralCanvas);
        }
        animateNeuralCanvas();
    </script>
</body>
</html>
