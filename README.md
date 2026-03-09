<!doctype html>
<html lang="pt-BR" class="h-full">

<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>ÉLITE - Moda de Luxo</title>
  <script src="https://cdn.tailwindcss.com/3.4.17"></script>
  <script src="/_sdk/element_sdk.js"></script>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link
    href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:wght@300;400;500;600;700&amp;family=Montserrat:wght@300;400;500;600&amp;display=swap"
    rel="stylesheet">
  <style>
    :root {
      --bg-color: #0a0a0a;
      --surface-color: #1a1a1a;
      --text-color: #f5f5f5;
      --accent-color: #c9a962;
      --accent-hover: #b8944d;
    }

    * {
      box-sizing: border-box;
    }

    html,
    body {
      height: 100%;
      margin: 0;
    }

    body {
      font-family: 'Montserrat', sans-serif;
      background: var(--bg-color);
      color: var(--text-color);
    }

    .font-display {
      font-family: 'Cormorant Garamond', serif;
    }

    .gold-gradient {
      background: linear-gradient(135deg, #c9a962 0%, #f0d78c 50%, #c9a962 100%);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      background-clip: text;
    }

    .card-hover {
      transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
    }

    .card-hover:hover {
      transform: translateY(-8px);
      box-shadow: 0 20px 40px rgba(201, 169, 98, 0.15);
    }

    .btn-gold {
      background: linear-gradient(135deg, #c9a962 0%, #dfc074 100%);
      color: #0a0a0a;
      transition: all 0.3s ease;
    }

    .btn-gold:hover {
      background: linear-gradient(135deg, #dfc074 0%, #c9a962 100%);
      transform: scale(1.02);
    }

    .cart-slide {
      transform: translateX(100%);
      transition: transform 0.4s cubic-bezier(0.4, 0, 0.2, 1);
    }

    .cart-slide.open {
      transform: translateX(0);
    }

    .overlay {
      opacity: 0;
      pointer-events: none;
      transition: opacity 0.3s ease;
    }

    .overlay.open {
      opacity: 1;
      pointer-events: auto;
    }

    .product-image {
      background: linear-gradient(145deg, #2a2a2a 0%, #1a1a1a 100%);
      position: relative;
      overflow: hidden;
    }

    .product-image::before {
      content: '';
      position: absolute;
      top: 0;
      left: -100%;
      width: 100%;
      height: 100%;
      background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.1), transparent);
      transition: left 0.6s ease;
    }

    .card-hover:hover .product-image::before {
      left: 100%;
    }

    .filter-btn {
      transition: all 0.3s ease;
      border: 1px solid #333;
    }

    .filter-btn:hover,
    .filter-btn.active {
      border-color: var(--accent-color);
      color: var(--accent-color);
    }

    .badge {
      animation: pulse 2s infinite;
    }

    @keyframes pulse {

      0%,
      100% {
        transform: scale(1);
      }

      50% {
        transform: scale(1.1);
      }
    }

    .fade-in {
      animation: fadeIn 0.5s ease forwards;
    }

    @keyframes fadeIn {
      from {
        opacity: 0;
        transform: translateY(20px);
      }

      to {
        opacity: 1;
        transform: translateY(0);
      }
    }

    input[type="range"] {
      -webkit-appearance: none;
      background: #333;
      height: 4px;
      border-radius: 2px;
    }

    input[type="range"]::-webkit-slider-thumb {
      -webkit-appearance: none;
      width: 16px;
      height: 16px;
      background: var(--accent-color);
      border-radius: 50%;
      cursor: pointer;
    }
  </style>
  <style>
    body {
      box-sizing: border-box;
    }
  </style>
  <script src="/_sdk/data_sdk.js" type="text/javascript"></script>
</head>

<body class="h-full overflow-auto">
  <div id="app" class="min-h-full w-full"><!-- Header -->
    <header class="fixed top-0 left-0 right-0 z-40 bg-[#0a0a0a]/95 backdrop-blur-md border-b border-[#222]">
      <div class="max-w-7xl mx-auto px-4 py-4 flex items-center justify-between">
        <h1 id="store-name" class="font-display text-2xl md:text-3xl font-light tracking-[0.3em] gold-gradient">ÉLITE
        </h1>
        <nav class="hidden md:flex items-center gap-8 text-sm tracking-widest"><button
            class="category-nav hover:text-[#c9a962] transition-colors pb-2 border-b-2 border-transparent hover:border-[#c9a962]"
            data-category="all">TODAS</button> <button
            class="category-nav hover:text-[#c9a962] transition-colors pb-2 border-b-2 border-transparent hover:border-[#c9a962]"
            data-category="Feminino">FEMININO</button> <button
            class="category-nav hover:text-[#c9a962] transition-colors pb-2 border-b-2 border-transparent hover:border-[#c9a962]"
            data-category="Masculino">MASCULINO</button> <button
            class="category-nav hover:text-[#c9a962] transition-colors pb-2 border-b-2 border-transparent hover:border-[#c9a962]"
            data-category="Acessórios">ACESSÓRIOS</button> <button
            class="category-nav hover:text-[#c9a962] transition-colors pb-2 border-b-2 border-transparent hover:border-[#c9a962]"
            data-category="Novidades">NOVIDADES</button>
        </nav><button id="cart-btn" class="relative p-2 hover:text-[#c9a962] transition-colors">
          <svg class="w-6 h-6" fill="none" stroke="currentColor" viewbox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5"
              d="M16 11V7a4 4 0 00-8 0v4M5 9h14l1 12H4L5 9z" />
          </svg><span id="cart-count"
            class="absolute -top-1 -right-1 w-5 h-5 bg-[#c9a962] text-[#0a0a0a] text-xs rounded-full flex items-center justify-center font-semibold badge hidden">0</span>
        </button>
      </div>
    </header><!-- Hero Section -->
    <section class="relative h-[60%] min-h-[400px] flex items-center justify-center overflow-hidden mt-16">
      <div class="absolute inset-0 bg-gradient-to-b from-[#1a1a1a] via-[#0a0a0a] to-[#0a0a0a]"></div>
      <div class="absolute inset-0 opacity-20"
        style="background-image: radial-gradient(circle at 2px 2px, #c9a962 1px, transparent 0); background-size: 40px 40px;">
      </div>
      <div class="relative text-center px-4 fade-in">
        <p class="text-[#c9a962] tracking-[0.5em] text-sm mb-4">COLEÇÃO 2024</p>
        <h2 id="hero-title" class="font-display text-4xl md:text-6xl lg:text-7xl font-light mb-4 leading-tight">G.L.A
          <span class="italic">Roupas</span>
        </h2>
        <p id="hero-subtitle" class="text-gray-400 text-lg md:text-xl font-light tracking-wide max-w-xl mx-auto">
          Descubra peças exclusivas das melhores marcas do mundo</p><button
          class="mt-8 btn-gold px-10 py-4 text-sm tracking-widest font-medium rounded-none">EXPLORAR COLEÇÃO</button>
      </div>
    </section><!-- Filter Section -->
    <section class="max-w-7xl mx-auto px-4 py-8">
      <div
        class="flex flex-col md:flex-row items-start md:items-center justify-between gap-6 border-b border-[#222] pb-8">
        <div>
          <h3 class="font-display text-2xl mb-2">Filtrar por Preço</h3>
          <p class="text-gray-500 text-sm">Selecione a faixa de preço desejada</p>
        </div>
        <div class="flex flex-wrap gap-3"><button
            class="filter-btn px-5 py-2 text-sm tracking-wider rounded-none active" data-filter="all">TODOS</button>
          <button class="filter-btn px-5 py-2 text-sm tracking-wider rounded-none" data-filter="under5000">ATÉ
            R$5.000</button> <button class="filter-btn px-5 py-2 text-sm tracking-wider rounded-none"
            data-filter="5000to10000">R$5.000 - R$10.000</button> <button
            class="filter-btn px-5 py-2 text-sm tracking-wider rounded-none" data-filter="10000to20000">R$10.000 -
            R$20.000</button> <button class="filter-btn px-5 py-2 text-sm tracking-wider rounded-none"
            data-filter="over20000">ACIMA DE R$20.000</button>
        </div>
      </div>
    </section><!-- Products Grid -->
    <section class="max-w-7xl mx-auto px-4 pb-16">
      <div id="products-grid" class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4 gap-6">
        <!-- Products will be inserted here -->
      </div>
      <p id="no-results" class="hidden text-center text-gray-500 py-16 text-lg">Nenhum produto encontrado nesta faixa de
        preço.</p>
    </section><!-- Cart Overlay -->
    <div id="cart-overlay" class="fixed inset-0 bg-black/70 z-50 overlay" onclick="closeCart()"></div>
    <!-- Cart Sidebar -->
    <aside id="cart-sidebar" class="fixed top-0 right-0 h-full w-full max-w-md bg-[#111] z-50 cart-slide flex flex-col">
      <div class="p-6 border-b border-[#222] flex items-center justify-between">
        <h3 class="font-display text-2xl">Seu Carrinho</h3><button onclick="closeCart()"
          class="p-2 hover:text-[#c9a962] transition-colors">
          <svg class="w-6 h-6" fill="none" stroke="currentColor" viewbox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M6 18L18 6M6 6l12 12" />
          </svg></button>
      </div>
      <div id="cart-items" class="flex-1 overflow-auto p-6 space-y-4"><!-- Cart items will be inserted here -->
      </div>
      <div id="cart-empty" class="flex-1 flex items-center justify-center text-gray-500">
        <div class="text-center">
          <svg class="w-16 h-16 mx-auto mb-4 opacity-30" fill="none" stroke="currentColor" viewbox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1"
              d="M16 11V7a4 4 0 00-8 0v4M5 9h14l1 12H4L5 9z" />
          </svg>
          <p>Seu carrinho está vazio</p>
        </div>
      </div>
      <div id="cart-footer" class="hidden border-t border-[#222] p-6">
        <div class="flex justify-between mb-4 text-lg"><span>Subtotal</span> <span id="cart-total"
            class="font-display text-[#c9a962]">R$ 0,00</span>
        </div><button onclick="checkout()" class="w-full btn-gold py-4 text-sm tracking-widest font-medium">FINALIZAR
          COMPRA</button> <button onclick="clearCart()"
          class="w-full mt-3 py-3 border border-[#333] text-sm tracking-widest hover:border-red-500 hover:text-red-500 transition-colors">LIMPAR
          CARRINHO</button>
      </div>
    </aside><!-- Toast Notification -->
    <div id="toast"
      class="fixed bottom-8 left-1/2 -translate-x-1/2 bg-[#1a1a1a] border border-[#c9a962] px-6 py-4 rounded-none z-50 flex items-center gap-3 opacity-0 pointer-events-none transition-all duration-300 transform translate-y-4">
      <svg class="w-5 h-5 text-[#c9a962]" fill="none" stroke="currentColor" viewbox="0 0 24 24">
        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7" />
      </svg><span id="toast-message">Produto adicionado ao carrinho!</span>
    </div>
  </div>
  <script>
    // Product Data
    const products = [
      // FEMININO
      { id: 1, name: "Blazer Alfaiataria Premium", brand: "MAISON NOIR", price: 4890, category: "Feminino", image: "https://images.unsplash.com/photo-1591195853828-11db59a44f6b?w=500&h=600&fit=crop", isNew: false },
      { id: 2, name: "Vestido Seda Italiano", brand: "VALENTINA", price: 7250, category: "Feminino", image: "https://images.unsplash.com/photo-1595777707802-32b53fa61b2d?w=500&h=600&fit=crop", isNew: false },
      { id: 5, name: "Casaco Cashmere", brand: "NORDIC ELITE", price: 18500, category: "Feminino", image: "https://images.unsplash.com/photo-1539533057440-7188bbc266e8?w=500&h=600&fit=crop", isNew: false },
      { id: 11, name: "Saia Midi Plissada", brand: "ATELIER ROSE", price: 3450, category: "Feminino", image: "https://images.unsplash.com/photo-1583273167999-ab4d1de21b5e?w=500&h=600&fit=crop", isNew: false },
      { id: 13, name: "Jumpsuit Preto Elegante", brand: "STELLA", price: 8900, category: "Feminino", image: "https://images.unsplash.com/photo-1564257631407-4deb1f14e714?w=500&h=600&fit=crop", isNew: false },
      { id: 14, name: "Calça Alfaiataria Cinza", brand: "LUXE", price: 5200, category: "Feminino", image: "https://images.unsplash.com/photo-1594938298603-c8148c4dae35?w=500&h=600&fit=crop", isNew: false },
      { id: 15, name: "Blusa Cetim Branca", brand: "SILK COUTURE", price: 2950, category: "Feminino", image: "https://images.unsplash.com/photo-1594938357195-19675b854625?w=500&h=600&fit=crop", isNew: true },
      { id: 16, name: "Vestido Festa Dourado", brand: "GALA", price: 12500, category: "Feminino", image: "https://images.unsplash.com/photo-1589066823604-27d7754908e1?w=500&h=600&fit=crop", isNew: true },

      // MASCULINO
      { id: 4, name: "Camisa Linho Egípcio", brand: "ARTISAN", price: 2890, category: "Masculino", image: "https://images.unsplash.com/photo-1596362051801-3d6ad0849dcf?w=500&h=600&fit=crop", isNew: false },
      { id: 6, name: "Sapato Oxford Artesanal", brand: "GENTLEMEN'S", price: 6750, category: "Masculino", image: "https://images.unsplash.com/photo-1542291026-7eec264c27ff?w=500&h=600&fit=crop", isNew: false },
      { id: 8, name: "Terno Sob Medida", brand: "SAVILE ROW", price: 15800, category: "Masculino", image: "https://images.unsplash.com/photo-1552062407-291817635baa?w=500&h=600&fit=crop", isNew: false },
      { id: 10, name: "Jaqueta Couro Premium", brand: "REBELLION", price: 9900, category: "Masculino", image: "https://images.unsplash.com/photo-1551028719-00167b16ebc5?w=500&h=600&fit=crop", isNew: false },
      { id: 17, name: "Camisa Social Azul Royal", brand: "FORMAL WEAR", price: 3200, category: "Masculino", image: "https://images.unsplash.com/photo-1596398215868-7526d49cdc89?w=500&h=600&fit=crop", isNew: false },
      { id: 18, name: "Calça Jeans Premium", brand: "DENIM ELITE", price: 1850, category: "Masculino", image: "https://images.unsplash.com/photo-1542272604-787c62d465d1?w=500&h=600&fit=crop", isNew: false },
      { id: 19, name: "Blazer Marrom Claro", brand: "CLASSIC", price: 6800, category: "Masculino", image: "https://images.unsplash.com/photo-1550258987-920a2eae3c3d?w=500&h=600&fit=crop", isNew: true },
      { id: 20, name: "Sapato Loafer Couro", brand: "DERBY", price: 5600, category: "Masculino", image: "https://images.unsplash.com/photo-1543163521-9efad2b3b718?w=500&h=600&fit=crop", isNew: true },

      // ACESSÓRIOS
      { id: 3, name: "Bolsa Couro Estruturada", brand: "LUXE PARIS", price: 12900, category: "Acessórios", image: "https://images.unsplash.com/photo-1548036328-c9fa89d128fa?w=500&h=600&fit=crop", isNew: false },
      { id: 7, name: "Relógio Automático", brand: "CHRONOS", price: 24900, category: "Acessórios", image: "https://images.unsplash.com/photo-1523275335684-37898b6baf30?w=500&h=600&fit=crop", isNew: false },
      { id: 9, name: "Lenço Seda Estampado", brand: "HERMÈS STYLE", price: 1890, category: "Acessórios", image: "https://images.unsplash.com/photo-1616564589676-4b5f87a5a8a0?w=500&h=600&fit=crop", isNew: false },
      { id: 12, name: "Óculos Sol Titanium", brand: "OPTICA LUX", price: 4200, category: "Acessórios", image: "https://images.unsplash.com/photo-1572635196237-14b3f281503f?w=500&h=600&fit=crop", isNew: false },
      { id: 21, name: "Cinturão Couro Italiana", brand: "BELT LUXE", price: 2150, category: "Acessórios", image: "https://images.unsplash.com/photo-1553062407-98eeb64c6a62?w=500&h=600&fit=crop", isNew: false },
      { id: 22, name: "Bolsa Crossbody Preta", brand: "ELEGANCE", price: 8900, category: "Acessórios", image: "https://images.unsplash.com/photo-1548036328-c9fa89d128fa?w=500&h=600&fit=crop", isNew: false },
      { id: 23, name: "Luvas Pele Cashmere", brand: "GLOVE ELITE", price: 1450, category: "Acessórios", image: "https://images.unsplash.com/photo-1520087589308-9d64b5ce6e1c?w=500&h=600&fit=crop", isNew: true },
      { id: 24, name: "Carteira Couro Premium", brand: "WALLET NOIR", price: 1680, category: "Acessórios", image: "https://images.unsplash.com/photo-1548036328-c9fa89d128fa?w=500&h=600&fit=crop", isNew: true },

      // NOVIDADES
      { id: 25, name: "Tênis Premium Branco", brand: "SPORT LUXE", price: 3890, category: "Novidades", image: "https://images.unsplash.com/photo-1542291026-7eec264c27ff?w=500&h=600&fit=crop", isNew: true },
      { id: 26, name: "Bolsa Transversal Bege", brand: "CHIC BAG", price: 7500, category: "Novidades", image: "https://images.unsplash.com/photo-1548036328-c9fa89d128fa?w=500&h=600&fit=crop", isNew: true },
      { id: 27, name: "Óculos Redondo Vintage", brand: "RETRO OPTICS", price: 3200, category: "Novidades", image: "https://images.unsplash.com/photo-1572635196237-14b3f281503f?w=500&h=600&fit=crop", isNew: true },
      { id: 28, name: "Jaqueta Jeans Azul", brand: "DENIM ART", price: 4500, category: "Novidades", image: "https://images.unsplash.com/photo-1551028719-00167b16ebc5?w=500&h=600&fit=crop", isNew: true },
    ];

    let cart = [];
    let currentFilter = 'all';
    let currentCategory = 'all';

    const defaultConfig = {
      store_name: "ÉLITE",
      hero_title: "G.L.V Roupas",
      hero_subtitle: "Descubra peças exclusivas das melhores marcas do mundo",
      background_color: "#0a0a0a",
      surface_color: "#1a1a1a",
      text_color: "#f5f5f5",
      primary_action: "#c9a962",
      secondary_action: "#b8944d",
      font_family: "Montserrat",
      font_size: 16
    };

    // Initialize Element SDK
    if (window.elementSdk) {
      window.elementSdk.init({
        defaultConfig,
        onConfigChange: async (config) => {
          const storeName = document.getElementById('store-name');
          const heroTitle = document.getElementById('hero-title');
          const heroSubtitle = document.getElementById('hero-subtitle');

          if (storeName) storeName.textContent = config.store_name || defaultConfig.store_name;
          if (heroTitle) heroTitle.innerHTML = (config.hero_title || defaultConfig.hero_title).replace('Atemporal', '<span class="italic">Atemporal</span>');
          if (heroSubtitle) heroSubtitle.textContent = config.hero_subtitle || defaultConfig.hero_subtitle;

          // Apply colors
          document.documentElement.style.setProperty('--bg-color', config.background_color || defaultConfig.background_color);
          document.documentElement.style.setProperty('--surface-color', config.surface_color || defaultConfig.surface_color);
          document.documentElement.style.setProperty('--text-color', config.text_color || defaultConfig.text_color);
          document.documentElement.style.setProperty('--accent-color', config.primary_action || defaultConfig.primary_action);
          document.documentElement.style.setProperty('--accent-hover', config.secondary_action || defaultConfig.secondary_action);

          // Apply font
          const fontFamily = config.font_family || defaultConfig.font_family;
          document.body.style.fontFamily = `${fontFamily}, sans-serif`;

          // Apply font size scaling
          const baseSize = config.font_size || defaultConfig.font_size;
          document.body.style.fontSize = `${baseSize}px`;
        },
        mapToCapabilities: (config) => ({
          recolorables: [
            { get: () => config.background_color || defaultConfig.background_color, set: (v) => window.elementSdk.setConfig({ background_color: v }) },
            { get: () => config.surface_color || defaultConfig.surface_color, set: (v) => window.elementSdk.setConfig({ surface_color: v }) },
            { get: () => config.text_color || defaultConfig.text_color, set: (v) => window.elementSdk.setConfig({ text_color: v }) },
            { get: () => config.primary_action || defaultConfig.primary_action, set: (v) => window.elementSdk.setConfig({ primary_action: v }) },
            { get: () => config.secondary_action || defaultConfig.secondary_action, set: (v) => window.elementSdk.setConfig({ secondary_action: v }) }
          ],
          borderables: [],
          fontEditable: { get: () => config.font_family || defaultConfig.font_family, set: (v) => window.elementSdk.setConfig({ font_family: v }) },
          fontSizeable: { get: () => config.font_size || defaultConfig.font_size, set: (v) => window.elementSdk.setConfig({ font_size: v }) }
        }),
        mapToEditPanelValues: (config) => new Map([
          ["store_name", config.store_name || defaultConfig.store_name],
          ["hero_title", config.hero_title || defaultConfig.hero_title],
          ["hero_subtitle", config.hero_subtitle || defaultConfig.hero_subtitle]
        ])
      });
    }

    // Format price
    function formatPrice(price) {
      return price.toLocaleString('pt-BR', { style: 'currency', currency: 'BRL' });
    }

    // Get price filter
    function getPriceFilter(price) {
      if (price < 5000) return 'under5000';
      if (price >= 5000 && price < 10000) return '5000to10000';
      if (price >= 10000 && price < 20000) return '10000to20000';
      return 'over20000';
    }

    // Render products
    function renderProducts() {
      const grid = document.getElementById('products-grid');
      const noResults = document.getElementById('no-results');

      const filteredProducts = products.filter(product => {
        const categoryMatch = currentCategory === 'all' || product.category === currentCategory;
        const priceMatch = currentFilter === 'all' || getPriceFilter(product.price) === currentFilter;
        return categoryMatch && priceMatch;
      });

      if (filteredProducts.length === 0) {
        grid.innerHTML = '';
        noResults.classList.remove('hidden');
        return;
      }

      noResults.classList.add('hidden');
      grid.innerHTML = filteredProducts.map((product, index) => `
        <div class="card-hover fade-in" style="animation-delay: ${index * 0.05}s">
          <div class="product-image aspect-[3/4] overflow-hidden relative bg-[#2a2a2a]">
            <img src="${product.image}" alt="${product.name}" loading="lazy" class="w-full h-full object-cover" onerror="console.error('Image failed to load:', this.src); this.style.background='#1a1a1a'; this.alt='Imagem indisponível';">
            <span class="absolute top-3 left-3 bg-[#c9a962] text-[#0a0a0a] text-xs px-3 py-1 tracking-wider font-medium">${product.brand}</span>
            ${product.isNew ? '<span class="absolute top-3 right-3 bg-red-600 text-white text-xs px-3 py-1 tracking-wider font-medium">NOVO</span>' : ''}
          </div>
          <div class="p-4 bg-[#1a1a1a]">
            <p class="text-xs text-gray-500 tracking-wider mb-1">${product.category.toUpperCase()}</p>
            <h4 class="font-display text-lg mb-2">${product.name}</h4>
            <div class="flex items-center justify-between">
              <span class="text-[#c9a962] font-medium">${formatPrice(product.price)}</span>
              <button onclick="addToCart(${product.id})" class="p-2 border border-[#333] hover:border-[#c9a962] hover:text-[#c9a962] transition-all">
                <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M12 6v6m0 0v6m0-6h6m-6 0H6"/>
                </svg>
              </button>
            </div>
          </div>
        </div>
      `).join('');
    }

    // Get product icon based on category
    function getProductIcon(category) {
      switch (category) {
        case 'Feminino':
          return '<path d="M12 2a4 4 0 014 4v1h3a1 1 0 011 1v12a2 2 0 01-2 2H6a2 2 0 01-2-2V8a1 1 0 011-1h3V6a4 4 0 014-4z"/>';
        case 'Masculino':
          return '<path d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm-1 17.93c-3.95-.49-7-3.85-7-7.93 0-.62.08-1.21.21-1.79L9 15v1c0 1.1.9 2 2 2v1.93z"/>';
        default:
          return '<path d="M20 7l-8-4-8 4m16 0l-8 4m8-4v10l-8 4m0-10L4 7m8 4v10M4 7v10l8 4"/>';
      }
    }

    // Adjust color brightness
    function adjustColor(color, amount) {
      const num = parseInt(color.replace('#', ''), 16);
      const r = Math.min(255, Math.max(0, (num >> 16) + amount));
      const g = Math.min(255, Math.max(0, ((num >> 8) & 0x00FF) + amount));
      const b = Math.min(255, Math.max(0, (num & 0x0000FF) + amount));
      return '#' + (0x1000000 + r * 0x10000 + g * 0x100 + b).toString(16).slice(1);
    }

    // Add to cart
    function addToCart(productId) {
      const product = products.find(p => p.id === productId);
      if (!product) return;

      const existingItem = cart.find(item => item.id === productId);
      if (existingItem) {
        existingItem.quantity++;
      } else {
        cart.push({ ...product, quantity: 1 });
      }

      updateCart();
      showToast(`${product.name} adicionado ao carrinho!`);
    }

    // Remove from cart
    function removeFromCart(productId) {
      cart = cart.filter(item => item.id !== productId);
      updateCart();
    }

    // Update quantity
    function updateQuantity(productId, change) {
      const item = cart.find(i => i.id === productId);
      if (item) {
        item.quantity += change;
        if (item.quantity <= 0) {
          removeFromCart(productId);
        } else {
          updateCart();
        }
      }
    }

    // Update cart UI
    function updateCart() {
      const cartItems = document.getElementById('cart-items');
      const cartEmpty = document.getElementById('cart-empty');
      const cartFooter = document.getElementById('cart-footer');
      const cartCount = document.getElementById('cart-count');
      const cartTotal = document.getElementById('cart-total');

      const totalItems = cart.reduce((sum, item) => sum + item.quantity, 0);
      const totalPrice = cart.reduce((sum, item) => sum + (item.price * item.quantity), 0);

      // Update badge
      if (totalItems > 0) {
        cartCount.textContent = totalItems;
        cartCount.classList.remove('hidden');
      } else {
        cartCount.classList.add('hidden');
      }

      // Update cart content
      if (cart.length === 0) {
        cartItems.classList.add('hidden');
        cartEmpty.classList.remove('hidden');
        cartFooter.classList.add('hidden');
      } else {
        cartItems.classList.remove('hidden');
        cartEmpty.classList.add('hidden');
        cartFooter.classList.remove('hidden');

        cartItems.innerHTML = cart.map(item => `
          <div class="flex gap-4 bg-[#1a1a1a] p-4">
            <div class="w-20 h-24 flex-shrink-0 overflow-hidden bg-[#2a2a2a]">
              <img src="${item.image}" alt="${item.name}" loading="lazy" class="w-full h-full object-cover" onerror="console.error('Image failed to load:', this.src); this.style.background='#1a1a1a';">
            </div>
            <div class="flex-1">
              <p class="text-xs text-[#c9a962] tracking-wider mb-1">${item.brand}</p>
              <h4 class="font-display text-sm mb-2">${item.name}</h4>
              <p class="text-[#c9a962] font-medium text-sm">${formatPrice(item.price)}</p>
              <div class="flex items-center gap-3 mt-2">
                <button onclick="updateQuantity(${item.id}, -1)" class="w-7 h-7 border border-[#333] flex items-center justify-center hover:border-[#c9a962] transition-colors">
                  <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M20 12H4"/>
                  </svg>
                </button>
                <span class="text-sm w-6 text-center">${item.quantity}</span>
                <button onclick="updateQuantity(${item.id}, 1)" class="w-7 h-7 border border-[#333] flex items-center justify-center hover:border-[#c9a962] transition-colors">
                  <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 6v6m0 0v6m0-6h6m-6 0H6"/>
                  </svg>
                </button>
                <button onclick="removeFromCart(${item.id})" class="ml-auto text-gray-500 hover:text-red-500 transition-colors">
                  <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M19 7l-.867 12.142A2 2 0 0116.138 21H7.862a2 2 0 01-1.995-1.858L5 7m5 4v6m4-6v6m1-10V4a1 1 0 00-1-1h-4a1 1 0 00-1 1v3M4 7h16"/>
                  </svg>
                </button>
              </div>
            </div>
          </div>
        `).join('');

        cartTotal.textContent = formatPrice(totalPrice);
      }
    }

    // Open cart
    function openCart() {
      document.getElementById('cart-sidebar').classList.add('open');
      document.getElementById('cart-overlay').classList.add('open');
    }

    // Close cart
    function closeCart() {
      document.getElementById('cart-sidebar').classList.remove('open');
      document.getElementById('cart-overlay').classList.remove('open');
    }

    // Clear cart
    function clearCart() {
      cart = [];
      updateCart();
      showToast('Carrinho limpo com sucesso!');
    }

    // Checkout
    function checkout() {
      const total = cart.reduce((sum, item) => sum + (item.price * item.quantity), 0);
      showToast(`Compra de ${formatPrice(total)} realizada com sucesso!`);
      cart = [];
      updateCart();
      closeCart();
    }

    // Show toast notification
    function showToast(message) {
      const toast = document.getElementById('toast');
      const toastMessage = document.getElementById('toast-message');
      toastMessage.textContent = message;
      toast.classList.remove('opacity-0', 'pointer-events-none', 'translate-y-4');
      toast.classList.add('opacity-100', 'translate-y-0');

      setTimeout(() => {
        toast.classList.add('opacity-0', 'pointer-events-none', 'translate-y-4');
        toast.classList.remove('opacity-100', 'translate-y-0');
      }, 3000);
    }

    // Filter button click handlers
    document.querySelectorAll('.filter-btn').forEach(btn => {
      btn.addEventListener('click', () => {
        document.querySelectorAll('.filter-btn').forEach(b => b.classList.remove('active'));
        btn.classList.add('active');
        currentFilter = btn.dataset.filter;
        renderProducts();
      });
    });

    // Category button click handlers
    document.querySelectorAll('.category-nav').forEach(btn => {
      btn.addEventListener('click', () => {
        document.querySelectorAll('.category-nav').forEach(b => b.classList.remove('border-[#c9a962]'));
        btn.classList.add('border-[#c9a962]');
        currentCategory = btn.dataset.category;
        currentFilter = 'all';
        document.querySelectorAll('.filter-btn').forEach(b => b.classList.remove('active'));
        document.querySelector('[data-filter="all"]').classList.add('active');
        renderProducts();
      });
    });

    // Set initial active category
    document.querySelector('[data-category="all"]').classList.add('border-[#c9a962]');

    // Cart button click handler
    document.getElementById('cart-btn').addEventListener('click', openCart);

    // Initialize
    renderProducts();
    updateCart();
  </script>
  <script>(function () { function c() { var b = a.contentDocument || a.contentWindow.document; if (b) { var d = b.createElement('script'); d.innerHTML = "window.__CF$cv$params={r:'9d6988da015d5448',t:'MTc3MjU1MDI3Ni4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);"; b.getElementsByTagName('head')[0].appendChild(d) } } if (document.body) { var a = document.createElement('iframe'); a.height = 1; a.width = 1; a.style.position = 'absolute'; a.style.top = 0; a.style.left = 0; a.style.border = 'none'; a.style.visibility = 'hidden'; document.body.appendChild(a); if ('loading' !== document.readyState) c(); else if (window.addEventListener) document.addEventListener('DOMContentLoaded', c); else { var e = document.onreadystatechange || function () { }; document.onreadystatechange = function (b) { e(b); 'loading' !== document.readyState && (document.onreadystatechange = e, c()) } } } })();</script>
</body>

</html>
