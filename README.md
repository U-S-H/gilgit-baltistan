<html lang="ur" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>GB Tourist Portal | Prime Solutions</title>
    <script type="module">
        import { initializeApp } from "https://www.gstatic.com/firebasejs/10.8.0/firebase-app.js";
        import { getAuth, GoogleAuthProvider, signInWithPopup, signOut, onAuthStateChanged } from "https://www.gstatic.com/firebasejs/10.8.0/firebase-auth.js";
        import { getDatabase, ref, push, onValue, remove } from "https://www.gstatic.com/firebasejs/10.8.0/firebase-database.js";

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
        const auth = getAuth(app);
        const db = getDatabase(app);
        const provider = new GoogleAuthProvider();

        window.googleLogin = () => signInWithPopup(auth, provider);
        window.logout = () => signOut(auth).then(() => location.reload());

        window.saveBooking = () => {
            const city = document.getElementById('city').value;
            const phone = document.getElementById('phone').value;
            if(!phone) { alert("واٹس ایپ نمبر درج کریں!"); return; }
            push(ref(db, 'bookings/' + auth.currentUser.uid), { city, phone, status: "⏳ پینڈنگ" });
            alert("بکنگ موصول ہو گئی!");
        };

        window.openAdminPanel = () => {
            if (prompt("Admin Key:") === "5426") {
                document.getElementById('adminPanel').style.display = 'block';
                onValue(ref(db, 'bookings'), (snap) => {
                    let html = "";
                    snap.forEach(user => {
                        user.forEach(b => {
                            html += `<div class="card">📍 ${b.val().city} | 📱 ${b.val().phone} 
                            <button onclick="window.open('https://wa.me/${b.val().phone}')" style="background:#25D366; width:auto;">Quote بھیجیں</button>
                            <button onclick="remove(ref(db, 'bookings/${user.key}/${b.key}'))" style="background:red; width:auto;">❌</button></div>`;
                        });
                    });
                    document.getElementById('adminData').innerHTML = html;
                });
            }
        };

        onAuthStateChanged(auth, (user) => {
            if (user) {
                document.getElementById('authSection').style.display = 'none';
                document.getElementById('appSection').style.display = 'block';
                onValue(ref(db, 'bookings/' + user.uid), (snap) => {
                    let html = "";
                    snap.forEach(s => { html += `<div class="card">📍 ${s.val().city} - <b>${s.val().status}</b></div>`; });
                    document.getElementById('myBookings').innerHTML = html;
                });
            }
        });
    </script>
    <style>
        :root { --main: #00d4ff; --bg: #0f172a; --text: #ffffff; }
        body { background: var(--bg); color: var(--text); font-family: sans-serif; padding: 20px; }
        .glass { background: rgba(255,255,255,0.05); padding: 25px; border-radius: 20px; max-width: 500px; margin: auto; border: 1px solid rgba(255,255,255,0.1); }
        .card { background: #1e293b; padding: 15px; border-radius: 10px; margin: 10px 0; border-right: 4px solid var(--main); }
        button { padding: 12px; width: 100%; border-radius: 10px; border: none; cursor: pointer; background: var(--main); font-weight: bold; margin-top:10px; }
        input, select { width: 100%; padding: 12px; margin: 8px 0; border-radius: 10px; border: none; background: #1e293b; color: white; box-sizing: border-box; }
    </style>
</head>
<body>

<div id="authSection" class="glass" style="text-align:center;">
    <h1 onclick="openAdminPanel()">🏔️ GB Tourist Portal</h1>
    <button onclick="googleLogin()">Google سے لاگ ان کریں</button>
</div>

<div id="appSection" class="glass" style="display:none;">
    <h3>بکنگ فارم</h3>
    <input type="text" id="phone" placeholder="واٹس ایپ نمبر">
    <select id="city">
        <option value="استور">استور</option><option value="ہنزہ">ہنزہ</option>
        <option value="سکردو">سکردو</option><option value="دیوسائی">دیوسائی</option>
        <option value="فیری میڈوز">فیری میڈوز</option>
    </select>
    <button onclick="saveBooking()">بکنگ کنفرم کریں</button>
    <h4>میری بکنگز:</h4>
    <div id="myBookings"></div>
    <button onclick="logout()" style="background:#ef4444;">Logout</button>
</div>

<div id="adminPanel" class="glass" style="display:none; position:fixed; top:0; width:100%; z-index:999;">
    <h2>Admin Dashboard</h2>
    <div id="adminData"></div>
    <button onclick="document.getElementById('adminPanel').style.display='none'">بند کریں</button>
</div>

<a href="https://wa.me/923332637235" style="position:fixed; bottom:20px; right:20px; background:#25D366; padding:15px; border-radius:50px; text-decoration:none; color:white; font-weight:bold;">💬 WhatsApp</a>

</body>
</html>
