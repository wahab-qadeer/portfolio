<!DOCTYPE html>
<html lang="en" class="scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Wahab Qadeer | BS AI Portfolio @ BIIT</title>
    
    <!-- Google Fonts -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Fira+Code:wght@400;500;600&family=Inter:wght@300;400;500;600;700&family=Space+Grotesk:wght@400;500;600;700&display=swap" rel="stylesheet">
    
    <!-- FontAwesome Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    
    <!-- Chart.js for Analytics & Animations -->
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
                        forest: {
                            900: '#011612',
                            800: '#032e25',
                            700: '#044236',
                            600: '#07604f'
                        },
                        neon: {
                            emerald: '#10b981',
                            lime: '#a3e635',
                            teal: '#14b8a6',
                            mint: '#6ee7b7',
                            purple: '#8b5cf6',
                            cyan: '#06b6d4'
                        }
                    },
                    animation: {
                        'spin-slow': 'spin 10s linear infinite',
                        'float': 'float 5s ease-in-out infinite',
                        'pulse-glow': 'pulseGlow 3s infinite alternate',
                        'bounce-subtle': 'bounceSubtle 2s infinite ease-in-out',
                        'glow-line': 'glowLine 2s infinite alternate',
                    },
                    keyframes: {
                        float: {
                            '0%, 100%': { transform: 'translateY(0px)' },
                            '50%': { transform: 'translateY(-12px)' },
                        },
                        pulseGlow: {
                            '0%': { boxShadow: '0 0 15px rgba(16, 185, 129, 0.2)' },
                            '100%': { boxShadow: '0 0 35px rgba(163, 230, 53, 0.4)' },
                        },
                        bounceSubtle: {
                            '0%, 100%': { transform: 'translateY(0)' },
                            '50%': { transform: 'translateY(-5px)' },
                        },
                        glowLine: {
                            '0%': { opacity: 0.5, boxShadow: '0 0 5px #10b981' },
                            '100%': { opacity: 1, boxShadow: '0 0 15px #14b8a6, 0 0 20px #10b981' },
                        }
                    }
                }
            }
        }
    </script>

    <style>
        body {
            background-color: #011612;
            color: #f1f5f9;
            font-family: 'Inter', sans-serif;
            overflow-x: hidden;
            -webkit-font-smoothing: antialiased;
        }

        h1, h2, h3, h4, .font-heading {
            font-family: 'Space Grotesk', sans-serif;
        }

        /* Neural Canvas Background */
        #neural-canvas {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -10;
            pointer-events: none;
        }

        /* Ambient Orbs */
        .ambient-orb {
            position: fixed;
            border-radius: 50%;
            filter: blur(140px);
            z-index: -9;
            opacity: 0.20;
            pointer-events: none;
        }
        .orb-emerald { top: -10%; left: -10%; width: 50vw; height: 50vw; background: #10b981; }
        .orb-teal { bottom: -15%; right: -10%; width: 60vw; height: 60vw; background: #14b8a6; }

        /* Glassmorphism Cards */
        .glass-card {
            background: rgba(4, 66, 54, 0.35);
            backdrop-filter: blur(16px);
            -webkit-backdrop-filter: blur(16px);
            border: 1px solid rgba(255, 255, 255, 0.05);
            box-shadow: 0 10px 30px -10px rgba(0, 0, 0, 0.5);
            transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
        }

        .glass-card:hover {
            background: rgba(4, 66, 54, 0.55);
            border-color: rgba(16, 185, 129, 0.3);
            box-shadow: 0 20px 40px -15px rgba(16, 185, 129, 0.2);
            transform: translateY(-5px);
        }

        /* Dashboard Panel Style */
        .dashboard-panel {
            background: linear-gradient(145deg, rgba(3, 46, 37, 0.9), rgba(1, 22, 18, 0.95));
            border: 1px solid rgba(20, 184, 166, 0.4);
            box-shadow: 0 0 40px rgba(16, 185, 129, 0.1);
        }

        /* Gradient Text Effects */
        .gradient-text-emerald-lime {
            background: linear-gradient(135deg, #10b981 0%, #a3e635 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        .gradient-text-teal-mint {
            background: linear-gradient(135deg, #14b8a6 0%, #6ee7b7 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        /* Profile Ring Avatar (Hero) */
        .profile-avatar-container {
            position: relative;
            width: 280px;
            height: 280px;
            margin: 0 auto;
            border-radius: 50%;
        }

        .profile-avatar-container::before {
            content: '';
            position: absolute;
            inset: -6px;
            border-radius: 50%;
            background: conic-gradient(from 0deg, #10b981, #14b8a6, #a3e635, #10b981);
            animation: spin 8s linear infinite;
            filter: blur(12px);
            opacity: 0.9;
        }

        .profile-avatar-container::after {
            content: '';
            position: absolute;
            inset: -3px;
            border-radius: 50%;
            background: conic-gradient(from 0deg, #10b981, #14b8a6, #a3e635, #10b981);
            animation: spin 8s linear infinite;
            z-index: 1;
        }

        .profile-img-wrap {
            position: relative;
            z-index: 2;
            width: 100%;
            height: 100%;
            border-radius: 50%;
            background: #011612;
            padding: 5px;
            overflow: hidden;
        }

        .profile-img-wrap img {
            width: 100%;
            height: 100%;
            border-radius: 50%;
            object-fit: cover;
            transition: transform 0.6s ease;
        }

        .profile-avatar-container:hover .profile-img-wrap img {
            transform: scale(1.08);
        }

        /* Dashboard specific DP Ring */
        .dash-dp-ring {
            box-shadow: 0 0 20px rgba(16, 185, 129, 0.4), inset 0 0 20px rgba(20, 184, 166, 0.4);
        }

        /* Scroll Reveal Utility */
        .reveal {
            opacity: 0;
            transform: translateY(40px);
            transition: all 0.8s cubic-bezier(0.16, 1, 0.3, 1);
        }

        .reveal.active {
            opacity: 1;
            transform: translateY(0);
        }

        /* Custom Scrollbar */
        ::-webkit-scrollbar { width: 8px; }
        ::-webkit-scrollbar-track { background: #011612; }
        ::-webkit-scrollbar-thumb { background: #044236; border-radius: 4px; }
        ::-webkit-scrollbar-thumb:hover { background: #10b981; }

        /* Typing Caret */
        .typing-cursor::after {
            content: '|';
            animation: blink 1s step-end infinite;
            color: #10b981;
            margin-left: 2px;
        }

        @keyframes blink {
            from, to { opacity: 1; }
            50% { opacity: 0; }
        }
    </style>
</head>
<body class="selection:bg-neon-emerald selection:text-forest-900">

    <!-- Ambient Backgrounds -->
    <canvas id="neural-canvas"></canvas>
    <div class="ambient-orb orb-emerald"></div>
    <div class="ambient-orb orb-teal"></div>

    <header class="fixed top-0 left-0 w-full z-50 transition-all duration-300 px-4 sm:px-8 py-4" id="main-header">
        <div class="max-w-7xl mx-auto">
            <div class="glass-card rounded-2xl px-6 py-3 flex items-center justify-between border border-white/10">
                <!-- Logo -->
                <a href="#" class="font-heading font-bold text-2xl tracking-wider text-white flex items-center gap-2 group">
                    <span class="w-8 h-8 rounded-lg bg-gradient-to-br from-neon-emerald to-neon-lime flex items-center justify-center text-forest-900 font-bold text-sm shadow-lg shadow-neon-emerald/20">WQ</span>
                    <span class="group-hover:text-neon-emerald transition-colors">Wahab<span class="text-neon-emerald">.ai</span></span>
                </a>

                <!-- Desktop Nav -->
                <nav class="hidden md:flex items-center space-x-8 text-sm font-medium text-slate-300">
                    <a href="#about" class="hover:text-neon-emerald transition-colors">About</a>
                    <a href="#skills" class="hover:text-neon-emerald transition-colors">Analytics</a>
                    <a href="#projects" class="hover:text-neon-emerald transition-colors">Projects</a>
                    <a href="#focus" class="hover:text-neon-emerald transition-colors">Growth Dashboard</a>
                    <a href="#connect" class="hover:text-neon-emerald transition-colors">Connect</a>
                </nav>

                <!-- CTA Button -->
                <a href="#connect" class="px-5 py-2 rounded-xl bg-gradient-to-r from-neon-emerald to-neon-teal text-forest-900 font-semibold text-xs uppercase tracking-wider hover:opacity-90 transition-all shadow-md shadow-neon-emerald/30 flex items-center gap-2 animate-pulse-glow">
                    <i class="fa-solid fa-paper-plane"></i> Get In Touch
                </a>
            </div>
        </div>
    </header>

    <main class="relative pt-28">

        <!-- Hero Section (DP MOVED TO LEFT) -->
        <section class="min-h-[90vh] flex items-center justify-center px-4 sm:px-6 lg:px-8 py-12 relative">
            <div class="max-w-6xl mx-auto grid grid-cols-1 lg:grid-cols-12 gap-12 items-center">
                
                <!-- Left Profile Avatar (Moved here based on request) -->
                <div class="lg:col-span-5 flex justify-center order-first lg:order-none reveal">
                    <div class="profile-avatar-container animate-float">
                        <div class="profile-img-wrap">
                            <!-- Update with your actual image path -->
                            <img 
                                src="WhatsApp Image 2026-08-13 at 1.09.24 PM_2.jpeg" 
                                alt="Wahab Qadeer" 
                                onerror="this.src='https://placehold.co/400x400/032e25/10b981?text=Wahab+Qadeer+BS(AI)'"
                            >
                        </div>
                    </div>
                </div>

                <!-- Right Content -->
                <div class="lg:col-span-7 space-y-6 text-center lg:text-left reveal">
                    <div class="inline-flex items-center gap-2 px-4 py-2 rounded-full glass-card border-neon-emerald/30 text-neon-emerald text-xs font-code uppercase tracking-wider">
                        <span class="w-2 h-2 rounded-full bg-neon-lime animate-ping"></span>
                        BS Artificial Intelligence @ BIIT
                    </div>

                    <h1 class="text-4xl sm:text-6xl font-bold tracking-tight text-white leading-tight">
                        Hi, I'm <span class="gradient-text-emerald-lime">Wahab Qadeer</span> 👋
                    </h1>

                    <div class="text-xl sm:text-2xl font-medium text-slate-300 h-10 flex items-center justify-center lg:justify-start">
                        <span id="typing-text" class="typing-cursor font-code text-neon-mint"></span>
                    </div>

                    <p class="text-slate-400 text-base sm:text-lg leading-relaxed max-w-2xl mx-auto lg:mx-0">
                        Undergraduate Computer Science & Artificial Intelligence student passionate about Machine Learning algorithms, Data Structures, OOP architectures, and automated hardware-software ecosystems.
                    </p>

                    <!-- Quote Card -->
                    <div class="glass-card p-5 rounded-2xl border-l-4 border-l-neon-emerald text-left text-sm text-slate-300 italic relative my-6 hover:border-l-neon-lime transition-colors">
                        <i class="fa-solid fa-quote-left text-neon-emerald/20 text-3xl absolute top-3 left-3"></i>
                        <p class="pl-8 relative z-10">
                            "In a world of infinite data, pattern recognition and artificial intelligence are the ultimate levers of human potential."
                        </p>
                    </div>

                    <!-- CTA Buttons -->
                    <div class="flex flex-wrap justify-center lg:justify-start gap-4 pt-2">
                        <a href="#projects" class="px-7 py-3.5 rounded-xl bg-neon-emerald text-forest-900 font-bold text-sm tracking-wide hover:bg-white transition-all shadow-lg shadow-neon-emerald/25 flex items-center gap-2">
                            <i class="fa-solid fa-rocket"></i> Explore Projects
                        </a>
                        <a href="#focus" class="px-7 py-3.5 rounded-xl glass-card text-white font-medium text-sm hover:border-neon-teal/50 transition-all flex items-center gap-2">
                            <i class="fa-solid fa-chart-pie text-neon-emerald text-base"></i> View Dashboard
                        </a>
                    </div>
                </div>

            </div>
        </section>

        <!-- Projects Section -->
        <section id="projects" class="py-20 px-4 sm:px-6 lg:px-8 max-w-7xl mx-auto border-t border-t-white/5">
            <div class="text-center mb-12 reveal">
                <h2 class="text-3xl sm:text-4xl font-bold text-white mb-3">Featured <span class="gradient-text-teal-mint">Projects</span></h2>
                <p class="text-slate-400 text-sm max-w-xl mx-auto">Demonstrating practical implementation across Java OOP, SQL, C++, Arduino, and Web tech.</p>
                
                <!-- Filter Buttons -->
                <div class="flex flex-wrap justify-center gap-3 mt-8" id="project-filters">
                    <button class="filter-btn active px-5 py-2 rounded-xl text-xs font-semibold glass-card border-neon-emerald text-neon-emerald transition-all" data-filter="all">All Projects</button>
                    <button class="filter-btn px-5 py-2 rounded-xl text-xs font-semibold glass-card text-slate-300 hover:text-white transition-all" data-filter="software">Software & AI</button>
                    <button class="filter-btn px-5 py-2 rounded-xl text-xs font-semibold glass-card text-slate-300 hover:text-white transition-all" data-filter="hardware">Hardware & IoT</button>
                    <button class="filter-btn px-5 py-2 rounded-xl text-xs font-semibold glass-card text-slate-300 hover:text-white transition-all" data-filter="webdb">Web & DB</button>
                </div>
            </div>

            <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8" id="projects-grid">
                
                <!-- Project 1 -->
                <div class="project-card glass-card rounded-3xl p-7 flex flex-col justify-between reveal group" data-category="software">
                    <div>
                        <div class="w-14 h-14 rounded-2xl bg-forest-700/50 border border-neon-emerald/30 flex items-center justify-center text-neon-emerald text-2xl mb-6 group-hover:scale-110 transition-transform">
                            <i class="fa-solid fa-hospital"></i>
                        </div>
                        <h3 class="text-xl font-bold text-white mb-3">Smart Hospital System</h3>
                        <p class="text-slate-400 text-sm leading-relaxed mb-6">
                            A complete desktop hospital management solution developed in Java using object-oriented principles and JDBC database connectivity.
                        </p>
                    </div>
                    <div>
                        <div class="flex flex-wrap gap-2 font-code text-[11px]">
                            <span class="px-3 py-1.5 rounded-lg bg-neon-emerald/10 text-neon-emerald border border-neon-emerald/20">Java</span>
                            <span class="px-3 py-1.5 rounded-lg bg-neon-lime/10 text-neon-lime border border-neon-lime/20">OOP</span>
                            <span class="px-3 py-1.5 rounded-lg bg-neon-teal/10 text-neon-teal border border-neon-teal/20">SQL</span>
                        </div>
                    </div>
                </div>

                <!-- Project 2 -->
                <div class="project-card glass-card rounded-3xl p-7 flex flex-col justify-between reveal group" data-category="webdb">
                    <div>
                        <div class="w-14 h-14 rounded-2xl bg-forest-700/50 border border-neon-teal/30 flex items-center justify-center text-neon-teal text-2xl mb-6 group-hover:scale-110 transition-transform">
                            <i class="fa-solid fa-plane-departure"></i>
                        </div>
                        <h3 class="text-xl font-bold text-white mb-3">Flight Reservation DB</h3>
                        <p class="text-slate-400 text-sm leading-relaxed mb-6">
                            A relational database project demonstrating complex SQL schema design, normalized tables, joins, and transactions.
                        </p>
                    </div>
                    <div>
                        <div class="flex flex-wrap gap-2 font-code text-[11px]">
                            <span class="px-3 py-1.5 rounded-lg bg-neon-teal/10 text-neon-teal border border-neon-teal/20">SQL</span>
                            <span class="px-3 py-1.5 rounded-lg bg-neon-emerald/10 text-neon-emerald border border-neon-emerald/20">RDBMS</span>
                        </div>
                    </div>
                </div>

                <!-- Project 3 -->
                <div class="project-card glass-card rounded-3xl p-7 flex flex-col justify-between reveal group" data-category="hardware">
                    <div>
                        <div class="w-14 h-14 rounded-2xl bg-forest-700/50 border border-neon-lime/30 flex items-center justify-center text-neon-lime text-2xl mb-6 group-hover:scale-110 transition-transform">
                            <i class="fa-solid fa-seedling"></i>
                        </div>
                        <h3 class="text-xl font-bold text-white mb-3">Smart Irrigation Logic</h3>
                        <p class="text-slate-400 text-sm leading-relaxed mb-6">
                            A logic-driven automation project implemented in C++ to model smart soil moisture checking and automated water valve triggering.
                        </p>
                    </div>
                    <div>
                        <div class="flex flex-wrap gap-2 font-code text-[11px]">
                            <span class="px-3 py-1.5 rounded-lg bg-neon-lime/10 text-neon-lime border border-neon-lime/20">C++</span>
                            <span class="px-3 py-1.5 rounded-lg bg-neon-mint/10 text-neon-mint border border-neon-mint/20">Logic Design</span>
                        </div>
                    </div>
                </div>

            </div>
        </section>

        <!-- Focus / Continuous Growth Section (NEW DASHBOARD UI) -->
        <section id="focus" class="py-20 px-4 sm:px-6 lg:px-8 max-w-7xl mx-auto overflow-hidden">
            <div class="text-center mb-12 reveal">
                <span class="text-xs font-code text-neon-teal uppercase tracking-widest block mb-2 animate-bounce-subtle">Continuous Growth</span>
                <h2 class="text-3xl sm:text-4xl font-bold text-white">Currently <span class="gradient-text-teal-mint">Learning & Expanding</span></h2>
            </div>

            <!-- Main Dashboard Layout -->
            <div class="flex flex-col lg:flex-row gap-6 lg:gap-0 items-center lg:items-stretch reveal">
                
                <!-- Left Identity Panel (DP & Title) -->
                <div class="lg:w-1/4 flex flex-col justify-center items-center relative z-10 bg-forest-900/40 p-8 rounded-3xl border border-neon-teal/20 backdrop-blur-md">
                    <!-- Glowing Horizontal Connector Line (Only on Desktop) -->
                    <div class="hidden lg:block absolute top-1/2 -right-[15%] w-[30%] h-[2px] bg-neon-emerald animate-glow-line z-0"></div>
                    <div class="hidden lg:block absolute top-1/2 right-[15%] w-3 h-3 rounded-full bg-white shadow-[0_0_10px_#10b981] transform -translate-y-1/2 z-10"></div>
                    
                    <!-- Circular DP -->
                    <div class="relative z-20 w-36 h-36 rounded-full p-1 bg-gradient-to-br from-neon-emerald via-neon-teal to-forest-800 dash-dp-ring mb-6">
                        <img 
                            src="WhatsApp Image 2026-08-13 at 1.09.24 PM_2.jpeg" 
                            alt="Wahab Qadeer DP" 
                            class="w-full h-full object-cover rounded-full border-4 border-forest-900"
                            onerror="this.src='https://placehold.co/200x200/032e25/10b981?text=WQ'"
                        >
                    </div>
                    
                    <h3 class="text-lg font-bold text-white tracking-wide text-center leading-tight">WAHAB QADEER | BIIT</h3>
                    <p class="text-sm text-slate-300 mt-1 font-medium text-center">BS(AI) Candidate</p>
                </div>

                <!-- Right Analytics Dashboard Panel -->
                <div class="lg:w-3/4 dashboard-panel rounded-3xl p-6 lg:p-8 relative z-20 lg:-ml-6 w-full">
                    
                    <!-- Top Charts Row -->
                    <div class="grid grid-cols-1 md:grid-cols-2 gap-6 mb-6">
                        
                        <!-- Pie / Doughnut Chart Card -->
                        <div class="bg-forest-900/60 p-5 rounded-2xl border border-white/5 shadow-inner">
                            <h4 class="text-xs text-center text-slate-300 font-bold mb-4 tracking-widest uppercase">Skill Depth Distribution</h4>
                            <div class="relative h-48 w-full flex justify-center">
                                <canvas id="skillDepthChart"></canvas>
                            </div>
                        </div>

                        <!-- Bar & Line Graph Chart Card -->
                        <div class="bg-forest-900/60 p-5 rounded-2xl border border-white/5 shadow-inner relative">
                            <h4 class="text-xs text-center text-slate-300 font-bold mb-4 tracking-widest uppercase">Learning Velocity (Latest Phase)</h4>
                            <div class="relative h-48 w-full">
                                <canvas id="learningVelocityChart"></canvas>
                            </div>
                            <!-- Current Status Indicator -->
                            <div class="absolute right-6 top-[40%] flex flex-col items-center opacity-80 hidden sm:flex">
                                <div class="w-1 h-8 border-l border-dashed border-neon-mint mb-1"></div>
                                <span class="text-[10px] text-neon-mint uppercase tracking-wider">Current Status</span>
                            </div>
                        </div>
                    </div>

                    <!-- Bottom Learning Cards Grid -->
                    <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-4">
                        
                        <!-- Card 1 -->
                        <div class="p-4 rounded-xl bg-forest-800/40 border border-neon-teal/30 hover:bg-forest-800 transition-colors group">
                            <div class="flex items-center gap-3 mb-2">
                                <i class="fa-brands fa-java text-neon-teal text-xl group-hover:scale-110 transition-transform"></i>
                                <h5 class="text-sm font-bold text-white leading-tight">Advanced<br>Java</h5>
                            </div>
                            <p class="text-[11px] text-slate-400 mt-2 leading-relaxed">Multi-threading, design patterns, and enterprise frameworks.</p>
                        </div>

                        <!-- Card 2 -->
                        <div class="p-4 rounded-xl bg-forest-800/40 border border-neon-purple/40 hover:bg-forest-800 transition-colors group">
                            <div class="flex items-center gap-3 mb-2">
                                <i class="fa-solid fa-mobile-screen-button text-neon-purple text-xl group-hover:scale-110 transition-transform"></i>
                                <h5 class="text-sm font-bold text-white leading-tight">Kotlin<br>Development</h5>
                            </div>
                            <p class="text-[11px] text-slate-400 mt-2 leading-relaxed">Modern Android app design & reactive logic.</p>
                        </div>

                        <!-- Card 3 -->
                        <div class="p-4 rounded-xl bg-forest-800/40 border border-neon-emerald/30 hover:bg-forest-800 transition-colors group">
                            <div class="flex items-center gap-3 mb-2">
                                <i class="fa-solid fa-diagram-project text-neon-emerald text-xl group-hover:scale-110 transition-transform"></i>
                                <h5 class="text-sm font-bold text-white leading-tight">Advanced<br>DSA</h5>
                            </div>
                            <p class="text-[11px] text-slate-400 mt-2 leading-relaxed">Graph theory, dynamic programming, and optimization algorithms.</p>
                        </div>

                        <!-- Card 4 -->
                        <div class="p-4 rounded-xl bg-forest-800/40 border border-neon-mint/30 hover:bg-forest-800 transition-colors group">
                            <div class="flex items-center gap-3 mb-2">
                                <i class="fa-solid fa-server text-neon-mint text-xl group-hover:scale-110 transition-transform"></i>
                                <h5 class="text-sm font-bold text-white leading-tight">Backend<br>Engineering</h5>
                            </div>
                            <p class="text-[11px] text-slate-400 mt-2 leading-relaxed">RESTful API creation, database scaling, and microservices.</p>
                        </div>

                    </div>
                </div>
            </div>
        </section>

        <!-- Connect Section -->
        <section id="connect" class="py-20 px-4 sm:px-6 lg:px-8 max-w-7xl mx-auto">
            <div class="grid grid-cols-1 lg:grid-cols-12 gap-12 items-center">
                <!-- Contact Form Code Remains Identical -->
                <div class="lg:col-span-5 reveal space-y-6">
                    <h2 class="text-3xl sm:text-4xl font-bold text-white">Connect With <span class="gradient-text-emerald-lime">Wahab</span></h2>
                    <p class="text-slate-400 text-sm leading-relaxed">
                        Interested in collaborating on software projects, AI research, or discussing computer science concepts? Feel free to reach out directly through any platform below.
                    </p>

                    <div class="space-y-4 pt-2">
                        <!-- Links... -->
                        <a href="https://www.linkedin.com/in/wahab-qadeer/" target="_blank" class="flex items-center gap-4 p-4 rounded-2xl glass-card hover:border-neon-emerald/40 group transition-all">
                            <div class="w-12 h-12 rounded-xl bg-neon-emerald/10 flex items-center justify-center text-neon-emerald text-xl group-hover:bg-neon-emerald group-hover:text-forest-900 transition-all">
                                <i class="fa-brands fa-linkedin-in"></i>
                            </div>
                            <div>
                                <span class="text-xs text-slate-500 uppercase tracking-wider block">LinkedIn Profile</span>
                                <span class="text-sm font-semibold text-white group-hover:text-neon-emerald transition-colors">linkedin.com/in/wahab-qadeer</span>
                            </div>
                        </a>
                        <a href="https://github.com/wahab-qadeer" target="_blank" class="flex items-center gap-4 p-4 rounded-2xl glass-card hover:border-neon-lime/40 group transition-all">
                            <div class="w-12 h-12 rounded-xl bg-neon-lime/10 flex items-center justify-center text-neon-lime text-xl group-hover:bg-neon-lime group-hover:text-forest-900 transition-all">
                                <i class="fa-brands fa-github"></i>
                            </div>
                            <div>
                                <span class="text-xs text-slate-500 uppercase tracking-wider block">GitHub Repository</span>
                                <span class="text-sm font-semibold text-white group-hover:text-neon-lime transition-colors">github.com/wahab-qadeer</span>
                            </div>
                        </a>
                        <a href="mailto:realwahabqadeer@gmail.com" class="flex items-center gap-4 p-4 rounded-2xl glass-card hover:border-neon-teal/40 group transition-all">
                            <div class="w-12 h-12 rounded-xl bg-neon-teal/10 flex items-center justify-center text-neon-teal text-xl group-hover:bg-neon-teal group-hover:text-forest-900 transition-all">
                                <i class="fa-solid fa-envelope"></i>
                            </div>
                            <div>
                                <span class="text-xs text-slate-500 uppercase tracking-wider block">Direct Email</span>
                                <span class="text-sm font-semibold text-white group-hover:text-neon-teal transition-colors">realwahabqadeer@gmail.com</span>
                            </div>
                        </a>
                    </div>
                </div>

                <div class="lg:col-span-7 reveal">
                    <form id="contact-form" class="glass-card p-8 rounded-3xl space-y-5 relative">
                        <h3 class="text-xl font-bold text-white mb-2">Send a Message</h3>
                        <div>
                            <label class="block text-xs font-medium text-slate-300 mb-1">Your Name</label>
                            <input type="text" required id="form-name" placeholder="Enter your name" class="w-full px-4 py-3 rounded-xl bg-forest-900 border border-white/10 text-white placeholder-slate-500 text-sm focus:outline-none focus:border-neon-emerald transition-colors">
                        </div>
                        <div>
                            <label class="block text-xs font-medium text-slate-300 mb-1">Your Email</label>
                            <input type="email" required id="form-email" placeholder="Enter your email" class="w-full px-4 py-3 rounded-xl bg-forest-900 border border-white/10 text-white placeholder-slate-500 text-sm focus:outline-none focus:border-neon-emerald transition-colors">
                        </div>
                        <div>
                            <label class="block text-xs font-medium text-slate-300 mb-1">Subject</label>
                            <input type="text" required id="form-subject" placeholder="Project Inquiry / Opportunity" class="w-full px-4 py-3 rounded-xl bg-forest-900 border border-white/10 text-white placeholder-slate-500 text-sm focus:outline-none focus:border-neon-emerald transition-colors">
                        </div>
                        <div>
                            <label class="block text-xs font-medium text-slate-300 mb-1">Message</label>
                            <textarea rows="4" required id="form-message" placeholder="Write your message here..." class="w-full px-4 py-3 rounded-xl bg-forest-900 border border-white/10 text-white placeholder-slate-500 text-sm focus:outline-none focus:border-neon-emerald transition-colors resize-none"></textarea>
                        </div>
                        <button type="submit" class="w-full py-3.5 rounded-xl bg-gradient-to-r from-neon-emerald to-neon-teal text-forest-900 font-bold text-sm tracking-wider uppercase hover:opacity-95 transition-all shadow-lg shadow-neon-emerald/20 flex items-center justify-center gap-2">
                            <i class="fa-solid fa-paper-plane"></i> Send Message
                        </button>
                    </form>
                </div>
            </div>
        </section>

    </main>

    <footer class="border-t border-white/10 py-10 px-4 sm:px-6 lg:px-8 text-center text-xs text-slate-500 relative z-10 bg-forest-900/50">
        <div class="max-w-7xl mx-auto flex flex-col sm:flex-row justify-between items-center gap-4">
            <p>© <span id="current-year"></span> Wahab Qadeer. BS Artificial Intelligence @ BIIT.</p>
            <div class="flex items-center gap-4">
                <a href="https://github.com/wahab-qadeer" target="_blank" class="hover:text-neon-emerald transition-colors"><i class="fa-brands fa-github text-lg"></i></a>
                <a href="https://www.linkedin.com/in/wahab-qadeer/" target="_blank" class="hover:text-neon-emerald transition-colors"><i class="fa-brands fa-linkedin text-lg"></i></a>
                <a href="mailto:realwahabqadeer@gmail.com" class="hover:text-neon-emerald transition-colors"><i class="fa-solid fa-envelope text-lg"></i></a>
            </div>
        </div>
    </footer>

    <!-- Toast Notification -->
    <div id="toast" class="fixed bottom-6 right-6 z-50 transform translate-y-24 opacity-0 transition-all duration-300 pointer-events-none glass-card px-6 py-4 rounded-2xl border-neon-emerald flex items-center gap-3 text-white text-sm shadow-2xl">
        <div class="w-8 h-8 rounded-full bg-neon-emerald/20 flex items-center justify-center text-neon-emerald">
            <i class="fa-solid fa-check"></i>
        </div>
        <span id="toast-message">Message sent successfully!</span>
    </div>

    <script>
        // Update Year
        document.getElementById('current-year').textContent = new Date().getFullYear();

        // Scroll Reveal
        const revealElements = document.querySelectorAll('.reveal');
        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.classList.add('active');
                }
            });
        }, { threshold: 0.1 });
        revealElements.forEach(el => observer.observe(el));

        // Typing Effect
        const typingPhrases = [
            "BS(AI) Student @ BIIT",
            "AI & Machine Learning Developer",
            "Software & OOP Specialist",
            "Hardware & IoT Integrator"
        ];
        let phraseIdx = 0, charIdx = 0, isDeleting = false;
        const typingElement = document.getElementById('typing-text');

        function typeLoop() {
            const currentPhrase = typingPhrases[phraseIdx];
            if (isDeleting) {
                typingElement.textContent = currentPhrase.substring(0, charIdx - 1);
                charIdx--;
            } else {
                typingElement.textContent = currentPhrase.substring(0, charIdx + 1);
                charIdx++;
            }
            let typeSpeed = isDeleting ? 40 : 80;
            if (!isDeleting && charIdx === currentPhrase.length) {
                typeSpeed = 2000;
                isDeleting = true;
            } else if (isDeleting && charIdx === 0) {
                isDeleting = false;
                phraseIdx = (phraseIdx + 1) % typingPhrases.length;
                typeSpeed = 500;
            }
            setTimeout(typeLoop, typeSpeed);
        }
        typeLoop();

        // Project Filtering
        const filterBtns = document.querySelectorAll('.filter-btn');
        const projectCards = document.querySelectorAll('.project-card');

        filterBtns.forEach(btn => {
            btn.addEventListener('click', () => {
                filterBtns.forEach(b => {
                    b.classList.remove('active', 'border-neon-emerald', 'text-neon-emerald');
                    b.classList.add('text-slate-300');
                });
                btn.classList.add('active', 'border-neon-emerald', 'text-neon-emerald');

                const filter = btn.getAttribute('data-filter');
                projectCards.forEach(card => {
                    if (filter === 'all' || card.getAttribute('data-category') === filter) {
                        card.style.display = 'flex';
                        setTimeout(() => card.style.opacity = '1', 50);
                    } else {
                        card.style.opacity = '0';
                        setTimeout(() => card.style.display = 'none', 300);
                    }
                });
            });
        });

        // Chart.js Graph Animations and Initialization
        document.addEventListener("DOMContentLoaded", function() {
            
            Chart.defaults.color = '#94a3b8';
            Chart.defaults.font.family = "'Inter', sans-serif";
            
            // 1. Doughnut / Pie Chart (Skill Depth Distribution)
            const ctxDoughnut = document.getElementById('skillDepthChart').getContext('2d');
            new Chart(ctxDoughnut, {
                type: 'doughnut',
                data: {
                    labels: ['Programming', 'Logic', 'Architecture', 'Tools'],
                    datasets: [{
                        data: [35, 25, 20, 20],
                        backgroundColor: [
                            '#10b981', // Emerald
                            '#14b8a6', // Teal
                            '#06b6d4', // Cyan
                            '#8b5cf6'  // Purple
                        ],
                        borderColor: '#011612',
                        borderWidth: 2,
                        hoverOffset: 6
                    }]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    cutout: '70%',
                    plugins: {
                        legend: {
                            position: 'right',
                            labels: {
                                color: '#cbd5e1',
                                boxWidth: 12,
                                padding: 15,
                                font: { size: 10 }
                            }
                        },
                        tooltip: {
                            backgroundColor: 'rgba(3, 46, 37, 0.95)',
                            titleColor: '#fff',
                            bodyColor: '#10b981',
                            borderColor: '#10b981',
                            borderWidth: 1,
                            callbacks: {
                                label: function(context) {
                                    return ' ' + context.label + ': ' + context.parsed + '%';
                                }
                            }
                        }
                    },
                    animation: {
                        animateScale: true,
                        animateRotate: true,
                        duration: 2000,
                        easing: 'easeOutQuart'
                    }
                }
            });

            // 2. Mixed Bar & Line Graph (Learning Velocity)
            const ctxMixed = document.getElementById('learningVelocityChart').getContext('2d');
            
            // Gradient for bars
            const barGradient = ctxMixed.createLinearGradient(0, 0, 0, 200);
            barGradient.addColorStop(0, '#10b981'); // Emerald
            barGradient.addColorStop(1, 'rgba(16, 185, 129, 0.1)'); // Transparent emerald

            new Chart(ctxMixed, {
                type: 'bar',
                data: {
                    labels: ['Jan', 'Feb', 'Mar', 'Apr', 'Jun', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec'],
                    datasets: [
                        {
                            type: 'line',
                            label: 'Velocity Trend',
                            data: [15, 20, 22, 35, 45, 55, 60, 58, 80, 95],
                            borderColor: '#6ee7b7', // Mint
                            borderWidth: 2,
                            borderDash: [5, 5],
                            pointBackgroundColor: '#fff',
                            pointBorderColor: '#14b8a6',
                            pointRadius: 3,
                            tension: 0.4, // Smooth curve
                            fill: false,
                            order: 1
                        },
                        {
                            type: 'bar',
                            label: 'Metrics Reached',
                            data: [11, 18, 25, 28, 40, 45, 53, 51, 76, 90],
                            backgroundColor: barGradient,
                            borderRadius: 4,
                            barPercentage: 0.5,
                            order: 2
                        }
                    ]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    scales: {
                        x: {
                            grid: { display: false, drawBorder: false },
                            ticks: { font: { size: 10 } }
                        },
                        y: {
                            grid: { color: 'rgba(255, 255, 255, 0.05)' },
                            beginAtZero: true,
                            max: 100,
                            ticks: { font: { size: 10 }, stepSize: 25 }
                        }
                    },
                    plugins: {
                        legend: { display: false },
                        tooltip: {
                            backgroundColor: 'rgba(3, 46, 37, 0.95)',
                            borderColor: '#14b8a6',
                            borderWidth: 1
                        }
                    },
                    animation: {
                        duration: 2500,
                        easing: 'easeOutQuart',
                        // Adds a staggered progressive drawing effect
                        delay: (context) => {
                            let delay = 0;
                            if (context.type === 'data' && context.mode === 'default') {
                                delay = context.dataIndex * 100 + context.datasetIndex * 100;
                            }
                            return delay;
                        }
                    }
                }
            });
        });

        // Neural Network Canvas Animation (Emerald Theme)
        const canvas = document.getElementById('neural-canvas');
        const ctx = canvas.getContext('2d');

        function resizeCanvas() {
            canvas.width = window.innerWidth;
            canvas.height = window.innerHeight;
        }
        window.addEventListener('resize', resizeCanvas);
        resizeCanvas();

        class NeuralNode {
            constructor() {
                this.x = Math.random() * canvas.width;
                this.y = Math.random() * canvas.height;
                this.vx = (Math.random() - 0.5) * 0.6;
                this.vy = (Math.random() - 0.5) * 0.6;
                this.radius = Math.random() * 2 + 1;
            }
            update() {
                this.x += this.vx;
                this.y += this.vy;
                if (this.x < 0 || this.x > canvas.width) this.vx *= -1;
                if (this.y < 0 || this.y > canvas.height) this.vy *= -1;
            }
            draw() {
                ctx.beginPath();
                ctx.arc(this.x, this.y, this.radius, 0, Math.PI * 2);
                ctx.fillStyle = '#10b981';
                ctx.fill();
            }
        }

        const nodes = [];
        const nodeCount = Math.min(Math.floor((window.innerWidth * window.innerHeight) / 12000), 80);
        for (let i = 0; i < nodeCount; i++) {
            nodes.push(new NeuralNode());
        }

        function animateNeuralNet() {
            ctx.clearRect(0, 0, canvas.width, canvas.height);
            for (let i = 0; i < nodes.length; i++) {
                nodes[i].update();
                nodes[i].draw();
                for (let j = i + 1; j < nodes.length; j++) {
                    const dx = nodes[i].x - nodes[j].x;
                    const dy = nodes[i].y - nodes[j].y;
                    const dist = Math.sqrt(dx * dx + dy * dy);
                    if (dist < 140) {
                        ctx.beginPath();
                        ctx.moveTo(nodes[i].x, nodes[i].y);
                        ctx.lineTo(nodes[j].x, nodes[j].y);
                        ctx.strokeStyle = `rgba(16, 185, 129, ${1 - dist / 140 * 0.85})`;
                        ctx.lineWidth = 0.6;
                        ctx.stroke();
                    }
                }
            }
            requestAnimationFrame(animateNeuralNet);
        }
        window.onload = function() { animateNeuralNet(); };
    </script>
</body>
</html>
