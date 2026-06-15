<html lang="ur" dir="rtl" id="appHtml">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Discover GB - Ultimate Portal</title>
    <script src="https://www.gstatic.com/firebasejs/10.8.0/firebase-app-compat.js"></script>
    <script src="https://www.gstatic.com/firebasejs/10.8.0/firebase-database-compat.js"></script>
    <style>
        :root { --accent: #38bdf8; --bg: #0f172a; }
        body { background: var(--bg); color: white; font-family: sans-serif; padding: 20px; }
        .card { background: rgba(255,255,255,0.05); padding: 20px; border-radius: 20px; margin-bottom: 20px; border: 1px solid rgba(255,255,255,0.1); }
        input, select { width: 100%; padding: 12px; margin: 8px 0; border-radius: 10px; border: none; }
        button { width: 100%; padding: 12px; background: var(--accent); border: none; border-radius: 10px; font-weight: bold; cursor: pointer; }
        .modal { display: none; position: fixed; top:0; left:0; width: 100%; height: 100%; background: rgba(0,0,0,0.95); padding: 20px; overflow-y: auto; z-index: 9999; }
        .data-item { background: #1e293b; padding: 15px; border-radius: 10px; margin-bottom: 10px; border-right: 5px solid var(--accent); }
    </style>
</head>
<body>

    <h2 onclick="triggerAdmin()" style="text-align: center; cursor: pointer;">🏔️ Discover GB</h2>
    <button onclick="toggleLang()" id="langBtn" style="width: auto; margin-bottom: 20px;">English</button>

    <div class="card">
        <h3 id="hTitle">مفت ٹور پلان حاصل کریں</h3>
        <input type="text" id="name" placeholder="آپ کا نام">
        <input type="text" id="contact" placeholder="واٹس ایپ نمبر یا ای میل">
        <select id="city">
            <option value="استور">استور</option>
            <option value="گلگت">گلگت</option>
            <option value="سکردو">سکردو</option>
        </select>
        <input type="date" id="date">
        <button onclick="submitData()">درخواست جمع کریں</button>
    </div>

    <!-- Receipt -->
    <div id="receipt" class="modal">
        <div class="card" style="text-align: center;">
            <h2>✅ رسید</h2>
            <div id="receiptBody" style="text-align: right;"></div>
            <button onclick="document.getElementById('receipt').style.display='none'">اوکے (Save Screenshot)</button>
        </div>
    </div>

    <!-- Admin Panel -->
    <div id="adminPanel" class="modal">
        <h2 style="color:var(--accent);">🔐 ایڈمن پینل (5426)</h2>
        <div id="adminData"></div>
        <button style="background:crimson;" onclick="document.getElementById('adminPanel').style.display='none'">بند کریں</button>
    </div>

    <script>
        const db = firebase.database();
        firebase.initializeApp({databaseURL: "https://gilgit-79048-default-rtdb.firebaseio.com"});
        
        let taps = 0;
        function triggerAdmin() {
            if(++taps === 4) {
                if(prompt("خفیہ کوڈ درج کریں:") === "5426") {
                    document.getElementById('adminPanel').style.display = 'block';
                    loadAdmin();
                }
                taps = 0;
            }
        }

        function submitData() {
            let data = { name: document.getElementById('name').value, contact: document.getElementById('contact').value, city: document.getElementById('city').value, date: document.getElementById('date').value };
            db.ref('quotes').push(data);
            document.getElementById('receiptBody').innerHTML = `نام: ${data.name}<br>رابطہ: ${data.contact}<br>شہر: ${data.city}<br>تاریخ: ${data.date}`;
            document.getElementById('receipt').style.display = 'block';
        }

        function loadAdmin() {
            db.ref('quotes').on('value', snap => {
                let html = "";
                snap.forEach(s => { let v = s.val(); html += `<div class="data-item">👤 ${v.name}<br>📞 ${v.contact}<br>🗺️ ${v.city}<br>📅 ${v.date}</div>`; });
                document.getElementById('adminData').innerHTML = html;
            });
        }

        function toggleLang() {
            let btn = document.getElementById('langBtn');
            let t = document.getElementById('hTitle');
            if(btn.innerText === "English") {
                btn.innerText = "اردو";
                t.innerText = "Get Free Tour Plan";
            } else {
                btn.innerText = "English";
                t.innerText = "مفت ٹور پلان حاصل کریں";
            }
        }
    </script>
</body>
</html>
