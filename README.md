<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Discover Gilgit-Baltistan | Enterprise Hub</title>
    <script src="https://cdn.jsdelivr.net/npm/@tailwindcss/browser@4"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">
    <style>
        .custom-scrollbar::-webkit-scrollbar { width: 5px; }
        .custom-scrollbar::-webkit-scrollbar-track { background: rgba(15, 23, 42, 0.1); }
        .custom-scrollbar::-webkit-scrollbar-thumb { background: #059669; border-radius: 4px; }
    </style>
</head>
<body class="bg-slate-50 text-slate-800 font-sans tracking-wide scroll-smooth">

    <nav class="bg-white/90 backdrop-blur-md shadow-sm sticky top-0 z-40 border-b border-emerald-100">
        <div class="max-w-7xl mx-auto px-6 py-4 flex justify-between items-center">
            <button id="logoTrigger" class="text-2xl font-black text-emerald-700 tracking-wider flex items-center gap-2 cursor-pointer focus:outline-none select-none">
                <i class="fas fa-mountain"></i> DISCOVER <span class="text-slate-900 font-light">GB</span>
            </button>
            <div class="hidden lg:flex space-x-6 font-semibold text-xs uppercase tracking-wider text-slate-600">
                <a href="#home" class="hover:text-emerald-600 transition">Home</a>
                <a href="#destinations" class="hover:text-emerald-600 transition">Destinations</a>
                <a href="#quote-system" class="hover:text-emerald-600 transition">Planner</a>
                <a href="#faq-section" class="hover:text-emerald-600 transition">FAQs</a>
                <a href="#company-details" class="hover:text-emerald-600 transition">About</a>
            </div>
            <div class="flex items-center gap-4">
                <button id="userAuthBtn" class="flex items-center gap-2 text-xs font-bold bg-slate-100 text-slate-700 px-4 py-2 rounded-full border border-slate-200 hover:bg-slate-200 transition cursor-pointer">
                    <i class="fas fa-user-circle text-base text-slate-500" id="userAuthIcon"></i>
                    <span id="userAuthText">User Sign In</span>
                </button>
                <a href="https://wa.me/923332637235" target="_blank" class="bg-emerald-600 text-white px-4 py-2 rounded-full font-bold hover:bg-emerald-700 transition shadow-sm flex items-center gap-2 text-xs">
                    <i class="fab fa-whatsapp text-sm"></i> WHATSAPP
                </a>
            </div>
        </div>
    </nav>

    <section id="home" class="relative bg-slate-950 text-white py-32 px-6 bg-cover bg-center" style="background-image: linear-gradient(to bottom, rgba(2, 6, 23, 0.8), rgba(6, 78, 59, 0.85)), url('https://images.unsplash.com/photo-1549880338-65ddcdfd017b?auto=format&fit=crop&w=1200&q=80');">
        <div class="max-w-7xl mx-auto text-center md:text-left relative z-10">
            <span class="bg-emerald-500/20 text-emerald-400 px-4 py-1.5 rounded-full text-xs font-bold uppercase tracking-widest border border-emerald-500/30">The Premium GB Gateway</span>
            <h1 class="text-4xl md:text-6xl font-extrabold mt-4 max-w-3xl">Your Journey Across the <span class="text-emerald-400">Northern Frontiers</span> Starts Here</h1>
            <p class="mt-4 text-slate-300 max-w-xl font-light text-sm md:text-base">Real-time calculations, validated local guidelines, secure cloud storage infrastructure, and direct live support agents.</p>
        </div>
    </section>

    <section id="destinations" class="py-20 px-6 max-w-7xl mx-auto">
        <div class="text-center max-w-3xl mx-auto mb-16">
            <h2 class="text-3xl font-black text-slate-900 tracking-tight mb-2">Iconic Landscapes</h2>
            <div class="w-16 h-1 bg-emerald-600 mx-auto rounded-full"></div>
        </div>
        <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
            <div class="bg-white rounded-2xl shadow-sm hover:shadow-md transition border border-slate-100 overflow-hidden group">
                <img src="https://images.unsplash.com/photo-1605649487212-47bdab064df7?auto=format&fit=crop&w=600&q=80" alt="Hunza" class="w-full h-44 object-cover group-hover:scale-105 transition duration-300">
                <div class="p-6">
                    <h3 class="text-xl font-bold text-slate-900 mb-1">Hunza Valley</h3>
                    <p class="text-slate-600 font-light text-xs leading-relaxed">Altit/Baltit Forts, Passu Cones, and Attabad Lake accessibility mappings.</p>
                </div>
            </div>
            <div class="bg-white rounded-2xl shadow-sm hover:shadow-md transition border border-slate-100 overflow-hidden group">
                <img src="https://images.unsplash.com/photo-1589308078059-be1415eab4c3?auto=format&fit=crop&w=600&q=80" alt="Skardu" class="w-full h-44 object-cover group-hover:scale-105 transition duration-300">
                <div class="p-6">
                    <h3 class="text-xl font-bold text-slate-900 mb-1">Skardu Plateau</h3>
                    <p class="text-slate-600 font-light text-xs leading-relaxed">Shangrila Basin, Cold Desert sand duning, and Deosai ecological reserves.</p>
                </div>
            </div>
            <div class="bg-white rounded-2xl shadow-sm hover:shadow-md transition border border-slate-100 overflow-hidden group">
                <img src="https://images.unsplash.com/photo-1464822759023-fed622ff2c3b?auto=format&fit=crop&w=600&q=80" alt="Ghizer" class="w-full h-44 object-cover group-hover:scale-105 transition duration-300">
                <div class="p-6">
                    <h3 class="text-xl font-bold text-slate-900 mb-1">Ghizer District</h3>
                    <p class="text-slate-600 font-light text-xs leading-relaxed">Phander Lake trout matching networks and clear deep-valley turquoise ecosystems.</p>
                </div>
            </div>
        </div>
    </section>

    <div class="bg-slate-900 text-white py-20 px-6">
        <div class="max-w-7xl mx-auto grid grid-cols-1 lg:grid-cols-2 gap-12">
            
            <section id="quote-system" class="bg-slate-800 p-8 rounded-3xl border border-slate-700/60 shadow-xl">
                <div class="mb-6">
                    <h2 class="text-2xl font-black">Instant Tour Planner</h2>
                    <p class="text-slate-400 text-xs mt-1">Select location metrics to stream baseline financial approximations.</p>
                </div>
                <form id="quoteForm" class="space-y-4 text-slate-900" onsubmit="return false;">
                    <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
                        <div class="sm:col-span-2"><input type="text" id="userName" required placeholder="Full Name" class="w-full bg-white px-4 py-3 rounded-xl border-none outline-none text-sm"></div>
                        <div class="sm:col-span-2"><input type="tel" id="userPhone" required placeholder="Contact Number (e.g., 0333XXXXXXX)" class="w-full bg-white px-4 py-3 rounded-xl border-none outline-none text-sm"></div>
                        <div class="sm:col-span-2">
                            <select id="destination" class="w-full bg-white px-4 py-3 rounded-xl outline-none border-none text-sm">
                                <option value="Gilgit City" data-price="35000">Gilgit City Axis Base (PKR 35,000)</option>
                                <option value="Naltar Valley" data-price="45000">Naltar Lakes & Ski Fields (PKR 45,000)</option>
                                <option value="Karimabad (Hunza)" data-price="48000">Hunza Core Karimabad Circuit (PKR 48,000)</option>
                                <option value="Attabad Lake" data-price="50000">Attabad Deep Mappings & Passu (PKR 50,000)</option>
                                <option value="Khunjerab Pass" data-price="55000">Khunjerab High Frontier Border (PKR 55,000)</option>
                                <option value="Skardu Town" data-price="50000">Skardu Urban & Kharpocho Base (PKR 50,000)</option>
                                <option value="Deosai National Park" data-price="60000">Deosai Alpine High Meadow Plateau (PKR 60,000)</option>
                                <option value="Fairy Meadows" data-price="55000">Fairy Meadows Nanga Parbat Base (PKR 55,000)</option>
                            </select>
                        </div>
                        <div class="sm:col-span-2">
                            <select id="days" class="w-full bg-white px-4 py-3 rounded-xl outline-none border-none text-sm">
                                <option value="5">Standard 5-Day Allocation Track</option>
                                <option value="7">Extended 7-Day Allocation Track</option>
                                <option value="10">Premium 10-Day Allocation Track</option>
                            </select>
                        </div>
                    </div>
                    <div class="bg-slate-950 p-4 rounded-xl border border-slate-700/80 text-center">
                        <span class="text-slate-400 text-xs block uppercase tracking-wider">Estimated Parameter Cost</span>
                        <span id="totalEstimate" class="text-2xl font-black text-emerald-400 mt-0.5 block">PKR 35,000</span>
                    </div>
                    <button type="button" id="submitBtn" class="w-full bg-emerald-500 text-slate-950 py-3.5 rounded-xl font-black text-sm hover:bg-emerald-400 transition cursor-pointer">Submit & Process Parameters</button>
                </form>
            </section>

            <section id="contact-form-section" class="bg-slate-800/50 p-8 rounded-3xl border border-slate-700/40 shadow-xl flex flex-col justify-between">
                <div>
                    <h2 class="text-2xl font-black">Dynamic Messaging Node</h2>
                    <p class="text-slate-400 text-xs mt-1">Submit non-pricing general requests directly to storage servers.</p>
                </div>
                <form id="inquiryForm" class="space-y-4 mt-6 text-slate-900">
                    <input type="text" id="inqSubject" required placeholder="Subject / Intent" class="w-full bg-white px-4 py-3 rounded-xl text-sm border-none outline-none">
                    <textarea id="inqMessage" rows="4" required placeholder="State your architectural requirements or questions explicitly..." class="w-full bg-white px-4 py-3 rounded-xl text-sm border-none outline-none"></textarea>
                    <button type="submit" class="w-full bg-slate-950 text-white py-3.5 rounded-xl font-bold text-sm hover:bg-slate-900 border border-slate-700 transition cursor-pointer">Transmit Message Node</button>
                </form>
            </section>

        </div>
    </div>

    <section id="company-details" class="py-20 px-6 max-w-7xl mx-auto grid grid-cols-1 lg:grid-cols-3 gap-12">
        
        <div class="space-y-4">
            <h3 class="text-xl font-black text-slate-900 uppercase tracking-tight">Corporate Architecture</h3>
            <div class="w-12 h-1 bg-emerald-600 rounded-full"></div>
            <p class="text-slate-600 font-light text-xs leading-relaxed">Discover Gilgit-Baltistan operates as a digitized hub engineered to provide accurate route mapping, localized asset dispatch solutions, and security auditing metrics for northern operations across Pakistan.</p>
            <div class="bg-white p-4 rounded-xl border border-slate-200 space-y-2 text-xs">
                <div><span class="font-bold text-slate-700">HQ Axis:</span> Gilgit Main, Gilgit-Baltistan, PK</div>
                <div><span class="font-bold text-slate-700">Operations Node:</span> info@discovergb.com</div>
                <div><span class="font-bold text-slate-700">Registry Token:</span> DGB-2026-SSL</div>
            </div>
        </div>

        <div id="faq-section" class="space-y-3">
            <h3 class="text-xl font-black text-slate-900 uppercase tracking-tight">Operational FAQs</h3>
            <div class="w-12 h-1 bg-emerald-600 rounded-full mb-4"></div>
            
            <div class="bg-white border border-slate-200 rounded-xl overflow-hidden text-xs">
                <button onclick="toggleFaq(1)" class="w-full p-4 text-left font-bold text-slate-800 flex justify-between items-center bg-slate-50/50">
                    <span>How are baseline price indexes compiled?</span><i class="fas fa-chevron-down text-slate-400" id="faqIcon1"></i>
                </button>
                <div id="faqAns1" class="hidden p-4 border-t border-slate-100 text-slate-600 font-light bg-white">Calculations run off fixed local multi-tier multipliers assessing mileage base values, fuel indices, and hotel standard tiers.</div>
            </div>

            <div class="bg-white border border-slate-200 rounded-xl overflow-hidden text-xs">
                <button onclick="toggleFaq(2)" class="w-full p-4 text-left font-bold text-slate-800 flex justify-between items-center bg-slate-50/50">
                    <span>Is identity encryption handled securely?</span><i class="fas fa-chevron-down text-slate-400" id="faqIcon2"></i>
                </button>
                <div id="faqAns2" class="hidden p-4 border-t border-slate-100 text-slate-600 font-light bg-white">All entries process through automated security pathways into isolated cloud nodes accessible exclusively via certified tokens.</div>
            </div>
        </div>

        <div class="space-y-4">
            <h3 class="text-xl font-black text-slate-900 uppercase tracking-tight">Privacy Architecture</h3>
            <div class="w-12 h-1 bg-emerald-600 rounded-full"></div>
            <div class="bg-white p-5 rounded-2xl border border-slate-200 text-xs text-slate-600 font-light space-y-2 max-h-56 overflow-y-auto custom-scrollbar">
                <p class="font-bold text-slate-800">Data Access Protocols:</p>
                <p>We process your baseline communication nodes, identity emails, phone parameters, and calculation data strictly to provide internal dashboard processing maps.</p>
                <p class="font-bold text-slate-800">Retention Matrix:</p>
                <p>Leads are kept inside secured databases unless purged manually by server network operators via encrypted commands.</p>
            </div>
        </div>

    </section>

    <section id="userDashboardSection" class="max-w-7xl mx-auto px-6 mb-20 hidden">
        <div class="bg-white border border-slate-200 rounded-3xl p-6 shadow-sm">
            <h3 class="text-lg font-black text-slate-900 mb-4 flex items-center gap-2"><i class="fas fa-history text-emerald-600"></i> Your Transmission Log Logs (Personal History)</h3>
            <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                <div>
                    <h4 class="text-xs font-bold uppercase text-slate-400 mb-2">Quote Mappings</h4>
                    <div id="userQuotesList" class="space-y-2 text-xs"></div>
                </div>
                <div>
                    <h4 class="text-xs font-bold uppercase text-slate-400 mb-2">General Message Submissions</h4>
                    <div id="userMessagesList" class="space-y-2 text-xs"></div>
                </div>
            </div>
        </div>
    </section>

    <section id="testimonials" class="py-12 bg-slate-100 border-t border-slate-200 px-6">
        <div class="max-w-7xl mx-auto text-center mb-8">
            <h3 class="text-xl font-black text-slate-900">Verified System Feedback</h3>
        </div>
        <div class="max-w-4xl mx-auto grid grid-cols-1 md:grid-cols-2 gap-6 text-xs text-slate-600 font-light italic">
            <div class="bg-white p-4 rounded-xl border border-slate-200">"Realtime billing calculation framework works beautifully. Highly accurate parameters." - Ali A.</div>
            <div class="bg-white p-4 rounded-xl border border-slate-200">"Secure dashboard structures and neat communication pathways." - Zainab K.</div>
        </div>
    </section>

    <div id="liveChatWidget" class="fixed bottom-6 right-6 z-50 flex flex-col items-end">
        <div id="chatWindow" class="w-80 h-96 bg-slate-900 text-white rounded-2xl border border-slate-800 shadow-2xl flex flex-col hidden mb-4 overflow-hidden">
            <div class="bg-slate-950 p-4 border-b border-slate-800 flex justify-between items-center">
                <div class="flex items-center gap-2 text-xs font-bold text-emerald-400">
                    <span class="w-2 h-2 bg-emerald-500 rounded-full animate-pulse"></span> Network Support Chat
                </div>
                <button onclick="toggleChatWindow()" class="text-slate-400 hover:text-white text-sm cursor-pointer"><i class="fas fa-minus"></i></button>
            </div>
            <div id="chatMessagesPipeline" class="flex-1 p-4 overflow-y-auto space-y-3 text-xs custom-scrollbar bg-slate-900/60"></div>
            <div class="p-3 bg-slate-950 border-t border-slate-800 flex gap-2">
                <input type="text" id="chatInputPayload" placeholder="Type a message..." class="flex-1 bg-slate-800 text-white text-xs rounded-lg px-3 border border-slate-700 outline-none">
                <button id="sendChatPayloadBtn" class="bg-emerald-600 text-white px-3 py-1.5 rounded-lg text-xs font-bold cursor-pointer hover:bg-emerald-500"><i class="fas fa-paper-plane"></i></button>
            </div>
        </div>
        <button onclick="toggleChatWindow()" class="bg-slate-900 hover:bg-slate-950 text-white w-14 h-14 rounded-full shadow-2xl flex items-center justify-center border border-slate-800 hover:border-emerald-500 transition cursor-pointer group">
            <i class="fas fa-comments text-xl text-emerald-400 group-hover:scale-110 transition"></i>
        </button>
    </div>

    <div id="adminModal" class="fixed inset-0 bg-slate-950/95 hidden items-center justify-center p-4 z-50 overflow-y-auto">
        <div class="bg-slate-900 border border-slate-800 p-6 rounded-3xl max-w-6xl w-full relative">
            <button id="closeAdminBtn" class="absolute top-4 right-4 text-slate-400 hover:text-white text-xl cursor-pointer"><i class="fas fa-times"></i></button>
            
            <div id="pinGateway" class="text-center space-y-4 py-12">
                <i class="fas fa-user-shield text-5xl text-emerald-500"></i>
                <h3 class="text-2xl font-black text-white">System Security Pin</h3>
                <input type="password" id="secretKeyField" placeholder="Enter System Passcode" class="bg-slate-800 text-white text-center px-4 py-3 rounded-xl border border-slate-700 text-lg w-64 block mx-auto tracking-widest outline-none">
                <button id="verifyPinBtn" class="bg-emerald-500 text-slate-950 px-6 py-2.5 rounded-xl font-bold hover:bg-emerald-400 transition cursor-pointer">Verify Token</button>
            </div>

            <div id="googleGateway" class="text-center space-y-4 hidden py-12">
                <i class="fab fa-google text-5xl text-blue-500"></i>
                <h3 class="text-2xl font-black text-white">Identity Credentials</h3>
                <button id="googleSignInBtn" class="bg-white text-slate-900 px-6 py-3 rounded-xl font-bold hover:bg-slate-100 transition inline-flex items-center gap-2 cursor-pointer">
                    <i class="fab fa-google text-red-500"></i> Authenticate Administrator
                </button>
            </div>

            <div id="adminDashboard" class="hidden space-y-6">
                <div class="flex flex-col sm:flex-row justify-between items-start sm:items-center border-b border-slate-800 pb-4 gap-4">
                    <h3 class="text-xl font-black text-white flex items-center gap-2"><i class="fas fa-database text-emerald-500"></i> Master Node Operations Dashboard</h3>
                    <button id="logoutBtn" class="bg-rose-600/20 text-rose-400 border border-rose-500/30 px-4 py-2 rounded-lg text-xs font-bold hover:bg-rose-600 hover:text-white transition cursor-pointer">Sign Out</button>
                </div>
                
                <div class="flex flex-wrap gap-2 mb-4">
                    <button id="tabLeads" class="px-4 py-2 rounded-lg text-xs font-bold bg-emerald-600 text-slate-950 cursor-pointer">Tour Quotes</button>
                    <button id="tabMessages" class="px-4 py-2 rounded-lg text-xs font-bold bg-slate-800 text-slate-400 cursor-pointer">General Messages</button>
                    <button id="tabChats" class="px-4 py-2 rounded-lg text-xs font-bold bg-slate-800 text-slate-400 cursor-pointer">Support Desk Chats</button>
                </div>

                <div class="overflow-x-auto custom-scrollbar max-h-96">
                    
                    <table id="tableLeads" class="w-full text-left border-collapse">
                        <thead>
                            <tr class="text-slate-400 border-b border-slate-800 text-xs uppercase bg-slate-950/40">
                                <th class="p-3">Customer Profile</th>
                                <th class="p-3">Destination</th>
                                <th class="p-3">Metrics</th>
                                <th class="p-3">Price</th>
                                <th class="p-3 text-center">Administrative Control Actions</th>
                            </tr>
                        </thead>
                        <tbody id="leadsTableBody" class="text-xs divide-y divide-slate-800 text-slate-300"></tbody>
                    </table>

                    <table id="tableMessages" class="w-full text-left border-collapse hidden">
                        <thead>
                            <tr class="text-slate-400 border-b border-slate-800 text-xs uppercase bg-slate-950/40">
                                <th class="p-3">Sender Context</th>
                                <th class="p-3">Intent Subject</th>
                                <th class="p-3">Payload Data Message</th>
                                <th class="p-3">Timestamp</th>
                                <th class="p-3 text-center">Administrative Control Actions</th>
                            </tr>
                        </thead>
                        <tbody id="messagesTableBody" class="text-xs divide-y divide-slate-800 text-slate-300"></tbody>
                    </table>

                    <div id="tableChatsContainer" class="hidden space-y-4">
                        <div class="grid grid-cols-1 lg:grid-cols-3 gap-4">
                            <div class="bg-slate-950 p-4 rounded-xl space-y-2 border border-slate-800">
                                <h4 class="text-xs font-bold uppercase text-slate-500 tracking-wider">Active Stream Hubs</h4>
                                <div id="adminChatHubsList" class="space-y-1 divide-y divide-slate-900"></div>
                            </div>
                            <div class="lg:col-span-2 bg-slate-950 p-4 rounded-xl border border-slate-800 flex flex-col h-80">
                                <div id="adminChatAreaTitle" class="text-xs text-emerald-400 font-bold mb-2 pb-2 border-b border-slate-800">Select an active user thread from left list container</div>
                                <div id="adminChatMessagesArea" class="flex-1 overflow-y-auto space-y-2 p-2 text-xs custom-scrollbar"></div>
                                <div class="mt-2 pt-2 border-t border-slate-800 flex gap-2">
                                    <input type="text" id="adminChatInput" placeholder="Reply to user directly..." class="flex-1 bg-slate-800 rounded-lg px-3 border border-slate-700 text-xs text-white outline-none">
                                    <button id="adminSendChatBtn" class="bg-emerald-600 text-slate-950 px-4 py-1.5 rounded-lg text-xs font-bold cursor-pointer hover:bg-emerald-500">Send</button>
                                </div>
                            </div>
                        </div>
                    </div>

                </div>
            </div>
        </div>
    </div>

    <footer class="bg-slate-950 text-slate-500 py-12 px-6 border-t border-slate-900 text-xs">
        <div class="max-w-7xl mx-auto flex flex-col md:flex-row justify-between items-center gap-6">
            <div class="text-center md:text-left">
                <p class="font-bold text-slate-300">Discover Gilgit-Baltistan System Engine</p>
                <p class="mt-1 text-slate-600">&copy; 2026 Enterprise Pipeline Hub. Architectural rights enforced.</p>
            </div>
            <div class="flex gap-6 text-lg">
                <a href="https://wa.me/923332637235" target="_blank" class="hover:text-emerald-500 transition" title="WhatsApp Communication Gateway"><i class="fab fa-whatsapp"></i></a>
                <a href="https://www.facebook.com/profile.php?id=61590624220027&mibextid=ZbWKwL" target="_blank" class="hover:text-blue-500 transition" title="Facebook Official Community Page Hub"><i class="fab fa-facebook-f"></i></a>
                <a href="#home" class="hover:text-white transition" title="Top Return"><i class="fas fa-arrow-up"></i></a>
            </div>
        </div>
    </footer>

    <script type="module">
        import { initializeApp } from "https://www.gstatic.com/firebasejs/10.8.0/firebase-app.js";
        import { getDatabase, ref, set, push, onValue, remove } from "https://www.gstatic.com/firebasejs/10.8.0/firebase-database.js";
        import { getAuth, signInWithPopup, GoogleAuthProvider, signOut, onAuthStateChanged } from "https://www.gstatic.com/firebasejs/10.8.0/firebase-auth.js";

        const firebaseConfig = {
            apiKey: "AIzaSyBiti-Ih5nxvRQ8Xt9YImiN1X3RnPoXoTI",
            authDomain: "gilgit-79048.firebaseapp.com",
            databaseURL: "https://gilgit-79048-default-rtdb.firebaseio.com",
            projectId: "gilgit-79048",
            storageBucket: "gilgit-79048.firebasestorage.app",
            messagingSenderId: "784852692962",
            appId: "1:784852692962:web:eab87b313e024ebf7953bb"
        };

        const app = initializeApp(firebaseConfig);
        const database = getDatabase(app);
        const auth = getAuth(app);
        const provider = new GoogleAuthProvider();

        let currentUser = null;
        let activeAdminSession = false;
        let selectedAdminChatUID = null;

        // Context Elements Tracking
        const destinationSelect = document.getElementById('destination');
        const daysSelect = document.getElementById('days');
        const totalEstimateDisplay = document.getElementById('totalEstimate');
        const submitBtn = document.getElementById('submitBtn');
        const logoTrigger = document.getElementById('logoTrigger');
        const adminModal = document.getElementById('adminModal');
        const userAuthBtn = document.getElementById('userAuthBtn');

        // Toggle Accordion Interface Mappings
        window.toggleFaq = function(id) {
            const el = document.getElementById(`faqAns${id}`);
            const icon = document.getElementById(`faqIcon${id}`);
            if(el.classList.contains('hidden')) {
                el.classList.remove('hidden');
                icon.className = "fas fa-chevron-up text-emerald-500";
            } else {
                el.classList.add('hidden');
                icon.className = "fas fa-chevron-down text-slate-400";
            }
        };

        window.toggleChatWindow = function() {
            const win = document.getElementById('chatWindow');
            win.classList.toggle('hidden');
        };

        // Price Engine Matrix logic
        function calculateQuote() {
            const selectedOption = destinationSelect.options[destinationSelect.selectedIndex];
            const basePrice = parseInt(selectedOption.getAttribute('data-price'));
            const daysMultiplier = parseInt(daysSelect.value) / 5;
            const total = Math.round(basePrice * daysMultiplier);
            totalEstimateDisplay.innerText = `PKR ${total.toLocaleString()}`;
        }
        destinationSelect.addEventListener('change', calculateQuote);
        daysSelect.addEventListener('change', calculateQuote);

        // Core Identity Listening Observer (Handles dual user/admin rendering mechanics)
        onAuthStateChanged(auth, (user) => {
            if (user) {
                currentUser = user;
                document.getElementById('userAuthText').innerText = user.displayName || user.email;
                document.getElementById('userAuthIcon').className = "fas fa-check-circle text-emerald-500 text-base";
                document.getElementById('userDashboardSection').classList.remove('hidden');
                syncUserHistoryLogs();
                syncUserLiveChatStreams();
            } else {
                currentUser = null;
                document.getElementById('userAuthText').innerText = "User Sign In";
                document.getElementById('userAuthIcon').className = "fas fa-user-circle text-slate-500 text-base";
                document.getElementById('userDashboardSection').classList.add('hidden');
                document.getElementById('chatMessagesPipeline').innerHTML = "<p class='text-slate-500 p-2 text-center'>Please log in to initiate real-time communication.</p>";
            }
        });

        // User Identity Execution Layer
        userAuthBtn.addEventListener('click', () => {
            if(currentUser) {
                if(confirm("Terminate your current application session?")) { signOut(auth); }
            } else {
                signInWithPopup(auth, provider).catch(err => alert("Handshake Error: " + err.message));
            }
        });

        // Push Lead Entry Protocol Node
        submitBtn.addEventListener('click', () => {
            const name = document.getElementById('userName').value.trim();
            const phone = document.getElementById('userPhone').value.trim();
            const dest = destinationSelect.value;
            const duration = daysSelect.value;
            const cost = totalEstimateDisplay.innerText;

            if(!name || !phone) { alert("Complete parameters."); return; }

            const targetRef = push(ref(database, 'leads'));
            set(targetRef, {
                uid: currentUser ? currentUser.uid : "anonymous",
                email: currentUser ? currentUser.email : "anonymous",
                customerName: name,
                customerPhone: phone,
                selectedDestination: dest,
                tripDurationDays: duration,
                calculatedQuotePrice: cost,
                timestamp: new Date().toLocaleString()
            }).then(() => {
                const text = encodeURIComponent(`Discover GB Tour Node:\nName: ${name}\nDestination: ${dest}\nPrice: ${cost}`);
                window.open(`https://wa.me/923332637235?text=${text}`, '_blank');
            });
        });

        // Push Message Entry Protocol Node
        document.getElementById('inquiryForm').addEventListener('submit', (e) => {
            e.preventDefault();
            const subject = document.getElementById('inqSubject').value.trim();
            const msg = document.getElementById('inqMessage').value.trim();

            set(push(ref(database, 'messages')), {
                uid: currentUser ? currentUser.uid : "anonymous",
                senderEmail: currentUser ? currentUser.email : "anonymous-node@system.com",
                messageSubject: subject,
                detailedText: msg,
                timestamp: new Date().toLocaleString()
            }).then(() => {
                alert("Message transmission log finalized.");
                document.getElementById('inquiryForm').reset();
            });
        });

        // User History Sync Logs Interface Logic
        function syncUserHistoryLogs() {
            if(!currentUser) return;
            
            // Sync Quotes
            onValue(ref(database, 'leads'), (snap) => {
                const list = document.getElementById('userQuotesList');
                list.innerHTML = "";
                const data = snap.val();
                let count = 0;
                if(data) {
                    Object.keys(data).forEach(k => {
                        if(data[k].uid === currentUser.uid) {
                            count++;
                            list.innerHTML += `<div class='bg-slate-100 p-3 rounded-lg border border-slate-200'>
                                <strong>${data[k].selectedDestination}</strong> (${data[k].tripDurationDays} Days)<br>
                                <span class='text-emerald-600 font-bold'>${data[k].calculatedQuotePrice}</span> <span class='text-[10px] text-slate-400 float-right'>${data[k].timestamp}</span>
                            </div>`;
                        }
                    });
                }
                if(count === 0) list.innerHTML = "<p class='text-slate-400 italic text-[11px]'>No quote executions matched to profile node.</p>";
            });

            // Sync Messages Nodes
            onValue(ref(database, 'messages'), (snap) => {
                const list = document.getElementById('userMessagesList');
                list.innerHTML = "";
                const data = snap.val();
                let count = 0;
                if(data) {
                    Object.keys(data).forEach(k => {
                        if(data[k].uid === currentUser.uid) {
                            count++;
                            list.innerHTML += `<div class='bg-slate-100 p-3 rounded-lg border border-slate-200'>
                                <strong>Subject: ${data[k].messageSubject}</strong><br>
                                <p class='text-slate-500 mt-1'>${data[k].detailedText}</p>
                                <span class='text-[10px] text-slate-400 block mt-1'>${data[k].timestamp}</span>
                            </div>`;
                        }
                    });
                }
                if(count === 0) list.innerHTML = "<p class='text-slate-400 italic text-[11px]'>No transmission entries mapped to current profile.</p>";
            });
        }

        // Live Chat Sync Pipelines (User Module Context)
        function syncUserLiveChatStreams() {
            if(!currentUser) return;
            onValue(ref(database, `chats/${currentUser.uid}`), (snap) => {
                const container = document.getElementById('chatMessagesPipeline');
                container.innerHTML = "";
                const data = snap.val();
                if(!data) { container.innerHTML = "<p class='text-slate-500 text-center p-4'>Send a message token below to establish support handshake link.</p>"; return; }
                Object.keys(data).forEach(k => {
                    const msg = data[k];
                    const isAdmin = msg.sender === 'admin';
                    container.innerHTML += `<div class="flex flex-col ${isAdmin ? 'items-start' : 'items-end'}">
                        <div class="p-2.5 rounded-xl max-w-[85%] ${isAdmin ? 'bg-slate-800 text-slate-200 rounded-tl-none' : 'bg-emerald-600 text-white rounded-tr-none'}">
                            ${msg.text}
                            <span class="block text-[8px] opacity-60 text-right mt-1">${msg.time}</span>
                        </div>
                    </div>`;
                });
                container.scrollTop = container.scrollHeight;
            });
        }

        document.getElementById('sendChatPayloadBtn').addEventListener('click', executeUserChatSend);
        function executeUserChatSend() {
            const input = document.getElementById('chatInputPayload');
            const txt = input.value.trim();
            if(!txt || !currentUser) return;
            const target = ref(database, `chats/${currentUser.uid}`);
            push(target, {
                sender: currentUser.uid,
                senderEmail: currentUser.email,
                text: txt,
                time: new Date().toLocaleTimeString([], {hour: '2-digit', minute:'2-digit'})
            }).then(() => { input.value = ""; });
        }

        // Easter Egg Tap Matrix Triggers (5 Fast Click Events tracking)
        let taps = 0; let windowTimeout;
        logoTrigger.addEventListener('click', () => {
            taps++; clearTimeout(windowTimeout);
            if(taps === 5) { taps = 0; adminModal.classList.remove('hidden'); adminModal.classList.add('flex'); }
            windowTimeout = setTimeout(() => { taps = 0; }, 2500);
        });
        document.getElementById('closeAdminBtn').addEventListener('click', () => { adminModal.className = "fixed inset-0 bg-slate-950/95 hidden items-center justify-center p-4 z-50 overflow-y-auto"; });

        // Admin Validation Action Sequences
        document.getElementById('verifyPinBtn').addEventListener('click', () => {
            if(document.getElementById('secretKeyField').value === "5426") {
                document.getElementById('pinGateway').classList.add('hidden');
                document.getElementById('googleGateway').classList.remove('hidden');
            } else { alert("Passcode validation rejection."); }
        });

        document.getElementById('googleSignInBtn').addEventListener('click', () => {
            signInWithPopup(auth, provider).then(() => {
                document.getElementById('googleGateway').classList.add('hidden');
                document.getElementById('adminDashboard').classList.remove('hidden');
                activeAdminSession = true;
                initializeAdminLiveViewports();
            }).catch(err => alert("Auth handshake failure: " + err.message));
        });

        // Global Destructive Admin Control Wipe Actions (Deletes specific record node)
        window.executeNodeDeletion = function(nodePath, key) {
            if(confirm(`Execute absolute database wipe for token node [${key}]?`)) {
                remove(ref(database, `${nodePath}/${key}`))
                .then(() => alert("Target sequence cleared from live datastream successfully."))
                .catch(err => alert("Execution abort: " + err.message));
            }
        };

        // Master Viewport Tabs Switching (Admin Dashboard)
        const tLeads = document.getElementById('tableLeads');
        const tMsgs = document.getElementById('tableMessages');
        const tChats = document.getElementById('tableChatsContainer');
        const btnLeads = document.getElementById('tabLeads');
        const btnMsgs = document.getElementById('tabMessages');
        const btnChats = document.getElementById('tabChats');

        btnLeads.addEventListener('click', () => {
            tLeads.classList.remove('hidden'); tMsgs.classList.add('hidden'); tChats.classList.add('hidden');
            btnLeads.className = "px-4 py-2 rounded-lg text-xs font-bold bg-emerald-600 text-slate-950 cursor-pointer";
            btnMsgs.className = "px-4 py-2 rounded-lg text-xs font-bold bg-slate-800 text-slate-400 cursor-pointer";
            btnChats.className = "px-4 py-2 rounded-lg text-xs font-bold bg-slate-800 text-slate-400 cursor-pointer";
        });
        btnMsgs.addEventListener('click', () => {
            tLeads.classList.add('hidden'); tMsgs.classList.remove('hidden'); tChats.classList.add('hidden');
            btnLeads.className = "px-4 py-2 rounded-lg text-xs font-bold bg-slate-800 text-slate-400 cursor-pointer";
            btnMsgs.className = "px-4 py-2 rounded-lg text-xs font-bold bg-emerald-600 text-slate-950 cursor-pointer";
            btnChats.className = "px-4 py-2 rounded-lg text-xs font-bold bg-slate-800 text-slate-400 cursor-pointer";
        });
        btnChats.addEventListener('click', () => {
            tLeads.classList.add('hidden'); tMsgs.classList.add('hidden'); tChats.classList.remove('hidden');
            btnLeads.className = "px-4 py-2 rounded-lg text-xs font-bold bg-slate-800 text-slate-400 cursor-pointer";
            btnMsgs.className = "px-4 py-2 rounded-lg text-xs font-bold bg-slate-800 text-slate-400 cursor-pointer";
            btnChats.className = "px-4 py-2 rounded-lg text-xs font-bold bg-emerald-600 text-slate-950 cursor-pointer";
        });

        // Initialize Admin Core Listeners
        function initializeAdminLiveViewports() {
            if(!activeAdminSession) return;

            // Stream Quotes (Leads)
            onValue(ref(database, 'leads'), (snap) => {
                const tbody = document.getElementById('leadsTableBody'); tbody.innerHTML = "";
                const data = snap.val();
                if(!data) { tbody.innerHTML = "<tr><td colspan='5' class='p-4 text-center text-slate-600'>No quotes inside storage node.</td></tr>"; return; }
                Object.keys(data).reverse().forEach(k => {
                    const r = data[k];
                    tbody.innerHTML += `<tr class='border-b border-slate-800/60 hover:bg-slate-950/20'>
                        <td class='p-3 font-bold text-white'>${r.customerName || 'N/A'}<br><span class='text-slate-500 font-normal text-[11px]'>${r.customerPhone || 'N/A'} (${r.email || 'Anon'})</span></td>
                        <td class='p-3'>${r.selectedDestination || 'N/A'}</td>
                        <td class='p-3'>${r.tripDurationDays || '5'} Days</td>
                        <td class='p-3 text-emerald-400 font-bold'>${r.calculatedQuotePrice || '0'}</td>
                        <td class='p-3 text-center space-x-2'>
                            <a href='https://wa.me/${(r.customerPhone || '').replace(/[^0-9]/g, '')}' target='_blank' class='bg-emerald-600/20 text-emerald-400 border border-emerald-500/30 px-2.5 py-1 rounded text-[10px] font-bold inline-block'>Chat</a>
                            <button onclick="executeNodeDeletion('leads', '${k}')" class='bg-rose-600/20 text-rose-400 border border-rose-500/30 px-2.5 py-1 rounded text-[10px] font-bold hover:bg-rose-600 hover:text-white transition cursor-pointer'>Delete</button>
                        </td>
                    </tr>`;
                });
            });

            // Stream Offline Message Nodes
            onValue(ref(database, 'messages'), (snap) => {
                const tbody = document.getElementById('messagesTableBody'); tbody.innerHTML = "";
                const data = snap.val();
                if(!data) { tbody.innerHTML = "<tr><td colspan='5' class='p-4 text-center text-slate-600'>No messaging nodes found inside storage ref.</td></tr>"; return; }
                Object.keys(data).reverse().forEach(k => {
                    const r = data[k];
                    tbody.innerHTML += `<tr class='border-b border-slate-800/60 hover:bg-slate-950/20'>
                        <td class='p-3 text-emerald-400 font-semibold'>${r.senderEmail || 'N/A'}</td>
                        <td class='p-3 font-bold text-white'>${r.messageSubject || 'N/A'}</td>
                        <td class='p-3 text-slate-400 max-w-xs break-words'>${r.detailedText || 'N/A'}</td>
                        <td class='p-3 text-slate-500'>${r.timestamp || 'N/A'}</td>
                        <td class='p-3 text-center'>
                            <button onclick="executeNodeDeletion('messages', '${k}')" class='bg-rose-600/20 text-rose-400 border border-rose-500/30 px-2.5 py-1 rounded text-[10px] font-bold hover:bg-rose-600 hover:text-white transition cursor-pointer'>Clear</button>
                        </td>
                    </tr>`;
                });
            });

            // Stream Interactive Chat Session Lists
            onValue(ref(database, 'chats'), (snap) => {
                const hub = document.getElementById('adminChatHubsList'); hub.innerHTML = "";
                const data = snap.val();
                if(!data) { hub.innerHTML = "<p class='text-slate-600 text-center text-[11px] p-2'>No active support handshake threads.</p>"; return; }
                Object.keys(data).forEach(uid => {
                    const threads = data[uid];
                    const keyArray = Object.keys(threads);
                    const lastMsg = threads[keyArray[keyArray.length - 1]];
                    hub.innerHTML += `<button onclick="mountAdminChatChannel('${uid}', '${lastMsg.senderEmail || 'User Session'}')" class="w-full text-left p-2.5 block rounded hover:bg-slate-800 text-[11px] transition text-slate-300 border-b border-slate-900">
                        <div class='font-bold text-white truncate'>${lastMsg.senderEmail || 'Anon Thread'}</div>
                        <div class='text-slate-500 truncate mt-0.5'>${lastMsg.text}</div>
                    </button>`;
                });
            });
        }

        // Mount Targeted Message Box Thread (Admin Desk)
        window.mountAdminChatChannel = function(uid, emailTitle) {
            selectedAdminChatUID = uid;
            document.getElementById('adminChatAreaTitle').innerText = `Active Session Node: ${emailTitle}`;
            onValue(ref(database, `chats/${uid}`), (snap) => {
                if(selectedAdminChatUID !== uid) return;
                const canvas = document.getElementById('adminChatMessagesArea'); canvas.innerHTML = "";
                const data = snap.val();
                if(data) {
                    Object.keys(data).forEach(k => {
                        const m = data[k];
                        const isSystemAdmin = m.sender === 'admin';
                        canvas.innerHTML += `<div class="flex flex-col ${isSystemAdmin ? 'items-end' : 'items-start'}">
                            <div class="p-2 rounded-lg max-w-[80%] ${isSystemAdmin ? 'bg-emerald-600 text-slate-950 font-semibold' : 'bg-slate-800 text-slate-300'}">
                                ${m.text}
                                <span class="block text-[7px] opacity-40 text-right mt-0.5">${m.time}</span>
                            </div>
                        </div>`;
                    });
                    canvas.scrollTop = canvas.scrollHeight;
                }
            });
        };

        // Dispatch Admin Reply Method
        document.getElementById('adminSendChatBtn').addEventListener('click', () => {
            const input = document.getElementById('adminChatInput');
            const txt = input.value.trim();
            if(!txt || !selectedAdminChatUID) return;
            push(ref(database, `chats/${selectedAdminChatUID}`), {
                sender: 'admin',
                senderEmail: 'System Administrator Operations Desk',
                text: txt,
                time: new Date().toLocaleTimeString([], {hour: '2-digit', minute:'2-digit'})
            }).then(() => { input.value = ""; });
        });

        // Global Session Revocation
        document.getElementById('logoutBtn').addEventListener('click', () => {
            signOut(auth).then(() => {
                activeAdminSession = false; selectedAdminChatUID = null;
                document.getElementById('adminDashboard').classList.add('hidden');
                document.getElementById('pinGateway').classList.remove('hidden');
                document.getElementById('secretKeyField').value = "";
                adminModal.className = "fixed inset-0 bg-slate-950/95 hidden items-center justify-center p-4 z-50 overflow-y-auto";
            });
        });

    </script>
</body>
</html>
