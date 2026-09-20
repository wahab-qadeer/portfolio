<!DOCTYPE html>
<html lang="en" class="scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Wahab Qadeer | Advanced AI & Software Portfolio</title>
    
    <!-- Google Fonts -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Fira+Code:wght@400;500;600;700&family=Inter:wght@300;400;500;600;700;800&family=Space+Grotesk:wght@400;500;600;700;800&display=swap" rel="stylesheet">
    
    <!-- FontAwesome Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    
    <!-- Chart.js for Analytics -->
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    
    <!-- Tailwind Config for Deep Customization -->
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
                        deep: {
                            950: '#000a08',
                            900: '#011612',
                            800: '#02241d',
                            700: '#033b30',
                            600: '#055c4b',
                            500: '#08856c'
                        },
                        neon: {
                            emerald: '#10b981',
                            lime: '#a3e635',
                            teal: '#14b8a6',
                            mint: '#6ee7b7',
                            cyan: '#06b6d4',
                            blue: '#3b82f6'
                        }
                    },
                    animation: {
                        'spin-slow': 'spin 12s linear infinite',
                        'float': 'float 6s ease-in-out infinite',
                        'float-delayed': 'float 6s ease-in-out 3s infinite',
                        'pulse-glow': 'pulseGlow 3s infinite alternate',
                        'bounce-subtle': 'bounceSubtle 3s infinite ease-in-out',
                        'morph': 'morph 8s ease-in-out infinite',
                        'slide-up': 'slideUp 0.8s ease-out forwards',
                        'glitch': 'glitch 1s linear infinite'
                    },
                    keyframes: {
                        float: {
                            '0%, 100%': { transform: 'translateY(0px)' },
                            '50%': { transform: 'translateY(-20px)' },
                        },
                        pulseGlow: {
                            '0%': { boxShadow: '0 0 15px rgba(16, 185, 129, 0.2)' },
                            '100%': { boxShadow: '0 0 40px rgba(163, 230, 53, 0.5)' },
                        },
                        bounceSubtle: {
                            '0%, 100%': { transform: 'translateY(0)' },
                            '50%': { transform: 'translateY(-8px)' },
                        },
                        morph: {
                            '0%': { borderRadius: '60% 40% 30% 70%/60% 30% 70% 40%' },
                            '50%': { borderRadius: '30% 60% 70% 40%/50% 60% 30% 60%' },
                            '100%': { borderRadius: '60% 40% 30% 70%/60% 30% 70% 40%' }
                        },
                        slideUp: {
                            '0%': { opacity: '0', transform: 'translateY(50px)' },
                            '100%': { opacity: '1', transform: 'translateY(0)' }
                        },
                        glitch: {
                            '2%, 64%': { transform: 'translate(2px,0) skew(0deg)' },
                            '4%, 60%': { transform: 'translate(-2px,0) skew(0deg)' },
                            '62%': { transform: 'translate(0,0) skew(5deg)' },
                        }
                    }
                }
            }
        }
    </script>

    <style>
        /* Base Styles & Typography */
        body {
            background-color: #000a08;
            color: #f8fafc;
            font-family: 'Inter', sans-serif;
            overflow-x: hidden;
            -webkit-font-smoothing: antialiased;
            -moz-osx-font-smoothing: grayscale;
        }

        h1, h2, h3, h4, h5, h6, .font-heading {
            font-family: 'Space Grotesk', sans-serif;
            letter-spacing: -0.02em;
        }

        /* Dual Canvas System */
        #neural-canvas {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -10;
            pointer-events: none;
            opacity: 0.4;
        }
        
        #interaction-canvas {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -9;
            pointer-events: none;
        }

        /* Abstract Morphing Blobs */
        .morph-blob {
            position: absolute;
            filter: blur(80px);
            z-index: -8;
            opacity: 0.15;
            pointer-events: none;
            animation: morph 15s ease-in-out infinite;
        }
        .blob-1 { top: 10%; left: 5%; width: 500px; height: 500px; background: linear-gradient(135deg, #10b981, #14b8a6); }
        .blob-2 { bottom: 20%; right: -5%; width: 600px; height: 600px; background: linear-gradient(135deg, #14b8a6, #3b82f6); animation-delay: -5s; }
        .blob-3 { top: 40%; left: 30%; width: 400px; height: 400px; background: linear-gradient(135deg, #a3e635, #10b981); animation-delay: -10s; }

        /* Premium Glassmorphism Cards */
        .glass-panel {
            background: rgba(3, 59, 48, 0.25);
            backdrop-filter: blur(20px);
            -webkit-backdrop-filter: blur(20px);
            border: 1px solid rgba(255, 255, 255, 0.08);
            box-shadow: 0 25px 50px -12px rgba(0, 0, 0, 0.7);
            transition: all 0.5s cubic-bezier(0.4, 0, 0.2, 1);
        }

        .glass-panel:hover {
            background: rgba(3, 59, 48, 0.4);
            border-color: rgba(16, 185, 129, 0.4);
            box-shadow: 0 30px 60px -15px rgba(16, 185, 129, 0.25);
            transform: translateY(-6px);
        }

        /* Advanced Square/Rounded DP (Not Circle) */
        .dp-showcase {
            position: relative;
            width: 320px;
            height: 400px;
            margin: 0 auto;
            border-radius: 2rem; /* Rounded Rectangle */
            background: linear-gradient(145deg, rgba(20, 184, 166, 0.1), rgba(3, 59, 48, 0.8));
            border: 2px solid rgba(16, 185, 129, 0.3);
            box-shadow: 
                0 0 30px rgba(16, 185, 129, 0.2),
                inset 0 0 20px rgba(0, 0, 0, 0.8);
            overflow: hidden;
            transition: transform 0.6s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            transform: perspective(1000px) rotateY(10deg) rotateX(5deg);
        }

        .dp-showcase:hover {
            transform: perspective(1000px) rotateY(0deg) rotateX(0deg) scale(1.02);
            border-color: rgba(163, 230, 53, 0.6);
            box-shadow: 
                0 0 50px rgba(16, 185, 129, 0.4),
                inset 0 0 20px rgba(0, 0, 0, 0.5);
        }

        .dp-showcase::before {
            content: '';
            position: absolute;
            top: 0; left: -100%;
            width: 50%; height: 100%;
            background: linear-gradient(to right, transparent, rgba(255,255,255,0.1), transparent);
            transform: skewX(-25deg);
            animation: shine 6s infinite;
            z-index: 10;
        }

        @keyframes shine {
            0% { left: -100%; }
            20% { left: 200%; }
            100% { left: 200%; }
        }

        .dp-img-wrapper {
            width: 100%;
            height: 100%;
            padding: 12px;
            box-sizing: border-box;
        }

        .dp-img-wrapper img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            border-radius: 1.5rem; /* Inner rounded rectangle */
            filter: contrast(1.05) brightness(0.95);
            transition: all 0.7s ease;
        }

        .dp-showcase:hover .dp-img-wrapper img {
            filter: contrast(1.1) brightness(1.05);
            transform: scale(1.05);
        }

        /* 3D Floating Objects */
        .float-obj {
            position: absolute;
            border-radius: 12px;
            background: rgba(20, 184, 166, 0.1);
            backdrop-filter: blur(10px);
            border: 1px solid rgba(20, 184, 166, 0.3);
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.5rem;
            color: #10b981;
            box-shadow: 0 10px 30px rgba(0,0,0,0.5);
        }

        /* Gradient Typography */
        .text-gradient-emerald {
            background: linear-gradient(to right, #10b981, #a3e635);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }
        
        .text-gradient-teal {
            background: linear-gradient(to right, #14b8a6, #6ee7b7);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        /* Typing Caret */
        .typing-cursor::after {
            content: '_';
            animation: blink 1s step-end infinite;
            color: #10b981;
            margin-left: 4px;
        }

        @keyframes blink { 0%, 100% { opacity: 1; } 50% { opacity: 0; } }

        /* Scroll Reveal Utility */
        .reveal {
            opacity: 0;
            transform: translateY(60px);
            transition: all 1s cubic-bezier(0.16, 1, 0.3, 1);
        }
        .reveal.active {
            opacity: 1;
            transform: translateY(0);
        }

        /* Custom GitHub Heatmap Styles */
        .heatmap-grid {
            display: grid;
            grid-template-columns: repeat(52, 1fr);
            gap: 4px;
            width: 100%;
            overflow-x: auto;
            padding-bottom: 10px;
        }
        
        .heatmap-cell {
            width: 12px;
            height: 12px;
            border-radius: 3px;
            background-color: #033b30;
            transition: all 0.2s ease;
        }
        
        .heatmap-cell:hover {
            transform: scale(1.5);
            box-shadow: 0 0 10px #10b981;
            z-index: 10;
        }
        
        .level-0 { background-color: #02241d; }
        .level-1 { background-color: #055c4b; }
        .level-2 { background-color: #08856c; }
        .level-3 { background-color: #10b981; }
        .level-4 { background-color: #a3e635; }

        /* Modals */
        .modal-overlay {
            position: fixed;
            top: 0; left: 0; right: 0; bottom: 0;
            background: rgba(0, 10, 8, 0.85);
            backdrop-filter: blur(15px);
            z-index: 100;
            display: flex;
            align-items: center;
            justify-content: center;
            opacity: 0;
            pointer-events: none;
            transition: all 0.4s ease;
        }
        
        .modal-overlay.active {
            opacity: 1;
            pointer-events: all;
        }

        .modal-content {
            background: #011612;
            border: 1px solid rgba(20, 184, 166, 0.3);
            border-radius: 1.5rem;
            width: 90%;
            max-width: 800px;
            max-height: 90vh;
            overflow-y: auto;
            transform: scale(0.9) translateY(20px);
            transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            box-shadow: 0 25px 50px rgba(0,0,0,0.8), 0 0 40px rgba(16, 185, 129, 0.1);
        }

        .modal-overlay.active .modal-content {
            transform: scale(1) translateY(0);
        }

        /* Scrollbars */
        ::-webkit-scrollbar { width: 10px; height: 10px; }
        ::-webkit-scrollbar-track { background: #000a08; }
        ::-webkit-scrollbar-thumb { background: #055c4b; border-radius: 5px; border: 2px solid #000a08; }
        ::-webkit-scrollbar-thumb:hover { background: #10b981; }
    </style>
</head>
<body class="selection:bg-neon-emerald selection:text-deep-950">

    <!-- Dual Animated Canvas System -->
    <canvas id="neural-canvas"></canvas>
    <canvas id="interaction-canvas"></canvas>
    
    <!-- Morphing Ambient Background Blobs -->
    <div class="morph-blob blob-1"></div>
    <div class="morph-blob blob-2"></div>
    <div class="morph-blob blob-3"></div>

    <!-- Navigation Header -->
    <header class="fixed top-0 left-0 w-full z-50 transition-all duration-300 px-4 sm:px-8 py-5" id="main-header">
        <div class="max-w-7xl mx-auto">
            <div class="glass-panel rounded-2xl px-8 py-4 flex items-center justify-between">
                <!-- Brand Logo -->
                <a href="#" class="font-heading font-bold text-2xl tracking-wide text-white flex items-center gap-3 group">
                    <div class="w-10 h-10 rounded-xl bg-gradient-to-br from-neon-emerald to-neon-teal flex items-center justify-center text-deep-950 font-black text-lg shadow-[0_0_15px_rgba(16,185,129,0.5)] transform group-hover:rotate-12 transition-all">
                        WQ
                    </div>
                    <span class="group-hover:text-neon-emerald transition-colors">Wahab<span class="text-neon-emerald">.ai</span></span>
                </a>

                <!-- Desktop Navigation Links -->
                <nav class="hidden md:flex items-center space-x-10 text-sm font-semibold text-slate-300">
                    <a href="#about" class="hover:text-neon-emerald hover:-translate-y-1 transition-all duration-300">Architecture</a>
                    <a href="#dashboard" class="hover:text-neon-emerald hover:-translate-y-1 transition-all duration-300">Analytics Dashboard</a>
                    <a href="#projects" class="hover:text-neon-emerald hover:-translate-y-1 transition-all duration-300">Systems Built</a>
                    <a href="#timeline" class="hover:text-neon-emerald hover:-translate-y-1 transition-all duration-300">Timeline</a>
                </nav>

                <!-- Action Button -->
                <a href="#connect" class="hidden sm:flex px-6 py-2.5 rounded-xl bg-neon-emerald text-deep-950 font-bold text-sm uppercase tracking-widest hover:bg-neon-lime transition-all shadow-[0_0_20px_rgba(16,185,129,0.4)] hover:shadow-[0_0_30px_rgba(163,230,53,0.6)] items-center gap-2 transform hover:scale-105">
                    <i class="fa-solid fa-terminal"></i> Initialize
                </a>
            </div>
        </div>
    </header>

    <main class="relative pt-32 pb-20">

        <!-- HERO SECTION (Non-Circular DP, Enhanced Layout) -->
        <section class="min-h-[85vh] flex items-center justify-center px-4 sm:px-6 lg:px-8 py-12 relative overflow-hidden">
            <div class="max-w-7xl mx-auto w-full">
                
                <div class="flex flex-col lg:flex-row items-center gap-16 lg:gap-24">
                    
                    <!-- LEFT: Advanced Shape Profile Picture -->
                    <div class="w-full lg:w-5/12 flex justify-center order-2 lg:order-1 relative reveal">
                        <!-- Floating Tech Nodes -->
                        <div class="float-obj w-14 h-14 -top-6 -left-6 animate-float" style="animation-delay: 0s;">
                            <i class="fa-brands fa-java text-neon-teal"></i>
                        </div>
                        <div class="float-obj w-12 h-12 top-1/2 -right-8 animate-float" style="animation-delay: 1.5s;">
                            <i class="fa-solid fa-database text-neon-emerald"></i>
                        </div>
                        <div class="float-obj w-16 h-16 -bottom-8 left-10 animate-float" style="animation-delay: 3s;">
                            <i class="fa-solid fa-microchip text-neon-lime"></i>
                        </div>

                        <!-- Main DP Showcase -->
                        <div class="dp-showcase z-10">
                            <div class="dp-img-wrapper">
                                <!-- Replace with actual image -->
                                <img 
                                    src="WhatsApp Image 2026-08-13 at 1.09.24 PM_2.jpeg" 
                                    alt="Wahab Qadeer Portfolio Identity" 
                                    onerror="this.src='https://placehold.co/400x500/032e25/10b981?text=WQ'"
                                >
                            </div>
                        </div>
                        
                        <!-- Glow Floor -->
                        <div class="absolute -bottom-10 left-1/2 transform -translate-x-1/2 w-3/4 h-8 bg-neon-emerald/30 blur-2xl rounded-full"></div>
                    </div>

                    <!-- RIGHT: Dynamic Typography & Info -->
                    <div class="w-full lg:w-7/12 space-y-8 text-center lg:text-left order-1 lg:order-2 reveal">
                        
                        <!-- Status Badge -->
                        <div class="inline-flex items-center gap-3 px-5 py-2.5 rounded-full glass-panel border-neon-emerald/40 text-neon-emerald text-sm font-code uppercase tracking-widest shadow-[0_0_15px_rgba(16,185,129,0.1)]">
                            <span class="relative flex h-3 w-3">
                              <span class="animate-ping absolute inline-flex h-full w-full rounded-full bg-neon-lime opacity-75"></span>
                              <span class="relative inline-flex rounded-full h-3 w-3 bg-neon-emerald"></span>
                            </span>
                            System Online | BS(AI) BIIT
                        </div>

                        <!-- Hero Headline -->
                        <div class="space-y-4">
                            <h1 class="text-5xl sm:text-6xl lg:text-7xl font-extrabold tracking-tighter text-white leading-[1.1]">
                                Architecting <br>
                                <span class="text-gradient-emerald">Intelligent</span> Systems.
                            </h1>
                            <div class="text-2xl sm:text-3xl font-medium text-slate-300 h-12 flex items-center justify-center lg:justify-start">
                                <span>I build </span>
                                <span id="typing-text" class="typing-cursor font-code text-neon-teal font-bold ml-3"></span>
                            </div>
                        </div>

                        <!-- Hero Bio -->
                        <p class="text-slate-400 text-lg sm:text-xl leading-relaxed max-w-2xl mx-auto lg:mx-0 font-light">
                            Computer Science undergraduate specializing in Artificial Intelligence. Bridging the gap between raw data, complex algorithmic logic, and robust object-oriented software architectures.
                        </p>

                        <!-- Action Metrics & Buttons -->
                        <div class="pt-6 flex flex-col sm:flex-row items-center gap-6 justify-center lg:justify-start">
                            <a href="#dashboard" class="px-8 py-4 rounded-xl bg-gradient-to-r from-neon-emerald to-neon-teal text-deep-950 font-bold text-base tracking-wide hover:shadow-[0_0_30px_rgba(16,185,129,0.5)] transition-all flex items-center gap-3 transform hover:-translate-y-1">
                                <i class="fa-solid fa-chart-network"></i> Launch Dashboard
                            </a>
                            
                            <div class="flex gap-6 items-center">
                                <div class="text-left">
                                    <span class="block text-3xl font-black text-white counter" data-target="15">0</span>
                                    <span class="text-xs text-neon-teal uppercase tracking-widest font-bold">Projects</span>
                                </div>
                                <div class="w-px h-10 bg-slate-700"></div>
                                <div class="text-left">
                                    <span class="block text-3xl font-black text-white counter" data-target="98">0</span>
                                    <span class="text-xs text-neon-lime uppercase tracking-widest font-bold">Efficiency %</span>
                                </div>
                            </div>
                        </div>

                    </div>
                </div>
            </div>
        </section>

        <!-- DASHBOARD SECTION (Massively Expanded Analytics) -->
        <section id="dashboard" class="py-24 px-4 sm:px-6 lg:px-8 relative z-10 border-t border-deep-800">
            <div class="max-w-[1400px] mx-auto">
                
                <!-- Section Header -->
                <div class="text-center mb-16 reveal">
                    <span class="text-sm font-code text-neon-teal uppercase tracking-widest block mb-3 font-bold flex items-center justify-center gap-2">
                        <i class="fa-solid fa-radar text-neon-lime animate-spin-slow"></i> Telemetry & Metrics
                    </span>
                    <h2 class="text-4xl sm:text-5xl font-extrabold text-white">Live <span class="text-gradient-emerald">Growth Dashboard</span></h2>
                    <p class="text-slate-400 mt-4 max-w-2xl mx-auto text-lg leading-relaxed">Real-time visualization of skill acquisition, technological proficiencies, and architectural competencies.</p>
                </div>

                <!-- Bento Grid Layout for Dashboard -->
                <div class="grid grid-cols-1 md:grid-cols-2 xl:grid-cols-3 gap-6 lg:gap-8 reveal">
                    
                    <!-- Widget 1: Skill Distribution (Doughnut) -->
                    <div class="glass-panel p-8 rounded-3xl flex flex-col h-full relative overflow-hidden">
                        <div class="absolute -right-10 -top-10 w-40 h-40 bg-neon-emerald/20 blur-3xl rounded-full"></div>
                        <h3 class="text-lg font-bold text-white mb-2 flex items-center gap-3">
                            <i class="fa-solid fa-chart-pie text-neon-emerald"></i> Resource Allocation
                        </h3>
                        <p class="text-xs text-slate-400 mb-6 font-code uppercase tracking-wider">Depth Distribution %</p>
                        <div class="relative flex-grow min-h-[250px] w-full flex items-center justify-center">
                            <canvas id="chartDoughnut"></canvas>
                        </div>
                    </div>

                    <!-- Widget 2: Core Competencies (Radar) -->
                    <div class="glass-panel p-8 rounded-3xl flex flex-col h-full relative overflow-hidden">
                        <div class="absolute -left-10 -bottom-10 w-40 h-40 bg-neon-teal/20 blur-3xl rounded-full"></div>
                        <h3 class="text-lg font-bold text-white mb-2 flex items-center gap-3">
                            <i class="fa-solid fa-bullseye text-neon-teal"></i> Vector Analysis
                        </h3>
                        <p class="text-xs text-slate-400 mb-6 font-code uppercase tracking-wider">Competency Radar Matrix</p>
                        <div class="relative flex-grow min-h-[250px] w-full flex items-center justify-center">
                            <canvas id="chartRadar"></canvas>
                        </div>
                    </div>

                    <!-- Widget 3: Tech Stack Mastery (Polar Area) -->
                    <div class="glass-panel p-8 rounded-3xl flex flex-col h-full xl:col-span-1 md:col-span-2 relative overflow-hidden">
                        <div class="absolute right-1/2 top-1/2 w-40 h-40 bg-neon-lime/10 blur-3xl rounded-full transform translate-x-1/2 -translate-y-1/2"></div>
                        <h3 class="text-lg font-bold text-white mb-2 flex items-center gap-3">
                            <i class="fa-solid fa-layer-group text-neon-lime"></i> Tech Stack Mastery
                        </h3>
                        <p class="text-xs text-slate-400 mb-6 font-code uppercase tracking-wider">Syntax & Frameworks</p>
                        <div class="relative flex-grow min-h-[250px] w-full flex items-center justify-center">
                            <canvas id="chartPolar"></canvas>
                        </div>
                    </div>

                    <!-- Widget 4: Learning Velocity (Wide Bar/Line Mixed Chart) -->
                    <div class="glass-panel p-8 rounded-3xl xl:col-span-2 md:col-span-2 flex flex-col relative">
                        <h3 class="text-lg font-bold text-white mb-2 flex items-center gap-3">
                            <i class="fa-solid fa-chart-line text-neon-cyan"></i> Learning Velocity
                        </h3>
                        <p class="text-xs text-slate-400 mb-6 font-code uppercase tracking-wider">12-Month Progression Trend</p>
                        <div class="relative h-[300px] w-full">
                            <canvas id="chartMixed"></canvas>
                        </div>
                    </div>

                    <!-- Widget 5: GitHub Style Activity Heatmap -->
                    <div class="glass-panel p-8 rounded-3xl xl:col-span-1 md:col-span-2 flex flex-col">
                        <h3 class="text-lg font-bold text-white mb-2 flex items-center gap-3">
                            <i class="fa-solid fa-calendar-days text-neon-emerald"></i> Activity Matrix
                        </h3>
                        <p class="text-xs text-slate-400 mb-6 font-code uppercase tracking-wider">Commit & Compilation Density</p>
                        
                        <div class="bg-deep-900/50 p-4 rounded-xl border border-deep-700 overflow-hidden">
                            <!-- Heatmap dynamically generated via JS -->
                            <div class="heatmap-grid" id="heatmap-container"></div>
                            
                            <div class="flex justify-between items-center mt-4 text-[10px] text-slate-500 font-code font-bold uppercase tracking-widest">
                                <span>Less</span>
                                <div class="flex gap-1">
                                    <div class="w-3 h-3 rounded-sm bg-[#02241d]"></div>
                                    <div class="w-3 h-3 rounded-sm bg-[#055c4b]"></div>
                                    <div class="w-3 h-3 rounded-sm bg-[#08856c]"></div>
                                    <div class="w-3 h-3 rounded-sm bg-[#10b981]"></div>
                                    <div class="w-3 h-3 rounded-sm bg-[#a3e635]"></div>
                                </div>
                                <span>More</span>
                            </div>
                        </div>
                    </div>

                </div>
            </div>
        </section>

        <!-- PROJECTS / SYSTEMS BUILT SECTION -->
        <section id="projects" class="py-24 px-4 sm:px-6 lg:px-8 bg-deep-900/40 border-y border-deep-800 relative z-10">
            <div class="max-w-7xl mx-auto">
                
                <div class="flex flex-col md:flex-row justify-between items-end mb-16 reveal gap-6">
                    <div>
                        <span class="text-sm font-code text-neon-lime uppercase tracking-widest block mb-3 font-bold">Execution</span>
                        <h2 class="text-4xl sm:text-5xl font-extrabold text-white">Engineered <span class="text-gradient-teal">Systems</span></h2>
                    </div>
                    <p class="text-slate-400 max-w-md text-base leading-relaxed text-left md:text-right">
                        Click on any architecture node to view deep diagnostic data, source logic, and implementation details.
                    </p>
                </div>

                <!-- Projects Grid -->
                <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
                    
                    <!-- Project 1 -->
                    <div class="glass-panel p-8 rounded-3xl group cursor-pointer reveal project-card" onclick="openModal('modal-1')">
                        <div class="w-16 h-16 rounded-2xl bg-deep-800 border border-neon-emerald/30 flex items-center justify-center text-neon-emerald text-3xl mb-6 group-hover:scale-110 group-hover:bg-neon-emerald/10 transition-all duration-300 shadow-[0_0_15px_rgba(16,185,129,0.1)] group-hover:shadow-[0_0_25px_rgba(16,185,129,0.3)]">
                            <i class="fa-solid fa-hospital-user"></i>
                        </div>
                        <h3 class="text-2xl font-bold text-white mb-3 tracking-tight group-hover:text-neon-emerald transition-colors">Smart Hospital Core</h3>
                        <p class="text-slate-400 text-sm leading-relaxed mb-8 h-20 overflow-hidden">
                            Enterprise-level desktop application enforcing strict Object-Oriented paradigms (Java) connected to a relational database to manage complex medical logistics.
                        </p>
                        <div class="flex items-center justify-between border-t border-white/10 pt-5">
                            <div class="flex gap-2">
                                <span class="w-2 h-2 rounded-full bg-neon-emerald"></span>
                                <span class="w-2 h-2 rounded-full bg-neon-teal"></span>
                                <span class="w-2 h-2 rounded-full bg-neon-lime"></span>
                            </div>
                            <span class="text-xs font-code text-neon-teal font-bold tracking-widest uppercase flex items-center gap-2 group-hover:translate-x-2 transition-transform">
                                Analyze <i class="fa-solid fa-arrow-right"></i>
                            </span>
                        </div>
                    </div>

                    <!-- Project 2 -->
                    <div class="glass-panel p-8 rounded-3xl group cursor-pointer reveal project-card" onclick="openModal('modal-2')">
                        <div class="w-16 h-16 rounded-2xl bg-deep-800 border border-neon-teal/30 flex items-center justify-center text-neon-teal text-3xl mb-6 group-hover:scale-110 group-hover:bg-neon-teal/10 transition-all duration-300 shadow-[0_0_15px_rgba(20,184,166,0.1)] group-hover:shadow-[0_0_25px_rgba(20,184,166,0.3)]">
                            <i class="fa-solid fa-plane-up"></i>
                        </div>
                        <h3 class="text-2xl font-bold text-white mb-3 tracking-tight group-hover:text-neon-teal transition-colors">Aero-Reserve DB</h3>
                        <p class="text-slate-400 text-sm leading-relaxed mb-8 h-20 overflow-hidden">
                            Complex relational schema design demonstrating normalized tables, high-performance joins, indexing, and transactional integrity for flight systems.
                        </p>
                        <div class="flex items-center justify-between border-t border-white/10 pt-5">
                            <div class="flex gap-2">
                                <span class="w-2 h-2 rounded-full bg-neon-teal"></span>
                                <span class="w-2 h-2 rounded-full bg-neon-cyan"></span>
                            </div>
                            <span class="text-xs font-code text-neon-teal font-bold tracking-widest uppercase flex items-center gap-2 group-hover:translate-x-2 transition-transform">
                                Analyze <i class="fa-solid fa-arrow-right"></i>
                            </span>
                        </div>
                    </div>

                    <!-- Project 3 -->
                    <div class="glass-panel p-8 rounded-3xl group cursor-pointer reveal project-card" onclick="openModal('modal-3')">
                        <div class="w-16 h-16 rounded-2xl bg-deep-800 border border-neon-lime/30 flex items-center justify-center text-neon-lime text-3xl mb-6 group-hover:scale-110 group-hover:bg-neon-lime/10 transition-all duration-300 shadow-[0_0_15px_rgba(163,230,53,0.1)] group-hover:shadow-[0_0_25px_rgba(163,230,53,0.3)]">
                            <i class="fa-solid fa-droplet"></i>
                        </div>
                        <h3 class="text-2xl font-bold text-white mb-3 tracking-tight group-hover:text-neon-lime transition-colors">Automated Irrigation</h3>
                        <p class="text-slate-400 text-sm leading-relaxed mb-8 h-20 overflow-hidden">
                            C++ logical simulation managing resource constraints, automated sensor triggering, and algorithmic water conservation schedules.
                        </p>
                        <div class="flex items-center justify-between border-t border-white/10 pt-5">
                            <div class="flex gap-2">
                                <span class="w-2 h-2 rounded-full bg-neon-lime"></span>
                                <span class="w-2 h-2 rounded-full bg-neon-emerald"></span>
                            </div>
                            <span class="text-xs font-code text-neon-teal font-bold tracking-widest uppercase flex items-center gap-2 group-hover:translate-x-2 transition-transform">
                                Analyze <i class="fa-solid fa-arrow-right"></i>
                            </span>
                        </div>
                    </div>

                    <!-- Project 4 (Hardware) -->
                    <div class="glass-panel p-8 rounded-3xl group cursor-pointer reveal project-card" onclick="openModal('modal-4')">
                        <div class="w-16 h-16 rounded-2xl bg-deep-800 border border-[#ef4444]/30 flex items-center justify-center text-[#ef4444] text-3xl mb-6 group-hover:scale-110 group-hover:bg-[#ef4444]/10 transition-all duration-300 shadow-[0_0_15px_rgba(239,68,68,0.1)] group-hover:shadow-[0_0_25px_rgba(239,68,68,0.3)]">
                            <i class="fa-solid fa-fire-flame-curved"></i>
                        </div>
                        <h3 class="text-2xl font-bold text-white mb-3 tracking-tight group-hover:text-[#ef4444] transition-colors">Hardware: Fire Brigade</h3>
                        <p class="text-slate-400 text-sm leading-relaxed mb-8 h-20 overflow-hidden">
                            Embedded systems engineering combining Arduino microcontrollers, flame detection logic, motor drivers, and real-time physical actuation.
                        </p>
                        <div class="flex items-center justify-between border-t border-white/10 pt-5">
                            <div class="flex gap-2">
                                <span class="w-2 h-2 rounded-full bg-[#ef4444]"></span>
                                <span class="w-2 h-2 rounded-full bg-neon-emerald"></span>
                            </div>
                            <span class="text-xs font-code text-neon-teal font-bold tracking-widest uppercase flex items-center gap-2 group-hover:translate-x-2 transition-transform">
                                Analyze <i class="fa-solid fa-arrow-right"></i>
                            </span>
                        </div>
                    </div>

                </div>
            </div>
        </section>

        <!-- TIMELINE SECTION (Education & Focus) -->
        <section id="timeline" class="py-24 px-4 sm:px-6 lg:px-8 relative z-10">
            <div class="max-w-4xl mx-auto">
                <div class="text-center mb-16 reveal">
                    <h2 class="text-4xl sm:text-5xl font-extrabold text-white">Academic <span class="text-gradient-emerald">Trajectory</span></h2>
                </div>

                <div class="relative border-l-2 border-neon-emerald/30 pl-8 ml-4 md:ml-0 space-y-12">
                    
                    <!-- Timeline Node 1 -->
                    <div class="relative reveal">
                        <div class="absolute -left-[41px] top-1 w-6 h-6 rounded-full bg-deep-900 border-4 border-neon-emerald shadow-[0_0_15px_#10b981]"></div>
                        <div class="glass-panel p-8 rounded-2xl ml-4 relative overflow-hidden">
                            <div class="absolute right-0 top-0 w-32 h-full bg-gradient-to-l from-neon-emerald/10 to-transparent pointer-events-none"></div>
                            <span class="text-xs font-code font-bold text-neon-emerald tracking-widest uppercase block mb-2">Current Epoch</span>
                            <h3 class="text-2xl font-bold text-white mb-1">BS Artificial Intelligence</h3>
                            <h4 class="text-lg text-slate-300 font-medium mb-4">Barani Institute of Information Technology (BIIT)</h4>
                            <p class="text-slate-400 text-sm leading-relaxed">
                                Immersed in higher-order mathematics (Multivariable Calculus, Linear Algebra), Data Structures, and advanced object-oriented paradigms. Building a theoretical foundation for complex machine learning models.
                            </p>
                        </div>
                    </div>

                    <!-- Timeline Node 2 -->
                    <div class="relative reveal">
                        <div class="absolute -left-[41px] top-1 w-6 h-6 rounded-full bg-deep-900 border-4 border-neon-teal shadow-[0_0_15px_#14b8a6]"></div>
                        <div class="glass-panel p-8 rounded-2xl ml-4 relative overflow-hidden">
                            <div class="absolute right-0 top-0 w-32 h-full bg-gradient-to-l from-neon-teal/10 to-transparent pointer-events-none"></div>
                            <span class="text-xs font-code font-bold text-neon-teal tracking-widest uppercase block mb-2">Parallel Processing</span>
                            <h3 class="text-2xl font-bold text-white mb-1">Independent Research & Development</h3>
                            <h4 class="text-lg text-slate-300 font-medium mb-4">Software Architecture & Hardware Integration</h4>
                            <p class="text-slate-400 text-sm leading-relaxed">
                                Proactively expanding beyond curriculum. Mastering backend engineering concepts, relational database normalization, and designing logic gates and microcontrollers for real-world automated systems.
                            </p>
                        </div>
                    </div>

                </div>
            </div>
        </section>

        <!-- CONNECT / TERMINAL SECTION -->
        <section id="connect" class="py-24 px-4 sm:px-6 lg:px-8 bg-deep-900/60 border-t border-deep-800 relative z-10">
            <div class="max-w-5xl mx-auto">
                <div class="glass-panel rounded-[2.5rem] p-8 md:p-14 border border-neon-emerald/30 shadow-[0_30px_60px_-15px_rgba(0,0,0,0.8),0_0_40px_rgba(16,185,129,0.1)] reveal">
                    
                    <div class="grid grid-cols-1 lg:grid-cols-2 gap-16">
                        
                        <!-- Left: Info -->
                        <div class="space-y-8">
                            <div>
                                <span class="text-sm font-code text-neon-emerald uppercase tracking-widest block mb-3 font-bold">Establishing Handshake</span>
                                <h2 class="text-4xl font-extrabold text-white mb-6">Initialize <span class="text-gradient-emerald">Connection</span></h2>
                                <p class="text-slate-400 text-lg leading-relaxed">
                                    Ready to compile ideas into reality. Open to collaboration on AI research, software engineering projects, or technical discussions.
                                </p>
                            </div>

                            <div class="space-y-5 pt-4">
                                <a href="mailto:realwahabqadeer@gmail.com" class="flex items-center gap-5 p-5 rounded-2xl bg-deep-800/50 border border-deep-700 hover:border-neon-emerald/50 group transition-all duration-300 transform hover:translate-x-2">
                                    <div class="w-14 h-14 rounded-xl bg-deep-900 flex items-center justify-center text-neon-emerald text-2xl group-hover:bg-neon-emerald group-hover:text-deep-900 transition-colors shadow-inner">
                                        <i class="fa-solid fa-envelope"></i>
                                    </div>
                                    <div>
                                        <span class="text-xs font-code text-slate-500 uppercase tracking-widest block mb-1">Direct Protocol</span>
                                        <span class="text-base font-bold text-white group-hover:text-neon-emerald transition-colors">realwahabqadeer@gmail.com</span>
                                    </div>
                                </a>

                                <a href="https://www.linkedin.com/in/wahab-qadeer/" target="_blank" class="flex items-center gap-5 p-5 rounded-2xl bg-deep-800/50 border border-deep-700 hover:border-neon-blue/50 group transition-all duration-300 transform hover:translate-x-2">
                                    <div class="w-14 h-14 rounded-xl bg-deep-900 flex items-center justify-center text-neon-blue text-2xl group-hover:bg-neon-blue group-hover:text-deep-900 transition-colors shadow-inner">
                                        <i class="fa-brands fa-linkedin-in"></i>
                                    </div>
                                    <div>
                                        <span class="text-xs font-code text-slate-500 uppercase tracking-widest block mb-1">Professional Network</span>
                                        <span class="text-base font-bold text-white group-hover:text-neon-blue transition-colors">linkedin.com/in/wahab-qadeer</span>
                                    </div>
                                </a>

                                <a href="https://github.com/wahab-qadeer" target="_blank" class="flex items-center gap-5 p-5 rounded-2xl bg-deep-800/50 border border-deep-700 hover:border-white/50 group transition-all duration-300 transform hover:translate-x-2">
                                    <div class="w-14 h-14 rounded-xl bg-deep-900 flex items-center justify-center text-white text-2xl group-hover:bg-white group-hover:text-deep-900 transition-colors shadow-inner">
                                        <i class="fa-brands fa-github"></i>
                                    </div>
                                    <div>
                                        <span class="text-xs font-code text-slate-500 uppercase tracking-widest block mb-1">Source Repositories</span>
                                        <span class="text-base font-bold text-white group-hover:text-white transition-colors">github.com/wahab-qadeer</span>
                                    </div>
                                </a>
                            </div>
                        </div>

                        <!-- Right: Form -->
                        <div class="bg-deep-950/80 rounded-3xl p-8 border border-deep-800 shadow-inner relative overflow-hidden">
                            <!-- Terminal styling header -->
                            <div class="flex gap-2 mb-6 border-b border-deep-800 pb-4">
                                <div class="w-3 h-3 rounded-full bg-red-500"></div>
                                <div class="w-3 h-3 rounded-full bg-yellow-500"></div>
                                <div class="w-3 h-3 rounded-full bg-neon-emerald"></div>
                                <span class="ml-4 text-xs font-code text-slate-500">bash: ./send_message.sh</span>
                            </div>

                            <form id="contact-form" class="space-y-6">
                                <div class="group">
                                    <label class="block text-xs font-code font-bold text-neon-emerald mb-2 uppercase tracking-widest">>> Name_String</label>
                                    <input type="text" required id="form-name" class="w-full bg-transparent border-b-2 border-deep-700 text-white px-0 py-2 focus:outline-none focus:border-neon-emerald transition-colors font-code placeholder-slate-700" placeholder="Enter identifier">
                                </div>
                                <div class="group">
                                    <label class="block text-xs font-code font-bold text-neon-emerald mb-2 uppercase tracking-widest">>> Address_Protocol</label>
                                    <input type="email" required id="form-email" class="w-full bg-transparent border-b-2 border-deep-700 text-white px-0 py-2 focus:outline-none focus:border-neon-emerald transition-colors font-code placeholder-slate-700" placeholder="Enter email">
                                </div>
                                <div class="group">
                                    <label class="block text-xs font-code font-bold text-neon-emerald mb-2 uppercase tracking-widest">>> Payload_Data</label>
                                    <textarea rows="4" required id="form-message" class="w-full bg-transparent border-b-2 border-deep-700 text-white px-0 py-2 focus:outline-none focus:border-neon-emerald transition-colors font-code placeholder-slate-700 resize-none" placeholder="Write logic here..."></textarea>
                                </div>
                                <button type="submit" class="w-full py-4 rounded-xl bg-neon-emerald text-deep-950 font-black text-sm uppercase tracking-widest hover:bg-neon-lime hover:shadow-[0_0_20px_rgba(163,230,53,0.5)] transition-all flex items-center justify-center gap-3">
                                    Execute Transmission <i class="fa-solid fa-paper-plane"></i>
                                </button>
                            </form>
                        </div>
                        
                    </div>
                </div>
            </div>
        </section>
    </main>

    <footer class="border-t border-deep-800 py-12 px-4 bg-deep-950 relative z-10 text-center">
        <div class="max-w-7xl mx-auto flex flex-col items-center gap-6">
            <div class="w-12 h-12 rounded-xl bg-gradient-to-br from-neon-emerald to-neon-teal flex items-center justify-center text-deep-950 font-black text-xl mb-2">WQ</div>
            <p class="text-slate-500 font-code text-sm">
                System compiled by <span class="text-neon-emerald font-bold">Wahab Qadeer</span> © <span id="current-year"></span>. <br>
                <span class="text-xs">BS Artificial Intelligence @ BIIT. All architectures reserved.</span>
            </p>
        </div>
    </footer>

    <!-- MODAL SYSTEM (For deep dive into projects) -->
    <!-- Modal 1 -->
    <div id="modal-1" class="modal-overlay" onclick="closeModal(event, 'modal-1')">
        <div class="modal-content p-8 md:p-12" onclick="event.stopPropagation()">
            <div class="flex justify-between items-start mb-6 border-b border-deep-800 pb-6">
                <div>
                    <span class="text-neon-emerald font-code text-sm uppercase tracking-widest font-bold block mb-2">Enterprise Software</span>
                    <h2 class="text-3xl font-extrabold text-white">Smart Hospital Management System</h2>
                </div>
                <button onclick="closeModal(null, 'modal-1')" class="w-10 h-10 rounded-full bg-deep-800 text-slate-400 hover:text-white hover:bg-red-500/20 hover:border-red-500/50 border border-transparent transition-all flex items-center justify-center">
                    <i class="fa-solid fa-xmark text-xl"></i>
                </button>
            </div>
            <div class="space-y-6 text-slate-300 leading-relaxed">
                <p>A comprehensive desktop application designed to streamline healthcare administration. Built from the ground up using strict Object-Oriented Programming (OOP) paradigms in Java.</p>
                <h4 class="text-xl font-bold text-white mt-6 mb-3">Architectural Highlights:</h4>
                <ul class="list-disc pl-6 space-y-2 text-sm">
                    <li><strong>Encapsulation & Inheritance:</strong> Clean class hierarchies for Patients, Doctors, and Administrators ensuring data security and modularity.</li>
                    <li><strong>Database Connectivity:</strong> Integrated with a relational database via JDBC to handle persistent storage of appointments, medical records, and billing.</li>
                    <li><strong>Graphical User Interface:</strong> Designed intuitive dashboards for staff to quickly input and retrieve critical patient data.</li>
                </ul>
                <div class="flex flex-wrap gap-3 mt-8 pt-6 border-t border-deep-800">
                    <span class="px-4 py-2 rounded-lg bg-deep-800 text-neon-emerald font-code text-xs font-bold border border-neon-emerald/30">Java</span>
                    <span class="px-4 py-2 rounded-lg bg-deep-800 text-neon-teal font-code text-xs font-bold border border-neon-teal/30">JDBC</span>
                    <span class="px-4 py-2 rounded-lg bg-deep-800 text-neon-lime font-code text-xs font-bold border border-neon-lime/30">OOP Design</span>
                </div>
            </div>
        </div>
    </div>

    <!-- Modal 2 -->
    <div id="modal-2" class="modal-overlay" onclick="closeModal(event, 'modal-2')">
        <div class="modal-content p-8 md:p-12" onclick="event.stopPropagation()">
            <div class="flex justify-between items-start mb-6 border-b border-deep-800 pb-6">
                <div>
                    <span class="text-neon-teal font-code text-sm uppercase tracking-widest font-bold block mb-2">Database Engineering</span>
                    <h2 class="text-3xl font-extrabold text-white">Flight Reservation DBMS</h2>
                </div>
                <button onclick="closeModal(null, 'modal-2')" class="w-10 h-10 rounded-full bg-deep-800 text-slate-400 hover:text-white transition-all flex items-center justify-center"><i class="fa-solid fa-xmark text-xl"></i></button>
            </div>
            <div class="space-y-6 text-slate-300 leading-relaxed">
                <p>A highly normalized relational database project engineered to simulate the backend of an international airline booking system.</p>
                <h4 class="text-xl font-bold text-white mt-6 mb-3">Core Database Logic:</h4>
                <ul class="list-disc pl-6 space-y-2 text-sm">
                    <li><strong>Schema Normalization:</strong> Entities reduced to 3NF/BCNF to eliminate data redundancy and insertion anomalies.</li>
                    <li><strong>Advanced Querying:</strong> Utilized complex multi-table JOINs, subqueries, and aggregate functions for report generation.</li>
                    <li><strong>Entity-Relationship Modeling:</strong> Translated conceptual ER diagrams into robust physical database tables defining strict cardinalities and foreign key constraints.</li>
                </ul>
                <div class="flex flex-wrap gap-3 mt-8 pt-6 border-t border-deep-800">
                    <span class="px-4 py-2 rounded-lg bg-deep-800 text-neon-teal font-code text-xs font-bold border border-neon-teal/30">SQL</span>
                    <span class="px-4 py-2 rounded-lg bg-deep-800 text-neon-cyan font-code text-xs font-bold border border-neon-cyan/30">Relational DB</span>
                    <span class="px-4 py-2 rounded-lg bg-deep-800 text-white font-code text-xs font-bold border border-white/30">ER Diagrams</span>
                </div>
            </div>
        </div>
    </div>

    <!-- Modal 3 & 4 (Shortened for brevity, but functional) -->
    <div id="modal-3" class="modal-overlay" onclick="closeModal(event, 'modal-3')"><div class="modal-content p-8 md:p-12" onclick="event.stopPropagation()"><div class="flex justify-between items-start mb-6 border-b border-deep-800 pb-6"><div><span class="text-neon-lime font-code text-sm uppercase tracking-widest font-bold block mb-2">Algorithmic Logic</span><h2 class="text-3xl font-extrabold text-white">Smart Irrigation Automation</h2></div><button onclick="closeModal(null, 'modal-3')" class="w-10 h-10 rounded-full bg-deep-800 text-slate-400 hover:text-white transition-all flex items-center justify-center"><i class="fa-solid fa-xmark text-xl"></i></button></div><div class="space-y-6 text-slate-300 leading-relaxed"><p>A console-based logic simulation built in C++ to model intelligent water distribution based on variable environmental factors.</p><div class="flex flex-wrap gap-3 mt-8 pt-6 border-t border-deep-800"><span class="px-4 py-2 rounded-lg bg-deep-800 text-neon-lime font-code text-xs font-bold border border-neon-lime/30">C++</span></div></div></div></div>
    
    <div id="modal-4" class="modal-overlay" onclick="closeModal(event, 'modal-4')"><div class="modal-content p-8 md:p-12" onclick="event.stopPropagation()"><div class="flex justify-between items-start mb-6 border-b border-deep-800 pb-6"><div><span class="text-[#ef4444] font-code text-sm uppercase tracking-widest font-bold block mb-2">Embedded Systems</span><h2 class="text-3xl font-extrabold text-white">Arduino Auto Fire Brigade</h2></div><button onclick="closeModal(null, 'modal-4')" class="w-10 h-10 rounded-full bg-deep-800 text-slate-400 hover:text-white transition-all flex items-center justify-center"><i class="fa-solid fa-xmark text-xl"></i></button></div><div class="space-y-6 text-slate-300 leading-relaxed"><p>Hardware and software synergy. Designed an autonomous robot utilizing flame sensors and microcontrollers to detect and extinguish fires dynamically.</p><div class="flex flex-wrap gap-3 mt-8 pt-6 border-t border-deep-800"><span class="px-4 py-2 rounded-lg bg-deep-800 text-[#ef4444] font-code text-xs font-bold border border-[#ef4444]/30">Arduino</span><span class="px-4 py-2 rounded-lg bg-deep-800 text-neon-emerald font-code text-xs font-bold border border-neon-emerald/30">C Language</span></div></div></div></div>

    <!-- Notification Toast -->
    <div id="toast" class="fixed bottom-8 right-8 z-50 transform translate-y-32 opacity-0 transition-all duration-500 pointer-events-none glass-panel px-6 py-4 rounded-xl border border-neon-emerald flex items-center gap-4 text-white font-code text-sm">
        <i class="fa-solid fa-circle-check text-neon-emerald text-2xl"></i>
        <span><strong class="block text-neon-emerald uppercase">Success</strong> Payload transmitted successfully.</span>
    </div>

    <!-- MAIN JAVASCRIPT ENGINE -->
    <script>
        // 1. Utilities & Initialization
        document.getElementById('current-year').textContent = new Date().getFullYear();

        // 2. Scroll Reveal & Number Counter Observers
        const revealElements = document.querySelectorAll('.reveal');
        const counters = document.querySelectorAll('.counter');
        let hasCounted = false;

        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.classList.add('active');
                    
                    // Trigger counters if they are visible
                    if(entry.target.querySelector('.counter') && !hasCounted) {
                        hasCounted = true;
                        counters.forEach(counter => {
                            const target = +counter.getAttribute('data-target');
                            const duration = 2000; 
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
        }, { threshold: 0.1 });
        revealElements.forEach(el => observer.observe(el));

        // 3. Typing Effect
        const phrases = ["Machine Learning Models", "Object-Oriented Logic", "Relational Databases", "Embedded IoT Systems"];
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
            let speed = isDel ? 30 : 60;
            if (!isDel && cIdx === current.length) { speed = 2500; isDel = true; } 
            else if (isDel && cIdx === 0) { isDel = false; pIdx = (pIdx + 1) % phrases.length; speed = 500; }
            setTimeout(typeWriter, speed);
        }
        setTimeout(typeWriter, 1000);

        // 4. Modal Logic
        function openModal(id) {
            document.body.style.overflow = 'hidden';
            document.getElementById(id).classList.add('active');
        }
        function closeModal(e, id) {
            if(e && e.target !== e.currentTarget) return;
            document.body.style.overflow = 'auto';
            document.getElementById(id).classList.remove('active');
        }

        // 5. Contact Form Toast
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

        // 6. Dynamic GitHub Heatmap Generation
        const heatmapContainer = document.getElementById('heatmap-container');
        const cellsNeeded = 52 * 7; // 1 year of weeks
        for(let i=0; i<cellsNeeded; i++) {
            const cell = document.createElement('div');
            // Randomly assign activity levels to simulate a busy student
            let level = 0;
            const rand = Math.random();
            if(rand > 0.9) level = 4;
            else if(rand > 0.75) level = 3;
            else if(rand > 0.5) level = 2;
            else if(rand > 0.3) level = 1;
            
            cell.className = `heatmap-cell level-${level}`;
            heatmapContainer.appendChild(cell);
        }

        // 7. CHART.JS MASSIVE INITIALIZATION
        document.addEventListener("DOMContentLoaded", function() {
            Chart.defaults.color = '#94a3b8';
            Chart.defaults.font.family = "'Fira Code', monospace";
            
            // Chart 1: Doughnut (Skill Depth)
            new Chart(document.getElementById('chartDoughnut').getContext('2d'), {
                type: 'doughnut',
                data: {
                    labels: ['Logic & Algorithms', 'System Architecture', 'Database Design', 'Hardware IoT'],
                    datasets: [{
                        data: [35, 25, 25, 15],
                        backgroundColor: ['#10b981', '#14b8a6', '#06b6d4', '#a3e635'],
                        borderColor: '#011612',
                        borderWidth: 4,
                        hoverOffset: 10
                    }]
                },
                options: {
                    responsive: true, maintainAspectRatio: false, cutout: '75%',
                    plugins: { 
                        legend: { position: 'bottom', labels: { padding: 20, font: {size: 11} } },
                        tooltip: { backgroundColor: '#033b30', titleColor: '#10b981', padding: 12 }
                    }
                }
            });

            // Chart 2: Radar (Core Competencies)
            new Chart(document.getElementById('chartRadar').getContext('2d'), {
                type: 'radar',
                data: {
                    labels: ['OOP', 'SQL', 'C++', 'Data Structures', 'Embedded Systems', 'Web Dev'],
                    datasets: [{
                        label: 'Competency Level',
                        data: [95, 90, 85, 88, 80, 75],
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
                            angleLines: { color: 'rgba(255,255,255,0.1)' },
                            grid: { color: 'rgba(255,255,255,0.1)' },
                            pointLabels: { color: '#6ee7b7', font: {size: 10} },
                            ticks: { display: false, max: 100 }
                        }
                    },
                    plugins: { legend: { display: false } }
                }
            });

            // Chart 3: Polar Area (Tech Stack)
            new Chart(document.getElementById('chartPolar').getContext('2d'), {
                type: 'polarArea',
                data: {
                    labels: ['Java', 'SQL', 'HTML/CSS', 'Kotlin', 'Arduino'],
                    datasets: [{
                        data: [90, 85, 70, 50, 80],
                        backgroundColor: [
                            'rgba(16, 185, 129, 0.6)',
                            'rgba(6, 182, 212, 0.6)',
                            'rgba(59, 130, 246, 0.6)',
                            'rgba(139, 92, 246, 0.6)',
                            'rgba(239, 68, 68, 0.6)'
                        ],
                        borderColor: '#011612',
                        borderWidth: 2
                    }]
                },
                options: {
                    responsive: true, maintainAspectRatio: false,
                    scales: { r: { grid: { color: 'rgba(255,255,255,0.1)' }, ticks: {display: false} } },
                    plugins: { legend: { position: 'right', labels: {font: {size: 10}} } }
                }
            });

            // Chart 4: Mixed (Learning Velocity)
            const ctxMixed = document.getElementById('chartMixed').getContext('2d');
            const gradBar = ctxMixed.createLinearGradient(0, 0, 0, 300);
            gradBar.addColorStop(0, 'rgba(6, 182, 212, 0.8)');
            gradBar.addColorStop(1, 'rgba(6, 182, 212, 0.1)');

            new Chart(ctxMixed, {
                type: 'bar',
                data: {
                    labels: ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 'Jul', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec'],
                    datasets: [
                        {
                            type: 'line', label: 'Expected Trajectory',
                            data: [10, 15, 25, 30, 45, 50, 65, 70, 75, 80, 90, 98],
                            borderColor: '#a3e635', borderWidth: 2, borderDash: [5, 5],
                            pointBackgroundColor: '#011612', pointBorderColor: '#a3e635', pointRadius: 4,
                            tension: 0.4
                        },
                        {
                            type: 'bar', label: 'Actual Knowledge Units',
                            data: [12, 18, 22, 35, 42, 55, 60, 68, 80, 85, 88, 95],
                            backgroundColor: gradBar, borderRadius: 4, barPercentage: 0.6
                        }
                    ]
                },
                options: {
                    responsive: true, maintainAspectRatio: false,
                    scales: {
                        x: { grid: { display: false } },
                        y: { grid: { color: 'rgba(255,255,255,0.05)' }, max: 100 }
                    },
                    plugins: { legend: { position: 'top', labels: {boxWidth: 10} } },
                    animation: { duration: 2500, delay: (c) => c.dataIndex * 50 }
                }
            });
        });

        // 8. Dual Canvas Background System
        // Canvas 1: Neural Network (Static slow float)
        const canvasNeural = document.getElementById('neural-canvas');
        const ctxN = canvasNeural.getContext('2d');
        
        // Canvas 2: Interactive Particles (React to mouse)
        const canvasInteract = document.getElementById('interaction-canvas');
        const ctxI = canvasInteract.getContext('2d');
        
        let width, height;
        let mouse = { x: null, y: null, radius: 150 };

        window.addEventListener('mousemove', (e) => {
            mouse.x = e.x;
            mouse.y = e.y;
        });

        function resize() {
            width = window.innerWidth;
            height = window.innerHeight;
            canvasNeural.width = width; canvasNeural.height = height;
            canvasInteract.width = width; canvasInteract.height = height;
        }
        window.addEventListener('resize', resize);
        resize();

        class Node {
            constructor(isInteractive) {
                this.x = Math.random() * width;
                this.y = Math.random() * height;
                this.vx = (Math.random() - 0.5) * (isInteractive ? 1.5 : 0.5);
                this.vy = (Math.random() - 0.5) * (isInteractive ? 1.5 : 0.5);
                this.radius = Math.random() * 2 + 1;
                this.isInteractive = isInteractive;
                this.baseX = this.x;
                this.baseY = this.y;
            }
            update() {
                if(this.isInteractive && mouse.x != null) {
                    let dx = mouse.x - this.x;
                    let dy = mouse.y - this.y;
                    let distance = Math.sqrt(dx*dx + dy*dy);
                    let force = (mouse.radius - distance) / mouse.radius;
                    
                    if(distance < mouse.radius) {
                        this.x -= dx * force * 0.03;
                        this.y -= dy * force * 0.03;
                    } else {
                        if(this.x !== this.baseX) this.x -= (this.x - this.baseX) * 0.01;
                        if(this.y !== this.baseY) this.y -= (this.y - this.baseY) * 0.01;
                    }
                }
                
                this.x += this.vx; this.y += this.vy;
                this.baseX += this.vx; this.baseY += this.vy;

                if (this.x < 0 || this.x > width) this.vx *= -1;
                if (this.y < 0 || this.y > height) this.vy *= -1;
            }
            draw(ctx, color) {
                ctx.beginPath();
                ctx.arc(this.x, this.y, this.radius, 0, Math.PI * 2);
                ctx.fillStyle = color;
                ctx.fill();
            }
        }

        const neuralNodes = Array.from({length: 60}, () => new Node(false));
        const interactNodes = Array.from({length: 80}, () => new Node(true));

        function animateCanvas() {
            ctxN.clearRect(0, 0, width, height);
            ctxI.clearRect(0, 0, width, height);

            // Draw Neural
            neuralNodes.forEach((n, i) => {
                n.update(); n.draw(ctxN, '#055c4b');
                for(let j=i+1; j<neuralNodes.length; j++) {
                    let dx = n.x - neuralNodes[j].x, dy = n.y - neuralNodes[j].y;
                    let dist = Math.sqrt(dx*dx + dy*dy);
                    if(dist < 150) {
                        ctxN.beginPath(); ctxN.moveTo(n.x, n.y); ctxN.lineTo(neuralNodes[j].x, neuralNodes[j].y);
                        ctxN.strokeStyle = `rgba(5, 92, 75, ${1 - dist/150})`; ctxN.stroke();
                    }
                }
            });

            // Draw Interactive
            interactNodes.forEach((n, i) => {
                n.update(); n.draw(ctxI, '#10b981');
                for(let j=i+1; j<interactNodes.length; j++) {
                    let dx = n.x - interactNodes[j].x, dy = n.y - interactNodes[j].y;
                    let dist = Math.sqrt(dx*dx + dy*dy);
                    if(dist < 120) {
                        ctxI.beginPath(); ctxI.moveTo(n.x, n.y); ctxI.lineTo(interactNodes[j].x, interactNodes[j].y);
                        ctxI.strokeStyle = `rgba(20, 184, 166, ${1 - dist/120})`; ctxI.stroke();
                    }
                }
            });

            requestAnimationFrame(animateCanvas);
        }
        animateCanvas();
    </script>
</body>
</html>
