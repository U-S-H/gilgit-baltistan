<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Discover Gilgit-Baltistan</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        /* Sliding Animation */
        .slide-in { animation: slideIn 1.5s ease-out forwards; }
        @keyframes slideIn {
            from { transform: translateX(-100%); opacity: 0; }
            to { transform: translateX(0); opacity: 1; }
        }
        .glass { background: rgba(0, 0, 0, 0.6); backdrop-filter: blur(10px); }
    </style>
</head>
<body class="bg-black text-white font-sans">

    <!-- Hero Section -->
    <header class="h-screen flex flex-col justify-center items-center text-center p-6 bg-cover bg-center" 
            style="background-image: url('https://images.unsplash.com/photo-1599940824399-b879d7312eb0?auto=format&fit=crop&w=1920&q=80');">
        <h1 class="text-4xl md:text-7xl font-black slide-in mb-6">Welcome to Discover Gilgit-Baltistan</h1>
        <p class="text-xl text-gray-200 slide-in delay-500">The Land of Mountains, Culture, and Adventure.</p>
        <a href="#destinations" class="mt-8 bg-cyan-600 px-8 py-3 rounded-full font-bold hover:bg-cyan-500 transition">Explore Now</a>
    </header>

    <!-- Destinations Grid -->
    <section id="destinations" class="p-10 max-w-7xl mx-auto">
        <h2 class="text-4xl font-bold mb-12 text-center text-cyan-400">Top Destinations</h2>
        <div id="cityGrid" class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-4 gap-8"></div>
    </section>

    <script>
        const cities = ["Hunza", "Skardu", "Astore", "Ghizer", "Nagar", "Shigar", "Kharmang", "Ghanche", "Diamer", "Gilgit", "Yasin", "Ishkoman", "Phander", "Rama Lake", "Deosai", "Hushe", "Khaplu", "Gahkuch", "Chilas", "Darel"];
        const grid = document.getElementById('cityGrid');
        
        cities.forEach(city => {
            grid.innerHTML += `
                <div class="group cursor-pointer">
                    <div class="overflow-hidden rounded-2xl">
                        <img src="https://source.unsplash.com/400x500/?${city},landscape,mountain" 
                             class="w-full h-80 object-cover transition duration-500 group-hover:scale-110" alt="${city}">
                    </div>
                    <h3 class="text-xl font-bold mt-4">${city}</h3>
                </div>
            `;
        });
    </script>
</body>
</html>
