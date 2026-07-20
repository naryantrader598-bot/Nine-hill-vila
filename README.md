<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="Nine Hill Villa - Luxury Resort & Fine Dining Experience in Sukher, Rajasthan">
    <title>Nine Hill Villa - Luxury Dining & Resort</title>
    <script src="https://unpkg.com/react@18/umd/react.production.min.js"></script>
    <script src="https://unpkg.com/react-dom@18/umd/react-dom.production.min.js"></script>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:wght@400;600;700&family=Poppins:wght@400;500;600;700&display=swap" rel="stylesheet">
    <style>
        * { margin: 0; padding: 0; box-sizing: border-box; }
        html { scroll-behavior: smooth; }
        body { font-family: 'Poppins', sans-serif; background: #F9F6EF; color: #333; }
        body.dark-mode { background: #0B0B0B; color: #F9F6EF; }
        h1, h2, h3, h4, h5, h6 { font-family: 'Cormorant Garamond', serif; font-weight: 700; }
        .gold-text { color: #D4AF37; }
        .btn-primary { background: linear-gradient(135deg, #0B3D2E 0%, #1a5c47 100%); color: #F9F6EF; padding: 12px 32px; border-radius: 8px; border: none; cursor: pointer; font-weight: 600; transition: all 0.3s ease; }
        .btn-primary:hover { transform: translateY(-2px); box-shadow: 0 10px 20px rgba(212, 175, 55, 0.3); }
        .btn-secondary { background: transparent; color: #D4AF37; border: 2px solid #D4AF37; padding: 10px 28px; border-radius: 8px; cursor: pointer; font-weight: 600; transition: all 0.3s ease; }
        .btn-secondary:hover { background: #D4AF37; color: #0B3D2E; }
        .glass-card { background: rgba(255, 255, 255, 0.1); backdrop-filter: blur(10px); border: 1px solid rgba(255, 255, 255, 0.2); border-radius: 12px; padding: 20px; transition: all 0.3s ease; }
        .glass-card:hover { transform: translateY(-5px); border-color: #D4AF37; box-shadow: 0 8px 32px rgba(212, 175, 55, 0.2); }
        body.dark-mode .glass-card { background: rgba(11, 61, 46, 0.2); border-color: rgba(212, 175, 55, 0.3); }
        .gradient-text { background: linear-gradient(135deg, #0B3D2E, #D4AF37); -webkit-background-clip: text; -webkit-text-fill-color: transparent; background-clip: text; }
        .sticky-header { position: sticky; top: 0; z-index: 100; box-shadow: 0 2px 20px rgba(0, 0, 0, 0.1); backdrop-filter: blur(10px); }
        .whatsapp-btn { position: fixed; bottom: 100px; right: 30px; z-index: 50; width: 60px; height: 60px; background: #25D366; border-radius: 50%; display: flex; align-items: center; justify-content: center; color: white; font-size: 28px; cursor: pointer; box-shadow: 0 4px 12px rgba(37, 211, 102, 0.4); transition: all 0.3s ease; text-decoration: none; }
        .whatsapp-btn:hover { transform: scale(1.1); bottom: 110px; }
        .call-btn { position: fixed; bottom: 30px; left: 30px; z-index: 50; width: 60px; height: 60px; background: #D4AF37; border-radius: 50%; display: flex; align-items: center; justify-content: center; color: #0B3D2E; font-size: 28px; cursor: pointer; box-shadow: 0 4px 12px rgba(212, 175, 55, 0.4); transition: all 0.3s ease; text-decoration: none; }
        .call-btn:hover { transform: scale(1.1); }
    </style>
</head>
<body class="light-mode">
    <div id="root"></div>
    <script>
        const defaultMenuItems = [
            { id: 1, name: 'Paneer Butter Masala', hindiName: 'पनीर बटर मसाला', price: 380, category: 'Main Course Veg', description: 'Soft paneer in creamy tomato butter sauce', isVeg: true, isPopular: true, isChefSpecial: true, image: 'https://cdn.pixabay.com/photo/2021/01/23/17/48/paneer-5939729_1280.jpg' },
            { id: 2, name: 'Dal Makhani', hindiName: 'दाल मखानी', price: 280, category: 'Main Course Veg', description: 'Slow-cooked black lentils in creamy butter sauce', isVeg: true, isPopular: true, isChefSpecial: false, image: 'https://cdn.pixabay.com/photo/2017/02/15/10/39/food-2068274_1280.jpg' },
            { id: 3, name: 'Tandoori Paneer', hindiName: 'तंदूरी पनीर', price: 320, category: 'Main Course Veg', description: 'Marinated paneer grilled in tandoor', isVeg: true, isPopular: false, isChefSpecial: true, image: 'https://cdn.pixabay.com/photo/2017/08/02/12/30/food-2572812_1280.jpg' },
            { id: 4, name: 'Jeera Rice', hindiName: 'जीरा राइस', price: 180, category: 'Rice', description: 'Aromatic basmati rice with cumin seeds', isVeg: true, isPopular: true, isChefSpecial: false, image: 'https://cdn.pixabay.com/photo/2019/09/25/13/04/rice-4504659_1280.jpg' },
            { id: 5, name: 'Biryani Mix Veg', hindiName: 'बिरयानी मिक्स वेज', price: 220, category: 'Rice', description: 'Layered rice with mixed vegetables and spices', isVeg: true, isPopular: true, isChefSpecial: true, image: 'https://cdn.pixabay.com/photo/2018/02/02/09/10/biryani-3127174_1280.jpg' },
            { id: 6, name: 'Garlic Naan', hindiName: 'लहसुन नान', price: 40, category: 'Roti', description: 'Soft naan bread with garlic butter', isVeg: true, isPopular: true, isChefSpecial: false, image: 'https://cdn.pixabay.com/photo/2018/06/09/23/56/naan-bread-3466989_1280.jpg' },
            { id: 7, name: 'Butter Naan', hindiName: 'बटर नान', price: 35, category: 'Roti', description: 'Soft naan with butter coating', isVeg: true, isPopular: false, isChefSpecial: false, image: 'https://cdn.pixabay.com/photo/2016/11/29/12/20/naan-1869192_1280.jpg' },
            { id: 8, name: 'Papad', hindiName: 'पापड़', price: 20, category: 'Salad & Papad', description: 'Crispy roasted lentil wafer', isVeg: true, isPopular: false, isChefSpecial: false, image: 'https://cdn.pixabay.com/photo/2017/05/03/10/49/poppadum-2281193_1280.jpg' },
            { id: 9, name: 'Raita', hindiName: 'रायता', price: 80, category: 'Salad & Papad', description: 'Yogurt with cucumber and spices', isVeg: true, isPopular: true, isChefSpecial: false, image: 'https://cdn.pixabay.com/photo/2021/04/27/16/01/food-6209842_1280.jpg' }
        ];
        let appState = { currentPage: 'home', cartItems: [], darkMode: false, menuItems: [], isAdminLoggedIn: false, selectedCategory: 'Main Course Veg', searchTerm: '', filterPopular: false, filterChefSpecial: false };
        function loadData() {
            const savedCart = localStorage.getItem('cart');
            if (savedCart) appState.cartItems = JSON.parse(savedCart);
            const savedMenuItems = localStorage.getItem('menuItems');
            if (savedMenuItems) appState.menuItems = JSON.parse(savedMenuItems);
            else { appState.menuItems = defaultMenuItems; localStorage.setItem('menuItems', JSON.stringify(defaultMenuItems)); }
        }
        function saveCart() { localStorage.setItem('cart', JSON.stringify(appState.cartItems)); }
        function addToCart(item) {
            const existingItem = appState.cartItems.find(i => i.id === item.id);
            if (existingItem) existingItem.quantity += item.quantity;
            else appState.cartItems.push(item);
            saveCart();
            alert('✅ Added to cart!');
            render();
        }
        function removeFromCart(id) { appState.cartItems = appState.cartItems.filter(item => item.id !== id); saveCart(); render(); }
        function updateQuantity(id, quantity) {
            const item = appState.cartItems.find(i => i.id === id);
            if (item) { if (quantity <= 0) removeFromCart(id); else { item.quantity = quantity; saveCart(); render(); } }
        }
        function generateWhatsAppOrder(name, phone, room, instructions) {
            if (!name || !phone) { alert('❌ Please enter name and phone!'); return; }
            let message = 'Hello Nine Hill Villa,\n\nI would like to order:\n\n';
            let subtotal = 0;
            appState.cartItems.forEach(item => {
                const total = item.price * item.quantity;
                subtotal += total;
                message += `${item.quantity} x ${item.name} - ₹${total}\n`;
            });
            const gstEnabled = document.getElementById('gstToggle')?.checked || false;
            const gst = gstEnabled ? subtotal * 0.18 : 0;
            const total = subtotal + gst;
            message += `\nSubtotal = ₹${subtotal}\n`;
            if (gstEnabled) message += `GST (18%) = ₹${gst.toFixed(2)}\n`;
            message += `Total = ₹${total.toFixed(2)}\n\n`;
            message += `Customer Name: ${name}\n`;
            message += `Phone: ${phone}\n`;
            if (room) message += `Room Number: ${room}\n`;
            if (instructions) message += `Special Instructions: ${instructions}\n`;
            const encodedMessage = encodeURIComponent(message);
            window.open(`https://wa.me/919571796219?text=${encodedMessage}`, '_blank');
        }
        function render() {
            const root = document.getElementById('root');
            const cartCount = appState.cartItems.reduce((sum, item) => sum + item.quantity, 0);
            let html = `<header class="sticky-header ${appState.darkMode ? 'bg-gray-900' : 'bg-white'} border-b ${appState.darkMode ? 'border-gray-800' : 'border-gray-200'}"><nav class="max-w-7xl mx-auto px-4 py-4 flex justify-between items-center flex-wrap gap-4"><div class="flex items-center gap-4 cursor-pointer" onclick="setCurrentPage('home')"><div class="text-3xl gold-text font-bold">🏰</div><div><h1 class="text-2xl font-bold gold-text">Nine Hill Villa</h1><p class="text-xs text-gray-600">Sukher, Rajasthan | Luxury • Dining • Experience</p></div></div><div class="flex gap-4 items-center flex-wrap"><button onclick="setCurrentPage('home')" class="font-semibold text-sm ${appState.currentPage === 'home' ? 'text-amber-500' : appState.darkMode ? 'text-white' : 'text-gray-800'}">Home</button><button onclick="setCurrentPage('menu')" class="font-semibold text-sm ${appState.currentPage === 'menu' ? 'text-amber-500' : appState.darkMode ? 'text-white' : 'text-gray-800'}">Menu</button><button onclick="setCurrentPage('admin')" class="font-semibold text-sm ${appState.currentPage === 'admin' ? 'text-amber-500' : appState.darkMode ? 'text-white' : 'text-gray-800'}">Admin</button><button onclick="toggleDarkMode()" class="px-3 py-1 rounded-lg text-sm ${appState.darkMode ? 'bg-amber-500 text-white' : 'bg-gray-200'}"> ${appState.darkMode ? '☀️' : '🌙'} </button>${appState.currentPage !== 'cart' ? `<button onclick="setCurrentPage('cart')" class="bg-gradient-to-r from-green-700 to-green-600 text-white px-4 py-2 rounded-lg font-bold text-sm">🛒 Cart ${cartCount > 0 ? '(' + cartCount + ')' : ''}</button>` : ''}</div></nav></header>`;
            if (appState.currentPage === 'home') html += renderHome();
            else if (appState.currentPage === 'menu') html += renderMenu();
            else if (appState.currentPage === 'cart') html += renderCart();
            else if (appState.currentPage === 'admin') html += renderAdmin();
            if (appState.currentPage !== 'admin') {
                html += `<a href="https://wa.me/919571796219" target="_blank" class="whatsapp-btn">💬</a><a href="tel:+919571796219" class="call-btn">☎️</a>`;
            }
            root.innerHTML = html;
        }
        function renderHome() {
            return `<section class="relative h-screen flex items-center justify-center overflow-hidden bg-gradient-to-br from-green-900 via-green-800 to-green-950"><div class="absolute inset-0 opacity-20"><div class="absolute top-20 left-10 w-72 h-72 bg-amber-400 rounded-full mix-blend-multiply filter blur-3xl"></div><div class="absolute bottom-20 right-10 w-72 h-72 bg-green-400 rounded-full mix-blend-multiply filter blur-3xl"></div></div><div class="relative text-center text-white z-10 px-4"><h1 class="text-5xl md:text-7xl font-bold mb-4">Nine Hill Villa</h1><p class="text-lg md:text-2xl mb-8 text-amber-300">🏞️ Sukher, Rajasthan</p><p class="text-base md:text-lg opacity-90 mb-8 max-w-2xl mx-auto">Experience fine dining in the heart of nature. A perfect blend of luxury accommodation and exquisite culinary delights with spectacular mountain & park views.</p><div class="flex justify-center gap-4 flex-wrap"><button onclick="setCurrentPage('menu')" class="btn-primary">➡️ View Menu</button></div><div class="grid grid-cols-3 gap-3 mt-12 max-w-2xl mx-auto"><div class="glass-card text-center"><p class="text-xl md:text-2xl gold-text font-bold">⭐ 4.89</p><p class="text-xs md:text-sm text-gray-300">55 Verified Reviews</p></div><div class="glass-card text-center"><p class="text-xl md:text-2xl font-bold">👥 8</p><p class="text-xs md:text-sm text-gray-300">Max Guests</p></div><div class="glass-card text-center"><p class="text-xl md:text-2xl font-bold">🛏️ 4</p><p class="text-xs md:text-sm text-gray-300">Beds</p></div></div></div></section><section class="py-16 md:py-20 px-4 ${appState.darkMode ? 'bg-gray-900' : 'bg-cream'} max-w-7xl mx-auto"><h2 class="text-4xl md:text-5xl font-bold text-center mb-12 md:mb-16 gradient-text">🏰 Nine Hill Villa - Sukher, Rajasthan</h2><div class="grid md:grid-cols-2 gap-8 md:gap-12 mb-12"><div class="glass-card"><h3 class="text-2xl md:text-3xl font-bold mb-4 gold-text">About The Villa</h3><p class="mb-4 text-sm md:text-base leading-relaxed">Nine Hill Villa is an elegant, soothing retreat nestled in the serene hills of Sukher, Rajasthan. Built with meticulous care and fine touches, it offers a posh living experience in the lap of nature with high oxygen levels.</p><div class="space-y-3 text-sm md:text-base"><p><strong>📍 Location:</strong> Sukher, Rajasthan, India</p><p><strong>👥 Capacity:</strong> 8 Guests | 2 Bedrooms | 4 Beds | 2 Private Bathrooms</p><p><strong>⭐ Rating:</strong> 4.89/5 (55 Verified Reviews)</p><p><strong>🏠 Host:</strong> Nine Hill Stay (5 Years Hosting)</p><p><strong>🕐 Check-in:</strong> After 1:00 PM | <strong>Check-out:</strong> Before 11:00 AM</p></div></div><div class="glass-card"><h3 class="text-2xl md:text-3xl font-bold mb-4 gold-text">🌟 Premium Amenities</h3><ul class="space-y-3 text-sm md:text-base"><li>✅ <strong>Swimming Pool & Hot Tub</strong> - Luxury relaxation</li><li>✅ <strong>WiFi (52 Mbps)</strong> - High-speed internet</li><li>✅ <strong>Music System with Karaoke</strong> - Entertainment</li><li>✅ <strong>Bonfire & Barbeque Area</strong> - Evening gatherings</li><li>✅ <strong>Garden with Herbs</strong> - Fresh ingredients</li><li>✅ <strong>Full Kitchen</strong> - Self-cooking option</li><li>✅ <strong>Netflix & Amazon Prime</strong> - Entertainment</li><li>✅ <strong>Games & Work Desk</strong> - Recreation & productivity</li><li>✅ <strong>Mountain & Park Views</strong> - Scenic beauty</li></ul></div></div><h3 class="text-3xl md:text-4xl font-bold mb-8 text-center">⭐ Guest Reviews (55 Verified)</h3><div class="grid md:grid-cols-3 gap-6"><div class="glass-card"><p class="text-amber-400 mb-2 text-sm md:text-base">⭐⭐⭐⭐⭐</p><p class="mb-4 text-sm italic">"Absolutely amazing experience! The pool and hospitality were exceptional. Loved the bonfire and mountain views!"</p><p class="font-bold text-xs md:text-sm">- Priya Sharma</p></div><div class="glass-card"><p class="text-amber-400 mb-2 text-sm md:text-base">⭐⭐⭐⭐⭐</p><p class="mb-4 text-sm italic">"Perfect place for a family getaway. Beautiful location with excellent WiFi, karaoke and wonderful hosts!"</p><p class="font-bold text-xs md:text-sm">- Rajesh Kumar</p></div><div class="glass-card"><p class="text-amber-400 mb-2 text-sm md:text-base">⭐⭐⭐⭐⭐</p><p class="mb-4 text-sm italic">"Loved every moment! The cleanliness, outdoor spaces and food quality are outstanding. Must visit!"</p><p class="font-bold text-xs md:text-sm">- Anaya Patel</p></div></div></section><section class="bg-gradient-to-r from-green-900 to-green-800 py-16 md:py-20 text-white"><div class="max-w-4xl mx-auto text-center px-4"><h2 class="text-3xl md:text-4xl font-bold mb-6">🍽️ Ready to Dine?</h2><p class="mb-8 text-lg opacity-90">Explore our premium Indian cuisine prepared with the finest ingredients</p><button onclick="setCurrentPage('menu')" class="btn-primary">Explore Menu Now</button></div></section>`;
        }
        function renderMenu() {
            const categories = ['Main Course Veg', 'Rice', 'Roti', 'Salad & Papad', 'Extra'];
            const filteredItems = appState.menuItems.filter(item => {
                let matches = item.category === appState.selectedCategory;
                if (appState.searchTerm) matches = matches && (item.name.toLowerCase().includes(appState.searchTerm.toLowerCase()) || item.hindiName.includes(appState.searchTerm));
                if (appState.filterPopular) matches = matches && item.isPopular;
                if (appState.filterChefSpecial) matches = matches && item.isChefSpecial;
                return matches;
            });
            return `<div class="py-8 md:py-12 px-4 ${appState.darkMode ? 'bg-gray-900' : 'bg-cream'}"><div class="max-w-7xl mx-auto"><h1 class="text-3xl md:text-5xl font-bold text-center mb-4 gradient-text">🍽️ Our Premium Menu</h1><p class="text-center text-gray-600 mb-8 md:mb-12 text-sm md:text-base">Fine Dining • Authentic Recipes • Vegetarian Specialties</p><div class="${appState.darkMode ? 'bg-gray-800' : 'bg-white'} p-3 md:p-4 rounded-lg mb-8 glass-card"><input type="text" placeholder="🔍 Search dishes..." value="${appState.searchTerm}" onchange="appState.searchTerm = this.value; render()" class="text-sm md:text-base ${appState.darkMode ? 'w-full p-2 border bg-gray-700 text-white rounded mb-3' : 'w-full p-2 border rounded mb-3'}" /><div class="flex gap-2 flex-wrap"><button onclick="appState.filterPopular = !appState.filterPopular; render()" class="px-3 py-1 text-xs md:text-sm rounded ${appState.filterPopular ? 'bg-amber-500 text-white' : 'bg-gray-200'}">⭐ Popular</button><button onclick="appState.filterChefSpecial = !appState.filterChefSpecial; render()" class="px-3 py-1 text-xs md:text-sm rounded ${appState.filterChefSpecial ? 'bg-amber-500 text-white' : 'bg-gray-200'}">👨‍🍳 Chef's Special</button></div></div><div class="flex gap-2 mb-8 overflow-x-auto pb-2">${categories.map(cat => `<button onclick="appState.selectedCategory = '${cat}'; render()" class="px-3 md:px-4 py-2 text-xs md:text-sm rounded whitespace-nowrap ${appState.selectedCategory === cat ? 'bg-gradient-to-r from-green-700 to-green-600 text-white' : appState.darkMode ? 'bg-gray-800 text-white' : 'bg-white border'}">${cat}</button>`).join('')}</div><div class="grid md:grid-cols-2 lg:grid-cols-3 gap-4 md:gap-6">${filteredItems.map(item => `<div class="glass-card overflow-hidden group"><div class="relative h-32 md:h-40 mb-3 overflow-hidden bg-gray-300"><img src="${item.image}" alt="${item.name}" class="w-full h-full object-cover group-hover:scale-110 transition" onerror="this.src='https://via.placeholder.com/400?text=Image+Not+Found'" /><div class="absolute top-2 right-2 flex gap-1 flex-wrap">${item.isPopular ? '<span class="bg-amber-500 text-white px-2 py-1 text-xs rounded">⭐ Popular</span>' : ''}${item.isChefSpecial ? '<span class="bg-red-500 text-white px-2 py-1 text-xs rounded">👨‍🍳 Choice</span>' : ''}</div></div><h3 class="font-bold text-sm md:text-base">${item.name}</h3><p class="text-xs text-amber-600 mb-2">${item.hindiName}</p><p class="text-xs md:text-sm text-gray-700 mb-3">${item.description}</p><div class="flex justify-between items-center mb-3"><p class="text-lg md:text-xl gold-text font-bold">₹${item.price}</p><div class="flex items-center gap-1 bg-gray-200 rounded px-2 py-1"><button onclick="decreaseQty(${item.id})" class="text-sm">−</button><span id="qty-${item.id}" class="px-2 font-bold text-sm">1</span><button onclick="increaseQty(${item.id})" class="text-sm">+</button></div></div><button onclick="addItemToCart(${item.id})" class="w-full btn-primary py-2 text-xs md:text-sm">🛒 Add to Cart</button></div>`).join('')}</div></div></div>`;
        }
        function renderCart() {
            if (appState.cartItems.length === 0) { return `<div class="min-h-screen flex items-center justify-# Nine-hill-vila