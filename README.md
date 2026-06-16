<html lang="en" class="scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Prime Solutions | GB Elite Portal</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://unpkg.com/lucide@latest"></script>
    <style>
        .glass { background: rgba(255, 255, 255, 0.05); backdrop-filter: blur(12px); border: 1px solid rgba(255, 255, 255, 0.1); }
        .hero-anim { animation: fadeIn 2s ease-in; }
        @keyframes fadeIn { from { opacity: 0; } to { opacity: 1; } }
    </style>
</head>
<body class="bg-black text-white font-sans">

    <nav class="flex justify-between items-center p-6 glass sticky top-0 z-50">
        <h1 class="text-2xl font-bold text-cyan-400 cursor-pointer" onclick="openAdmin()">PRIME SOLUTIONS</h1>
        <div class="flex gap-4 items-center">
            <button onclick="toggleUserDashboard()" class="text-xs bg-gray-800 px-4 py-2 rounded-full">Dashboard</button>
            <a href="#booking" class="bg-cyan-600 px-4 py-2 rounded-full text-sm font-bold">Book Now</a>
        </div>
    </nav>

    <section id="userDashboard" class="hidden p-6 glass m-4 rounded-xl">
        <h2 class="text-xl mb-4 text-cyan-400">My Trips</h2>
        <div id="userBookingStatus" class="text-sm">No active requests.</div>
    </section>

    <header class="h-[70vh] flex flex-col justify-center items-center text-center hero-anim bg-cover bg-center" style="background-image: linear-gradient(rgba(0,0,0,0.8), rgba(0,0,0,0.8)), url('https://images.unsplash.com/photo-1544735716-39212c46f63f?auto=format&fit=crop&w=1920&q=80');">
        <h1 class="text-5xl md:text-7xl font-black mb-4">Discover The North</h1>
        <p class="text-gray-400 text-lg">Premium guided tours for 20+ breathtaking destinations.</p>
    </header>

    <section id="destinations" class="p-10 max-w-7xl mx-auto">
        <h2 class="text-3xl font-bold mb-8 text-center">Featured Destinations</h2>
        <div id="cityGrid" class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-4 gap-6"></div>
    </section>

    <section id="booking" class="p-10 max-w-lg mx-auto glass rounded-3xl mb-20">
        <h2 class="text-2xl mb-6 font-bold">Secure Your Trip</h2>
        <input type="text" id="name" placeholder="Full Name" class="w-full p-4 mb-4 bg-black border border-gray-700 rounded-xl">
        <select id="city" class="w-full p-4 mb-4 bg-black border border-gray-700 rounded-xl"></select>
        <button onclick="addLead()" class="w-full bg-cyan-600 py-4 rounded-xl font-bold">Confirm Booking</button>
    </section>

    <section id="adminPanel" class="hidden p-6 glass m-4 rounded-xl border border-cyan-500">
        <h2 class="text-2xl mb-4 text-cyan-400">Admin Panel</h2>
        <div id="leadsList" class="space-y-2"></div>
    </section>

    <script>
        lucide.createIcons();
        const cities = ["Hunza", "Skardu", "Astore", "Ghizer", "Nagar", "Shigar", "Kharmang", "Ghanche", "Diamer", "Gilgit", "Yasin", "Ishkoman", "Phander", "Rama Lake", "Deosai", "Hushe", "Khaplu", "Gahkuch", "Chilas", "Darel"];
        
        // Populate Select and Grid
        const grid = document.getElementById('cityGrid');
        const citySelect = document.getElementById('city');
        cities.forEach(city => {
            citySelect.innerHTML += `<option value="${city}">${city}</option>`;
            grid.innerHTML += `
                <div class="glass rounded-xl p-4 hover:border-cyan-500 transition">
                    <img src="https://source.unsplash.com/400x300/?${city},mountain,tourism" class="rounded-lg mb-4 h-40 w-full object-cover">
                    <h3 class="font-bold text-cyan-400">${city}</h3>
                </div>`;
        });

        let leads = JSON.parse(localStorage.getItem('leads')) || [];

        function addLead() {
            const name = document.getElementById('name').value;
            const city = document.getElementById('city').value;
            leads.push({ id: Date.now(), name, city, status: 'Pending' });
            localStorage.setItem('leads', JSON.stringify(leads));
            alert("Booking request submitted, sweetie!");
            updateUserDashboard();
        }

        function toggleUserDashboard() { document.getElementById('userDashboard').classList.toggle('hidden'); }

        function updateUserDashboard() {
            document.getElementById('userBookingStatus').innerHTML = leads.map(l => `<p class="border-b p-2 border-gray-800">${l.city}: <span class="text-yellow-500">${l.status}</span></p>`).join('');
        }

        function openAdmin() {
            if(prompt("Enter Admin Key:") === "5426") {
                document.getElementById('adminPanel').classList.remove('hidden');
                renderAdminLeads();
            }
        }

        function renderAdminLeads() {
            document.getElementById('leadsList').innerHTML = leads.map(l => `
                <div class="flex justify-between p-2 border-b border-gray-800 text-sm">
                    <span>${l.name} - ${l.city} (${l.status})</span>
                    <div class="flex gap-2">
                        <button onclick="updateLead(${l.id}, 'Approved')" class="bg-green-800 px-2 rounded">✓</button>
                        <button onclick="deleteLead(${l.id})" class="bg-red-800 px-2 rounded">✕</button>
                    </div>
                </div>`).join('');
        }

        function updateLead(id, status) {
            leads = leads.map(l => l.id === id ? {...l, status} : l);
            localStorage.setItem('leads', JSON.stringify(leads));
            renderAdminLeads();
            updateUserDashboard();
        }

        function deleteLead(id) {
            leads = leads.filter(l => l.id !== id);
            localStorage.setItem('leads', JSON.stringify(leads));
            renderAdminLeads();
        }
    </script>
</body>
</html>
