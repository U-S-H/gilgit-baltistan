<html lang="ur">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Discover Gilgit-Baltistan - Ultimate Tourist Information Hub</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background-color: #f7fafc;
            color: #2d3748;
            line-height: 1.7;
        }

        /* Top Bar */
        .top-bar {
            background-color: #2b6cb0;
            color: white;
            text-align: center;
            padding: 8px 10px;
            font-size: 0.9rem;
            font-weight: 500;
        }

        /* Header Styling */
        header {
            background: linear-gradient(rgba(26, 54, 93, 0.75), rgba(43, 108, 176, 0.75)), url('https://images.unsplash.com/photo-1548013146-72479768bada?q=80&w=1200') no-repeat center center/cover;
            height: 65vh;
            color: white;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
            padding: 20px;
        }

        header h1 {
            font-size: 3.5rem;
            margin-bottom: 15px;
            text-shadow: 3px 3px 6px rgba(0,0,0,0.6);
        }

        header p {
            font-size: 1.3rem;
            max-width: 700px;
            text-shadow: 1px 1px 4px rgba(0,0,0,0.5);
            margin-bottom: 25px;
        }

        /* Search Bar Box */
        .search-container {
            width: 100%;
            max-width: 500px;
            position: relative;
        }

        .search-container input {
            width: 100%;
            padding: 15px 25px;
            border: none;
            border-radius: 50px;
            font-size: 1.1rem;
            box-shadow: 0 4px 15px rgba(0,0,0,0.2);
            outline: none;
        }

        /* Navigation Bar */
        nav {
            background-color: #1a365d;
            display: flex;
            justify-content: center;
            flex-wrap: wrap;
            padding: 15px 0;
            position: sticky;
            top: 0;
            z-index: 1000;
            box-shadow: 0 4px 6px rgba(0,0,0,0.1);
        }

        nav a {
            color: white;
            text-decoration: none;
            margin: 5px 20px;
            font-size: 1.1rem;
            font-weight: 600;
            transition: color 0.3s;
        }

        nav a:hover {
            color: #4299e1;
        }

        /* Main Content Container */
        .container {
            max-width: 1200px;
            margin: 50px auto;
            padding: 0 20px;
        }

        .section-title {
            text-align: center;
            margin-bottom: 40px;
            color: #1a365d;
            font-size: 2.2rem;
            position: relative;
            padding-bottom: 10px;
        }

        .section-title::after {
            content: '';
            width: 80px;
            height: 4px;
            background-color: #3182ce;
            position: absolute;
            bottom: 0;
            left: 50%;
            transform: translateX(-50%);
            border-radius: 2px;
        }

        /* Destinations Grid */
        .grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
            gap: 35px;
            margin-bottom: 60px;
        }

        .card {
            background: white;
            border-radius: 12px;
            overflow: hidden;
            box-shadow: 0 10px 20px rgba(0,0,0,0.05);
            transition: transform 0.3s, box-shadow 0.3s;
        }

        .card:hover {
            transform: translateY(-8px);
            box-shadow: 0 15px 30px rgba(0,0,0,0.12);
        }

        .card img {
            width: 100%;
            height: 230px;
            object-fit: cover;
        }

        .card-content {
            padding: 25px;
        }

        .card-content h3 {
            margin-bottom: 12px;
            color: #2b6cb0;
            font-size: 1.4rem;
        }

        .card-content p {
            font-size: 1rem;
            color: #4a5568;
        }

        /* Directory & Tables */
        .directory-section {
            background: white;
            padding: 35px;
            border-radius: 12px;
            box-shadow: 0 10px 20px rgba(0,0,0,0.05);
            margin-bottom: 60px;
        }

        table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 20px;
            font-size: 1rem;
        }

        th, td {
            text-align: center;
            padding: 12px 15px;
            border-bottom: 1px solid #e2e8f0;
        }

        th {
            background-color: #ebf8ff;
            color: #2b6cb0;
            font-weight: 700;
        }

        tr:hover {
            background-color: #f7fafc;
        }

        /* Info & Advisory Boxes */
        .flex-info {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(450px, 1fr));
            gap: 30px;
            margin-bottom: 60px;
        }

        .info-box {
            background-color: #ebf8ff;
            border-right: 5px solid #3182ce;
            padding: 30px;
            border-radius: 8px;
        }

        .alert-box {
            background-color: #fffaf0;
            border-right: 5px solid #dd6b20;
            padding: 30px;
            border-radius: 8px;
        }

        .info-box h3, .alert-box h3 {
            margin-bottom: 15px;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        /* Reviews Section */
        .reviews-section {
            background: white;
            padding: 35px;
            border-radius: 12px;
            box-shadow: 0 10px 20px rgba(0,0,0,0.05);
            margin-bottom: 40px;
        }

        .review-form input, .review-form textarea {
            width: 100%;
            padding: 12px;
            margin-bottom: 15px;
            border: 1px solid #cbd5e0;
            border-radius: 6px;
            outline: none;
        }

        .review-form button {
            background-color: #1a365d;
            color: white;
            border: none;
            padding: 12px 25px;
            font-weight: bold;
            border-radius: 6px;
            cursor: pointer;
            transition: background 0.3s;
        }

        .review-form button:hover {
            background-color: #2b6cb0;
        }

        .reviews-list {
            margin-top: 30px;
            border-top: 1px solid #e2e8f0;
            padding-top: 20px;
        }

        .user-comment {
            background: #f7fafc;
            padding: 15px;
            border-radius: 6px;
            margin-bottom: 15px;
        }

        /* Floating WhatsApp Button */
        .whatsapp-float {
            position: fixed;
            bottom: 30px;
            right: 30px;
            background-color: #25D366;
            color: white;
            width: 60px;
            height: 60px;
            border-radius: 50px;
            display: flex;
            justify-content: center;
            align-items: center;
            box-shadow: 0 4px 12px rgba(0,0,0,0.3);
            z-index: 2000;
            text-decoration: none;
            font-size: 1.8rem;
            transition: transform 0.3s;
        }

        .whatsapp-float:hover {
            transform: scale(1.1);
            background-color: #1ebd58;
        }

        /* Footer */
        footer {
            background-color: #1a365d;
            color: white;
            text-align: center;
            padding: 25px 0;
            font-size: 0.95rem;
        }
    </style>
</head>
<body>

    <!-- Top Info Bar -->
    <div class="top-bar">✨ گلگت بلتستان ٹورازم ہیلپ لائن اور گائیڈ پورٹل میں خوش آمدید!</div>

    <!-- Header Section -->
    <header>
        <h1>Discover Gilgit-Baltistan</h1>
        <p>جنت نظیر وادیوں، فلک بوس پہاڑوں اور خوبصورت ثقافت کی سرزمین میں آپ کا استقبال ہے۔ اپنی اگلی ویکیشن پلان کریں۔</p>
        
        <!-- Feature 1: Search Bar -->
        <div class="search-container">
            <input type="text" id="searchInput" onkeyup="searchFunction()" placeholder="اپنی پسندیدہ وادی یا مقام تلاش کریں...">
        </div>
    </header>

    <!-- Navigation -->
    <nav>
        <a href="#destinations">سیاحتی مقامات</a>
        <a href="#directory">لوکل گائیڈز اور سروسز</a>
        <a href="#advisory">ٹریول ایڈوائزری</a>
        <a href="#feedback">سیاحوں کی رائے</a>
    </nav>

    <!-- Main Container -->
    <div class="container">
        
        <!-- Destinations Section -->
        <section id="destinations">
            <h2 class="section-title">مشہور سیاحتی مقامات</h2>
            
            <div class="grid" id="destinationsGrid">
                <!-- Card 1 -->
                <div class="card">
                    <img src="https://images.unsplash.com/photo-1627483262769-04d0a1401487?q=80&w=600" alt="Hunza Valley">
                    <div class="card-content">
                        <h3>ہنزہ وادی (Hunza Valley)</h3>
                        <p>اپنے خوبصورت پہاڑوں، التت اور بلتت قلعوں، اور مہمان نواز لوکل کلچر کی وجہ سے دنیا بھر میں مشہور ہے۔</p>
                    </div>
                </div>

                <!-- Card 2 -->
                <div class="card">
                    <img src="https://images.unsplash.com/photo-1589308078059-be1415eab4c3?q=80&w=600" alt="Attabad Lake">
                    <div class="card-content">
                        <h3>عطا آباد جھیل (Attabad Lake)</h3>
                        <p>شاندار نیلے پانی کی یہ جھیل ہنزہ میں کشتی رانی، جیٹ اسکیئنگ اور فوٹوگرافی کے لیے بہترین مانی جاتی ہے۔</p>
                    </div>
                </div>

                <!-- Card 3 -->
                <div class="card">
                    <img src="https://images.unsplash.com/photo-1605649487212-47bdab064df7?q=80&w=600" alt="Skardu">
                    <div class="card-content">
                        <h3>سکردو وادی (Skardu Valley)</h3>
                        <p>بلتستان کا مرکز، جو شنگریلا جھیل، سرفرنگا سرد ریگستان اور دنیا کی دوسری بلند ترین چوٹی K2 کے راستے کے لیے جانا جاتا ہے۔</p>
                    </div>
                </div>
            </div>
        </section>

        <!-- Feature 2: Services Directory Table -->
        <section id="directory" class="directory-section">
            <h2 class="section-title">لوکل گائیڈز اور ٹرانسپورٹ ڈائریکٹری</h2>
            <p style="text-align: center; margin-bottom: 20px; color:#718096;">سفر کو آسان بنانے کے لیے مقامی ٹرانسپورٹ اور گائیڈز کے متوقع ریٹس:</p>
            <table>
                <thead>
                    <tr>
                        <th>سروس / گاڑی کا نام</th>
                        <th>روٹ / لوکیشن</th>
                        <th>اندازاً کرایہ (یومیہ)</th>
                        <th>بکنگ کا طریقہ</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td>Prado / Jeep 4x4</td>
                        <td>گلگت تا ہنزہ / دیوسائی</td>
                        <td>12,000 - 15,000 PKR</td>
                        <td>واٹس ایپ ہیلپ لائن</td>
                    </tr>
                    <tr>
                        <td>Hiace (Grand Cabin)</td>
                        <td>اسلام آباد تا گلگت/سکردو</td>
                        <td>18,000 - 22,000 PKR</td>
                        <td>واٹس ایپ ہیلپ لائن</td>
                    </tr>
                    <tr>
                        <td>لوکل ٹور گائیڈ سروس</td>
                        <td>تمام مقامی وادیاں</td>
                        <td>3,500 - 5,000 PKR</td>
                        <td>آن لائن بکنگ</td>
                    </tr>
                </tbody>
            </table>
        </section>

        <!-- Feature 3: Advisory & Emergency Info Boxes -->
        <div class="flex-info" id="advisory">
            <div class="info-box">
                <h3 style="color: #2b6cb0;">ℹ️ سیاحوں کے لیے اہم ہدایات</h3>
                <p>گلگت بلتستان آنے سے پہلے موسم اور روڈز (خاص کر شاہراہ قراقرم) کی تازہ ترین صورتحال لازمی چیک کریں۔ مقامی ثقافت، روایات کا احترام کریں، اور ماحول کو صاف ستھرا رکھنے میں اپنا کردار ادا کریں۔</p>
            </div>
            
            <div class="alert-box">
                <h3 style="color: #dd6b20;">🚨 ہنگامی نمبرز (Emergency Contacts)</h3>
                <p><b>ٹورازم ہیلپ لائن:</b> 1422<br>
                <b>جی بی پولیس ہیلپ لائن:</b> 15<br>
                <b>میڈیکل / ریسکیو سروس:</b> 1122<br>
                <b>ڈائریکٹ سپورٹ:</b> 03332637235</p>
            </div>
        </div>

        <!-- Feature 4: Interactive Review / Feedback Section -->
        <section id="feedback" class="reviews-section">
            <h2 class="section-title">سیاحوں کی رائے اور فیڈ بیک</h2>
            <div class="review-form">
                <h3>اپنا خوبصورت تجربہ شیئر کریں:</h3>
                <input type="text" id="visitorName" placeholder="آپ کا نام">
                <textarea id="visitorMessage" rows="4" placeholder="آپ کو گلگت بلتستان کیسا لگا؟ اپنا فیڈ بیک لکھیں..."></textarea>
                <button onclick="addComment()">فیڈ بیک جمع کریں</button>
            </div>

            <div class="reviews-list" id="commentsContainer">
                <div class="user-comment">
                    <strong>علی احمد (اسلام آباد):</strong>
                    <p>ہنزہ اور عطا آباد جھیل کا تجربہ لاجواب تھا! یہاں کے لوگ بہت مخلص اور مددگار ہیں۔ میں سب کو یہاں آنے کا مشورہ دوں گا۔</p>
                </div>
            </div>
        </section>

    </div>

    <!-- Feature 5: Floating WhatsApp Contact Button -->
    <a href="https://wa.me/923332637235" target="_blank" class="whatsapp-float" title="Contact Us on WhatsApp">
        💬
    </a>

    <!-- Footer -->
    <footer>
        <p>&copy; 2026 Discover Gilgit-Baltistan. Created for Travelers & Adventurers.</p>
    </footer>

    <!-- Simple JavaScript for Search & Dynamic Comments -->
    <script>
        // Search Filter Function
        function searchFunction() {
            let input = document.getElementById('searchInput').value.toLowerCase();
            let cards = document.getElementsByClassName('card');
            
            for (let i = 0; i < cards.length; i++) {
                let title = cards[i].getElementsByTagName('h3')[0].innerText.toLowerCase();
                let text = cards[i].getElementsByTagName('p')[0].innerText.toLowerCase();
                if (title.includes(input) || text.includes(input)) {
                    cards[i].style.display = "";
                } else {
                    cards[i].style.display = "none";
                }
            }
        }

        // Add Dynamic Comment Function
        function addComment() {
            let name = document.getElementById('visitorName').value;
            let message = document.getElementById('visitorMessage').value;
            
            if (name.trim() === "" || message.trim() === "") {
                alert("براہ کرم نام اور پیغام دونوں لکھیں!");
                return;
            }
            
            let container = document.getElementById('commentsContainer');
            let newComment = document.createElement('div');
            newComment.className = 'user-comment';
            newComment.innerHTML = `<strong>${name}:</strong><p>${message}</p>`;
            
            container.insertBefore(newComment, container.firstChild);
            
            // Clear Inputs
            document.getElementById('visitorName').value = "";
            document.getElementById('visitorMessage').value = "";
        }
    </script>

</body>
</html>
