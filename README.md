<html lang="ur" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Discover GB - Pro Portal</title>
    <!-- Firebase SDKs -->
    <script src="https://www.gstatic.com/firebasejs/10.8.0/firebase-app-compat.js"></script>
    <script src="https://www.gstatic.com/firebasejs/10.8.0/firebase-auth-compat.js"></script>
    <script src="https://www.gstatic.com/firebasejs/10.8.0/firebase-database-compat.js"></script>
    
    <style>
        /* CSS (پروفیشنل لک کے لیے) */
        body { font-family: sans-serif; background: #f8fafc; margin: 0; padding-bottom: 70px; }
        .loader { position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: white; z-index: 9999; display: flex; justify-content: center; align-items: center; }
        .card { background: white; padding: 20px; border-radius: 15px; margin: 15px; box-shadow: 0 4px 6px rgba(0,0,0,0.05); }
        select, input, textarea { width: 100%; padding: 12px; margin: 8px 0; border: 1px solid #ddd; border-radius: 8px; }
        button { background: #1e3a8a; color: white; padding: 12px; border: none; border-radius: 8px; width: 100%; cursor: pointer; }
    </style>
</head>
<body>

    <!-- Professional Loader -->
    <div class="loader" id="loader">🔄 سسٹم لوڈ ہو رہا ہے...</div>

    <div class="card">
        <h2 id="userName">خوش آمدید!</h2>
        <button id="loginBtn" onclick="googleLogin()">Google سے لاگ ان کریں</button>
    </div>

    <div class="card">
        <h3>ٹور کوٹیشن (Free Quote)</h3>
        <select id="citySelect">
            <option>اپنا شہر منتخب کریں</option>
            <option>گلگت</option><option>سکردو</option><option>ہنزہ</option>
            <option>غذر</option><option>دیامر</option><option>استور</option>
            <option>گانچھے</option><option>شگر</option><option>کھرمنگ</option>
        </select>
        <textarea id="quoteDetails" placeholder="اپنے ٹور کی تفصیلات بتائیں..."></textarea>
        <button onclick="requestQuote()">کوٹیشن حاصل کریں</button>
    </div>

    <div class="card">
        <h3>کمپنی اور پرائیویسی</h3>
        <button onclick="loadContent('privacy')">پرائیویسی پالیسی</button>
        <div id="dynamicContent" style="margin-top:15px; font-size:0.9rem; color:#555;"></div>
    </div>

    <script>
        // Firebase Config (آپ کی وہی پرانی والی)
        const firebaseConfig = { /* ... اپنی کنفیگ یہاں دوبارہ ڈالیں ... */ };
        firebase.initializeApp(firebaseConfig);

        // 1. Loader Logic
        window.onload = () => { setTimeout(() => document.getElementById('loader').style.display = 'none', 1000); };

        // 2. Google Login
        function googleLogin() {
            const provider = new firebase.auth.GoogleAuthProvider();
            firebase.auth().signInWithPopup(provider).then(res => {
                document.getElementById('userName').innerText = "خوش آمدید، " + res.user.displayName;
            });
        }

        // 3. Dynamic Content Loader (Professional Feel)
        function loadContent(type) {
            document.getElementById('dynamicContent').innerHTML = "لوڈ ہو رہا ہے...";
            setTimeout(() => {
                if(type === 'privacy') {
                    document.getElementById('dynamicContent').innerHTML = "ہم آپ کا ڈیٹا محفوظ رکھتے ہیں۔ یہ ایک پروفیشنل ٹورسٹ پورٹل ہے۔";
                }
            }, 800);
        }

        // 4. Quote Request (No Direct Price)
        function requestQuote() {
            alert("آپ کی درخواست موصول ہوگئی! ہم جلد آپ سے رابطہ کریں گے۔");
        }
    </script>
</body>
</html>
