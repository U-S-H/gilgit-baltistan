<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Prime Solutions | Professional Web Hub</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        .glass-card { background: rgba(255, 255, 255, 0.03); backdrop-filter: blur(10px); border: 1px solid rgba(255, 255, 255, 0.1); transition: 0.3s; }
        .glass-card:hover { transform: translateY(-10px); border-color: #06b6d4; }
        .hero-gradient { background: radial-gradient(circle at center, #0e7490 0%, #000 70%); }
    </style>
</head>
<body class="bg-black text-white font-sans selection:bg-cyan-500">

    <!-- Navigation -->
    <nav class="flex justify-between items-center p-6 max-w-7xl mx-auto">
        <h1 class="text-2xl font-bold tracking-tighter text-cyan-400">PRIME<span class="text-white">SOLUTIONS</span></h1>
        <div class="hidden md:flex space-x-8 font-medium text-sm uppercase tracking-widest">
            <a href="#" class="hover:text-cyan-400">Home</a>
            <a href="#services" class="hover:text-cyan-400">Services</a>
            <a href="#contact" class="hover:text-cyan-400">Contact</a>
        </div>
    </nav>

    <!-- Hero Section -->
    <header class="hero-gradient min-h-[70vh] flex flex-col justify-center items-center text-center p-6">
        <h2 class="text-5xl md:text-7xl font-black mb-6 leading-tight">Elevate Your Digital<br><span class="text-cyan-500">Presence.</span></h2>
        <p class="text-gray-400 mb-8 max-w-lg">Custom web development, design, and digital solutions tailored for your business success.</p>
        <div class="flex gap-4">
            <a href="#contact" class="bg-white text-black px-8 py-3 rounded-full font-bold hover:bg-cyan-400 transition">Get Started</a>
        </div>
    </header>

    <!-- Services Section -->
    <section id="services" class="p-10 max-w-7xl mx-auto">
        <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
            <div class="glass-card p-10 rounded-2xl">
                <h3 class="text-2xl font-bold mb-4">Web Development</h3>
                <p class="text-gray-400">High-performance websites built with modern tech stacks.</p>
            </div>
            <div class="glass-card p-10 rounded-2xl">
                <h3 class="text-2xl font-bold mb-4">UI/UX Design</h3>
                <p class="text-gray-400">Stunning interfaces focused on user experience and conversion.</p>
            </div>
            <div class="glass-card p-10 rounded-2xl">
                <h3 class="text-2xl font-bold mb-4">Cloud Integration</h3>
                <p class="text-gray-400">Secure, scalable, and reliable cloud solutions with Firebase.</p>
            </div>
        </div>
    </section>

    <!-- Contact / Booking Section -->
    <section id="contact" class="p-10 max-w-4xl mx-auto text-center my-20">
        <h2 class="text-4xl font-bold mb-6">Let's Build Something Great</h2>
        <div class="glass-card p-8 rounded-3xl">
            <input type="text" id="name" placeholder="Full Name" class="w-full bg-transparent border-b border-gray-700 p-4 mb-4 focus:outline-none focus:border-cyan-500">
            <textarea id="msg" placeholder="Your Project Idea" class="w-full bg-transparent border-b border-gray-700 p-4 mb-6 focus:outline-none focus:border-cyan-500"></textarea>
            <button onclick="sendToWhatsApp()" class="w-full bg-cyan-600 py-4 rounded-full font-bold">Send Message</button>
        </div>
    </section>

    <script>
        function sendToWhatsApp() {
            const name = document.getElementById('name').value;
            const msg = document.getElementById('msg').value;
            window.open(`https://wa.me/923000000000?text=Hi, I am ${name}. ${msg}`);
        }
    </script>
</body>
</html>
