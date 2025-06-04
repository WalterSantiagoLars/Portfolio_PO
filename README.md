<!DOCTYPE html>
<html lang="pt-BR" class="scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Walter Santiago - Product Owner Estratégico</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://unpkg.com/boxicons@2.1.4/css/boxicons.min.css" rel="stylesheet">
    <script>
        tailwind.config = {
            darkMode: 'class',
            theme: {
                extend: {
                    colors: {
                        primary: '#5D5CDE',
                        secondary: '#818CF8',
                        accent: '#A855F7',
                    },
                    animation: {
                        'float': 'float 6s ease-in-out infinite',
                        'pulse-slow': 'pulse 3s ease-in-out infinite',
                        'fade-in': 'fadeIn 0.6s ease-out',
                        'slide-up': 'slideUp 0.8s ease-out',
                        'bounce-slow': 'bounce 2s infinite',
                    },
                    keyframes: {
                        float: {
                            '0%, 100%': { transform: 'translateY(0px)' },
                            '50%': { transform: 'translateY(-20px)' },
                        },
                        fadeIn: {
                            '0%': { opacity: '0', transform: 'translateY(30px)' },
                            '100%': { opacity: '1', transform: 'translateY(0)' },
                        },
                        slideUp: {
                            '0%': { opacity: '0', transform: 'translateY(50px)' },
                            '100%': { opacity: '1', transform: 'translateY(0)' },
                        }
                    }
                }
            }
        }
    </script>
    <style>
        .gradient-text {
            background: linear-gradient(135deg, #5D5CDE, #A855F7);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }
        
        .gradient-bg {
            background: linear-gradient(135deg, #5D5CDE, #A855F7);
        }
        
        .gradient-border {
            background: linear-gradient(135deg, #5D5CDE, #A855F7);
            padding: 2px;
            border-radius: 12px;
        }
        
        .skill-bar {
            transition: width 2s ease-in-out;
        }
        
        .floating-element {
            position: absolute;
            opacity: 0.1;
            animation: float 6s ease-in-out infinite;
        }
        
        .floating-element:nth-child(2) { animation-delay: -2s; }
        .floating-element:nth-child(3) { animation-delay: -4s; }
        
        .progress-bar {
            position: fixed;
            top: 0;
            left: 0;
            width: 0%;
            height: 3px;
            background: linear-gradient(90deg, #5D5CDE, #A855F7);
            z-index: 9999;
            transition: width 0.1s ease;
        }
        
        .project-card {
            transition: all 0.3s ease;
            border: 2px solid transparent;
            background: linear-gradient(white, white) padding-box,
                        linear-gradient(135deg, #5D5CDE, #A855F7) border-box;
        }
        
        .dark .project-card {
            background: linear-gradient(#1f2937, #1f2937) padding-box,
                        linear-gradient(135deg, #5D5CDE, #A855F7) border-box;
        }
        
        .project-card:hover {
            transform: translateY(-8px);
            box-shadow: 0 20px 40px rgba(93, 92, 222, 0.2);
        }
        
        .workflow-block {
            transition: all 0.3s ease;
        }
        
        .workflow-block:hover {
            transform: scale(1.05);
        }
        
        .nav-link.active {
            color: #5D5CDE;
            font-weight: 600;
        }
        
        .tool-icon {
            transition: all 0.3s ease;
        }
        
        .tool-icon:hover {
            transform: translateY(-5px);
            color: #5D5CDE;
        }
        
        .profile-image {
            border: 4px solid transparent;
            background: linear-gradient(white, white) padding-box,
                        linear-gradient(135deg, #5D5CDE, #A855F7) border-box;
        }
        
        .dark .profile-image {
            background: linear-gradient(#1f2937, #1f2937) padding-box,
                        linear-gradient(135deg, #5D5CDE, #A855F7) border-box;
        }
        
        .project-modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.8);
            z-index: 1000;
            backdrop-filter: blur(4px);
        }
        
        .project-modal.active {
            display: flex;
            align-items: center;
            justify-content: center;
            animation: fadeIn 0.3s ease;
        }
        
        .modal-content {
            background: white;
            max-width: 90vw;
            max-height: 90vh;
            overflow-y: auto;
            border-radius: 16px;
            animation: slideUp 0.3s ease;
        }
        
        .dark .modal-content {
            background: #1f2937;
        }

        .image-modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.9);
            z-index: 2000;
            backdrop-filter: blur(4px);
        }
        
        .image-modal.active {
            display: flex;
            align-items: center;
            justify-content: center;
            animation: fadeIn 0.3s ease;
        }
        
        .image-modal-content {
            max-width: 95vw;
            max-height: 95vh;
            position: relative;
        }
        
        .image-modal img {
            max-width: 100%;
            max-height: 95vh;
            object-fit: contain;
            border-radius: 8px;
        }
        
        .image-modal-close {
            position: absolute;
            top: -40px;
            right: 0;
            background: white;
            color: black;
            border-radius: 50%;
            width: 40px;
            height: 40px;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            font-size: 20px;
            font-weight: bold;
        }
    </style>
</head>
<body class="bg-white dark:bg-gray-900 text-gray-900 dark:text-white transition-colors duration-300">
    <!-- Progress Bar -->
    <div class="progress-bar"></div>
    
    <!-- Header -->
    <header class="fixed top-0 w-full bg-white/90 dark:bg-gray-900/90 backdrop-blur-md border-b border-gray-200 dark:border-gray-700 z-50 transition-all duration-300">
        <nav class="container mx-auto px-6 py-4">
            <div class="flex items-center justify-between">
                <!-- Logo -->
                <div class="flex items-center space-x-2">
                    <div class="w-10 h-10 gradient-bg rounded-lg flex items-center justify-center">
                        <i class='bx bx-brain text-white text-xl'></i>
                    </div>
                    <span class="text-xl font-bold gradient-text">Walter Santiago</span>
                </div>
                
                <!-- Desktop Navigation -->
                <ul class="hidden md:flex space-x-8">
                    <li><a href="#inicio" class="nav-link text-gray-700 dark:text-gray-300 hover:text-primary transition-colors font-medium">Início</a></li>
                    <li><a href="#sobre" class="nav-link text-gray-700 dark:text-gray-300 hover:text-primary transition-colors font-medium">Sobre</a></li>
                    <li><a href="#projetos" class="nav-link text-gray-700 dark:text-gray-300 hover:text-primary transition-colors font-medium">Projetos</a></li>
                    <li><a href="#habilidades" class="nav-link text-gray-700 dark:text-gray-300 hover:text-primary transition-colors font-medium">Habilidades</a></li>
                    <li><a href="#contato" class="nav-link text-gray-700 dark:text-gray-300 hover:text-primary transition-colors font-medium">Contato</a></li>
                </ul>
                
                <!-- Dark Mode Toggle -->
                <div class="hidden md:flex items-center space-x-4">
                    <button id="theme-toggle" class="p-2 rounded-lg hover:bg-gray-100 dark:hover:bg-gray-800 transition-colors">
                        <i class='bx bx-moon dark:hidden text-xl'></i>
                        <i class='bx bx-sun hidden dark:block text-xl'></i>
                    </button>
                </div>
                
                <!-- Mobile Menu Button -->
                <button id="mobile-menu-button" class="md:hidden p-2 rounded-lg hover:bg-gray-100 dark:hover:bg-gray-800">
                    <i class='bx bx-menu text-2xl'></i>
                </button>
            </div>
            
            <!-- Mobile Menu -->
            <div id="mobile-menu" class="hidden md:hidden mt-4 pb-4">
                <ul class="space-y-4">
                    <li><a href="#inicio" class="block text-gray-700 dark:text-gray-300 hover:text-primary transition-colors">Início</a></li>
                    <li><a href="#sobre" class="block text-gray-700 dark:text-gray-300 hover:text-primary transition-colors">Sobre</a></li>
                    <li><a href="#projetos" class="block text-gray-700 dark:text-gray-300 hover:text-primary transition-colors">Projetos</a></li>
                    <li><a href="#habilidades" class="block text-gray-700 dark:text-gray-300 hover:text-primary transition-colors">Habilidades</a></li>
                    <li><a href="#contato" class="block text-gray-700 dark:text-gray-300 hover:text-primary transition-colors">Contato</a></li>
                </ul>
                <div class="mt-4 pt-4 border-t border-gray-200 dark:border-gray-700">
                    <button id="mobile-theme-toggle" class="flex items-center space-x-2 text-gray-700 dark:text-gray-300">
                        <i class='bx bx-moon dark:hidden'></i>
                        <i class='bx bx-sun hidden dark:block'></i>
                        <span>Alternar tema</span>
                    </button>
                </div>
            </div>
        </nav>
    </header>

    <!-- Hero Section -->
    <section id="inicio" class="pt-20 min-h-screen flex items-center relative overflow-hidden">
        <!-- Animated Background Elements -->
        <div class="floating-element w-64 h-64 gradient-bg rounded-full blur-3xl top-20 left-10"></div>
        <div class="floating-element w-48 h-48 bg-purple-500 rounded-full blur-3xl bottom-20 right-10"></div>
        <div class="floating-element w-32 h-32 bg-blue-500 rounded-full blur-3xl top-1/2 right-1/4"></div>
        
        <div class="container mx-auto px-6 relative z-10">
            <div class="grid md:grid-cols-2 gap-12 items-center">
                <!-- Content -->
                <div class="animate-fade-in">
                    <div class="mb-4">
                        <span class="text-primary font-semibold text-lg">👋 Olá, eu sou</span>
                    </div>
                    <h1 class="text-4xl md:text-6xl font-bold mb-6">
                        <span class="gradient-text">Walter Santiago</span>
                    </h1>
                    <h2 class="text-2xl md:text-3xl text-gray-600 dark:text-gray-300 mb-6">
                        Product Owner Estratégico
                    </h2>
                    <p class="text-lg text-gray-600 dark:text-gray-400 mb-8 leading-relaxed">
                        com foco em valor e resultados

Transformo necessidades de usuários e objetivos de negócio em produtos digitais escaláveis e bem-sucedidos. Com experiência em SAP Commerce, S/4 Hana e ferramentas ágeis, lidero estratégias orientadas por dados, combinando Design Thinking e CRM para gerar entregas com impacto real.
                    </p>
                    
                    <!-- CTA Buttons -->
                    <div class="flex flex-col sm:flex-row gap-4 mb-8">
                        <a href="#contato" class="gradient-bg text-white px-8 py-3 rounded-lg font-semibold hover:scale-105 transition-transform text-center">
                            Entre em Contato
                        </a>
                        <a href="#projetos" class="border-2 border-primary text-primary px-8 py-3 rounded-lg font-semibold hover:bg-primary hover:text-white transition-all text-center">
                            Ver Projetos
                        </a>
                    </div>
                    
                    <!-- Social Links -->
                    <div class="flex space-x-4">
                        <a href="https://linkedin.com" target="_blank" class="w-12 h-12 bg-gray-100 dark:bg-gray-800 rounded-lg flex items-center justify-center hover:bg-primary hover:text-white transition-colors">
                            <i class='bx bxl-linkedin text-xl'></i>
                        </a>
                        <a href="https://github.com" target="_blank" class="w-12 h-12 bg-gray-100 dark:bg-gray-800 rounded-lg flex items-center justify-center hover:bg-primary hover:text-white transition-colors">
                            <i class='bx bxl-github text-xl'></i>
                        </a>
                        
                    </div>
                </div>
                
                <!-- Profile Image -->
                <div class="flex justify-center animate-float">
                    <div class="relative">
                        <div class="w-80 h-80 profile-image rounded-full overflow-hidden">
                            <img src="https://pfst.cf2.poecdn.net/base/image/49c50f1632c19fc6b7d99431d7c3407799981eb3c758aaae34be4ae0e8339192?w=684&h=684" alt="Walter Santiago - Product Owner Estratégico" class="w-full h-full object-cover">
                        </div>
                        <!-- Decorative Elements -->
                        <div class="absolute -top-4 -right-4 w-8 h-8 bg-primary rounded-full animate-pulse-slow"></div>
                        <div class="absolute -bottom-4 -left-4 w-6 h-6 bg-accent rounded-full animate-bounce-slow"></div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- About Section -->
    <section id="sobre" class="py-20 bg-gray-50 dark:bg-gray-800">
        <div class="container mx-auto px-6">
            <div class="text-center mb-16">
                <h2 class="text-3xl md:text-4xl font-bold mb-4">
                    <span class="gradient-text">Sobre Mim</span>
                </h2>
                <p class="text-xl text-gray-600 dark:text-gray-400">Minha jornada no mundo de produtos digitais</p>
            </div>
            
            <div class="grid md:grid-cols-2 gap-12 items-center mb-16">
                <div class="animate-fade-in">
                    <p class="text-lg text-gray-600 dark:text-gray-400 mb-6 leading-relaxed">
                        Especialista em transformar ideias em produtos digitais de sucesso. Foco em estratégia de produto, metodologias ágeis e análise de dados para gerar valor real para usuários e negócios.
                    </p>
                    <p class="text-lg text-gray-600 dark:text-gray-400 mb-6 leading-relaxed">
                        Ao longo dos anos, foquei no papel de Product Owner, onde desenvolvi habilidades em pesquisa de usuário, análise de mercado, definição de estratégias de produto e liderança de equipes multidisciplinares. Minha abordagem combina metodologias ágeis com análise orientada por dados.
                    </p>
                    
                    <!-- Quote -->
                    <div class="gradient-border">
                        <div class="bg-white dark:bg-gray-900 p-6 rounded-lg">
                            <blockquote class="text-lg italic text-gray-700 dark:text-gray-300 mb-4">
                                "Funcionalidade por si só não justifica um produto. O que realmente importa é sua capacidade de resolver problemas reais com impacto mensurável. É por isso que minha tomada de decisão é sempre guiada por dados e feedbacks concretos do usuário."
                            </blockquote>
                            <cite class="text-primary font-semibold">— Walter Santiago</cite>
                        </div>
                    </div>
                </div>
                
                <div class="grid grid-cols-2 gap-6">
                    <div class="workflow-block bg-white dark:bg-gray-900 p-6 rounded-lg shadow-lg text-center">
                        <div class="w-16 h-16 gradient-bg rounded-full flex items-center justify-center mx-auto mb-4">
                            <i class='bx bx-search-alt text-white text-2xl'></i>
                        </div>
                        <h3 class="font-bold mb-2">Discovery</h3>
                        <p class="text-sm text-gray-600 dark:text-gray-400">Pesquisa e identificação de oportunidades</p>
                    </div>
                    
                    <div class="workflow-block bg-white dark:bg-gray-900 p-6 rounded-lg shadow-lg text-center">
                        <div class="w-16 h-16 gradient-bg rounded-full flex items-center justify-center mx-auto mb-4">
                            <i class='bx bx-map text-white text-2xl'></i>
                        </div>
                        <h3 class="font-bold mb-2">Planning</h3>
                        <p class="text-sm text-gray-600 dark:text-gray-400">Estratégia e roadmap de produto</p>
                    </div>
                    
                    <div class="workflow-block bg-white dark:bg-gray-900 p-6 rounded-lg shadow-lg text-center">
                        <div class="w-16 h-16 gradient-bg rounded-full flex items-center justify-center mx-auto mb-4">
                            <i class='bx bx-rocket text-white text-2xl'></i>
                        </div>
                        <h3 class="font-bold mb-2">Execution</h3>
                        <p class="text-sm text-gray-600 dark:text-gray-400">Desenvolvimento ágil e iterativo</p>
                    </div>
                    
                    <div class="workflow-block bg-white dark:bg-gray-900 p-6 rounded-lg shadow-lg text-center">
                        <div class="w-16 h-16 gradient-bg rounded-full flex items-center justify-center mx-auto mb-4">
                            <i class='bx bx-bar-chart-alt-2 text-white text-2xl'></i>
                        </div>
                        <h3 class="font-bold mb-2">Measure</h3>
                        <p class="text-sm text-gray-600 dark:text-gray-400">Análise de métricas e otimização</p>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Projects Section -->
    <section id="projetos" class="py-20">
        <div class="container mx-auto px-6">
            <div class="text-center mb-16">
                <h2 class="text-3xl md:text-4xl font-bold mb-4">
                    <span class="gradient-text">Projetos</span>
                </h2>
                <p class="text-xl text-gray-600 dark:text-gray-400">Portfolio de estudos e cases de sucesso</p>
            </div>
            
            <!-- Project Cards -->
            <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-8">
                <!-- HireTrack -->
                <div class="project-card rounded-lg p-6 cursor-pointer" onclick="openModal('hiretrack')">
                    
        <div class="absolute top-2 right-2">
            <a href="https" target="_blank" class="bg-primary text-white px-3 py-1 text-xs rounded-lg font-semibold hover:bg-accent transition">
                HARP
            </a>
        </div>
    
<div class="mb-4">
                        <div class="w-12 h-12 gradient-bg rounded-lg flex items-center justify-center mb-4">
                            <i class='bx bx-briefcase text-white text-xl'></i>
                        </div>
                        <h3 class="text-xl font-bold mb-2">HireTrack</h3>
                        <p class="text-gray-600 dark:text-gray-400 mb-4">Sistema de gestão de processos seletivos com automação de fluxos e análise de candidatos.</p>
                        
                        <!-- Tags -->
                        <div class="flex flex-wrap gap-2 mb-4">
                            <span class="bg-primary/10 text-primary px-3 py-1 rounded-full text-sm">RH Tech</span>
                            <span class="bg-primary/10 text-primary px-3 py-1 rounded-full text-sm">B2B</span>
                            <span class="bg-primary/10 text-primary px-3 py-1 rounded-full text-sm">SaaS</span>
                        </div>
                        
                        <div class="text-sm text-gray-500 dark:text-gray-400 mb-4">
                            <span class="font-semibold">Tech:</span> React, Node.js, MongoDB
                        </div>
                        
                        <button class="w-full gradient-bg text-white py-2 rounded-lg font-semibold hover:scale-105 transition-transform">
                            Ver Detalhes
                        </button>
                    </div>
                </div>
                
                <!-- CriptoPoupança -->
                <div class="project-card rounded-lg p-6 cursor-pointer" onclick="openModal('cripto')">
                    
        <div class="absolute top-2 right-2">
            <a href="https" target="_blank" class="bg-primary text-white px-3 py-1 text-xs rounded-lg font-semibold hover:bg-accent transition">
                HARP
            </a>
        </div>
    
<div class="mb-4">
                        <div class="w-12 h-12 gradient-bg rounded-lg flex items-center justify-center mb-4">
                            <i class='bx bx-bitcoin text-white text-xl'></i>
                        </div>
                        <h3 class="text-xl font-bold mb-2">CriptoPoupança</h3>
                        <p class="text-gray-600 dark:text-gray-400 mb-4">Plataforma de microinvestimentos em criptomoedas com estratégias automatizadas.</p>
                        
                        <!-- Tags -->
                        <div class="flex flex-wrap gap-2 mb-4">
                            <span class="bg-primary/10 text-primary px-3 py-1 rounded-full text-sm">FinTech</span>
                            <span class="bg-primary/10 text-primary px-3 py-1 rounded-full text-sm">Crypto</span>
                            <span class="bg-primary/10 text-primary px-3 py-1 rounded-full text-sm">B2C</span>
                        </div>
                        
                        <div class="text-sm text-gray-500 dark:text-gray-400 mb-4">
                            <span class="font-semibold">Tech:</span> Vue.js, Python, PostgreSQL
                        </div>
                        
                        <button class="w-full gradient-bg text-white py-2 rounded-lg font-semibold hover:scale-105 transition-transform">
                            Ver Detalhes
                        </button>
                    </div>
                </div>
                
                <!-- ReparoFácil -->
                <div class="project-card rounded-lg p-6 cursor-pointer" onclick="openModal('reparo')">
                    
        <div class="absolute top-2 right-2">
            <a href="https" target="_blank" class="bg-primary text-white px-3 py-1 text-xs rounded-lg font-semibold hover:bg-accent transition">
                HARP
            </a>
        </div>
    
<div class="mb-4">
                        <div class="w-12 h-12 gradient-bg rounded-lg flex items-center justify-center mb-4">
                            <i class='bx bx-wrench text-white text-xl'></i>
                        </div>
                        <h3 class="text-xl font-bold mb-2">ReparoFácil</h3>
                        <p class="text-gray-600 dark:text-gray-400 mb-4">Assistente de diagnóstico doméstico com IA para identificar problemas e soluções.</p>
                        
                        <!-- Tags -->
                        <div class="flex flex-wrap gap-2 mb-4">
                            <span class="bg-primary/10 text-primary px-3 py-1 rounded-full text-sm">AI/ML</span>
                            <span class="bg-primary/10 text-primary px-3 py-1 rounded-full text-sm">IoT</span>
                            <span class="bg-primary/10 text-primary px-3 py-1 rounded-full text-sm">B2C</span>
                        </div>
                        
                        <div class="text-sm text-gray-500 dark:text-gray-400 mb-4">
                            <span class="font-semibold">Tech:</span> React Native, TensorFlow, AWS
                        </div>
                        
                        <button class="w-full gradient-bg text-white py-2 rounded-lg font-semibold hover:scale-105 transition-transform">
                            Ver Detalhes
                        </button>
                    </div>
                </div>
                
                <!-- AgroIA -->
                <div class="project-card rounded-lg p-6 cursor-pointer" onclick="openModal('agro')">
                    
        <div class="absolute top-2 right-2">
            <a href="https" target="_blank" class="bg-primary text-white px-3 py-1 text-xs rounded-lg font-semibold hover:bg-accent transition">
                HARP
            </a>
        </div>
    
<div class="mb-4">
                        <div class="w-12 h-12 gradient-bg rounded-lg flex items-center justify-center mb-4">
                            <i class='bx bx-leaf text-white text-xl'></i>
                        </div>
                        <h3 class="text-xl font-bold mb-2">AgroIA</h3>
                        <p class="text-gray-600 dark:text-gray-400 mb-4">Assistente virtual para agricultores com análise de cultivo e otimização de produção.</p>
                        
                        <!-- Tags -->
                        <div class="flex flex-wrap gap-2 mb-4">
                            <span class="bg-primary/10 text-primary px-3 py-1 rounded-full text-sm">AgTech</span>
                            <span class="bg-primary/10 text-primary px-3 py-1 rounded-full text-sm">AI/ML</span>
                            <span class="bg-primary/10 text-primary px-3 py-1 rounded-full text-sm">B2B</span>
                        </div>
                        
                        <div class="text-sm text-gray-500 dark:text-gray-400 mb-4">
                            <span class="font-semibold">Tech:</span> Flutter, Python, TensorFlow
                        </div>
                        
                        <button class="w-full gradient-bg text-white py-2 rounded-lg font-semibold hover:scale-105 transition-transform">
                            Ver Detalhes
                        </button>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Modal atualizado do HireTrack com todas as informações detalhadas -->
<div id="hiretrack-modal" class="project-modal">
  <div class="modal-content p-8 m-4">
    <div class="flex justify-between items-center mb-6">
      <h2 class="text-2xl font-bold gradient-text">HireTrack - Sistema de Gestão Ágil de Processos Seletivos</h2>
      <button onclick="closeModal('hiretrack')" class="text-2xl hover:text-primary">×</button>
    </div>

    <div class="space-y-6 text-gray-600 dark:text-gray-400">
      <div>
        <h3 class="text-xl font-bold mb-2">📌 Visão geral e problema</h3>
        <p>Como Product Owner, identifiquei que startups e PMEs enfrentam dificuldades para estruturar seus processos seletivos. Criei uma plataforma SaaS colaborativa, visual e eficiente para organizar o funil de candidatos e melhorar decisões de contratação.</p>
      </div>

      <div>
        <h3 class="text-xl font-bold mb-2">👤 Personas</h3>
        <ul class="list-disc list-inside space-y-2">
          <li><strong>Ana, Recrutadora (32 anos):</strong> Gerencia múltiplos processos seletivos, precisa de comunicação fluida e centralizada.</li>
          <li><strong>Carlos, Gestor de TI (45 anos):</strong> Participa apenas nas etapas finais, busca informações organizadas.</li>
          <li><strong>Eduardo, CEO de Startup (38 anos):</strong> Quer agilidade e visibilidade dos KPIs sem envolvimento operacional.</li>
        </ul>
      </div>

      <div>
        <h3 class="text-xl font-bold mb-2">🧭 Mapa de stakeholders</h3>
        <p><strong>Primários:</strong> Recrutadores, Gestores, Candidatos<br>
           <strong>Secundários:</strong> TI, Financeiro, CEO<br>
           <strong>Influenciadores:</strong> Consultores de RH e analistas externos</p>
      </div>

      <div>
        <h3 class="text-xl font-bold mb-2">🔁 Jornadas do usuário</h3>
        <p><strong>Recrutador:</strong> Criação da vaga → Triagem Kanban → Entrevista → Métricas<br>
           <strong>Gestor:</strong> Shortlist → Avaliação → Parecer<br>
           <strong>Candidato:</strong> Aplicação → Atualizações → Entrevista → Feedback</p>
      </div>

      <div>
        <h3 class="text-xl font-bold mb-2">🖥️ Protótipos de telas</h3>
        <div class="mb-4">
          <a href="https://miro.com/app/board/uXjVIsR2Lzo=/?share_link_id=294230524810" target="_blank" class="block">
            <img 
              src="https://pfst.cf2.poecdn.net/base/image/ec93566155dc25d9222aae4bab6bfdc8bab4d3eb050ec79d4e999fcf44c31dfa?w=1850&h=781" 
              alt="Protótipos das telas do HireTrack no Miro" 
              class="w-full rounded-lg border-2 border-gray-200 dark:border-gray-600 cursor-pointer hover:scale-105 transition-transform duration-300 shadow-lg"
            />
          </a>
          <p class="text-sm text-gray-500 dark:text-gray-400 mt-2 text-center">Clique na imagem para acessar o protótipo completo no Miro</p>
        </div>
              </div>

      <div>
        <h3 class="text-xl font-bold mb-2">🎯 Roadmap</h3>
        <ul class="list-disc list-inside">
          <li><strong>Fase 1 – MVP:</strong> Cadastro de vagas, Kanban, e-mail</li>
          <li><strong>Fase 2:</strong> LinkedIn, templates de e-mail, Google Calendar</li>
          <li><strong>Fase 3:</strong> Dashboards, feedback automatizado</li>
        </ul>
      </div>

      <div>
        <h3 class="text-xl font-bold mb-2">✅ Backlog com User Stories</h3>
        <ul class="list-disc list-inside">
          <li>Como Recrutador, quero mover candidatos entre etapas do funil</li>
          <li>Como Gestor, quero visualizar apenas os finalistas</li>
          <li>Como Candidato, quero receber feedbacks automáticos</li>
        </ul>
      </div>

      <div>
        <h3 class="text-xl font-bold mb-2">📈 KPIs e OKRs</h3>
        <ul class="list-disc list-inside">
          <li><strong>OKR:</strong> Aumentar eficiência do processo</li>
          <li>KR: Reduzir tempo médio de contratação de 30 para 20 dias</li>
          <li>KR: Aumentar resposta de candidatos em 40%</li>
          <li><strong>KPIs:</strong> tempo por etapa, conversão, candidatos por vaga, NPS</li>
        </ul>
      </div>

      <div>
        <h3 class="text-xl font-bold mb-2">🛠️ Stack sugerida e métodos</h3>
        <p><strong>Front-end:</strong> React.js + Tailwind CSS<br>
           <strong>Back-end:</strong> Node.js + Express<br>
           <strong>DB:</strong> MongoDB<br>
           <strong>Infra:</strong> Render<br>
           <strong>Ferramentas:</strong> Figma, Jira, Notion, Slack<br>
           <strong>Metodologias:</strong> Scrum quinzenal, Design Thinking</p>
      </div>
    </div>
  </div>
</div>

<!-- Image Modal -->
<div id="image-modal" class="image-modal">
  <div class="image-modal-content">
    <div class="image-modal-close" onclick="closeImageModal()">×</div>
    <img id="modal-image" src="" alt="" />
  </div>
</div>

<!-- Modal completo do projeto CriptoPoupança -->
<div id="cripto-modal" class="project-modal">
  <div class="modal-content p-8 m-4">
    <div class="flex justify-between items-center mb-6">
      <h2 class="text-2xl font-bold gradient-text">CriptoPoupança – Microinvestimentos Automatizados</h2>
      <button onclick="closeModal('cripto')" class="text-2xl hover:text-primary">×</button>
    </div>
    <div class="space-y-6 text-gray-600 dark:text-gray-400">

      <div>
        <h3 class="text-xl font-bold mb-2">📌 Visão geral e problema</h3>
        <p>Como Product Owner, percebi que muitas pessoas queriam investir em criptomoedas, mas se sentiam inseguras, desinformadas ou achavam o processo complexo. Criei uma plataforma de microinvestimentos automatizados, com aportes recorrentes e simples, ideal para quem tem pouco tempo, conhecimento técnico ou recursos financeiros iniciais.</p>
      </div>

      <div>
        <h3 class="text-xl font-bold mb-2">👤 Personas</h3>
        <ul class="list-disc list-inside space-y-2">
          <li><strong>Lucas, Universitário (22 anos):</strong> Queria investir R$50 por mês sem se preocupar com análise de mercado.</li>
          <li><strong>Patrícia, Profissional Liberal (34 anos):</strong> Buscava diversificação com pouco tempo disponível.</li>
          <li><strong>Renato, Pai de Família (40 anos):</strong> Queria poupar para os filhos sem arriscar demais, mas sem deixar o dinheiro parado.</li>
        </ul>
      </div>

      <div>
        <h3 class="text-xl font-bold mb-2">🧭 Mapa de stakeholders</h3>
        <p><strong>Primários:</strong> Investidores iniciantes, profissionais ocupados, pais que poupam para filhos<br>
           <strong>Secundários:</strong> Corretoras parceiras, suporte jurídico e contábil<br>
           <strong>Influenciadores:</strong> Influencers de finanças, planejadores financeiros, youtubers de cripto</p>
      </div>

      <div>
        <h3 class="text-xl font-bold mb-2">🔁 Jornadas do usuário</h3>
        <p><strong>Investidor Iniciante:</strong> Cadastro → Escolha da carteira → Aporte → Projeção → Acompanhamento<br>
           <strong>Investidor Ocupado:</strong> Cadastro rápido → Sugestão automatizada → Notificações mensais → Revisão<br>
           <strong>Educador Financeiro:</strong> Cadastro → Criação de carteira pública → Divulgação → Comissão</p>
      </div>

      <div>
        <h3 class="text-xl font-bold mb-2">🖥️ Protótipos de Telas</h3>
        <div class="mb-4">
          <a href="https://miro.com/app/board/uXjVIsv74bM=/?share_link_id=610314238018" target="_blank" class="block">
            <img 
              src="https://pfst.cf2.poecdn.net/base/image/eb034a35a39d3dd62625c132721fd24c40482d6c7111b34091f1efb92a6c3d51?w=1456&h=790" 
              alt="Protótipos das telas do CriptoPoupança no Miro" 
              class="w-full rounded-lg border-2 border-gray-200 dark:border-gray-600 cursor-pointer hover:scale-105 transition-transform duration-300 shadow-lg"
            />
          </a>
          <p class="text-sm text-gray-500 dark:text-gray-400 mt-2 text-center">Clique na imagem para acessar o protótipo completo no Miro</p>
        </div>
              </div>

      <div>
        <h3 class="text-xl font-bold mb-2">🎯 Roadmap</h3>
        <ul class="list-disc list-inside">
          <li><strong>Fase 1 – MVP:</strong> Carteiras automatizadas, Pix, painel de acompanhamento</li>
          <li><strong>Fase 2:</strong> Exchanges, relatórios simplificados, chatbot</li>
          <li><strong>Fase 3:</strong> Gamificação, carteiras públicas, autenticação 2FA</li>
        </ul>
      </div>

      <div>
        <h3 class="text-xl font-bold mb-2">✅ Backlog com user stories</h3>
        <ul class="list-disc list-inside">
          <li>Como investidor, quero entender quanto posso ganhar com R$50 por mês</li>
          <li>Como usuária ocupada, quero automatizar meus investimentos</li>
          <li>Como influenciador, quero criar uma carteira pública para seguidores</li>
        </ul>
      </div>

            <div>
        <h3 class="text-xl font-bold mb-2">📈 KPIs e OKRs</h3>
        <ul class="list-disc list-inside">
          <li><strong>OKR:</strong> Democratizar o acesso a investimentos</li>
          <li>KR: 5.000 usuários ativos em 6 meses</li>
          <li>KR: Ticket médio > R$75</li>
          <li>KR: Retenção de 70% após 3 meses</li>
          <li><strong>KPIs:</strong> crescimento semanal, cancelamento de aportes, tempo médio no app, NPS</li>
        </ul>
      </div>

      <div>
        <h3 class="text-xl font-bold mb-2">🛠️ Stack sugerida e métodos</h3>
        <p><strong>Front-end:</strong> Vue.js + Vuetify<br>
           <strong>Back-end:</strong> Python (FastAPI)<br>
           <strong>Banco:</strong> PostgreSQL<br>
           <strong>Integrações:</strong> APIs de corretoras e gateways<br>
           <strong>Infra:</strong> Heroku (MVP), AWS (escala)<br>
           <strong>Métodos:</strong> Lean Startup, Scrum quinzenal</p>
      </div>

    </div>
  </div>
</div>


<!-- ReparoFácil Modal Atualizado -->
<div id="reparo-modal" class="project-modal">
  <div class="modal-content p-8 m-4">
    <div class="flex justify-between items-center mb-6">
      <h2 class="text-2xl font-bold gradient-text">ReparoFácil - Diagnóstico Inteligente Residencial</h2>
      <button onclick="closeModal('reparo')" class="text-2xl hover:text-primary">×</button>
    </div>
    <div class="space-y-6 text-gray-600 dark:text-gray-400">

      <div>
        <h3 class="text-xl font-bold mb-2">📌 Visão geral e problema</h3>
        <p>Como Product Owner, percebi que muitas pessoas enfrentam problemas domésticos simples, mas não sabem como resolvê-los ou se precisam de ajuda técnica. Criei o ReparoFácil, um aplicativo que usa IA para identificar sintomas de falhas e recomendar soluções ou profissionais qualificados, promovendo autonomia e agilidade nas decisões.</p>
      </div>

      <div>
        <h3 class="text-xl font-bold mb-2">👤 Personas</h3>
        <ul class="list-disc list-inside space-y-2">
          <li><strong>Daniela, Designer (28 anos):</strong> Mora sozinha e quer resolver pequenos reparos sem depender de terceiros.</li>
          <li><strong>João, Proprietário de imóveis (45 anos):</strong> Precisa reduzir tempo e custo com manutenções em apartamentos alugados.</li>
          <li><strong>Ana, Idosa (66 anos):</strong> Busca auxílio confiável para identificar problemas técnicos em casa sem correr riscos.</li>
        </ul>
      </div>

      <div>
        <h3 class="text-xl font-bold mb-2">🧭 Mapa de stakeholders</h3>
        <p><strong>Primários:</strong> Moradores autônomos, locadores de imóveis, idosos<br>
           <strong>Secundários:</strong> Prestadores de serviço, plataformas de marketplace<br>
           <strong>Influenciadores:</strong> Youtubers de DIY, influenciadores de vida prática e manutenção</p>
      </div>

      <div>
        <h3 class="text-xl font-bold mb-2">🔁 Jornadas do usuário</h3>
        <p><strong>Usuária Autônoma:</strong> Descreve falha → Recebe diagnóstico → Resolve sozinha ou contrata<br>
           <strong>Proprietário:</strong> Cadastro → Gerencia imóveis → Acompanha diagnósticos remotos → Encaminha serviços<br>
           <strong>Prestador de Serviço:</strong> Recebe indicações → Ganha reputação → Fideliza clientes</p>
      </div>

      <div>
        <h3 class="text-xl font-bold mb-4">🖥️ Protótipos de Telas</h3>
        <div class="mb-6">
          <a href="https://miro.com/app/board/uXjVIsoyaPE=/?share_link_id=773153796830" target="_blank" class="block">
            <img 
              src="https://pfst.cf2.poecdn.net/base/image/d49aad0ca253b9eb6faea08b6b6191d7a00f8a176792f6633e84ed30575421b1?w=1791&h=791" 
              alt="Protótipos das telas do ReparoFácil no Miro" 
              class="w-full rounded-lg border-2 border-gray-200 dark:border-gray-600 cursor-pointer hover:scale-105 transition-transform duration-300 shadow-lg"
            />
          </a>
          <p class="text-sm text-gray-500 dark:text-gray-400 mt-2 text-center">Clique na imagem para acessar o protótipo completo no Miro</p>
        </div>
      </div>

      <div>
        <h3 class="text-xl font-bold mb-2">🎯 Roadmap</h3>
        <ul class="list-disc list-inside">
          <li><strong>Fase 1 - MVP:</strong> Diagnóstico por texto e voz, sugestões básicas</li>
          <li><strong>Fase 2:</strong> Recomendação de peças, agendamento com técnicos</li>
          <li><strong>Fase 3:</strong> Integração com marketplaces, pagamento via app</li>
        </ul>
      </div>

      <div>
        <h3 class="text-xl font-bold mb-2">✅ Backlog com user stories</h3>
        <ul class="list-disc list-inside">
          <li>Como moradora sozinha, quero saber se um problema é grave ou não</li>
          <li>Como proprietário, quero ter um histórico por imóvel</li>
          <li>Como técnico, quero receber alertas de chamados próximos</li>
        </ul>
      </div>

          <div>
        <h3 class="text-xl font-bold mb-2">📈 KPIs e OKRs</h3>
        <ul class="list-disc list-inside">
          <li><strong>OKR:</strong> Reduzir visitas técnicas desnecessárias</li>
          <li>KR: 15 mil diagnósticos no trimestre</li>
          <li>KR: 50 técnicos parceiros em regiões piloto</li>
          <li><strong>KPIs:</strong> taxa de conversão de diagnósticos, tempo médio de resolução, NPS, feedback positivo > 85%</li>
        </ul>
      </div>

      <div>
        <h3 class="text-xl font-bold mb-2">🛠️ Stack sugerida e métodos</h3>
        <p><strong>Front-end:</strong> React Native<br>
           <strong>Back-end:</strong> Node.js (NestJS)<br>
           <strong>Banco:</strong> MongoDB<br>
           <strong>IA:</strong> OpenAI API + classificadores treinados<br>
           <strong>Infra:</strong> Firebase + Vercel<br>
           <strong>Métodos:</strong> Design Thinking, MVP Lean, Scrum semanal</p>
      </div>

    </div>
  </div>
</div>

<!-- AgroIA Modal Atualizado -->
<div id="agro-modal" class="project-modal">
  <div class="modal-content p-8 m-4">
    <div class="flex justify-between items-center mb-6">
      <h2 class="text-2xl font-bold gradient-text">AgroIA - Assistente de Cultivo Inteligente</h2>
      <button onclick="closeModal('agro')" class="text-2xl hover:text-primary">×</button>
    </div>
    <div class="space-y-6 text-gray-600 dark:text-gray-400">

      <div>
        <h3 class="text-xl font-bold mb-2">📌 Visão geral e problema</h3>
        <p>Como Product Owner, percebi que pequenos e médios produtores rurais enfrentam dificuldades para tomar decisões técnicas com base em dados. Criei o AgroIA para oferecer um assistente inteligente que analisa solo, clima e histórico agrícola, otimizando as decisões de plantio, irrigação e colheita.</p>
      </div>

      <div>
        <h3 class="text-xl font-bold mb-2">👤 Personas</h3>
        <ul class="list-disc list-inside space-y-2">
          <li><strong>Seu Pedro, Agricultor (63 anos):</strong> Quer modernizar sua produção com ajuda simples e prática.</li>
          <li><strong>Marina, Engenheira Agrônoma (31 anos):</strong> Atende cooperativas e precisa tomar decisões técnicas com base em dados.</li>
          <li><strong>Rafael, Produtor Familiar (26 anos):</strong> Quer aumentar produtividade sem gastar com consultoria externa.</li>
        </ul>
      </div>

      <div>
        <h3 class="text-xl font-bold mb-2">🧭 Mapa de stakeholders</h3>
        <p><strong>Primários:</strong> Produtores rurais, engenheiros agrônomos, cooperativas<br>
           <strong>Secundários:</strong> Fornecedores de insumos, agências de extensão<br>
           <strong>Influenciadores:</strong> Canais de agro no YouTube, agrônomos influentes, sindicatos rurais</p>
      </div>

      <div>
        <h3 class="text-xl font-bold mb-2">🔁 Jornadas do usuário</h3>
        <p><strong>Agricultor:</strong> Cadastro → Escolhe cultura → Recebe recomendações → Monitora resultados<br>
           <strong>Agrônoma:</strong> Cria perfis de clientes → Analisa recomendações → Gera relatórios<br>
           <strong>Cooperativa:</strong> Integra dados → Gerencia lotes → Compartilha insights</p>
      </div>

      <div>
        <h3 class="text-xl font-bold mb-4">🖥️ Protótipos de Telas</h3>
        <div class="mb-6">
          <a href="https://miro.com/app/board/uXjVIsR_bZk=/?share_link_id=144931867761" target="_blank" class="block">
            <img 
              src="https://pfst.cf2.poecdn.net/base/image/f921f8cc2d2961016965d187e3fe2f4c6906a8b70622eddb970d362161be43a4?w=1845&h=1028" 
              alt="Protótipos das telas do AgroIA no Miro" 
              class="w-full rounded-lg border-2 border-gray-200 dark:border-gray-600 cursor-pointer hover:scale-105 transition-transform duration-300 shadow-lg"
            />
          </a>
          <p class="text-sm text-gray-500 dark:text-gray-400 mt-2 text-center">Clique na imagem para acessar o protótipo completo no Miro</p>
        </div>
      </div>

      <div>
        <h3 class="text-xl font-bold mb-2">🎯 Roadmap</h3>
        <ul class="list-disc list-inside">
          <li><strong>Fase 1 - MVP:</strong> Análise de solo + clima em tempo real</li>
          <li><strong>Fase 2:</strong> Integração com sensores de campo, alertas de pragas</li>
          <li><strong>Fase 3:</strong> Previsão de safra e indicadores de lucro</li>
        </ul>
      </div>

      <div>
        <h3 class="text-xl font-bold mb-2">✅ Backlog com user stories</h3>
        <ul class="list-disc list-inside">
          <li>Como agricultor, quero saber o melhor dia para irrigar</li>
          <li>Como engenheira, quero alertas sobre pragas em clientes</li>
          <li>Como cooperativa, quero relatórios automáticos por lote</li>
        </ul>
      </div>

      <div>
        <h3 class="text-xl font-bold mb-2">🎨 Protótipos simulados</h3>
        <pre class="bg-gray-100 dark:bg-gray-800 p-4 rounded-lg text-sm overflow-x-auto">
[ Cultura Selecionada: Milho ]
- Umidade ideal do solo: 40% a 55%
- Última leitura: 37%
- Sugestão: Irrigar 12mm nas próximas 24h

[ Alerta Ativo ]
⚠️ Risco de praga detectado (Lagarta do cartucho)
📍 Local: Lote 3 - Talhão A
📅 Data: 20/05</pre>
      </div>

      <div>
        <h3 class="text-xl font-bold mb-2">📈 KPIs e OKRs</h3>
        <ul class="list-disc list-inside">
          <li><strong>OKR:</strong> Aumentar a produtividade agrícola com uso de IA</li>
          <li>KR: 1.000 hectares monitorados</li>
          <li>KR: Redução de 20% no uso de água</li>
          <li>KR: 500 alertas preventivos emitidos</li>
          <li><strong>KPIs:</strong> taxa de adesão por cultura, precisão dos alertas, feedback de técnicos, NPS</li>
        </ul>
      </div>

      <div>
        <h3 class="text-xl font-bold mb-2">🛠️ Stack sugerida e métodos</h3>
        <p><strong>Front-end:</strong> React + Leaflet<br>
           <strong>Back-end:</strong> Python (Django)<br>
           <strong>Banco:</strong> PostgreSQL + PostGIS<br>
           <strong>IA:</strong> Modelos de previsão climática e diagnósticos de solo<br>
           <strong>Infra:</strong> Google Cloud + IoT Core<br>
           <strong>Métodos:</strong> Agile Kanban + MVP incremental</p>
      </div>

    </div>
  </div>
</div>

    <!-- Skills Section -->
    <section id="habilidades" class="py-20 bg-gray-50 dark:bg-gray-800">
        <div class="container mx-auto px-6">
            <div class="text-center mb-16">
                <h2 class="text-3xl md:text-4xl font-bold mb-4">
                    <span class="gradient-text">Habilidades</span>
                </h2>
                <p class="text-xl text-gray-600 dark:text-gray-400">Competências técnicas e estratégicas</p>
            </div>
            
            <div class="grid md:grid-cols-3 gap-8 mb-16">
                <!-- Estratégia de Produto -->
                <div class="bg-white dark:bg-gray-900 p-6 rounded-lg shadow-lg">
                    <h3 class="text-xl font-bold mb-6 gradient-text">Estratégia de Produto</h3>
                    <div class="space-y-4">
                        <div>
                            <div class="flex justify-between mb-2">
                                <span>Roadmapping</span>
                                <span>95%</span>
                            </div>
                            <div class="w-full bg-gray-200 dark:bg-gray-700 rounded-full h-2">
                                <div class="skill-bar bg-gradient-to-r from-primary to-accent h-2 rounded-full" data-width="95"></div>
                            </div>
                        </div>
                        <div>
                            <div class="flex justify-between mb-2">
                                <span>MVP Design</span>
                                <span>90%</span>
                            </div>
                            <div class="w-full bg-gray-200 dark:bg-gray-700 rounded-full h-2">
                                <div class="skill-bar bg-gradient-to-r from-primary to-accent h-2 rounded-full" data-width="90"></div>
                            </div>
                        </div>
                        <div>
                            <div class="flex justify-between mb-2">
                                <span>Business Model</span>
                                <span>85%</span>
                            </div>
                            <div class="w-full bg-gray-200 dark:bg-gray-700 rounded-full h-2">
                                <div class="skill-bar bg-gradient-to-r from-primary to-accent h-2 rounded-full" data-width="85"></div>
                            </div>
                        </div>
                        <div>
                            <div class="flex justify-between mb-2">
                                <span>User Research</span>
                                <span>88%</span>
                            </div>
                            <div class="w-full bg-gray-200 dark:bg-gray-700 rounded-full h-2">
                                <div class="skill-bar bg-gradient-to-r from-primary to-accent h-2 rounded-full" data-width="88"></div>
                            </div>
                        </div>
                    </div>
                </div>
                
                <!-- Execução Ágil -->
                <div class="bg-white dark:bg-gray-900 p-6 rounded-lg shadow-lg">
                    <h3 class="text-xl font-bold mb-6 gradient-text">Execução Ágil</h3>
                    <div class="space-y-4">
                        <div>
                            <div class="flex justify-between mb-2">
                                <span>Scrum Master</span>
                                <span>92%</span>
                            </div>
                            <div class="w-full bg-gray-200 dark:bg-gray-700 rounded-full h-2">
                                <div class="skill-bar bg-gradient-to-r from-primary to-accent h-2 rounded-full" data-width="92"></div>
                            </div>
                        </div>
                        <div>
                            <div class="flex justify-between mb-2">
                                <span>Backlog Management</span>
                                <span>95%</span>
                            </div>
                            <div class="w-full bg-gray-200 dark:bg-gray-700 rounded-full h-2">
                                <div class="skill-bar bg-gradient-to-r from-primary to-accent h-2 rounded-full" data-width="95"></div>
                            </div>
                        </div>
                        <div>
                            <div class="flex justify-between mb-2">
                                <span>Sprint Planning</span>
                                <span>90%</span>
                            </div>
                            <div class="w-full bg-gray-200 dark:bg-gray-700 rounded-full h-2">
                                <div class="skill-bar bg-gradient-to-r from-primary to-accent h-2 rounded-full" data-width="90"></div>
                            </div>
                        </div>
                        <div>
                            <div class="flex justify-between mb-2">
                                <span>Stakeholder Management</span>
                                <span>87%</span>
                            </div>
                            <div class="w-full bg-gray-200 dark:bg-gray-700 rounded-full h-2">
                                <div class="skill-bar bg-gradient-to-r from-primary to-accent h-2 rounded-full" data-width="87"></div>
                            </div>
                        </div>
                    </div>
                </div>
                
                <!-- Análise e Ferramentas -->
                <div class="bg-white dark:bg-gray-900 p-6 rounded-lg shadow-lg">
                    <h3 class="text-xl font-bold mb-6 gradient-text">Análise e Ferramentas</h3>
                    <div class="space-y-4">
                        <div>
                            <div class="flex justify-between mb-2">
                                <span>Data Analytics</span>
                                <span>85%</span>
                            </div>
                            <div class="w-full bg-gray-200 dark:bg-gray-700 rounded-full h-2">
                                <div class="skill-bar bg-gradient-to-r from-primary to-accent h-2 rounded-full" data-width="85"></div>
                            </div>
                        </div>
                        <div>
                            <div class="flex justify-between mb-2">
                                <span>A/B Testing</span>
                                <span>80%</span>
                            </div>
                            <div class="w-full bg-gray-200 dark:bg-gray-700 rounded-full h-2">
                                <div class="skill-bar bg-gradient-to-r from-primary to-accent h-2 rounded-full" data-width="80"></div>
                            </div>
                        </div>
                        <div>
                            <div class="flex justify-between mb-2">
                                <span>UX Research</span>
                                <span>88%</span>
                            </div>
                            <div class="w-full bg-gray-200 dark:bg-gray-700 rounded-full h-2">
                                <div class="skill-bar bg-gradient-to-r from-primary to-accent h-2 rounded-full" data-width="88"></div>
                            </div>
                        </div>
                        <div>
                            <div class="flex justify-between mb-2">
                                <span>Market Analysis</span>
                                <span>83%</span>
                            </div>
                            <div class="w-full bg-gray-200 dark:bg-gray-700 rounded-full h-2">
                                <div class="skill-bar bg-gradient-to-r from-primary to-accent h-2 rounded-full" data-width="83"></div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
            
            <!-- Tools & Technologies -->
            <div class="text-center">
                <h3 class="text-2xl font-bold mb-8 gradient-text">Ferramentas & Tecnologias</h3>
                <div class="grid grid-cols-3 md:grid-cols-6 lg:grid-cols-8 gap-6">
                   
                    <div class="tool-icon flex flex-col items-center">
                        <i class='bx bx-notepad text-4xl text-gray-600 dark:text-gray-400 mb-2'></i>
                        <span class="text-sm">Jira</span>
                    </div>
                    <div class="tool-icon flex flex-col items-center">
                        <i class='bx bx-layout text-4xl text-gray-600 dark:text-gray-400 mb-2'></i>
                        <span class="text-sm">Figma</span>
                    </div>
                    <div class="tool-icon flex flex-col items-center">
                        <i class='bx bx-bar-chart-alt text-4xl text-gray-600 dark:text-gray-400 mb-2'></i>
                        <span class="text-sm">Analytics</span>
                    </div>
                    <div class="tool-icon flex flex-col items-center">
                        <i class='bx bx-table text-4xl text-gray-600 dark:text-gray-400 mb-2'></i>
                        <span class="text-sm">Trello</span>
                    </div>
                    <div class="tool-icon flex flex-col items-center">
                        <i class='bx bx-user-check text-4xl text-gray-600 dark:text-gray-400 mb-2'></i>
                        <span class="text-sm">Miro</span>
                    </div>
                    <div class="tool-icon flex flex-col items-center">
                        <i class='bx bx-git-branch text-4xl text-gray-600 dark:text-gray-400 mb-2'></i>
                        <span class="text-sm">Git</span>
                    </div>
                    <div class="tool-icon flex flex-col items-center">
                        <i class='bx bx-code-curly text-4xl text-gray-600 dark:text-gray-400 mb-2'></i>
                        <span class="text-sm">SQL</span>
                    </div>
                     <div class="tool-icon flex flex-col items-center">
                        <i class='bx bxl-slack text-4xl text-gray-600 dark:text-gray-400 mb-2'></i>
                        <span class="text-sm">Slack</span>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Contact Section -->
    <section id="contato" class="py-20">
        <div class="container mx-auto px-6">
            <div class="text-center mb-16">
                <h2 class="text-3xl md:text-4xl font-bold mb-4">
                    <span class="gradient-text">Contato</span>
                </h2>
                <p class="text-xl text-gray-600 dark:text-gray-400">Vamos conversar sobre seu próximo projeto</p>
            </div>
            
            <div class="grid md:grid-cols-3 gap-8 max-w-4xl mx-auto">
                <!-- Email -->
                <div class="text-center p-6 bg-white dark:bg-gray-800 rounded-lg shadow-lg hover:shadow-xl transition-shadow">
                    <div class="w-16 h-16 gradient-bg rounded-full flex items-center justify-center mx-auto mb-4">
                        <i class='bx bx-envelope text-white text-2xl'></i>
                    </div>
                    <h3 class="text-xl font-bold mb-2">Email</h3>
                    <p class="text-gray-600 dark:text-gray-400 mb-4">Envie-me uma mensagem</p>
                    <a href="mailto:waltercreator@gmail.com" class="gradient-bg text-white px-6 py-2 rounded-lg font-semibold hover:scale-105 transition-transform inline-block">
                        Enviar Email
                    </a>
                </div>
                
                <!-- LinkedIn -->
                <div class="text-center p-6 bg-white dark:bg-gray-800 rounded-lg shadow-lg hover:shadow-xl transition-shadow">
                    <div class="w-16 h-16 gradient-bg rounded-full flex items-center justify-center mx-auto mb-4">
                        <i class='bx bxl-linkedin text-white text-2xl'></i>
                    </div>
                    <h3 class="text-xl font-bold mb-2">LinkedIn</h3>
                    <p class="text-gray-600 dark:text-gray-400 mb-4">Conecte-se comigo</p>
                    <a href="https://www.linkedin.com/in/waltersantiagoscrummasterproductowner/" target="_blank" class="gradient-bg text-white px-6 py-2 rounded-lg font-semibold hover:scale-105 transition-transform inline-block">
                        Conectar
                    </a>
                </div>
                
               <!-- WhatsApp -->
<div class="text-center p-6 bg-white dark:bg-gray-800 rounded-lg shadow-lg hover:shadow-xl transition-shadow">
    <div class="w-16 h-16 gradient-bg rounded-full flex items-center justify-center mx-auto mb-4">
        <i class='bx bxl-whatsapp text-white text-2xl'></i>
    </div>
    <h3 class="text-xl font-bold mb-2">WhatsApp</h3>
    <p class="text-gray-600 dark:text-gray-400 mb-4">Fale comigo diretamente</p>
    <a href="https://wa.me/5584981897143" target="_blank" class="gradient-bg text-white px-6 py-2 rounded-lg font-semibold hover:scale-105 transition-transform inline-block">
        Enviar Mensagem
    </a>
</div>
            </div>
        </div>
    </section>

    <!-- Footer -->
    <footer class="bg-gray-900 dark:bg-black text-white py-12">
        <div class="container mx-auto px-6">
            <div class="text-center">
                <div class="flex items-center justify-center space-x-2 mb-4">
                    <div class="w-8 h-8 gradient-bg rounded-lg flex items-center justify-center">
                        <i class='bx bx-brain text-white'></i>
                    </div>
                    <span class="text-xl font-bold">Walter Santiago</span>
                </div>
                <p class="text-gray-400 mb-6">Product Owner Estratégico</p>
                    
                <!-- Back to Top -->
                <button id="back-to-top" class="gradient-bg text-white px-6 py-2 rounded-lg font-semibold hover:scale-105 transition-transform mb-6">
                    <i class='bx bx-up-arrow-alt mr-2'></i>
                    Voltar ao Topo
                </button>
                
                <div class="border-t border-gray-800 pt-6">
                    <p class="text-gray-400 text-sm">
                        © <span id="current-year"></span> Walter Santiago. Todos os direitos reservados.
                    </p>
                </div>
            </div>
        </div>
    </footer>

    <script>
        // Dark Mode
        function initDarkMode() {
            if (window.matchMedia && window.matchMedia('(prefers-color-scheme: dark)').matches) {
                document.documentElement.classList.add('dark');
            }
            
            window.matchMedia('(prefers-color-scheme: dark)').addEventListener('change', event => {
                if (event.matches) {
                    document.documentElement.classList.add('dark');
                } else {
                    document.documentElement.classList.remove('dark');
                }
            });
        }

        // Theme Toggle
        function setupThemeToggle() {
            const toggleButtons = ['theme-toggle', 'mobile-theme-toggle'];
            
            toggleButtons.forEach(id => {
                document.getElementById(id).addEventListener('click', () => {
                    document.documentElement.classList.toggle('dark');
                });
            });
        }

        // Mobile Menu
        function setupMobileMenu() {
            const menuButton = document.getElementById('mobile-menu-button');
            const mobileMenu = document.getElementById('mobile-menu');
            
            menuButton.addEventListener('click', () => {
                mobileMenu.classList.toggle('hidden');
            });
            
            // Close mobile menu when clicking on a link
            const mobileLinks = mobileMenu.querySelectorAll('a');
            mobileLinks.forEach(link => {
                link.addEventListener('click', () => {
                    mobileMenu.classList.add('hidden');
                });
            });
        }

        // Progress Bar
        function setupProgressBar() {
            const progressBar = document.querySelector('.progress-bar');
            
            window.addEventListener('scroll', () => {
                const scrollTop = window.pageYOffset;
                const docHeight = document.documentElement.scrollHeight - window.innerHeight;
                const scrollPercent = (scrollTop / docHeight) * 100;
                progressBar.style.width = scrollPercent + '%';
            });
        }

        // Active Navigation
        function setupActiveNavigation() {
            const sections = document.querySelectorAll('section[id]');
            const navLinks = document.querySelectorAll('.nav-link');
            
            window.addEventListener('scroll', () => {
                let current = '';
                sections.forEach(section => {
                    const sectionTop = section.offsetTop;
                    if (window.pageYOffset >= sectionTop - 200) {
                        current = section.getAttribute('id');
                    }
                });
                
                navLinks.forEach(link => {
                    link.classList.remove('active');
                    if (link.getAttribute('href') === '#' + current) {
                        link.classList.add('active');
                    }
                });
            });
        }

        // Skill Bars Animation
        function animateSkillBars() {
            const skillBars = document.querySelectorAll('.skill-bar');
            const observer = new IntersectionObserver((entries) => {
                entries.forEach(entry => {
                    if (entry.isIntersecting) {
                        const bar = entry.target;
                        const width = bar.getAttribute('data-width');
                        setTimeout(() => {
                            bar.style.width = width + '%';
                        }, 300);
                    }
                });
            }, { threshold: 0.5 });
            
            skillBars.forEach(bar => {
                observer.observe(bar);
            });
        }

        // Project Modals
        function openModal(projectId) {
            const modal = document.getElementById(projectId + '-modal');
            modal.classList.add('active');
            document.body.style.overflow = 'hidden';
        }

        function closeModal(projectId) {
            const modal = document.getElementById(projectId + '-modal');
            modal.classList.remove('active');
            document.body.style.overflow = 'auto';
        }

        // Image Modal Functions
        function openImageModal(src, alt) {
            const modal = document.getElementById('image-modal');
            const modalImage = document.getElementById('modal-image');
            modalImage.src = src;
            modalImage.alt = alt;
            modal.classList.add('active');
            document.body.style.overflow = 'hidden';
        }

        function closeImageModal() {
            const modal = document.getElementById('image-modal');
            modal.classList.remove('active');
            document.body.style.overflow = 'auto';
        }

        // Close modal when clicking outside
        document.addEventListener('click', (e) => {
            if (e.target.classList.contains('project-modal')) {
                e.target.classList.remove('active');
                document.body.style.overflow = 'auto';
            }
            if (e.target.classList.contains('image-modal')) {
                e.target.classList.remove('active');
                document.body.style.overflow = 'auto';
            }
        });

        // Back to Top
        function setupBackToTop() {
            const backToTopButton = document.getElementById('back-to-top');
            
            backToTopButton.addEventListener('click', () => {
                window.scrollTo({ top: 0, behavior: 'smooth' });
            });
        }

        // Set Current Year
        function setCurrentYear() {
            document.getElementById('current-year').textContent = new Date().getFullYear();
        }

        // Smooth Scrolling for Navigation Links
        function setupSmoothScrolling() {
            const links = document.querySelectorAll('a[href^="#"]');
            
            links.forEach(link => {
                link.addEventListener('click', (e) => {
                    e.preventDefault();
                    const target = document.querySelector(link.getAttribute('href'));
                    if (target) {
                        target.scrollIntoView({
                            behavior: 'smooth',
                            block: 'start'
                        });
                    }
                });
            });
        }

        // Initialize all functions
        document.addEventListener('DOMContentLoaded', () => {
            initDarkMode();
            setupThemeToggle();
            setupMobileMenu();
            setupProgressBar();
            setupActiveNavigation();
            animateSkillBars();
            setupBackToTop();
            setCurrentYear();
            setupSmoothScrolling();
        });

        // Add more project modals data (simplified for brevity)
        // You can expand this with full project details
    </script>
</body>
</html>
