<html lang="ur" dir="rtl" id="appTheme">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>GB Tourist Information Hub | Prime Solutions</title>
    <script src="https://www.gstatic.com/firebasejs/10.8.0/firebase-app-compat.js"></script>
    <script src="https://www.gstatic.com/firebasejs/10.8.0/firebase-database-compat.js"></script>
    <style>
        :root { --main: #00d4ff; --bg: #0f172a; --card: rgba(255,255,255,0.05); }
        body { background: var(--bg); color: #fff; font-family: sans-serif; padding: 20px; }
        .box { background: var(--card); padding: 20px; border-radius: 20px; margin-bottom: 20px; backdrop-filter: blur(10px); }
        .data-card { background: #1e293b; padding: 15px; border-radius: 15px; margin-bottom: 10px; border-right: 5px solid var(--main); display: flex; justify-content: space-between; align-items: center; }
        input, select { width: 100%; padding: 12px; margin: 8px 0; border-radius: 10px; border: none; background: rgba(0,0,0,0.2); color: white; }
        button { padding: 12px; background: var(--main); border: none; border-radius: 10px; font-weight: bold; cursor: pointer; color: black; }
        .modal { display: none; position: fixed; top:0; left:0; width: 100%; height: 100%; background: #000; padding: 20px; overflow-y: auto; z-index: 9999; }
    </style>
</head>
<body>

    <h1 onclick="taps++" style="text-align:center; cursor:pointer;">🏔️ GB Tourist Information Hub</h1>

    <div class="box">
        <h3>ٹور معلومات حاصل کریں</h3>
        <input type="text" id="name" placeholder="آپ کا نام">
        <select id="city">
            <option value="استور">استور</option><option value="ہنزہ">ہنزہ</option><option value="سکردو">سکردو</option>
            <option value="گلگت">گلگت</option><option value="فیری میڈوز">فیری میڈوز</option><option value="دیوسائی">دیوسائی</option>
        </select>
        <button onclick="bookNow()" style="width:100%;">واٹس ایپ پر رابطہ کریں 💬</button>
    </div>

    <!-- Admin Panel -->
    <div id="adminPanel" class="modal">
        <div style="max-width:600px; margin:auto;">
            <h2 style="color:var(--main);">🔐 ایڈمن پینل</h2>
            <button onclick="clearAllData()" style="background:red; color:white; width:100%; margin-bottom:20px;">تمام ڈیٹا ڈیلیٹ کریں (Clear All)</button>
            <div id="adminData"></div>
            <button onclick="document.getElementById('adminPanel').style.display='none'" style="width:100%; margin-top:20px;">بند کریں</button>
        </div>
    </div>

    <script>
        firebase.initializeApp({databaseURL: "https://gilgit-79048-default-rtdb.firebaseio.com"});
        const db = firebase.database();

        function bookNow() {
            let n = document.getElementById('name').value;
            let c = document.getElementById('city').value;
            db.ref('quotes').push({ name: n, city: c, time: Date.now() });
            window.open(`https://wa.me/923332637235?text=ہیلو، میرا نام ${n} ہے اور میں ${c} کے لیے معلومات چاہتا ہوں۔`, '_blank');
        }

        // Secret Trigger
        let taps = 0;
        document.querySelector('h1').onclick = () => {
            if(++taps === 4) {
                if(prompt("Admin Key:") === "5426") {
                    document.getElementById('adminPanel').style.display = 'block';
                    loadData();
                }
                taps = 0;
            }
        }

        function loadData() {
            db.ref('quotes').on('value', snap => {
                let html = "";
                snap.forEach(s => {
                    let v = s.val();
                    html += `<div class="data-card">
                                <div>👤 ${v.name} <br> 🗺️ ${v.city}</div>
                                <button onclick="deleteItem('${s.key}')" style="background:red; color:white; padding:5px 10px;">❌</button>
                             </div>`;
                });
                document.getElementById('adminData').innerHTML = html;
            });
        }

        function deleteItem(key) { db.ref('quotes/'+key).remove(); }
        function clearAllData() { if(confirm("کیا آپ سارا ڈیٹا ڈیلیٹ کرنا چاہتے ہیں؟")) db.ref('quotes').remove(); }
    </script>
</body>
</html>
