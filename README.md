```html
<!DOCTYPE html>
<html lang="pt-BR" class="dark">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>BancoX - Sistema Bancário & Economia Discord</title>
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <script>
        tailwind.config = {
            darkMode: 'class',
            theme: {
                extend: {
                    colors: {
                        brand: {
                            blue: '#2563eb',
                            green: '#10b981',
                            gold: '#f59e0b',
                            darkBg: '#0f172a',
                            cardBg: '#1e293b',
                            sidebar: '#0b0f19'
                        }
                    }
                }
            }
        }
    </script>
    <!-- FontAwesome Icons CDN -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <!-- Chart.js CDN -->
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <!-- Google Fonts -->
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Inter', sans-serif;
            background-color: #0b0f19;
            color: #f8fafc;
        }
        /* Custom scrollbars */
        ::-webkit-scrollbar {
            width: 6px;
            height: 6px;
        }
        ::-webkit-scrollbar-track {
            background: #0f172a;
        }
        ::-webkit-scrollbar-thumb {
            background: #334155;
            border-radius: 4px;
        }
        ::-webkit-scrollbar-thumb:hover {
            background: #475569;
        }
        .glass-card {
            background: rgba(30, 41, 59, 0.7);
            backdrop-filter: blur(12px);
            border: 1px solid rgba(255, 255, 255, 0.08);
        }
        .glass-card-gold {
            background: rgba(245, 158, 11, 0.05);
            backdrop-filter: blur(12px);
            border: 1px solid rgba(245, 158, 11, 0.2);
        }
        .animate-fade-in {
            animation: fadeIn 0.3s ease-in-out;
        }
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(6px); }
            to { opacity: 1; transform: translateY(0); }
        }
    </style>
</head>
<body class="min-h-screen flex flex-col md:flex-row overflow-x-hidden">

    <!-- Mobile Top Navigation Header -->
    <div class="md:hidden bg-slate-900 border-b border-slate-800 p-4 flex justify-between items-center sticky top-0 z-50">
        <div class="flex items-center space-x-3">
            <div class="w-9 h-9 rounded-xl bg-gradient-to-tr from-blue-600 via-emerald-500 to-amber-500 flex items-center justify-center font-black text-xl shadow-lg">
                🏦
            </div>
            <div>
                <h1 class="font-bold text-lg tracking-wider text-white">Banco<span class="text-amber-400">X</span></h1>
                <p class="text-xs text-slate-400">Economia Discord</p>
            </div>
        </div>
        <button id="mobileMenuBtn" class="text-slate-300 hover:text-white p-2 rounded-lg bg-slate-800 focus:outline-none">
            <i class="fa-solid fa-bars text-xl"></i>
        </button>
    </div>

    <!-- Sidebar Navigation -->
    <aside id="sidebar" class="fixed inset-y-0 left-0 z-40 w-64 bg-[#080c14] border-r border-slate-800 transform -translate-x-full md:translate-x-0 transition-transform duration-300 ease-in-out flex flex-col justify-between md:static md:inset-auto">
        <div>
            <!-- Sidebar Header / Logo -->
            <div class="p-5 flex items-center justify-between border-b border-slate-800/80">
                <div class="flex items-center space-x-3">
                    <div class="w-10 h-10 rounded-xl bg-gradient-to-tr from-blue-600 via-emerald-500 to-amber-500 flex items-center justify-center font-bold text-2xl shadow-lg shadow-blue-900/30">
                        🏦
                    </div>
                    <div>
                        <h1 class="font-extrabold text-xl tracking-wider text-white">Banco<span class="text-amber-400">X</span></h1>
                        <span class="text-[10px] bg-blue-500/20 text-blue-400 border border-blue-500/30 px-2 py-0.5 rounded-full font-medium">v2.5 PRO</span>
                    </div>
                </div>
                <button id="closeSidebarBtn" class="md:hidden text-slate-400 hover:text-white">
                    <i class="fa-solid fa-xmark text-xl"></i>
                </button>
            </div>

            <!-- Profile Summary Widget -->
            <div class="p-4 mx-3 my-3 bg-slate-900/80 border border-slate-800 rounded-xl flex items-center space-x-3">
                <img id="sidebarAvatar" src="https://images.unsplash.com/photo-1534528741775-53994a69daeb?w=100&auto=format&fit=crop&q=80" class="w-11 h-11 rounded-full border-2 border-emerald-500/50 object-cover" alt="User Avatar">
                <div class="overflow-hidden">
                    <h2 id="sidebarUsername" class="font-semibold text-sm text-slate-100 truncate">Alex_Discord</h2>
                    <p id="sidebarTag" class="text-xs text-slate-400 truncate">ID: #84920412</p>
                    <div class="mt-1 flex items-center space-x-1">
                        <span class="text-[10px] bg-emerald-500/20 text-emerald-400 px-1.5 py-0.2 rounded font-medium">🟢 Protegida</span>
                    </div>
                </div>
            </div>

            <!-- Navigation Links -->
            <nav class="px-3 space-y-1 max-h-[calc(100vh-280px)] overflow-y-auto">
                <a href="#dashboard" class="nav-btn active text-blue-400 bg-blue-600/10 border-l-4 border-blue-500 flex items-center px-4 py-2.5 rounded-r-lg text-sm font-medium transition-all group">
                    <i class="fa-solid fa-chart-pie w-6 text-blue-400"></i>
                    <span>Dashboard</span>
                </a>
                <a href="#conta" class="nav-btn text-slate-400 hover:text-slate-200 hover:bg-slate-800/60 flex items-center px-4 py-2.5 rounded-r-lg text-sm font-medium transition-all group">
                    <i class="fa-solid fa-building-columns w-6 text-slate-500 group-hover:text-amber-400 transition-colors"></i>
                    <span>Conta Bancária</span>
                </a>
                <a href="#transferir" class="nav-btn text-slate-400 hover:text-slate-200 hover:bg-slate-800/60 flex items-center px-4 py-2.5 rounded-r-lg text-sm font-medium transition-all group">
                    <i class="fa-solid fa-paper-plane w-6 text-slate-500 group-hover:text-emerald-400 transition-colors"></i>
                    <span>Transferência</span>
                </a>
                <a href="#empregos" class="nav-btn text-slate-400 hover:text-slate-200 hover:bg-slate-800/60 flex items-center px-4 py-2.5 rounded-r-lg text-sm font-medium transition-all group">
                    <i class="fa-solid fa-briefcase w-6 text-slate-500 group-hover:text-blue-400 transition-colors"></i>
                    <span>Empregos & Level</span>
                </a>
                <a href="#investimentos" class="nav-btn text-slate-400 hover:text-slate-200 hover:bg-slate-800/60 flex items-center px-4 py-2.5 rounded-r-lg text-sm font-medium transition-all group">
                    <i class="fa-solid fa-chart-line w-6 text-slate-500 group-hover:text-emerald-400 transition-colors"></i>
                    <span>Investimentos</span>
                </a>
                <a href="#loja" class="nav-btn text-slate-400 hover:text-slate-200 hover:bg-slate-800/60 flex items-center px-4 py-2.5 rounded-r-lg text-sm font-medium transition-all group">
                    <i class="fa-solid fa-store w-6 text-slate-500 group-hover:text-amber-400 transition-colors"></i>
                    <span>Loja Virtual</span>
                </a>
                <a href="#inventario" class="nav-btn text-slate-400 hover:text-slate-200 hover:bg-slate-800/60 flex items-center px-4 py-2.5 rounded-r-lg text-sm font-medium transition-all group">
                    <i class="fa-solid fa-boxes-stacked w-6 text-slate-500 group-hover:text-purple-400 transition-colors"></i>
                    <span>Inventário</span>
                </a>
                <a href="#daily" class="nav-btn text-slate-400 hover:text-slate-200 hover:bg-slate-800/60 flex items-center px-4 py-2.5 rounded-r-lg text-sm font-medium transition-all group">
                    <i class="fa-solid fa-gift w-6 text-slate-500 group-hover:text-pink-400 transition-colors"></i>
                    <span>Recompensa Diária</span>
                </a>
                <a href="#historico" class="nav-btn text-slate-400 hover:text-slate-200 hover:bg-slate-800/60 flex items-center px-4 py-2.5 rounded-r-lg text-sm font-medium transition-all group">
                    <i class="fa-solid fa-clock-rotate-left w-6 text-slate-500 group-hover:text-blue-400 transition-colors"></i>
                    <span>Histórico</span>
                </a>
                <a href="#ranking" class="nav-btn text-slate-400 hover:text-slate-200 hover:bg-slate-800/60 flex items-center px-4 py-2.5 rounded-r-lg text-sm font-medium transition-all group">
                    <i class="fa-solid fa-trophy w-6 text-slate-500 group-hover:text-amber-400 transition-colors"></i>
                    <span>Ranking Global</span>
                </a>
                <a href="#seguranca" class="nav-btn text-slate-400 hover:text-slate-200 hover:bg-slate-800/60 flex items-center px-4 py-2.5 rounded-r-lg text-sm font-medium transition-all group">
                    <i class="fa-solid fa-shield-halved w-6 text-slate-500 group-hover:text-emerald-400 transition-colors"></i>
                    <span>Segurança</span>
                </a>
                <a href="#configuracoes" class="nav-btn text-slate-400 hover:text-slate-200 hover:bg-slate-800/60 flex items-center px-4 py-2.5 rounded-r-lg text-sm font-medium transition-all group">
                    <i class="fa-solid fa-gear w-6 text-slate-500 group-hover:text-slate-300 transition-colors"></i>
                    <span>Configurações</span>
                </a>
                <a href="#comandos" class="nav-btn text-slate-400 hover:text-slate-200 hover:bg-slate-800/60 flex items-center px-4 py-2.5 rounded-r-lg text-sm font-medium transition-all group">
                    <i class="fa-solid fa-terminal w-6 text-slate-500 group-hover:text-cyan-400 transition-colors"></i>
                    <span>Comandos do Bot</span>
                </a>
            </nav>
        </div>

        <!-- Discord Dynamic Actions Block -->
        <div class="p-4 border-t border-slate-800 space-y-2">
            <a id="btnJoinDiscord" href="https://discord.gg/example" target="_blank" class="w-full bg-indigo-600/20 hover:bg-indigo-600/30 text-indigo-300 border border-indigo-500/30 font-medium py-2 px-3 rounded-lg text-xs flex items-center justify-center space-x-2 transition">
                <i class="fa-brands fa-discord text-sm"></i>
                <span>Entrar no Discord</span>
            </a>
            <a id="btnAddBot" href="https://discord.com/api/oauth2/authorize" target="_blank" class="w-full bg-emerald-600/20 hover:bg-emerald-600/30 text-emerald-300 border border-emerald-500/30 font-medium py-2 px-3 rounded-lg text-xs flex items-center justify-center space-x-2 transition">
                <i class="fa-solid fa-robot text-sm"></i>
                <span>Adicionar Bot</span>
            </a>
        </div>
    </aside>

    <!-- Main Content Container -->
    <main class="flex-1 p-4 md:p-8 overflow-y-auto max-w-7xl mx-auto w-full">

        <!-- Top Notification Banner -->
        <div class="mb-6 bg-gradient-to-r from-blue-900/40 via-purple-900/30 to-amber-900/30 border border-blue-500/20 rounded-2xl p-4 flex flex-col sm:flex-row items-center justify-between gap-3 shadow-xl">
            <div class="flex items-center space-x-3 text-center sm:text-left">
                <div class="p-2.5 bg-blue-500/10 text-blue-400 rounded-xl hidden sm:block">
                    <i class="fa-solid fa-bullhorn text-xl"></i>
                </div>
                <div>
                    <h3 class="text-sm font-semibold text-slate-200">Painel do Bot de Economia BancoX</h3>
                    <p class="text-xs text-slate-400">Gerencie sua vida financeira virtual no servidor do Discord diretamente neste dashboard interativo.</p>
                </div>
            </div>
            <div class="flex items-center space-x-2">
                <button onclick="quickActionDaily()" class="text-xs bg-amber-500 hover:bg-amber-600 text-slate-950 font-bold px-3 py-1.5 rounded-lg transition shadow-md shadow-amber-500/20 flex items-center space-x-1 whitespace-nowrap">
                    <i class="fa-solid fa-gift"></i>
                    <span>Resgatar Daily</span>
                </button>
            </div>
        </div>

        <!-- Dynamic Page Views Container -->
        <div id="views-container">

            <!-- 1. DASHBOARD VIEW -->
            <section id="view-dashboard" class="page-view space-y-6 animate-fade-in">
                <!-- Stat Cards Grid -->
                <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4 gap-4">
                    <!-- Wallet Card -->
                    <div class="glass-card p-5 rounded-2xl border border-slate-800 relative overflow-hidden">
                        <div class="flex justify-between items-start">
                            <div>
                                <p class="text-xs text-slate-400 uppercase font-bold tracking-wider">Carteira</p>
                                <h3 id="dashWallet" class="text-2xl font-black text-emerald-400 mt-1">R$ 0</h3>
                            </div>
                            <div class="p-3 bg-emerald-500/10 text-emerald-400 rounded-xl">
                                <i class="fa-solid fa-wallet text-xl"></i>
                            </div>
                        </div>
                        <div class="mt-4 text-[11px] text-slate-400 flex items-center space-x-1">
                            <span class="text-emerald-400"><i class="fa-solid fa-coins"></i></span>
                            <span>Dinheiro vivo disponível</span>
                        </div>
                    </div>

                    <!-- Bank Balance Card -->
                    <div class="glass-card p-5 rounded-2xl border border-slate-800 relative overflow-hidden">
                        <div class="flex justify-between items-start">
                            <div>
                                <p class="text-xs text-slate-400 uppercase font-bold tracking-wider">Saldo Bancário</p>
                                <h3 id="dashBank" class="text-2xl font-black text-blue-400 mt-1">R$ 0</h3>
                            </div>
                            <div class="p-3 bg-blue-500/10 text-blue-400 rounded-xl">
                                <i class="fa-solid fa-vault text-xl"></i>
                            </div>
                        </div>
                        <div class="mt-4 text-[11px] text-slate-400 flex items-center space-x-1">
                            <span class="text-blue-400"><i class="fa-solid fa-shield-halved"></i></span>
                            <span>Protegido contra roubos</span>
                        </div>
                    </div>

                    <!-- Net Worth Card -->
                    <div class="glass-card-gold p-5 rounded-2xl relative overflow-hidden">
                        <div class="flex justify-between items-start">
                            <div>
                                <p class="text-xs text-amber-400 uppercase font-bold tracking-wider">Patrimônio Total</p>
                                <h3 id="dashNetWorth" class="text-2xl font-black text-amber-300 mt-1">R$ 0</h3>
                            </div>
                            <div class="p-3 bg-amber-500/10 text-amber-400 rounded-xl">
                                <i class="fa-solid fa-gem text-xl"></i>
                            </div>
                        </div>
                        <div class="mt-4 text-[11px] text-amber-400/80 flex items-center space-x-1">
                            <span><i class="fa-solid fa-arrow-trend-up"></i></span>
                            <span>Carteira + Banco + Investimentos</span>
                        </div>
                    </div>

                    <!-- Job / Salary Card -->
                    <div class="glass-card p-5 rounded-2xl border border-slate-800 relative overflow-hidden">
                        <div class="flex justify-between items-start">
                            <div>
                                <p class="text-xs text-slate-400 uppercase font-bold tracking-wider">Emprego Atual</p>
                                <h3 id="dashJob" class="text-lg font-bold text-slate-100 mt-1">Nenhum</h3>
                                <p id="dashSalary" class="text-xs text-emerald-400 font-semibold mt-0.5">Salário: R$ 0/trab</p>
                            </div>
                            <div class="p-3 bg-indigo-500/10 text-indigo-400 rounded-xl">
                                <i class="fa-solid fa-user-tie text-xl"></i>
                            </div>
                        </div>
                        <div class="mt-3">
                            <div class="flex justify-between text-[11px] text-slate-400 mb-1">
                                <span>Level <span id="dashLevel" class="text-white font-bold">1</span></span>
                                <span><span id="dashXP">0</span>/100 XP</span>
                            </div>
                            <div class="w-full bg-slate-800 h-1.5 rounded-full overflow-hidden">
                                <div id="dashXPBar" class="bg-gradient-to-r from-blue-500 to-amber-400 h-full w-0 transition-all duration-300"></div>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Secondary Dashboard Status row -->
                <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                    <div class="glass-card p-5 rounded-2xl flex items-center justify-between border border-slate-800">
                        <div class="flex items-center space-x-4">
                            <div class="p-3.5 bg-emerald-500/10 text-emerald-400 rounded-xl">
                                <i class="fa-solid fa-chart-line text-2xl"></i>
                            </div>
                            <div>
                                <p class="text-xs text-slate-400">Investimento Ativo</p>
                                <h4 id="dashInvestActive" class="text-lg font-bold text-slate-100">R$ 0,00</h4>
                                <span id="dashInvestType" class="text-xs text-slate-400">Nenhum investimento em curso</span>
                            </div>
                        </div>
                        <button onclick="navigateTo('investimentos')" class="px-4 py-2 bg-slate-800 hover:bg-slate-700 text-xs font-semibold text-slate-200 rounded-xl transition">
                            Gerenciar
                        </button>
                    </div>

                    <div class="glass-card p-5 rounded-2xl flex items-center justify-between border border-slate-800">
                        <div class="flex items-center space-x-4">
                            <div class="p-3.5 bg-amber-500/10 text-amber-400 rounded-xl">
                                <i class="fa-solid fa-gift text-2xl"></i>
                            </div>
                            <div>
                                <p class="text-xs text-slate-400">Recompensa Diária (Daily)<# index.htmlsite
