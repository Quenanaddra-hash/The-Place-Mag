# The-Place-Mag
Site internet pour un web magazine 
<!doctype html>
<html lang="fr" class="h-full" style="--color-bg: #0a0a0a; --color-surface: #141414; --color-text: #fafafa; --color-primary: #d4af37; --color-secondary: #737373;">
 <head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>THE PLACE — Where Talent Gets Seen</title>
  <script src="https://cdn.tailwindcss.com/3.4.17"></script>
  <script src="/_sdk/element_sdk.js"></script>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,400;0,500;0,600;0,700;1,400;1,500&amp;family=Inter:wght@300;400;500;600&amp;display=swap" rel="stylesheet">
  <style>
    :root {
      --color-bg: #0a0a0a;
      --color-surface: #141414;
      --color-text: #fafafa;
      --color-primary: #d4af37;
      --color-secondary: #737373;
    }
    * { box-sizing: border-box; }
    html, body { 
      margin: 0; 
      padding: 0; 
      height: 100%;
      background: var(--color-bg);
    }
    .font-editorial { font-family: 'Cormorant Garamond', Georgia, serif; }
    .font-sans { font-family: 'Inter', system-ui, sans-serif; }
    
    /* Animations */
    @keyframes fadeInUp {
      from { opacity: 0; transform: translateY(30px); }
      to { opacity: 1; transform: translateY(0); }
    }
    @keyframes fadeIn {
      from { opacity: 0; }
      to { opacity: 1; }
    }
    @keyframes slideIn {
      from { transform: translateX(-100%); }
      to { transform: translateX(0); }
    }
    @keyframes shimmer {
      0% { background-position: -200% 0; }
      100% { background-position: 200% 0; }
    }
    .animate-fade-in-up { animation: fadeInUp 0.8s ease-out forwards; }
    .animate-fade-in { animation: fadeIn 0.6s ease-out forwards; }
    .animate-slide-in { animation: slideIn 0.4s ease-out forwards; }
    .delay-100 { animation-delay: 0.1s; }
    .delay-200 { animation-delay: 0.2s; }
    .delay-300 { animation-delay: 0.3s; }
    .delay-400 { animation-delay: 0.4s; }
    .delay-500 { animation-delay: 0.5s; }
    
    /* Gold shimmer effect */
    .gold-shimmer {
      background: linear-gradient(90deg, var(--color-primary) 0%, #f4d03f 50%, var(--color-primary) 100%);
      background-size: 200% 100%;
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      background-clip: text;
      animation: shimmer 3s linear infinite;
    }
    
    /* Custom scrollbar */
    ::-webkit-scrollbar { width: 6px; }
    ::-webkit-scrollbar-track { background: var(--color-bg); }
    ::-webkit-scrollbar-thumb { background: var(--color-primary); border-radius: 3px; }
    
    /* Page transitions */
    .page { display: none; opacity: 0; }
    .page.active { display: block; animation: fadeIn 0.4s ease-out forwards; }
    
    /* Mobile menu */
    .mobile-menu { transform: translateX(-100%); transition: transform 0.3s ease; }
    .mobile-menu.open { transform: translateX(0); }
    
    /* Hover effects */
    .talent-card:hover .talent-overlay { opacity: 1; }
    .talent-card:hover img { transform: scale(1.05); }
    
    /* Form styles */
    input:focus, textarea:focus, select:focus {
      outline: none;
      border-color: var(--color-primary);
      box-shadow: 0 0 0 2px rgba(212, 175, 55, 0.2);
    }
  </style>
  <style>body { box-sizing: border-box; }</style>
  <script src="/_sdk/data_sdk.js" type="text/javascript"></script>
 </head>
 <body class="h-full font-sans text-white overflow-x-hidden" style="background: var(--color-bg);">
  <div id="app" class="h-full w-full overflow-auto"><!-- Navigation -->
   <nav id="navbar" class="fixed top-0 left-0 right-0 z-50 transition-all duration-300" style="background: transparent;">
    <div class="max-w-7xl mx-auto px-6 py-4">
     <div class="flex items-center justify-between"><!-- Logo --> <a href="#" onclick="navigateTo('home')" class="flex items-center gap-3 group">
       <div class="w-10 h-10 border-2 flex items-center justify-center" style="border-color: var(--color-primary); background: var(--color-primary);"><span class="font-editorial text-xl font-bold" style="color: var(--color-bg);">P</span>
       </div><span class="font-editorial text-2xl tracking-wider hidden sm:block"><span style="color: var(--color-text);">THE </span><span style="color: var(--color-primary);">P</span><span style="color: var(--color-text);">LACE</span></span> </a> <!-- Desktop Navigation -->
      <div class="hidden lg:flex items-center gap-8"><a href="#" onclick="navigateTo('about')" class="nav-link text-sm tracking-widest uppercase transition-colors hover:text-yellow-500" style="color: var(--color-secondary);">À propos</a> <a href="#" onclick="navigateTo('magazine')" class="nav-link text-sm tracking-widest uppercase transition-colors hover:text-yellow-500" style="color: var(--color-secondary);">Magazine</a> <a href="#" onclick="navigateTo('talents')" class="nav-link text-sm tracking-widest uppercase transition-colors hover:text-yellow-500" style="color: var(--color-secondary);">Talents</a> <a href="#" onclick="navigateTo('apply')" class="nav-link text-sm tracking-widest uppercase transition-colors hover:text-yellow-500" style="color: var(--color-secondary);">Candidater</a> <a href="#" onclick="navigateTo('opportunities')" class="nav-link text-sm tracking-widest uppercase transition-colors hover:text-yellow-500" style="color: var(--color-secondary);">Opportunités</a> <a href="#" onclick="navigateTo('contact')" class="px-6 py-2 text-sm tracking-widest uppercase transition-all hover:scale-105" style="background: var(--color-primary); color: var(--color-bg);">Contact</a>
      </div><!-- Mobile Menu Button --> <button onclick="toggleMobileMenu()" class="lg:hidden p-2" aria-label="Menu">
       <svg id="menu-icon" class="w-6 h-6" fill="none" stroke="currentColor" viewbox="0 0 24 24" style="color: var(--color-text);"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16" />
       </svg></button>
     </div>
    </div>
   </nav><!-- Mobile Menu -->
   <div id="mobile-menu" class="mobile-menu fixed inset-0 z-40 lg:hidden" style="background: var(--color-bg);">
    <div class="flex flex-col items-center justify-center h-full gap-8"><a href="#" onclick="navigateTo('home'); toggleMobileMenu();" class="font-editorial text-3xl" style="color: var(--color-text);">Accueil</a> <a href="#" onclick="navigateTo('about'); toggleMobileMenu();" class="font-editorial text-3xl" style="color: var(--color-text);">À propos</a> <a href="#" onclick="navigateTo('magazine'); toggleMobileMenu();" class="font-editorial text-3xl" style="color: var(--color-text);">Magazine</a> <a href="#" onclick="navigateTo('talents'); toggleMobileMenu();" class="font-editorial text-3xl" style="color: var(--color-text);">Talents</a> <a href="#" onclick="navigateTo('apply'); toggleMobileMenu();" class="font-editorial text-3xl" style="color: var(--color-text);">Candidater</a> <a href="#" onclick="navigateTo('opportunities'); toggleMobileMenu();" class="font-editorial text-3xl" style="color: var(--color-text);">Opportunités</a> <a href="#" onclick="navigateTo('contact'); toggleMobileMenu();" class="font-editorial text-3xl" style="color: var(--color-primary);">Contact</a>
    </div>
   </div><!-- ==================== HOME PAGE ==================== -->
   <div id="page-home" class="page active"><!-- Hero Section -->
    <section class="relative min-h-screen flex items-center justify-center overflow-hidden"><!-- Background Pattern -->
     <div class="absolute inset-0 opacity-5">
      <div class="absolute inset-0" style="background-image: radial-gradient(circle at 1px 1px, var(--color-primary) 1px, transparent 0); background-size: 50px 50px;"></div>
     </div><!-- Hero Content -->
     <div class="relative z-10 text-center px-6 max-w-5xl mx-auto">
      <div class="opacity-0 animate-fade-in-up"><span class="inline-block px-4 py-1 text-xs tracking-[0.3em] uppercase mb-8" style="border: 1px solid var(--color-primary); color: var(--color-primary);">Le média des talents d'exception</span>
      </div>
      <h1 id="hero-tagline" class="font-editorial text-5xl sm:text-7xl lg:text-8xl font-medium leading-tight mb-8 opacity-0 animate-fade-in-up delay-100" style="color: var(--color-text);">Where talent<br><span class="gold-shimmer">gets seen.</span></h1>
      <p id="hero-manifesto" class="text-lg sm:text-xl max-w-2xl mx-auto mb-12 leading-relaxed opacity-0 animate-fade-in-up delay-200" style="color: var(--color-secondary);">THE PLACE révèle les talents qui façonnent le monde de demain. Un média d'excellence, sélectif et ambitieux, dédié à ceux qui osent se démarquer.</p>
      <div class="flex flex-col sm:flex-row gap-4 justify-center opacity-0 animate-fade-in-up delay-300"><button onclick="navigateTo('magazine')" class="group px-8 py-4 text-sm tracking-widest uppercase transition-all hover:scale-105" style="background: var(--color-primary); color: var(--color-bg);"> Découvrir le magazine <span class="inline-block ml-2 transition-transform group-hover:translate-x-1">→</span> </button> <button onclick="navigateTo('apply')" class="px-8 py-4 text-sm tracking-widest uppercase transition-all hover:scale-105" style="border: 1px solid var(--color-primary); color: var(--color-primary); background: transparent;"> Proposer un talent </button>
      </div>
     </div><!-- Scroll Indicator -->
     <div class="absolute bottom-8 left-1/2 -translate-x-1/2 opacity-0 animate-fade-in delay-500">
      <div class="flex flex-col items-center gap-2"><span class="text-xs tracking-widest uppercase" style="color: var(--color-secondary);">Scroll</span>
       <div class="w-px h-12 animate-pulse" style="background: linear-gradient(to bottom, var(--color-primary), transparent);"></div>
      </div>
     </div>
    </section><!-- Featured Talent Section -->
    <section class="py-24 px-6" style="background: var(--color-surface);">
     <div class="max-w-7xl mx-auto">
      <div class="text-center mb-16"><span class="text-xs tracking-[0.3em] uppercase" style="color: var(--color-primary);">Édition actuelle</span>
       <h2 class="font-editorial text-4xl sm:text-5xl mt-4" style="color: var(--color-text);">Talent en couverture</h2>
      </div>
      <div class="grid lg:grid-cols-2 gap-12 items-center"><!-- Cover Image -->
       <div class="relative group flex items-center justify-center" style="min-height: 500px;">
        <div class="text-center">
         <p class="font-editorial text-3xl sm:text-4xl mb-4" style="color: var(--color-text);">Bientôt disponible</p>
         <p class="text-sm" style="color: var(--color-secondary);">La première édition arrive très bientôt.</p>
        </div>
       </div><!-- Cover Info -->
       <div class="lg:pl-8"><span class="text-xs tracking-[0.3em] uppercase" style="color: var(--color-primary);">Édition actuelle — 2026</span>
        <h3 class="font-editorial text-4xl sm:text-5xl mt-4 mb-6" style="color: var(--color-text);">Bientôt disponible</h3>
        <p class="text-lg leading-relaxed mb-6" style="color: var(--color-secondary);">Notre première édition arrive très bientôt avec une sélection de talents d'exception qui façonnent le monde de demain. Restez connectés pour découvrir notre couverture exclusive.</p>
        <div class="pl-6 my-8" style="border-left: 2px solid var(--color-primary);">
         <p class="font-editorial text-xl italic" style="color: var(--color-text);">12 talents sélectionnés • 48 pages • Une vision nouvelle du mérite</p>
        </div><button onclick="navigateTo('magazine')" class="group inline-flex items-center gap-2 text-sm tracking-widest uppercase transition-colors" style="color: var(--color-primary);"> Découvrir l'édition <span class="transition-transform group-hover:translate-x-1">→</span> </button>
       </div>
      </div>
     </div>
    </section><!-- Talents Grid -->
    <section class="py-24 px-6">
     <div class="max-w-7xl mx-auto">
      <div class="flex flex-col sm:flex-row justify-between items-start sm:items-center mb-16 gap-4">
       <div><span class="text-xs tracking-[0.3em] uppercase" style="color: var(--color-primary);">Dans cette édition</span>
        <h2 id="home-talents-title" class="font-editorial text-4xl sm:text-5xl mt-4" style="color: var(--color-text);">Talents sélectionnés</h2>
       </div><button onclick="navigateTo('talents')" class="group inline-flex items-center gap-2 text-sm tracking-widest uppercase" style="color: var(--color-primary);"> Voir tous les talents <span class="transition-transform group-hover:translate-x-1">→</span> </button>
      </div>
      <div class="grid sm:grid-cols-2 lg:grid-cols-3 gap-8"><!-- Talent Card 1 -->
       <div class="talent-card group cursor-pointer" onclick="navigateTo('talents')">
        <div class="aspect-[3/4] overflow-hidden mb-4 relative" style="background: var(--color-surface);">
         <div class="w-full h-full flex items-center justify-center transition-transform duration-500">
          <div class="text-center">
           <p class="font-editorial text-2xl" style="color: var(--color-text);">Bientôt disponible</p>
          </div>
         </div>
         <div class="talent-overlay absolute inset-0 flex items-end p-6 opacity-0 transition-opacity duration-300" style="background: linear-gradient(to top, rgba(0,0,0,0.9), transparent);"><span class="text-sm tracking-widest uppercase" style="color: var(--color-primary);">Voir le profil →</span>
         </div>
        </div><span class="text-xs tracking-wider uppercase" style="color: var(--color-primary);">Talents</span>
        <h3 class="font-editorial text-2xl mt-2" style="color: var(--color-text);">Bientôt disponible</h3>
        <p class="mt-2 text-sm" style="color: var(--color-secondary);">La première sélection arrive très bientôt</p>
       </div>
      </div>
     </div>
    </section><!-- Why THE PLACE -->
    <section class="py-24 px-6" style="background: var(--color-surface);">
     <div class="max-w-7xl mx-auto">
      <div class="text-center mb-16"><span class="text-xs tracking-[0.3em] uppercase" style="color: var(--color-primary);">Notre différence</span>
       <h2 class="font-editorial text-4xl sm:text-5xl mt-4" style="color: var(--color-text);">Pourquoi THE PLACE ?</h2>
      </div>
      <div class="grid sm:grid-cols-2 lg:grid-cols-4 gap-8">
       <div class="text-center p-8">
        <div class="w-16 h-16 mx-auto mb-6 flex items-center justify-center" style="border: 1px solid var(--color-primary);">
         <svg class="w-8 h-8" fill="none" stroke="currentColor" viewbox="0 0 24 24" style="color: var(--color-primary);"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z" />
         </svg>
        </div>
        <h3 class="font-editorial text-xl mb-3" style="color: var(--color-text);">Sélectif</h3>
        <p class="text-sm leading-relaxed" style="color: var(--color-secondary);">Une sélection rigoureuse basée sur le mérite et l'excellence</p>
       </div>
       <div class="text-center p-8">
        <div class="w-16 h-16 mx-auto mb-6 flex items-center justify-center" style="border: 1px solid var(--color-primary);">
         <svg class="w-8 h-8" fill="none" stroke="currentColor" viewbox="0 0 24 24" style="color: var(--color-primary);"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M15 12a3 3 0 11-6 0 3 3 0 016 0z" /> <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M2.458 12C3.732 7.943 7.523 5 12 5c4.478 0 8.268 2.943 9.542 7-1.274 4.057-5.064 7-9.542 7-4.477 0-8.268-2.943-9.542-7z" />
         </svg>
        </div>
        <h3 class="font-editorial text-xl mb-3" style="color: var(--color-text);">Visible</h3>
        <p class="text-sm leading-relaxed" style="color: var(--color-secondary);">Une exposition premium auprès de décideurs influents</p>
       </div>
       <div class="text-center p-8">
        <div class="w-16 h-16 mx-auto mb-6 flex items-center justify-center" style="border: 1px solid var(--color-primary);">
         <svg class="w-8 h-8" fill="none" stroke="currentColor" viewbox="0 0 24 24" style="color: var(--color-primary);"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M17 20h5v-2a3 3 0 00-5.356-1.857M17 20H7m10 0v-2c0-.656-.126-1.283-.356-1.857M7 20H2v-2a3 3 0 015.356-1.857M7 20v-2c0-.656.126-1.283.356-1.857m0 0a5.002 5.002 0 019.288 0M15 7a3 3 0 11-6 0 3 3 0 016 0zm6 3a2 2 0 11-4 0 2 2 0 014 0zM7 10a2 2 0 11-4 0 2 2 0 014 0z" />
         </svg>
        </div>
        <h3 class="font-editorial text-xl mb-3" style="color: var(--color-text);">Ouvert</h3>
        <p class="text-sm leading-relaxed" style="color: var(--color-secondary);">Accessible à tous les profils exceptionnels, sans distinction</p>
       </div>
       <div class="text-center p-8">
        <div class="w-16 h-16 mx-auto mb-6 flex items-center justify-center" style="border: 1px solid var(--color-primary);">
         <svg class="w-8 h-8" fill="none" stroke="currentColor" viewbox="0 0 24 24" style="color: var(--color-primary);"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M13 10V3L4 14h7v7l9-11h-7z" />
         </svg>
        </div>
        <h3 class="font-editorial text-xl mb-3" style="color: var(--color-text);">Impact</h3>
        <p class="text-sm leading-relaxed" style="color: var(--color-secondary);">Des opportunités concrètes et un réseau d'excellence</p>
       </div>
      </div>
     </div>
    </section><!-- Partners Section -->
    <section class="py-24 px-6">
     <div class="max-w-7xl mx-auto text-center"><span class="text-xs tracking-[0.3em] uppercase" style="color: var(--color-primary);">Ils nous font confiance</span>
      <h2 class="font-editorial text-4xl sm:text-5xl mt-4 mb-16" style="color: var(--color-text);">Nos partenaires</h2>
      <div class="flex flex-wrap justify-center items-center gap-12 opacity-50">
       <div class="text-2xl font-editorial tracking-wider" style="color: var(--color-secondary);">
        PARTNER 1
       </div>
       <div class="text-2xl font-editorial tracking-wider" style="color: var(--color-secondary);">
        PARTNER 2
       </div>
       <div class="text-2xl font-editorial tracking-wider" style="color: var(--color-secondary);">
        PARTNER 3
       </div>
       <div class="text-2xl font-editorial tracking-wider" style="color: var(--color-secondary);">
        PARTNER 4
       </div>
      </div>
      <p class="mt-12 text-sm" style="color: var(--color-secondary);">Vous souhaitez devenir partenaire ? <button onclick="navigateTo('contact')" class="underline transition-colors hover:text-yellow-500" style="color: var(--color-primary);">Contactez-nous</button></p>
     </div>
    </section><!-- CTA Section -->
    <section class="py-24 px-6" style="background: linear-gradient(135deg, rgba(212,175,55,0.1), transparent);">
     <div class="max-w-4xl mx-auto text-center">
      <h2 class="font-editorial text-4xl sm:text-5xl mb-6" style="color: var(--color-text);">Prêt à être mis en lumière ?</h2>
      <p class="text-lg mb-12" style="color: var(--color-secondary);">Rejoignez la communauté des talents d'exception et faites entendre votre voix.</p>
      <div class="flex flex-col sm:flex-row gap-4 justify-center"><button onclick="navigateTo('apply')" class="px-8 py-4 text-sm tracking-widest uppercase transition-all hover:scale-105" style="background: var(--color-primary); color: var(--color-bg);"> Candidater maintenant </button> <button onclick="navigateTo('about')" class="px-8 py-4 text-sm tracking-widest uppercase transition-all hover:scale-105" style="border: 1px solid var(--color-text); color: var(--color-text); background: transparent;"> En savoir plus </button>
      </div>
     </div>
    </section>
   </div><!-- ==================== ABOUT PAGE ==================== -->
   <div id="page-about" class="page">
    <section class="pt-32 pb-24 px-6">
     <div class="max-w-4xl mx-auto"><span class="text-xs tracking-[0.3em] uppercase" style="color: var(--color-primary);">À propos</span>
      <h1 id="about-title" class="font-editorial text-5xl sm:text-6xl mt-4 mb-12" style="color: var(--color-text);">Notre Vision</h1>
      <div class="space-y-8 text-lg leading-relaxed" style="color: var(--color-secondary);">
       <p class="first-letter:text-6xl first-letter:font-editorial first-letter:float-left first-letter:mr-4 first-letter:leading-none" style="color: var(--color-text);">THE PLACE est né d'une conviction simple : le talent mérite d'être vu. Dans un monde saturé d'informations, les profils d'exception peinent à se démarquer. Nous avons créé un espace où l'excellence trouve sa lumière.</p>
       <p>Notre mission est de révéler les talents qui façonnent le monde de demain. Nous croyons au mérite, à l'audace et à la persévérance. Chaque portrait publié dans nos pages raconte une histoire unique, un parcours inspirant, une vision qui compte.</p>
       <div class="my-16 p-8" style="background: var(--color-surface); border-left: 3px solid var(--color-primary);">
        <h3 class="font-editorial text-2xl mb-6" style="color: var(--color-text);">Notre positionnement</h3>
        <ul class="space-y-4">
         <li class="flex items-start gap-4"><span style="color: var(--color-primary);">✦</span> <span><strong class="text-white">Ouvert à tous</strong> — Pas de critère d'école, de réseau ou d'origine. Seul le talent compte.</span></li>
         <li class="flex items-start gap-4"><span style="color: var(--color-primary);">✦</span> <span><strong class="text-white">Sélectif dans la mise en avant</strong> — Chaque édition ne présente qu'un nombre limité de profils, garantissant qualité et impact.</span></li>
         <li class="flex items-start gap-4"><span style="color: var(--color-primary);">✦</span> <span><strong class="text-white">Ambitieux dans notre vision</strong> — Nous construisons bien plus qu'un magazine : un écosystème de talents.</span></li>
        </ul>
       </div>
       <p>Nos valeurs fondamentales guident chacune de nos décisions : le mérite avant tout, l'excellence comme standard, la visibilité comme récompense, l'impact comme objectif.</p>
       <div class="mt-16 pt-16" style="border-top: 1px solid var(--color-surface);">
        <blockquote class="font-editorial text-3xl sm:text-4xl italic text-center" style="color: var(--color-text);">
         "Le talent n'attend pas qu'on le découvre.<br>
          Il mérite qu'on le révèle."
        </blockquote>
        <p class="text-center mt-6 text-sm tracking-widest uppercase" style="color: var(--color-primary);">— Quenan Addra</p>
       </div>
      </div>
     </div>
    </section>
   </div><!-- ==================== MAGAZINE PAGE ==================== -->
   <div id="page-magazine" class="page">
    <section class="pt-32 pb-24 px-6">
     <div class="max-w-7xl mx-auto">
      <div class="text-center mb-16"><span class="text-xs tracking-[0.3em] uppercase" style="color: var(--color-primary);">Publications</span>
       <h1 class="font-editorial text-5xl sm:text-6xl mt-4" style="color: var(--color-text);">Le Magazine</h1>
       <p class="mt-6 max-w-2xl mx-auto" style="color: var(--color-secondary);">Découvrez nos éditions et les talents d'exception qui font notre ligne éditoriale.</p>
      </div>
      <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-8"><!-- Magazine Issue 1 -->
       <article class="group">
        <div class="aspect-[3/4] mb-6 overflow-hidden relative" style="background: linear-gradient(135deg, #1a1a1a, #2a2a2a);">
         <div class="absolute inset-0 flex flex-col items-center justify-center p-8 text-center"><span class="text-xs tracking-[0.3em] uppercase mb-4" style="color: var(--color-primary);">Édition actuelle</span>
          <h3 class="font-editorial text-4xl mb-2" style="color: var(--color-text);">THE PLACE</h3>
          <p class="text-sm" style="color: var(--color-secondary);">Bientôt disponible</p>
          <div class="w-24 h-24 mt-8 rounded-full flex items-center justify-center" style="background: var(--color-primary);"><span class="font-editorial text-3xl" style="color: var(--color-bg);">?</span>
          </div>
          <p class="mt-4 font-editorial text-lg" style="color: var(--color-text);">Bientôt disponible</p>
         </div>
         <div class="absolute top-4 right-4 px-3 py-1 text-xs" style="background: var(--color-primary); color: var(--color-bg);">
          À VENIR
         </div>
        </div>
        <div class="flex justify-between items-start">
         <div>
          <h4 class="font-editorial text-xl" style="color: var(--color-text);">Édition actuelle</h4>
          <p class="text-sm mt-1" style="color: var(--color-secondary);">Bientôt disponible</p>
         </div><button class="px-4 py-2 text-xs tracking-wider uppercase transition-colors hover:bg-yellow-600" style="background: var(--color-secondary); color: var(--color-bg);" disabled> À venir </button>
        </div>
        <div class="mt-4">
         <p class="text-sm" style="color: var(--color-secondary);">Prochainement sur THE PLACE...</p>
        </div>
       </article><!-- Coming Soon Issues -->
       <article class="group opacity-60">
        <div class="aspect-[3/4] mb-6 overflow-hidden relative flex items-center justify-center" style="background: var(--color-surface); border: 1px dashed var(--color-secondary);">
         <div class="text-center">
          <h3 class="font-editorial text-2xl mt-2" style="color: var(--color-secondary);">Bientôt disponible</h3>
         </div>
        </div>
        <h4 class="font-editorial text-xl" style="color: var(--color-secondary);">Prochaine édition</h4>
        <p class="text-sm mt-1" style="color: var(--color-secondary);">Bientôt disponible</p>
       </article>
       <article class="group opacity-40">
        <div class="aspect-[3/4] mb-6 overflow-hidden relative flex items-center justify-center" style="background: var(--color-surface); border: 1px dashed var(--color-secondary);">
         <div class="text-center">
          <h3 class="font-editorial text-2xl mt-2" style="color: var(--color-secondary);">Bientôt disponible</h3>
         </div>
        </div>
        <h4 class="font-editorial text-xl" style="color: var(--color-secondary);">Édition à venir</h4>
        <p class="text-sm mt-1" style="color: var(--color-secondary);">Bientôt disponible</p>
       </article>
      </div><!-- Premium Access -->
      <div class="mt-24 p-12 text-center" style="background: var(--color-surface);"><span class="text-xs tracking-[0.3em] uppercase" style="color: var(--color-primary);">Accès Premium</span>
       <h3 class="font-editorial text-3xl mt-4 mb-4" style="color: var(--color-text);">Ne manquez aucune édition</h3>
       <p class="max-w-xl mx-auto mb-8" style="color: var(--color-secondary);">Inscrivez-vous pour recevoir chaque nouvelle édition directement dans votre boîte mail.</p>
       <div class="flex flex-col sm:flex-row gap-4 justify-center max-w-md mx-auto"><input type="email" placeholder="votre@email.com" class="flex-1 px-4 py-3 text-sm" style="background: var(--color-bg); border: 1px solid var(--color-secondary); color: var(--color-text);"> <button class="px-6 py-3 text-sm tracking-wider uppercase transition-all hover:scale-105" style="background: var(--color-primary); color: var(--color-bg);"> S'inscrire </button>
       </div>
      </div>
     </div>
    </section>
   </div><!-- ==================== TALENTS PAGE ==================== -->
   <div id="page-talents" class="page">
    <section class="pt-32 pb-24 px-6">
     <div class="max-w-7xl mx-auto">
      <div class="text-center mb-16"><span class="text-xs tracking-[0.3em] uppercase" style="color: var(--color-primary);">Galerie</span>
       <h1 id="talents-title" class="font-editorial text-5xl sm:text-6xl mt-4" style="color: var(--color-text);">Nos Talents</h1>
       <p class="mt-6 max-w-2xl mx-auto" style="color: var(--color-secondary);">Découvrez les profils d'exception qui ont été mis en lumière par THE PLACE.</p>
      </div><!-- Filter -->
      <div class="flex flex-wrap justify-center gap-4 mb-12"><button class="talent-filter active px-4 py-2 text-xs tracking-wider uppercase transition-colors" style="background: var(--color-primary); color: var(--color-bg);" onclick="filterTalents('all')">Tous</button> <button class="talent-filter px-4 py-2 text-xs tracking-wider uppercase transition-colors" style="border: 1px solid var(--color-secondary); color: var(--color-secondary);" onclick="filterTalents('tech')">Tech</button> <button class="talent-filter px-4 py-2 text-xs tracking-wider uppercase transition-colors" style="border: 1px solid var(--color-secondary); color: var(--color-secondary);" onclick="filterTalents('droit')">Droit</button> <button class="talent-filter px-4 py-2 text-xs tracking-wider uppercase transition-colors" style="border: 1px solid var(--color-secondary); color: var(--color-secondary);" onclick="filterTalents('business')">Business</button> <button class="talent-filter px-4 py-2 text-xs tracking-wider uppercase transition-colors" style="border: 1px solid var(--color-secondary); color: var(--color-secondary);" onclick="filterTalents('creatif')">Créatif</button>
      </div><!-- Talents Grid -->
      <div id="talents-grid" class="grid sm:grid-cols-2 lg:grid-cols-4 gap-6"><!-- All Bientôt disponible -->
       <div class="talent-item sm:col-span-2 sm:row-span-2" data-category="all">
        <div class="relative h-full group cursor-pointer flex items-center justify-center" style="min-height: 500px; background: var(--color-surface);">
         <div class="text-center">
          <p class="font-editorial text-3xl" style="color: var(--color-text);">Bientôt disponible</p>
         </div>
        </div>
       </div>
      </div>
     </div>
    </section>
   </div><!-- ==================== APPLY PAGE ==================== -->
   <div id="page-apply" class="page">
    <section class="pt-32 pb-24 px-6">
     <div class="max-w-4xl mx-auto">
      <div class="text-center mb-16"><span class="text-xs tracking-[0.3em] uppercase" style="color: var(--color-primary);">Rejoignez-nous</span>
       <h1 class="font-editorial text-5xl sm:text-6xl mt-4" style="color: var(--color-text);">Candidater</h1>
       <p class="mt-6 max-w-2xl mx-auto" style="color: var(--color-secondary);">Deux façons de nous rejoindre : proposer votre talent ou contribuer un article au magazine. THE PLACE est un média participatif dédié à l'excellence.</p>
      </div>
      <div class="grid lg:grid-cols-2 gap-12"><!-- Info Section -->
       <div class="space-y-8">
        <div id="info-talent" class="p-6" style="background: var(--color-surface);">
         <h3 class="font-editorial text-xl mb-4" style="color: var(--color-primary);">Qui peut candidater ?</h3>
         <ul class="space-y-3 text-sm" style="color: var(--color-secondary);">
          <li class="flex items-start gap-3"><span style="color: var(--color-primary);">✦</span> <span>Étudiants et jeunes diplômés à fort potentiel</span></li>
          <li class="flex items-start gap-3"><span style="color: var(--color-primary);">✦</span> <span>Entrepreneurs et créateurs d'entreprise</span></li>
          <li class="flex items-start gap-3"><span style="color: var(--color-primary);">✦</span> <span>Professionnels aux parcours remarquables</span></li>
          <li class="flex items-start gap-3"><span style="color: var(--color-primary);">✦</span> <span>Talents créatifs et innovants</span></li>
         </ul>
        </div>
        <div id="info-talent-2" class="p-6" style="background: var(--color-surface);">
         <h3 class="font-editorial text-xl mb-4" style="color: var(--color-primary);">Critères de sélection</h3>
         <ul class="space-y-3 text-sm" style="color: var(--color-secondary);">
          <li class="flex items-start gap-3"><span style="color: var(--color-primary);">01</span> <span>Excellence dans votre domaine</span></li>
          <li class="flex items-start gap-3"><span style="color: var(--color-primary);">02</span> <span>Parcours inspirant et atypique</span></li>
          <li class="flex items-start gap-3"><span style="color: var(--color-primary);">03</span> <span>Vision et ambition clairement définies</span></li>
          <li class="flex items-start gap-3"><span style="color: var(--color-primary);">04</span> <span>Capacité à inspirer les autres</span></li>
         </ul>
        </div>
        <div id="info-talent-3" class="p-4 text-center" style="border: 1px solid var(--color-primary);">
         <p class="text-sm" style="color: var(--color-primary);">⚡ Nombre de places limité : 12 talents par édition</p>
        </div><!-- Article info -->
        <div id="info-article" class="hidden p-6" style="background: var(--color-surface);">
         <h3 class="font-editorial text-xl mb-4" style="color: var(--color-primary);">À propos des contributions</h3>
         <ul class="space-y-3 text-sm" style="color: var(--color-secondary);">
          <li class="flex items-start gap-3"><span style="color: var(--color-primary);">✦</span> <span>Articles de 800 à 3000 mots</span></li>
          <li class="flex items-start gap-3"><span style="color: var(--color-primary);">✦</span> <span>Thèmes : innovation, talents, tendances, réflexions</span></li>
          <li class="flex items-start gap-3"><span style="color: var(--color-primary);">✦</span> <span>Accompagnement éditorial si nécessaire</span></li>
          <li class="flex items-start gap-3"><span style="color: var(--color-primary);">✦</span> <span>Mise en avant dans le magazine et sur nos réseaux</span></li>
         </ul>
        </div>
        <div id="info-article-2" class="hidden p-4 text-center" style="border: 1px solid var(--color-primary);">
         <p class="text-sm" style="color: var(--color-primary);">📝 Contribution volontaire, impact maximum</p>
        </div>
       </div><!-- Form Section -->
       <div class="space-y-8"><!-- Talent Form Button -->
        <div id="talent-section" class="text-center p-8" style="background: var(--color-surface);">
         <h3 class="font-editorial text-2xl mb-4" style="color: var(--color-text);">Figurer comme talent</h3>
         <p class="text-sm mb-6" style="color: var(--color-secondary);">Proposez-vous pour faire partie de nos talents d'exception.</p><a href="https://forms.zohopublic.eu/quenanaddraicl1/form/THEPLACEFigurercommetalent/formperma/v3LIKv-pyAcgo7ZlsrZWCvpjbAMx8Vw9aECSQVaPpRQ" target="_blank" rel="noopener noreferrer" class="inline-block px-8 py-4 text-sm tracking-widest uppercase transition-all hover:scale-105" style="background: var(--color-primary); color: var(--color-bg);">Accéder au formulaire</a>
        </div><!-- Article Form Button -->
        <div id="article-section" class="hidden text-center p-8" style="background: var(--color-surface);">
         <h3 class="font-editorial text-2xl mb-4" style="color: var(--color-text);">Proposer un article</h3>
         <p class="text-sm mb-6" style="color: var(--color-secondary);">Soumettez votre contribution au magazine THE PLACE.</p><a href="https://forms.zohopublic.eu/quenanaddraicl1/form/THEPLACEProposerunarticle/formperma/6l9LWMfOxq8kn70k-Czd6V8ki2lgxel7JCalXVHkWf4" target="_blank" rel="noopener noreferrer" class="inline-block px-8 py-4 text-sm tracking-widest uppercase transition-all hover:scale-105" style="background: var(--color-primary); color: var(--color-bg);">Accéder au formulaire</a>
        </div><!-- Toggle Buttons -->
        <div class="flex justify-center gap-4 pt-4"><button onclick="toggleForm('talent')" id="btn-talent-form" class="px-6 py-3 text-sm tracking-widest uppercase transition-all" style="background: var(--color-primary); color: var(--color-bg);">Figurer comme talent</button> <button onclick="toggleForm('article')" id="btn-article-form" class="px-6 py-3 text-sm tracking-widest uppercase transition-all" style="border: 1px solid var(--color-primary); color: var(--color-primary); background: transparent;">Proposer un article</button>
        </div>
       </div>
      </div>
     </div>
    </section>
   </div><!-- ==================== OPPORTUNITIES PAGE ==================== -->
   <div id="page-opportunities" class="page">
    <section class="pt-32 pb-24 px-6">
     <div class="max-w-7xl mx-auto">
      <div class="text-center mb-16"><span class="text-xs tracking-[0.3em] uppercase" style="color: var(--color-primary);">Carrières</span>
       <h1 class="font-editorial text-5xl sm:text-6xl mt-4" style="color: var(--color-text);">Opportunités</h1>
       <p class="mt-6 max-w-2xl mx-auto" style="color: var(--color-secondary);">Découvrez les talents sélectionnés actuellement en recherche de nouvelles opportunités professionnelles.</p>
      </div><!-- Opportunity Types -->
      <div class="flex flex-wrap justify-center gap-4 mb-12"><span class="px-4 py-2 text-xs tracking-wider uppercase" style="background: rgba(212,175,55,0.2); color: var(--color-primary);">Stage</span> <span class="px-4 py-2 text-xs tracking-wider uppercase" style="background: rgba(212,175,55,0.2); color: var(--color-primary);">CDD</span> <span class="px-4 py-2 text-xs tracking-wider uppercase" style="background: rgba(212,175,55,0.2); color: var(--color-primary);">CDI</span>
      </div><!-- Profiles Grid -->
      <div class="grid md:grid-cols-2 gap-6"><!-- Profile 1 -->
       <article class="p-6 flex gap-6" style="background: var(--color-surface);">
        <div class="w-20 h-20 flex-shrink-0 rounded-full flex items-center justify-center" style="background: var(--color-primary);">
         <span class="font-editorial text-2xl" style="color: var(--color-bg);">?</span>
        </div>
        <div class="flex-1">
         <div class="flex items-start justify-between gap-4">
          <div>
           <h3 class="font-editorial text-xl" style="color: var(--color-text);">Bientôt disponible</h3>
           <p class="text-sm mt-1" style="color: var(--color-secondary);">Les premières opportunités seront listées très bientôt</p>
          </div><span class="px-3 py-1 text-xs" style="background: var(--color-primary); color: var(--color-bg);">À VENIR</span>
         </div>
        </div>
       </article>
      </div><!-- CTA for Employers -->
      <div class="mt-16 p-12 text-center" style="background: var(--color-surface);"><span class="text-xs tracking-[0.3em] uppercase" style="color: var(--color-primary);">Recruteurs</span>
       <h3 class="font-editorial text-3xl mt-4 mb-4" style="color: var(--color-text);">Vous recrutez ?</h3>
       <p class="max-w-xl mx-auto mb-8" style="color: var(--color-secondary);">Accédez à notre vivier de talents d'exception et trouvez votre prochain collaborateur.</p><button onclick="navigateTo('contact')" class="px-8 py-4 text-sm tracking-widest uppercase transition-all hover:scale-105" style="background: var(--color-primary); color: var(--color-bg);"> Nous contacter </button>
      </div>
     </div>
    </section>
   </div><!-- ==================== CONTACT PAGE ==================== -->
   <div id="page-contact" class="page">
    <section class="pt-32 pb-24 px-6">
     <div class="max-w-4xl mx-auto">
      <div class="text-center mb-16"><span class="text-xs tracking-[0.3em] uppercase" style="color: var(--color-primary);">Contact</span>
       <h1 class="font-editorial text-5xl sm:text-6xl mt-4" style="color: var(--color-text);">Parlons ensemble</h1>
       <p class="mt-6 max-w-2xl mx-auto" style="color: var(--color-secondary);">Une question, une proposition de partenariat, ou une demande presse ? Nous sommes à votre écoute.</p>
      </div>
      <div class="grid lg:grid-cols-2 gap-12"><!-- Contact Info -->
       <div class="space-y-8">
        <div class="p-6" style="background: var(--color-surface);">
         <h3 class="font-editorial text-xl mb-4" style="color: var(--color-text);">Coordonnées</h3>
         <div class="space-y-4">
          <div class="flex items-center gap-4">
           <div class="w-10 h-10 flex items-center justify-center" style="border: 1px solid var(--color-primary);">
            <svg class="w-5 h-5" fill="none" stroke="currentColor" viewbox="0 0 24 24" style="color: var(--color-primary);"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M3 8l7.89 5.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z" />
            </svg>
           </div><span style="color: var(--color-secondary);">theplace.mag0@gmail.com</span>
          </div>
          <div class="flex items-center gap-4">
           <div class="w-10 h-10 flex items-center justify-center" style="border: 1px solid var(--color-primary);">
            <svg class="w-5 h-5" fill="none" stroke="currentColor" viewbox="0 0 24 24" style="color: var(--color-primary);"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M17.657 16.657L13.414 20.9a1.998 1.998 0 01-2.827 0l-4.244-4.243a8 8 0 1111.314 0z" /> <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M15 11a3 3 0 11-6 0 3 3 0 016 0z" />
            </svg>
           </div><span style="color: var(--color-secondary);">Paris, France</span>
          </div>
         </div>
        </div>
        <div class="p-6" style="background: var(--color-surface);">
         <h3 class="font-editorial text-xl mb-4" style="color: var(--color-text);">LinkedIn</h3>
         <div class="flex gap-4"><a href="https://www.linkedin.com/company/the-place-mag/" target="_blank" rel="noopener noreferrer" class="w-12 h-12 flex items-center justify-center transition-colors hover:bg-yellow-500" style="border: 1px solid var(--color-primary);">
           <svg class="w-5 h-5" fill="currentColor" viewbox="0 0 24 24" style="color: var(--color-primary);"><path d="M19 0h-14c-2.761 0-5 2.239-5 5v14c0 2.761 2.239 5 5 5h14c2.762 0 5-2.239 5-5v-14c0-2.761-2.238-5-5-5zm-11 19h-3v-11h3v11zm-1.5-12.268c-.966 0-1.75-.79-1.75-1.764s.784-1.764 1.75-1.764 1.75.79 1.75 1.764-.783 1.764-1.75 1.764zm13.5 12.268h-3v-5.604c0-3.368-4-3.113-4 0v5.604h-3v-11h3v1.765c1.396-2.586 7-2.777 7 2.476v6.759z" />
           </svg></a>
         </div>
        </div>
       </div><!-- Contact Form -->
       <div>
        <form id="contact-form" onsubmit="handleContactSubmit(event)" class="space-y-6">
         <div><label for="contact-type" class="block text-xs tracking-wider uppercase mb-2" style="color: var(--color-secondary);">Type de demande *</label> <select id="contact-type" required class="w-full px-4 py-3 text-sm transition-colors" style="background: var(--color-surface); border: 1px solid var(--color-secondary); color: var(--color-text);"> <option value="">Sélectionnez</option> <option value="talent">Je suis un talent</option> <option value="partenaire">Proposition de partenariat</option> <option value="presse">Demande presse</option> <option value="autre">Autre</option> </select>
         </div>
         <div class="grid sm:grid-cols-2 gap-4">
          <div><label for="contact-firstname" class="block text-xs tracking-wider uppercase mb-2" style="color: var(--color-secondary);">Prénom *</label> <input type="text" id="contact-firstname" required class="w-full px-4 py-3 text-sm transition-colors" style="background: var(--color-surface); border: 1px solid var(--color-secondary); color: var(--color-text);">
          </div>
          <div><label for="contact-lastname" class="block text-xs tracking-wider uppercase mb-2" style="color: var(--color-secondary);">Nom *</label> <input type="text" id="contact-lastname" required class="w-full px-4 py-3 text-sm transition-colors" style="background: var(--color-surface); border: 1px solid var(--color-secondary); color: var(--color-text);">
          </div>
         </div>
         <div><label for="contact-email" class="block text-xs tracking-wider uppercase mb-2" style="color: var(--color-secondary);">Email *</label> <input type="email" id="contact-email" required class="w-full px-4 py-3 text-sm transition-colors" style="background: var(--color-surface); border: 1px solid var(--color-secondary); color: var(--color-text);">
         </div>
         <div><label for="contact-company" class="block text-xs tracking-wider uppercase mb-2" style="color: var(--color-secondary);">Entreprise / Organisation</label> <input type="text" id="contact-company" class="w-full px-4 py-3 text-sm transition-colors" style="background: var(--color-surface); border: 1px solid var(--color-secondary); color: var(--color-text);">
         </div>
         <div><label for="contact-message" class="block text-xs tracking-wider uppercase mb-2" style="color: var(--color-secondary);">Message *</label> <textarea id="contact-message" required rows="5" class="w-full px-4 py-3 text-sm transition-colors resize-none" style="background: var(--color-surface); border: 1px solid var(--color-secondary); color: var(--color-text);"></textarea>
         </div><button type="submit" class="w-full py-4 text-sm tracking-widest uppercase transition-all hover:scale-[1.02]" style="background: var(--color-primary); color: var(--color-bg);"> Envoyer le message </button>
        </form>
        <div id="contact-success" class="hidden text-center p-8" style="background: var(--color-surface);">
         <div class="w-16 h-16 mx-auto mb-4 rounded-full flex items-center justify-center" style="background: var(--color-primary);">
          <svg class="w-8 h-8" fill="none" stroke="currentColor" viewbox="0 0 24 24" style="color: var(--color-bg);"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7" />
          </svg>
         </div>
         <h3 class="font-editorial text-2xl mb-2" style="color: var(--color-text);">Message envoyé !</h3>
         <p class="text-sm" style="color: var(--color-secondary);">Nous vous répondrons dans les plus brefs délais.</p>
        </div>
       </div>
      </div>
     </div>
    </section>
   </div><!-- ==================== LEGAL PAGE ==================== -->
   <div id="page-legal" class="page">
    <section class="pt-32 pb-24 px-6">
     <div class="max-w-4xl mx-auto"><span class="text-xs tracking-[0.3em] uppercase" style="color: var(--color-primary);">Légal</span>
      <h1 class="font-editorial text-5xl sm:text-6xl mt-4 mb-12" style="color: var(--color-text);">Mentions légales</h1>
      <div class="space-y-8 text-sm leading-relaxed" style="color: var(--color-secondary);">
       <div>
        <h3 class="font-editorial text-xl mb-4" style="color: var(--color-text);">Éditeur du site</h3>
        <p>THE PLACE<br>
          Paris, France<br>
          Email : theplace.mag0@gmail.com</p>
       </div>
       <div>
        <h3 class="font-editorial text-xl mb-4" style="color: var(--color-text);">Nature du site</h3>
        <p>THE PLACE est un média en ligne dédié à la mise en lumière des talents d'exception. Le site propose un magazine mensuel, une galerie de talents, un formulaire de candidature, une section opportunités professionnelles et un système de contact.</p>
       </div>
       <div>
        <h3 class="font-editorial text-xl mb-4" style="color: var(--color-text);">Hébergement</h3>
        <p>Ce site est hébergé et maintenu par Canva Code. L'infrastructure technique est gérée de manière à assurer la disponibilité du service.</p>
       </div>
       <div>
        <h3 class="font-editorial text-xl mb-4" style="color: var(--color-text);">Propriété intellectuelle</h3>
        <p>L'ensemble du contenu présent sur THE PLACE (textes, images, mises en page, graphismes, logos) est la propriété de THE PLACE ou de ses partenaires. Toute reproduction, adaptation ou représentation, totale ou partielle, sans l'accord préalable écrit de THE PLACE est strictement interdite.</p>
       </div>
       <div>
        <h3 class="font-editorial text-xl mb-4" style="color: var(--color-text);">Responsabilité</h3>
        <p>THE PLACE s'efforce de maintenir la précision et la qualité des informations publiées. Cependant, THE PLACE décline toute responsabilité en cas d'erreur, d'omission ou de contenu inadéquat. L'utilisation du site se fait à vos risques et périls.</p>
       </div>
       <div>
        <h3 class="font-editorial text-xl mb-4" style="color: var(--color-text);">Données personnelles</h3>
        <p>Les données collectées via les formulaires sont traitées conformément à notre <button onclick="navigateTo('privacy')" class="underline transition-colors hover:text-yellow-500" style="color: var(--color-primary);">politique de confidentialité</button>.</p>
       </div>
       <div>
        <h3 class="font-editorial text-xl mb-4" style="color: var(--color-text);">Évolution du site</h3>
        <p>THE PLACE se réserve le droit de modifier, ajouter ou supprimer des contenus ou fonctionnalités à tout moment, sans préavis.</p>
       </div>
      </div>
     </div>
    </section>
   </div><!-- ==================== PRIVACY PAGE ==================== -->
   <div id="page-privacy" class="page">
    <section class="pt-32 pb-24 px-6">
     <div class="max-w-4xl mx-auto"><span class="text-xs tracking-[0.3em] uppercase" style="color: var(--color-primary);">Confidentialité</span>
      <h1 class="font-editorial text-5xl sm:text-6xl mt-4 mb-12" style="color: var(--color-text);">Politique de confidentialité</h1>
      <div class="space-y-8 text-sm leading-relaxed" style="color: var(--color-secondary);">
       <div>
        <h3 class="font-editorial text-xl mb-4" style="color: var(--color-text);">Introduction</h3>
        <p>La présente politique de confidentialité a pour objectif d'informer les utilisateurs du site THE PLACE sur la manière dont leurs données personnelles sont collectées, utilisées et protégées.</p>
       </div>
       <div>
        <h3 class="font-editorial text-xl mb-4" style="color: var(--color-text);">Données collectées</h3>
        <p>Dans le cadre de son activité, THE PLACE peut être amené à collecter les données suivantes :</p>
        <ul class="list-disc list-inside space-y-2 mt-4">
         <li>Nom et prénom</li>
         <li>Adresse e-mail</li>
         <li>Profil professionnel (LinkedIn, CV, portfolio)</li>
         <li>Informations fournies volontairement via les formulaires (candidature, contact, inscription)</li>
        </ul>
       </div>
       <div>
        <h3 class="font-editorial text-xl mb-4" style="color: var(--color-text);">Utilisation des données</h3>
        <p>Les données collectées sont utilisées exclusivement pour :</p>
        <ul class="list-disc list-inside space-y-2 mt-4">
         <li>La gestion des candidatures et propositions de talents</li>
         <li>La communication éditoriale du média</li>
         <li>La publication et la sélection de profils dans le magazine</li>
         <li>L'envoi d'informations liées aux activités de THE PLACE (newsletter, annonces)</li>
        </ul>
       </div>
       <div>
        <h3 class="font-editorial text-xl mb-4" style="color: var(--color-text);">Partage des données</h3>
        <p>THE PLACE s'engage à ne pas vendre, louer ou céder les données personnelles à des tiers. Les données peuvent être consultées uniquement par l'éditeur du média et, le cas échéant, par des collaborateurs internes soumis à une obligation de confidentialité.</p>
       </div>
       <div>
        <h3 class="font-editorial text-xl mb-4" style="color: var(--color-text);">Durée de conservation</h3>
        <p>Les données personnelles sont conservées uniquement pendant la durée nécessaire aux finalités pour lesquelles elles ont été collectées, sauf obligation légale contraire.</p>
       </div>
       <div>
        <h3 class="font-editorial text-xl mb-4" style="color: var(--color-text);">Sécurité</h3>
        <p>THE PLACE met en œuvre des mesures raisonnables pour assurer la sécurité et la confidentialité des données personnelles et éviter tout accès non autorisé.</p>
       </div>
       <div>
        <h3 class="font-editorial text-xl mb-4" style="color: var(--color-text);">Droits des utilisateurs</h3>
        <p>Conformément à la réglementation applicable, chaque utilisateur dispose d'un droit d'accès, de rectification, de suppression ou d'opposition concernant ses données personnelles.</p>
        <p class="mt-4">Toute demande peut être adressée à : <span style="color: var(--color-text);">theplace.mag0@gmail.com</span></p>
       </div>
      </div>
     </div>
    </section>
   </div>
   <footer class="py-16 px-6" style="background: var(--color-surface); border-top: 1px solid rgba(255,255,255,0.05);">
    <div class="max-w-7xl mx-auto">
     <div class="grid md:grid-cols-4 gap-12 mb-12"><!-- Brand -->
      <div class="md:col-span-2">
       <div class="flex items-center gap-3 mb-6">
        <div class="w-10 h-10 border-2 flex items-center justify-center" style="border-color: var(--color-primary); background: var(--color-primary);"><span class="font-editorial text-xl font-bold" style="color: var(--color-bg);">P</span>
        </div><span class="font-editorial text-2xl tracking-wider" style="color: var(--color-text);">THE <span style="color: var(--color-primary);">P</span><span style="color: var(--color-text);">LACE</span></span>
       </div>
       <p class="text-sm max-w-sm" style="color: var(--color-secondary);">Le média des talents d'exception. Révéler l'excellence, inspirer l'ambition.</p>
      </div><!-- Navigation -->
      <div>
       <h4 class="text-xs tracking-widest uppercase mb-4" style="color: var(--color-text);">Navigation</h4>
       <ul class="space-y-3">
        <li><a href="#" onclick="navigateTo('about')" class="text-sm transition-colors hover:text-yellow-500" style="color: var(--color-secondary);">À propos</a></li>
        <li><a href="#" onclick="navigateTo('magazine')" class="text-sm transition-colors hover:text-yellow-500" style="color: var(--color-secondary);">Magazine</a></li>
        <li><a href="#" onclick="navigateTo('talents')" class="text-sm transition-colors hover:text-yellow-500" style="color: var(--color-secondary);">Talents</a></li>
        <li><a href="#" onclick="navigateTo('opportunities')" class="text-sm transition-colors hover:text-yellow-500" style="color: var(--color-secondary);">Opportunités</a></li>
       </ul>
      </div><!-- Contact -->
      <div>
       <h4 class="text-xs tracking-widest uppercase mb-4" style="color: var(--color-text);">Contact</h4>
       <ul class="space-y-3">
        <li><a href="#" onclick="navigateTo('apply')" class="text-sm transition-colors hover:text-yellow-500" style="color: var(--color-secondary);">Candidater</a></li>
        <li><a href="#" onclick="navigateTo('contact')" class="text-sm transition-colors hover:text-yellow-500" style="color: var(--color-secondary);">Nous contacter</a></li>
        <li><span class="text-sm" style="color: var(--color-secondary);">theplace.mag0@gmail.com</span></li>
       </ul>
      </div>
     </div><!-- Bottom -->
     <div class="pt-8 flex flex-col sm:flex-row justify-between items-center gap-4" style="border-top: 1px solid rgba(255,255,255,0.05);">
      <p class="copyright-year">© 2026 THE PLACE. Tous droits réservés.</p>
      <div class="flex gap-6"><a href="#" onclick="navigateTo('legal')" class="text-xs transition-colors hover:text-yellow-500" style="color: var(--color-secondary);">Mentions légales</a> <a href="#" onclick="navigateTo('privacy')" class="text-xs transition-colors hover:text-yellow-500" style="color: var(--color-secondary);">Politique de confidentialité</a>
      </div>
     </div>
    </div>
   </footer>
  </div>
  <script>
    // Default configuration
    const defaultConfig = {
      hero_tagline: 'Where talent gets seen.',
      manifesto_text: 'THE PLACE révèle les talents qui façonnent le monde de demain. Un média d\'excellence, sélectif et ambitieux, dédié à ceux qui osent se démarquer.',
      about_title: 'Notre Vision',
      talents_title: 'Nos Talents',
      background_color: '#0a0a0a',
      surface_color: '#141414',
      text_color: '#fafafa',
      primary_color: '#d4af37',
      secondary_color: '#737373',
      font_family: 'Cormorant Garamond',
      font_size: 16
    };

    let currentPage = 'home';

    // Initialize Element SDK
    if (window.elementSdk) {
      window.elementSdk.init({
        defaultConfig,
        onConfigChange: async (config) => {
          // Update CSS variables
          document.documentElement.style.setProperty('--color-bg', config.background_color || defaultConfig.background_color);
          document.documentElement.style.setProperty('--color-surface', config.surface_color || defaultConfig.surface_color);
          document.documentElement.style.setProperty('--color-text', config.text_color || defaultConfig.text_color);
          document.documentElement.style.setProperty('--color-primary', config.primary_color || defaultConfig.primary_color);
          document.documentElement.style.setProperty('--color-secondary', config.secondary_color || defaultConfig.secondary_color);
          
          // Update font
          const fontFamily = config.font_family || defaultConfig.font_family;
          document.querySelectorAll('.font-editorial').forEach(el => {
            el.style.fontFamily = `${fontFamily}, Georgia, serif`;
          });
          
          // Update font size
          const baseSize = config.font_size || defaultConfig.font_size;
          document.documentElement.style.fontSize = `${baseSize}px`;
          
          // Update text content
          const heroTagline = document.getElementById('hero-tagline');
          if (heroTagline) {
            heroTagline.innerHTML = `Where talent<br><span class="gold-shimmer">${(config.hero_tagline || defaultConfig.hero_tagline).split(' ').slice(-2).join(' ')}</span>`;
          }
          
          const heroManifesto = document.getElementById('hero-manifesto');
          if (heroManifesto) {
            heroManifesto.textContent = config.manifesto_text || defaultConfig.manifesto_text;
          }
          
          const aboutTitle = document.getElementById('about-title');
          if (aboutTitle) {
            aboutTitle.textContent = config.about_title || defaultConfig.about_title;
          }
          
          const talentsTitle = document.getElementById('talents-title');
          if (talentsTitle) {
            talentsTitle.textContent = config.talents_title || defaultConfig.talents_title;
          }
          
          const homeTalentsTitle = document.getElementById('home-talents-title');
          if (homeTalentsTitle) {
            homeTalentsTitle.textContent = config.talents_title || defaultConfig.talents_title;
          }
        },
        mapToCapabilities: (config) => ({
          recolorables: [
            {
              get: () => config.background_color || defaultConfig.background_color,
              set: (value) => { config.background_color = value; window.elementSdk.setConfig({ background_color: value }); }
            },
            {
              get: () => config.surface_color || defaultConfig.surface_color,
              set: (value) => { config.surface_color = value; window.elementSdk.setConfig({ surface_color: value }); }
            },
            {
              get: () => config.text_color || defaultConfig.text_color,
              set: (value) => { config.text_color = value; window.elementSdk.setConfig({ text_color: value }); }
            },
            {
              get: () => config.primary_color || defaultConfig.primary_color,
              set: (value) => { config.primary_color = value; window.elementSdk.setConfig({ primary_color: value }); }
            },
            {
              get: () => config.secondary_color || defaultConfig.secondary_color,
              set: (value) => { config.secondary_color = value; window.elementSdk.setConfig({ secondary_color: value }); }
            }
          ],
          borderables: [],
          fontEditable: {
            get: () => config.font_family || defaultConfig.font_family,
            set: (value) => { config.font_family = value; window.elementSdk.setConfig({ font_family: value }); }
          },
          fontSizeable: {
            get: () => config.font_size || defaultConfig.font_size,
            set: (value) => { config.font_size = value; window.elementSdk.setConfig({ font_size: value }); }
          }
        }),
        mapToEditPanelValues: (config) => new Map([
          ['hero_tagline', config.hero_tagline || defaultConfig.hero_tagline],
          ['manifesto_text', config.manifesto_text || defaultConfig.manifesto_text],
          ['about_title', config.about_title || defaultConfig.about_title],
          ['talents_title', config.talents_title || defaultConfig.talents_title]
        ])
      });
    }

    // Navigation
    function navigateTo(page) {
      // Hide all pages
      document.querySelectorAll('.page').forEach(p => p.classList.remove('active'));
      
      // Show target page
      const targetPage = document.getElementById(`page-${page}`);
      if (targetPage) {
        targetPage.classList.add('active');
        currentPage = page;
        
        // Scroll to top
        document.getElementById('app').scrollTo({ top: 0, behavior: 'smooth' });
        
        // Update navbar background on scroll
        updateNavbar();
      }
    }

    // Mobile menu toggle
    function toggleMobileMenu() {
      const menu = document.getElementById('mobile-menu');
      menu.classList.toggle('open');
    }

    // Navbar background on scroll
    function updateNavbar() {
      const app = document.getElementById('app');
      const navbar = document.getElementById('navbar');
      
      app.addEventListener('scroll', () => {
        if (app.scrollTop > 50) {
          navbar.style.background = 'rgba(10, 10, 10, 0.95)';
          navbar.style.backdropFilter = 'blur(10px)';
        } else {
          navbar.style.background = 'transparent';
          navbar.style.backdropFilter = 'none';
        }
      });
    }

    // Talent filter
    function filterTalents(category) {
      const items = document.querySelectorAll('.talent-item');
      const buttons = document.querySelectorAll('.talent-filter');
      
      // Update button styles
      buttons.forEach(btn => {
        btn.style.background = 'transparent';
        btn.style.border = '1px solid var(--color-secondary)';
        btn.style.color = 'var(--color-secondary)';
      });
      
      event.target.style.background = 'var(--color-primary)';
      event.target.style.border = 'none';
      event.target.style.color = 'var(--color-bg)';
      
      // Filter items
      items.forEach(item => {
        if (category === 'all' || item.dataset.category === category) {
          item.style.display = 'block';
        } else {
          item.style.display = 'none';
        }
      });
    }

    function handleContactSubmit(e) {
      e.preventDefault();
      document.getElementById('contact-form').classList.add('hidden');
      document.getElementById('contact-success').classList.remove('hidden');
    }

    function toggleForm(type) {
      if (type === 'talent') {
        document.getElementById('talent-section').classList.remove('hidden');
        document.getElementById('article-section').classList.add('hidden');
        document.getElementById('btn-talent-form').style.background = 'var(--color-primary)';
        document.getElementById('btn-talent-form').style.color = 'var(--color-bg)';
        document.getElementById('btn-talent-form').style.border = 'none';
        document.getElementById('btn-article-form').style.background = 'transparent';
        document.getElementById('btn-article-form').style.color = 'var(--color-primary)';
        document.getElementById('btn-article-form').style.border = '1px solid var(--color-primary)';
        
        document.getElementById('info-talent').classList.remove('hidden');
        document.getElementById('info-talent-2').classList.remove('hidden');
        document.getElementById('info-talent-3').classList.remove('hidden');
        document.getElementById('info-article').classList.add('hidden');
        document.getElementById('info-article-2').classList.add('hidden');
      } else {
        document.getElementById('talent-section').classList.add('hidden');
        document.getElementById('article-section').classList.remove('hidden');
        document.getElementById('btn-article-form').style.background = 'var(--color-primary)';
        document.getElementById('btn-article-form').style.color = 'var(--color-bg)';
        document.getElementById('btn-article-form').style.border = 'none';
        document.getElementById('btn-talent-form').style.background = 'transparent';
        document.getElementById('btn-talent-form').style.color = 'var(--color-primary)';
        document.getElementById('btn-talent-form').style.border = '1px solid var(--color-primary)';
        
        document.getElementById('info-talent').classList.add('hidden');
        document.getElementById('info-talent-2').classList.add('hidden');
        document.getElementById('info-talent-3').classList.add('hidden');
        document.getElementById('info-article').classList.remove('hidden');
        document.getElementById('info-article-2').classList.remove('hidden');
      }
    }

    // Initialize
    updateNavbar();
  </script>
 <script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'9d1ed79f443c229c',t:'MTc3MTc2NzA3MC4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script></body>
</html>