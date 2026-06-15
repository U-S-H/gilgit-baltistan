<html lang="ur">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Discover Gilgit-Baltistan - Tourist Hub</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background-color: #f4f7f6;
            color: #333;
            line-height: 1.6;
        }

        /* Header Styling */
        header {
            background: linear-gradient(rgba(0, 0, 0, 0.6), rgba(0, 0, 0, 0.6)), url('https://images.unsplash.com/photo-1548013146-72479768bada?q=80&w=1200') no-repeat center center/cover;
            height: 60vh;
            color: white;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
            padding: 20px;
        }

        header h1 {
            font-size: 3rem;
            margin-bottom: 10px;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.7);
        }

        header p {
            font-size: 1.2rem;
            max-width: 600px;
            text-shadow: 1px 1px 3px rgba(0,0,0,0.5);
        }

        /* Navigation Bar */
        nav {
            background-color: #1a365d;
            display: flex;
            justify-content: center;
            padding: 15px 0;
            position: sticky;
            top: 0;
            z-index: 1000;
        }

        nav a {
            color: white;
            text-decoration: none;
            margin: 0 20px;
            font-size: 1.1rem;
            font-weight: bold;
            transition: color 0.3s;
        }

        nav a:hover {
            color: #63b3ed;
        }

        /* Main Content */
        .container {
            max-width: 1200px;
            margin: 40px auto;
            padding: 0 20px;
        }

        .section-title {
            text-align: center;
            margin-bottom: 30px;
            color: #2c5282;
            font-size: 2rem;
        }

        /* Destination Cards Grid */
        .grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 30px;
        }

        .card {
            background: white;
            border-radius: 8px;
            overflow: hidden;
            box-shadow: 0 4px 6px rgba(0,0,0,0.1);
            transition: transform 0.3s;
        }

        .card:hover {
            transform: translateY(-5px);
        }

        .card img {
            width: 100%;
            height: 200px;
            object-fit: cover;
        }

        .card-content {
            padding: 20px;
        }

        .card-content h3 {
            margin-bottom: 10px;
            color: #1a365d;
        }

        .card-content p {
            font-size: 0.95rem;
            color: #555;
        }

        /* Info Section */
        .info-box {
            background-color: #ebf8ff;
            border-left: 5px solid #3182ce;
            padding: 20px;
            margin-top: 40px;
            border-radius: 4px;
        }

        .info-box h2 {
            color: #2b6cb0;
            margin-bottom: 10px;
        }

        /* WhatsApp Button Section */
        .whatsapp-section {
            text-align: center;
            margin: 50px 0;
            padding: 30px;
            background: #e3faf1;
            border-radius: 10px;
            box-shadow: 0 4px 15px rgba(0,0,0,0.05);
        }

        .whatsapp-section h3 {
            color: #204133;
            margin-bottom: 15px;
            font-size: 1.5rem;
        }

        .ws-btn {
            display: inline-flex;
            align-items: center;
            background-color: #25D366;
            color: white;
            text-decoration: none;
            padding: 12px 30px;
            font-size: 1.2rem;
            font-weight: bold;
            border-radius: 50px;
            box-shadow: 0 4px 10px rgba(37, 211, 102, 0.4);
            transition: transform 0.2s, background-color 0.3s;
        }

        .ws-btn:hover {
            background-color: #1ebd58;
            transform: scale(1.05);
        }

        /* Footer */
        footer {
            background-color: #1a365d;
            color: white;
            text-align: center;
            padding: 20px 0;
            margin-top: 60px;
            font-size: 0.9rem;
        }
    </style>
</head>
<body>

    <!-- Header Section -->
    <header>
        <h1>Discover Gilgit-Baltistan</h1>
        <p>جنت نظیر وادیوں، فلک بوس پہاڑوں اور خوبصورت ثقافت کی سرزمین میں آپ کا استقبال ہے۔</p>
    </header>

    <!-- Navigation -->
    <nav>
        <a href="#home">ہوم</a>
        <a href="#destinations">مقامات</a>
        <a href="#guides">سفری معلومات</a>
    </nav>

    <!-- Main Container -->
    <div class="container">
        
        <!-- Destinations Section -->
        <section id="destinations">
            <h2 class="section-title">مشہور سیاحتی مقامات</h2>
            
            <div class="grid">
                <!-- Card 1 -->
                <div class="card">
                    <img src="https://images.unsplash.com/photo-1627483262769-04d0a1401487?q=80&w=600" alt="Hunza Valley">
                    <div class="card-content">
                        <h3>ہنزہ وادی (Hunza Valley)</h3>
                        <p>اپنے خوبصورت پہاڑوں، قلعوں (Baltit & Altit) اور مہمان نواز لوگوں کی وجہ سے دنیا بھر میں مشہور ہے۔</p>
                    </div>
                </div>

                <!-- Card 2 -->
                <div class="card">
                    <img src="https://images.unsplash.com/photo-1589308078059-be1415eab4c3?q=80&w=600" alt="Attabad Lake">
                    <div class="card-content">
                        <h3>عطا آباد جھیل (Attabad Lake)</h3>
                        <p>نیلے چمکدار پانی کی یہ جھیل کشتی رانی اور جیٹ اسکیئنگ کے شوقین افراد کے لیے ایک بہترین جگہ ہے۔</p>
                    </div>
                </div>

                <!-- Card 3 -->
                <div class="card">
                    <img src="https://images.unsplash.com/photo-1605649487212-47bdab064df7?q=80&w=600" alt="Skardu">
                    <div class="card-content">
                        <h3>سکردو (Skardu Valley)</h3>
                        <p>کے ٹو (K2) کی بیس کیمپ کا راستہ اور شنگریلا جھیل جیسے خوبصورت مقامات کا مرکز۔</p>
                    </div>
                </div>
            </div>
        </section>

        <!-- WhatsApp Contact Section -->
        <section class="whatsapp-section">
            <h3>گلگت بلتستان ٹور گائیڈ اور معلومات کے لیے ہم سے رابطہ کریں</h3>
            <a href="https://wa.me/923332637235" target="_blank" class="ws-btn">
                💬 واٹس ایپ پر رابطہ کریں
            </a>
        </section>

        <!-- Travel Guide Section -->
        <section id="guides" class="info-box">
            <h2>سیاحوں کے لیے اہم معلومات 🏔️</h2>
            <p>گلگت بلتستان آنے سے پہلے موسم کی صورتحال لازمی چیک کریں۔ مقامی ثقافت اور روایات کا احترام کریں، اور خوبصورتی کو برقرار رکھنے کے لیے صفائی کا خاص خیال رکھیں۔</p>
        </section>

    </div>

    <!-- Footer -->
    <footer>
        <p>&copy; 2026 Discover Gilgit-Baltistan. All Rights Reserved.</p>
    </footer>

</body>
</html>
