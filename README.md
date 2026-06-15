<html lang="ur">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>Discover GB - Pro Tourist Hub</title>
    
    <!-- Firebase Compatibility SDKs -->
    <script src="https://www.gstatic.com/firebasejs/10.8.0/firebase-app-compat.js"></script>
    <script src="https://www.gstatic.com/firebasejs/10.8.0/firebase-auth-compat.js"></script>
    <script src="https://www.gstatic.com/firebasejs/10.8.0/firebase-database-compat.js"></script>
    
    <style>
        /* Base & Reset Styles */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;
            -webkit-tap-highlight-color: transparent;
        }

        body {
            background-color: #f1f5f9;
            color: #1e293b;
            padding-bottom: 80px; 
            direction: rtl; 
        }

        /* Professional Full Screen Loader */
        .app-loader {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: #ffffff;
            z-index: 9999;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            font-weight: bold;
            color: #1e3a8a;
            font-size: 1.2rem;
            transition: opacity 0.5s ease, visibility 0.5s;
        }
        .spinner {
            border: 4px solid #f3f3f3;
            border-top: 4px solid #1e3a8a;
            border-radius: 50%;
            width: 40px;
            height: 40px;
            animation: spin 1s linear infinite;
            margin-bottom: 15px;
        }
        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }

        /* App Top Header */
        .app-header {
            background-color: #1e3a8a;
            color: white;
            padding: 15px;
            text-align: center;
            font-size: 1.2rem;
            font-weight: bold;
            position: sticky;
            top: 0;
            z-index: 1000;
            box-shadow: 0 2px 8px rgba(0,0,0,0.1);
        }

        /* Hero App Banner */
        .app-banner {
            background: linear-gradient(rgba(30, 58, 138, 0.6), rgba(30, 58, 138, 0.8)), url('https://images.unsplash.com/photo-1548013146-72479768bada?q=80&w=600') no-repeat center center/cover;
            height: 180px;
            color: white;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
            padding: 20px;
            margin-bottom: 15px;
        }

        .app-banner h2 { font-size: 1.6rem; margin-bottom: 5px; }
        .app-banner p { font-size: 0.85rem; opacity: 0.9; }

        .app-container { padding: 0 15px; }

        /* Google Login Component */
        .login-card {
            background: white;
            border-radius: 12px;
            padding: 15px;
            text-align: center;
            box-shadow: 0 2px 8px rgba(0,0,0,0.04);
            margin-bottom: 20px;
        }
        .login-profile { display: flex; align-items: center; gap: 10px; justify-content: center; }
        .login-profile img { width: 40px; height: 40px; border-radius: 50%; }
        .google-btn {
            background-color: #fff;
            color: #757575;
            border: 1px solid #ddd;
            padding: 10px 15px;
            border-radius: 8px;
            font-weight: bold;
            display: inline-flex;
            align-items: center;
            gap: 10px;
            cursor: pointer;
            box-shadow: 0 2px 4px rgba(0,0,0,0.05);
        }

        /* Form Components */
        .app-card-form {
            background: white;
            border-radius: 12px;
            padding: 15px;
            box-shadow: 0 2px 8px rgba(0,0,0,0.04);
            margin-bottom: 25px;
        }
        .form-group { margin-bottom: 12px; }
        .form-group label { font-size: 0.9rem; font-weight: bold; color: #475569; display: block; margin-bottom: 5px; }
        select, input, textarea {
            width: 100%;
            padding: 12px;
            border: 1px solid #cbd5e1;
            border-radius: 8px;
            outline: none;
            font-size: 0.95rem;
            background: #f8fafc;
        }
        .app-btn {
            background-color: #1e3a8a;
            color: white;
            border: none;
            padding: 12px;
            border-radius: 8px;
            font-weight: bold;
            font-size: 1rem;
            width: 100%;
            cursor: pointer;
        }

        /* Section Title */
        .section-title {
            font-size: 1.1rem;
            color: #0f172a;
            margin-bottom: 12px;
            border-right: 4px solid #2563eb;
            padding-right: 8px;
        }

        /* Destinations Grid */
        .card-stack { display: flex; flex-direction: column; gap: 15px; margin-bottom: 25px; }
        .app-card { background: white; border-radius: 12px; overflow: hidden; box-shadow: 0 2px 8px rgba(0,0,0,0.04); }
        .app-card img { width: 100%; height: 150px; object-fit: cover; }
        .app-card-content { padding: 12px; }
        .app-card-content h4 { color: #1e3a8a; font-size: 1rem; margin-bottom: 4px; }
        .app-card-content p { font-size: 0.85rem; color: #64748b; }

        /* Inline Page/Content Loader (Privacy Policy & Company Details) */
        .sub-page-section {
            background: white;
            border-radius: 12px;
            padding: 15px;
            box-shadow: 0 2px 8px rgba(0,0,0,0.04);
            margin-bottom: 25px;
        }
        .tab-btn-container { display: flex; gap: 10px; margin-bottom: 12px; }
        .tab-btn {
            flex: 1;
            padding: 8px;
            background: #e2e8f0;
            border: none;
            border-radius: 6px;
            font-size: 0.85rem;
            font-weight: bold;
            color: #475569;
            cursor: pointer;
        }
        .tab-btn.active { background: #1e3a8a; color: white; }
        .dynamic-content-area {
            min-height: 60px;
            font-size: 0.9rem;
            color: #475569;
            position: relative;
        }
        .inline-loader {
            display: none;
            text-align: center;
            color: #2563eb;
            font-weight: bold;
            padding: 10px 0;
        }

        /* Bottom Navigation Dock */
        .bottom-nav {
            position: fixed;
            bottom: 0; left: 0; right: 0;
            height: 65px;
            background: white;
            display: flex;
            justify-content: space-around;
            align-items: center;
            box-shadow: 0 -2px 10px rgba(0,0,0,0.08);
            z-index: 2000;
        }
        .nav-tab {
            display: flex; flex-direction: column; align-items: center;
            color: #64748b; text-decoration: none; font-size: 0.75rem; font-weight: bold; width: 20%;
        }
        .nav-tab.active { color: #2563eb; }
        .nav-tab .tab-icon { font-size: 1.3rem; margin-bottom: 2px; }
        .whatsapp-float-btn {
            background-color: #25D366; color: white; width: 48px; height: 48px; border-radius: 50%;
            display: flex; justify-content: center; align-items: center; font-size: 1.4rem;
            box-shadow: 0 4px 10px rgba(0,0,0,0.15); text-decoration: none;
        }
    </style>
</head>
<body>

    <!-- Professional App Loader Component -->
    <div class="app-loader" id="mainLoader">
        <div class="spinner"></div>
        <span>سسٹم لوڈ ہو رہا ہے...</span>
    </div>

    <!-- App Header -->
    <div class="app-header">🏔️ Discover Gilgit-Baltistan</div>

    <!-- App Banner -->
    <div class="app-banner" id="home-view">
        <h2>جی بی ٹورسٹ پورٹل</h2>
        <p>موبائل فرینڈلی سمارٹ ٹریول ڈائریکٹری</p>
    </div>

    <div class="app-container">

        <!-- 1. Google Auth Component -->
        <div class="login-card">
            <div id="authContent">
                <p style="font-size: 0.9rem; margin-bottom: 10px; color: #64748b;">بہتر تجربے اور لائیو فیڈ بیک کے لیے لاگ ان کریں:</p>
                <button class="google-btn" onclick="handleGoogleLogin()">
                    🌐 Google کے ساتھ سائن ان کریں
                </button>
            </div>
        </div>

        <!-- 2. Smart Free Quote Selector Form (No Direct Prices) -->
        <h3 class="section-title" id="quote-view">مفت ٹور کوٹیشن حاصل کریں</h3>
        <div class="app-card-form">
            <div class="form-group">
                <label>آپ گلگت بلتستان کے کس شہر جانا چاہتے ہیں؟</label>
                <select id="tourCity">
                    <option value="">-- شہر منتخب کریں --</option>
                    <option value="استور">استور (Astore)</option>
                    <option value="گلگت">گلگت (Gilgit)</option>
                    <option value="سکردو">سکردو (Skardu)</option>
                    <option value="ہنزہ">ہنزہ (Hunza)</option>
                    <option value="غذر">غذر (Ghizer)</option>
                    <option value="دیامر">دیامر (Diamer)</option>
                    <option value="شگر">شگر (Shigar)</option>
                    <option value="کھرمنگ">کھرمنگ (Kharmang)</option>
                    <option value="گانچھے">گانچھے (Ghanche)</option>
                    <option value="نگر">نگر (Nagar)</option>
                </select>
            </div>
            <div class="form-group">
                <label>گاڑی / سروس کی نوعیت</label>
                <select id="vehicleType">
                    <option value="Prado / Jeep 4x4">Prado / Jeep 4x4</option>
                    <option value="Hiace Grand Cabin">Hiace Grand Cabin</option>
                    <option value="صرف لوکل ٹور گائیڈ">صرف لوکل ٹور گائیڈ</option>
                </select>
            </div>
            <div class="form-group">
                <label>اضافی تفصیلات (دنوں کی تعداد وغیرہ)</label>
                <textarea id="quoteNotes" rows="2" placeholder="مثال کے طور پر: 5 دن کا ٹور پلان ہے..."></textarea>
            </div>
            <button class="app-btn" onclick="submitQuoteRequest()">کوٹیشن کی درخواست بھیجیں</button>
        </div>

        <!-- Destinations Display -->
        <h3 class="section-title">مشہور سیاحتی مقامات</h3>
        <div class="card-stack">
            <div class="app-card">
                <img src="https://images.unsplash.com/photo-1627483262769-04d0a1401487?q=80&w=600" alt="Hunza">
                <div class="app-card-content">
                    <h4>ہنزہ اور عطا آباد (Hunza Valley)</h4>
                    <p>خوبصورت جھیلیں اور تاریخی قلعے دیکھنے کے لیے بہترین انتخاب۔</p>
                </div>
            </div>
        </div>

        <!-- 3. Professional In-App Content Loader (Company Info & Privacy) -->
        <h3 class="section-title" id="info-view">کمپنی اور قانونی معلومات</h3>
        <div class="sub-page-section">
            <div class="tab-btn-container">
                <button class="tab-btn active" id="btnCompany" onclick="switchTab('company')">کمپنی کی تفصیلات</button>
                <button class="tab-btn" id="btnPrivacy" onclick="switchTab('privacy')">پرائیویسی پالیسی</button>
            </div>
            <div class="dynamic-content-area">
                <div class="inline-loader" id="inlineLoader">🔄 معلومات لوڈ ہو رہی ہیں...</div>
                <div id="tabContentBody">
                    Discover Gilgit-Baltistan ایک رجسٹرڈ مقامی ٹریول گائیڈ نیٹ ورک ہے جو سیاحوں کو محفوظ اور سستی سفری سہولیات فراہم کرتا ہے۔
                </div>
            </div>
        </div>

        <!-- Live Firebase Reviews Component -->
        <h3 class="section-title" id="reviews-view">سیاحوں کے لائیو ریویوز</h3>
        <div class="app-card-form">
            <input type="text" id="fbUserName" placeholder="آپ کا نام (یا لاگ ان کریں)" style="margin-bottom:8px;">
            <textarea id="fbUserMsg" rows="2" placeholder="اپنا سفری تجربہ شیئر کریں..." style="margin-bottom:10px;"></textarea>
            <button class="app-btn" style="background:#10b981;" onclick="sendFirebaseReview()">ریویو پوسٹ کریں</button>
            
            <div id="liveReviewsBox" style="margin-top:15px; max-height:200px; overflow-y:auto;">
                <p style="text-align:center; color:#64748b; font-size:0.85rem;" id="dbStatus">لوڈنگ رائیڈز...</p>
            </div>
        </div>

    </div>

    <!-- App Bottom Dock Navigation -->
    <div class="bottom-nav">
        <a href="#home-view" class="nav-tab active" onclick="setActiveNav(this)">
            <span class="tab-icon">🏠</span><span>ہوم</span>
        </a>
        <a href="#quote-view" class="nav-tab" onclick="setActiveNav(this)">
            <span class="tab-icon">📝</span><span>کوٹیشن</span>
        </a>
        
        <!-- Center Floating Call Action -->
        <a href="https://wa.me/923332637235" target="_blank" class="whatsapp-float-btn">💬</a>

        <a href="#reviews-view" class="nav-tab" onclick="setActiveNav(this)">
            <span class="tab-icon">⭐</span><span>ریویوز</span>
        </a>
        <a href="#info-view" class="nav-tab" onclick="setActiveNav(this)">
            <span class="tab-icon">ℹ️</span><span>معلومات</span>
        </a>
    </div>

    <!-- Firebase System & App Automation Scripts -->
    <script>
        // فائر بیس کنفیگریشن
        const firebaseConfig = {
          apiKey: "AIzaSyBiti-Ih5nxvRQ8Xt9YImiN1X3RnPoXoTI",
          authDomain: "gilgit-79048.firebaseapp.com",
          databaseURL: "https://gilgit-79048-default-rtdb.firebaseio.com",
          projectId: "gitgit-79048",
          storageBucket: "gilgit-79048.firebasestorage.app",
          messagingSenderId: "784852692962",
          appId: "1:784852692962:web:eab87b313e024ebf7953bb"
        };

        // فائر بیس کو انیشیلائز کریں
        firebase.initializeApp(firebaseConfig);
        const auth = firebase.auth();
        const database = firebase.database();

        let currentLoggedInUser = null;

        // 1. پرو لوڈر اینیمیشن لاجک
        window.addEventListener('DOMContentLoaded', () => {
            setTimeout(() => {
                const loader = document.getElementById('mainLoader');
                loader.style.opacity = '0';
                setTimeout(() => loader.style.visibility = 'hidden', 500);
            }, 1200);
        });

        // 2. گوگل لاگ ان اور سائن اپ سسٹم
        function handleGoogleLogin() {
            const provider = new firebase.auth.GoogleAuthProvider();
            auth.signInWithPopup(provider).then((result) => {
                currentLoggedInUser = result.user;
                updateAuthUI(currentLoggedInUser);
            }).catch((error) => {
                alert("گوگل سائن ان ناکام ہوا: " + error.message);
            });
        }

        function updateAuthUI(user) {
            const container = document.getElementById('authContent');
            if(user) {
                document.getElementById('fbUserName').value = user.displayName;
                document.getElementById('fbUserName').disabled = true;
                container.innerHTML = `
                    <div class="login-profile">
                        <img src="${user.photoURL || 'https://via.placeholder.com/40'}" alt="User Profile">
                        <div style="text-align:right;">
                            <strong style="font-size:0.9rem; display:block;">${user.displayName}</strong>
                            <span style="color:#10b981; font-size:0.75rem; font-weight:bold;">🟢 لاگ ان ہو چکے ہیں</span>
                        </div>
                    </div>
                `;
            }
        }

        // 3. لائیو ریویوز لوڈنگ اور سینڈنگ (Firebase Realtime DB)
        database.ref('reviews').on('value', (snapshot) => {
            const box = document.getElementById('liveReviewsBox');
            box.innerHTML = "";
            let data = snapshot.val();
            if(data) {
                Object.keys(data).reverse().forEach((key) => {
                    let div = document.createElement('div');
                    div.style.cssText = "background:#f8fafc; padding:10px; border-radius:8px; margin-bottom:8px; font-size:0.85rem; border-right:3px solid #10b981;";
                    div.innerHTML = `<strong>${data[key].username}:</strong> <p style="color:#475569; margin-top:2px;">${data[key].message}</p>`;
                    box.appendChild(div);
                });
            } else {
                box.innerHTML = `<p style="text-align:center; color:#64748b; font-size:0.8rem;">کوئی ریویو موجود نہیں ہے۔</p>`;
            }
        });

        function sendFirebaseReview() {
            let name = document.getElementById('fbUserName').value;
            let msg = document.getElementById('fbUserMsg').value;
            if(!name.trim() || !msg.trim()) { return alert("براہ کرم نام اور کمنٹ درج کریں!"); }

            database.ref('reviews').push({
                username: name,
                message: msg,
                timestamp: Date.now()
            }).then(() => {
                document.getElementById('fbUserMsg').value = "";
            });
        }

        // 4. فری کوٹیشن فارم ڈیٹا ہینڈلر
        function submitQuoteRequest() {
            let city = document.getElementById('tourCity').value;
            let vehicle = document.getElementById('vehicleType').value;
            let notes = document.getElementById('quoteNotes').value;

            if(!city) { return alert("براہ کرم کسی شہر کا انتخاب کریں!"); }

            // ڈیٹا بیس میں کوٹیشن کی تفصیلات محفوظ کرنا
            database.ref('quotes').push({
                selectedCity: city,
                serviceRequested: vehicle,
                additionalNotes: notes,
                user: currentLoggedInUser ? currentLoggedInUser.displayName : "انجان کسٹمر",
                time: Date.now()
            }).then(() => {
                alert(`شکریہ! آپ کی ${city} کے لیے کوٹیشن کی درخواست موصول ہو گئی ہے۔ ہم جلد آپ سے واٹس ایپ پر رابطہ کریں گے۔`);
                document.getElementById('quoteNotes').value = "";
            });
        }

        // 5. ان-ایپ سب پیجز لوڈنگ سسٹم (Professional Tab Switcher)
        function switchTab(type) {
            const body = document.getElementById('tabContentBody');
            const inlineLoader = document.getElementById('inlineLoader');
            const btnComp = document.getElementById('btnCompany');
            const btnPriv = document.getElementById('btnPrivacy');

            body.style.display = 'none';
            inlineLoader.style.display = 'block';

            if(type === 'company') {
                btnComp.classList.add('active');
                btnPriv.classList.remove('active');
            } else {
                btnPriv.classList.add('active');
                btnComp.classList.remove('active');
            }

            setTimeout(() => {
                inlineLoader.style.display = 'none';
                body.style.display = 'block';
                if(type === 'company') {
                    body.innerHTML = "Discover Gilgit-Baltistan ایک رجسٹرڈ مقامی ٹریول گائیڈ نیٹ ورک ہے جو سیاحوں کو محفوظ اور سستی سفری سہولیات فراہم کرتا ہے۔";
                } else {
                    body.innerHTML = "پرائیویسی پالیسی: ہم آپ کی فراہم کردہ معلومات (جیسے نام یا کوٹیشن کی تفصیلات) کو صرف ٹور مینیجمنٹ کے لیے استعمال کرتے ہیں اور اسے کسی تیسری پارٹی سے شیئر نہیں کیا جاتا۔";
                }
            }, 600); // 600ms کا کلاسی ان-ایپ لوڈنگ ویٹ فیل
        }

        // نیویگیشن ٹیب چینجر لاجک
        function setActiveNav(element) {
            let tabs = document.getElementsByClassName('nav-tab');
            for(let i=0; i<tabs.length; i++) { tabs[i].classList.remove('active'); }
            element.classList.add('active');
        }
    </script>
</body>
</html>
