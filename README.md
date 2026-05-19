<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Prime Solutions - Web Development Academy</title>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/html2pdf.js/0.10.1/html2pdf.bundle.min.js"></script>
    <style>
        * { box-sizing: border-box; margin: 0; padding: 0; font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; }
        body { background-color: #f0f4f8; color: #2d3748; padding: 15px; min-height: 100vh; display: flex; flex-direction: column; justify-content: space-between; }
        .container { max-width: 900px; margin: 0 auto; width: 100%; }
        
        .navbar { display: flex; justify-content: space-between; align-items: center; background: white; padding: 15px 20px; border-radius: 12px; box-shadow: 0 4px 6px rgba(0,0,0,0.05); margin-bottom: 25px; }
        .nav-brand { font-weight: bold; color: #1a365d; font-size: 1.1rem; }
        .btn-google { background: #ea4335; color: white; padding: 10px 16px; border: none; border-radius: 8px; font-weight: bold; cursor: pointer; box-shadow: 0 2px 4px rgba(234,67,53,0.3); }
        .user-profile { font-weight: 600; color: #2b6cb0; font-size: 0.95rem; }

        header { text-align: center; padding: 35px 20px; background: linear-gradient(135deg, #1a365d, #2a4365); color: white; border-radius: 15px; margin-bottom: 25px; box-shadow: 0 10px 20px rgba(26,54,93,0.15); position: relative; }
        header h1 { font-size: 2rem; letter-spacing: 0.5px; margin-top: 5px; }
        
        .secret-logo { width: 55px; height: 55px; background: rgba(255,255,255,0.15); margin: 0 auto 10px auto; border-radius: 50%; display: flex; align-items: center; justify-content: center; cursor: pointer; font-size: 1.6rem; user-select: none; }

        .card { background: white; padding: 30px 25px; border-radius: 15px; box-shadow: 0 10px 25px rgba(0,0,0,0.05); margin-bottom: 25px; display: none; }
        
        .status-box { padding: 15px; border-radius: 8px; font-weight: 600; margin-bottom: 20px; text-align: center; font-size: 1rem; }
        .status-pending { background: #feebc8; color: #c05621; border: 1px solid #fbd38d; }
        .status-rejected { background: #fed7d7; color: #9b2c2c; border: 1px solid #feb2b2; }
        .status-expired { background: #fff5f5; color: #c53030; border: 1px solid #feb2b2; padding: 15px; border-radius: 8px; margin-bottom: 15px; font-weight: bold; }

        .account-wrapper { background: #f7fafc; border: 1px dashed #cbd5e0; padding: 20px; border-radius: 10px; margin: 20px 0; text-align: left; }
        .account-item { display: flex; justify-content: space-between; padding: 8px 0; border-bottom: 1px solid #edf2f7; }
        .input-field { width: 100%; padding: 14px; margin-bottom: 15px; border: 1px solid #e2e8f0; border-radius: 8px; font-size: 1rem; outline: none; }
        .btn-submit { width: 100%; padding: 14px; background: #3182ce; color: white; border: none; border-radius: 8px; font-size: 1.05rem; font-weight: bold; cursor: pointer; box-shadow: 0 4px 6px rgba(49,130,206,0.25); }

        /* Highly Detailed Extended Course Layout Styling */
        .chapter-card { background: white; padding: 30px; border-radius: 12px; margin-bottom: 30px; box-shadow: 0 4px 12px rgba(0,0,0,0.04); border-left: 6px solid #3182ce; text-align: left; position: relative; }
        .chapter-locked { opacity: 0.4; pointer-events: none; border-left-color: #a0aec0; }
        .chapter-locked::before { content: "🔒 Locked (Pass Previous Chapter Verification Test)"; position: absolute; top: 15px; right: 15px; background: #cbd5e0; color: #4a5568; padding: 6px 14px; border-radius: 20px; font-size: 0.75rem; font-weight: bold; z-index: 10; }
        
        .chapter-title { color: #1a365d; font-size: 1.5rem; font-weight: 700; margin-bottom: 20px; border-bottom: 2px solid #edf2f7; padding-bottom: 10px; }
        .topic-sec { margin-bottom: 25px; background: #f8fafc; padding: 20px; border-radius: 8px; border: 1px solid #edf2f7; }
        .topic-sec h4 { color: #2b6cb0; margin-bottom: 10px; font-size: 1.15rem; border-left: 3px solid #2b6cb0; padding-left: 8px; }
        .topic-sec p { line-height: 1.7; font-size: 0.98rem; color: #4a5568; margin-bottom: 12px; text-align: justify; }
        .topic-sec ul { margin-left: 20px; margin-bottom: 12px; color: #4a5568; line-height: 1.6; }
        .topic-sec ul li { margin-bottom: 6px; font-size: 0.95rem; }
        .code-box { background: #1a202c; color: #f7fafc; padding: 14px; border-radius: 6px; font-family: 'Courier New', Courier, monospace; font-size: 0.88rem; margin-top: 8px; overflow-x: auto; white-space: pre; line-height: 1.5; border-left: 4px solid #ecc94b; }
        
        /* Interactive Quiz Engine */
        .quiz-box { background: #ebf8ff; border: 2px solid #bee3f8; padding: 22px; border-radius: 10px; margin-top: 25px; }
        .quiz-box h5 { color: #2b6cb0; font-size: 1.15rem; margin-bottom: 12px; }
        .quiz-option { display: block; background: white; padding: 12px 15px; border: 1px solid #e2e8f0; border-radius: 6px; margin: 8px 0; cursor: pointer; transition: 0.2s; font-weight: 500; }
        .quiz-option:hover { background: #edf2f7; }
        .quiz-option input { margin-right: 10px; transform: scale(1.1); vertical-align: middle; }
        .btn-quiz { background: #2b6cb0; color: white; padding: 12px 24px; border: none; border-radius: 6px; font-weight: bold; cursor: pointer; margin-top: 10px; box-shadow: 0 2px 4px rgba(43,108,176,0.2); }
        
        /* Premium Digital Certificate Canvas */
        #certificate-area { background: white; border: 12px double #b91c1c; padding: 45px; border-radius: 10px; width: 100%; max-width: 800px; margin: 30px auto; text-align: center; box-shadow: 0 15px 35px rgba(0,0,0,0.1); position: relative; display: none; background-image: radial-gradient(#fffdf6 60%, #fef9e7); }
        #certificate-area::before { content: ""; position: absolute; top: 10px; bottom: 10px; left: 10px; right: 10px; border: 2px solid #b91c1c; pointer-events: none; }
        .cert-title { font-family: 'Georgia', serif; font-size: 2.4rem; color: #1e3a8a; font-weight: bold; text-transform: uppercase; letter-spacing: 2px; margin-bottom: 12px; }
        .cert-sub { font-style: italic; color: #4b5563; font-size: 1.15rem; margin-bottom: 25px; }
        .cert-name { font-family: 'Courier New', Courier, monospace; font-size: 2.6rem; color: #b91c1c; font-weight: bold; border-bottom: 3px solid #1e3a8a; display: inline-block; padding: 0 35px; margin-bottom: 25px; }
        .cert-desc { font-size: 1.05rem; color: #374151; line-height: 1.8; max-width: 650px; margin: 0 auto 35px auto; text-align: center; }
        .cert-footer { display: flex; justify-content: space-between; align-items: center; margin-top: 45px; padding: 0 40px; }
        .cert-sign { text-align: center; border-top: 2px dashed #4b5563; padding-top: 6px; width: 180px; font-weight: bold; color: #1e3a8a; font-size: 0.95rem; }
        .cert-badge { width: 95px; height: 95px; background: #fbbf24; border-radius: 50%; border: 4px dashed #b91c1c; display: flex; align-items: center; justify-content: center; font-size: 2rem; box-shadow: 0 4px 10px rgba(0,0,0,0.1); }
        .btn-download-cert { display: none; background: #10b981; color: white; padding: 15px 30px; border: none; border-radius: 8px; font-weight: bold; cursor: pointer; font-size: 1.1rem; margin: 20px auto; box-shadow: 0 4px 10px rgba(16,185,129,0.3); }

        /* Advanced Enterprise Admin CRM Dashboard Panel */
        .admin-modal { display: none; position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0,0,0,0.6); backdrop-filter: blur(5px); z-index: 1000; justify-content: center; align-items: center; padding: 15px; }
        .admin-content { background: white; padding: 30px; border-radius: 15px; max-width: 850px; width: 100%; max-height: 90vh; overflow-y: auto; position: relative; box-shadow: 0 20px 40px rgba(0,0,0,0.2); }
        .close-admin { position: absolute; top: 15px; right: 20px; font-size: 1.8rem; cursor: pointer; color: #a0aec0; }
        
        .admin-section-title { font-size: 1.3rem; color: #1a365d; margin-top: 25px; margin-bottom: 12px; border-left: 5px solid #e53e3e; padding-left: 10px; font-weight: bold; }
        .student-row { background: #f7fafc; padding: 20px; margin-top: 15px; border-radius: 10px; border: 1px solid #e2e8f0; box-shadow: 0 2px 4px rgba(0,0,0,0.02); }
        .preview-img { max-width: 100%; max-height: 220px; margin-top: 12px; border-radius: 8px; border: 2px solid #cbd5e0; display: block; }
        
        /* Interactive Data Logging Grid Table */
        .db-table-wrapper { width: 100%; overflow-x: auto; margin-top: 10px; background: white; border: 1px solid #e2e8f0; border-radius: 8px; }
        .db-table { width: 100%; border-collapse: collapse; text-align: left; font-size: 0.9rem; }
        .db-table th { background: #2d3748; color: white; padding: 12px; font-weight: 600; }
        .db-table td { padding: 12px; border-bottom: 1px solid #edf2f7; color: #4a5568; }
        .db-table tr:hover { background: #f7fafc; }
        .badge-status { padding: 4px 8px; border-radius: 4px; font-weight: bold; font-size: 0.78rem; text-transform: uppercase; }
        .badge-paid { background: #c6f6d5; color: #22543d; }
        .badge-pending { background: #feebc8; color: #744210; }
        .badge-rejected { background: #fed7d7; color: #742a2a; }
        .badge-expired { background: #e2e8f0; color: #2d3748; }

        .btn-action-panel { display: flex; gap: 10px; margin-top: 14px; }
        .btn-approve { background: #38a169; color: white; padding: 10px; border: none; border-radius: 6px; cursor: pointer; font-weight: bold; flex: 1; }
        .btn-reject { background: #e53e3e; color: white; padding: 10px; border: none; border-radius: 6px; cursor: pointer; font-weight: bold; flex: 1; }

        footer { text-align: center; padding: 25px 0; color: #718096; font-size: 0.9rem; border-top: 1px solid #e2e8f0; margin-top: 40px; }
    </style>
</head>
<body>

<div class="container">
    <div class="navbar">
        <div class="nav-brand">🌐 Prime Solutions Academy</div>
        <div>
            <span id="user-display" class="user-profile">🔒 Security Gate</span>
            <button id="btn-login" class="btn-google">Login with Google</button>
        </div>
    </div>

    <header>
        <div id="secret-trigger" class="secret-logo">👨‍💻</div>
        <h1>A to Z Full Stack Web Development Masterclass</h1>
        <p>Instructor & Platform Architect: Muhammad Nazim</p>
    </header>

    <main>
        <div id="welcome-gate" class="card" style="display: block; text-align: center;">
            <h2>Assalam-o-Alaikum Student! 👋</h2>
            <p style="color: #64748b; margin-top: 10px; line-height: 1.7; font-size: 1.02rem;">Muhammad Nazim bhai ke professional production enterprise learning portal par khushamdeed. Git/GitHub Clouds, Full Front-End Architecture, Responsive Engineering, Javascript Runtime, aur Firebase Live System Core Database Logics ko full depth details me seekhne ke liye apna Google account authenticate karein.</p>
        </div>

        <div id="payment-gate" class="card">
            <div id="student-status-notice"></div>

            <h2>🔒 Premium Curriculum Engine Locked</h2>
            <p style="color: #64748b; margin-top: 5px;">Comprehensive structural lectures, evaluation modules aur digital certificate distribution generator keys active karne ke liye standard monthly platform fee details pass karein:</p>
            
            <div class="account-wrapper">
                <div class="account-item"><strong>📱 JazzCash Account:</strong> <span>03705519562</span></div>
                <div class="account-item"><strong>📱 EasyPaisa Account:</strong> <span>03379827882</span></div>
                <div class="account-item"><strong>👤 Account Title:</strong> <span>Muhammad Nazim</span></div>
                <div class="account-item"><strong>💰 Subscription Fee:</strong> <span>1,500 PKR (30 Days Full Pipeline Streaming)</span></div>
            </div>

            <form id="payment-form">
                <input type="text" id="tid-input" placeholder="Enter 11-Digit Transaction ID (TID)" required class="input-field">
                <label style="font-weight: 600; display: block; margin-bottom: 8px; text-align: left; font-size: 0.9rem; color: #4a5568;">Upload Payment Receipt Screenshot Snapshot:</label>
                <input type="file" id="screenshot-input" accept="image/*" required class="input-field" style="padding: 10px;">
                <button type="submit" class="btn-submit">Submit Verification Request</button>
            </form>
        </div>

        <div id="course-content" class="card">
            <div style="background: #e6fffa; padding: 14px; border-radius: 8px; color: #234e52; font-weight: bold; text-align: center; margin-bottom: 30px; border: 1px solid #b2f5ea;">
                🚀 Premium Access Status: Active (30 Days Corporate Pipeline Streaming & Certificate Provisioning Live)
            </div>

            <div class="chapter-card" id="ch1">
                <div class="chapter-title">📚 Chapter 1: Deep-Dive Front-End Engineering Architecture (HTML5 & CSS3)</div>
                
                <div class="topic-sec">
                    <h4>1. Local Core Development Environment Configurations (Terminal Operations):</h4>
                    <p>Modern developers mobile devices ko mini code servers block me map karne ke liye software terminal application (Termux) configure karte hain. Is module mein aap seekhenge ke kis tarah underlying storage access layers link kiye jaate hain aur structured project scoping boilerplate trees formulate kiye jaate hain:</p>
                    <ul>
                        <li><strong>Storage Interlink Setup:</strong> Operating system parameters validation layers bypass karna.</li>
                        <li><strong>Directory Layout Execution:</strong> Production asset directories tree configuration structure deployment.</li>
                    </ul>
                    <div class="code-box"># Invoke android physical system storage configuration maps
termux-setup-storage

# Formulate enterprise grade isolated repository storage locations
mkdir -p nazim-academy-portal/assets/{css,javascript,media}
cd nazim-academy-portal && touch index.html assets/css/global-styles.css</div>
                </div>

                <div class="topic-sec">
                    <h4>2. Advanced HTML5 Semantic DOM Node Structuring:</h4>
                    <p>Search Engine Optimization (SEO) algorithms or modern multi-screen displays standards match karne ke liye sadi body tags use nahi hoti. Hum strict nested layout containers semantic formatting architecture mapping build karna seekhenge jisse website standard servers algorithm indexation rules read out kar sakein:</p>
                    <ul>
                        <li><code>&lt;meta name="viewport"&gt;</code>: Target dynamic device screen dimensions scales capture rules engine initialization mapping setup.</li>
                        <li><code>&lt;article&gt;</code>, <code>&lt;section&gt;</code>, <code>&lt;nav&gt;</code>: Standard enterprise rendering formatting tags.</li>
                    </ul>
                    <div class="code-box">&lt;!DOCTYPE html&gt;
&lt;html lang="en"&gt;
&lt;head&gt;
    &lt;meta charset="UTF-8"&gt;
    &lt;meta name="viewport" content="width=device-width, initial-scale=1.0"&gt;
    &lt;meta name="description" content="Premium Web Interface Engineered By Muhammad Nazim Course Framework"&gt;
    &lt;title&gt;Prime Solutions Advanced Portal Hub&lt;/title&gt;
    &lt;link rel="stylesheet" href="assets/css/global-styles.css"&gt;
&lt;/head&gt;
&lt;body&gt;
    &lt;nav class="header-navigation-bar"&gt;
        &lt;div class="branding"&gt;Prime Architecture Node&lt;/div&gt;
    &lt;/nav&gt;
    &lt;main id="primary-content-wrapper"&gt;
        &lt;section class="hero-billboard-container"&gt;
            &lt;h1&gt;Architecting Future Standard Web Pipelines&lt;/h1&gt;
            &lt;p&gt;Mastering multi-tier responsive dynamic application frameworks locally.&lt;/p&gt;
        &lt;/section&gt;
    &lt;/main&gt;
&lt;/body&gt;
&lt;/html&gt;</div>
                </div>

                <div class="topic-sec">
                    <h4>3. CSS3 Flex Layout Distribution Matrix & Fluid Adaptive Breakpoints:</h4>
                    <p>Website components ko mathematical pixel spacing patterns, multi-alignment axis positioning parameters dene aur desktop se mobile screen par components grid alignment configurations automatic adjust karne ka flow sequence stylesheet code:</p>
                    <ul>
                        <li><code>display: flex</code>: Flexbox container modeling parameters enable mapping algorithms.</li>
                        <li><code>media query queries breakpoints</code>: Specific dimension matrix screens adaptive overrides rules.</li>
                    </ul>
                    <div class="code-box">/* Base Core Global Definitions Rules */
body { background: #f0f4f8; margin: 0; padding: 20px; font-family: system-ui, sans-serif; }
.hero-billboard-container { display: flex; flex-direction: column; align-items: center; justify-content: center; background: linear-gradient(135deg, #1a365d, #2b6cb0); color: #ffffff; padding: 40px; border-radius: 12px; box-shadow: 0 4px 15px rgba(0,0,0,0.1); text-align: center; }

/* 📱 Responsive Adaptive Fluid Breakpoint Layout Core Configuration Engine */
@media (max-width: 768px) {
    body { padding: 10px; }
    .hero-billboard-container { padding: 20px; border-radius: 8px; }
    h1 { font-size: 1.5rem; line-height: 1.3; }
}</div>
                </div>

                <div class="quiz-box" id="quiz1-box">
                    <h5>📝 Chapter 1 Technical Verification Test:</h5>
                    <p style="font-size: 0.95rem; margin-bottom: 10px; color:#4a5568;"><strong>Q. Elements alignment layouts ko fluid responsiveness dene aur screens ke dimension context ke mutabiq UI rules change karne ke liye CSS mein kya declare karte hain?</strong></p>
                    <label class="quiz-option"><input type="radio" name="q1" value="wrong"> Box-Model Layout Variable Boundary Rules</label>
                    <label class="quiz-option"><input type="radio" name="q1" value="correct"> @media Rules (Fluid Adaptive Breakpoint Queries)</label>
                    <label class="quiz-option"><input type="radio" name="q1" value="wrong"> Standard Static Inline HTML Tags Elements Alignment Controls</label>
                    <button class="btn-quiz" onclick="verifyTest(1)">Submit & Verify Level Logic</button>
                </div>
            </div>

            <div class="chapter-card chapter-locked" id="ch2">
                <div class="chapter-title">📚 Chapter 2: GitHub Cloud Infrastructure Handshakes & Production Deployments</div>
                
                <div class="topic-sec">
                    <h4>1. Cryptographic Identity Signature Configuration:</h4>
                    <p>Git tracking local engine ko cloud core servers (GitHub repositories data clouds) ke sath network pathways configure karne aur accurate developer authorization tags append karne ka full workspace initialization setup workflow rules commands:</p>
                    <div class="code-box"># Initialize cryptographic local metadata indexing tables inside folder
git init

# Bind production global user accounts validation parameters handles
git config --global user.name "YourGitHubUsername"
git config --global user.email "yourauthenticatedaddress@gmail.com"</div>
                </div>

                <div class="topic-sec">
                    <h4>2. Staging Vector Buffers Tracking Matrix & Commit Time-stamping:</h4>
                    <p>Developer files updates or scripts logic changes queue lines code monitoring management workflow framework steps. Is sequence se modification tracks permanently local state registry me snapshot mapping me register kiye jaate hain:</p>
                    <div class="code-box"># Scan and capture modification indices within files structures
git status

# Push all files mutations trackers index vectors inside staging buffer queue
git add .

# Inject snapshot block package tag validation commit code footprint
git commit -m "Integrated premium standard course architecture layout pipelines node"</div>
                </div>

                <div class="topic-sec">
                    <h4>3. Publishing Code Repositories straight into Live Web Domain URLs (GitHub Pages Mapping):</h4>
                    <p>Static or front-end rendering logic elements pages web apps code repositories ko bina expensive web hostings khareede internet dynamic live path cloud URLs (`github.io/repo-name`) par directly route distribution pipelines broadcast instructions flow code commands:</p>
                    <div class="code-box"># Allocate primary development tracking lifecycle pointer stream container
git branch -M main

# Link online isolated cloud system database endpoint address targets URL
git remote add origin https://github.com/YourGitHubUsername/repository-name.git

# Stream entire file data arrays package synchronization transmission protocols
git push -u origin main</div>
                </div>

                <div class="quiz-box" id="quiz2-box">
                    <h5>📝 Chapter 2 Technical Verification Test:</h5>
                    <p style="font-size: 0.95rem; margin-bottom: 10px; color:#4a5568;"><strong>Q. Apne local changes arrays snapshots repositories data code structures ko internet server par existing remote target GitHub repository location directory par push karne ki operation key command kiya hai?</strong></p>
                    <label class="quiz-option"><input type="radio" name="q2" value="correct"> git push -u origin main</label>
                    <label class="quiz-option"><input type="radio" name="q2" value="wrong"> git commit -m "update"</label>
                    <label class="quiz-option"><input type="radio" name="q2" value="wrong"> git remote access configure</label>
                    <button class="btn-quiz" onclick="verifyTest(2)">Submit & Verify Level Logic</button>
                </div>
            </div>

            <div class="chapter-card chapter-locked" id="ch3">
                <div class="chapter-title">📚 Chapter 3: Firebase Cloud Firestore Database Engineering & Authentication</div>
                
                <div class="topic-sec">
                    <h4>1. Application Real-Time Modular Configuration Integrations:</h4>
                    <p>Firebase multi-device cloud architecture parameters parameters ko application browser memory modules core scripts runtime pipelines link integration steps mapping rules:</p>
                    <div class="code-box">&lt;script type="module"&gt;
  import { initializeApp } from "https://www.gstatic.com/firebasejs/9.22.0/firebase-app.js";
  import { getFirestore, doc, setDoc } from "https://www.gstatic.com/firebasejs/9.22.0/firebase-firestore.js";

  // Production-grade credentials endpoints structural configuration layout records mapping
  const firebaseConfig = {
    apiKey: "AIzaSyCsgXPW-ENTERPRISE_DATABASE_SECURITY_KEY_MAPPINGS",
    authDomain: "prime-solutions-academy.firebaseapp.com",
    projectId: "prime-solutions-academy",
    storageBucket: "prime-solutions-academy.appspot.com"
  };

  const app = initializeApp(firebaseConfig);
  const db = getFirestore(app);
&lt;/script&gt;</div>
                </div>

                <div class="topic-sec">
                    <h4>2. Non-SQL NoSQL Firestore Database Write Operations Execution (Real-time Cloud Streaming):</h4>
                    <p>Students tracking structures profiles fields profiles validation indicators matrices records injection document collections datasets arrays update syntax logic instructions handlers parameters functions script:</p>
                    <div class="code-box">// Script logic execution schema data streaming pipeline logic
await setDoc(doc(db, "users", currentUser.uid), {
    studentProfileName: currentUser.displayName,
    enrolledCurriculum: "Full Stack Advanced Frameworks Engineering Model",
    status: "paid",
    billingCycleValidityTimestamp: new Date().toISOString()
}, { merge: true }); // Using critical non-destructive data property values merge mechanics</div>
                </div>

                <div class="quiz-box" id="quiz3-box">
                    <h5>📝 Chapter 3 Technical Verification Test:</h5>
                    <p style="font-size: 0.95rem; margin-bottom: 10px; color:#4a5568;"><strong>Q. Firebase NoSQL Firestore Database Engine infrastructure architecture target documents parameters locations data rows logs updates records inject karne ka direct execution call method kya hai?</strong></p>
                    <label class="quiz-option"><input type="radio" name="q3" value="wrong"> getFirestore(initializeApplicationState)</label>
                    <label class="quiz-option"><input type="radio" name="q3" value="correct"> setDoc(doc(databaseRef, collection, documentId), payload, configurations)</label>
                    <label class="quiz-option"><input type="radio" name="q3" value="wrong"> document.write(firebaseSyncBufferDataLogs)</label>
                    <button class="btn-quiz" onclick="verifyTest(3)">Submit & Verify Level Logic</button>
                </div>
            </div>

            <div class="chapter-card chapter-locked" id="ch4" style="border-left-color: #10b981;">
                <div class="chapter-title" style="color: #10b981;">🎓 Module 4: Engineering Graduation Accomplishments & Verified Certification</div>
                <p style="margin-bottom: 15px; font-weight: 500; color: #374151;">Mubarak ho! Aapne Muhammad Nazim bhai ka highly extended structural full stack development syllabus training parameters framework evaluate tests successfully qualify aur match kar liya hai. Aapka enterprise printable cryptographic level verification award live ready state status active ho chuka hai:</p>
                
                <div id="certificate-area">
                    <div class="cert-title">Certificate of Completion</div>
                    <div class="cert-sub">This is officially presented to</div>
                    <div class="cert-name" id="cert-student-name">Student Name</div>
                    <div class="cert-desc">For successfully pursuing, completing, and fulfilling all testing assignment parameters for the <strong>Full Stack Web Development & Cloud Architecture Masterclass</strong> under the strict mentoring and technical guidance of Prime Solutions Academy.</div>
                    
                    <div class="cert-footer">
                        <div class="cert-sign">
                            <span style="font-family: 'Brush Script MT', cursive, sans-serif; font-size: 1.3rem; color: #b91c1c;">M. Nazim</span><br>
                            Authorized Signature
                        </div>
                        <div class="cert-badge">🏆</div>
                        <div class="cert-sign">
                            <span style="font-family: monospace; font-size: 0.9rem; color: #1e3a8a;">PRIME-2026-REG</span><br>
                            Verification Code
                        </div>
                    </div>
                </div>

                <button class="btn-download-cert" id="download-btn" onclick="triggerPDFDownload()">📥 Download Premium Verified High-Quality PDF Certificate</button>
            </div>

        </div>
    </main>
</div>

<div id="admin-panel" class="admin-modal">
    <div class="admin-content">
        <span id="close-modal" class="close-admin">&times;</span>
        <h2 style="color: #1a365d; border-bottom: 3px solid #3182ce; padding-bottom: 8px; font-size: 1.6rem; font-weight: bold;">😎 Prime Solutions Enterprise Control Room</h2>
        <p style="font-size: 0.88rem; color: #4a5568; margin-top: 4px;">Ecosystem Architect Platform Controller Manager View Node: Muhammad Nazim</p>
        
        <div class="admin-section-title">⏳ Pending Payments Verification Stream Queue</div>
        <div id="student-requests-list" style="margin-top: 10px;">
            <p style="color: #718096; text-align: center; padding: 20px 0;">No active incoming payload processing verifications tokens queues.</p>
        </div>

        <div class="admin-section-title">📊 Registered Students Real-time Records Master Directory Ledger</div>
        <div class="db-table-wrapper">
            <table class="db-table">
                <thead>
                    <tr>
                        <th>Student Name Name</th>
                        <th>Registered Email</th>
                        <th>Submit TID</th>
                        <th>Current Chapter Level Progress</th>
                        <th>Billing System Status</th>
                        <th>Manual Action Control Panel</th>
                    </tr>
                </thead>
                <tbody id="crm-students-data-rows">
                    <tr>
                        <td colspan="6" style="text-align: center; padding: 20px; color: #a0aec0;">Syncing Firebase Firestore Core Cloud Pipelines Data Logs Matrices...</td>
                    </tr>
                </tbody>
            </table>
        </div>
    </div>
</div>

<footer>
    <p>© 2026 Prime Solutions Inc. Core Full Stack Platform Architecture Systems Designed & Engineered by Muhammad Nazim. All Rights Reserved. 🚀</p>
</footer>

<script type="module">
  import { initializeApp } from "https://www.gstatic.com/firebasejs/9.22.0/firebase-app.js";
  import { getFirestore, doc, setDoc, getDoc, collection, getDocs, updateDoc } from "https://www.gstatic.com/firebasejs/9.22.0/firebase-firestore.js";
  import { getAuth, signInWithPopup, GoogleAuthProvider, onAuthStateChanged } from "https://www.gstatic.com/firebasejs/9.22.0/firebase-auth.js";

  const firebaseConfig = {
    apiKey: "AIzaSyCsgXPW-h2NzAHMrDBIL_HjlU8wSpcgzvI",
    authDomain: "course-3cc77.firebaseapp.com",
    databaseURL: "https://course-3cc77-default-rtdb.firebaseio.com",
    projectId: "course-3cc77",
    storageBucket: "course-3cc77.firebasestorage.app",
    messagingSenderId: "136140432667",
    appId: "1:136140432667:web:9f543dc3db8683944ddfbe"
  };

  const app = initializeApp(firebaseConfig);
  const db = getFirestore(app);
  const auth = getAuth(app);
  const provider = new GoogleAuthProvider();
  let currentUser = null;

  document.getElementById("btn-login").addEventListener("click", () => {
      signInWithPopup(auth, provider).catch(err => alert("Auth Authentication Handshake Aborted Network Error Code: " + err.message));
  });

  onAuthStateChanged(auth, async (user) => {
    if (user) {
      currentUser = user;
      document.getElementById("user-display").innerText = "👤 " + user.displayName;
      document.getElementById("btn-login").style.display = "none";
      document.getElementById("welcome-gate").style.display = "none";
      document.getElementById("cert-student-name").innerText = user.displayName; 
      syncUserAuthorization();
    } else {
      document.getElementById("welcome-gate").style.display = "block";
      document.getElementById("payment-gate").style.display = "none";
      document.getElementById("course-content").style.display = "none";
    }
  });

  async function syncUserAuthorization() {
      const userDoc = await getDoc(doc(db, "users", currentUser.uid));
      const noticeDiv = document.getElementById("student-status-notice");
      const formElement = document.getElementById("payment-form");
      noticeDiv.innerHTML = ""; 

      if (userDoc.exists()) {
          const userData = userDoc.data();
          
          if (userData.status === "paid") {
              const approvalTime = new Date(userData.approved_at).getTime();
              const currentTime = new Date().getTime();
              const daysPassed = (currentTime - approvalTime) / (1000 * 60 * 60 * 24);

              // 30 Days Validation Expiry Automation Checks Engine
              if (daysPassed >= 30) { 
                  await updateDoc(doc(db, "users", currentUser.uid), { status: "expired" });
                  location.reload();
              } else {
                  document.getElementById("payment-gate").style.display = "none";
                  document.getElementById("course-content").style.display = "block";
                  
                  if(userData.chapterProgress) {
                      for(let i=2; i<=4; i++) {
                          if(userData.chapterProgress >= i) {
                              document.getElementById("ch" + i).classList.remove("chapter-locked");
                              if(i === 4) { 
                                  document.getElementById("certificate-area").style.display = "block";
                                  document.getElementById("download-btn").style.display = "block";
                              }
                          }
                      }
                  }
              }
          } 
          else if (userData.status === "expired") {
              document.getElementById("payment-gate").style.display = "block";
              document.getElementById("course-content").style.display = "none";
              formElement.style.display = "block";
              noticeDiv.innerHTML = `<div class="status-box status-expired">🚨 Premium Boundary Error: Aapka monthly validation subscription loop duration lifecycle (30 Days Active Plan) complete ho chuka hai. Web elements restore karne ke liye verification request details forms check fields execute karein!</div>`;
          }
          else if (userData.status === "pending") {
              document.getElementById("payment-gate").style.display = "block";
              document.getElementById("course-content").style.display = "none";
              formElement.style.display = "none";
              noticeDiv.innerHTML = `<div class="status-box status-pending">⏳ Verification Data Processing Queue: Systems elements transaction files values tracking mapping process are under review. System administrator evaluation checks active.</div>`;
          } 
          else if (userData.status === "rejected") {
              document.getElementById("payment-gate").style.display = "block";
              document.getElementById("course-content").style.display = "none";
              formElement.style.display = "block";
              noticeDiv.innerHTML = `<div class="status-box status-rejected">❌ <strong>Subscription Request Rejected Denied:</strong> ${userData.rejection_reason || 'TID match patterns failed validation models.'} Transaction information forms re-apply parameters details.</div>`;
          }
      } else {
          document.getElementById("payment-gate").style.display = "block";
          formElement.style.display = "block";
          
          // Initialize New Fresh Entry Cloud Document Record on Database if user logins first time
          await setDoc(doc(db, "users", currentUser.uid), {
              uid: currentUser.uid,
              name: currentUser.displayName,
              email: currentUser.email,
              status: "not_applied",
              chapterProgress: 1,
              tid: "N/A",
              submitted_at: new Date().toISOString()
          }, { merge: true });
      }
  }

  document.getElementById("payment-form").addEventListener("submit", (e) => {
      e.preventDefault();
      const tid = document.getElementById("tid-input").value;
      const file = document.getElementById("screenshot-input").files[0];

      if (file) {
          const reader = new FileReader();
          reader.onloadend = async () => {
              try {
                  await setDoc(doc(db, "users", currentUser.uid), {
                      uid: currentUser.uid,
                      name: currentUser.displayName,
                      email: currentUser.email,
                      status: "pending",
                      tid: tid,
                      screenshot_base64: reader.result,
                      submitted_at: new Date().toISOString()
                  }, { merge: true });
                  alert("Verification transmission payloads injected successfully into Firestore Cloud Ledger Pipelines!");
                  syncUserAuthorization();
              } catch (err) { alert("Core Database Engine Input Crash System Error: " + err.message); }
          };
          reader.readAsDataURL(file);
      }
  });

  // Automated Testing Real-time Interactive Score Evaluation Handlers Engine
  window.verifyTest = async function(chapterNumber) {
      const selectedOpt = document.querySelector(`input[name="q${chapterNumber}"]:checked`);
      if(!selectedOpt) return alert("Pehle active checklist radio interface element options variables click checked select karein!");

      if(selectedOpt.value === "correct") {
          alert("🎉 Evaluation Matrix Validated! Agla premium instruction module dashboard core data structure layer successfully load structural unlock ho gaya hai.");
          const nextChapterNum = chapterNumber + 1;
          
          const nextChEl = document.getElementById("ch" + nextChapterNum);
          if(nextChEl) {
              nextChEl.classList.remove("chapter-locked");
              if(nextChapterNum === 4) { 
                  document.getElementById("certificate-area").style.display = "block";
                  document.getElementById("download-btn").style.display = "block";
              }
          }
          
          if(currentUser) {
              try {
                  await setDoc(doc(db, "users", currentUser.uid), {
                      chapterProgress: nextChapterNum
                  }, { merge: true });
              } catch(e) { console.error("Cloud Synchronization Runtime Mapping Logic Fault: ", e); }
          }
      } else {
          alert("❌ Compile Execution Logic Match Error: Selected Answer Invalid! Provided structural concepts readings instructions blocks ko re-study check karein.");
      }
  }

  // Instant Document Certificate Layout PDF Generation Module Link Logic
  window.triggerPDFDownload = function() {
      const elementTarget = document.getElementById('certificate-area');
      const configurationOptions = {
          margin:       0.4,
          filename:     'Prime_Solutions_Web_Development_Graduation_Award.pdf',
          image:        { type: 'jpeg', quality: 0.99 },
          html2canvas:  { scale: 2.5, useCORS: true },
          jsPDF:        { unit: 'in', format: 'letter', orientation: 'landscape' }
      };
      html2pdf().set(configurationOptions).from(elementTarget).save();
  };

  // Advanced Secure Admin Panel Portal Matrix Trigger (4 Taps Sequence Node Interface Controllers)
  let clickSessionCount = 0;
  let clickTimeout;
  document.getElementById("secret-trigger").addEventListener("click", () => {
      clickSessionCount++;
      clearTimeout(clickTimeout);
      clickTimeout = setTimeout(() => { clickSessionCount = 0; }, 1200);
      if (clickSessionCount === 4) {
          clickSessionCount = 0;
          let accessPass = prompt("🔑 Admin Gateway Master Console Handshake Key Credentials Entry:");
          if (accessPass === "nor804") launchControlConsole();
      }
  });

  async function launchControlConsole() {
      document.getElementById("admin-panel").style.display = "flex";
      const requestsContainer = document.getElementById("student-requests-list");
      const crmTableBody = document.getElementById("crm-students-data-rows");
      
      requestsContainer.innerHTML = "<p style='text-align:center; font-weight:600;'>Accessing Processing Requests Stream Keys Buffer Matrix...</p>";
      crmTableBody.innerHTML = "<tr><td colspan='6' style='text-align:center;'>Accessing Cloud Full System Documents Directory Database Matrices Logs Ledger...</td></tr>";

      try {
          const cloudSnapshot = await getDocs(collection(db, "users"));
          requestsContainer.innerHTML = "";
          crmTableBody.innerHTML = "";
          let requestsPending = false;

          cloudSnapshot.forEach((docSnap) => {
              const profile = docSnap.data();
              
              // ⏳ RENDER COMPONENT TYPE A: RENDER INCOMING TICKETS QUEUE LINK PILES LOGS
              if (profile.status === "pending") {
                  requestsPending = true;
                  const requestItem = document.createElement("div");
                  requestItem.className = "student-row";
                  requestItem.innerHTML = `
                      <p><strong>Student Target Identity:</strong> ${profile.name}</p>
                      <p><strong>Associated Authentication Route Email:</strong> ${profile.email}</p>
                      <p><strong>Transaction TID Index Code:</strong> <span style="color:#e53e3e; font-weight:700;">${profile.tid}</span></p>
                      <img src="${profile.screenshot_base64}" class="preview-img" alt="Screenshot Snapshot Log Receipt Attachment"/>
                      <div class="btn-action-panel">
                          <button class="btn-approve" data-uid="${profile.uid}">Approve Token Activation & Provide 30 Days Access</button>
                          <button class="btn-reject" data-uid="${profile.uid}">Deny Request Ticket Payload</button>
                      </div>
                  `;
                  requestsContainer.appendChild(requestItem);
              }

              // 📊 RENDER COMPONENT TYPE B: LIVE FULL ENTERPRISE DIRECTORY DATABASE RECORDS LEDGER TABLE ROWS BUILD INJECTIONS
              const rowItem = document.createElement("tr");
              let progressLabel = profile.chapterProgress ? "Module " + profile.chapterProgress : "Module 1 Initialization";
              if (profile.chapterProgress === 4) progressLabel = "🎓 Graduated Complete Certificate Enabled";
              
              let statusBadgeClass = "badge-pending";
              if(profile.status === "paid") statusBadgeClass = "badge-paid";
              if(profile.status === "rejected") statusBadgeClass = "badge-rejected";
              if(profile.status === "expired") statusBadgeClass = "badge-expired";

              rowItem.innerHTML = `
                  <td><strong>${profile.name || "Unknown User Node"}</strong></td>
                  <td>${profile.email || "N/A Address"}</td>
                  <td style="font-family:monospace; font-weight:bold; color:#2c5282;">${profile.tid || "No Upload Logs"}</td>
                  <td><span style="color:#2b6cb0; font-weight:600;">${progressLabel}</span></td>
                  <td><span class="badge-status ${statusBadgeClass}">${profile.status || "not_applied"}</span></td>
                  <td>
                      <button class="btn-approve manual-status-toggle" data-uid="${profile.uid}" style="padding: 4px 8px; font-size: 0.75rem; border-radius:4px; margin-right:4px;">Force Active Access</button>
                      <button class="btn-reject manual-status-revoke" data-uid="${profile.uid}" style="padding: 4px 8px; font-size: 0.75rem; border-radius:4px;">Force Revoke Expire</button>
                  </td>
              `;
              crmTableBody.appendChild(rowItem);
          });

          if (!requestsPending) {
              requestsContainer.innerHTML = "<p style='color:#38a169; font-weight:700; text-align:center; padding:15px;'>🎉 Target active requests verification queue clean. No pending user data pipelines payload validation actions logs.</p>";
          }

          // Register Action Grid Handles Listeners Hooks Elements Targets Blocks Parameters Functions Execution Loops
          document.querySelectorAll(".btn-approve").forEach(actionBtn => {
              actionBtn.addEventListener("click", async (event) => {
                  const targetedUid = event.target.getAttribute("data-uid");
                  try {
                      await updateDoc(doc(db, "users", targetedUid), { 
                          status: "paid",
                          approved_at: new Date().toISOString(),
                          chapterProgress: 1
                      });
                      alert("🎯 System Payload Active: Student core parameters tokens activated safely for 30 Days active lifespan!");
                      launchControlConsole(); 
                      if(currentUser && currentUser.uid === targetedUid) syncUserAuthorization();
                  } catch (err) { alert("Failed Processing Pipeline Action Handle Error: " + err.message); }
              });
          });

          document.querySelectorAll(".btn-reject").forEach(actionBtn => {
              actionBtn.addEventListener("click", async (event) => {
                  const targetedUid = event.target.getAttribute("data-uid");
                  let reason = prompt("Enter Dynamic Rejection Verification Feedback Log System String Context Details:");
                  if (reason === null) return;
                  try {
                      await updateDoc(doc(db, "users", targetedUid), { 
                          status: "rejected",
                          rejection_reason: reason
                      });
                      alert("❌ Processing Operations Revoked: Rejection feedback criteria log metrics appended into database snapshot doc.");
                      launchControlConsole(); 
                      if(currentUser && currentUser.uid === targetedUid) syncUserAuthorization();
                  } catch (err) { alert("Failed Processing Pipeline Action Handle Error: " + err.message); }
              });
          });

          // CRM Dynamic Manual Override Action Handling Rules Direct Triggers
          document.querySelectorAll(".manual-status-revoke").forEach(actionBtn => {
              actionBtn.addEventListener("click", async (event) => {
                  const targetedUid = event.target.getAttribute("data-uid");
                  if(!confirm("Are you absolute sure to force expire this student account?")) return;
                  try {
                      await updateDoc(doc(db, "users", targetedUid), { status: "expired" });
                      alert("🔒 Target access vector permanently expired and revoked successfully!");
                      launchControlConsole();
                      if(currentUser && currentUser.uid === targetedUid) syncUserAuthorization();
                  } catch (err) { alert("CRM Write Override Track Fault: " + err.message); }
              });
          });

      } catch (err) { 
          requestsContainer.innerHTML = "<p style='color:red;'>Operational Backplane Framework Sync Crash Error Message Trace: " + err.message + "</p>"; 
          crmTableBody.innerHTML = "<tr><td colspan='6' style='color:red; font-weight:bold; text-align:center;'>Operational Firestore Sync Stack Error Fatal!</td></tr>";
      }
  }

  document.getElementById("close-modal").addEventListener("click", () => {
      document.getElementById("admin-panel").style.display = "none";
  });
</script>
</body>
</html>
