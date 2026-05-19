<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Prime Solutions - Web Development Academy</title>
    <style>
        * { box-sizing: border-box; margin: 0; padding: 0; font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; }
        body { background-color: #f0f4f8; color: #2d3748; padding: 15px; min-height: 100vh; display: flex; flex-direction: column; justify-content: space-between; }
        .container { max-width: 750px; margin: 0 auto; width: 100%; }
        
        /* Premium Top Navbar */
        .navbar { display: flex; justify-content: space-between; align-items: center; background: white; padding: 15px 20px; border-radius: 12px; box-shadow: 0 4px 6px rgba(0,0,0,0.05); margin-bottom: 25px; }
        .nav-brand { font-weight: bold; color: #1a365d; font-size: 1.1rem; }
        .btn-google { background: #ea4335; color: white; padding: 10px 16px; border: none; border-radius: 8px; font-weight: bold; cursor: pointer; display: flex; align-items: center; gap: 8px; box-shadow: 0 2px 4px rgba(234,67,53,0.3); transition: 0.2s; }
        .btn-google:hover { background: #d33225; }
        .user-profile { font-weight: 600; color: #2b6cb0; font-size: 0.95rem; }

        /* Professional Header */
        header { text-align: center; padding: 35px 20px; background: linear-gradient(135deg, #1a365d, #2a4365); color: white; border-radius: 15px; margin-bottom: 25px; box-shadow: 0 10px 20px rgba(26,54,93,0.15); position: relative; }
        header h1 { font-size: 2rem; letter-spacing: 0.5px; margin-top: 5px; }
        header p { font-size: 1rem; opacity: 0.85; margin-top: 5px; }
        
        /* Secret Hidden Trigger */
        .secret-logo { width: 55px; height: 55px; background: rgba(255,255,255,0.15); margin: 0 auto 10px auto; border-radius: 50%; display: flex; align-items: center; justify-content: center; cursor: pointer; font-size: 1.6rem; user-select: none; transition: 0.3s; }
        .secret-logo:hover { background: rgba(255,255,255,0.25); transform: scale(1.05); }

        /* Elegant Cards System */
        .card { background: white; padding: 30px 25px; border-radius: 15px; box-shadow: 0 10px 25px rgba(0,0,0,0.05); margin-bottom: 25px; display: none; }
        .card h2 { color: #1a365d; font-size: 1.4rem; margin-bottom: 10px; }
        
        /* Dynamic Status Notice Boxes */
        .status-box { padding: 15px; border-radius: 8px; font-weight: 600; margin-bottom: 20px; text-align: center; font-size: 1rem; }
        .status-pending { background: #feebc8; color: #c05621; border: 1px solid #fbd38d; }
        .status-rejected { background: #fed7d7; color: #9b2c2c; border: 1px solid #feb2b2; text-align: left; }

        /* Payment Gateway Styling */
        .account-wrapper { background: #f7fafc; border: 1px dashed #cbd5e0; padding: 20px; border-radius: 10px; margin: 20px 0; text-align: left; }
        .account-item { display: flex; justify-content: space-between; padding: 8px 0; border-bottom: 1px solid #edf2f7; }
        .account-item:last-child { border: none; }
        .input-field { width: 100%; padding: 14px; margin-bottom: 15px; border: 1px solid #e2e8f0; border-radius: 8px; font-size: 1rem; outline: none; transition: 0.2s; }
        .input-field:focus { border-color: #3182ce; box-shadow: 0 0 0 3px rgba(49,130,206,0.15); }
        .btn-submit { width: 100%; padding: 14px; background: #3182ce; color: white; border: none; border-radius: 8px; font-size: 1.05rem; font-weight: bold; cursor: pointer; box-shadow: 0 4px 6px rgba(49,130,206,0.25); }
        .btn-submit:hover { background: #2b6cb0; }

        /* Course Dashboard Styling */
        .week-card { background: white; padding: 25px; border-radius: 12px; margin-bottom: 20px; box-shadow: 0 4px 6px rgba(0,0,0,0.02); border-left: 6px solid #3182ce; }
        .week-header { display: flex; justify-content: space-between; align-items: center; margin-bottom: 15px; }
        .week-title { color: #2c5282; font-size: 1.3rem; font-weight: 700; }
        .badge { background: #48bb78; color: white; padding: 5px 12px; border-radius: 20px; font-size: 0.8rem; font-weight: bold; text-transform: uppercase; }
        ul { list-style: none; }
        li { margin: 12px 0; font-size: 1.02rem; color: #4a5568; display: flex; align-items: flex-start; gap: 10px; }
        li::before { content: "⚡"; color: #3182ce; font-weight: bold; }

        /* Secret Admin View */
        .admin-modal { display: none; position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0,0,0,0.6); backdrop-filter: blur(5px); z-index: 1000; justify-content: center; align-items: center; padding: 15px; }
        .admin-content { background: white; padding: 30px; border-radius: 15px; max-width: 600px; width: 100%; max-height: 85vh; overflow-y: auto; position: relative; box-shadow: 0 20px 25px rgba(0,0,0,0.15); }
        .close-admin { position: absolute; top: 15px; right: 20px; font-size: 1.8rem; cursor: pointer; color: #a0aec0; }
        .student-row { background: #f7fafc; padding: 18px; margin-top: 15px; border-radius: 10px; border: 1px solid #e2e8f0; }
        .preview-img { max-width: 100%; max-height: 180px; margin-top: 12px; border-radius: 8px; border: 2px solid #e2e8f0; object-fit: contain; background: white; }
        .btn-action-panel { display: flex; gap: 10px; margin-top: 12px; }
        .btn-approve { background: #38a169; color: white; padding: 10px; border: none; border-radius: 6px; cursor: pointer; font-weight: bold; flex: 1; }
        .btn-reject { background: #e53e3e; color: white; padding: 10px; border: none; border-radius: 6px; cursor: pointer; font-weight: bold; flex: 1; }

        footer { text-align: center; padding: 25px 0; color: #718096; font-size: 0.9rem; border-top: 1px solid #e2e8f0; margin-top: 40px; }
    </style>
</head>
<body>

<div class="container">
    <div class="navbar">
        <div class="nav-brand">🌐 Prime Solutions</div>
        <div>
            <span id="user-display" class="user-profile">🔒 Security Gate</span>
            <button id="btn-login" class="btn-google">Login with Google</button>
        </div>
    </div>

    <header>
        <div id="secret-trigger" class="secret-logo">👨‍💻</div>
        <h1>Web Development Academy</h1>
        <p>Instructor & Mentor: Muhammad Nazim</p>
    </header>

    <main>
        <div id="welcome-gate" class="card" style="display: block; text-align: center;">
            <h2>Assalam-o-Alaikum Student! 👋</h2>
            <p style="color: #64748b; margin-top: 10px; line-height: 1.6;">Prime Solutions ke official premium portal par khushamdeed. Dashboard access karne ke liye upar diye gaye button se Google Login karein.</p>
        </div>

        <div id="payment-gate" class="card">
            <div id="student-status-notice"></div>

            <h2>🔒 Premium Content Locked</h2>
            <p style="color: #64748b; margin-top: 5px;">Course content unlock karne ke liye fee send kar ke details submit karein:</p>
            
            <div class="account-wrapper">
                <div class="account-item"><strong>📱 JazzCash Account:</strong> <span>03705519562</span></div>
                <div class="account-item"><strong>📱 EasyPaisa Account:</strong> <span>03379827882</span></div>
                <div class="account-item"><strong>👤 Account Title:</strong> <span>Muhammad Nazim</span></div>
                <div class="account-item"><strong>💰 Monthly Course Fee:</strong> <span>1,500 PKR</span></div>
            </div>

            <form id="payment-form">
                <input type="text" id="tid-input" placeholder="Enter 11-Digit Transaction ID (TID)" required class="input-field">
                <label style="font-weight: 600; display: block; margin-bottom: 8px; text-align: left; font-size: 0.9rem; color: #4a5568;">Upload Payment Receipt Screenshot:</label>
                <input type="file" id="screenshot-input" accept="image/*" required class="input-field" style="padding: 10px;">
                <button type="submit" id="btn-submit-payment" class="btn-submit">Submit Verification Request</button>
            </form>
        </div>

        <div id="course-content" class="card">
            <div class="week-card">
                <div class="week-header">
                    <span class="week-title">Week 1: Foundations of HTML5</span>
                    <span class="badge">Live & Active</span>
                </div>
                <ul>
                    <li>Setting up environment inside Termux & Acode editor on Android.</li>
                    <li>Understanding the DOM hierarchy and HTML basic scaffolding tags.</li>
                    <li>Working with semantic tags, hyperlinks, custom tables, and asset injection.</li>
                    <li><strong>Practical Assignment:</strong> Build your structured business resume page.</li>
                </ul>
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
    <p>© 2026 Prime Solutions Inc. Developed by Muhammad Nazim. All Rights Reserved. 🚀</p>
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
      signInWithPopup(auth, provider).catch(err => alert("Auth Engine Error: " + err.message));
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
              document.getElementById("payment-gate").style.display = "none";
              document.getElementById("course-content").style.display = "block";
          } 
          else if (userData.status === "pending") {
              document.getElementById("payment-gate").style.display = "block";
              document.getElementById("course-content").style.display = "none";
              formElement.style.display = "none"; // Hide input fields if pending
              noticeDiv.innerHTML = `<div class="status-box status-pending">⏳ Aapki payment check ho rahi hai. Nazim bhai jald hi verify kar ke course unlock kar denge!</div>`;
          } 
          else if (userData.status === "rejected") {
              document.getElementById("payment-gate").style.display = "block";
              document.getElementById("course-content").style.display = "none";
              formElement.style.display = "block"; // Show form again to let them retry
              noticeDiv.innerHTML = `
                  <div class="status-box status-rejected">
                      ❌ <strong>Aapki Payment Request Reject ho gayi hai!</strong><br>
                      <span style="font-weight:normal;">Reason: ${userData.rejection_reason || 'Invalid TID or Screenshot.'}</span><br>
                      <span style="font-size:0.9rem; opacity:0.9;">Khas taur par sahi screenshot aur real TID daal kar dobara apply karein.</span>
                  </div>`;
          }
          else { // unpaid status
              document.getElementById("payment-gate").style.display = "block";
              document.getElementById("course-content").style.display = "none";
              formElement.style.display = "block";
          }
      } else {
          document.getElementById("payment-gate").style.display = "block";
          document.getElementById("course-content").style.display = "none";
          formElement.style.display = "block";
      }
  }

  document.getElementById("payment-form").addEventListener("submit", (e) => {
      e.preventDefault();
      if (!currentUser) return alert("Session expired.");

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
                      status: "pending", // Status update to pending
                      tid: tid,
                      screenshot_base64: reader.result,
                      submitted_at: new Date().toISOString()
                  }, { merge: true });
                  alert("Transmitted successfully!");
                  syncUserAuthorization();
              } catch (err) { alert("Error: " + err.message); }
          };
          reader.readAsDataURL(file);
      }
  });

  // Secret 4-Tap Easter Egg Logic
  let clickSessionCount = 0;
  let clickTimeout;

  document.getElementById("secret-trigger").addEventListener("click", () => {
      clickSessionCount++;
      clearTimeout(clickTimeout);
      clickTimeout = setTimeout(() => { clickSessionCount = 0; }, 1200);

      if (clickSessionCount === 4) {
          clickSessionCount = 0;
          let accessPass = prompt("🔑 Core System Authentication Required:");
          if (accessPass === "nor804") {
              launchControlConsole();
          } else if (accessPass !== null) {
              alert("💥 Intrusion Detected. Access Denied.");
          }
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
              if (profile.status === "pending") { // Only pending show in admin control
                  requestsPending = true;
                  const requestItem = document.createElement("div");
                  requestItem.className = "student-row";
                  requestItem.innerHTML = `
                      <p><strong>Student:</strong> ${profile.name || 'Anonymous User'}</p>
                      <p><strong>Email:</strong> ${profile.email}</p>
                      <p><strong>TID:</strong> <span style="color:#e53e3e; font-weight:700;">${profile.tid}</span></p>
                      <img src="${profile.screenshot_base64}" class="preview-img" alt="Receipt"/>
                      <div class="btn-action-panel">
                          <button class="btn-approve" data-uid="${profile.uid}">Approve & Unlock</button>
                          <button class="btn-reject" data-uid="${profile.uid}">Reject</button>
                      </div>
                  `;
                  requestsContainer.appendChild(requestItem);
              }
          });

          if (!requestsPending) {
              requestsContainer.innerHTML = "<p style='color:#38a169; font-weight:700; text-align:center; padding:15px;'>🎉 No active pending requests found in Firestore.</p>";
          }

          // Approve Logic
          document.querySelectorAll(".btn-approve").forEach(actionBtn => {
              actionBtn.addEventListener("click", async (event) => {
                  const targetedUid = event.target.getAttribute("data-uid");
                  try {
                      await updateDoc(doc(db, "users", targetedUid), { status: "paid" });
                      alert("🎯 Status Updated to PAID.");
                      launchControlConsole(); 
                      if(currentUser && currentUser.uid === targetedUid) syncUserAuthorization();
                  } catch (err) { alert("Execution Failed: " + err.message); }
              });
          });

          // Reject Logic
          document.querySelectorAll(".btn-reject").forEach(actionBtn => {
              actionBtn.addEventListener("click", async (event) => {
                  const targetedUid = event.target.getAttribute("data-uid");
                  let reason = prompt("Enter Rejection Reason (e.g., Fake Screenshot / Expired TID):");
                  if (reason === null) return; // cancel click
                  if (reason.trim() === "") reason = "Invalid or blurry verification details.";
                  
                  try {
                      await updateDoc(doc(db, "users", targetedUid), { 
                          status: "rejected",
                          rejection_reason: reason
                      });
                      alert("❌ Status Updated to REJECTED.");
                      launchControlConsole(); 
                      if(currentUser && currentUser.uid === targetedUid) syncUserAuthorization();
                  } catch (err) { alert("Execution Failed: " + err.message); }
              });
          });

      } catch (err) { requestsContainer.innerHTML = "<p style='color:red;'>Failed to compile cloud documents: " + err.message + "</p>"; }
  }

  document.getElementById("close-modal").addEventListener("click", () => {
      document.getElementById("admin-panel").style.display = "none";
  });
</script>
</body>
</html>
