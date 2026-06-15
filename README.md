<html lang="ur" dir="rtl" id="appHtml">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>Discover GB - Ultra Modern Hub</title>
    
    <!-- Firebase Compatibility SDKs -->
    <script src="https://www.gstatic.com/firebasejs/10.8.0/firebase-app-compat.js"></script>
    <script src="https://www.gstatic.com/firebasejs/10.8.0/firebase-auth-compat.js"></script>
    <script src="https://www.gstatic.com/firebasejs/10.8.0/firebase-database-compat.js"></script>
    
    <style>
        :root {
            --bg-gradient: linear-gradient(135deg, #0f172a 0%, #1e1b4b 100%);
            --glass-bg: rgba(255, 255, 255, 0.08);
            --glass-border: rgba(255, 255, 255, 0.15);
            --accent-color: #38bdf8;
            --text-main: #f8fafc;
            --text-sub: #94a3b8;
        }

        * {
            margin: 0; padding: 0; box-sizing: border-box;
            font-family: 'Segoe UI', Roboto, -apple-system, sans-serif;
            -webkit-tap-highlight-color: transparent;
        }

        body {
            background: var(--bg-gradient);
            color: var(--text-main);
            padding-bottom: 90px;
            min-height: 100vh;
        }

        .glass-card {
            background: var(--glass-bg);
            backdrop-filter: blur(12px);
            -webkit-backdrop-filter: blur(12px);
            border: 1px solid var(--glass-border);
            border-radius: 20px;
            padding: 20px;
            margin: 15px;
            box-shadow: 0 8px 32px 0 rgba(0, 0, 0, 0.3);
        }

        .app-header {
            background: rgba(15, 23, 42, 0.6);
            backdrop-filter: blur(10px);
            border-bottom: 1px solid var(--glass-border);
            padding: 15px 20px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            position: sticky; top: 0; z-index: 1000;
        }

        /* Logo Button style (Secret Trigger) */
        .brand-title { font-weight: 800; font-size: 1.2rem; color: #fff; cursor: pointer; user-select: none; }
        
        .lang-btn {
            background: var(--accent-color); color: #0f172a;
            border: none; padding: 8px 16px; border-radius: 30px; font-weight: bold;
            cursor: pointer; font-size: 0.85rem; box-shadow: 0 4px 14px rgba(56, 189, 248, 0.4);
        }

        .hero-section { text-align: center; padding: 30px 15px; }
        .hero-section h1 { font-size: 1.8rem; margin-bottom: 8px; color: #fff; }
        .hero-section p { color: var(--text-sub); font-size: 0.9rem; }

        label { font-size: 0.85rem; color: var(--text-sub); display: block; margin-bottom: 6px; }
        select, input, textarea {
            width: 100%; padding: 14px; margin-bottom: 15px;
            background: rgba(255, 255, 255, 0.05); border: 1px solid var(--glass-border);
            border-radius: 12px; color: #fff; outline: none; font-size: 0.95rem;
        }
        select option { background: #0f172a; color: #fff; }

        .action-btn {
            background: linear-gradient(90deg, #2563eb, #38bdf8);
            color: white; border: none; padding: 14px; border-radius: 12px;
            font-weight: bold; font-size: 1rem; width: 100%; cursor: pointer;
            box-shadow: 0 4px 20px rgba(37, 99, 235, 0.3);
        }

        .dest-card {
            border-radius: 20px; overflow: hidden; background: rgba(255, 255, 255, 0.03);
            border: 1px solid var(--glass-border); margin-bottom: 15px;
        }
        .dest-card img { width: 100%; height: 180px; object-fit: cover; }
        .dest-info { padding: 15px; }
        .dest-info h3 { color: var(--accent-color); font-size: 1.1rem; margin-bottom: 5px; }
        .dest-info p { color: var(--text-sub); font-size: 0.85rem; }

        .review-item {
            background: rgba(255,255,255,0.03); padding: 12px;
            border-radius: 12px; margin-top: 10px; border-right: 3px solid var(--accent-color);
        }

        /* Admin Secret View Modal Styling */
        .admin-modal {
            display: none; position: fixed; top: 0; left: 0; width: 100%; height: 100%;
            background: rgba(15, 23, 42, 0.95); z-index: 9999; overflow-y: auto; padding: 20px;
        }
        .admin-header { display: flex; justify-content: space-between; align-items: center; margin-bottom: 20px; border-bottom: 1px solid var(--glass-border); padding-bottom: 10px; }
        .data-row {
            background: rgba(255,255,255,0.05); padding: 15px; border-radius: 12px;
            margin-bottom: 12px; border-left: 4px solid var(--accent-color); font-size: 0.9rem;
        }

        .bottom-dock {
            position: fixed; bottom: 0; left: 0; right: 0;
            background: rgba(15, 23, 42, 0.8); backdrop-filter: blur(15px);
            border-top: 1px solid var(--glass-border); height: 70px;
            display: flex; justify-content: space-around; align-items: center; z-index: 2000;
        }
        .dock-tab { display: flex; flex-direction: column; align-items: center; color: var(--text-sub); text-decoration: none; font-size: 0.75rem; }
        .dock-tab.active { color: var(--accent-color); }
        .dock-icon { font-size: 1.4rem; margin-bottom: 2px; }

        .float-wa {
            background: #25D366; color: white; width: 50px; height: 50px; border-radius: 50%;
            display: flex; justify-content: center; align-items: center; font-size: 1.5rem;
            box-shadow: 0 8px 20px rgba(37, 211, 102, 0.4); text-decoration: none;
        }
    </style>
</head>
<body>

    <!-- Header -->
    <div class="app-header">
        <!-- 4 Tap Custom Secret Trigger Embedded in Logo -->
        <div class="brand-title" id="navTitle" onclick="triggerSecretAdmin()">🏔️ Discover GB</div>
        <button class="lang-btn" onclick="toggleLanguage()" id="langBtn">English</button>
    </div>

    <!-- Hero -->
    <div class="hero-section">
        <h1 id="heroTitle">جی بی ٹورسٹ پورٹل</h1>
        <p id="heroSub">خوبصورت وادیوں کی ماڈرن ڈیجیٹل گائیڈ</p>
    </div>

    <div class="app-container">
        <!-- Google Login -->
        <div class="glass-card" style="text-align: center;">
            <p id="loginTxt" style="font-size: 0.9rem; margin-bottom: 12px; color: var(--text-sub);">گوگل کے ساتھ ایک کلک میں سائن ان کریں:</p>
            <button class="action-btn" style="background: #fff; color: #111;" onclick="googleAuth()" id="googleBtn">🌐 Google Sign In</button>
        </div>

        <!-- Quote Request Form -->
        <div class="glass-card" id="quote-section">
            <h2 id="quoteTitle" style="font-size: 1.2rem; margin-bottom: 15px; color: var(--accent-color);">مفت ٹور پلان حاصل کریں</h2>
            
            <label id="lblCity">شہر کا انتخاب کریں:</label>
            <select id="destCity">
                <option value="استور">استور (Astore)</option>
                <option value="گلگت">گلگت (Gilgit)</option>
                <option value="سکردو">سکردو (Skardu)</option>
                <option value="ہنزہ">ہنزہ (Hunza)</option>
                <option value="غذر">غذر (Ghizer)</option>
            </select>

            <label id="lblDate">روانگی کی تاریخ:</label>
            <input type="date" id="tourDate">

            <label id="lblMembers">مسافروں کی تعداد:</label>
            <select id="membersCount">
                <option value="1-2">1-2 افراد</option>
                <option value="3-5">3-5 افراد</option>
                <option value="6+">6 یا زیادہ افراد</option>
            </select>

            <button class="action-btn" onclick="sendQuoteRequest()" id="quoteBtnSubmit">درخواست جمع کریں</button>
        </div>

        <!-- Destination Post -->
        <div class="glass-card">
            <div class="dest-card">
                <img src="https://images.unsplash.com/photo-1548013146-72479768bada?q=80&w=600" alt="Astore Valley">
                <div class="dest-info">
                    <h3 id="cardTitle">وادی استور (Astore Valley)</h3>
                    <p id="cardDesc">راما جھیل اور دیوسائی کے خوبصورت راستوں کا گڑھ۔ نیلے پانیوں اور سرسبز میدانوں کی جنت۔</p>
                </div>
            </div>
        </div>

        <!-- Live Feedback System -->
        <div class="glass-card" id="reviews-section">
            <h2 id="revTitle" style="font-size: 1.1rem; margin-bottom: 10px; color: var(--accent-color);">سیاحوں کی رائے (Live)</h2>
            <input type="text" id="rName" placeholder="آپ کا نام">
            <textarea id="rMsg" rows="2" placeholder="اپنا سفری تجربہ لکھیں..."></textarea>
            <button class="action-btn" style="background: #10b981;" onclick="postReview()" id="revBtn">پوسٹ کریں</button>

            <div id="commentsBox" style="margin-top: 15px;"></div>
        </div>
    </div>

    <!-- SECRET ADMIN SYSTEM MODAL PANEL -->
    <div class="admin-modal" id="secretAdminPanel">
        <div class="admin-header">
            <h2 style="color:var(--accent-color);">🔐 سیکیور ایڈمن پینل</h2>
            <button onclick="closeAdminPanel()" style="background:crimson; color:white; border:none; padding:6px 12px; border-radius:8px; font-weight:bold; cursor:pointer;">بند کریں</button>
        </div>
        <h4 style="margin-bottom:15px; color:#10b981;">📋 کسٹمرز کی تمام درخواستیں (Everything Details):</h4>
        <div id="adminDataContainer">
            <p style="color:var(--text-sub);">ڈیٹا لوڈ ہو رہا ہے...</p>
        </div>
    </div>

    <!-- Bottom Dock -->
    <div class="bottom-dock">
        <a href="#" class="dock-tab active"><span class="dock-icon">🏠</span><span id="tabHome">ہوم</span></a>
        <a href="#quote-section" class="dock-tab"><span class="dock-icon">📅</span><span id="tabPlan">پلانر</span></a>
        <a href="https://wa.me/923332637235" target="_blank" class="float-wa">💬</a>
        <a href="#reviews-section" class="dock-tab"><span class="dock-icon">⭐</span><span id="tabRev">رائے</span></a>
    </div>

    <script>
        // فائر بیس کنفیگریشن
        const firebaseConfig = {
          apiKey: "AIzaSyBiti-Ih5nxvRQ8Xt9YImiN1X3RnPoXoTI",
          authDomain: "gilgit-79048.firebaseapp.com",
          databaseURL: "https://gilgit-79048-default-rtdb.firebaseio.com",
          projectId: "gilgit-79048",
          storageBucket: "gilgit-79048.firebasestorage.app",
          messagingSenderId: "784852692962",
          appId: "1:784852692962:web:eab87b313e024ebf7953bb"
        };

        firebase.initializeApp(firebaseConfig);
        const auth = firebase.auth();
        const database = firebase.database();

        let currentLang = "ur";
        let currentUserName = "انجان کسٹمر";
        let tapCount = 0;
        let tapTimeout;

        const dictionary = {
            ur: {
                dir: "rtl", langBtn: "English", navTitle: "🏔️ Discover GB",
                heroTitle: "جی بی ٹورسٹ پورٹل", heroSub: "خوبصورت وادیوں کی ماڈرن ڈیجیٹل گائیڈ",
                loginTxt: "گوگل کے ساتھ ایک کلک میں سائن ان کریں:", quoteTitle: "مفت ٹور پلان حاصل کریں",
                lblCity: "شہر کا انتخاب کریں:", lblDate: "روانگی کی تاریخ:", lblMembers: "مسافروں کی تعداد:",
                quoteBtnSubmit: "درخواست جمع کریں", cardTitle: "وادی استور (Astore Valley)",
                cardDesc: "راما جھیل اور دیوسائی کے خوبصورت راستوں کا گڑھ۔ نیلے پانیوں اور سرسبز میدانوں کی جنت۔",
                revTitle: "سیاحوں کی رائے (Live)", rName: "آپ کا نام", rMsg: "اپنا سفری تجربہ لکھیں...",
                revBtn: "پوسٹ کریں", tabHome: "ہوم", tabPlan: "پلانر", tabRev: "رائے"
            },
            en: {
                dir: "ltr", langBtn: "اردو", navTitle: "🏔️ Discover GB",
                heroTitle: "GB Tourist Portal", heroSub: "Modern Digital Guide to Celestial Valleys",
                loginTxt: "Sign in with Google in just one click:", quoteTitle: "Get a Free Tour Quote",
                lblCity: "Select Destination:", lblDate: "Departure Date:", lblMembers: "Number of Travelers:",
                quoteBtnSubmit: "Submit Request", cardTitle: "Astore Valley",
                cardDesc: "The hub of beautiful routes to Rama Lake and Deosai. A paradise of blue waters and lush green meadows.",
                revTitle: "Visitor Reviews (Live)", rName: "Your Name", rMsg: "Share your travel experience...",
                revBtn: "Post Review", tabHome: "Home", tabPlan: "Planner", tabRev: "Reviews"
            }
        };

        function toggleLanguage() {
            currentLang = currentLang === "ur" ? "en" : "ur";
            const data = dictionary[currentLang];
            document.getElementById("appHtml").setAttribute("dir", data.dir);
            document.getElementById("langBtn").innerText = data.langBtn;
            document.getElementById("navTitle").innerText = data.navTitle;
            document.getElementById("heroTitle").innerText = data.heroTitle;
            document.getElementById("heroSub").innerText = data.heroSub;
            document.getElementById("loginTxt").innerText = data.loginTxt;
            document.getElementById("quoteTitle").innerText = data.quoteTitle;
            document.getElementById("lblCity").innerText = data.lblCity;
            document.getElementById("lblDate").innerText = data.lblDate;
            document.getElementById("lblMembers").innerText = data.lblMembers;
            document.getElementById("quoteBtnSubmit").innerText = data.quoteBtnSubmit;
            document.getElementById("cardTitle").innerText = data.cardTitle;
            document.getElementById("cardDesc").innerText = data.cardDesc;
            document.getElementById("revTitle").innerText = data.revTitle;
            document.getElementById("rName").placeholder = data.rName;
            document.getElementById("rMsg").placeholder = data.rMsg;
            document.getElementById("revBtn").innerText = data.revBtn;
            document.getElementById("tabHome").innerText = data.tabHome;
            document.getElementById("tabPlan").innerText = data.tabPlan;
            document.getElementById("tabRev").innerText = data.tabRev;
        }

        // 🕵️‍♂️ SECRET 4-TAP LOGIC SYSTEM
        function triggerSecretAdmin() {
            tapCount++;
            clearTimeout(tapTimeout);
            
            // اگر یوزر 2 سیکنڈ تک دوبارہ ٹیپ نہیں کرتا تو کاؤنٹ زیرو ہو جائے گا
            tapTimeout = setTimeout(() => { tapCount = 0; }, 2000);

            if (tapCount === 4) {
                tapCount = 0; // ری سیٹ کریں
                let secretKey = prompt(currentLang === "ur" ? "خفیہ سیکیورٹی کوڈ درج کریں:" : "Enter Secret Admin Key:");
                
                if (secretKey === "5426") {
                    openAdminPanel();
                } else if (secretKey !== null) {
                    alert(currentLang === "ur" ? "غلط کوڈ! رسائی ممنوع ہے۔" : "Wrong Key! Access Denied.");
                }
            }
        }

        function openAdminPanel() {
            document.getElementById("secretAdminPanel").style.display = "block";
            loadAdminData();
        }

        function closeAdminPanel() {
            document.getElementById("secretAdminPanel").style.display = "none";
        }

        // ایڈمن کے لیے کسٹمر کا سارا ڈیٹا لائیو فیچ کرنا
        function loadAdminData() {
            const container = document.getElementById("adminDataContainer");
            container.innerHTML = "<p>فائر بیس سے کسٹمرز کا لائیو ڈیٹا نکل رہا ہے...</p>";

            database.ref('quotes').on('value', (snapshot) => {
                container.innerHTML = "";
                let data = snapshot.val();
                if(data) {
                    Object.keys(data).reverse().forEach((key) => {
                        let div = document.createElement('div');
                        div.className = "data-row";
                        let dateObj = new Date(data[key].time).toLocaleString('ur-PK');
                        div.innerHTML = `
                            <strong>👤 کسٹمر کا نام:</strong> ${data[key].user || "انجان کسٹمر"}<br>
                            <strong>🗺️ منزل (شہر):</strong> ${data[key].city}<br>
                            <strong>📅 ٹور کی تاریخ:</strong> ${data[key].date}<br>
                            <strong>👥 مسافروں کی تعداد:</strong> ${data[key].travelers}<br>
                            <span style="font-size:0.75rem; color:var(--text-sub);">⏰ آرڈر ٹائم: ${dateObj}</span>
                        `;
                        container.appendChild(div);
                    });
                } else {
                    container.innerHTML = "<p>فائر بیس پر فی الحال کوئی کوٹیشن موجود نہیں ہے۔</p>";
                }
            });
        }

        // گوگل لاگ ان
        function googleAuth() {
            const provider = new firebase.auth.GoogleAuthProvider();
            auth.signInWithPopup(provider).then((res) => {
                currentUserName = res.user.displayName;
                document.getElementById("rName").value = currentUserName;
                document.getElementById("rName").disabled = true;
                alert(currentLang === "ur" ? "لاگ ان کامیاب!" : "Login Successful!");
            });
        }

        // کوٹیشن ڈیٹا بیس میں بھیجیں
        function sendQuoteRequest() {
            let city = document.getElementById("destCity").value;
            let date = document.getElementById("tourDate").value;
            let members = document.getElementById("membersCount").value;

            if(!date) return alert(currentLang === "ur" ? "براہ کرم تاریخ منتخب کریں!" : "Please select a date!");

            database.ref('quotes').push({
                city: city, 
                date: date, 
                travelers: members, 
                user: currentUserName,
                time: Date.now()
            }).then(() => {
                alert(currentLang === "ur" ? "درخواست موصول ہو گئی۔ ہم جلد رابطہ کریں گے!" : "Request received. We will contact you soon!");
            });
        }

        // لائیو کمنٹس فائر بیس سے سننا
        database.ref('reviews').on('value', (snapshot) => {
            const box = document.getElementById("commentsBox");
            box.innerHTML = "";
            let data = snapshot.val();
            if(data) {
                Object.keys(data).reverse().forEach((key) => {
                    let div = document.createElement('div');
                    div.className = "review-item";
                    div.innerHTML = `<strong>${data[key].username}</strong>: <p style="color:var(--text-sub); margin-top:4px;">${data[key].message}</p>`;
                    box.appendChild(div);
                });
            }
        });

        function postReview() {
            let name = document.getElementById("rName").value;
            let msg = document.getElementById("rMsg").value;
            if(!name.trim() || !msg.trim()) return alert("Fill fields!");

            database.ref('reviews').push({
                username: name, message: msg, timestamp: Date.now()
            }).then(() => { document.getElementById("rMsg").value = ""; });
        }
    </script>
</body>
</html>
