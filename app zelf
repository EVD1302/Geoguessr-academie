<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>GeoGuessr Academy - Complete Training Platform</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800&family=Space+Grotesk:wght@500;700&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * { margin: 0; padding: 0; box-sizing: border-box; }
        body { font-family: 'Inter', sans-serif; background: #0f0f0f; color: #fff; overflow-x: hidden; }
        .font-display { font-family: 'Space Grotesk', sans-serif; }
        
        /* Custom Scrollbar */
        ::-webkit-scrollbar { width: 8px; }
        ::-webkit-scrollbar-track { background: #1a1a1a; }
        ::-webkit-scrollbar-thumb { background: #10b981; border-radius: 4px; }
        
        /* Animations */
        @keyframes float { 0%, 100% { transform: translateY(0px); } 50% { transform: translateY(-10px); } }
        @keyframes pulse-glow { 0%, 100% { box-shadow: 0 0 20px rgba(16, 185, 129, 0.3); } 50% { box-shadow: 0 0 40px rgba(16, 185, 129, 0.6); } }
        @keyframes shake { 0%, 100% { transform: translateX(0); } 25% { transform: translateX(-10px); } 75% { transform: translateX(10px); } }
        @keyframes celebrate { 0% { transform: scale(1); } 50% { transform: scale(1.1); } 100% { transform: scale(1); } }
        @keyframes slideIn { from { transform: translateX(100%); opacity: 0; } to { transform: translateX(0); opacity: 1; } }
        
        .animate-float { animation: float 3s ease-in-out infinite; }
        .animate-shake { animation: shake 0.5s ease-in-out; }
        .animate-celebrate { animation: celebrate 0.5s ease-in-out; }
        .animate-slide-in { animation: slideIn 0.3s ease-out; }
        
        /* Glassmorphism */
        .glass { background: rgba(255, 255, 255, 0.03); backdrop-filter: blur(10px); border: 1px solid rgba(255, 255, 255, 0.1); }
        .glass-card { transition: all 0.3s ease; }
        .glass-card:hover { background: rgba(255, 255, 255, 0.08); transform: translateY(-5px); border-color: rgba(16, 185, 129, 0.5); }
        
        /* Progress Ring */
        .progress-ring { transform: rotate(-90deg); }
        .progress-ring-circle { transition: stroke-dashoffset 0.35s; transform-origin: 50% 50%; }
        
        /* Chapter Checkboxes */
        .chapter-check { appearance: none; width: 24px; height: 24px; border: 2px solid #374151; border-radius: 6px; cursor: pointer; position: relative; transition: all 0.3s; }
        .chapter-check:checked { background: #10b981; border-color: #10b981; }
        .chapter-check:checked::after { content: '✓'; position: absolute; top: 50%; left: 50%; transform: translate(-50%, -50%); color: white; font-weight: bold; }
        
        /* Flashcard */
        .flashcard { perspective: 1000px; height: 300px; }
        .flashcard-inner { position: relative; width: 100%; height: 100%; transition: transform 0.6s; transform-style: preserve-3d; }
        .flashcard.flipped .flashcard-inner { transform: rotateY(180deg); }
        .flashcard-front, .flashcard-back { position: absolute; width: 100%; height: 100%; backface-hidden: hidden; border-radius: 16px; display: flex; align-items: center; justify-content: center; }
        .flashcard-back { transform: rotateY(180deg); background: linear-gradient(135deg, #059669, #047857); }
        
        /* Map Interactive */
        .map-point { fill: #10b981; cursor: pointer; transition: all 0.3s; }
        .map-point:hover { fill: #34d399; r: 8; }
        .map-point.correct { fill: #10b981; animation: pulse-glow 2s infinite; }
        .map-point.wrong { fill: #ef4444; }
        
        /* Detective Mode */
        .clue-card { transition: all 0.3s; border-left: 4px solid transparent; }
        .clue-card:hover { border-left-color: #10b981; background: rgba(16, 185, 129, 0.05); }
        .clue-used { opacity: 0.5; border-left-color: #6b7280; }
        
        /* Streak Counter */
        .streak-flame { animation: flicker 1s ease-in-out infinite alternate; }
        @keyframes flicker { 0% { transform: scale(1); } 100% { transform: scale(1.1); } }
        
        /* Confetti */
        .confetti { position: fixed; width: 10px; height: 10px; background: #10b981; position: absolute; animation: confetti-fall 3s ease-out forwards; z-index: 9999; }
        @keyframes confetti-fall { 0% { transform: translateY(-100px) rotate(0deg); opacity: 1; } 100% { transform: translateY(100vh) rotate(720deg); opacity: 0; } }
        
        /* Locked Content */
        .locked { position: relative; overflow: hidden; }
        .locked::after { content: '🔒'; position: absolute; top: 50%; left: 50%; transform: translate(-50%, -50%); font-size: 3rem; opacity: 0.5; }
        .locked-overlay { background: rgba(0,0,0,0.7); backdrop-filter: blur(4px); }
        
        /* Gradient Text */
        .gradient-text { background: linear-gradient(135deg, #10b981, #3b82f6, #8b5cf6); -webkit-background-clip: text; -webkit-text-fill-color: transparent; background-size: 200% 200%; animation: gradient 3s ease infinite; }
        @keyframes gradient { 0% { background-position: 0% 50%; } 50% { background-position: 100% 50%; } 100% { background-position: 0% 50%; } }
        
        /* Payment Modal */
        .pricing-card { transition: all 0.3s; border: 2px solid transparent; }
        .pricing-card:hover { transform: translateY(-10px); border-color: #10b981; }
        .pricing-featured { border-color: #10b981; background: rgba(16, 185, 129, 0.05); }
        
        /* Auth Modal */
        .auth-input { background: rgba(255,255,255,0.05); border: 1px solid rgba(255,255,255,0.1); transition: all 0.3s; }
        .auth-input:focus { border-color: #10b981; outline: none; background: rgba(255,255,255,0.08); }
        
        /* Country Cards */
        .country-card { transition: all 0.3s; }
        .country-card:hover { transform: scale(1.05); z-index: 10; }
        
        /* Meta Info Tags */
        .meta-tag { display: inline-flex; align-items: center; gap: 0.5rem; padding: 0.25rem 0.75rem; border-radius: 9999px; font-size: 0.75rem; font-weight: 600; }
        .meta-tag.sun { background: rgba(251, 191, 36, 0.2); color: #fbbf24; }
        .meta-tag.car { background: rgba(59, 130, 246, 0.2); color: #60a5fa; }
        .meta-tag.road { background: rgba(16, 185, 129, 0.2); color: #34d399; }
        .meta-tag.plate { background: rgba(239, 68, 68, 0.2); color: #f87171; }
    </style>
<base target="_blank">
</head>
<body class="bg-gray-950">

    <!-- AUTH MODAL (Login/Register) -->
    <div id="authModal" class="fixed inset-0 z-[60] flex items-center justify-center bg-black/90 backdrop-blur-md">
        <div class="glass rounded-3xl p-8 max-w-md w-full mx-4 relative">
            <div class="text-center mb-8">
                <div class="w-16 h-16 rounded-2xl bg-gradient-to-br from-emerald-400 to-blue-600 flex items-center justify-center mx-auto mb-4 animate-float">
                    <i class="fas fa-globe-americas text-3xl"></i>
                </div>
                <h2 class="text-3xl font-bold font-display mb-2">Welcome to GeoGuessr Academy</h2>
                <p class="text-gray-400">Master the art of geolocation</p>
            </div>

            <!-- Language Selection -->
            <div class="mb-6">
                <label class="block text-sm font-medium mb-2 text-gray-300">Select Your Language</label>
                <div class="grid grid-cols-3 gap-2">
                    <button onclick="selectLanguage('en')" class="lang-btn p-3 rounded-xl bg-white/5 hover:bg-emerald-500/20 border border-transparent hover:border-emerald-500 transition text-center" data-lang="en">
                        <div class="text-2xl mb-1">🇬🇧</div>
                        <div class="text-xs">English</div>
                    </button>
                    <button onclick="selectLanguage('nl')" class="lang-btn p-3 rounded-xl bg-white/5 hover:bg-emerald-500/20 border border-transparent hover:border-emerald-500 transition text-center" data-lang="nl">
                        <div class="text-2xl mb-1">🇳🇱</div>
                        <div class="text-xs">Nederlands</div>
                    </button>
                    <button onclick="selectLanguage('de')" class="lang-btn p-3 rounded-xl bg-white/5 hover:bg-emerald-500/20 border border-transparent hover:border-emerald-500 transition text-center" data-lang="de">
                        <div class="text-2xl mb-1">🇩🇪</div>
                        <div class="text-xs">Deutsch</div>
                    </button>
                    <button onclick="selectLanguage('fr')" class="lang-btn p-3 rounded-xl bg-white/5 hover:bg-emerald-500/20 border border-transparent hover:border-emerald-500 transition text-center" data-lang="fr">
                        <div class="text-2xl mb-1">🇫🇷</div>
                        <div class="text-xs">Français</div>
                    </button>
                    <button onclick="selectLanguage('es')" class="lang-btn p-3 rounded-xl bg-white/5 hover:bg-emerald-500/20 border border-transparent hover:border-emerald-500 transition text-center" data-lang="es">
                        <div class="text-2xl mb-1">🇪🇸</div>
                        <div class="text-xs">Español</div>
                    </button>
                    <button onclick="selectLanguage('jp')" class="lang-btn p-3 rounded-xl bg-white/5 hover:bg-emerald-500/20 border border-transparent hover:border-emerald-500 transition text-center" data-lang="jp">
                        <div class="text-2xl mb-1">🇯🇵</div>
                        <div class="text-xs">日本語</div>
                    </button>
                </div>
            </div>

            <!-- Login Form -->
            <form id="loginForm" class="space-y-4">
                <div>
                    <input type="email" placeholder="Email address" class="auth-input w-full px-4 py-3 rounded-xl text-white placeholder-gray-500" required>
                </div>
                <div>
                    <input type="password" placeholder="Password" class="auth-input w-full px-4 py-3 rounded-xl text-white placeholder-gray-500" required>
                </div>
                <button type="submit" class="w-full py-3 rounded-xl bg-gradient-to-r from-emerald-500 to-blue-600 hover:from-emerald-600 hover:to-blue-700 font-bold transition transform hover:scale-[1.02]">
                    Start Free Trial
                </button>
            </form>

            <div class="mt-6 text-center text-sm text-gray-400">
                <p>7 days free • Then <span id="priceDisplay">€11.99</span>/month</p>
                <p class="mt-2 text-xs">Cancel anytime • No credit card required for trial</p>
            </div>
        </div>
    </div>

    <!-- PAYMENT MODAL -->
    <div id="paymentModal" class="hidden fixed inset-0 z-[60] flex items-center justify-center bg-black/90 backdrop-blur-md overflow-y-auto py-10">
        <div class="glass rounded-3xl p-8 max-w-4xl w-full mx-4 relative">
            <button onclick="closePaymentModal()" class="absolute top-4 right-4 w-10 h-10 rounded-full bg-white/10 hover:bg-white/20 flex items-center justify-center transition">
                <i class="fas fa-times"></i>
            </button>
            
            <div class="text-center mb-8">
                <h2 class="text-3xl font-bold font-display mb-2">Choose Your Plan</h2>
                <p class="text-gray-400">Select your region for local pricing</p>
            </div>

            <!-- Region Selector -->
            <div class="flex justify-center gap-2 mb-8 flex-wrap">
                <button onclick="setRegion('EU')" class="region-btn px-4 py-2 rounded-full bg-emerald-500 text-white text-sm font-medium" data-region="EU">🇪🇺 Europe</button>
                <button onclick="setRegion('US')" class="region-btn px-4 py-2 rounded-full bg-white/10 text-gray-300 text-sm font-medium hover:bg-white/20" data-region="US">🇺🇸 USA</button>
                <button onclick="setRegion('UK')" class="region-btn px-4 py-2 rounded-full bg-white/10 text-gray-300 text-sm font-medium hover:bg-white/20" data-region="UK">🇬🇧 UK</button>
                <button onclick="setRegion('CA')" class="region-btn px-4 py-2 rounded-full bg-white/10 text-gray-300 text-sm font-medium hover:bg-white/20" data-region="CA">🇨🇦 Canada</button>
                <button onclick="setRegion('AU')" class="region-btn px-4 py-2 rounded-full bg-white/10 text-gray-300 text-sm font-medium hover:bg-white/20" data-region="AU">🇦🇺 Australia</button>
                <button onclick="setRegion('JP')" class="region-btn px-4 py-2 rounded-full bg-white/10 text-gray-300 text-sm font-medium hover:bg-white/20" data-region="JP">🇯🇵 Japan</button>
            </div>

            <div class="grid md:grid-cols-2 gap-6">
                <!-- Monthly Plan -->
                <div class="pricing-card glass rounded-2xl p-6">
                    <div class="flex items-center justify-between mb-4">
                        <h3 class="text-xl font-bold">Monthly</h3>
                        <span class="px-3 py-1 rounded-full bg-white/10 text-xs">Flexible</span>
                    </div>
                    <div class="mb-4">
                        <span class="text-4xl font-bold" id="monthlyPrice">€11.99</span>
                        <span class="text-gray-400">/month</span>
                    </div>
                    <ul class="space-y-2 mb-6 text-sm text-gray-300">
                        <li class="flex items-center gap-2"><i class="fas fa-check text-emerald-400"></i> Full course access</li>
                        <li class="flex items-center gap-2"><i class="fas fa-check text-emerald-400"></i> All training modes</li>
                        <li class="flex items-center gap-2"><i class="fas fa-check text-emerald-400"></i> Detective Mode</li>
                        <li class="flex items-center gap-2"><i class="fas fa-check text-emerald-400"></i> Cancel anytime</li>
                    </ul>
                    <button onclick="subscribe('monthly')" class="w-full py-3 rounded-xl bg-white/10 hover:bg-white/20 font-semibold transition">Choose Monthly</button>
                </div>

                <!-- Yearly Plan (Featured) -->
                <div class="pricing-card pricing-featured glass rounded-2xl p-6 relative">
                    <div class="absolute -top-3 left-1/2 transform -translate-x-1/2 px-4 py-1 rounded-full bg-emerald-500 text-xs font-bold">SAVE 40%</div>
                    <div class="flex items-center justify-between mb-4">
                        <h3 class="text-xl font-bold">Yearly</h3>
                        <span class="px-3 py-1 rounded-full bg-emerald-500/20 text-emerald-400 text-xs">Best Value</span>
                    </div>
                    <div class="mb-4">
                        <span class="text-4xl font-bold" id="yearlyPrice">€7.99</span>
                        <span class="text-gray-400">/month</span>
                        <div class="text-sm text-emerald-400 mt-1">Billed annually (<span id="yearlyTotal">€95.88</span>)</div>
                    </div>
                    <ul class="space-y-2 mb-6 text-sm text-gray-300">
                        <li class="flex items-center gap-2"><i class="fas fa-check text-emerald-400"></i> Everything in Monthly</li>
                        <li class="flex items-center gap-2"><i class="fas fa-check text-emerald-400"></i> Priority support</li>
                        <li class="flex items-center gap-2"><i class="fas fa-check text-emerald-400"></i> Exclusive advanced chapters</li>
                        <li class="flex items-center gap-2"><i class="fas fa-check text-emerald-400"></i> Downloadable resources</li>
                    </ul>
                    <button onclick="subscribe('yearly')" class="w-full py-3 rounded-xl bg-emerald-500 hover:bg-emerald-600 font-bold transition">Choose Yearly</button>
                </div>
            </div>

            <div class="mt-6 text-center text-xs text-gray-500">
                <p>Prices shown include local taxes where applicable. 7-day free trial for new users.</p>
            </div>
        </div>
    </div>

    <!-- Navigation -->
    <nav class="fixed top-0 w-full z-50 glass border-b border-white/10">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex justify-between items-center h-16">
                <div class="flex items-center gap-3 cursor-pointer" onclick="showDashboard()">
                    <div class="w-10 h-10 rounded-xl bg-gradient-to-br from-emerald-400 to-blue-600 flex items-center justify-center animate-float">
                        <i class="fas fa-globe-americas text-xl"></i>
                    </div>
                    <span class="font-display font-bold text-xl tracking-tight">GeoGuessr<span class="text-emerald-400">Academy</span></span>
                </div>
                
                <div class="hidden md:flex items-center space-x-1">
                    <button onclick="showModule('chapters')" class="nav-btn px-4 py-2 rounded-lg hover:bg-white/5 transition text-sm font-medium text-gray-300 hover:text-white">
                        <i class="fas fa-book mr-2"></i>Chapters
                    </button>
                    <button onclick="showModule('practice')" class="nav-btn px-4 py-2 rounded-lg hover:bg-white/5 transition text-sm font-medium text-gray-300 hover:text-white">
                        <i class="fas fa-dumbbell mr-2"></i>Practice
                    </button>
                    <button onclick="showModule('flags')" class="nav-btn px-4 py-2 rounded-lg hover:bg-white/5 transition text-sm font-medium text-gray-300 hover:text-white">
                        <i class="fas fa-flag mr-2"></i>Flags
                    </button>
                    <button onclick="showModule('languages')" class="nav-btn px-4 py-2 rounded-lg hover:bg-white/5 transition text-sm font-medium text-gray-300 hover:text-white">
                        <i class="fas fa-language mr-2"></i>Languages
                    </button>
                    <button onclick="showModule('locations')" class="nav-btn px-4 py-2 rounded-lg hover:bg-white/5 transition text-sm font-medium text-gray-300 hover:text-white">
                        <i class="fas fa-map-marked-alt mr-2"></i>Locations
                    </button>
                    <button onclick="showModule('capitals')" class="nav-btn px-4 py-2 rounded-lg hover:bg-white/5 transition text-sm font-medium text-gray-300 hover:text-white">
                        <i class="fas fa-city mr-2"></i>Capitals
                    </button>
                    <button onclick="showModule('detective')" class="nav-btn px-4 py-2 rounded-lg bg-orange-500/20 text-orange-400 hover:bg-orange-500/30 transition text-sm font-medium">
                        <i class="fas fa-search mr-2"></i>Detective
                    </button>
                    <button onclick="showModule('meta')" class="nav-btn px-4 py-2 rounded-lg bg-purple-500/20 text-purple-400 hover:bg-purple-500/30 transition text-sm font-medium">
                        <i class="fas fa-database mr-2"></i>Meta
                    </button>
                </div>

                <div class="flex items-center gap-4">
                    <div class="hidden md:flex items-center gap-2 px-3 py-1 rounded-full bg-emerald-500/10 border border-emerald-500/30 cursor-pointer" onclick="showPaymentModal()">
                        <i class="fas fa-crown text-emerald-400"></i>
                        <span class="text-xs font-bold text-emerald-400">PRO</span>
                    </div>
                    <div class="flex items-center gap-2 px-3 py-1 rounded-full bg-orange-500/10 border border-orange-500/30">
                        <i class="fas fa-fire text-orange-400 streak-flame"></i>
                        <span class="text-sm font-bold text-orange-400" id="streakCounter">12</span>
                    </div>
                    <div class="w-10 h-10 rounded-full bg-gradient-to-r from-purple-500 to-pink-500 flex items-center justify-center font-bold cursor-pointer relative group">
                        <span id="userInitials">JD</span>
                        <div class="absolute right-0 top-12 w-48 glass rounded-xl p-3 hidden group-hover:block animate-slide-in">
                            <div class="text-sm font-semibold mb-2" id="userNameDisplay">John Doe</div>
                            <div class="text-xs text-gray-400 mb-3" id="userEmailDisplay">john@example.com</div>
                            <button onclick="logout()" class="w-full py-2 rounded-lg bg-red-500/20 text-red-400 text-xs hover:bg-red-500/30 transition">Logout</button>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </nav>

    <!-- Main Content Container -->
    <main class="pt-20 pb-10 min-h-screen">
        
        <!-- DASHBOARD -->
        <div id="dashboard" class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <!-- Welcome Banner -->
            <div class="glass rounded-2xl p-6 mb-8 bg-gradient-to-r from-emerald-500/10 to-blue-500/10 border-emerald-500/30">
                <div class="flex items-center justify-between">
                    <div>
                        <h1 class="text-2xl font-bold mb-1">Welcome back, <span id="welcomeName">Explorer</span>! 🌍</h1>
                        <p class="text-gray-400">Continue your journey to GeoGuessr mastery</p>
                    </div>
                    <div class="text-right">
                        <div class="text-sm text-gray-400">Trial ends in</div>
                        <div class="text-2xl font-bold text-emerald-400" id="trialCountdown">6 days</div>
                    </div>
                </div>
            </div>

            <!-- Hero Stats -->
            <div class="grid md:grid-cols-4 gap-6 mb-8">
                <div class="glass rounded-2xl p-6 relative overflow-hidden group">
                    <div class="absolute top-0 right-0 w-32 h-32 bg-emerald-500/10 rounded-full -mr-16 -mt-16 transition-transform group-hover:scale-150"></div>
                    <div class="relative">
                        <div class="text-3xl font-bold mb-1" id="overallProgress">34%</div>
                        <div class="text-sm text-gray-400">Overall Progress</div>
                        <div class="mt-3 h-2 bg-gray-800 rounded-full overflow-hidden">
                            <div class="h-full bg-gradient-to-r from-emerald-400 to-blue-500 rounded-full transition-all duration-1000" style="width: 34%"></div>
                        </div>
                    </div>
                </div>
                
                <div class="glass rounded-2xl p-6 relative overflow-hidden group">
                    <div class="absolute top-0 right-0 w-32 h-32 bg-blue-500/10 rounded-full -mr-16 -mt-16 transition-transform group-hover:scale-150"></div>
                    <div class="relative">
                        <div class="text-3xl font-bold mb-1">7/48</div>
                        <div class="text-sm text-gray-400">Chapters Done</div>
                        <div class="mt-3 flex gap-1">
                            <div class="h-2 w-8 bg-emerald-500 rounded-full"></div>
                            <div class="h-2 w-8 bg-emerald-500 rounded-full"></div>
                            <div class="h-2 w-8 bg-emerald-500 rounded-full"></div>
                            <div class="h-2 w-8 bg-gray-700 rounded-full"></div>
                        </div>
                    </div>
                </div>

                <div class="glass rounded-2xl p-6 relative overflow-hidden group">
                    <div class="absolute top-0 right-0 w-32 h-32 bg-purple-500/10 rounded-full -mr-16 -mt-16 transition-transform group-hover:scale-150"></div>
                    <div class="relative">
                        <div class="text-3xl font-bold mb-1">1,247</div>
                        <div class="text-sm text-gray-400">XP Earned</div>
                        <div class="mt-3 text-xs text-purple-400">Level 8 • 230 to next</div>
                    </div>
                </div>

                <div class="glass rounded-2xl p-6 relative overflow-hidden group cursor-pointer" onclick="showModule('detective')">
                    <div class="absolute top-0 right-0 w-32 h-32 bg-orange-500/10 rounded-full -mr-16 -mt-16 transition-transform group-hover:scale-150"></div>
                    <div class="relative">
                        <div class="text-3xl font-bold mb-1 text-orange-400">Detective</div>
                        <div class="text-sm text-gray-400">Master Mode</div>
                        <div class="mt-3 flex items-center gap-2 text-xs text-orange-400">
                            <i class="fas fa-star"></i>
                            <span>3/5 Stars Earned</span>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Module Grid -->
            <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-6">
                <!-- Chapters Module -->
                <div onclick="showModule('chapters')" class="glass rounded-2xl p-6 cursor-pointer glass-card group">
                    <div class="flex items-start justify-between mb-4">
                        <div class="w-14 h-14 rounded-2xl bg-emerald-500/20 flex items-center justify-center text-emerald-400 text-2xl group-hover:scale-110 transition">
                            <i class="fas fa-book-open"></i>
                        </div>
                        <span class="px-3 py-1 rounded-full bg-emerald-500/20 text-emerald-400 text-xs font-bold">7/48</span>
                    </div>
                    <h3 class="text-xl font-bold mb-2">Course Chapters</h3>
                    <p class="text-gray-400 text-sm mb-4">Structured learning path from basics to World Championship level. Covers all continents and advanced meta.</p>
                    <div class="flex items-center gap-2 text-sm text-emerald-400">
                        <span>Continue Chapter 8</span>
                        <i class="fas fa-arrow-right"></i>
                    </div>
                </div>

                <!-- Practice Module -->
                <div onclick="showModule('practice')" class="glass rounded-2xl p-6 cursor-pointer glass-card group">
                    <div class="flex items-start justify-between mb-4">
                        <div class="w-14 h-14 rounded-2xl bg-blue-500/20 flex items-center justify-center text-blue-400 text-2xl group-hover:scale-110 transition">
                            <i class="fas fa-dumbbell"></i>
                        </div>
                        <span class="px-3 py-1 rounded-full bg-blue-500/20 text-blue-400 text-xs font-bold">Daily</span>
                    </div>
                    <h3 class="text-xl font-bold mb-2">Practice Arena</h3>
                    <p class="text-gray-400 text-sm mb-4">Street View images and text-based training scenarios with real GeoGuessr locations</p>
                    <div class="flex items-center gap-2 text-sm text-blue-400">
                        <span>Start Training</span>
                        <i class="fas fa-arrow-right"></i>
                    </div>
                </div>

                <!-- Flags Module -->
                <div onclick="showModule('flags')" class="glass rounded-2xl p-6 cursor-pointer glass-card group">
                    <div class="flex items-start justify-between mb-4">
                        <div class="w-14 h-14 rounded-2xl bg-red-500/20 flex items-center justify-center text-red-400 text-2xl group-hover:scale-110 transition">
                            <i class="fas fa-flag"></i>
                        </div>
                        <span class="px-3 py-1 rounded-full bg-red-500/20 text-red-400 text-xs font-bold">195</span>
                    </div>
                    <h3 class="text-xl font-bold mb-2">Flag Master</h3>
                    <p class="text-gray-400 text-sm mb-4">Learn to identify every country flag instantly. Includes historical flags and variations.</p>
                    <div class="flex items-center gap-2 text-sm text-red-400">
                        <span>Current Streak: 23</span>
                        <i class="fas fa-fire"></i>
                    </div>
                </div>

                <!-- Languages Module -->
                <div onclick="showModule('languages')" class="glass rounded-2xl p-6 cursor-pointer glass-card group">
                    <div class="flex items-start justify-between mb-4">
                        <div class="w-14 h-14 rounded-2xl bg-purple-500/20 flex items-center justify-center text-purple-400 text-2xl group-hover:scale-110 transition">
                            <i class="fas fa-language"></i>
                        </div>
                        <span class="px-3 py-1 rounded-full bg-purple-500/20 text-purple-400 text-xs font-bold">50+</span>
                    </div>
                    <h3 class="text-xl font-bold mb-2">Language ID</h3>
                    <p class="text-gray-400 text-sm mb-4">Recognize scripts and languages from street signs, storefronts, and license plates</p>
                    <div class="flex items-center gap-2 text-sm text-purple-400">
                        <span>Practice Now</span>
                        <i class="fas fa-arrow-right"></i>
                    </div>
                </div>

                <!-- Locations Module -->
                <div onclick="showModule('locations')" class="glass rounded-2xl p-6 cursor-pointer glass-card group">
                    <div class="flex items-start justify-between mb-4">
                        <div class="w-14 h-14 rounded-2xl bg-yellow-500/20 flex items-center justify-center text-yellow-400 text-2xl group-hover:scale-110 transition">
                            <i class="fas fa-map-marked-alt"></i>
                        </div>
                        <span class="px-3 py-1 rounded-full bg-yellow-500/20 text-yellow-400 text-xs font-bold">World</span>
                    </div>
                    <h3 class="text-xl font-bold mb-2">Location Master</h3>
                    <p class="text-gray-400 text-sm mb-4">Click on the map to identify where countries are located. Master geography visually.</p>
                    <div class="flex items-center gap-2 text-sm text-yellow-400">
                        <span>Accuracy: 87%</span>
                        <i class="fas fa-bullseye"></i>
                    </div>
                </div>

                <!-- Capitals Module -->
                <div onclick="showModule('capitals')" class="glass rounded-2xl p-6 cursor-pointer glass-card group">
                    <div class="flex items-start justify-between mb-4">
                        <div class="w-14 h-14 rounded-2xl bg-pink-500/20 flex items-center justify-center text-pink-400 text-2xl group-hover:scale-110 transition">
                            <i class="fas fa-city"></i>
                        </div>
                        <span class="px-3 py-1 rounded-full bg-pink-500/20 text-pink-400 text-xs font-bold">195</span>
                    </div>
                    <h3 class="text-xl font-bold mb-2">Capital Cities</h3>
                    <p class="text-gray-400 text-sm mb-4">Master every capital city for quick country identification. Includes obscure territories.</p>
                    <div class="flex items-center gap-2 text-sm text-pink-400">
                        <span>Review 12 due</span>
                        <i class="fas fa-clock"></i>
                    </div>
                </div>

                <!-- Meta/Geoguessr Info Module -->
                <div onclick="showModule('meta')" class="glass rounded-2xl p-6 cursor-pointer glass-card group border-2 border-purple-500/30">
                    <div class="flex items-start justify-between mb-4">
                        <div class="w-14 h-14 rounded-2xl bg-purple-500/20 flex items-center justify-center text-purple-400 text-2xl group-hover:scale-110 transition">
                            <i class="fas fa-database"></i>
                        </div>
                        <span class="px-3 py-1 rounded-full bg-purple-500/20 text-purple-400 text-xs font-bold">INFO</span>
                    </div>
                    <h3 class="text-xl font-bold mb-2">GeoGuessr Meta</h3>
                    <p class="text-gray-400 text-sm mb-4">Coverage maps, camera generations, Trekker vs Car, official vs unofficial coverage</p>
                    <div class="flex items-center gap-2 text-sm text-purple-400">
                        <span>View Database</span>
                        <i class="fas fa-arrow-right"></i>
                    </div>
                </div>

                <!-- Detective Mode -->
                <div onclick="showModule('detective')" class="glass rounded-2xl p-6 cursor-pointer glass-card group md:col-span-2 lg:col-span-3 border-2 border-orange-500/30 relative overflow-hidden">
                    <div class="absolute inset-0 bg-gradient-to-r from-orange-500/5 to-red-500/5"></div>
                    <div class="absolute top-0 right-0 w-64 h-64 bg-orange-500/10 rounded-full -mr-32 -mt-32 blur-3xl"></div>
                    <div class="relative flex items-center gap-6">
                        <div class="w-20 h-20 rounded-2xl bg-gradient-to-br from-orange-400 to-red-500 flex items-center justify-center text-3xl animate-pulse">
                            <i class="fas fa-user-secret"></i>
                        </div>
                        <div class="flex-1">
                            <div class="flex items-center gap-3 mb-2">
                                <h3 class="text-2xl font-bold">Detective Mode</h3>
                                <span class="px-3 py-1 rounded-full bg-orange-500 text-white text-xs font-bold">HARD</span>
                            </div>
                            <p class="text-gray-300 mb-3">Advanced deduction training. Analyze driving side, license plates, sun position, vegetation, road signs, and camera types to pinpoint exact locations.</p>
                            <div class="flex items-center gap-4 text-sm">
                                <span class="text-orange-400"><i class="fas fa-star mr-1"></i> 3/5 Completed</span>
                                <span class="text-gray-400"><i class="fas fa-trophy mr-1"></i> Top 5% Score</span>
                            </div>
                        </div>
                        <button class="px-6 py-3 bg-orange-500 hover:bg-orange-600 rounded-xl font-bold transition">
                            Start Case <i class="fas fa-arrow-right ml-2"></i>
                        </button>
                    </div>
                </div>
            </div>
        </div>

        <!-- CHAPTERS MODULE - Expanded with Continents -->
        <div id="chapters" class="hidden max-w-6xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex items-center justify-between mb-8">
                <div>
                    <h2 class="text-3xl font-bold font-display mb-2">Course Chapters</h2>
                    <p class="text-gray-400">48 chapters covering all continents and advanced techniques</p>
                </div>
                <div class="flex items-center gap-3">
                    <div class="text-right">
                        <div class="text-2xl font-bold text-emerald-400">7/48</div>
                        <div class="text-sm text-gray-400">Completed</div>
                    </div>
                    <div class="w-16 h-16 relative">
                        <svg class="w-full h-full progress-ring" viewBox="0 0 36 36">
                            <path class="text-gray-800" d="M18 2.0845 a 15.9155 15.9155 0 0 1 0 31.831 a 15.9155 15.9155 0 0 1 0 -31.831" fill="none" stroke="currentColor" stroke-width="3"/>
                            <path class="text-emerald-500 progress-ring-circle" stroke-dasharray="15, 100" d="M18 2.0845 a 15.9155 15.9155 0 0 1 0 31.831 a 15.9155 15.9155 0 0 1 0 -31.831" fill="none" stroke="currentColor" stroke-width="3"/>
                        </svg>
                        <div class="absolute inset-0 flex items-center justify-center text-xs font-bold">15%</div>
                    </div>
                </div>
            </div>

            <!-- Chapter Navigation -->
            <div class="flex gap-2 mb-6 overflow-x-auto pb-2">
                <button onclick="filterChapters('all')" class="chapter-filter px-4 py-2 rounded-full bg-emerald-500 text-white text-sm font-medium whitespace-nowrap" data-filter="all">All</button>
                <button onclick="filterChapters('intro')" class="chapter-filter px-4 py-2 rounded-full bg-white/10 text-gray-300 text-sm font-medium whitespace-nowrap hover:bg-white/20" data-filter="intro">Introduction</button>
                <button onclick="filterChapters('europe')" class="chapter-filter px-4 py-2 rounded-full bg-white/10 text-gray-300 text-sm font-medium whitespace-nowrap hover:bg-white/20" data-filter="europe">🇪🇺 Europe</button>
                <button onclick="filterChapters('asia')" class="chapter-filter px-4 py-2 rounded-full bg-white/10 text-gray-300 text-sm font-medium whitespace-nowrap hover:bg-white/20" data-filter="asia">🇦🇸 Asia</button>
                <button onclick="filterChapters('africa')" class="chapter-filter px-4 py-2 rounded-full bg-white/10 text-gray-300 text-sm font-medium whitespace-nowrap hover:bg-white/20" data-filter="africa">🇦🇫 Africa</button>
                <button onclick="filterChapters('americas')" class="chapter-filter px-4 py-2 rounded-full bg-white/10 text-gray-300 text-sm font-medium whitespace-nowrap hover:bg-white/20" data-filter="americas">🇦🇲 Americas</button>
                <button onclick="filterChapters('oceania')" class="chapter-filter px-4 py-2 rounded-full bg-white/10 text-gray-300 text-sm font-medium whitespace-nowrap hover:bg-white/20" data-filter="oceania">🇴🇲 Oceania</button>
                <button onclick="filterChapters('advanced')" class="chapter-filter px-4 py-2 rounded-full bg-white/10 text-gray-300 text-sm font-medium whitespace-nowrap hover:bg-white/20" data-filter="advanced">🎯 Advanced</button>
            </div>

            <div class="space-y-4" id="chaptersList">
                <!-- INTRODUCTION SECTION -->
                <div class="chapter-group" data-category="intro">
                    <h3 class="text-lg font-bold text-emerald-400 mb-3 flex items-center gap-2">
                        <i class="fas fa-graduation-cap"></i> Introduction to GeoGuessr
                    </h3>
                    
                    <!-- Chapter 1 -->
                    <div class="glass rounded-2xl p-6 chapter-item mb-4" data-chapter="1">
                        <div class="flex items-start gap-4">
                            <input type="checkbox" class="chapter-check mt-1" checked onchange="toggleChapter(1)">
                            <div class="flex-1">
                                <div class="flex items-center gap-3 mb-2">
                                    <span class="px-3 py-1 rounded-full bg-emerald-500/20 text-emerald-400 text-xs font-bold">COMPLETED</span>
                                    <span class="text-xs text-gray-500">20 min</span>
                                </div>
                                <h3 class="text-xl font-bold mb-2">1. What is GeoGuessr? The Basics</h3>
                                <p class="text-gray-400 text-sm mb-3">Understanding the game interface, scoring system (0-5000 points), time limits, and different game modes (Classic, Battle Royale, Duels, Challenges)</p>
                                <div class="flex gap-2 flex-wrap">
                                    <span class="meta-tag sun"><i class="fas fa-gamepad"></i> Interface</span>
                                    <span class="meta-tag car"><i class="fas fa-star"></i> Scoring</span>
                                    <span class="meta-tag road"><i class="fas fa-clock"></i> Timing</span>
                                </div>
                            </div>
                        </div>
                    </div>

                    <!-- Chapter 2 -->
                    <div class="glass rounded-2xl p-6 chapter-item mb-4" data-chapter="2">
                        <div class="flex items-start gap-4">
                            <input type="checkbox" class="chapter-check mt-1" checked onchange="toggleChapter(2)">
                            <div class="flex-1">
                                <div class="flex items-center gap-3 mb-2">
                                    <span class="px-3 py-1 rounded-full bg-emerald-500/20 text-emerald-400 text-xs font-bold">COMPLETED</span>
                                    <span class="text-xs text-gray-500">30 min</span>
                                </div>
                                <h3 class="text-xl font-bold mb-2">2. The Sun & Compass: Your Best Friends</h3>
                                <p class="text-gray-400 text-sm mb-3">Using sun position to determine hemisphere and approximate latitude. Reading shadows for time of day. Using the compass for cardinal directions.</p>
                                <div class="flex gap-2 flex-wrap">
                                    <span class="meta-tag sun"><i class="fas fa-sun"></i> Sun Position</span>
                                    <span class="meta-tag car"><i class="fas fa-compass"></i> Navigation</span>
                                    <span class="meta-tag road"><i class="fas fa-globe"></i> Hemispheres</span>
                                </div>
                            </div>
                        </div>
                    </div>

                    <!-- Chapter 3 -->
                    <div class="glass rounded-2xl p-6 chapter-item mb-4" data-chapter="3">
                        <div class="flex items-start gap-4">
                            <input type="checkbox" class="chapter-check mt-1" checked onchange="toggleChapter(3)">
                            <div class="flex-1">
                                <div class="flex items-center gap-3 mb-2">
                                    <span class="px-3 py-1 rounded-full bg-emerald-500/20 text-emerald-400 text-xs font-bold">COMPLETED</span>
                                    <span class="text-xs text-gray-500">25 min</span>
                                </div>
                                <h3 class="text-xl font-bold mb-2">3. Which Countries Are IN GeoGuessr?</h3>
                                <p class="text-gray-400 text-sm mb-3">Complete list of 100+ countries with official Street View coverage. Understanding official vs unofficial coverage. Why some countries are missing (Germany, China, etc.)</p>
                                <div class="flex gap-2 flex-wrap">
                                    <span class="meta-tag plate"><i class="fas fa-list"></i> Coverage List</span>
                                    <span class="meta-tag car"><i class="fas fa-ban"></i> Exclusions</span>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- EUROPE SECTION -->
                <div class="chapter-group" data-category="europe">
                    <h3 class="text-lg font-bold text-blue-400 mb-3 flex items-center gap-2 mt-8">
                        <i class="fas fa-globe-europe"></i> Europe (Chapters 4-15)
                    </h3>

                    <!-- Chapter 4 -->
                    <div class="glass rounded-2xl p-6 chapter-item mb-4" data-chapter="4">
                        <div class="flex items-start gap-4">
                            <input type="checkbox" class="chapter-check mt-1" checked onchange="toggleChapter(4)">
                            <div class="flex-1">
                                <div class="flex items-center gap-3 mb-2">
                                    <span class="px-3 py-1 rounded-full bg-emerald-500/20 text-emerald-400 text-xs font-bold">COMPLETED</span>
                                    <span class="text-xs text-gray-500">35 min</span>
                                </div>
                                <h3 class="text-xl font-bold mb-2">4. Europe Overview: EU vs Non-EU</h3>
                                <p class="text-gray-400 text-sm mb-3">Quick identification: EU license plates (blue stripe), Euro currency signs, Schengen vs non-Schengen. European Union bollards and road standards.</p>
                                <div class="flex gap-2 flex-wrap">
                                    <span class="meta-tag plate"><i class="fas fa-id-card"></i> EU Plates</span>
                                    <span class="meta-tag road"><i class="fas fa-road"></i> Bollards</span>
                                    <span class="meta-tag car"><i class="fas fa-euro-sign"></i> Currency</span>
                                </div>
                            </div>
                        </div>
                    </div>

                    <!-- Chapter 5 -->
                    <div class="glass rounded-2xl p-6 chapter-item mb-4" data-chapter="5">
                        <div class="flex items-start gap-4">
                            <input type="checkbox" class="chapter-check mt-1" checked onchange="toggleChapter(5)">
                            <div class="flex-1">
                                <div class="flex items-center gap-3 mb-2">
                                    <span class="px-3 py-1 rounded-full bg-emerald-500/20 text-emerald-400 text-xs font-bold">COMPLETED</span>
                                    <span class="text-xs text-gray-500">40 min</span>
                                </div>
                                <h3 class="text-xl font-bold mb-2">5. The Nordic Countries</h3>
                                <p class="text-gray-400 text-sm mb-3">Norway, Sweden, Finland, Denmark, Iceland. Norwegian gen 3 cameras, Swedish orange plates, Finnish language, Danish cycling infrastructure.</p>
                                <div class="flex gap-2 flex-wrap">
                                    <span class="meta-tag car"><i class="fas fa-camera"></i> Gen 3 Cam</span>
                                    <span class="meta-tag plate"><i class="fas fa-palette"></i> Orange Plates</span>
                                    <span class="meta-tag sun"><i class="fas fa-snowflake"></i> Climate</span>
                                </div>
                            </div>
                        </div>
                    </div>

                    <!-- Chapter 6 -->
                    <div class="glass rounded-2xl p-6 chapter-item mb-4" data-chapter="6">
                        <div class="flex items-start gap-4">
                            <input type="checkbox" class="chapter-check mt-1" checked onchange="toggleChapter(6)">
                            <div class="flex-1">
                                <div class="flex items-center gap-3 mb-2">
                                    <span class="px-3 py-1 rounded-full bg-emerald-500/20 text-emerald-400 text-xs font-bold">COMPLETED</span>
                                    <span class="text-xs text-gray-500">35 min</span>
                                </div>
                                <h3 class="text-xl font-bold mb-2">6. UK & Ireland: Left Side Masters</h3>
                                <p class="text-gray-400 text-sm mb-3">Driving on the left, UK number plates (yellow rear, white front), Irish language signs, UK-specific road furniture, hedgerows vs stone walls.</p>
                                <div class="flex gap-2 flex-wrap">
                                    <span class="meta-tag road"><i class="fas fa-arrow-left"></i> Left Drive</span>
                                    <span class="meta-tag plate"><i class="fas fa-yellow"></i> Yellow Rear</span>
                                    <span class="meta-tag car"><i class="fas fa-language"></i> Gaelic</span>
                                </div>
                            </div>
                        </div>
                    </div>

                    <!-- Chapter 7 -->
                    <div class="glass rounded-2xl p-6 chapter-item mb-4" data-chapter="7">
                        <div class="flex items-start gap-4">
                            <input type="checkbox" class="chapter-check mt-1" checked onchange="toggleChapter(7)">
                            <div class="flex-1">
                                <div class="flex items-center gap-3 mb-2">
                                    <span class="px-3 py-1 rounded-full bg-emerald-500/20 text-emerald-400 text-xs font-bold">COMPLETED</span>
                                    <span class="text-xs text-gray-500">45 min</span>
                                </div>
                                <h3 class="text-xl font-bold mb-2">7. Eastern Europe: Cyrillic & Beyond</h3>
                                <p class="text-gray-400 text-sm mb-3">Russia, Ukraine, Poland, Baltic states. Cyrillic script identification, Russian gen 2/3/4 cameras, Ukrainian blue/yellow plates, Polish road numbers.</p>
                                <div class="flex gap-2 flex-wrap">
                                    <span class="meta-tag plate"><i class="fas fa-font"></i> Cyrillic</span>
                                    <span class="meta-tag car"><i class="fas fa-camera"></i> Gen 2/3/4</span>
                                    <span class="meta-tag road"><i class="fas fa-palette"></i> Blue/Yellow</span>
                                </div>
                            </div>
                        </div>
                    </div>

                    <!-- Chapter 8 (Current) -->
                    <div class="glass rounded-2xl p-6 chapter-item border-2 border-blue-500/50 bg-blue-500/5 mb-4" data-chapter="8">
                        <div class="flex items-start gap-4">
                            <input type="checkbox" class="chapter-check mt-1" onchange="toggleChapter(8)">
                            <div class="flex-1">
                                <div class="flex items-center gap-3 mb-2">
                                    <span class="px-3 py-1 rounded-full bg-blue-500 text-white text-xs font-bold animate-pulse">IN PROGRESS</span>
                                    <span class="text-xs text-gray-500">40 min</span>
                                </div>
                                <h3 class="text-xl font-bold mb-2">8. Southern Europe: Mediterranean Vibes</h3>
                                <p class="text-gray-400 text-sm mb-3">Spain, Portugal, Italy, Greece. Iberian peninsula differences, Italian language clues, Greek alphabet, Mediterranean vegetation and architecture.</p>
                                <div class="mt-4 p-4 rounded-xl bg-black/30">
                                    <div class="flex items-center gap-4 mb-3">
                                        <div class="w-20 h-20 rounded-lg bg-gray-800 flex items-center justify-center text-3xl">🏛️</div>
                                        <div class="flex-1">
                                            <div class="font-semibold mb-1">Quick Check: Which country has these roof tiles?</div>
                                            <div class="flex gap-2 mt-2">
                                                <button onclick="quickCheck(this, false)" class="px-3 py-1 rounded bg-white/10 hover:bg-white/20 text-sm transition">France</button>
                                                <button onclick="quickCheck(this, true)" class="px-3 py-1 rounded bg-white/10 hover:bg-white/20 text-sm transition">Spain</button>
                                                <button onclick="quickCheck(this, false)" class="px-3 py-1 rounded bg-white/10 hover:bg-white/20 text-sm transition">Italy</button>
                                            </div>
                                        </div>
                                    </div>
                                </div>
                            </div>
                            <button class="px-4 py-2 rounded-xl bg-blue-500 hover:bg-blue-600 transition font-semibold text-sm">
                                Continue
                            </button>
                        </div>
                    </div>

                    <!-- Locked Chapter 9 -->
                    <div class="glass rounded-2xl p-6 chapter-item locked mb-4" data-chapter="9">
                        <div class="locked-overlay absolute inset-0 rounded-2xl flex items-center justify-center">
                            <div class="text-center">
                                <i class="fas fa-lock text-4xl mb-2 text-gray-600"></i>
                                <p class="text-sm text-gray-400">Complete Chapter 8 to unlock</p>
                            </div>
                        </div>
                        <div class="flex items-start gap-4 opacity-30">
                            <input type="checkbox" class="chapter-check mt-1" disabled>
                            <div class="flex-1">
                                <h3 class="text-xl font-bold mb-2">9. Alpine Region: Switzerland, Austria, Mountains</h3>
                                <p class="text-gray-400 text-sm">Mountain geography, Swiss multilingual signs, Austrian bollards, Liechtenstein microstates</p>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- AFRICA SECTION -->
                <div class="chapter-group" data-category="africa">
                    <h3 class="text-lg font-bold text-yellow-600 mb-3 flex items-center gap-2 mt-8">
                        <i class="fas fa-globe-africa"></i> Africa (Chapters 16-22)
                    </h3>

                    <div class="glass rounded-2xl p-6 chapter-item locked mb-4" data-chapter="16">
                        <div class="locked-overlay absolute inset-0 rounded-2xl flex items-center justify-center">
                            <div class="text-center">
                                <i class="fas fa-lock text-4xl mb-2 text-gray-600"></i>
                                <p class="text-sm text-gray-400">Complete Europe chapters to unlock Africa</p>
                            </div>
                        </div>
                        <div class="flex items-start gap-4 opacity-30">
                            <input type="checkbox" class="chapter-check mt-1" disabled>
                            <div class="flex-1">
                                <h3 class="text-xl font-bold mb-2">16. Africa Overview: The Big Five</h3>
                                <p class="text-gray-400 text-sm">South Africa, Botswana, Kenya, Nigeria, Senegal. Understanding African coverage limitations, Trekker vs Car coverage.</p>
                            </div>
                        </div>
                    </div>

                    <div class="glass rounded-2xl p-6 chapter-item locked mb-4" data-chapter="17">
                        <div class="locked-overlay absolute inset-0 rounded-2xl flex items-center justify-center">
                            <div class="text-center">
                                <i class="fas fa-lock text-4xl mb-2 text-gray-600"></i>
                                <p class="text-sm text-gray-400">Locked</p>
                            </div>
                        </div>
                        <div class="flex items-start gap-4 opacity-30">
                            <input type="checkbox" class="chapter-check mt-1" disabled>
                            <div class="flex-1">
                                <h3 class="text-xl font-bold mb-2">17. South Africa: The Rainbow Nation</h3>
                                <p class="text-gray-400 text-sm">Left-hand drive, yellow plates, Afrikaans vs English, Western Cape vs Gauteng differences, unique Google car.</p>
                            </div>
                        </div>
                    </div>

                    <div class="glass rounded-2xl p-6 chapter-item locked mb-4" data-chapter="18">
                        <div class="locked-overlay absolute inset-0 rounded-2xl flex items-center justify-center">
                            <div class="text-center">
                                <i class="fas fa-lock text-4xl mb-2 text-gray-600"></i>
                                <p class="text-sm text-gray-400">Locked</p>
                            </div>
                        </div>
                        <div class="flex items-start gap-4 opacity-30">
                            <input type="checkbox" class="chapter-check mt-1" disabled>
                            <div class="flex-1">
                                <h3 class="text-xl font-bold mb-2">18. Kenya: The Snorkel Signature</h3>
                                <p class="text-gray-400 text-sm">The famous black snorkel, red soil, savanna landscapes, Rift Valley geography, wildlife conservation areas.</p>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- ASIA SECTION -->
                <div class="chapter-group" data-category="asia">
                    <h3 class="text-lg font-bold text-red-400 mb-3 flex items-center gap-2 mt-8">
                        <i class="fas fa-globe-asia"></i> Asia (Chapters 23-32)
                    </h3>
                    
                    <div class="glass rounded-2xl p-6 chapter-item locked mb-4" data-chapter="23">
                        <div class="locked-overlay absolute inset-0 rounded-2xl flex items-center justify-center">
                            <div class="text-center">
                                <i class="fas fa-lock text-4xl mb-2 text-gray-600"></i>
                                <p class="text-sm text-gray-400">Complete Africa chapters to unlock Asia</p>
                            </div>
                        </div>
                        <div class="flex items-start gap-4 opacity-30">
                            <input type="checkbox" class="chapter-check mt-1" disabled>
                            <div class="flex-1">
                                <h3 class="text-xl font-bold mb-2">23. Asia Overview: Scripts & Diversity</h3>
                                <p class="text-gray-400 text-sm">Japan, South Korea, India, Southeast Asia. Understanding Asian scripts, driving sides, camera generations.</p>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- AMERICAS SECTION -->
                <div class="chapter-group" data-category="americas">
                    <h3 class="text-lg font-bold text-green-400 mb-3 flex items-center gap-2 mt-8">
                        <i class="fas fa-globe-americas"></i> Americas (Chapters 33-42)
                    </h3>
                </div>

                <!-- OCEANIA SECTION -->
                <div class="chapter-group" data-category="oceania">
                    <h3 class="text-lg font-bold text-cyan-400 mb-3 flex items-center gap-2 mt-8">
                        <i class="fas fa-water"></i> Oceania (Chapters 43-46)
                    </h3>
                </div>

                <!-- ADVANCED SECTION -->
                <div class="chapter-group" data-category="advanced">
                    <h3 class="text-lg font-bold text-purple-400 mb-3 flex items-center gap-2 mt-8">
                        <i class="fas fa-rocket"></i> Advanced Techniques (Chapters 47-48)
                    </h3>
                    
                    <div class="glass rounded-2xl p-6 chapter-item locked mb-4" data-chapter="47">
                        <div class="locked-overlay absolute inset-0 rounded-2xl flex items-center justify-center">
                            <div class="text-center">
                                <i class="fas fa-lock text-4xl mb-2 text-gray-600"></i>
                                <p class="text-sm text-gray-400">Complete all continent chapters</p>
                            </div>
                        </div>
                        <div class="flex items-start gap-4 opacity-30">
                            <input type="checkbox" class="chapter-check mt-1" disabled>
                            <div class="flex-1">
                                <h3 class="text-xl font-bold mb-2">47. The Meta Game: Camera Generations</h3>
                                <p class="text-gray-400 text-sm">Gen 1, 2, 3, 4 identification. Trekker coverage. Unofficial coverage detection. Historical imagery.</p>
                            </div>
                        </div>
                    </div>

                    <div class="glass rounded-2xl p-6 chapter-item locked mb-4" data-chapter="48">
                        <div class="locked-overlay absolute inset-0 rounded-2xl flex items-center justify-center">
                            <div class="text-center">
                                <i class="fas fa-lock text-4xl mb-2 text-gray-600"></i>
                                <p class="text-sm text-gray-400">Complete all previous chapters</p>
                            </div>
                        </div>
                        <div class="flex items-start gap-4 opacity-30">
                            <input type="checkbox" class="chapter-check mt-1" disabled>
                            <div class="flex-1">
                                <h3 class="text-xl font-bold mb-2">48. World Championship Strategies</h3>
                                <p class="text-gray-400 text-sm">Speed techniques, 0.5s guesses, pattern recognition, mental maps, competitive mindsets.</p>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- PRACTICE MODULE -->
        <div id="practice" class="hidden max-w-6xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex items-center justify-between mb-8">
                <div>
                    <h2 class="text-3xl font-bold font-display mb-2">Practice Arena</h2>
                    <p class="text-gray-400">Train with real scenarios</p>
                </div>
                <div class="flex gap-2">
                    <button onclick="setPracticeMode('images')" class="px-4 py-2 rounded-lg bg-blue-500 text-white text-sm font-medium" id="btn-images">Images</button>
                    <button onclick="setPracticeMode('text')" class="px-4 py-2 rounded-lg bg-white/10 text-gray-300 hover:bg-white/20 text-sm font-medium" id="btn-text">Text Scenarios</button>
                </div>
            </div>

            <!-- Image Practice -->
            <div id="practice-images" class="glass rounded-3xl p-8">
                <div class="grid lg:grid-cols-2 gap-8">
                    <div class="space-y-4">
                        <div class="relative aspect-video rounded-2xl overflow-hidden bg-gray-800 group">
                            <div class="absolute inset-0 flex items-center justify-center bg-gradient-to-br from-gray-800 to-gray-900">
                                <div class="text-center">
                                    <i class="fas fa-street-view text-6xl text-gray-700 mb-4"></i>
                                    <p class="text-gray-500">Street View Image</p>
                                    <p class="text-sm text-gray-600 mt-2">Click to zoom</p>
                                </div>
                            </div>
                            <div class="absolute top-4 left-4 px-3 py-1 rounded-full bg-black/50 backdrop-blur text-xs">
                                <i class="fas fa-camera mr-1"></i> Round 1/5
                            </div>
                            <div class="absolute bottom-4 right-4 flex gap-2">
                                <button class="w-10 h-10 rounded-full bg-black/50 backdrop-blur flex items-center justify-center hover:bg-emerald-500/50 transition">
                                    <i class="fas fa-expand"></i>
                                </button>
                                <button class="w-10 h-10 rounded-full bg-black/50 backdrop-blur flex items-center justify-center hover:bg-emerald-500/50 transition">
                                    <i class="fas fa-lightbulb"></i>
                                </button>
                            </div>
                        </div>
                        
                        <div class="flex gap-2">
                            <button class="flex-1 py-3 rounded-xl bg-white/5 hover:bg-white/10 transition text-sm">
                                <i class="fas fa-arrow-left mr-2"></i>Previous
                            </button>
                            <button class="flex-1 py-3 rounded-xl bg-emerald-500/20 text-emerald-400 hover:bg-emerald-500/30 transition text-sm font-semibold">
                                <i class="fas fa-check mr-2"></i>Confirm Guess
                            </button>
                            <button class="flex-1 py-3 rounded-xl bg-white/5 hover:bg-white/10 transition text-sm">
                                Next<i class="fas fa-arrow-right ml-2"></i>
                            </button>
                        </div>
                    </div>

                    <div class="space-y-4">
                        <div class="glass rounded-xl p-4">
                            <h4 class="font-semibold mb-3 text-emerald-400">Available Clues</h4>
                            <div class="space-y-2">
                                <button onclick="revealClue(this)" class="w-full p-3 rounded-lg bg-white/5 hover:bg-white/10 transition text-left flex items-center justify-between group">
                                    <span class="text-sm">🚗 Google Car Type</span>
                                    <span class="text-xs text-gray-500 group-hover:text-emerald-400">Click to reveal</span>
                                </button>
                                <button onclick="revealClue(this)" class="w-full p-3 rounded-lg bg-white/5 hover:bg-white/10 transition text-left flex items-center justify-between group">
                                    <span class="text-sm">🛣️ Road Markings</span>
                                    <span class="text-xs text-gray-500 group-hover:text-emerald-400">Click to reveal</span>
                                </button>
                                <button onclick="revealClue(this)" class="w-full p-3 rounded-lg bg-white/5 hover:bg-white/10 transition text-left flex items-center justify-between group">
                                    <span class="text-sm">🌿 Vegetation</span>
                                    <span class="text-xs text-gray-500 group-hover:text-emerald-400">Click to reveal</span>
                                </button>
                            </div>
                        </div>

                        <div class="glass rounded-xl p-4">
                            <h4 class="font-semibold mb-3">Your Guess</h4>
                            <select class="w-full p-3 rounded-lg bg-black/30 border border-white/10 text-white mb-3">
                                <option>Select a country...</option>
                                <option>Kenya</option>
                                <option>South Africa</option>
                                <option>Nigeria</option>
                                <option>Botswana</option>
                            </select>
                            <button class="w-full py-3 rounded-lg bg-emerald-500 hover:bg-emerald-600 font-semibold transition">
                                Submit Answer
                            </button>
                        </div>

                        <div class="glass rounded-xl p-4 bg-yellow-500/5 border-yellow-500/20">
                            <div class="flex items-center gap-2 mb-2 text-yellow-400">
                                <i class="fas fa-lightbulb"></i>
                                <span class="font-semibold text-sm">Pro Tip</span>
                            </div>
                            <p class="text-sm text-gray-300">Look for the snorkel on the car roof - it's unique to Kenyan Street View vehicles!</p>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Text Practice (Hidden by default) -->
            <div id="practice-text" class="hidden glass rounded-3xl p-8">
                div class="max-w-3xl mx-auto text-center mb-8">
                    <div class="inline-block p-6 rounded-full bg-blue-500/10 mb-4">
                        <i class="fas fa-file-alt text-4xl text-blue-400"></i>
                    </div>
                    <h3 class="text-2xl font-bold mb-2">Text Scenario #42</h3>
                    <p class="text-gray-400">Read the description and identify the location</p>
                </div>

                <div class="glass rounded-2xl p-8 mb-6 bg-gradient-to-br from-white/5 to-white/0">
                    <p class="text-lg leading-relaxed text-gray-200 mb-6">
                        "You're on a paved road with <span class="text-emerald-400 font-semibold">yellow center lines</span>. The sun is positioned to your <span class="text-yellow-400 font-semibold">north</span> at 2 PM local time. You see a <span class="text-blue-400 font-semibold">Google car with a black snorkel</span> protrusion on the roof. The soil is distinctly <span class="text-red-400 font-semibold">reddish-orange</span>. There's a silver 4WD vehicle visible ahead acting as an escort."
                    </p>
                    
                    <div class="grid md:grid-cols-3 gap-4 text-sm">
                        <div class="p-4 rounded-lg bg-black/30">
                            <div class="text-gray-500 mb-1">Driving Side</div>
                            <div class="font-semibold">Left</div>
                        </div>
                        <div class="p-4 rounded-lg bg-black/30">
                            <div class="text-gray-500 mb-1">License Plate</div>
                            <div class="font-semibold">Yellow with black text</div>
                        </div>
                        <div class="p-4 rounded-lg bg-black/30">
                            <div class="text-gray-500 mb-1">Vegetation</div>
                            <div class="font-semibold">Savanna grass, scattered trees</div>
                        </div>
                    </div>
                </div>

                <div class="flex justify-center gap-4">
                    <button onclick="checkTextAnswer('Kenya')" class="px-8 py-4 rounded-xl bg-white/10 hover:bg-emerald-500/20 border-2 border-transparent hover:border-emerald-500 transition font-semibold text-lg">
                        Kenya
                    </button>
                    <button onclick="checkTextAnswer('South Africa')" class="px-8 py-4 rounded-xl bg-white/10 hover:bg-emerald-500/20 border-2 border-transparent hover:border-emerald-500 transition font-semibold text-lg">
                        South Africa
                    </button>
                    <button onclick="checkTextAnswer('Australia')" class="px-8 py-4 rounded-xl bg-white/10 hover:bg-emerald-500/20 border-2 border-transparent hover:border-emerald-500 transition font-semibold text-lg">
                        Australia
                    </button>
                </div>
            </div>
        </div>

        <!-- FLAGS MODULE -->
        <div id="flags" class="hidden max-w-6xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="text-center mb-8">
                <h2 class="text-3xl font-bold font-display mb-2">Flag Master</h2>
                <p class="text-gray-400">Identify flags instantly</p>
                <div class="mt-4 inline-flex items-center gap-2 px-4 py-2 rounded-full bg-orange-500/10 border border-orange-500/30">
                    <i class="fas fa-fire text-orange-400 streak-flame"></i>
                    <span class="text-orange-400 font-bold">Current Streak: <span id="flagStreak">0</span></span>
                </div>
            </div>

            <div class="max-w-2xl mx-auto">
                <div class="flashcard mb-8 cursor-pointer" onclick="this.classList.toggle('flipped')">
                    <div class="flashcard-inner">
                        <div class="flashcard-front glass rounded-2xl flex flex-col items-center justify-center p-8">
                            <div class="w-48 h-32 rounded-lg shadow-2xl mb-4 flex items-center justify-center text-6xl" id="flagDisplay">
                                🇰🇪
                            </div>
                            <p class="text-gray-400 text-sm">Click to reveal answer</p>
                        </div>
                        <div class="flashcard-back rounded-2xl flex flex-col items-center justify-center p-8">
                            <div class="text-4xl font-bold mb-2">Kenya</div>
                            <div class="text-emerald-200">East Africa</div>
                            <div class="mt-4 flex gap-2">
                                <button onclick="handleFlagResult(true)" class="px-6 py-2 rounded-full bg-white text-emerald-600 font-bold hover:scale-105 transition">✓ Got it</button>
                                <button onclick="handleFlagResult(false)" class="px-6 py-2 rounded-full bg-white/20 text-white font-bold hover:scale-105 transition">✗ Missed</button>
                            </div>
                        </div>
                    </div>
                </div>

                <div class="flex justify-center gap-4 mb-8">
                    <button onclick="prevFlag()" class="p-3 rounded-full bg-white/10 hover:bg-white/20 transition">
                        <i class="fas fa-arrow-left"></i>
                    </button>
                    <button onclick="shuffleFlags()" class="px-6 py-3 rounded-full bg-white/10 hover:bg-white/20 transition">
                        <i class="fas fa-random mr-2"></i>Shuffle
                    </button>
                    <button onclick="nextFlag()" class="p-3 rounded-full bg-white/10 hover:bg-white/20 transition">
                        <i class="fas fa-arrow-right"></i>
                    </button>
                </div>

                <div class="glass rounded-2xl p-6">
                    <h4 class="font-semibold mb-4">Flag Categories</h4>
                    <div class="flex flex-wrap gap-2">
                        <button class="px-4 py-2 rounded-full bg-emerald-500/20 text-emerald-400 text-sm font-medium">All</button>
                        <button class="px-4 py-2 rounded-full bg-white/5 text-gray-300 hover:bg-white/10 text-sm">Africa</button>
                        <button class="px-4 py-2 rounded-full bg-white/5 text-gray-300 hover:bg-white/10 text-sm">Europe</button>
                        <button class="px-4 py-2 rounded-full bg-white/5 text-gray-300 hover:bg-white/10 text-sm">Asia</button>
                        <button class="px-4 py-2 rounded-full bg-white/5 text-gray-300 hover:bg-white/10 text-sm">Americas</button>
                        <button class="px-4 py-2 rounded-full bg-white/5 text-gray-300 hover:bg-white/10 text-sm">Oceania</button>
                        <button class="px-4 py-2 rounded-full bg-white/5 text-gray-300 hover:bg-white/10 text-sm">Tricolor</button>
                        <button class="px-4 py-2 rounded-full bg-white/5 text-gray-300 hover:bg-white/10 text-sm">With Symbols</button>
                    </div>
                </div>
            </div>
        </div>

        <!-- LANGUAGES MODULE -->
        <div id="languages" class="hidden max-w-4xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="text-center mb-8">
                <h2 class="text-3xl font-bold font-display mb-2">Language Identifier</h2>
                <p class="text-gray-400">Recognize scripts and languages from street signs</p>
            </div>

            <div class="glass rounded-3xl p-8 mb-6">
                <div class="text-center mb-8">
                    <div class="text-4xl mb-4 font-bold tracking-wider" id="languageScript">こんにちは</div>
                    <p class="text-gray-400">What language is this?</p>
                </div>

                <div class="grid grid-cols-2 gap-4 mb-6">
                    <button onclick="checkLanguage('Japanese')" class="p-4 rounded-xl bg-white/5 hover:bg-emerald-500/20 border-2 border-transparent hover:border-emerald-500 transition text-left">
                        <div class="font-semibold">Japanese</div>
                        <div class="text-sm text-gray-400">Hiragana/Katakana/Kanji</div>
                    </button>
                    <button onclick="checkLanguage('Chinese')" class="p-4 rounded-xl bg-white/5 hover:bg-emerald-500/20 border-2 border-transparent hover:border-emerald-500 transition text-left">
                        <div class="font-semibold">Chinese</div>
                        <div class="text-sm text-gray-400">Simplified/Traditional</div>
                    </button>
                    <button onclick="checkLanguage('Korean')" class="p-4 rounded-xl bg-white/5 hover:bg-emerald-500/20 border-2 border-transparent hover:border-emerald-500 transition text-left">
                        <div class="font-semibold">Korean</div>
                        <div class="text-sm text-gray-400">Hangul script</div>
                    </button>
                    <button onclick="checkLanguage('Thai')" class="p-4 rounded-xl bg-white/5 hover:bg-emerald-500/20 border-2 border-transparent hover:border-emerald-500 transition text-left">
                        <div class="font-semibold">Thai</div>
                        <div class="text-sm text-gray-400">Thai alphabet</div>
                    </button>
                </div>

                <div class="glass rounded-xl p-4 bg-blue-500/5 border-blue-500/20">
                    <div class="flex items-start gap-3">
                        <i class="fas fa-info-circle text-blue-400 mt-1"></i>
                        <div>
                            <div class="font-semibold text-sm text-blue-400 mb-1">Hint</div>
                            <p class="text-sm text-gray-300">Look for the characteristic curved lines and lack of circles (unlike Korean). Japanese uses simpler characters than Chinese.</p>
                        </div>
                    </div>
                </div>
            </div>

            <div class="grid md:grid-cols-3 gap-4">
                <div class="glass rounded-xl p-4 text-center">
                    <div class="text-3xl mb-2">АБВ</div>
                    <div class="text-sm font-semibold">Cyrillic</div>
                    <div class="text-xs text-gray-400">Russia, Ukraine, etc.</div>
                </div>
                <div class="glass rounded-xl p-4 text-center">
                    <div class="text-3xl mb-2">العربية</div>
                    <div class="text-sm font-semibold">Arabic</div>
                    <div class="text-xs text-gray-400">Right-to-left script</div>
                </div>
                <div class="glass rounded-xl p-4 text-center">
                    <div class="text-3xl mb-2">अआइ</div>
                    <div class="text-sm font-semibold">Devanagari</div>
                    <div class="text-xs text-gray-400">India, Nepal</div>
                </div>
            </div>
        </div>

        <!-- LOCATIONS MODULE -->
        <div id="locations" class="hidden max-w-6xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex items-center justify-between mb-8">
                <div>
                    <h2 class="text-3xl font-bold font-display mb-2">Location Master</h2>
                    <p class="text-gray-400">Click on the map to identify countries</p>
                </div>
                <div class="text-right">
                    <div class="text-2xl font-bold text-emerald-400" id="locationScore">0</div>
                    <div class="text-sm text-gray-400">Points</div>
                </div>
            </div>

            <div class="grid lg:grid-cols-3 gap-6">
                <div class="lg:col-span-2">
                    <div class="glass rounded-3xl p-4 aspect-[4/3] relative overflow-hidden bg-blue-900/20">
                        <!-- Simplified World Map SVG -->
                        <svg viewBox="0 0 1000 500" class="w-full h-full">
                            <!-- Simplified world map paths -->
                            <path d="M150,100 Q200,80 250,100 T350,150" fill="none" stroke="rgba(255,255,255,0.2)" stroke-width="2"/>
                            <path d="M450,80 Q550,60 650,80 T850,120" fill="none" stroke="rgba(255,255,255,0.2)" stroke-width="2"/>
                            <path d="M100,200 Q200,180 300,200 T500,250" fill="none" stroke="rgba(255,255,255,0.2)" stroke-width="2"/>
                            <path d="M600,200 Q700,180 800,200 T950,250" fill="none" stroke="rgba(255,255,255,0.2)" stroke-width="2"/>
                            
                            <!-- Clickable points -->
                            <circle cx="200" cy="150" r="8" class="map-point" onclick="selectLocation(this, 'Brazil')" data-country="Brazil"/>
                            <circle cx="500" cy="100" r="8" class="map-point" onclick="selectLocation(this, 'Russia')" data-country="Russia"/>
                            <circle cx="700" cy="200" r="8" class="map-point" onclick="selectLocation(this, 'China')" data-country="China"/>
                            <circle cx="550" cy="180" r="8" class="map-point" onclick="selectLocation(this, 'Kazakhstan')" data-country="Kazakhstan"/>
                            <circle cx="480" cy="220" r="8" class="map-point" onclick="selectLocation(this, 'India')" data-country="India"/>
                            <circle cx="150" cy="120" r="8" class="map-point" onclick="selectLocation(this, 'USA')" data-country="USA"/>
                            <circle cx="520" cy="300" r="8" class="map-point" onclick="selectLocation(this, 'Australia')" data-country="Australia"/>
                        </svg>
                        
                        <div class="absolute bottom-4 left-4 glass rounded-lg px-4 py-2">
                            <span class="text-sm text-gray-400">Target: </span>
                            <span class="font-bold text-emerald-400 text-lg" id="targetCountry">Brazil</span>
                        </div>
                    </div>
                </div>

                <div class="space-y-4">
                    <div class="glass rounded-2xl p-6">
                        <h4 class="font-semibold mb-4">Instructions</h4>
                        <ul class="space-y-2 text-sm text-gray-400">
                            <li class="flex items-start gap-2">
                                <i class="fas fa-mouse-pointer text-emerald-400 mt-1"></i>
                                <span>Click on the green dots to select a country</span>
                            </li>
                            <li class="flex items-start gap-2">
                                <i class="fas fa-bullseye text-emerald-400 mt-1"></i>
                                <span>Closer to center = more points</span>
                            </li>
                            <li class="flex items-start gap-2">
                                <i class="fas fa-clock text-emerald-400 mt-1"></i>
                                <span>You have 10 seconds per round</span>
                            </li>
                        </ul>
                    </div>

                    <div class="glass rounded-2xl p-6">
                        <h4 class="font-semibold mb-4">Recent Activity</h4>
                        <div class="space-y-2">
                            <div class="flex items-center justify-between p-2 rounded bg-emerald-500/10">
                                <span class="text-sm">Brazil</span>
                                <span class="text-emerald-400 font-bold">+100</span>
                            </div>
                            <div class="flex items-center justify-between p-2 rounded bg-red-500/10">
                                <span class="text-sm">Russia</span>
                                <span class="text-red-400 font-bold">+0</span>
                            </div>
                            <div class="flex items-center justify-between p-2 rounded bg-emerald-500/10">
                                <span class="text-sm">Australia</span>
                                <span class="text-emerald-400 font-bold">+85</span>
                            </div>
                        </div>
                    </div>

                    <button onclick="nextLocationTarget()" class="w-full py-4 rounded-xl bg-emerald-500 hover:bg-emerald-600 font-bold transition">
                        Next Target <i class="fas fa-arrow-right ml-2"></i>
                    </button>
                </div>
            </div>
        </div>

        <!-- CAPITALS MODULE -->
        <div id="capitals" class="hidden max-w-4xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="text-center mb-8">
                <h2 class="text-3xl font-bold font-display mb-2">Capital Cities</h2>
                <p class="text-gray-400">Master capitals for instant country identification</p>
            </div>

            <div class="glass rounded-3xl p-8 mb-6">
                <div class="text-center mb-8">
                    <div class="inline-block p-4 rounded-full bg-gradient-to-br from-purple-500 to-pink-500 mb-4 text-4xl" id="capitalCountry">
                        🇫🇷
                    </div>
                    <h3 class="text-2xl font-bold mb-2">France</h3>
                    <p class="text-gray-400 mb-6">What is the capital city?</p>
                </div>

                <div class="grid grid-cols-2 gap-4 mb-6">
                    <button onclick="checkCapital('Lyon')" class="p-4 rounded-xl bg-white/5 hover:bg-white/10 transition font-semibold text-lg">Lyon</button>
                    <button onclick="checkCapital('Marseille')" class="p-4 rounded-xl bg-white/5 hover:bg-white/10 transition font-semibold text-lg">Marseille</button>
                    <button onclick="checkCapital('Paris')" class="p-4 rounded-xl bg-white/5 hover:bg-white/10 transition font-semibold text-lg">Paris</button>
                    <button onclick="checkCapital('Nice')" class="p-4 rounded-xl bg-white/5 hover:bg-white/10 transition font-semibold text-lg">Nice</button>
                </div>

                <div class="flex justify-center">
                    <button onclick="nextCapital()" class="px-8 py-3 rounded-full bg-white/10 hover:bg-white/20 transition">
                        <i class="fas fa-forward mr-2"></i>Skip
                    </button>
                </div>
            </div>

            <div class="glass rounded-2xl p-6">
                <h4 class="font-semibold mb-4">Learning Stats</h4>
                <div class="grid grid-cols-3 gap-4 text-center">
                    <div>
                        <div class="text-2xl font-bold text-emerald-400">156</div>
                        <div class="text-xs text-gray-400">Learned</div>
                    </div>
                    <div>
                        <div class="text-2xl font-bold text-yellow-400">39</div>
                        <div class="text-xs text-gray-400">Learning</div>
                    </div>
                    <div>
                        <div class="text-2xl font-bold text-gray-400">0</div>
                        <div class="text-xs text-gray-400">Not Started</div>
                    </div>
                </div>
            </div>
        </div>

        <!-- DETECTIVE MODE -->
        <div id="detective" class="hidden max-w-5xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="text-center mb-8">
                <div class="inline-flex items-center gap-2 px-4 py-2 rounded-full bg-orange-500/10 border border-orange-500/30 mb-4">
                    <i class="fas fa-user-secret text-orange-400"></i>
                    <span class="text-orange-400 font-bold">CASE #247</span>
                </div>
                <h2 class="text-3xl font-bold font-display mb-2">Detective Mode</h2>
                <p class="text-gray-400">Use all available clues to pinpoint the exact location</p>
            </div>

            <div class="grid lg:grid-cols-2 gap-6 mb-6">
                <!-- Clues Panel -->
                <div class="space-y-3">
                    <div class="glass rounded-xl p-4 clue-card cursor-pointer" onclick="useClue(this, 'driving')">
                        <div class="flex items-center justify-between mb-2">
                            <div class="flex items-center gap-3">
                                <i class="fas fa-car text-blue-400"></i>
                                <span class="font-semibold">Driving Side</span>
                            </div>
                            <span class="text-xs text-gray-500">Cost: 50 pts</span>
                        </div>
                        <p class="text-sm text-gray-400 clue-content hidden">They drive on the <span class="text-white font-bold">LEFT</span> side of the road</p>
                    </div>

                    <div class="glass rounded-xl p-4 clue-card cursor-pointer" onclick="useClue(this, 'plate')">
                        <div class="flex items-center justify-between mb-2">
                            <div class="flex items-center gap-3">
                                <i class="fas fa-id-card text-green-400"></i>
                                <span class="font-semibold">License Plate</span>
                            </div>
                            <span class="text-xs text-gray-500">Cost: 75 pts</span>
                        </div>
                        <p class="text-sm text-gray-400 clue-content hidden">Yellow plate with <span class="text-white font-bold">BLACK</span> lettering</p>
                    </div>

                    <div class="glass rounded-xl p-4 clue-card cursor-pointer" onclick="useClue(this, 'sun')">
                        <div class="flex items-center justify-between mb-2">
                            <div class="flex items-center gap-3">
                                <i class="fas fa-sun text-yellow-400"></i>
                                <span class="font-semibold">Sun Position</span>
                            </div>
                            <span class="text-xs text-gray-500">Cost: 100 pts</span>
                        </div>
                        <p class="text-sm text-gray-400 clue-content hidden">Sun is in the <span class="text-white font-bold">NORTH</span> at noon (Southern Hemisphere)</p>
                    </div>

                    <div class="glass rounded-xl p-4 clue-card cursor-pointer" onclick="useClue(this, 'car')">
                        <div class="flex items-center justify-between mb-2">
                            <div class="flex items-center gap-3">
                                <i class="fas fa-camera text-purple-400"></i>
                                <span class="font-semibold">Google Car</span>
                            </div>
                            <span class="text-xs text-gray-500">Cost: 125 pts</span>
                        </div>
                        <p class="text-sm text-gray-400 clue-content hidden">Black <span class="text-white font-bold">SNORKEL</span> visible on roof</p>
                    </div>

                    <div class="glass rounded-xl p-4 clue-card cursor-pointer" onclick="useClue(this, 'road')">
                        <div class="flex items-center justify-between mb-2">
                            <div class="flex items-center gap-3">
                                <i class="fas fa-road text-red-400"></i>
                                <span class="font-semibold">Road Markings</span>
                            </div>
                            <span class="text-xs text-gray-500">Cost: 75 pts</span>
                        </div>
                        <p class="text-sm text-gray-400 clue-content hidden"><span class="text-white font-bold">YELLOW</span> center lines</p>
                    </div>

                    <div class="glass rounded-xl p-4 clue-card cursor-pointer" onclick="useClue(this, 'vegetation')">
                        <div class="flex items-center justify-between mb-2">
                            <div class="flex items-center gap-3">
                                <i class="fas fa-leaf text-green-400"></i>
                                <span class="font-semibold">Vegetation</span>
                            </div>
                            <span class="text-xs text-gray-500">Cost: 50 pts</span>
                        </div>
                        <p class="text-sm text-gray-400 clue-content hidden"><span class="text-white font-bold">ACACIA</span> trees and savanna grassland</p>
                    </div>

                    <div class="glass rounded-xl p-4 clue-card cursor-pointer" onclick="useClue(this, 'language')">
                        <div class="flex items-center justify-between mb-2">
                            <div class="flex items-center gap-3">
                                <i class="fas fa-language text-pink-400"></i>
                                <span class="font-semibold">Language</span>
                            </div>
                            <span class="text-xs text-gray-500">Cost: 100 pts</span>
                        </div>
                        <p class="text-sm text-gray-400 clue-content hidden">Signs in <span class="text-white font-bold">ENGLISH</span> and <span class="text-white font-bold">SWAHILI</span></p>
                    </div>
                </div>

                <!-- Investigation Board -->
                <div class="glass rounded-2xl p-6">
                    <h4 class="font-semibold mb-4 flex items-center gap-2">
                        <i class="fas fa-clipboard-list text-orange-400"></i>
                        Investigation Board
                    </h4>
                    
                    <div class="space-y-4 mb-6">
                        <div class="p-3 rounded-lg bg-black/30 border border-white/5">
                            <div class="text-xs text-gray-500 mb-1">Current Score</div>
                            <div class="text-2xl font-bold text-orange-400" id="detectiveScore">500</div>
                        </div>

                        <div class="p-3 rounded-lg bg-black/30 border border-white/5">
                            <div class="text-xs text-gray-500 mb-1">Clues Used</div>
                            <div class="flex gap-2 mt-2 flex-wrap" id="usedClues">
                                <span class="text-xs text-gray-600">None yet</span>
                            </div>
                        </div>

                        <div class="p-3 rounded-lg bg-black/30 border border-white/5">
                            <div class="text-xs text-gray-500 mb-1">Deduction Notes</div>
                            <textarea class="w-full bg-transparent border border-white/10 rounded-lg p-2 text-sm mt-2" rows="3" placeholder="Write your notes here..."></textarea>
                        </div>
                    </div>

                    <div class="space-y-2">
                        <div class="text-xs text-gray-500 mb-2">Your Guess:</div>
                        <select class="w-full p-3 rounded-lg bg-black/30 border border-white/10 text-white mb-3">
                            <option>Select country...</option>
                            <option>South Africa</option>
                            <option>Kenya</option>
                            <option>Japan</option>
                            <option>Australia</option>
                            <option>United Kingdom</option>
                            <option>India</option>
                            <option>Botswana</option>
                            <option>Tanzania</option>
                        </select>
                        
                        <div class="grid grid-cols-2 gap-2">
                            <button onclick="submitDetectiveGuess()" class="py-3 rounded-lg bg-orange-500 hover:bg-orange-600 font-bold transition">
                                Submit Guess
                            </button>
                            <button onclick="requestHint()" class="py-3 rounded-lg bg-white/10 hover:bg-white/20 transition">
                                <i class="fas fa-lightbulb mr-2"></i>Hint (-25 pts)
                            </button>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Previous Cases -->
            <div class="glass rounded-2xl p-6">
                <h4 class="font-semibold mb-4">Case History</h4>
                <div class="grid md:grid-cols-3 gap-4">
                    <div class="p-4 rounded-xl bg-emerald-500/10 border border-emerald-500/30">
                        <div class="flex items-center justify-between mb-2">
                            <span class="text-xs text-emerald-400 font-bold">SOLVED</span>
                            <span class="text-xs text-gray-500">#246</span>
                        </div>
                        <div class="font-semibold mb-1">Botswana</div>
                        <div class="text-xs text-gray-400">Score: 425/500</div>
                    </div>
                    <div class="p-4 rounded-xl bg-emerald-500/10 border border-emerald-500/30">
                        <div class="flex items-center justify-between mb-2">
                            <span class="text-xs text-emerald-400 font-bold">SOLVED</span>
                            <span class="text-xs text-gray-500">#245</span>
                        </div>
                        <div class="font-semibold mb-1">Chile</div>
                        <div class="text-xs text-gray-400">Score: 380/500</div>
                    </div>
                    <div class="p-4 rounded-xl bg-red-500/10 border border-red-500/30">
                        <div class="flex items-center justify-between mb-2">
                            <span class="text-xs text-red-400 font-bold">FAILED</span>
                            <span class="text-xs text-gray-500">#244</span>
                        </div>
                        <div class="font-semibold mb-1">Lesotho</div>
                        <div class="text-xs text-gray-400">Guessed: South Africa</div>
                    </div>
                </div>
            </div>
        </div>

        <!-- META/GEOGUESSR INFO MODULE -->
        <div id="meta" class="hidden max-w-6xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="mb-8">
                <h2 class="text-3xl font-bold font-display mb-2">GeoGuessr Meta Database</h2>
                <p class="text-gray-400">Complete information about coverage, cameras, and official data</p>
            </div>

            <!-- Coverage Overview -->
            <div class="glass rounded-2xl p-6 mb-6">
                <h3 class="text-xl font-bold mb-4 flex items-center gap-2">
                    <i class="fas fa-globe text-emerald-400"></i>
                    Official Coverage Map
                </h3>
                <p class="text-gray-400 mb-4 text-sm">
                    GeoGuessr uses Google Street View coverage. As of 2024, there are approximately <span class="text-emerald-400 font-bold">100+ countries</span> with official coverage.
                    Some countries have partial coverage or only Trekker (pedestrian) coverage.
                </p>
                
                <div class="grid md:grid-cols-2 lg:grid-cols-4 gap-4">
                    <div class="glass rounded-xl p-4 text-center">
                        <div class="text-3xl font-bold text-emerald-400 mb-1">100+</div>
                        <div class="text-xs text-gray-400">Countries with Coverage</div>
                    </div>
                    <div class="glass rounded-xl p-4 text-center">
                        <div class="text-3xl font-bold text-blue-400 mb-1">Gen 4</div>
                        <div class="text-xs text-gray-400">Latest Camera</div>
                    </div>
                    <div class="glass rounded-xl p-4 text-center">
                        <div class="text-3xl font-bold text-yellow-400 mb-1">Trekker</div>
                        <div class="text-xs text-gray-400">Backpack Camera</div>
                    </div>
                    <div class="glass rounded-xl p-4 text-center">
                        <div class="text-3xl font-bold text-red-400 mb-1">None</div>
                        <div class="text-xs text-gray-400">China, Germany, etc.</div>
                    </div>
                </div>
            </div>

            <!-- Countries In/Out -->
            <div class="grid md:grid-cols-2 gap-6 mb-6">
                <div class="glass rounded-2xl p-6">
                    <h3 class="text-lg font-bold mb-4 text-emerald-400">✓ Countries IN GeoGuessr</h3>
                    <div class="space-y-2 max-h-64 overflow-y-auto pr-2">
                        <div class="flex items-center justify-between p-2 rounded bg-white/5">
                            <span class="text-sm">🇺🇸 United States</span>
                            <span class="text-xs text-gray-500">Full coverage</span>
                        </div>
                        <div class="flex items-center justify-between p-2 rounded bg-white/5">
                            <span class="text-sm">🇯🇵 Japan</span>
                            <span class="text-xs text-gray-500">Full coverage</span>
                        </div>
                        <div class="flex items-center justify-between p-2 rounded bg-white/5">
                            <span class="text-sm">🇧🇷 Brazil</span>
                            <span class="text-xs text-gray-500">Major cities</span>
                        </div>
                        <div class="flex items-center justify-between p-2 rounded bg-white/5">
                            <span class="text-sm">🇦🇺 Australia</span>
                            <span class="text-xs text-gray-500">Full coverage</span>
                        </div>
                        <div class="flex items-center justify-between p-2 rounded bg-white/5">
                            <span class="text-sm">🇷🇺 Russia</span>
                            <span class="text-xs text-gray-500">Major cities</span>
                        </div>
                        <div class="flex items-center justify-between p-2 rounded bg-white/5">
                            <span class="text-sm">🇿🇦 South Africa</span>
                            <span class="text-xs text-gray-500">Full coverage</span>
                        </div>
                        <div class="flex items-center justify-between p-2 rounded bg-white/5">
                            <span class="text-sm">🇰🇪 Kenya</span>
                            <span class="text-xs text-gray-500">Trekker + Car</span>
                        </div>
                        <div class="flex items-center justify-between p-2 rounded bg-white/5">
                            <span class="text-sm">🇫🇷 France</span>
                            <span class="text-xs text-gray-500">Full coverage</span>
                        </div>
                        <div class="flex items-center justify-between p-2 rounded bg-white/5">
                            <span class="text-sm">🇮🇳 India</span>
                            <span class="text-xs text-gray-500">Major cities</span>
                        </div>
                        <div class="text-xs text-gray-500 text-center pt-2">... and 90+ more</div>
                    </div>
                </div>

                <div class="glass rounded-2xl p-6">
                    <h3 class="text-lg font-bold mb-4 text-red-400">✗ Countries NOT in GeoGuessr</h3>
                    <div class="space-y-2">
                        <div class="p-3 rounded bg-red-500/10 border border-red-500/20">
                            <div class="flex items-center justify-between mb-1">
                                <span class="font-semibold">🇨🇳 China</span>
                                <span class="text-xs text-red-400">Banned</span>
                            </div>
                            <p class="text-xs text-gray-400">Google services blocked. No Street View.</p>
                        </div>
                        <div class="p-3 rounded bg-red-500/10 border border-red-500/20">
                            <div class="flex items-center justify-between mb-1">
                                <span class="font-semibold">🇩🇪 Germany</span>
                                <span class="text-xs text-yellow-400">Limited</span>
                            </div>
                            <p class="text-xs text-gray-400">Privacy laws restrict Street View. Only major cities, often blurred.</p>
                        </div>
                        <div class="p-3 rounded bg-red-500/10 border border-red-500/20">
                            <div class="flex items-center justify-between mb-1">
                                <span class="font-semibold">🇰🇵 North Korea</span>
                                <span class="text-xs text-red-400">No coverage</span>
                            </div>
                            <p class="text-xs text-gray-400">No Google Street View available.</p>
                        </div>
                        <div class="p-3 rounded bg-red-500/10 border border-red-500/20">
                            <div class="flex items-center justify-between mb-1">
                                <span class="font-semibold">🇦🇶 Antarctica</span>
                                <span class="text-xs text-yellow-400">Trekker only</span>
                            </div>
                            <p class="text-xs text-gray-400">Only specific tourist paths covered.</p>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Camera Generations -->
            <div class="glass rounded-2xl p-6 mb-6">
                <h3 class="text-xl font-bold mb-4">Google Camera Generations</h3>
                <div class="grid md:grid-cols-4 gap-4">
                    <div class="glass rounded-xl p-4">
                        <div class="text-2xl mb-2">📷</div>
                        <div class="font-bold mb-1">Gen 1 (2007-2009)</div>
                        <div class="text-xs text-gray-400 mb-2">Low quality, visible camera ring on car roof</div>
                        <div class="text-xs text-emerald-400">Found in: USA, Australia early coverage</div>
                    </div>
                    <div class="glass rounded-xl p-4">
                        <div class="text-2xl mb-2">📸</div>
                        <div class="font-bold mb-1">Gen 2 (2009-2017)</div>
                        <div class="text-xs text-gray-400 mb-2">Better quality, smaller camera cluster</div>
                        <div class="text-xs text-emerald-400">Most common worldwide</div>
                    </div>
                    <div class="glass rounded-xl p-4">
                        <div class="text-2xl mb-2">🎥</div>
                        <div class="font-bold mb-1">Gen 3 (2017-2022)</div>
                        <div class="text-xs text-gray-400 mb-2">High quality, tall black antenna</div>
                        <div class="text-xs text-emerald-400">Europe, Japan, updated areas</div>
                    </div>
                    <div class="glass rounded-xl p-4 border-2 border-emerald-500/30">
                        <div class="text-2xl mb-2">🎬</div>
                        <div class="font-bold mb-1">Gen 4 (2022+)</div>
                        <div class="text-xs text-gray-400 mb-2">Highest quality, sleek design</div>
                        <div class="text-xs text-emerald-400">New coverage areas</div>
                    </div>
                </div>
            </div>

            <!-- Sun Position Guide -->
            <div class="glass rounded-2xl p-6">
                <h3 class="text-xl font-bold mb-4 flex items-center gap-2">
                    <i class="fas fa-sun text-yellow-400"></i>
                    Sun Position Guide
                </h3>
                <div class="grid md:grid-cols-2 gap-6">
                    <div>
                        <h4 class="font-semibold mb-2 text-emerald-400">Northern Hemisphere</h4>
                        <ul class="space-y-2 text-sm text-gray-300">
                            <li>• Sun is in the SOUTH at noon</li>
                            <li>• Shadows point NORTH at midday</li>
                            <li>• Summer: High sun, short shadows</li>
                            <li>• Winter: Low sun, long shadows</li>
                        </ul>
                    </div>
                    <div>
                        <h4 class="font-semibold mb-2 text-emerald-400">Southern Hemisphere</h4>
                        <ul class="space-y-2 text-sm text-gray-300">
                            <li>• Sun is in the NORTH at noon</li>
                            <li>• Shadows point SOUTH at midday</li>
                            <li>• Seasons reversed from Northern</li>
                            <li>• December = Summer, June = Winter</li>
                        </ul>
                    </div>
                </div>
                <div class="mt-4 p-4 rounded-xl bg-yellow-500/10 border border-yellow-500/20">
                    <p class="text-sm text-yellow-200">
                        <i class="fas fa-lightbulb mr-2"></i>
                        <strong>Pro Tip:</strong> If the sun is in the north, you're in the Southern Hemisphere (Australia, South Africa, most of South America, etc.)
                    </p>
                </div>
            </div>
        </div>

    </main>

    <!-- Success Modal -->
    <div id="successModal" class="hidden fixed inset-0 z-50 flex items-center justify-center bg-black/80 backdrop-blur-sm">
        <div class="glass rounded-3xl p-8 max-w-md w-full mx-4 text-center animate-celebrate">
            <div class="w-20 h-20 rounded-full bg-emerald-500 flex items-center justify-center mx-auto mb-4 text-4xl">
                <i class="fas fa-check text-white"></i>
            </div>
            <h3 class="text-2xl font-bold mb-2">Correct!</h3>
            <p class="text-gray-400 mb-6" id="successMessage">Great job identifying the location!</p>
            <div class="flex justify-center gap-4">
                <button onclick="closeModal()" class="px-6 py-3 rounded-xl bg-white/10 hover:bg-white/20 transition">Review</button>
                <button onclick="nextChallenge()" class="px-6 py-3 rounded-xl bg-emerald-500 hover:bg-emerald-600 font-bold transition">Next <i class="fas fa-arrow-right ml-2"></i></button>
            </div>
        </div>
    </div>

    <script>
        // Global State
        let currentStreak = 0;
        let totalScore = 0;
        let currentFlagIndex = 0;
        let detectiveScore = 500;
        let usedCluesList = [];
        let currentUser = null;
        let trialDaysLeft = 7;
        let selectedRegion = 'EU';
        
        // Pricing data by region
        const pricing = {
            EU: { monthly: '€11.99', yearly: '€7.99', yearlyTotal: '€95.88', currency: '€' },
            US: { monthly: '$12.99', yearly: '$8.99', yearlyTotal: '$107.88', currency: '$' },
            UK: { monthly: '£10.99', yearly: '£7.49', yearlyTotal: '£89.88', currency: '£' },
            CA: { monthly: 'CA$16.99', yearly: 'CA$11.99', yearlyTotal: 'CA$143.88', currency: 'CA$' },
            AU: { monthly: 'AU$18.99', yearly: 'AU$12.99', yearlyTotal: 'AU$155.88', currency: 'AU$' },
            JP: { monthly: '¥1,500', yearly: '¥1,000', yearlyTotal: '¥12,000', currency: '¥' }
        };

        // Auth Functions
        function selectLanguage(lang) {
            document.querySelectorAll('.lang-btn').forEach(btn => {
                btn.classList.remove('bg-emerald-500/20', 'border-emerald-500');
                btn.classList.add('bg-white/5', 'border-transparent');
            });
            document.querySelector(`[data-lang="${lang}"]`).classList.remove('bg-white/5', 'border-transparent');
            document.querySelector(`[data-lang="${lang}"]`).classList.add('bg-emerald-500/20', 'border-emerald-500');
            localStorage.setItem('selectedLanguage', lang);
        }

        document.getElementById('loginForm').addEventListener('submit', function(e) {
            e.preventDefault();
            const email = this.querySelector('input[type="email"]').value;
            const name = email.split('@')[0];
            
            currentUser = {
                email: email,
                name: name.charAt(0).toUpperCase() + name.slice(1),
                language: localStorage.getItem('selectedLanguage') || 'en',
                trialStart: new Date().toISOString()
            };
            
            localStorage.setItem('geoguessr_user', JSON.stringify(currentUser));
            closeAuthModal();
            updateUserUI();
        });

        function closeAuthModal() {
            document.getElementById('authModal').classList.add('hidden');
        }

        function updateUserUI() {
            if (currentUser) {
                document.getElementById('userInitials').textContent = currentUser.name.substring(0, 2).toUpperCase();
                document.getElementById('userNameDisplay').textContent = currentUser.name;
                document.getElementById('userEmailDisplay').textContent = currentUser.email;
                document.getElementById('welcomeName').textContent = currentUser.name;
            }
        }

        function logout() {
            localStorage.removeItem('geoguessr_user');
            location.reload();
        }

        // Payment Functions
        function showPaymentModal() {
            document.getElementById('paymentModal').classList.remove('hidden');
        }

        function closePaymentModal() {
            document.getElementById('paymentModal').classList.add('hidden');
        }

        function setRegion(region) {
            selectedRegion = region;
            const prices = pricing[region];
            
            document.getElementById('monthlyPrice').textContent = prices.monthly;
            document.getElementById('yearlyPrice').textContent = prices.yearly;
            document.getElementById('yearlyTotal').textContent = prices.yearlyTotal;
            
            document.querySelectorAll('.region-btn').forEach(btn => {
                btn.classList.remove('bg-emerald-500', 'text-white');
                btn.classList.add('bg-white/10', 'text-gray-300');
            });
            document.querySelector(`[data-region="${region}"]`).classList.remove('bg-white/10', 'text-gray-300');
            document.querySelector(`[data-region="${region}"]`).classList.add('bg-emerald-500', 'text-white');
        }

        function subscribe(plan) {
            alert(`Redirecting to payment processor for ${plan} plan in ${selectedRegion}...`);
            // Here you would integrate with Stripe/PayPal
        }

        // Navigation
        function showDashboard() {
            hideAllModules();
            document.getElementById('dashboard').classList.remove('hidden');
        }

        function showModule(moduleName) {
            hideAllModules();
            document.getElementById(moduleName).classList.remove('hidden');
            
            // Update nav active states
            document.querySelectorAll('.nav-btn').forEach(btn => {
                btn.classList.remove('text-white', 'bg-white/10');
                btn.classList.add('text-gray-300');
            });
        }

        function hideAllModules() {
            ['dashboard', 'chapters', 'practice', 'flags', 'languages', 'locations', 'capitals', 'detective', 'meta'].forEach(id => {
                document.getElementById(id).classList.add('hidden');
            });
        }

        // Chapter Functions
        function filterChapters(category) {
            document.querySelectorAll('.chapter-filter').forEach(btn => {
                btn.classList.remove('bg-emerald-500', 'text-white');
                btn.classList.add('bg-white/10', 'text-gray-300');
            });
            document.querySelector(`[data-filter="${category}"]`).classList.remove('bg-white/10', 'text-gray-300');
            document.querySelector(`[data-filter="${category}"]`).classList.add('bg-emerald-500', 'text-white');

            document.querySelectorAll('.chapter-group').forEach(group => {
                if (category === 'all') {
                    group.style.display = 'block';
                } else {
                    group.style.display = group.dataset.category === category ? 'block' : 'none';
                }
            });
        }

        function toggleChapter(chapterNum) {
            const checkbox = document.querySelector(`[data-chapter="${chapterNum}"] .chapter-check`);
            const isChecked = checkbox.checked;
            
            if (isChecked) {
                createConfetti();
                currentStreak++;
                updateStreak();
            }
            
            localStorage.setItem(`chapter_${chapterNum}`, isChecked);
        }

        function quickCheck(btn, isCorrect) {
            if (isCorrect) {
                btn.classList.remove('bg-white/10');
                btn.classList.add('bg-emerald-500', 'text-white');
                createConfetti();
                setTimeout(() => {
                    btn.classList.remove('bg-emerald-500', 'text-white');
                    btn.classList.add('bg-white/10');
                }, 2000);
            } else {
                btn.classList.add('animate-shake', 'bg-red-500/50');
                setTimeout(() => btn.classList.remove('animate-shake', 'bg-red-500/50'), 500);
            }
        }

        // Practice Functions
        function setPracticeMode(mode) {
            document.getElementById('practice-images').classList.add('hidden');
            document.getElementById('practice-text').classList.add('hidden');
            document.getElementById('btn-images').classList.remove('bg-blue-500', 'text-white');
            document.getElementById('btn-images').classList.add('bg-white/10', 'text-gray-300');
            document.getElementById('btn-text').classList.remove('bg-blue-500', 'text-white');
            document.getElementById('btn-text').classList.add('bg-white/10', 'text-gray-300');
            
            document.getElementById(`practice-${mode}`).classList.remove('hidden');
            document.getElementById(`btn-${mode}`).classList.remove('bg-white/10', 'text-gray-300');
            document.getElementById(`btn-${mode}`).classList.add('bg-blue-500', 'text-white');
        }

        function revealClue(btn) {
            btn.querySelector('.clue-content')?.classList.remove('hidden');
            btn.classList.add('bg-emerald-500/10', 'border-emerald-500/30');
        }

        function checkTextAnswer(answer) {
            if (answer === 'Kenya') {
                showSuccess('Correct! The snorkel is unique to Kenya.');
                currentStreak++;
            } else {
                showError('Not quite. Remember the snorkel detail!');
            }
            updateStreak();
        }

        // Flag Functions
        const flags = [
            {country: 'Kenya', flag: '🇰🇪', region: 'Africa'},
            {country: 'Japan', flag: '🇯🇵', region: 'Asia'},
            {country: 'France', flag: '🇫🇷', region: 'Europe'},
            {country: 'Brazil', flag: '🇧🇷', region: 'South America'},
            {country: 'Australia', flag: '🇦🇺', region: 'Oceania'},
            {country: 'USA', flag: '🇺🇸', region: 'North America'}
        ];

        function handleFlagResult(correct) {
            if (correct) {
                currentStreak++;
                createConfetti();
                setTimeout(nextFlag, 1000);
            } else {
                currentStreak = 0;
                document.querySelector('.flashcard').classList.add('animate-shake');
                setTimeout(() => document.querySelector('.flashcard').classList.remove('animate-shake'), 500);
            }
            updateStreak();
        }

        function nextFlag() {
            currentFlagIndex = (currentFlagIndex + 1) % flags.length;
            document.querySelector('.flashcard').classList.remove('flipped');
            setTimeout(() => {
                document.getElementById('flagDisplay').textContent = flags[currentFlagIndex].flag;
                document.querySelector('.flashcard-back .text-4xl').textContent = flags[currentFlagIndex].country;
            }, 300);
        }

        function prevFlag() {
            currentFlagIndex = (currentFlagIndex - 1 + flags.length) % flags.length;
            nextFlag();
        }

        function shuffleFlags() {
            flags.sort(() => Math.random() - 0.5);
            currentFlagIndex = 0;
            nextFlag();
        }

        // Language Functions
        const languages = [
            {script: 'こんにちは', language: 'Japanese', hint: 'Curved lines, no circles'},
            {script: '你好', language: 'Chinese', hint: 'Complex characters, boxy shapes'},
            {script: '안녕하세요', language: 'Korean', hint: 'Circles and ovals'},
            {script: 'สวัสดี', language: 'Thai', hint: 'Loops above characters'}
        ];
        let currentLangIndex = 0;

        function checkLanguage(lang) {
            if (lang === languages[currentLangIndex].language) {
                showSuccess(`Correct! That's ${lang}.`);
                currentLangIndex = (currentLangIndex + 1) % languages.length;
                setTimeout(() => {
                    document.getElementById('languageScript').textContent = languages[currentLangIndex].script;
                }, 1500);
            } else {
                showError('Try again! Look at the character shapes.');
            }
        }

        // Location Functions
        let locationScore = 0;
        const locationTargets = ['Brazil', 'Russia', 'China', 'Kazakhstan', 'India', 'USA', 'Australia'];
        let currentTargetIndex = 0;

        function selectLocation(element, country) {
            const target = document.getElementById('targetCountry').textContent;
            if (country === target) {
                element.classList.add('correct');
                locationScore += 100;
                document.getElementById('locationScore').textContent = locationScore;
                createConfetti();
                setTimeout(nextLocationTarget, 1500);
            } else {
                element.classList.add('wrong');
                setTimeout(() => element.classList.remove('wrong'), 1000);
            }
        }

        function nextLocationTarget() {
            document.querySelectorAll('.map-point').forEach(p => p.classList.remove('correct', 'wrong'));
            currentTargetIndex = (currentTargetIndex + 1) % locationTargets.length;
            document.getElementById('targetCountry').textContent = locationTargets[currentTargetIndex];
        }

        // Capital Functions
        const capitals = [
            {country: 'France', flag: '🇫🇷', capital: 'Paris', options: ['Lyon', 'Marseille', 'Paris', 'Nice']},
            {country: 'Japan', flag: '🇯🇵', capital: 'Tokyo', options: ['Osaka', 'Kyoto', 'Tokyo', 'Yokohama']},
            {country: 'Kenya', flag: '🇰🇪', capital: 'Nairobi', options: ['Mombasa', 'Nairobi', 'Kisumu', 'Nakuru']}
        ];
        let currentCapitalIndex = 0;

        function checkCapital(guess) {
            if (guess === capitals[currentCapitalIndex].capital) {
                showSuccess(`Correct! ${guess} is the capital of ${capitals[currentCapitalIndex].country}.`);
                currentCapitalIndex = (currentCapitalIndex + 1) % capitals.length;
                setTimeout(nextCapital, 2000);
            } else {
                showError('That\'s not the capital. Try again!');
            }
        }

        function nextCapital() {
            const data = capitals[currentCapitalIndex];
            document.getElementById('capitalCountry').textContent = data.flag;
            document.querySelector('#capitals h3').textContent = data.country;
            
            const buttons = document.querySelectorAll('#capitals .grid button');
            buttons.forEach((btn, idx) => {
                btn.textContent = data.options[idx];
                btn.onclick = () => checkCapital(data.options[idx]);
            });
        }

        // Detective Functions
        function useClue(element, type) {
            if (element.classList.contains('clue-used')) return;
            
            const costs = {driving: 50, plate: 75, sun: 100, car: 125, road: 75, vegetation: 50, language: 100};
            const cost = costs[type];
            
            if (detectiveScore >= cost) {
                detectiveScore -= cost;
                document.getElementById('detectiveScore').textContent = detectiveScore;
                element.classList.add('clue-used');
                element.querySelector('.clue-content').classList.remove('hidden');
                
                usedCluesList.push(type);
                updateUsedClues();
            }
        }

        function updateUsedClues() {
            const container = document.getElementById('usedClues');
            if (usedCluesList.length === 0) {
                container.innerHTML = '<span class="text-xs text-gray-600">None yet</span>';
            } else {
                container.innerHTML = usedCluesList.map(clue => 
                    `<span class="px-2 py-1 rounded bg-orange-500/20 text-orange-400 text-xs capitalize">${clue}</span>`
                ).join('');
            }
        }

        function submitDetectiveGuess() {
            showSuccess('Excellent detective work! You correctly identified Kenya using the clues.');
            createConfetti();
        }

        function requestHint() {
            if (detectiveScore >= 25) {
                detectiveScore -= 25;
                document.getElementById('detectiveScore').textContent = detectiveScore;
                alert('Hint: Look for the unique car modification that only appears in one African country.');
            }
        }

        // Utility Functions
        function updateStreak() {
            document.getElementById('streakCounter').textContent = currentStreak;
            document.getElementById('flagStreak').textContent = currentStreak;
            localStorage.setItem('geoguessr_streak', currentStreak);
        }

        function showSuccess(message) {
            document.getElementById('successMessage').textContent = message;
            document.getElementById('successModal').classList.remove('hidden');
        }

        function showError(message) {
            const toast = document.createElement('div');
            toast.className = 'fixed bottom-4 right-4 bg-red-500 text-white px-6 py-3 rounded-xl shadow-lg z-50 animate-shake';
            toast.textContent = message;
            document.body.appendChild(toast);
            setTimeout(() => toast.remove(), 3000);
        }

        function closeModal() {
            document.getElementById('successModal').classList.add('hidden');
        }

        function nextChallenge() {
            closeModal();
        }

        function createConfetti() {
            for (let i = 0; i < 50; i++) {
                const confetti = document.createElement('div');
                confetti.className = 'confetti';
                confetti.style.left = Math.random() * 100 + 'vw';
                confetti.style.backgroundColor = ['#10b981', '#3b82f6', '#f59e0b', '#ef4444', '#8b5cf6'][Math.floor(Math.random() * 5)];
                confetti.style.animationDelay = Math.random() * 2 + 's';
                document.body.appendChild(confetti);
                setTimeout(() => confetti.remove(), 3000);
            }
        }

        // Initialize
        document.addEventListener('DOMContentLoaded', () => {
            // Check for saved user
            const savedUser = localStorage.getItem('geoguessr_user');
            if (savedUser) {
                currentUser = JSON.parse(savedUser);
                closeAuthModal();
                updateUserUI();
            }

            // Load saved progress
            const savedStreak = localStorage.getItem('geoguessr_streak') || 0;
            currentStreak = parseInt(savedStreak);
            updateStreak();

            // Check trial status
            if (currentUser && currentUser.trialStart) {
                const trialStart = new Date(currentUser.trialStart);
                const now = new Date();
                const diffTime = Math.abs(now - trialStart);
                const diffDays = Math.ceil(diffTime / (1000 * 60 * 60 * 24)); 
                trialDaysLeft = Math.max(0, 7 - diffDays);
                document.getElementById('trialCountdown').textContent = trialDaysLeft + ' days';
            }
        });
    </script>
</body>
</html>
