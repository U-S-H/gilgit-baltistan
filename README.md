<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Prime Solutions - Web Development Academy</title>
    <style>
        * { box-sizing: border-box; margin: 0; padding: 0; font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; }
        body { background-color: #f0f4f8; color: #2d3748; padding: 15px; min-height: 100vh; display: flex; flex-direction: column; justify-content: space-between; }
        .container { max-width: 850px; margin: 0 auto; width: 100%; }
        
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

        /* Premium Syllabus & Chapters Expansion */
        .chapter-card { background: white; padding: 25px; border-radius: 12px; margin-bottom: 25px; box-shadow: 0 4px 12px rgba(0,0,0,0.04); border-left: 6px solid #3182ce; text-align: left; position: relative; }
        .chapter-locked { opacity: 0.6; pointer-events: none; border-left-color: #a0aec0; }
        .chapter-locked::before { content: "🔒 Chapter Locked (Complete Previous Test)"; position: absolute; top: 10px; right: 15px; background: #e2e8f0; color: #4a5568; padding: 4px 10px; border-radius: 20px; font-size: 0.75rem; font-weight: bold; }
        
        .chapter-title { color: #1a365d; font-size: 1.4rem; font-weight: 700; margin-bottom: 15px; border-bottom: 2px solid #edf2f7; padding-bottom: 8px; }
        .topic-sec { margin-bottom: 15px; background: #f8fafc; padding: 15px; border-radius: 8px; border: 1px solid #edf2f7; }
        .topic-sec h4 { color: #2b6cb0; margin-bottom: 8px; font-size: 1.1rem; }
        .code-box { background: #1a202c; color: #f7fafc; padding: 12px; border-radius: 6px; font-family: 'Courier New', Courier, monospace; font-size: 0.9rem; margin-top: 5px; overflow-x: auto; }
        
        /* Interactive Quiz Styling */
        .quiz-box { background: #ebf8ff; border: 2px solid #bee3f8; padding: 20px; border-radius: 10px; margin-top: 20px; }
        .quiz-box h5 { color: #2b6cb0; font-size: 1.1rem; margin-bottom: 12px; }
        .quiz-option { display: block; background: white; padding: 10px 15px; border: 1px solid #e2e8f0; border-radius: 6px; margin: 8px 0; cursor: pointer; transition: 0.2s; font-weight: 500; }
        .quiz-option:hover { background: #e2e8f0; }
        .quiz-option input { margin-right: 10px; }
        .btn-quiz { background: #2b6cb0; color: white; padding: 8px 16px; border: none; border-radius: 6px; font-weight: bold; cursor: pointer; margin-top: 10px; }
        
        /* Admin View */
        .admin-modal { display: none; position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0,0,0,0.6); backdrop-filter: blur(5px); z-index: 1000; justify-content: center; align-items: center; padding: 15px; }
        .admin-content { background: white; padding: 30px; border-radius: 15px; max-width: 600px; width: 100%; max-height: 85vh; overflow-y: auto; position: relative; }
        .close-admin { position: absolute; top: 15px; right: 20px; font-size: 1.8rem; cursor: pointer; color: #a0aec0; }
        .student-row { background: #f7fafc; padding: 18px; margin-top: 15px; border-radius: 10px; border: 1px solid #e2e8f0; }
        .preview-img { max-width: 100%; max-height: 180px; margin-top: 12px; border-radius: 8px; border: 2px solid #e2e8f0; }
        .btn-action-panel { display: flex; gap: 10px; margin-top: 12px; }
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
        <h1>Web Development Complete Premium Course</h1>
        <p>Instructor & Industry Mentor: Muhammad Nazim</p>
    </header>

    <main>
        <div id="welcome-gate" class="card" style="display: block; text-align: center;">
            <h2>Assalam-o-Alaikum Student! 👋</h2>
            <p style="color: #64748b; margin-top: 10px; line-height: 1.6;">Muhammad Nazim bhai ke premium learning portal par khushamdeed. A to Z long detailed chapters aur interactive assessments access karne ke liye apna Google account login karein.</p>
        </div>

        <div id="payment-gate" class="card">
            <div id="student-status-notice"></div>

            <h2>🔒 Premium Content Locked</h2>
            <p style="color: #64748b; margin-top: 5px;">Full course chapters unlock karne ke liye monthly subscription fee transfer kar ke verify karwayein:</p>
            
            <div class="account-wrapper">
                <div class="account-item"><strong>📱 JazzCash Account:</strong> <span>03705519562</span></div>
                <div class="account-item"><strong>📱 EasyPaisa Account:</strong> <span>03379827882</span></div>
                <div class="account-item"><strong>👤 Account Title:</strong> <span>Muhammad Nazim</span></div>
                <div class="account-item"><strong>💰 Monthly Subscription:</strong> <span>1,500 PKR (Valid for 30 Days)</span></div>
            </div>

            <form id="payment-form">
                <input type="text" id="tid-input" placeholder="Enter 11-Digit Transaction ID (TID)" required class="input-field">
                <label style="font-weight: 600; display: block; margin-bottom: 8px; text-align: left; font-size: 0.9rem; color: #4a5568;">Upload Payment Receipt Screenshot:</label>
                <input type="file" id="screenshot-input" accept="image/*" required class="input-field" style="padding: 10px;">
                <button type="submit" class="btn-submit">Submit Verification Request</button>
            </form>
        </div>

        <div id="course-content" class="card">
            <div style="background: #e6fffa; padding: 12px; border-radius: 8px; color: #234e52; font-weight: bold; text-align: center; margin-bottom: 25px;">
                🎉 Premium Course Dashboard: Active Status (30 Days Access Provisioned)
            </div>

            <div class="chapter-card" id="ch1">
                <div class="chapter-title">📚 Chapter 1: HTML5 Architecture & Semantic Layouts</div>
                
                <div class="topic-sec">
                    <h4>1. Termux Production Setup:</h4>
                    <p>Professional directory structure create karne ke liye Termux terminal par ye command chalayein:</p>
                    <div class="code-box">mkdir -p prime-project/{assets/css,assets/js,pages}
cd prime-project && touch index.html assets/css/style.css</div>
                </div>

                <div class="topic-sec">
                    <h4>2. HTML5 Semantic Scaffolding:</h4>
                    <p>SEO-friendly aur robust standard structural elements jo har modern layout ka hissa hote hain:</p>
                    <div class="code-box">&lt;header&gt;
    &lt;nav&gt;Home | About | Courses&lt;/nav&gt;
&lt;/header&gt;
&lt;main&gt;
    &lt;article&gt;
        &lt;h2&gt;Semantic Web Development&lt;/h2&gt;
        &lt;p&gt;Learning structure under Prime Solutions.&lt;/p&gt;
    &lt;/article&gt;
&lt;/main&gt;
&lt;footer&gt;&copy; 2026 Academy&lt;/footer&gt;</div>
                </div>

                <div class="quiz-box" id="quiz1-box">
                    <h5>📝 Chapter 1 Verification Test:</h5>
                    <p style="font-size: 0.95rem; margin-bottom: 10px; color:#4a5568;"><strong>Q. Kis tag ka use layout mein footer ya copyright details show karne ke liye kiya jata hai?</strong></p>
                    <label class="quiz-option"><input type="radio" name="q1" value="wrong"> &lt;bottom&gt;</label>
                    <label class="quiz-option"><input type="radio" name="q1" value="correct"> &lt;footer&gt;</label>
                    <label class="quiz-option"><input type="radio" name="q1" value="wrong"> &lt;section&gt;</label>
                    <button class="btn-quiz" onclick="verifyTest(1)">Submit Answer</button>
                </div>
            </div>

            <div class="chapter-card chapter-locked" id="ch2">
                <div class="chapter-title">📚 Chapter 2: Modern CSS3 Aesthetics & Box-Model</div>
                
                <div class="topic-sec">
                    <h4>1. CSS Box-Model Concepts:</h4>
                    <p>Margin, Border, Padding aur Content spacing ko effectively customize karna seekhein:</p>
                    <div class="code-box">.custom-card {
    width: 100%;
    padding: 20px;
    margin: 15px 0;
    border: 2px solid #3182ce;
    box-sizing: border-box;
}</div>
                </div>

                <div class="topic-sec">
                    <h4>2. CSS Flexbox Layout Alignment:</h4>
                    <p>Bina float use kiye cards ya elements ko dynamic flexible row ya column mein responsive alignment dena:</p>
                    <div class="code-box">.flex-container {
    display: flex;
    justify-content: space-between;
    align-items: center;
}</div>
                </div>

                <div class="quiz-box" id="quiz2-box">
                    <h5>📝 Chapter 2 Verification Test:</h5>
                    <p style="font-size: 0.95rem; margin-bottom: 10px; color:#4a5568;"><strong>Q. Flex items ko horizontally control karne ke liye kis property ka use hota hai?</strong></p>
                    <label class="quiz-option"><input type="radio" name="q2" value="correct"> justify-content</label>
                    <label class="quiz-option"><input type="radio" name="q2" value="wrong"> align-items</label>
                    <label class="quiz-option"><input type="radio" name="q2" value="wrong"> display-grid</label>
                    <button class="btn-quiz" onclick="verifyTest(2)">Submit Answer</button>
                </div>
            </div>

            <div class="chapter-card chapter-locked" id="ch3">
                <div class="chapter-title">📚 Chapter 3: Mobile-First Responsive Media Queries</div>
                
                <div class="topic-sec">
                    <h4>1. Viewport Meta Configuration:</h4>
                    <p>Mobile screens par elements auto-shrink hone se rokne ke liye head tag mein layout definition:</p>
                    <div class="code-box">&lt;meta name="viewport" content="width=device-width, initial-scale=1.0"&gt;</div>
                </div>

                <div class="topic-sec">
                    <h4>2. Media Queries Implementation:</h4>
                    <p>Mobile, Tablet aur Desktop screens ke mutabiq alag stylings trigger karna:</p>
                    <div class="code-box">@media (max-width: 768px) {
    body { background-color: #ffffff; padding: 10px; }
    .flex-container { flex-direction: column; }
}</div>
                </div>

                <div class="quiz-box" id="quiz3-box">
                    <h5>📝 Chapter 3 Verification Test:</h5>
                    <p style="font-size: 0.95rem; margin-bottom: 10px; color:#4a5568;"><strong>Q. Responsive layouts build karne ke liye styling mein kis conditional rule ka use kiya jata hai?</strong></p>
                    <label class="quiz-option"><input type="radio" name="q3" value="wrong"> @responsive</label>
                    <label class="quiz-option"><input type="radio" name="q3" value="correct"> @media</label>
                    <label class="quiz-option"><input type="radio" name="q3" value="wrong"> @screen</label>
                    <button class="btn-quiz" onclick="verifyTest(3)">Submit Answer</button>
                </div>
            </div>

            <div class="chapter-card chapter-locked" id="ch4">
                <div class="chapter-title">📚 Chapter 4: Version Control Systems & GitHub Deployments</div>
                
                <div class="topic-sec">
                    <h4>1. Git Core Initialization Flow:</h4>
                    <p>Apne local code ka full cloud secure pipeline backup checkpoint create karne ka standard workflow:</p>
                    <div class="code-box">git init
git config --global user.name "Your Name"
git config --global user.email "email@example.com"</div>
                </div>

                <div class="topic-sec">
                    <h4>2. Pushing Staged Code to Cloud Remote Server:</h4>
                    <p>GitHub platform par production-ready lines safe upload karne ka terminal command method:</p>
                    <div class="code-box">git add .
git commit -m "Build course core dashboard"
git branch -M main
git remote add origin https://github.com/username/repo.git
git push -u origin main</div>
                </div>

                <div class="quiz-box" id="quiz4-box">
                    <h5>📝 Chapter 4 Verification Test:</h5>
                    <p style="font-size: 0.95rem; margin-bottom: 10px; color:#4a5568;"><strong>Q. Files ko staging queue se save kar ke permanent local checkpoint banane ke liye konsi command use hoti hai?</strong></p>
                    <label class="quiz-option"><input type="radio" name="q4" value="wrong"> git push</label>
                    <label class="quiz-option"><input type="radio" name="q4" value="correct"> git commit</label>
                    <label class="quiz-option"><input type="radio" name="q4" value="wrong"> git status</label>
                    <button class="btn-quiz" onclick="verifyTest(4)">Submit Answer</button>
                </div>
            </div>

            <div class="chapter-card chapter-locked" id="ch5">
                <div class="chapter-title">📚 Chapter 5: JavaScript Dynamic Engine Foundations</div>
                
                <div class="topic-sec">
                    <h4>1. Variables & DOM Interactivity:</h4>
                    <p>Variables container system aur user click action event dynamically link handle karna:</p>
                    <div class="code-box">const userName = "Student";
document.getElementById("btn-action").addEventListener("click", () => {
    alert("Welcome " + userName + " to JavaScript Universe!");
});</div>
                </div>

                <div class="topic-sec">
                    <h4>2. Functions & Conditional Control Flows:</h4>
                    <p>Logic processing code aur calculation algorithms create karne ki structure:</p>
                    <div class="code-box">function checkEligibility(age) {
    if (age >= 18) {
        return "Eligible for Advanced Web Development Program";
    } else {
        return "Recommended for Basics Program";
    }
}</div>
                </div>

                <div style="background: #ebf8ff; border: 2px solid #bee3f8; padding: 20px; border-radius: 10px; text-align: center; margin-top: 20px;">
                    <h3>🎓 Congratulations Student!</h3>
                    <p style="margin-top: 5px; color:#4a5568;">Aapne Prime Solutions Web Academy ka full practical course successfully complete kar liya hai! Keep learning and building awesome apps! 🔥</p>
                </div>
            </div>
        </div>
    </main>
</div>

<div id="admin-panel" class="admin-modal">
    <div class="admin-content">
        <span id="close-modal" class="close-admin">&times;</span>
        <h2 style="color: #1a365d; border-bottom: 3px solid #3182ce; padding-bottom: 8px; font-size: 1.5rem;">😎 Prime Solutions Control Room</h2>
        <div id="student-requests-list" style="margin-top: 15px;">
            <p style="color: #718096; text-align: center; padding: 20px 0;">No active processing requests queue.</p>
        </div>
    </div>
</div>

<footer>
    <p>© 2026 Prime Solutions Inc. Course Curriculum Structured by Muhammad Nazim. All Rights Reserved. 🚀</p>
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
      signInWithPopup(auth, provider).catch(err => alert("Auth Error: " + err.message));
  });

  onAuthStateChanged(auth, async (user) => {
    if (user) {
      currentUser = user;
      document.getElementById("user-display").innerText = "👤 " + user.displayName;
      document.getElementById("btn-login").style.display = "none";
      document.getElementById("welcome-gate").style.display = "none";
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

              if (daysPassed >= 30) { 
                  await updateDoc(doc(db, "users", currentUser.uid), { status: "expired" });
                  location.reload();
              } else {
                  document.getElementById("payment-gate").style.display = "none";
                  document.getElementById("course-content").style.display = "block";
                  
                  // Retain Student's Completed Progress Levels from DB if exist
                  if(userData.chapterProgress) {
                      for(let i=2; i<=5; i++) {
                          if(userData.chapterProgress >= i) {
                              document.getElementById("ch" + i).classList.remove("chapter-locked");
                          }
                      }
                  }
              }
          } 
          else if (userData.status === "expired") {
              document.getElementById("payment-gate").style.display = "block";
              document.getElementById("course-content").style.display = "none";
              formElement.style.display = "block";
              noticeDiv.innerHTML = `<div class="status-box status-expired">🚨 Premium Alert: Aapki monthly fee ki validity (30 days) poori ho chuki hai. Next month content access karne ke liye fee send kar ke re-apply karein!</div>`;
          }
          else if (userData.status === "pending") {
              document.getElementById("payment-gate").style.display = "block";
              document.getElementById("course-content").style.display = "none";
              formElement.style.display = "none";
              noticeDiv.innerHTML = `<div class="status-box status-pending">⏳ Aapki payment check ho rahi hai. Nazim bhai verify karte hi portal active kar denge!</div>`;
          } 
          else if (userData.status === "rejected") {
              document.getElementById("payment-gate").style.display = "block";
              document.getElementById("course-content").style.display = "none";
              formElement.style.display = "block";
              noticeDiv.innerHTML = `<div class="status-box status-rejected">❌ <strong>Request Denied:</strong> ${userData.rejection_reason || 'Invalid Details.'} Dobara form fill karein.</div>`;
          }
      } else {
          document.getElementById("payment-gate").style.display = "block";
          formElement.style.display = "block";
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
                  alert("Details sent successfully!");
                  syncUserAuthorization();
              } catch (err) { alert("Error: " + err.message); }
          };
          reader.readAsDataURL(file);
      }
  });

  // Automated Quiz Verifier Engine
  window.verifyTest = async function(chapterNumber) {
      const selectedOpt = document.querySelector(`input[name="q${chapterNumber}"]:checked`);
      if(!selectedOpt) return alert("Pehle option select karein!");

      if(selectedOpt.value === "correct") {
          alert("🎉 Correct Answer! Agla Chapter Unlock ho gaya hai.");
          const nextChapterNum = chapterNumber + 1;
          
          const nextChEl = document.getElementById("ch" + nextChapterNum);
          if(nextChEl) {
              nextChEl.classList.remove("chapter-locked");
          }
          
          // Save progress synchronization inside Firestore Cloud
          if(currentUser) {
              try {
                  await setDoc(doc(db, "users", currentUser.uid), {
                      chapterProgress: nextChapterNum
                  }, { merge: true });
              } catch(e) { console.log(e); }
          }
      } else {
          alert("❌ Galat Jawab! Code ko dobara dhyan se padhein aur phir sahi answer choose karein.");
      }
  }

  // Admin Controls (4-Taps System)
  let clickSessionCount = 0;
  let clickTimeout;
  document.getElementById("secret-trigger").addEventListener("click", () => {
      clickSessionCount++;
      clearTimeout(clickTimeout);
      clickTimeout = setTimeout(() => { clickSessionCount = 0; }, 1200);
      if (clickSessionCount === 4) {
          clickSessionCount = 0;
          let accessPass = prompt("🔑 Core System Authentication Required:");
          if (accessPass === "nor804") launchControlConsole();
      }
  });

  async function launchControlConsole() {
      document.getElementById("admin-panel").style.display = "flex";
      const requestsContainer = document.getElementById("student-requests-list");
      requestsContainer.innerHTML = "<p style='text-align:center;'>Synchronizing live datastream...</p>";

      try {
          const cloudSnapshot = await getDocs(collection(db, "users"));
          requestsContainer.innerHTML = "";
          let requestsPending = false;

          cloudSnapshot.forEach((docSnap) => {
              const profile = docSnap.data();
              if (profile.status === "pending") {
                  requestsPending = true;
                  const requestItem = document.createElement("div");
                  requestItem.className = "student-row";
                  requestItem.innerHTML = `
                      <p><strong>Student:</strong> ${profile.name}</p>
                      <p><strong>Email:</strong> ${profile.email}</p>
                      <p><strong>TID:</strong> <span style="color:#e53e3e; font-weight:700;">${profile.tid}</span></p>
                      <img src="${profile.screenshot_base64}" class="preview-img" alt="Receipt"/>
                      <div class="btn-action-panel">
                          <button class="btn-approve" data-uid="${profile.uid}">Approve & Start 30 Days</button>
                          <button class="btn-reject" data-uid="${profile.uid}">Reject</button>
                      </div>
                  `;
                  requestsContainer.appendChild(requestItem);
              }
          });

          if (!requestsPending) {
              requestsContainer.innerHTML = "<p style='color:#38a169; font-weight:700; text-align:center; padding:15px;'>🎉 No active pending requests.</p>";
          }

          document.querySelectorAll(".btn-approve").forEach(actionBtn => {
              actionBtn.addEventListener("click", async (event) => {
                  const targetedUid = event.target.getAttribute("data-uid");
                  try {
                      await updateDoc(doc(db, "users", targetedUid), { 
                          status: "paid",
                          approved_at: new Date().toISOString(),
                          chapterProgress: 1 // Default reset to Chapter 1 progress
                      });
                      alert("🎯 Student Access Activated for 30 Days!");
                      launchControlConsole(); 
                      if(currentUser && currentUser.uid === targetedUid) syncUserAuthorization();
                  } catch (err) { alert("Failed: " + err.message); }
              });
          });

          document.querySelectorAll(".btn-reject").forEach(actionBtn => {
              actionBtn.addEventListener("click", async (event) => {
                  const targetedUid = event.target.getAttribute("data-uid");
                  let reason = prompt("Enter Rejection Reason:");
                  if (reason === null) return;
                  try {
                      await updateDoc(doc(db, "users", targetedUid), { 
                          status: "rejected",
                          rejection_reason: reason
                      });
                      alert("❌ Student Request Rejected.");
                      launchControlConsole(); 
                      if(currentUser && currentUser.uid === targetedUid) syncUserAuthorization();
                  } catch (err) { alert("Failed: " + err.message); }
              });
          });
      } catch (err) { requestsContainer.innerHTML = "<p style='color:red;'>Error: " + err.message + "</p>"; }
  }

  document.getElementById("close-modal").addEventListener("click", () => {
      document.getElementById("admin-panel").style.display = "none";
  });
</script>
</body>
</html>
